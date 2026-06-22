# Requerimentos Funcionales - El Jardín de tu Salud

## Módulo de Usuarios y Control de Acceso

- **FR-01:** Registro de usuarios con email, contraseña, nombre completo y teléfono de contacto.
- **FR-02:** Inicio de sesión mediante email/contraseña.
- **FR-03:** Recuperación de contraseña vía email con enlace temporal seguro.
- **FR-04:** Perfil de usuario con opción para editar datos personales, historial de compras y preferencias.
- **FR-05:** Roles de usuario:
  - **Cliente:** Compra productos, accede a cursos, recibe boletines.
  - **Administrador:** 
    - **Gestión de la plataforma:** Gestión completa de inventario, usuarios, cursos y pedidos. 
     - **Gestión de cursos:** Gestión de cursos, contenido y calendario de sesiones.

---

## Módulo de Catálogo Interactivo

- **FR-06:** Visualización de productos en formato grid/lista con paginación.

- **FR-07:** Filtros dinámicos por:

  - Categoría (Medicamentos, Plantas Medicinales, Snacks Saludables, Cursos).

  - Precio (rango).

  - Stock disponible.

- **FR-08:** Búsqueda predictiva por coincidencia de texto.

- **FR-09:** Vista detallada de producto con:

  - Imagen principal + galería de imágenes.

  - Descripción completa.

  - Ingredientes / composición.

  - Beneficios y propiedades.

  - Dosis o modo de uso sugerido.

  - Opiniones y calificaciones de otros usuarios.

  - Productos relacionados.

---

## Módulo de Inventario y Stock

- **FR-10:** Gestión de inventario por categorías:

  - **Medicamentos:** Control de lote, fecha de vencimiento, presentación (tabletas, jarabe, gotas).

  - **Plantas Medicinales:** Control de peso, presentación (fresca, seca, en polvo), origen.

  - **Snacks Saludables:** Control de fecha de caducidad, ingredientes alérgenos.

  - **Cursos:** Control de cupos disponibles por sesión/fecha.

- **FR-11:** Actualización automática de stock al realizar una compra.

- **FR-12:** Alertas de stock bajo.

- **FR-13:** Historial de movimientos de inventario (entradas, salidas, ajustes).

---

## Módulo de Métodos de Pago

- **FR-14:** Integración con pasarelas de pago:

  - Billetera digitale (MercadoPago).

- **FR-15:** Procesamiento de pagos con confirmación en tiempo real.

- **FR-16:** Historial de transacciones por usuario.

---

## Módulo de Cursos y Calendario

- **FR-17:** Catálogo de cursos con:

  - Título, descripción, instructor, duración, nivel (básico/intermedio/avanzado).

  - Precio (compra única) o suscripción .

  - Imagen promocional y trailer (video corto).

- **FR-18:** Sistema de calendario para:

  - Programación de sesiones en vivo (clases virtuales).

  - Reserva de cupos por sesión.

  - Recordatorios automáticos por email y/o notificaciones.

- **FR-19:** Contenido del curso estructurado en módulos:

  - Videos (reproducción de videos externos).

  - PDFs, documentos descargables.

- **FR-20:** Acceso a cursos comprados desde el panel de usuario.

---

## Módulo de Boletines Informativos

- **FR-21:** Suscripción a boletines informativos por email desde el sitio web.

- **FR-22:** Gestión de suscriptores (alta/baja manual o automática).

- **FR-23:** Creación y envío de boletines
  - Programación de envíos en fecha/hora específica.

- **FR-24:** Plantillas predefinidas para boletines (promociones, novedades, cursos).

- **FR-25:** Integración con servicios de email marketing (Mailchimp, SendGrid, etc.).

---

## Módulo de Administración y Reportes

- **FR-26:** Panel de administración con dashboard general (ventas, usuarios, inventario).

- **FR-27:** Gestión completa de productos (CRUD: Crear, Leer, Actualizar, Eliminar).

- **FR-28:** Gestión de pedidos con estados (pendiente, pagado, enviado, entregado, cancelado).

- **FR-29:** Generación de reportes:

  - Ventas diarias/semanales/mensuales.

  - Productos más vendidos.

  - Comportamiento de usuarios.

  - Rendimiento de cursos.

---

## Módulo de Notificaciones

- **FR-30:** Notificaciones por email para:

  - Confirmación de registro.

  - Confirmación de compra.

  - Recordatorio de sesión de curso.

  - Alerta de stock bajo.

  - Confirmación de suscripción a boletín.
