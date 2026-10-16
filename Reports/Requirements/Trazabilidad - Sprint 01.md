---
tipo: trazabilidad
estado: preliminar
actualizado: 2026-10-12
---
# Trazabilidad — Sprint 01

| Fuente canónica | Requisito resumido | Diseño | Contrato propuesto | QA | Trello | Estado real |
|---|---|---|---|---|---|---|
| FR-01 | Registro y confirmación | [[ADR-002 - Autenticación y autorización]] | POST `/auth/register` | AUTH-01..03 | Pendiente | No verificado |
| FR-02 | Login y logout | [[ADR-002 - Autenticación y autorización]] | POST `/auth/login`, `/auth/logout` | AUTH-04..06 | Pendiente | No verificado |
| FR-03 | Reset por correo | [[ADR-002 - Autenticación y autorización]] | POST `/auth/password-reset/*` | AUTH-07..08 | Pendiente | No verificado |
| FR-04 | Perfil propio | [[Modelo de clases - Usuarios y acceso]] | GET/PATCH `/users/me` | AUTH-09,11 | Pendiente | No verificado |
| FR-05 | Cliente/admin | [[ADR-002 - Autenticación y autorización]] | `/admin/users` ilustrativo | AUTH-09..10 | Pendiente | No verificado |

- Fuente: `FRs/functional-requirements.md` del repositorio.
- Prioridades temporales del sprint se ajustarán contra Gantt y Trello; no se infiere que FR-01 a FR-05 estén terminados.
- **Cupones**: fase final; fuera de los contratos/modelos/pruebas Sprint 01. Referencias originales intactas.
