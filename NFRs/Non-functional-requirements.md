<div align="justify">

# Requisitos No Funcionales - El Jardin de tu Salud

## Proposito

Este documento define los atributos de calidad que debe cumplir la plataforma "El Jardin de tu Salud". Los requisitos no funcionales estan organizados por modulos o areas transversales, sin formato de tabla, e indican su relacion con los modulos funcionales.

## Relaciones Generales

- **Seguridad y usuarios:** La proteccion de cuentas, contraseñas, roles y datos personales sostiene el registro, inicio de sesion, compras, cursos y administracion.
- **Rendimiento y catalogo:** La experiencia de busqueda, filtros, detalle de productos y checkout depende de tiempos de respuesta estables.
- **Disponibilidad y pagos:** El proceso de compra debe mantenerse disponible y recuperarse correctamente ante errores de pasarela, red o servicios externos.
- **Usabilidad y conversion:** Una interfaz clara, accesible y responsive ayuda a reducir abandono de carrito y mejora la conversion de visitantes a compradores.
- **Mantenibilidad y administracion:** Una arquitectura ordenada permite evolucionar productos, cursos, inventario, pedidos, boletines y reportes sin romper modulos existentes.
- **Email y soporte:** Los correos transaccionales, comerciales y operativos deben ser confiables, trazables y respetar las preferencias del usuario.

---

## Modulo 1: Seguridad y Privacidad

### NFR-01: Proteccion de datos personales

El sistema debe proteger datos personales como nombre, correo, telefono, direcciones, historial de compras y preferencias de comunicacion. La recoleccion de datos debe limitarse a lo necesario para operar la plataforma, cumplir obligaciones legales y mejorar la experiencia del usuario con consentimiento cuando aplique.

**Modulos relacionados:** Usuarios, pedidos, cursos, boletines y administracion.

### NFR-02: Cumplimiento de privacidad

La plataforma debe considerar regulaciones de proteccion de datos aplicables, como GDPR o legislacion local equivalente. Debe permitir gestionar consentimiento, bajas de boletines, rectificacion de datos y eliminacion o anonimizado cuando sea legal y operativamente posible.

**Modulos relacionados:** Usuarios, boletines, email marketing y administracion.

### NFR-03: Cifrado en transito

Todo el trafico entre cliente, servidor, pasarela de pago y servicios externos debe usar HTTPS con TLS vigente. No debe permitirse intercambio de credenciales, tokens, datos de pago o datos personales mediante canales inseguros.

**Modulos relacionados:** Todos los modulos.

### NFR-04: Gestion segura de contraseñas

Las contraseñas deben almacenarse mediante hashing fuerte con sal, como bcrypt, Argon2 o equivalente aprobado. El sistema nunca debe guardar contraseñas en texto plano ni enviarlas por correo electronico.

**Modulos relacionados:** Usuarios, control de acceso y administracion.

### NFR-05: Control de acceso por roles

Cada accion protegida debe validar permisos segun el rol del usuario. Las funciones administrativas deben impedir que clientes accedan a gestion de productos, inventario, pedidos, cursos, reportes, usuarios, cupones o boletines.

**Modulos relacionados:** Usuarios, administracion, pedidos, inventario y cursos.

### NFR-06: Seguridad de integraciones externas

Las claves de MercadoPago, PayPal, proveedores de email u otros servicios externos deben mantenerse fuera del codigo fuente y cargarse desde variables de entorno o un gestor de secretos. Los webhooks deben validarse para evitar eventos falsificados.

**Modulos relacionados:** Pagos, email, boletines, pedidos y seguridad.

---

## Modulo 2: Rendimiento y Capacidad

### NFR-07: Tiempo de carga inicial

La pagina principal y el catalogo deben cargar en menos de 2 segundos bajo condiciones normales de red y carga esperada. Imagenes de productos, cursos y recursos multimedia deben optimizarse para no afectar la experiencia de navegacion.

**Modulos relacionados:** Catalogo, cursos y contenido multimedia.

### NFR-08: Tiempo de respuesta de operaciones clave

Busquedas, filtros, agregado al carrito, validacion de stock, consulta de pedido e inicio de sesion deben responder rapidamente. Como objetivo inicial, las operaciones frecuentes no deberian superar 1 segundo en condiciones normales.

**Modulos relacionados:** Catalogo, carrito, pedidos, usuarios e inventario.

### NFR-09: Usuarios concurrentes

El sistema debe soportar al menos 200 usuarios concurrentes sin degradacion significativa en catalogo, autenticacion, carrito, checkout y acceso a cursos. Las pruebas de carga deben incluir escenarios de busqueda, compra y consumo de contenido.

**Modulos relacionados:** Usuarios, catalogo, pagos, pedidos y cursos.

### NFR-10: Escalabilidad

