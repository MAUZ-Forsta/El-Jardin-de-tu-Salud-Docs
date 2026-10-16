# Modelo lógico relacional v0.1

**DISEÑO PROPUESTO — PENDIENTE DE VALIDACIÓN FINAL**. Referencia: 14 de octubre de 2026.

Este modelo desarrolla [ADR-002](<../ADR/ADR-002 - Modelo lógico relacional v0.1.md>). Las cardinalidades son propuestas, no requisitos nuevos aprobados. No representa tablas creadas.

| Relación | Cardinalidad y significado propuestos |
| :--- | :--- |
| users → client_profiles | 1 a 0..1; cada perfil pertenece a un usuario. Para CLIENT se espera un perfil al registrarse (FR-01); ADMIN puede no tenerlo. |
| users → user_sessions | 1 a 0..N; cada sesión pertenece a un usuario. Entidad condicionada a la estrategia de autenticación. |
| categories → products | 1 a 0..N; cada producto tendría una categoría. La multiplicidad de categorías está por validar. |
| products → plants / supplements / medicines / courses | 1 a 0..1 por especialización; cada fila especializada corresponde a un producto. Exactamente una especialización en total por producto; falta resolver snacks. |
| users → carts | 1 a 0..N; cada carrito persistente propuesto pertenece a un usuario. Carritos de visitante, fusión y unicidad de carrito activo por definir. |
| carts → cart_items | 1 a 0..N; cada ítem pertenece a un carrito y referencia exactamente un producto. |
| products → cart_items | 1 a 0..N; unicidad propuesta de producto por carrito, sujeta a variantes. |
| users → orders | 1 a 0..N; cada pedido pertenece a un usuario registrado conforme a BR-06. |
| orders → order_items | 1 a 1..N; cada línea pertenece a un pedido y referencia un producto, conservando su copia histórica. |
| products → order_items | 1 a 0..N; no eliminar en cascada el historial de ventas. |
| orders → payments | 1 a 0..N; cada intento de pago pertenece a un pedido, permitiendo reintentos trazables. |
| products → inventory | 1 a 0..1; inventario para productos físicos, no para cursos digitales. Lotes o variantes podrían cambiar esta cardinalidad. |
| inventory → inventory_movements | 1 a 0..N; cada movimiento corresponde a un registro de inventario. |
| order_items → inventory_movements | 0..1 a 0..N; un movimiento puede referenciar una línea de pedido; ajustes manuales no requieren una. |
| users → inventory_movements | 0..1 a 0..N como responsable humano; movimientos automáticos requieren identificar origen y causa. |
| users → course_enrollments | 1 a 0..N; cada inscripción pertenece a un cliente. |
| courses → course_enrollments | 1 a 0..N; cada inscripción corresponde a un curso. |
| order_items → course_enrollments | 0..1 a 0..N; las inscripciones por venta requieren línea de curso y pago confirmado. Multiplicidad por compra sin decidir. |

Las relaciones con `course_enrollments` no fijan unicidad cliente/curso ni cupos, fechas o cantidades comprables. BR-08 y FR-27/28 permiten acceso manual por administrador: la vinculación opcional a una línea preserva esa excepción, pero su autorización, motivo y trazabilidad necesitan diseño final. Una inscripción por venta no podrá usar esta excepción para omitir el pago.

Las FK no bastan para comprobar que una línea corresponde al curso inscrito, que el pedido pertenece al inscrito o que un pago está aprobado: deben definirse y verificarse estas invariantes transaccionalmente. Asimismo deben validarse cantidades positivas, porcentajes entre 0 y 100, importes no negativos, referencias externas únicas según proveedor y alcance de idempotencia; las restricciones concretas quedan pendientes.

Ver [reglas de pagos, inventario y cursos](<../Reglas del backend.md>) y [brechas de cobertura y decisiones pendientes](<../../Management/Diferencias y decisiones pendientes.md>).
