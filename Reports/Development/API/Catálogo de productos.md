---
tipo: contrato-api
modulo: catalogo-productos-fisicos
estado: implementado-en-feature
actualizado: 2026-11-18
---
# Catálogo de productos físicos

Implementación en la rama `feat/product-catalog` del backend. Cubre FR-06, la búsqueda de FR-07, el detalle físico de FR-08 y las operaciones de producto de FR-34. Se limita a productos físicos; los cursos, inventario, opiniones, descuentos y compras requieren módulos posteriores. El catálogo público muestra productos **activos**, pero no confirma stock.

## Modelo y migración

La migración `c7e4a91f2b35`, después de `9b5b0c3d4e6f`, crea:

| Tabla | Contenido y restricciones |
| --- | --- |
| `products` | UUID, `kind`, categoría, nombre, descripción, precio `NUMERIC` no negativo, ingredientes, beneficios, propiedades, uso sugerido, advertencias, `is_active`, fechas. `kind` admite `PHYSICAL` y reserva `COURSE` para el modelo compartido futuro; esta API solo crea y consulta `PHYSICAL`. |
| `product_images` | UUID, FK a producto, URL y posición desde cero. La pareja producto/posición es única. La primera imagen es la principal. |

Las categorías físicas admitidas son `HERBAL_MEDICINE`, `MEDICINAL_PLANT`, `SUPPLEMENT` y `HEALTHY_SNACK`, según FR-06/FR-21. Se guardan como código en `products`; la tabla de categorías propuesta en ADR-002 sigue sin aprobarse y no se crea aquí. La relación producto→imágenes es 1 a N en el contrato HTTP; la API exige al menos una imagen al crear, aunque PostgreSQL no impone por sí solo ese mínimo entre tablas.

El precio usa `Decimal`/`NUMERIC` sin redondeo automático ni escala fijada: precisión monetaria, moneda, descuentos e impuestos siguen pendientes de decisión. `is_active=false` es el estado inicial; activar o desactivar reemplaza el borrado físico para preservar referencias comerciales futuras. No hay endpoint `DELETE`. Ninguna tabla de stock se crea ni se duplica en `products`.

## Endpoints

Prefijo público `/api/v1/products`; prefijo administrativo `/api/v1/admin/products`.

| Método y ruta | Parámetros / body | Respuesta | Acceso |
| --- | --- | --- | --- |
| `GET /api/v1/products` | `q` opcional, hasta 100 caracteres; `limit` 1–100 (20); `offset` ≥0 (0) | 200: `{items,total,limit,offset}`; solo físicos activos | Público |
| `GET /api/v1/products/{id}` | UUID en ruta | 200: producto activo con `related_products` | Público |
| `GET /api/v1/admin/products` | Mismos parámetros de búsqueda y paginación | 200: lista de físicos activos e inactivos, con estado y fechas | Sesión ADMIN |
| `GET /api/v1/admin/products/{id}` | UUID en ruta | 200: detalle administrativo | Sesión ADMIN |
| `POST /api/v1/admin/products` | JSON `ProductCreate` | 201: producto creado inactivo | Sesión ADMIN, origen confiable y CSRF |
| `PATCH /api/v1/admin/products/{id}` | JSON parcial `ProductPatch` | 200: producto actualizado | Sesión ADMIN, origen confiable y CSRF |

`q` busca coincidencia parcial sin distinguir mayúsculas en nombre, descripción, código de categoría y textos visibles de ingredientes, beneficios, propiedades, uso y advertencias. `%` y `_` se tratan como texto literal. No hay filtro dedicado de categoría, precio o stock conforme a DEC-05. La paginación ordena por creación descendente y UUID descendente. El detalle ofrece hasta cuatro productos activos de la misma categoría, excluyendo el actual.

## Contrato de datos

`ProductCreate` exige `name` (no vacío, máximo 200), `description` (no vacía), `category`, `price` ≥0 e `images` con al menos una URL HTTP(S). Puede incluir `ingredients`, `benefits`, `properties`, `suggested_use` y `warnings` como texto opcional. No acepta campos extra como `stock`, `kind`, `role` o `is_active`.

