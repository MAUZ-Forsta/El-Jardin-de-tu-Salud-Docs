---
tipo: adr
id: ADR-003
estado: propuesta
fecha: 2026-10-12
actualizado: 2026-10-21
tags: [seguridad, auth, arquitectura]
---
# ADR-003 — Autenticación y autorización

## Estado
**Propuesta**, no aprobada ni implementada. Complementa [[ADR-001 - Backend y persistencia]].

## Fuente de necesidades
- FR-01: alta con nombre, email, teléfono, contraseña, unicidad y correo de confirmación.
- FR-02: autenticación de clientes y administradores y cierre de sesión.
- FR-03: recuperación por enlace temporal de un solo uso y aviso de cambio.
- FR-04: edición de perfil, direcciones y validación reforzada para cambios sensibles.
- FR-05: dos roles principales, cliente y administrador, y aislamiento de datos entre cuentas.
- NFR-01, NFR-03, NFR-04, NFR-05: protección de información, TLS, hash de contraseña y autorización.

## Decisión técnica a validar
- **Identidad**: contraseña con hash Argon2id (o algoritmo robusto validado); nunca texto plano.
- **Sesión web**: preferencia inicial por cookie `HttpOnly`, `Secure`, `SameSite` apropiado + control de sesiones del servidor y CSRF cuando corresponda; revisar dominios reales de React/API antes de adoptar el mecanismo.
- **Alternativa**: tokens de acceso de corta duración con revocación/rotación adecuadas, si los requisitos de despliegue o clientes distintos lo exigen. No elegir ambos sin justificación.
- **Roles**: cliente y administrador conforme FR-05; validar permiso en cada endpoint y recurso (no solo ocultar componentes).
- **Recuperación**: token aleatorio de un solo uso, plazo corto, almacenamiento de su hash, invalidación atómica y respuesta genérica para evitar enumerar cuentas.
- **Email**: proveedor transaccional por definir; avisos sin secretos ni contraseñas.
- **Ataques**: límites de intentos, auditoría de eventos sensibles, protección de CSRF/CORS según topología y errores no reveladores.

## Decisiones abiertas
1. Topología del frontend/API (mismo sitio o dominios distintos) y comportamiento de cookies.
2. Flujo de confirmación de email antes de habilitar cuenta (detalle operacional).
3. Políticas exactas de longitud de contraseñas, caducidad, bloqueos y reautenticación.
4. Google OAuth diferido por DEC-02 y NFR-39; se mantiene HU-02 y el acceso convencional.
5. Modelo concreto de persistencia de sesión y proveedor de email.

## Consecuencias
Requiere pruebas de permisos por propietario, expiración/revocación, restablecimiento de contraseña, gestión de sesiones y fallos del proveedor de correo. No depende de cupones.

## Evidencia para aprobación
Revisión de React, prueba de integración, amenaza básica, prueba E2E, estimación dentro del Sprint 01 y aprobación de decisión.

## Identificador documental
El antiguo ADR-002 de autenticación pasa a ADR-003 para reservar ADR-002 al modelo relacional solicitado. Su contenido sigue siendo propuesta pendiente de validación.

## Estado contrastado con código — 2026-10-21

La autenticación sigue sin implementar. Las sesiones SQLAlchemy no resuelven la estrategia de sesión web. La columna password_hash y el CHECK de rol son bases de persistencia, no hashing ni autorización implementados.

Véase [[Registro de avances]] para evidencia, diferencias y límites de la validación.
