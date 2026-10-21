---
tipo: diseno-dominio
estado: borrador
actualizado: 2026-10-21
tags: [poo, dominio, pendiente-validacion]
---
# Modelo de dominio — borrador

> Inventario de conceptos, **no** esquema de base de datos, diagrama ER aprobado ni clases existentes.

| Concepto candidato | Fuente documental | Regla por aclarar |
|---|---|---|
| Cuenta / Usuario / Rol | FR-01 a FR-05; BR-06 | permisos fijos ADMIN/CLIENT confirmados; recuperación y política de sesiones pendientes |
| Producto físico | FR-06, FR-08, FR-21 | atributos, categorías y variantes |
| Curso / Acceso a contenido | FR-09, FR-26 a FR-28; BR-08 | acceso en línea, sin consumo offline; materiales individuales descargables conservados (DEC-03) |
| Carrito | FR-11 a FR-13 | persistencia y vigencia de precios |
| Pedido | FR-17 a FR-20 | estados, cancelaciones y reembolsos |
| Pago / Transacción | FR-14 a FR-16 | estados, conciliación e idempotencia |
| Inventario / Movimiento | FR-21 a FR-25; BR-07 | reservas, concurrencia y ajustes auditables |
| Suscripción / Boletín | FR-29 a FR-32 | consentimiento, bajas y automatización |
| Registro de auditoría | BR-11; NFR-27 y NFR-28 | eventos auditables y retención |

## Reglas a conservar
- **BR-06:** compra con cuenta registrada.
- **BR-07:** no vender productos sin stock ni cursos sin cupos disponibles cuando aplique.
- **BR-08:** acceso al curso después del pago o asignación administrativa autorizada.
- **BR-11:** trazabilidad administrativa.

## Diseño POO: responsabilidades iniciales
- Objetos de dominio: comportamiento y validación intrínseca.
- Servicios de aplicación: ejecutar casos de uso y coordinar persistencia.
- Repositorios: consultar y persistir, sin lógica comercial crítica propia.
- Adaptadores externos: encapsular respuestas del proveedor de pagos/correo.

## Pendientes antes del esquema relacional
1. Resolver inconsistencias de alcance entre BR, FR, UR, HU y GUIs.
2. Definir criterios de aceptación y estados de cada módulo.
3. Especificar invariantes transaccionales de inventario, pagos y pedidos.
4. Revisar componentes React y entradas/salidas realmente necesarias.

## Referencias
- [[Arquitectura del backend]]
- [[Contradicciones y decisiones pendientes]]
- [BR](<../../BRs/business-requirements.md>)
- [FR](<../../FRs/functional-requirements.md>)

## Estado contrastado con código — 2026-10-21

El inventario de conceptos sigue propuesto. Usuarios y perfiles cuentan con persistencia inicial; eso no completa registro, perfil funcional ni autorización.

Véase [[Registro de avances]] para evidencia, diferencias y límites de la validación.
