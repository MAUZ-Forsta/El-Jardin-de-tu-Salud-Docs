---
tipo: dashboard
estado: inicial
actualizado: 2026-10-16
tags: [backend, documentacion]
---
# Backend — índice documental

## Situación
- Frontend React parcial; código no recibido en esta fase.
- Backend y base de datos aún sin implementación verificada.
- El stack Python / FastAPI / PostgreSQL y el monolito modular están **aprobados, pendientes de implementación** (ADR-001). El modelo relacional ADR-002 sigue propuesto y la autenticación ADR-003 pendiente de validación.

## Navegación
- [[ADR-001 - Backend y persistencia]]
- [[Arquitectura del backend]]
- [[Modelo de dominio - borrador]]
- [[Contradicciones y decisiones pendientes]]
- [Requisitos de negocio](<../../BRs/business-requirements.md>)
- [Requisitos funcionales](<../../FRs/functional-requirements.md>)
- [Requisitos no funcionales](<../../NFRs/Non-functional-requirements.md>)

## Siguiente validación
1. Revisar repositorio frontend (`package.json`, rutas, servicios, componentes).
2. Confirmar decisiones de alcance con cliente.
3. Validar implementación futura del stack aprobado y resolver el modelo relacional y la estrategia de autenticación.
4. Diseñar contrato API inicial y pruebas de aceptación.