La arquitectura debe permitir crecer en volumen de productos, usuarios, pedidos, cursos, boletines y materiales digitales sin redisenar el sistema completo. Debe ser posible escalar la aplicacion, base de datos o servicios externos segun demanda.

**Modulos relacionados:** Todos los modulos.

### NFR-11: Optimizacion de consultas

Las consultas a catalogo, inventario, pedidos, usuarios y reportes deben usar indices, paginacion y filtros eficientes. Los reportes pesados no deben bloquear operaciones normales de compra, pago o administracion.

**Modulos relacionados:** Catalogo, inventario, pedidos, reportes y administracion.

---

## Modulo 3: Disponibilidad, Continuidad y Recuperacion

### NFR-12: Disponibilidad del servicio

La plataforma debe tener una disponibilidad minima objetivo de 99.5%, excluyendo mantenimientos programados comunicados previamente. Las funciones criticas son catalogo, carrito, pago, acceso a cursos y panel administrativo.

**Modulos relacionados:** Todos los modulos.

### NFR-13: Manejo de fallas externas

Si falla una pasarela de pago, proveedor de email u otro servicio externo, el sistema debe registrar el error, informar al usuario de forma clara y mantener consistencia en pedidos, pagos, stock, cupos y accesos a cursos.

**Modulos relacionados:** Pagos, pedidos, inventario, cursos y email.

### NFR-14: Respaldo de informacion

La base de datos debe respaldarse de manera periodica para proteger usuarios, pedidos, pagos, inventario, cursos, boletines y reportes. Los respaldos deben probarse con restauraciones controladas para asegurar que son utilizables.

**Modulos relacionados:** Todos los modulos.

### NFR-15: Recuperacion ante incidentes

El sistema debe contar con un procedimiento de recuperacion que defina responsables, pasos de restauracion, tiempos objetivo y verificacion posterior. La recuperacion debe priorizar ventas, pedidos pagados, pagos pendientes y acceso a cursos comprados.

**Modulos relacionados:** Pagos, pedidos, cursos, inventario y administracion.

---

## Modulo 4: Usabilidad y Accesibilidad

### NFR-16: Diseno responsive

La plataforma debe funcionar correctamente en moviles, tabletas y escritorio. Catalogo, detalle de producto, carrito, checkout, perfil, pedidos y cursos deben adaptarse sin perdida de informacion clave.

**Modulos relacionados:** Catalogo, carrito, usuarios, pedidos y cursos.

### NFR-17: Accesibilidad

La interfaz debe cumplir como objetivo con WCAG 2.1 nivel AA. Debe considerar contraste suficiente, navegacion con teclado, textos alternativos en imagenes, etiquetas de formularios y mensajes de error comprensibles.

**Modulos relacionados:** Todos los modulos visibles para clientes y administradores.

### NFR-18: Claridad del flujo de compra

El usuario debe entender en todo momento que esta comprando, cuanto pagara, que datos faltan y cual es el estado de su pedido. El checkout debe minimizar pasos innecesarios para favorecer compras en menos de 5 minutos.

**Modulos relacionados:** Catalogo, carrito, checkout, pagos y pedidos.

### NFR-19: Mensajes de error comprensibles

Los errores de formularios, pagos, stock, inicio de sesion, envio de correos y descarga de materiales deben explicar el problema y la accion sugerida sin exponer informacion tecnica sensible.

**Modulos relacionados:** Usuarios, pagos, cursos, carrito, inventario y email.

### NFR-20: Consistencia visual

Botones, formularios, tarjetas de producto, estados de pedido, formularios administrativos y mensajes del sistema deben seguir una misma guia visual para que el usuario aprenda rapidamente como interactuar con la plataforma.

**Modulos relacionados:** Catalogo, administracion, cursos, carrito y usuarios.

---

## Modulo 5: Mantenibilidad y Arquitectura

### NFR-21: Separacion modular

El sistema debe organizarse por responsabilidades claras: usuarios, catalogo, inventario, carrito, pagos, pedidos, cursos, boletines, email, administracion y reportes. Esta separacion debe facilitar cambios sin impactos innecesarios.

**Modulos relacionados:** Todos los modulos.

### NFR-22: Codigo mantenible

El codigo debe seguir convenciones de estilo, nombres claros, validaciones centralizadas cuando corresponda y documentacion minima para reglas complejas. La complejidad debe mantenerse controlada para facilitar soporte y evolucion.

**Modulos relacionados:** Todos los modulos.

### NFR-23: Pruebas automatizadas

Las funciones criticas deben cubrirse con pruebas automatizadas, incluyendo autenticacion, calculo de carrito, aplicacion de cupones, confirmacion de pago, descuento de inventario, habilitacion de cursos y envio de correos transaccionales.

**Modulos relacionados:** Usuarios, carrito, pagos, inventario, cursos y email.

### NFR-24: Gestion de configuracion

