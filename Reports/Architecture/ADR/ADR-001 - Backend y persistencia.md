---
tipo: adr
id: ADR-001
estado: propuesta
fecha: 2026-10-12
actualizado: 2026-10-12
tags: [arquitectura, backend, decision-pendiente]
---
# ADR-001 — Backend y persistencia

## Estado
**Propuesta — NO aprobada ni implementada.** Requiere inspección del código React, restricciones del cliente y prueba técnica.

## Contexto
- Frontend React parcialmente desarrollado (estado de referencia al 09-10-2026).
- Backend, base de datos y contratos reales de API pendientes de verificar/implementar.
- Desarrollo principalmente individual; capacidad base 17 horas por semana; entrega objetivo 02-12-2026.
- Mayor experiencia del desarrollador con Python que con Java; experiencia en Java sin uso empresarial de Spring.

## Decisión propuesta
- **Backend:** Python + FastAPI.
- **Organización:** monolito modular con orientación a objetos y servicios por caso de uso.
- **Persistencia:** PostgreSQL.
- **ORM:** SQLAlchemy 2.x.
- **Migraciones:** Alembic (propuesto).
- **Pruebas:** pytest y pruebas de integración con base de datos.
- **Infraestructura:** PaaS y base administrada como primera alternativa; no proveedor definitivo.

## Alternativas
- Spring Boot.
- VPS/IaaS: control adicional, pero mayor responsabilidad de operación y seguridad.

## Consecuencias y riesgos
- POO no sustituye transacciones SQL, restricciones relacionales ni control de concurrencia.
- Webhooks, reintentos y pagos necesitan idempotencia y validación de origen.

## Criterios de validación
1. Inspeccionar repositorio frontend y documentación de requisitos vigente.
2. Prototipo FastAPI + PostgreSQL + migraciones y pruebas.
3. Probar autenticación y autorización mínimas, sin credenciales reales en Git.
4. Desplegar entorno de prueba y confirmar conectividad/observabilidad.
5. Aprobar tecnologías y registrar fecha y decisión.

## Referencias
- [[Arquitectura del backend]]
- [[Modelo de dominio - borrador]]
- [[Contradicciones y decisiones pendientes]]
- [Requisitos funcionales](El-Jardin-de-tu-Salud-Docs/El_Jardin_Backend_POO_Documentacion_Fase_1/FRs/functional-requirements.md)
- [Requisitos no funcionales](El-Jardin-de-tu-Salud-Docs/El_Jardin_Backend_POO_Documentacion_Fase_1/NFRs/Non-functional-requirements.md)
