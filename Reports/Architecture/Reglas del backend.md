# Reglas técnicas por módulo

Referencia: 14 de octubre de 2026. **Reglas para implementación futura; no funcionalidades implementadas.** Stack en [ADR-001](<ADR/ADR-001 - Backend y persistencia.md>); propuesta de datos en [ADR-002](<ADR/ADR-002 - Modelo lógico relacional v0.1.md>).

## Identidad y autenticación

Roles iniciales ADMIN y CLIENT, con permisos fijos. El backend validará rol y propiedad de cada recurso protegido. Correos únicos sin distinción de mayúsculas y contraseñas con hash seguro. No se decide JWT, cookies ni almacenamiento de sesiones; `user_sessions` es condicional. FR-01 ya pide nombre completo, email, teléfono y contraseña; FR-04 incluye direcciones y preferencias. Su distribución y tratamiento exactos permanecen pendientes. HU-02 se conserva; Google OAuth queda diferido fuera de la primera versión mediante [NFR-39](<../../NFRs/Non-functional-requirements.md#nfr-39-autenticación-con-google>) y [DEC-02](<../Management/Contradicciones y decisiones pendientes.md#dec-02>). Se mantiene registro e inicio de sesión convencional sin cambiar FR-01 a FR-05.

## Catálogo y descuentos

Cursos y productos físicos comparten `products` y carrito. El tipo especializado será exclusivo. El backend consultará precios vigentes y calculará cantidades, disponibilidad, descuentos porcentuales y totales; no confiará en importes enviados por React. Los descuentos históricos se conservarán en `order_items`. Redondeo, orden de aplicación, impuestos y cargos requieren definición. Los cupones quedan diferidos por DEC-01 y [NFR-38](<../../NFRs/Non-functional-requirements.md#nfr-38-cupones-de-descuento>); checkout y pagos iniciales no dependerán de su aplicación ni administración. DEC-04 difiere el componente visual. No se incorporarán automáticamente al Sprint 06. La búsqueda conserva FR-07 sin cambios: coincidencia parcial o total, sin filtros especializados (DEC-05).

## Pedidos, inventario y pagos

La creación del pedido y sus líneas requiere una transacción. Reservar, liberar, descontar o reponer inventario requiere transacciones y control de concurrencia para impedir sobreventa. Una reserva no equivale a una venta definitiva. Expiración de reservas, estados y transiciones detalladas deben validarse, incluyendo cancelaciones, reembolsos y pagos tardíos.

React no determina la aprobación de pagos. Los webhooks de Mercado Pago requerirán verificación de autenticidad y comprobación del estado del pago con el proveedor, además de correspondencia de pedido, referencia, moneda e importe calculado por backend. Los detalles de integración deberán verificarse contra la documentación oficial al implementarlos; este documento no prescribe un protocolo concreto.

Los eventos duplicados y reintentos no deberán duplicar pedidos, movimientos ni inscripciones. La deduplicación y la transición de estado deberán ser atómicas junto con sus efectos locales; se deberá definir la clave de idempotencia y la referencia externa única. La confirmación válida coordinará pedido pagado, movimiento de stock e inscripción cuando corresponda. Fallas externas requerirán conciliación, sin asumir atomicidad entre PostgreSQL y Mercado Pago. El fallo de email no deberá deshacer una compra confirmada (NFR-30). No se almacenarán datos sensibles de tarjetas.

## Cursos e historia

Los cursos podrán venderse en el mismo carrito de productos. Según [DEC-03](<../Management/Contradicciones y decisiones pendientes.md#dec-03>), UR-03 exige acceso en línea desde el perfil tras confirmar el pago; se excluye la descarga de cursos completos para consumo offline. Se mantienen materiales individuales descargables conforme a FR-27/28. Según [DEC-03](<../Management/Contradicciones y decisiones pendientes.md#dec-03>), UR-03 exige acceso en línea desde el perfil tras confirmar el pago; se excluye la descarga de cursos completos para consumo offline. Se mantienen materiales individuales descargables conforme a FR-27/28. Las inscripciones por venta deberán corresponder a una compra confirmada del curso para ese cliente. Se preserva el acceso administrativo autorizado de BR-08 y FR-27/28 como excepción pendiente de modelado y auditoría. No se resuelven inscripciones múltiples, cupos ni fechas; FR-12 actualmente excluye cupos en el flujo ordinario.

Las bajas de cuentas, productos o cursos deberán conservar la integridad histórica de pedidos, pagos y movimientos. No se interpretará «eliminar» como borrar en cascada registros comerciales. La política concreta de retención, anonimización y revocación de acceso queda por acordar.

Fuentes: [BR](<../../BRs/business-requirements.md>) BR-06 a BR-11; [FR](<../../FRs/functional-requirements.md>) FR-01 a FR-05, FR-11 a FR-28 y FR-34; [NFR](<../../NFRs/Non-functional-requirements.md>) NFR-01 a NFR-06, NFR-13 y NFR-26 a NFR-30. Véanse [conflictos](<../Management/Diferencias y decisiones pendientes.md>) y [planificación](<../Management/Plan de sprints.md>).
