---
tipo: sprint
sprint: 1
estado: plan-propuesto
actualizado: 2026-10-21
capacidad_semanal_referencia_horas: 17
---
# Plan Sprint 01 — Usuarios y acceso

## Objetivo
Establecer base técnica y flujo mínimo seguro de registro, inicio/cierre de sesión y permisos, sustentado en FR-01 a FR-05. La cobertura completa de perfil, correos y recuperación se planifica y verifica por tareas; no declararla terminada por existir interfaz.

## Alcance preliminar
1. Verificar rutas, formularios, estado y servicios en React; inventariar API esperada.
2. Completar la verificación técnica del stack aprobado, con implementación parcial, mediante prototipo FastAPI + PostgreSQL + SQLAlchemy + Alembic + pytest.
3. Verificar la migración existente para usuarios/perfiles y roles; resolver por separado las sesiones de autenticación (aún propuestas), sin tablas de cupones.
4. Implementar flujo de registro con validación, unicidad y confirmación por correo según FR-01.
5. Implementar inicio/cierre de sesión, control de acceso cliente/administrador y protección de recursos.
6. Diseñar y priorizar recuperación de contraseña y perfil. Si no caben, registrar trabajo pendiente sin declarar conformidad FR-03/FR-04.
7. Ejecutar pruebas automatizadas y manuales de los escenarios definidos.

## Capacidad y fechas
- Desarrollo individual: **17 h/semana base**, no 17 h asignadas automáticamente a este sprint.
- Fecha objetivo global: **2026-12-02**.
- Inicio, fin, duración, horas estimadas y dependencias calendario: **pendientes de cotejar con Gantt y tarjetas Trello reales**.
- Riesgo alto de alcance para una sola iteración: dividir entregables verificables y proteger QA.

## Criterio de terminado (por tarea)
Código revisado · migración aplicada · autorización validada en backend · pruebas superadas · evidencia de ejecución · documentación y contrato actualizado. *Sprint terminado* solo cuando se revisen los criterios acordados y evidencia de todas las tareas comprometidas.

## Dependencias
[[ADR-001 - Backend y persistencia]] · [[ADR-003 - Autenticación y autorización]] · [[API propuesta - Usuarios y acceso]] · [[Plan de pruebas - Sprint 01]] · [[Contradicciones y decisiones pendientes]]

## Registro a completar
| Actividad / Trello | Requisito | Estimación h | Real h | Inicio/fin | Estado | Evidencia |
|---|---|---|---|---|---|---|
| Pendiente de vinculación | FR-01..FR-05 | Pendiente | — | Pendiente | No verificado | — |

## Alcance confirmado al 2026-10-16
Registro e inicio de sesión convencional. Google OAuth excluido del alcance inicial (DEC-02/NFR-39); cupones diferidos (DEC-01/NFR-38). Sin implementación acreditada por esta planificación. Véase [[Plan de sprints]].

## Estado contrastado con código — 2026-10-21

Los puntos de base técnica y persistencia tienen avance: configuración, FastAPI, errores, CORS y migraciones de usuarios/perfiles. No hay migración de sesiones de autenticación. Registro/login, hash, permisos, recuperación y correo siguen pendientes. No se acredita finalización del sprint.

Véase [[Registro de avances]] para evidencia, diferencias y límites de la validación.
