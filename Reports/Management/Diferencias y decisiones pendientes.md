# Conflictos, trazabilidad y decisiones pendientes

Referencia: 14 de octubre de 2026. Revisión documental: 16 de octubre de 2026.

Se revisaron todos los archivos existentes de BRs, FRs, NFRs, URs, UHs, GUIs y los README de documentación y backend. La rama actual contiene arquitectura, ADR, planificación y trazabilidad en Reports/. Se integran aquí las decisiones anteriores y DEC-01 a DEC-05; el diseño global sigue propuesto, con implementación parcial de la base técnica y persistencia de usuarios/perfiles verificada el 2026-10-21. Los BR y HU originales permanecen intactos. El 2026-10-16 se aprobaron [DEC-01 a DEC-05](<Contradicciones y decisiones pendientes.md>): UR-03 se actualiza y se agregan NFR-38/39 y notas de alcance. Estas resoluciones no acreditan funcionalidades implementadas. Los demás conflictos se conservan sin resolver automáticamente.

## Conflictos encontrados

| Tema | Evidencia original | Tratamiento documental |
| :--- | :--- | :--- |
| Stack | NFR-25 refiere React/Vue, Node.js Express/Springboot y hosting orientativo. | ADR-001 registra Python/FastAPI y React según decisión confirmada; se conserva NFR-25 hasta conciliar. Despliegue pendiente. |
| Cupones | BR-04, alcance BR, BR-12, HU-05, GUIs y NFR-05/23/27 los incluyen; propósito FR los excluye. | **Resuelto por DEC-01 y DEC-04:** cupones y componente visual diferidos mediante NFR-38; no bloquean la primera versión ni se incorporan automáticamente al Sprint 06. BR y HU se conservan. |
| Pasarelas | BR contempla PayPal futuro y NFR-06 lo menciona; FR excluye PayPal y FR-14 exige Mercado Pago únicamente. | Integración futura solo Mercado Pago en esta etapa. Conciliar alcance histórico. |
| Cursos | BR-03 y alcance BR incluyen sesiones en vivo, calendario y cupos; FR-09/12 exige contenido digital sin sesiones en vivo y sin cupos ordinarios. | No diseñar calendario o cupos sin validación. |
| Descargas | UR-03 pedía cursos sin conexión; FR-09/27 usa YouTube embebido y FR-28 materiales descargables. | **Resuelto por DEC-03:** UR-03 exige acceso en línea; se elimina consumo offline de cursos completos y se mantienen materiales individuales descargables. |
| Acceso manual | BR-08 y FR-27/28 permiten asignación administrativa; la propuesta vincula inscripciones a compras confirmadas. | Exigir compra confirmada para acceso por venta y preservar la excepción manual; validación final del modelo pendiente. |
| Snacks | BR, FR-06/21 y GUIs incluyen snacks/galletas; la lista propuesta de especializaciones carece de equivalente. | Mantener el requisito; no inventar tabla o reasignarlos a suplementos. Cobertura pendiente. |
| Visitantes | BR-06 exige cuenta para comprar; la solicitud mantiene compras como invitado entre pendientes. | Conservar compra registrada como regla vigente; compra invitada requerirá aprobación expresa. |
| Búsqueda y filtros | BR alcance y NFR-08 mencionan filtros; FR-07 excluye filtros especializados. | **Resuelto por DEC-05:** FR-07 permanece sin cambios, con coincidencia parcial o total; no se añaden filtros especializados. |
| Autenticación Google | HU-02 pide registro con Google; FR-01/02 describe correo y contraseña. | **Resuelto por DEC-02:** Google OAuth diferido mediante NFR-39; acceso convencional vigente. HU-02 y FR-01 a FR-05 se conservan. |

## Decisiones pendientes de validación

- Mecanismo de autenticación y almacenamiento de sesiones; diseño de recuperación de contraseña. La prioridad de Google ya está resuelta por DEC-02: diferido.
- Requisitos exactos de perfiles y datos personales, conservando los campos ya solicitados en FR-01/04.
- Variantes y presentaciones de productos; cobertura de snacks y lotes/vencimientos de FR-21/23.
- Expiración de reservas de inventario y tratamiento de pagos tardíos.
- Reglas de redondeo y aplicación de descuentos; precisión, moneda, impuestos y cargos.
- Inscripciones múltiples, cupos y fechas de cursos; acceso manual y tratamiento de cancelaciones/reembolsos.
- Compras como invitado: mientras no haya cambio aprobado, rige BR-06.
- Requisitos de entrega, envío o facturación: FR-13/17/19 y GUI ya piden dirección, seguimiento y factura; falta precisar reglas, no eliminarlos.
- Infraestructura de despliegue.
- Almacenamiento de imágenes y archivos, respetando requisitos de multimedia y materiales.
- Validaciones comerciales y regulatorias aplicables a medicamentos.
- Cardinalidades finales de categorías, carritos, inventario y asignación de cursos; restricciones de especialización e idempotencia.
- Políticas de retención, anonimización, bajas y auditoría.

## Brechas del modelo y del plan

La propuesta v0.1 no modela completamente opiniones (FR-10), avisos de stock (FR-25), boletines y email (FR-29 a FR-32), materiales de cursos (FR-28), auditoría general, historial de estados, lotes/vencimientos ni recuperación de contraseña. Tampoco implica que el dashboard y visualizaciones FR-33 a FR-35 estén resueltos. Deben desglosarse y priorizarse sin alterar requisitos originales.

Consultar [ADR-001](<../Architecture/ADR/ADR-001 - Backend y persistencia.md>), [ADR-002](<../Architecture/ADR/ADR-002 - Modelo lógico relacional v0.1.md>), [modelo lógico](<../Architecture/Database/Modelo lógico relacional v0.1.md>), [reglas por módulo](<../Architecture/Reglas del backend.md>) y [plan](<Plan de sprints.md>).

Fuentes originales: [BR](<../../BRs/business-requirements.md>), [FR](<../../FRs/functional-requirements.md>), [NFR](<../../NFRs/Non-functional-requirements.md>), [UR](<../../URs/User-requirements.md>), [HU](<../../UHs/User-stories.md>), [GUI](<../../GUIs/GUI-mockups.md>).

## Estado contrastado con código — 2026-10-21

La revisión del código detectó diferencias en plantilla de entorno, dependencias, nombres de proyecto/base de pruebas y cobertura del perfil. Su detalle está en Registro de avances; no se corrigen requisitos ni se aprueban decisiones pendientes automáticamente.

Véase [[Registro de avances]] para evidencia, diferencias y límites de la validación.
