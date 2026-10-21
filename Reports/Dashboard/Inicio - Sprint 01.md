---
tipo: dashboard
estado: preparacion
actualizado: 2026-10-21
---
# Inicio — Sprint 01: Base y autenticación

> Revisión 2026-10-21: base FastAPI y persistencia de usuarios/perfiles implementadas en código. Migraciones aplicadas a PostgreSQL no verificadas. ADR-001 tiene implementación parcial; ADR-002 global y ADR-003 siguen propuestos. Autenticación pendiente.

## Navegación
- [[Plan Sprint 01 - Usuarios y acceso]]
- [[ADR-001 - Backend y persistencia]]
- [[ADR-003 - Autenticación y autorización]]
- [[Modelo de clases - Usuarios y acceso]]
- [[API propuesta - Usuarios y acceso]]
- [[Plan de pruebas - Sprint 01]]
- [[Trazabilidad - Sprint 01]]
- [[Contradicciones y decisiones pendientes]]

## Restricción de alcance vigente
Cupones (NFR-38, DEC-01/04) y Google OAuth (NFR-39, DEC-02) diferidos, sin incorporación automática a Sprint 06. Registro e inicio de sesión convencional vigentes. Cursos en línea, materiales individuales descargables y búsqueda parcial o total según DEC-03/05.

## Próximos insumos a verificar
- Repositorio React: `package.json`, rutas, formularios y servicios existentes.
- Tarjetas reales de Trello y Gantt con fechas.
- Validación final del modelo relacional ADR-002 y de autenticación ADR-003, sesiones/cookies y servicio transaccional de email; ADR-001 ya aprobado.

## Estado contrastado con código — 2026-10-21

Existen las bases de aplicación y persistencia de usuarios/perfiles. Registro/login, sesiones de autenticación, recuperación, correos y control de acceso siguen pendientes.

Véase [[Registro de avances]] para evidencia, diferencias y límites de la validación.