`ProductPatch` acepta cualquier subconjunto de esos campos y `is_active`. Rechaza un objeto vacío, campos extra y `null` para nombre, descripción, categoría, precio, imágenes o estado. Al enviar `images`, reemplaza la galería completa; la posición sigue el orden de la lista. Los textos opcionales pueden limpiarse con `null`.

La respuesta pública incluye `id` (UUID), nombre, descripción, categoría, precio serializado como cadena decimal, `main_image_url`, `images` con URL/posición, los textos opcionales y `stock_available: null`. No expone `is_active`, `kind` ni fechas internas. La respuesta administrativa agrega `is_active`, `created_at` y `updated_at`.

Ejemplo de creación:

```http
POST /api/v1/admin/products
Origin: http://localhost:5173
X-CSRF-Token: <token-de-la-sesion>
Content-Type: application/json
Cookie: jardin_session=<cookie-http-only>

{
  "name": "Manzanilla orgánica",
  "description": "Infusión de manzanilla.",
  "category": "MEDICINAL_PLANT",
  "price": "12.99",
  "images": ["https://example.test/manzanilla.jpg"],
  "ingredients": "Manzanilla",
  "warnings": "Consultar a un profesional si corresponde."
}
```

La respuesta 201 contiene `is_active: false` y `stock_available: null`. Publicar requiere luego `PATCH /api/v1/admin/products/{id}` con `{"is_active": true}`. Publicar **no** garantiza existencias ni autoriza ventas: inventario y checkout deberán verificar disponibilidad y precio en backend al crear un pedido.

## Errores y seguridad

| Código HTTP | `error.code` | Cuándo |
| --- | --- | --- |
| 401 | `AUTHENTICATION_REQUIRED` o `INVALID_SESSION` | Falta una sesión administrativa válida |
| 403 | `ADMIN_REQUIRED` | La sesión pertenece a CLIENT |
| 403 | `UNTRUSTED_ORIGIN` o `INVALID_CSRF_TOKEN` | Escritura sin origen permitido o token CSRF válido |
| 404 | `PRODUCT_NOT_FOUND` | UUID inexistente o producto inactivo en ruta pública |
| 405 | `HTTP_ERROR` | `DELETE` no está implementado |
| 422 | `VALIDATION_ERROR` | UUID, parámetros o body inválidos |
| 500 | `PRODUCT_WRITE_FAILED` | Fallo de persistencia en creación/actualización, con rollback |

La API nunca acepta un rol enviado por React. Las escrituras verifican la sesión, rol, `Origin` y `X-CSRF-Token` en el backend. Los errores de lectura inesperados usan el manejador general de 500 sin exponer detalles internos.

## Dependencia con React y siguientes módulos

El prototipo React aún usa IDs numéricos, precios `number`, una imagen por producto, beneficios como lista, categorías `plantas/tes/tinturas/aceites/suplementos`, filtros visuales y stock local. El adaptador deberá mapear esos datos al contrato de UUID, precio decimal como cadena, galería y categorías físicas aprobadas; `tes`, `tinturas` y `aceites` no se reasignan automáticamente a una categoría de backend. Tampoco debe presentar `stock_available: null` como disponible ni habilitar compra con base solo en `is_active`.

El siguiente bloque de carrito y pedidos debe consultar precio vigente, exigir cuenta registrada y coordinar inventario transaccional antes del pago. FR-08 aún requiere definir cómo se mostrarán contenido legal de salud y productos relacionados en React; FR-21/22 requieren especializaciones, stock y reglas de concurrencia. Referencias: [FR-06 a FR-08](<../../../FRs/functional-requirements.md>), [FR-21/22 y FR-34](<../../../FRs/functional-requirements.md>), [ADR-002](<../../Architecture/ADR/ADR-002 - Modelo lógico relacional v0.1.md>) y [DEC-05](<../../Management/Contradicciones y decisiones pendientes.md>).
