<div align="justify">

# Requerimientos Funcionales - El Jardin de tu Salud

## Proposito

Este documento define las funciones que debe ofrecer la plataforma de comercio electronico "El Jardin de tu Salud". Los requerimientos estan separados por modulos y relaciones, sin formato de tabla, para facilitar su lectura, trazabilidad y posterior implementacion.

La cantidad total de requerimientos funcionales se mantiene por debajo de 40. La plataforma no incluye cupones, pagos por PayPal, filtros especializados, foros, sesiones en vivo ni exportaciones de reportes en CSV o formatos similares. Los cursos se entregaran mediante contenido digital, principalmente videos embebidos de YouTube.

## Nota de alcance — decisiones del 2026-10-16

Las siguientes decisiones ajustan el alcance de la primera versión sin cambiar la redacción ni los identificadores de los requisitos funcionales:

- DEC-01: los cupones se difieren mediante [NFR-38](<../NFRs/Non-functional-requirements.md#nfr-38-cupones-de-descuento>); no son dependencia del checkout inicial.
- DEC-02: Google OAuth se difiere mediante [NFR-39](<../NFRs/Non-functional-requirements.md#nfr-39-autenticación-con-google>); se conservan FR-01 a FR-05 y el acceso convencional.
- DEC-03: se excluye el consumo offline de cursos completos. Se mantienen los materiales individuales descargables de FR-27 y FR-28.
- DEC-05: FR-07 permanece vigente, con búsqueda por coincidencia parcial o total y sin incorporar filtros especializados.

Resoluciones y trazabilidad en [DEC-01 a DEC-05](<../Reports/Management/Contradicciones y decisiones pendientes.md>). Son decisiones documentales de alcance, no funcionalidades implementadas o probadas.

## Actores

- **Cliente visitante:** Persona que navega el catalogo sin iniciar sesion. Puede consultar productos, cursos y contenido disponible, e iniciar el proceso de registro o compra.
- **Cliente registrado:** Persona autenticada que puede comprar productos, acceder a cursos comprados, administrar su perfil, consultar pedidos y recibir correos relacionados con su actividad.
- **Administrador:** Usuario interno responsable de gestionar productos, inventario, cursos, pedidos, usuarios, boletines, visualizaciones internas de informacion comercial y configuraciones operativas.
- **Pasarela de pago:** Mercado Pago como unico servicio externo autorizado para procesar pagos y devolver estados de transaccion.
- **Servicio de email:** Servicio externo o interno usado para enviar correos transaccionales, boletines y avisos operativos.
- **YouTube:** Plataforma externa usada para alojar y embeber videos de cursos dentro del sistema.

## Relaciones Generales Entre Modulos

- **Usuarios y catalogo:** El catalogo puede consultarse sin iniciar sesion, pero las compras, opiniones, cursos adquiridos, direcciones y preferencias de comunicacion deben quedar asociadas a una cuenta de cliente registrado.
- **Catalogo, inventario y carrito:** El catalogo muestra disponibilidad segun el inventario; el carrito valida stock antes de permitir la compra; el inventario se actualiza cuando el pedido avanza segun las reglas de negocio.
- **Carrito, pagos y pedidos:** El carrito prepara la compra; Mercado Pago confirma, rechaza o deja pendiente la transaccion; pedidos conserva el estado operativo y administrativo de la compra.
- **Cursos, pagos y usuarios:** El acceso a cursos se habilita para el usuario despues de una compra aprobada o por asignacion administrativa autorizada. El contenido de video se muestra embebido desde YouTube.
- **Boletines, usuarios y email:** Las suscripciones a boletines se vinculan a correos o cuentas de usuario y se gestionan mediante el servicio de email definido.
- **Administracion y visualizacion operativa:** El panel administrativo consume datos de usuarios, ventas, inventario, cursos, pedidos y boletines para operar el negocio, sin requerir exportaciones CSV o similares.

---

## Modulo 1: Usuarios y Control de Acceso

### FR-01: Registro de usuarios

El sistema debe permitir que un cliente cree una cuenta con nombre completo, correo electronico, telefono y contraseña. Debe validar que el correo tenga formato correcto, que no exista una cuenta duplicada con el mismo email y que la contraseña cumpla reglas minimas de seguridad. Al completar el registro, el sistema debe crear un perfil de cliente y enviar un correo de confirmacion.

**Actores:** Cliente visitante, servicio de email.

**Relaciones:** Perfil de usuario, carrito persistente, pedidos, boletines y seguridad.

### FR-02: Inicio y cierre de sesion

El sistema debe permitir que clientes y administradores inicien sesion con correo y contraseña. La autenticacion debe crear una sesion valida para acceder a funciones privadas como perfil, historial de compras, cursos adquiridos y panel administrativo. El sistema tambien debe permitir cerrar sesion de forma clara y segura.

**Actores:** Cliente registrado, administrador.

**Relaciones:** Usuarios, cursos, pedidos y administracion.

### FR-03: Recuperacion de contraseña por email

El sistema debe permitir solicitar recuperacion de contraseña mediante correo electronico. Debe generar un enlace temporal, seguro y de un solo uso. Despues de actualizar la contraseña, el enlace debe quedar invalidado y el usuario debe recibir un correo que confirme el cambio.

**Actores:** Cliente registrado, administrador, servicio de email.

**Relaciones:** Seguridad, control de acceso y gestion de usuarios.

### FR-04: Gestion de perfil de cliente

El sistema debe permitir que el cliente consulte y edite sus datos personales, telefono, direcciones, preferencias de comunicacion, historial de compras, cursos comprados y suscripciones a boletines. Los cambios sensibles, como correo o contraseña, deben requerir validacion adicional.

**Actores:** Cliente registrado.

**Relaciones:** Pedidos, cursos, boletines, carrito y correos transaccionales.

### FR-05: Roles y permisos

El sistema debe manejar roles diferenciados para cliente y administrador. El cliente solo puede acceder y modificar su propia informacion; el administrador puede gestionar productos, inventario, pedidos, cursos, usuarios, boletines y visualizaciones internas de informacion comercial. Cada accion protegida debe validar permisos antes de ejecutarse.

**Actores:** Cliente registrado, administrador.

**Relaciones:** Todos los modulos administrativos y operaciones sensibles.

---

## Modulo 2: Catalogo de Productos y Cursos

### FR-06: Visualizacion del catalogo

El sistema debe mostrar productos fisicos y cursos en una vista organizada con imagen, nombre, categoria, precio, disponibilidad y datos relevantes para la decision de compra. La vista debe permitir navegar de forma comoda entre medicamentos herbales, plantas medicinales, suplementos, snacks saludables y cursos, sin filtros especializados.

**Actores:** Cliente visitante, cliente registrado.

**Relaciones:** Inventario, administracion de productos, cursos y reglas de publicacion.

### FR-07: Busqueda por texto en coincidencia

El sistema debe permitir buscar productos y cursos mediante texto libre. La busqueda debe funcionar por coincidencia parcial o total sobre campos visibles como nombre, descripcion, categoria, ingredientes, beneficios, instructor o titulo del curso. No se deben incluir filtros especializados por precio, stock, nivel, categoria u otros criterios avanzados.

**Actores:** Cliente visitante, cliente registrado.

**Relaciones:** Catalogo, cursos y experiencia de compra.

### FR-08: Detalle de producto fisico

El sistema debe mostrar una pagina detallada para cada producto fisico. Debe incluir imagen principal, galeria, descripcion, ingredientes o composicion, beneficios, propiedades, modo de uso sugerido, advertencias, precio, stock disponible y productos relacionados. En productos de salud natural, la informacion debe redactarse de forma responsable y sin promesas medicas no sustentadas.

**Actores:** Cliente visitante, cliente registrado.

**Relaciones:** Inventario, carrito, administracion de productos y contenido legal.

### FR-09: Detalle de curso

El sistema debe mostrar la informacion completa de cada curso: titulo, descripcion, instructor, duracion estimada, nivel, precio, temario, imagen promocional y videos embebidos de YouTube cuando correspondan. El usuario debe entender que el curso se consume como contenido digital embebido, sin sesiones en vivo ni foros dentro de la plataforma.

**Actores:** Cliente visitante, cliente registrado, YouTube.

**Relaciones:** Cursos, carrito, pagos y acceso a contenido.

### FR-10: Opiniones y calificaciones

El sistema debe permitir que clientes que hayan comprado un producto o curso publiquen una calificacion y comentario. El administrador debe poder revisar, ocultar o eliminar opiniones que incumplan reglas de convivencia, contengan informacion falsa o afecten la confianza de la plataforma.

**Actores:** Cliente registrado, administrador.

**Relaciones:** Usuarios, catalogo, pedidos y administracion.

---

## Modulo 3: Carrito y Checkout

### FR-11: Carrito de compras

El sistema debe permitir agregar, quitar y modificar cantidades de productos fisicos y cursos desde el catalogo o desde la vista de detalle. El carrito debe mostrar subtotales, disponibilidad y total estimado. Para usuarios autenticados, el carrito debe poder conservarse entre sesiones.

**Actores:** Cliente visitante, cliente registrado.

**Relaciones:** Catalogo, inventario, cursos, usuarios y checkout.

### FR-12: Validacion de disponibilidad antes del pago

Antes de confirmar la compra, el sistema debe validar stock de productos fisicos. Si un articulo deja de estar disponible, el sistema debe informar el cambio, ajustar el carrito y evitar que se genere una compra inconsistente. Los cursos digitales no deben manejar cupos, salvo que el negocio defina una restriccion administrativa manual fuera del flujo de compra.

**Actores:** Cliente visitante, cliente registrado.

**Relaciones:** Inventario, cursos, pedidos y pagos.

### FR-13: Checkout de compra

El sistema debe guiar al cliente por un proceso de checkout donde pueda revisar productos, cursos, cantidades, subtotales, costos de envio cuando apliquen y total final. Debe permitir capturar o seleccionar direccion de entrega para productos fisicos y confirmar la cuenta donde se habilitara el acceso a cursos digitales.

**Actores:** Cliente registrado.

**Relaciones:** Carrito, pedidos, pagos, usuarios, inventario y cursos.

---

## Modulo 4: Pagos y Transacciones

### FR-14: Integracion con Mercado Pago

El sistema debe integrarse con Mercado Pago como unica pasarela de pago. Debe enviar monto, moneda, identificador de orden y datos necesarios para procesar la transaccion de forma segura sin almacenar datos sensibles de tarjetas en la plataforma.

**Actores:** Cliente registrado, Mercado Pago.

**Relaciones:** Checkout, pedidos y seguridad.

### FR-15: Confirmacion y rechazo de pagos

El sistema debe recibir y procesar estados de pago aprobados, rechazados, cancelados o pendientes desde Mercado Pago. Cuando el pago sea aprobado, debe marcar el pedido como pagado, descontar inventario cuando aplique, habilitar cursos comprados y enviar el correo correspondiente al cliente. Si el pago falla, debe permitir reintentar sin duplicar pedidos ni descuentos de stock.

**Actores:** Cliente registrado, Mercado Pago, servicio de email.

**Relaciones:** Pedidos, inventario, cursos, carrito y correos transaccionales.

### FR-16: Historial de transacciones

El sistema debe permitir que el cliente consulte pagos realizados, fecha, estado, monto, metodo utilizado y pedido asociado. El administrador debe poder consultar transacciones por cliente, fecha, estado o referencia externa para fines de soporte y conciliacion dentro del panel, sin requerir exportaciones en CSV o formatos similares.

**Actores:** Cliente registrado, administrador.

**Relaciones:** Pedidos, soporte y auditoria.

---

## Modulo 5: Pedidos, Envios y Postventa

### FR-17: Creacion de pedidos

El sistema debe crear un pedido a partir del checkout con identificador unico, cliente, articulos comprados, precios al momento de compra, direccion, metodo de pago y estado inicial. El pedido debe conservar la informacion historica necesaria para soporte, auditoria y visualizacion operativa.

**Actores:** Cliente registrado.

**Relaciones:** Carrito, pagos, inventario y cursos.

### FR-18: Gestion de estados de pedido

El sistema debe manejar estados como pendiente, pagado, en preparacion, enviado, entregado, cancelado y reembolsado. Cada cambio debe registrar fecha, responsable y motivo cuando aplique. Los cambios relevantes deben generar correos al cliente para mantenerlo informado.

**Actores:** Administrador, cliente registrado, servicio de email.

**Relaciones:** Pagos, envios, inventario y correos transaccionales.

### FR-19: Seguimiento de envio

Para productos fisicos, el sistema debe permitir registrar paqueteria, numero de guia, fecha estimada de entrega y notas internas. El cliente debe poder consultar esta informacion desde su perfil y recibirla por correo cuando el pedido sea enviado.

**Actores:** Administrador, cliente registrado, servicio de email.

**Relaciones:** Pedidos, perfil de usuario y gestion administrativa.

### FR-20: Cancelaciones y reembolsos

El sistema debe permitir cancelar pedidos segun reglas de negocio. Si el pedido ya fue pagado, debe registrar el estado de reembolso y, cuando corresponda, reponer inventario. La accion debe quedar registrada para auditoria y soporte.

**Actores:** Administrador, Mercado Pago.

**Relaciones:** Pagos, inventario, cursos y pedidos.

---

## Modulo 6: Inventario y Stock

### FR-21: Gestion de inventario por categoria

El sistema debe permitir administrar inventario de medicamentos herbales, plantas medicinales, suplementos y snacks saludables. Cada categoria debe manejar atributos propios: lote, vencimiento y presentacion para medicamentos; peso, origen y presentacion para plantas; ingredientes, alergenos y caducidad para snacks.

**Actores:** Administrador.

**Relaciones:** Catalogo, carrito, pedidos y visualizacion operativa.

### FR-22: Actualizacion automatica de stock

El sistema debe descontar stock cuando una compra de productos fisicos sea aprobada y reponerlo cuando una cancelacion o reembolso lo requiera. La actualizacion debe evitar ventas superiores a la disponibilidad real y debe ejecutarse de forma consistente con el estado del pedido.

**Actores:** Administrador, Mercado Pago.

**Relaciones:** Pagos, pedidos y carrito.

### FR-23: Alertas de stock bajo y vencimientos por email

El sistema debe detectar productos con stock bajo, productos vencidos o proximos a vencer. Estas alertas deben mostrarse en el panel administrativo y enviarse por email a los responsables definidos.

**Actores:** Administrador, servicio de email.

**Relaciones:** Inventario, administracion y gestion operativa.

### FR-24: Historial de movimientos de inventario

El sistema debe registrar entradas, salidas, ajustes manuales, devoluciones y descuentos por venta. Cada movimiento debe incluir fecha, responsable, motivo, cantidad anterior y cantidad resultante para permitir trazabilidad y auditoria.

**Actores:** Administrador.

**Relaciones:** Pedidos, auditoria y administracion.

### FR-25: Aviso de regreso a stock por email

El sistema debe permitir que un cliente solicite recibir un correo cuando un producto agotado vuelva a estar disponible. Al reponer inventario, el sistema debe identificar a los interesados y enviar el aviso respetando sus preferencias de comunicacion.

**Actores:** Cliente registrado, servicio de email.

**Relaciones:** Catalogo, inventario, perfil de usuario y email.

## Modulo 7: Cursos con Videos Embebidos

### FR-26: Gestion de cursos

El sistema debe permitir crear, editar, publicar, despublicar y eliminar cursos. Cada curso debe incluir descripcion, instructor, precio, nivel, duracion estimada, imagen, temario, enlaces o identificadores de videos de YouTube y estado de publicacion. Solo los cursos publicados deben aparecer en el catalogo.

**Actores:** Administrador, YouTube.

**Relaciones:** Catalogo, carrito, pagos, usuarios y visualizacion operativa.

### FR-27: Acceso a contenido comprado

El sistema debe habilitar el contenido del curso en el perfil del cliente despues de confirmar el pago. El cliente debe poder consultar videos embebidos de YouTube, documentos, enlaces y materiales descargables segun las reglas definidas para cada curso.

**Actores:** Cliente registrado, YouTube.

**Relaciones:** Pagos, usuarios, perfil y gestion de cursos.

### FR-28: Materiales descargables de curso

El sistema debe permitir que el administrador adjunte documentos o enlaces complementarios a un curso. El cliente solo debe acceder a esos materiales cuando haya comprado el curso o cuando el administrador le haya concedido acceso.

**Actores:** Administrador, cliente registrado.

**Relaciones:** Cursos, usuarios y seguridad.

---

## Modulo 8: Boletines y Email Marketing

### FR-29: Suscripcion a boletines

El sistema debe permitir que visitantes y clientes registrados se suscriban a boletines mediante correo electronico. Debe validar consentimiento explicito y, si se define doble confirmacion, enviar un correo para activar la suscripcion.

**Actores:** Cliente visitante, cliente registrado, servicio de email.

**Relaciones:** Usuarios, preferencias de comunicacion y marketing.

### FR-30: Gestion de suscriptores

El sistema debe permitir altas, bajas, actualizacion de preferencias y consulta del estado de suscripcion. Cada boletin debe incluir una opcion clara de baja para que el usuario pueda dejar de recibir comunicaciones comerciales.

**Actores:** Cliente registrado, administrador, servicio de email.

**Relaciones:** Privacidad, usuarios y email marketing.

### FR-31: Creacion y programacion de boletines

El sistema debe permitir al administrador crear boletines con asunto, contenido, imagenes, enlaces, audiencia objetivo y fecha de envio. Tambien debe permitir programar envios y revisar el contenido antes de enviarlo.

**Actores:** Administrador, servicio de email.

**Relaciones:** Catalogo, cursos, comunicaciones comerciales y servicio de email.

### FR-32: Integracion con servicio de email

El sistema debe integrarse con un proveedor de email, como Mailchimp, SendGrid u otro servicio definido. Debe permitir enviar correos transaccionales, boletines, recuperacion de contraseña y alertas administrativas, manteniendo registro basico del envio para soporte.

**Actores:** Servicio de email, administrador.

**Relaciones:** Usuarios, pagos, pedidos, cursos, inventario y boletines.

---

## Modulo 9: Administracion y Visualizacion Operativa

### FR-33: Dashboard administrativo

El sistema debe mostrar un panel general con ventas, pedidos recientes, usuarios nuevos, productos con bajo stock, cursos activos y alertas operativas. La informacion debe ayudar al administrador a priorizar acciones diarias dentro de la plataforma.

**Actores:** Administrador.

**Relaciones:** Pedidos, inventario, cursos, usuarios y visualizacion operativa.

### FR-34: Gestion administrativa de productos, cursos y usuarios

El sistema debe permitir al administrador crear, consultar, actualizar y eliminar productos y cursos, asi como consultar usuarios, revisar historial de compras, cambiar roles permitidos y bloquear cuentas cuando exista una razon operativa o de seguridad.

**Actores:** Administrador.

**Relaciones:** Catalogo, cursos, inventario, usuarios, seguridad y auditoria.

### FR-35: Gestion administrativa de pedidos

El sistema debe permitir buscar, consultar y actualizar pedidos por estado, fecha, cliente, monto o metodo de pago dentro del panel administrativo. Tambien debe permitir registrar notas internas, datos de envio y acciones postventa sin perder trazabilidad.

**Actores:** Administrador.

**Relaciones:** Pedidos, pagos, envios y soporte.

### FR-36: Visualizacion operativa y comercial

El sistema debe mostrar informacion de ventas diarias, semanales y mensuales; productos mas vendidos; comportamiento de clientes; rendimiento de cursos; movimientos de inventario; y estados de pedidos dentro del panel administrativo. Esta informacion debe consultarse en pantalla y no debe requerir exportacion en CSV, Excel, PDF u otros formatos similares.

**Actores:** Administrador.

**Relaciones:** Ventas, pedidos, pagos, cursos, inventario, usuarios y decisiones de negocio.

</div>
