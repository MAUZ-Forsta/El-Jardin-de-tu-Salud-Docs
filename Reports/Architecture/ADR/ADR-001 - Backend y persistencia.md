---
tipo: adr
id: ADR-001
estado: aprobado-pendiente-implementacion
fecha: 2026-10-14
actualizado: 2026-10-16
---
# ADR-001 — Stack backend confirmado

Fecha de referencia: 14 de octubre de 2026. Actualización documental: 16 de octubre de 2026.

**Estado: APROBADO — PENDIENTE DE IMPLEMENTACIÓN**.

## Contexto y decisión

El frontend existente es React. Se aprueba Python con FastAPI, PostgreSQL para persistencia, SQLAlchemy 2.x como ORM y Alembic para migraciones futuras. La API será REST e intercambiará JSON. Mercado Pago será la integración futura de pagos.

La arquitectura será un monolito modular con separación de routers, servicios, repositorios, modelos y esquemas de validación. Se aplicará programación orientada a objetos donde aporte valor. La aprobación no acredita implementación: esta actualización no crea endpoints, modelos ni migraciones.

## Consecuencias

Los routers atenderán HTTP; los esquemas validarán entradas y salidas; los servicios coordinarán reglas y transacciones; los repositorios encapsularán persistencia; los modelos representarán datos. Los módulos compartirán una aplicación y una base PostgreSQL. No se seleccionan aún infraestructura, mecanismo de autenticación ni almacenamiento de archivos.

NFR-21 respalda la separación modular. NFR-25 menciona Node.js Express o Springboot como referencia, por lo que existe una discrepancia con este stack aprobado. Se conserva el requisito original hasta conciliarlo; no se interpreta esa referencia como una implementación existente.

## Referencias

- [Arquitectura propuesta](<../Capas del backend.md>).
- [ADR-002](<ADR-002 - Modelo lógico relacional v0.1.md>).
- [NFR originales](<../../../NFRs/Non-functional-requirements.md>): NFR-21 a NFR-25.
- [Conflictos y decisiones pendientes](<../../Management/Diferencias y decisiones pendientes.md>).
