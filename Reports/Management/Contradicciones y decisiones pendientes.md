---
tipo: registro-de-decisiones
fecha_actualizacion: 2026-10-16
actualizado: 2026-10-16
estado: decisiones_resueltas
tags: [requisitos, alcance, riesgos]
---

# Contradicciones y decisiones pendientes

Este registro documenta las decisiones aprobadas DEC-01 a DEC-05. **Resuelta** significa que se resolvió el alcance documental; no acredita desarrollo ni pruebas. Los restantes conflictos técnicos permanecen en el [informe de backend](<Diferencias y decisiones pendientes.md>).

## DEC-01

- **Estado:** RESUELTA.
- **Fecha de resolución:** 2026-10-16.
- **Problema original:** BR-12 y HU-05 requieren cupones, mientras los FR los excluyen; faltaba aclarar su prioridad inicial.
- **Resolución aprobada:** cupones no indispensables para la primera versión; funcionalidad diferida para la fase final o una versión posterior, sujeta a planificación y tiempo disponible.
- **Requisitos afectados:** [NFR-38](<../../NFRs/Non-functional-requirements.md#nfr-38-cupones-de-descuento>), [BR-12](<../../BRs/business-requirements.md#br-12-cupones-controlados>), [HU-05](<../../UHs/User-stories.md>); referencias a cupones en BR-04, alcance BR y NFR-05/23/27 se conservan con este diferimiento.
- **Impacto sobre la primera versión:** sin aplicación, administración ni componente visual de cupones; checkout y cálculo inicial de pagos sin dependencias de cupones. No se incorporan automáticamente al Sprint 06. Los descuentos porcentuales de productos conservan su alcance.

## DEC-02

- **Estado:** RESUELTA.
- **Fecha de resolución:** 2026-10-16.
- **Problema original:** HU-02 solicita Google y FR-01 a FR-05 describen el acceso convencional, sin prioridad definida para OAuth.
- **Resolución aprobada:** Google OAuth no indispensable para la primera versión; funcionalidad diferida mediante NFR-39.
- **Requisitos afectados:** [NFR-39](<../../NFRs/Non-functional-requirements.md#nfr-39-autenticación-con-google>), [HU-02](<../../UHs/User-stories.md>), [FR-01 a FR-05](<../../FRs/functional-requirements.md>), conservados sin cambios.
- **Impacto sobre la primera versión:** mantener registro e inicio de sesión convencional. Google OAuth queda fuera del alcance inicial y no se incorpora automáticamente al Sprint 06.

## DEC-03

- **Estado:** RESUELTA.
- **Fecha de resolución:** 2026-10-16.
- **Problema original:** UR-03 pedía descarga de cursos para consumo offline; FR-09/27 prevén contenido en línea y FR-28 materiales complementarios descargables.
- **Resolución aprobada:** eliminar consumo offline de cursos completos y actualizar UR-03 para acceso en línea desde el perfil después de confirmar el pago.
- **Requisitos afectados:** [UR-03](<../../URs/User-requirements.md>), [FR-09, FR-27 y FR-28](<../../FRs/functional-requirements.md>) y [HU-03](<../../UHs/User-stories.md>).
- **Impacto sobre la primera versión:** acceso en línea a cursos adquiridos; se mantienen descargas de materiales individuales conforme a los FR. Se preserva la excepción de acceso administrativo autorizado de los FR vigentes.

## DEC-04

- **Estado:** RESUELTA mediante [DEC-01](#dec-01).
- **Fecha de resolución:** 2026-10-16.
- **Problema original:** el panel de usuario incluía «Cupones disponibles» pese a su exclusión del flujo inicial.
- **Resolución aprobada:** diferir el componente visual de cupones según DEC-01.
- **Requisitos afectados:** [GUI — Panel de Usuario](<../../GUIs/GUI-mockups.md#4-panel-de-usuario>), [NFR-38](<../../NFRs/Non-functional-requirements.md#nfr-38-cupones-de-descuento>), BR-12 y HU-05.
- **Impacto sobre la primera versión:** no incluir dicho componente visual; la referencia se conserva marcada como diferida.

## DEC-05

- **Estado:** RESUELTA.
- **Fecha de resolución:** 2026-10-16.
- **Problema original:** BR y NFR mencionan filtros mientras FR-07 exige búsqueda por coincidencia sin filtros especializados.
- **Resolución aprobada:** conservar FR-07 íntegro, con coincidencias parciales y totales. Las referencias genéricas a filtros no amplían el alcance inicial.
- **Requisitos afectados:** [FR-07](<../../FRs/functional-requirements.md#fr-07-busqueda-por-texto-en-coincidencia>), [UR-01](<../../URs/User-requirements.md>), alcance [BR](<../../BRs/business-requirements.md>) y [NFR-08/11](<../../NFRs/Non-functional-requirements.md>).
- **Impacto sobre la primera versión:** prever búsqueda por coincidencia parcial y total en Sprint 02, sin añadir filtros especializados.

## Seguimiento

NFR-38 y NFR-39 son capacidades funcionales registradas excepcionalmente en NFR por decisión del proyecto; no son atributos de calidad. No se eliminan BR ni HU. La [[Matriz de trazabilidad]] y el [[Roadmap]] reflejan estas decisiones; el [plan de sprints](<Plan de sprints.md>) incorpora sus efectos. Las demás decisiones pendientes se conservan en el informe técnico enlazado al inicio.
