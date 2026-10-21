---
tipo: registro-de-avances
estado: implementacion-parcial
actualizado: 2026-10-21
---
# Registro de avances

## Revisión del backend — 2026-10-21

Fuente: repositorio hermano `El-Jardin-de-tu-Salud-Backend`, HEAD `c63fe97`. Se inspeccionaron código, configuración, migraciones y pruebas. Los commits `b37bd23`, `49b2236` y `c63fe97` incorporan CORS, aplicación/configuración y persistencia inicial. El contenido del código prevalece sobre el título del commit.

| Área | Evidencia en backend | Estado comprobado |
|---|---|---|
| Aplicación | `app/main.py`, `app/core/config.py` | Fábrica FastAPI, CORS, GET /health y documentación deshabilitada en producción |
| Errores | `app/core/exceptions.py` | Manejadores HTTP, validación, AppException y error general |
| Persistencia | `app/db/base.py`, `app/db/session.py` | Base declarativa, engine psycopg y sesiones SQLAlchemy; sin commit automático en get_db |
| Identidad | `app/modules/users/models.py` | User y ClientProfile; email único lower(email), CHECK de rol, UUID y FK RESTRICT |
| Migraciones | `alembic/versions/` | Baseline fbb92a483cb4 → ee44ed5d90be para users/client_profiles; aplicación a PostgreSQL no verificada |
| Pruebas HTTP | `tests/test_core.py` | Cuatro casos: health, origen CORS permitido, rechazado y 404 |
| Pruebas de persistencia | `tests/test_users_models.py` | Cuatro casos definidos; ejecución PostgreSQL no verificada en esta revisión |

`SessionLocal` corresponde a persistencia. No existe implementación de sesiones de autenticación, login, registro, permisos por recurso, hash de contraseñas ni recuperación/email. FR-01 a FR-05 siguen sin cumplimiento completo. El resto del modelo relacional y los módulos comerciales continúan propuestos.

## Diferencias comprobadas que requieren trabajo posterior

- El título del commit c63fe97 menciona sesiones, pero la migración crea usuarios y perfiles, no `user_sessions`.
- `.env.example` tiene APP_ENV inválido, booleanos vacíos y CORS_ORIGINS sin JSON válido; omite TEST_DATABASE_URL. Los campos DB_* no se usan para construir DATABASE_URL.
- `requirements.txt` no incluye SQLAlchemy, psycopg ni Alembic; el README dirige la instalación a `pyproject.toml`.
- `Settings.app_name` usa `La Tia Richard API`; la base de pruebas está fijada a `tia_richrad_test` en scripts y pruebas. Se documentan los nombres reales sin corregir código.
- ClientProfile separa nombres/apellidos, pero no implementa teléfono (FR-01), direcciones o preferencias (FR-04). La asignación obligatoria de perfil a CLIENT no se garantiza por FK.
- `password_hash` es una columna, no evidencia de hashing seguro implementado. El CHECK de rol no implementa autorización HTTP.
- `updated_at` usa onupdate en ORM, sin trigger de actualización SQL; UUID se genera en Python, no con default en servidor.
- `tests/test_database.py` no contiene casos recogidos por pytest; ejecutar pytest no aplica sus migraciones.
- El diagrama de clases sigue siendo conceptual: Credential, Session y PasswordResetToken no son tablas existentes; el hash está en users.

No se modifican requisitos ni se aprueban automáticamente las decisiones de autenticación por observar estas bases técnicas. DEC-01 a DEC-05 conservan su resolución.

## Verificación de esta revisión

Se revisaron enlaces, referencias a archivos y consistencia entre modelos y migraciones. Las migraciones y pruebas de integración no se ejecutaron contra una base configurada del usuario. Se intentó `venv/bin/python -m pytest tests/test_core.py -p no:cacheprovider` con Python 3.14.8: pytest recogió cuatro casos, pero la ejecución quedó detenida en test_health y fue interrumpida. No hay resultado aprobado ni causa diagnosticada. Se validaron 191 enlaces internos y relativos sin errores después de corregir la ruta al README hermano; git diff --check pasó en ambos repositorios.

[README del backend](<../../../El-Jardin-de-tu-Salud-Backend/README.md>) · [[ADR-001 - Backend y persistencia]] · [[ADR-002 - Modelo lógico relacional v0.1]] · [[ADR-003 - Autenticación y autorización]] · [[Trazabilidad - Sprint 01]]
