---
tipo: adr
id: ADR-002
estado: propuesto-pendiente-validacion
fecha: 2026-10-14
actualizado: 2026-10-16
---
# ADR-002 — Modelo lógico relacional v0.1

Fecha de referencia: 14 de octubre de 2026. Actualización documental: 16 de octubre de 2026.

**Estado: DISEÑO PROPUESTO — PENDIENTE DE VALIDACIÓN FINAL**.

## Decisiones de negocio confirmadas

Inicialmente existirán los roles ADMIN y CLIENT, con permisos fijos por rol. Los cursos serán productos comprables mediante el mismo carrito. Los descuentos de productos se expresarán como porcentajes. Esto no incluye cupones: quedan aplazados en esta etapa.

## Propuesta de persistencia

Se proponen `users`, `client_profiles` y, solo si lo requiere la estrategia de autenticación, `user_sessions`; `categories`, `products`, `plants`, `supplements`, `medicines`, `courses`; `carts`, `cart_items`, `orders`, `order_items`; `payments`, `inventory`, `inventory_movements`; y `course_enrollments`.

Los criterios propuestos son UUID como claves primarias, claves foráneas para integridad referencial e índices según consultas, con restricciones UNIQUE, CHECK y NOT NULL según corresponda. Los importes usarán NUMERIC y las marcas temporales TIMESTAMPTZ. La precisión monetaria, moneda y redondeo quedan por validar.

El correo será único sin distinguir mayúsculas, mediante una solución PostgreSQL a elegir. Las contraseñas solo se guardarán como hash seguro con sal; el algoritmo y sus parámetros deberán definirse. Los roles podrán representarse como un valor restringido en `users`; no se propone un sistema de permisos configurables.

Cada producto deberá tener exactamente un tipo especializado; el discriminador, las claves y la validación entre especializaciones deberán garantizarlo de forma consistente. Una FK por sí sola no impide que un producto aparezca en dos tablas especializadas. La lista actual no define una especialización para snacks saludables exigidos por FR-06 y FR-21: esa cobertura queda sin resolver, no se excluyen del alcance aprobado.

Los pedidos conservarán copias históricas de nombres, cantidades, precios, porcentajes y descuentos aplicados, importes y datos de entrega pertinentes, sin depender de cambios posteriores del catálogo o perfil. La eliminación de cuentas o productos no deberá borrar pedidos ni movimientos asociados; las reglas de baja, anonimización y retención requieren validación conforme a NFR-02 y NFR-29.

Las existencias y reservas se controlarán transaccionalmente, evitando disponibilidad negativa y sobreventa. El detalle de lotes, vencimientos, variantes y vencimiento de reservas no está resuelto. Los pagos requieren verificación de estado e idempotencia. Las inscripciones derivadas de ventas se vincularán a compras confirmadas.

## Relaciones y límites

Las cardinalidades tentativas se detallan en el [modelo lógico](<../Database/Modelo lógico relacional v0.1.md>). El modelo no cubre todavía todos los requisitos: email, boletines, opiniones, auditoría general, recuperación de contraseña y materiales de cursos requieren diseño posterior. No se crean tablas ni migraciones ni se presenta este inventario como esquema definitivo.

## Referencias

- [ADR-001](<ADR-001 - Backend y persistencia.md>).
- [Reglas por módulo](<../Reglas del backend.md>).
- [Conflictos y pendientes](<../../Management/Diferencias y decisiones pendientes.md>).
- [Requisitos funcionales originales](<../../../FRs/functional-requirements.md>).
