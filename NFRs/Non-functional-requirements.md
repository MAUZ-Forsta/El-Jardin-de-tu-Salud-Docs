# Requisitos No Funcionales - El Jardín de tu Salud

## Seguridad
- **NFR-01:** Cumplimiento con GDPR/Ley de Protección de Datos (los datos de salud son sensibles).
- **NFR-02:** Todo el tráfico debe ser HTTPS (SSL/TLS).
- **NFR-03:** Almacenamiento de contraseñas con hash (bcrypt).

## Rendimiento
- **NFR-04:** Tiempo de carga de la página principal < 2 segundos.
- **NFR-05:** Soporte para 500 usuarios concurrentes sin degradación.

## Disponibilidad
- **NFR-06:** Uptime del 99.5% (excepto mantenimientos programados).

## Usabilidad
- **NFR-07:** Diseño responsive (móvil, tablet, escritorio).
- **NFR-08:** Cumplir con WCAG 2.1 AA (accesibilidad para discapacitados).

## Tecnología (sugerida)
- **Frontend:** React/Vue.js con Next.js/Nuxt.
- **Backend:** Node.js (Express) o Python (Django).
- **Base de datos:** PostgreSQL.
- **Hosting:** AWS / Vercel / Netlify.