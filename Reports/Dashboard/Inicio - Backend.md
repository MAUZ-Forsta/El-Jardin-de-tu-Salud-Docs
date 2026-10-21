---
tipo: dashboard
estado: inicial
actualizado: 2026-10-21
tags: [backend, documentacion]
---
# Backend — índice documental

## Situación
- Frontend React parcial; código no recibido en esta fase.
- Backend con implementación inicial verificada por lectura de código: aplicación, configuración, errores, persistencia y migraciones de usuarios/perfiles. Aplicación de migraciones a PostgreSQL no verificada.
- El stack Python / FastAPI / PostgreSQL y el monolito modular están **aprobados, con implementación parcial** (ADR-001). El modelo relacional ADR-002 sigue propuesto y la autenticación ADR-003 pendiente de validación.

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
3. Completar y verificar la implementación parcial del stack aprobado y resolver el modelo relacional y la estrategia de autenticación.
4. Diseñar contrato API inicial y pruebas de aceptación.

## Estado contrastado con código — 2026-10-21

Sprint 01 parcialmente avanzado en infraestructura y persistencia; FR-01 a FR-05 no se consideran terminados.

Véase [[Registro de avances]] para evidencia, diferencias y límites de la validación.
