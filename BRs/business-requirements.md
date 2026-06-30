<div align="justify">

# Requisitos de Negocio - El Jardin de tu Salud

## 1. Proposito del Documento

Este documento define la base de negocio de la plataforma "El Jardin de tu Salud". Los requisitos de negocio son la cabeza de los requisitos de usuario, funcionales y no funcionales: explican por que existe el sistema, que valor debe entregar, que alcance tiene, como se medira el exito y que reglas deben guiar las decisiones de producto.

Los requerimientos funcionales deben derivarse de estos objetivos y reglas. Los requerimientos no funcionales deben asegurar que el sistema pueda operar con confianza, seguridad, rendimiento y calidad suficiente para cumplir el proposito comercial.

## 2. Vision del Proyecto

"El Jardin de tu Salud" sera una plataforma de comercio electronico especializada en productos naturistas, bienestar y educacion en salud natural. La plataforma debe permitir vender productos fisicos, como medicamentos herbales, plantas medicinales, suplementos y snacks saludables, junto con cursos digitales o sesiones en vivo sobre bienestar.

La vision del negocio es ofrecer una experiencia confiable, clara y accesible para personas interesadas en alternativas naturales, sin convertirse en una plataforma de consulta medica ni prometer tratamientos. El valor principal sera combinar catalogo especializado, informacion responsable, compra sencilla y formacion en habitos saludables.

## 3. Objetivos de Negocio

### BR-01: Crear un canal digital de venta especializado

El negocio necesita una plataforma propia para vender productos naturistas y cursos sin depender exclusivamente de ventas presenciales, redes sociales o marketplaces externos. El sistema debe permitir descubrir productos, agregarlos al carrito, pagar en linea y recibir confirmacion por email.

**Impacto en otros requisitos:** Este objetivo origina los modulos de catalogo, carrito, pagos, pedidos, inventario y email transaccional.

### BR-02: Aumentar la confianza del cliente

La plataforma debe presentar informacion clara sobre ingredientes, beneficios, modo de uso sugerido, advertencias, disponibilidad y precio. El cliente debe poder comprar con confianza, entendiendo que los productos de salud natural requieren comunicacion responsable y no sustituyen atencion medica profesional.

**Impacto en otros requisitos:** Este objetivo origina requisitos de detalle de producto, contenido responsable, seguridad, privacidad y usabilidad.

### BR-03: Vender cursos como linea complementaria de ingresos

El negocio desea ofrecer cursos digitales o sesiones en vivo sobre salud natural y bienestar. Los cursos deben poder venderse desde el mismo flujo de compra y habilitarse al cliente despues del pago.

**Impacto en otros requisitos:** Este objetivo origina requisitos de cursos, calendario, cupos, acceso a contenido, recordatorios por email y reportes de cursos.

### BR-04: Mejorar la operacion interna

La administracion debe poder gestionar productos, cursos, inventario, pedidos, cupones, usuarios y reportes desde un panel centralizado. Esto reduce trabajo manual, evita errores de stock y mejora el seguimiento de ventas.

**Impacto en otros requisitos:** Este objetivo origina requisitos de panel administrativo, gestion de inventario, reportes, trazabilidad y auditoria.

### BR-05: Mantener comunicacion comercial y operativa por email

El negocio usara email como canal principal para confirmaciones de registro, recuperacion de contraseña, confirmaciones de compra, cambios de pedido, recordatorios de cursos, avisos de stock y boletines comerciales.

**Impacto en otros requisitos:** Este objetivo origina la integracion con servicio de email, preferencias de comunicacion, boletines y registros basicos de envio.

## 4. Alcance del Proyecto

### 4.1 Incluye

- Catalogo de productos naturistas, medicamentos herbales, plantas medicinales, suplementos, snacks saludables y cursos.
- Busqueda, filtros y detalle de productos o cursos.
- Registro, inicio de sesion, recuperacion de contraseña y perfil de cliente.
- Carrito de compras, cupones y checkout.
- Pagos en linea mediante MercadoPago y opcion futura de PayPal.
- Creacion, gestion y seguimiento de pedidos.
- Gestion de inventario por categoria, incluyendo stock, lotes, fechas de vencimiento y cupos de cursos.
- Gestion de cursos, calendario, sesiones en vivo y acceso a contenido comprado.
- Boletines informativos y comunicaciones por email.
- Panel administrativo para productos, cursos, usuarios, pedidos, inventario, cupones y reportes.
- Reportes de ventas, productos mas vendidos, rendimiento de cursos, uso de cupones y movimientos de inventario.

### 4.2 No Incluye

- Consultas medicas en linea.
- Diagnosticos, recetas electronicas o seguimiento clinico de pacientes.
- Integracion directa con farmacias fisicas.
- Gestion de expedientes medicos.
- Promesas de curacion o sustitucion de tratamientos profesionales.
- Aplicacion movil nativa en la primera version.
- Sistema de mensajeria interna o avisos push; la comunicacion se manejara por email.

## 5. Publico Objetivo

El publico principal son personas interesadas en medicina alternativa, productos naturales, bienestar preventivo y alimentacion saludable.

- **Edad aproximada:** 25 a 60 anos.
- **Perfil de compra:** Personas que buscan productos confiables, informacion clara y una experiencia de compra sencilla.
- **Nivel socioeconomico esperado:** Medio a medio-alto, con interes en calidad, confianza y conveniencia.
- **Comportamiento digital:** Usuarios que pueden comprar desde movil o escritorio, y que esperan pagos digitales, correos de confirmacion y acceso simple a su historial.
- **Necesidades principales:** Encontrar productos por categoria o beneficio, conocer disponibilidad, comprar sin friccion, recibir informacion responsable y acceder a cursos comprados.

