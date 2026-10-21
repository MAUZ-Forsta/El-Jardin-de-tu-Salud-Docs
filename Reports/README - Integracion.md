---
tipo: guia
estado: actualizado
actualizado: 2026-10-21
---
# Organización del vault

Abrir la raíz del repositorio como vault de Obsidian. Los requisitos canónicos permanecen en BRs, FRs, NFRs, URs, UHs y GUIs. Toda la documentación técnica y de seguimiento se consolida en Reports, sin carpetas paralelas reports, ADRs, diagrams o 01 - Gestión.

- Dashboard: índices y roadmap; comenzar en [[Inicio - Backend]].
- Architecture: arquitectura, reglas, modelos, ADR y Database.
- Management: decisiones, riesgos y planificación; Sprints/Sprint 01 contiene el plan detallado.
- Requirements: matrices de trazabilidad.
- Development/API: contratos propuestos, no implementados.
- QA: planes de pruebas sin evidencia de ejecución.

ADR-001 registra el stack aprobado; ADR-002 el modelo relacional propuesto. El antiguo ADR-002 de autenticación se conserva como ADR-003 para evitar identificadores duplicados. Los enlaces fueron actualizados. No se modifican código, Trello ni alcance contractual ajeno a las decisiones autorizadas; no se realizan commit ni push.

## Estado contrastado con código — 2026-10-21

El estado implementado se registra en [[Registro de avances]]. La arquitectura global y contratos de autenticación siguen propuestos; la base FastAPI y persistencia de usuarios/perfiles ya existen. Las fechas de resolución DEC no cambian con esta revisión.

Véase [[Registro de avances]] para evidencia, diferencias y límites de la validación.
