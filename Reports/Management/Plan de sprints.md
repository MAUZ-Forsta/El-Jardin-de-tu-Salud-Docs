# Planificación del backend

Referencia: 14 de octubre de 2026. **Plan previsto; no evidencia de sprints completados.**

Fecha objetivo de entrega: **2 de diciembre de 2026**. Capacidad aproximada: **17 horas semanales compartidas entre frontend, backend, pruebas, documentación y despliegue**; no son 17 horas exclusivas para backend ni por persona.

| Sprint | Distribución conservada | Dependencias por resolver |
| :--- | :--- | :--- |
| 01 | Configuración, persistencia, usuarios y autenticación convencional; Google OAuth excluido del alcance inicial (DEC-02). | Estrategia de autenticación, sesiones y perfil; validar modelo antes de migraciones. |
| 02 | Catálogo y especializaciones de productos físicos; búsqueda por coincidencia parcial y total conforme a FR-07 (DEC-05). | Snacks, variantes, presentaciones y requisitos de medicamentos. |
| 03 | Carrito y pedidos, sin aplicación ni administración de cupones (DEC-01). | Históricos, descuentos, envío y compra registrada conforme a BR-06. |
| 04 | Mercado Pago e inventario; sin lógica de cupones en el cálculo inicial de pagos (DEC-01). | Verificación, idempotencia, concurrencia, reservas y conciliación. |
| 05 | Cursos e inscripciones: acceso en línea; sin consumo offline de cursos completos; mantener materiales individuales descargables (DEC-03). | Multiplicidad, acceso administrativo, cupos y fechas sin resolver. |
| 06 | P1, QA y entrega, incluyendo seguridad y despliegue; sin incorporación automática de cupones ni Google OAuth (DEC-01/02). | Infraestructura, almacenamiento y validación de flujos críticos. |

La distribución no fija duraciones ni fechas individuales no aprobadas. Entre la referencia y el objetivo hay siete semanas, aproximadamente 119 horas compartidas; no es una estimación de esfuerzo ni garantía de cobertura. Las dependencias pendientes y las brechas de requisitos deben revisarse antes de comprometer alcance detallado. Cupones y Google OAuth permanecen diferidos, sujetos a planificación y tiempo disponible; no se comprometen en Sprint 06. Véanse [DEC-01 a DEC-05](<Contradicciones y decisiones pendientes.md>) y [NFR-38/39](<../../NFRs/Non-functional-requirements.md>). DEC-04 difiere el componente visual de cupones junto con su funcionalidad.

La verificación futura deberá cubrir autenticación y permisos, importes históricos, no sobreventa bajo concurrencia, eventos duplicados y reintentos, pagos rechazados o pendientes, cancelaciones/reembolsos y acceso a cursos solo con autorización válida. No se crean pruebas de producción en esta tarea documental.

Referencias: [ADR-001](<../Architecture/ADR/ADR-001 - Backend y persistencia.md>), [ADR-002](<../Architecture/ADR/ADR-002 - Modelo lógico relacional v0.1.md>), [reglas](<../Architecture/Reglas del backend.md>) y [conflictos, pendientes y brechas](<Diferencias y decisiones pendientes.md>).
