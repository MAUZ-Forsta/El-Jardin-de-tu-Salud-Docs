# El Jardín de tu Salud - Documentación

Documentación funcional y técnica del e-commerce. Referencia de decisiones: 14 de octubre de 2026; actualización: 21 de octubre de 2026. La aprobación documental no acredita implementación ni pruebas.

## Estructura

```text
BRs/                         Requisitos de negocio
FRs/                         Requisitos funcionales
NFRs/                        Requisitos no funcionales y capacidades diferidas
URs/                         Requisitos de usuario
UHs/                         Historias de usuario
GUIs/                        Interfaces y mockups
Reports/
  Dashboard/                 Índices, roadmap y estado
  Architecture/
    ADR/                     Decisiones arquitectónicas
    Database/                Modelo lógico y cardinalidades
  Management/
    Sprints/Sprint 01/       Plan detallado del primer sprint
  Requirements/              Trazabilidad
  Development/API/           Contratos propuestos
  QA/                        Planes de pruebas
```

## Requisitos canónicos

- [Negocio](BRs/business-requirements.md)
- [Funcionales](FRs/functional-requirements.md)
- [No funcionales](NFRs/Non-functional-requirements.md)
- [Usuario](URs/User-requirements.md)
- [Historias](UHs/User-stories.md)
- [Interfaces](GUIs/GUI-mockups.md)

## Navegación técnica

- [[Inicio - Backend]] · [[Inicio - Sprint 01]]
- [[ADR-001 - Backend y persistencia]]: **APROBADO — IMPLEMENTACIÓN PARCIAL**.
- [[ADR-002 - Modelo lógico relacional v0.1]]: **DISEÑO PROPUESTO — PENDIENTE DE VALIDACIÓN FINAL**.
- [[ADR-003 - Autenticación y autorización]]: propuesta pendiente; antes identificado como ADR-002.
- [[Arquitectura del backend]] · [[Capas del backend]] · [[Modelo lógico relacional v0.1]] · [[Reglas del backend]]
- [[Contradicciones y decisiones pendientes]]: DEC-01 a DEC-05 resueltas el 2026-10-16.
- [[Diferencias y decisiones pendientes]]: conflictos y validaciones restantes.
- [[Plan de sprints]] · [[Roadmap]] · [[Matriz de trazabilidad]]
- [[README - Integracion]]: guía de organización y consolidación.

## Convenciones

Markdown relativo y enlaces internos Obsidian; YAML conservado en notas existentes. Mermaid para diagramas. Prefijos de ramas: `docs/`, `feat/`, `fix/` y `review/`. Cada documento tiene una ubicación canónica; evitar duplicados por mayúsculas o por estructura anterior.

Cupones y Google OAuth quedan diferidos mediante NFR-38/39; no se incorporan automáticamente al Sprint 06. UR-03 exige cursos en línea, conservando materiales individuales descargables. FR-07 mantiene coincidencias parciales y totales. BR, HU y redacción de los FR permanecen intactos.

## Estado contrastado con código — 2026-10-21

El backend ya contiene FastAPI, CORS, manejo de errores, SQLAlchemy, Alembic y modelos/migraciones de users/client_profiles. Autenticación, sesiones de usuario y módulos comerciales pendientes. [Guía de ejecución del backend](../El-Jardin-de-tu-Salud-Backend/README.md) (requiere repositorios hermanos).

Véase [[Registro de avances]] para evidencia, diferencias y límites de la validación.