## 6. Propuesta de Valor

La plataforma debe diferenciarse por combinar comercio electronico especializado, contenido educativo y confianza operativa.

- **Especializacion:** Catalogo enfocado en productos naturales y bienestar, no en consumo general.
- **Claridad:** Informacion completa sobre productos, cursos, precios, stock y condiciones de compra.
- **Confianza:** Pagos seguros, correos de confirmacion, historial de pedidos y contenido redactado responsablemente.
- **Conveniencia:** Compra en linea, acceso a cursos desde el perfil y comunicacion por email.
- **Gestion interna:** Administracion centralizada para reducir errores y mejorar la toma de decisiones.

## 7. Modelo de Ingresos

- Margen sobre productos fisicos como medicamentos herbales, plantas medicinales, suplementos y snacks saludables.
- Venta directa de cursos digitales o sesiones en vivo.
- Promociones y cupones para incentivar compras superiores a montos definidos por el negocio.
- Venta cruzada entre productos y cursos relacionados.
- Campanas de boletines para comunicar lanzamientos, promociones, reposiciones de stock y nuevos cursos.

## 8. Reglas de Negocio

### BR-06: Compra con cuenta registrada

La compra final debe asociarse a una cuenta registrada para permitir historial, seguimiento, acceso a cursos, soporte y correos transaccionales. El visitante puede navegar el catalogo, pero debe iniciar sesion o registrarse para completar la compra.

### BR-07: Stock y cupos obligatorios

No debe venderse un producto sin stock ni un curso sin cupo disponible cuando el curso tenga cupo limitado. El sistema debe validar disponibilidad antes del pago y actualizarla cuando el pago sea aprobado.

### BR-08: Acceso a cursos despues del pago

El acceso a cursos debe habilitarse solo despues de confirmacion de pago o asignacion manual autorizada por un administrador. Si la compra se cancela o reembolsa, el acceso puede suspenderse segun las politicas del negocio.

### BR-09: Comunicacion por email

Los eventos relevantes se comunicaran por email: registro, recuperacion de contraseña, confirmacion de compra, cambios de pedido, envio, recordatorios de cursos, regreso de stock y boletines. No se contempla un modulo independiente de avisos push o mensajeria interna.

### BR-10: Contenido de salud responsable

Las descripciones de productos deben evitar promesas medicas no comprobadas. El contenido debe informar beneficios, ingredientes, modo de uso sugerido y advertencias de manera responsable.

### BR-11: Administracion con trazabilidad

Las operaciones administrativas relevantes deben dejar rastro: cambios de inventario, actualizacion de pedidos, cambios de usuarios, gestion de cursos y ajustes de precios o cupones.

### BR-12: Cupones controlados

Los cupones deben tener reglas claras de vigencia, monto minimo, categorias aplicables, limite de uso y usuarios elegibles. El sistema debe impedir usos duplicados o fuera de regla.

## 9. Indicadores Clave de Exito

- Conversion de visitantes a compradores mayor al 3%.
- Tiempo promedio para completar una compra menor a 5 minutos.
- Tasa de abandono de carrito menor al 60%.
- Porcentaje de pedidos pagados correctamente mayor al 95% de los intentos validos.
- Disponibilidad de la plataforma igual o superior al 99.5%.
- Reduccion de errores manuales de stock mediante actualizacion automatica.
- Incremento mensual de ventas de cursos y productos relacionados.
- Tasa de apertura de boletines suficiente para validar el email como canal comercial.
- Tiempo de respuesta administrativa menor para preparar pedidos y atender incidencias.

## 10. Supuestos

- El negocio cuenta con productos, imagenes, precios y descripciones iniciales para cargar el catalogo.
- Los pagos se procesaran mediante proveedores externos y la plataforma no almacenara datos sensibles de tarjetas.
- El email sera el canal principal de comunicacion con clientes y administradores.
- La version inicial sera web responsive, no aplicacion movil nativa.
- La plataforma se desarrollara en espanol como idioma principal.
- La gestion de envios puede iniciar de forma manual con registro de guia o paqueteria dentro del pedido.

## 11. Restricciones

- El sistema no debe ofrecer diagnostico medico ni sustituir consulta profesional.
- La informacion de productos debe revisarse antes de publicarse para evitar afirmaciones riesgosas.
- La disponibilidad de pagos dependera de la pasarela seleccionada.
- El envio de correos dependera del proveedor de email contratado.
- El presupuesto y tiempo del proyecto pueden requerir priorizar una primera version con funciones esenciales.

## 12. Priorizacion de Version Inicial

### Prioridad Alta

- Catalogo de productos y cursos.
- Registro, inicio de sesion y perfil de cliente.
- Carrito, checkout y pagos.
- Pedidos y correos transaccionales.
- Inventario basico y validacion de stock.
- Gestion administrativa de productos, cursos y pedidos.

### Prioridad Media

- Cupones.
- Boletines.
- Reportes comerciales.
- Recordatorios de cursos por email.
- Avisos de regreso a stock.

### Prioridad Baja

- Integraciones avanzadas de marketing.
- Recomendaciones personalizadas.
- Internacionalizacion.
- Automatizaciones avanzadas de reportes.

## 13. Trazabilidad hacia otros documentos

- Los requisitos funcionales deben especificar como se cumplen los objetivos de catalogo, compra, pagos, inventario, cursos, email, administracion y reportes.
- Los requisitos no funcionales deben asegurar seguridad, rendimiento, disponibilidad, accesibilidad, mantenibilidad, trazabilidad y cumplimiento.
- Los requisitos de usuario deben expresar estas necesidades desde la perspectiva de clientes y administradores.
- Las historias de usuario deben convertir los requisitos en escenarios implementables y verificables.

</div>
