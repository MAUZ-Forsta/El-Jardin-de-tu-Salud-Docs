---
tipo: estado-proyecto
estado: implementacion-parcial
actualizado: 2026-11-18
---
# Estado del proyecto

## Avance de catálogo — 2026-11-18

En la rama `feat/product-catalog` del backend existe un catálogo de productos físicos con migración versionada, listado/detalle público, búsqueda parcial, paginación y edición protegida para ADMIN. La migración se aplicó **solo** a `tia_richrad_test`; 54 pruebas aprobaron, incluido el bloque anterior de autenticación. La integración a `dev`, el adaptador React y el inventario siguen pendientes. El contrato y las decisiones están en [[Catálogo de productos]].

La disponibilidad de stock aún se devuelve como desconocida. La publicación de un producto no autoriza venderlo; carrito y pedidos deben validar precio y stock en backend. Se mantienen las decisiones DEC-01 a DEC-05 y el objetivo de entrega existente.

## Revisión histórica — 2026-10-21

Backend revisado en c63fe97: base FastAPI, CORS, configuración, errores, SQLAlchemy y migraciones users/client_profiles presentes. Autenticación y módulos comerciales pendientes. No se acredita despliegue ni aplicación de migraciones a PostgreSQL.

Sprint 01 parcialmente avanzado; ningún sprint declarado completo. Se conservan entrega objetivo 2026-12-02 y capacidad compartida de 17 horas semanales. DEC-01 a DEC-05 siguen vigentes.

[[Registro de avances]] · [[Roadmap]] · [[Trazabilidad - Sprint 01]]
