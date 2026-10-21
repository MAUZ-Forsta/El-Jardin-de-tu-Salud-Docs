---
tipo: trazabilidad
estado: preliminar
actualizado: 2026-10-21
---
# Trazabilidad — Sprint 01

| Fuente canónica | Requisito resumido | Diseño | Contrato propuesto | QA | Trello | Estado real |
|---|---|---|---|---|---|---|
| FR-01 | Registro y confirmación | [[ADR-003 - Autenticación y autorización]] | POST `/auth/register` | AUTH-01..03 | Pendiente | No verificado |
| FR-02 | Login y logout | [[ADR-003 - Autenticación y autorización]] | POST `/auth/login`, `/auth/logout` | AUTH-04..06 | Pendiente | No verificado |
| FR-03 | Reset por correo | [[ADR-003 - Autenticación y autorización]] | POST `/auth/password-reset/*` | AUTH-07..08 | Pendiente | No verificado |
| FR-04 | Perfil propio | [[Modelo de clases - Usuarios y acceso]] | GET/PATCH `/users/me` | AUTH-09,11 | Pendiente | No verificado |
| FR-05 | Cliente/admin | [[ADR-003 - Autenticación y autorización]] | `/admin/users` ilustrativo | AUTH-09..10 | Pendiente | No verificado |

- Fuente: `FRs/functional-requirements.md` del repositorio.
- Prioridades temporales del sprint se ajustarán contra Gantt y Trello; no se infiere que FR-01 a FR-05 estén terminados.
- **Cupones**: diferidos mediante DEC-01/NFR-38, sin incorporación automática al Sprint 06; fuera de contratos/modelos/pruebas iniciales. Google OAuth diferido mediante DEC-02/NFR-39. FR-01 a FR-05 y HU originales intactos.

## Estado contrastado con código — 2026-10-21

FR-01/04: modelos users/client_profiles como base parcial, sin rutas, teléfono ni correo. FR-05: CHECK ADMIN/CLIENT, sin autorización por recurso. FR-02/03: flujos sin implementar. Las rutas de la tabla siguen propuestas. Los tests existentes son técnicos de core y persistencia; no equivalen a los escenarios AUTH completados.

Véase [[Registro de avances]] para evidencia, diferencias y límites de la validación.
