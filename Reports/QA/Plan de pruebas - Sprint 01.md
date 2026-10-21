---
tipo: plan-qa
estado: propuesto
actualizado: 2026-10-21
---
# Plan de pruebas — Sprint 01

Las pruebas siguientes son **casos propuestos**, no evidencia ejecutada. Aplican a FR-01 a FR-05, NFR-01/03/04/05. No incluir cupones en este sprint.

| ID | Escenario | Resultado esperado | Requisito | Estado |
|---|---|---|---|---|
| AUTH-01 | Registro con datos correctos | Cuenta creada y correo de confirmación procesado | FR-01 | No ejecutado |
| AUTH-02 | Email duplicado con variaciones de mayúsculas | No se crean cuentas duplicadas | FR-01 | No ejecutado |
| AUTH-03 | Registro con password inválida | Rechazo seguro de entrada | FR-01/NFR-04 | No ejecutado |
| AUTH-04 | Login correcto | Sesión autorizada | FR-02 | No ejecutado |
| AUTH-05 | Credenciales erróneas | Acceso denegado sin fuga de información | FR-02 | No ejecutado |
| AUTH-06 | Logout y reutilización de sesión | Sesión revocada | FR-02 | No ejecutado |
| AUTH-07 | Recuperación con token expirado o reutilizado | Rechazo, sin cambio de password | FR-03 | No ejecutado |
| AUTH-08 | Solicitud de recuperación de email inexistente | Respuesta indistinguible y limitación de abuso | FR-03 | No ejecutado |
| AUTH-09 | Cliente modifica perfil ajeno | 403/404 sin fuga de datos | FR-04/FR-05 | No ejecutado |
| AUTH-10 | Cliente invoca ruta administrativa | 403 | FR-05 | No ejecutado |
| AUTH-11 | Cambio sensible sin revalidación | Operación denegada | FR-04 | No ejecutado |
| AUTH-12 | Revisión de transporte y cookie | Solo HTTPS en producción y flags adecuados | NFR-03 | No ejecutado |

## Evidencia mínima
Commit/PR, versión de prueba, migración, resultado pytest, entorno, fecha y defectos. Ejecutar pruebas de concurrencia/autorización y revisión de dependencias antes de producción. Las cargas y umbrales específicos NFR deberán medirse en un entorno representativo.

## Gates de QA
- Errores de autorización o de filtración de datos bloquean aprobación.
- Correo no entregado o reset inseguro bloquean conformidad FR-01/FR-03 si sus alcances se entregan.
- Una pantalla React visible no constituye una prueba exitosa.

## Estado contrastado con código — 2026-10-21

Existen cuatro pruebas técnicas en tests/test_core.py y cuatro de modelos en tests/test_users_models.py. No acreditan los casos AUTH-01 a AUTH-12. tests/test_database.py es una utilidad, no un caso recogido por pytest. La evidencia de ejecución se registra por separado en Registro de avances.

Véase [[Registro de avances]] para evidencia, diferencias y límites de la validación.