Variables como credenciales, URLs de proveedores, umbrales de stock, moneda, impuestos, reglas de envio, configuracion de email y parametros de seguridad deben administrarse por entorno y no estar codificadas directamente.

**Modulos relacionados:** Pagos, email, inventario, seguridad y despliegue.

### NFR-25: Compatibilidad tecnologica

La solucion debe usar tecnologias ampliamente soportadas. Como referencia, frontend con React o Vue.js; backend con Node.js Express o Springboot; base de datos PostgreSQL; hosting en Vercel, Netlify o proveedor equivalente.

**Modulos relacionados:** Arquitectura general.

---

## Modulo 6: Datos, Auditoria y Trazabilidad

### NFR-26: Integridad de datos

El sistema debe mantener consistencia entre pedidos, pagos, inventario, cupos y accesos a cursos. No debe habilitarse un curso ni descontarse inventario de forma definitiva sin una confirmacion valida de pago o accion administrativa autorizada.

**Modulos relacionados:** Pagos, pedidos, inventario y cursos.

### NFR-27: Auditoria administrativa

Las acciones administrativas relevantes deben registrar usuario, fecha, accion, entidad afectada y valores importantes antes y despues cuando sea razonable. Esto incluye cambios de inventario, pedidos, cursos, roles, cupones y reportes sensibles.

**Modulos relacionados:** Administracion, inventario, usuarios, cursos y pedidos.

### NFR-28: Trazabilidad de transacciones

Cada pago debe poder rastrearse desde el pedido interno hasta la referencia de la pasarela externa. Esta trazabilidad debe ayudar a resolver reclamos, duplicados, pagos pendientes, reembolsos y conciliaciones.

**Modulos relacionados:** Pagos, pedidos, reportes y soporte.

### NFR-29: Retencion de registros

Los registros de pedidos, transacciones, movimientos de inventario, accesos a cursos y correos enviados deben conservarse durante el periodo definido por reglas legales y operativas. La retencion debe equilibrar auditoria, privacidad y capacidad de almacenamiento.

**Modulos relacionados:** Pedidos, inventario, cursos, email y reportes.

---

## Modulo 7: Email, Observabilidad y Soporte

### NFR-30: Confiabilidad del email

Los correos transaccionales, recordatorios de cursos, boletines y alertas administrativas deben enviarse mediante un proveedor confiable. El sistema debe registrar estado basico de envio cuando el proveedor lo permita y debe manejar fallas sin interrumpir procesos criticos como pago o pedido.

**Modulos relacionados:** Usuarios, pagos, pedidos, cursos, inventario y boletines.

### NFR-31: Registro de eventos

El sistema debe registrar eventos importantes como errores de pago, fallas de email, cambios de stock, accesos administrativos, actualizaciones de pedido y excepciones de aplicacion. Los registros deben evitar datos sensibles innecesarios.

**Modulos relacionados:** Todos los modulos.

### NFR-32: Monitoreo de salud

La plataforma debe contar con indicadores de salud para aplicacion, base de datos, integraciones de pago y proveedor de email. Los responsables tecnicos deben poder detectar caidas, degradaciones o errores repetidos.

**Modulos relacionados:** Infraestructura, pagos, email y administracion.

### NFR-33: Soporte a incidentes

La informacion disponible para soporte debe permitir ubicar rapidamente un usuario, pedido, pago, curso, movimiento de inventario o correo enviado. El soporte debe poder diagnosticar el estado sin modificar datos de forma accidental.

**Modulos relacionados:** Usuarios, pedidos, pagos, cursos, inventario y email.

---

## Modulo 8: Compatibilidad, Legalidad y Contenido

### NFR-34: Compatibilidad de navegadores

La plataforma debe funcionar en versiones recientes de Chrome, Edge, Firefox y Safari, tanto en escritorio como en movil cuando aplique. Las funciones criticas no deben depender de caracteristicas experimentales sin alternativa.

**Modulos relacionados:** Interfaz general.


### NFR-35: Responsabilidad sobre contenido de salud

Las descripciones de productos, beneficios, modos de uso y advertencias deben presentarse de forma responsable, evitando promesas medicas no sustentadas. Cuando aplique, debe incluirse informacion de uso sugerido y advertencias visibles.

**Modulos relacionados:** Catalogo, productos, cursos y administracion.

### NFR-36: Gestion de contenido multimedia

Imagenes de productos, videos de cursos y documentos descargables deben almacenarse y entregarse de forma optimizada. El sistema debe validar formatos permitidos y tamanos maximos para proteger rendimiento y seguridad.

**Modulos relacionados:** Catalogo, cursos, administracion y almacenamiento.

### NFR-37: Internacionalizacion futura

Aunque la version inicial puede estar en español, el sistema debe evitar decisiones que impidan agregar otros idiomas, monedas o formatos regionales en el futuro.

**Modulos relacionados:** Catalogo, checkout, pagos y reportes.

</div>
