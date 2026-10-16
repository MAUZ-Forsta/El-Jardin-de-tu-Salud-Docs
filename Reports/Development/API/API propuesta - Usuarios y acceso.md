---
tipo: contrato-api
estado: propuesta-no-implementada
actualizado: 2026-10-12
version: borrador-0
---
# API propuesta — Usuarios y acceso

**NO IMPLEMENTADA / NO APROBADA.** Prefijo ilustrativo `/api/v1`. Los nombres y códigos precisos requieren validación con React y la política de sesión elegida.

| Método | Ruta propuesta | Permiso | Entrada esquemática | Salida esquemática | Errores esperables | Origen |
|---|---|---|---|---|---|---|
| POST | `/auth/register` | Público | nombre, email, teléfono, contraseña | cuenta creada; estado de confirmación | 400/409/422/429 | FR-01 |
| POST | `/auth/login` | Público | email, contraseña | sesión establecida, datos mínimos del usuario | 401/403/429 | FR-02 |
| POST | `/auth/logout` | Autenticado | sesión actual; CSRF si aplica | 204 | 401 | FR-02 |
| POST | `/auth/password-reset/request` | Público | email | respuesta genérica | 422/429 | FR-03 |
| POST | `/auth/password-reset/confirm` | Token de reset válido | token, nueva contraseña | 204 | 400/410/422/429 | FR-03 |
| GET | `/users/me` | Cliente o admin autenticado | — | perfil propio | 401/403 | FR-04 |
| PATCH | `/users/me` | Propietario autenticado | campos editables permitidos | perfil actualizado | 400/401/409/422 | FR-04 |
| GET | `/admin/users` | Admin | paginación, filtros aprobados | lista restringida | 401/403 | FR-05 |

## Ejemplo de contrato ilustrativo de registro
```json
{
  "full_name": "Ejemplo Cliente",
  "email": "persona@example.test",
  "phone": "+520000000000",
  "password": "<valor-solo-ejemplo-no-real>"
}
```
No registrar nunca contraseñas/tokens en logs o ejemplos con credenciales reales.

## Reglas transversales
- Toda verificación de permisos ocurre **en backend**, incluyendo propiedad del recurso.
- Cookies seguras y protección CSRF según ADR-002; CORS restringido al frontend autorizado.
- Errores sin revelar existencia de emails en recuperación o credenciales incorrectas.
- Validación servidor de todos los campos; límite de peticiones de autenticación.
- Decidir cómo se confirma email y cómo responde login antes del contrato final.

## Dependencias frontend
Formularios reales, manejo de sesión, ruta protegida, mensaje de confirmación, restablecimiento, carga, errores y renovación de sesión. **No verificados: requieren revisión del repositorio React.**

## Cambios documentales asociados
[[ADR-002 - Autenticación y autorización]] · [[Modelo de clases - Usuarios y acceso]] · [[Plan de pruebas - Sprint 01]]
