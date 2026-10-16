# El Jardín de tu Salud - Documentación

Este repositorio contiene toda la documentación técnica y funcional del sitio web de e-commerce **"El Jardín de tu Salud"**, especializado en productos naturistas, medicamentos herbales, alimentos saludables y cursos de bienestar.

---

## Estructura del Repositorio

```
📦 El-Jardin-de-tu-Salud-Docs/
│
├── 📁 BRs/
│ └── business-requirements.md
│
├── 📁 FRs/
│ └── functional-requirements.md
│
├── 📁 NFRs/
│ └── non-functional-requirements.md
│
├── 📁 URs/
│ └── user-requirements.md
│
├── 📁 UHs/
│ └── user-stories.md
│
├── 📁 GUIs/
│ ├── wireframes/
│ │ ├── home-page.png
│ │ ├── product-detail.png
│ │ └── checkout-flow.png
│ ├── mockups/
│ │ └── figma-link.md
│ └── ui-guidelines.md
│
├── 📁 diagrams/
│ ├── er-diagram.md
│ ├── flowcharts/
│ │ └── purchase-flow.mermaid
│ └── architecture/
│ └── system-architecture.png
│
├── 📁 reports/
│ ├── weekly-progress.md
│ └── sprint-retrospectives.md
│
└── README.md
```


---

## Descripción de Carpetas

| Carpeta | Contenido |
| :--- | :--- |
| **BRs/** | Requisitos de negocio: objetivos, alcance, público objetivo, KPIs. |
| **FRs/** | Requisitos funcionales: características del sistema (módulos, acciones). |
| **NFRs/** | Requisitos no funcionales: seguridad, rendimiento, usabilidad, escalabilidad. |
| **URs/** | Requisitos de usuario: necesidades específicas expresadas por los stakeholders. |
| **UHs/** | Historias de usuario en formato ágil (*Como... quiero... para...*). |
| **GUIs/** | Diseños visuales: wireframes, mockups, flujos de navegación y guía de estilos. |
| **diagrams/** | Diagramas técnicos: entidad-relación, flujos de proceso, arquitectura del sistema. |
| **reports/** | Informes de avance, retrospectivas y métricas del proyecto. |

---

## Estructura Detallada

```
El-Jardin-de-tu-Salud-Docs/
│
├── BRs/ # Requisitos de Negocio
│ └── business-requirements.md # Objetivos, alcance, KPIs
│
├── FRs/ # Requisitos Funcionales
│ └── functional-requirements.md # Módulos: usuarios, productos, cursos, pagos
│
├── NFRs/ # Requisitos No Funcionales
│ └── non-functional-requirements.md # Seguridad, rendimiento, accesibilidad
│
├── URs/ # Requisitos de Usuario
│ └── user-requirements.md # Necesidades de clientes y admins
│
├── UHs/ # Historias de Usuario
│ └── user-stories.md # Formato: Como... quiero... para...
│
├── GUIs/ # Interfaces de Usuario
│ ├── wireframes/ # Bocetos de baja fidelidad
│ │ ├── home.png
│ │ ├── product-detail.png
│ │ └── checkout.png
│ ├── mockups/ # Diseños de alta fidelidad
│ │ └── figma-design.md # Enlace a Figma
│ └── ui-guidelines.md # Paleta de colores, tipografía, componentes
│
├── diagrams/ # Diagramas técnicos
│ ├── er-diagram.md # Modelo de base de datos (entidad-relación)
│ ├── flowcharts/ # Flujos de proceso
│ │ └── purchase-flow.mermaid # Flujo de compra (Mermaid)
│ └── architecture/ # Arquitectura del sistema
│ └── system-architecture.png # Microservicios / Monolito / Cloud
│
├── reports/ # Informes del proyecto
│ ├── weekly-progress.md # Avance semanal
│ └── sprint-retrospectives.md # Retrospectivas de sprints
│
└── README.md # Este archivo
```

---
## 📌 Convenciones de nombrado
| **Tipo** | **Ejemplo** |
| :--- | :--- |
|**docs/** |docs/actualizar-FRs|
|**feat/**  |feat/agregar-diagrama-ER|
|**fix/**   |fix/corregir-typo-en-BRs|
|**review/**|review/revisar-NFRs|

---
## 🛠️ Tecnologías para Documentación
- **Markdown:** Contenido textual.
- **Mermaid:** Diagramas de flujo y secuencia (soporte nativo en Github).
- **Figma/Draw.io:** Mockups y wirwframes.
- **PlantUML:** Diagramas de clases y arquitectura.