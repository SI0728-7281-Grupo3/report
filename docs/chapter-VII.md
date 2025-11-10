# Capítulo VII: Product Implementation, Validation & Deployment

## 7.1. Software Configuration Management

### 7.1.1. Software Development Environment Configuration

Herramientas y plataformas utilizadas para la gestión del proyecto, requisitos, diseño, desarrollo y documentación.

Project Management:
- Trello: Utilizado para la gestión de tareas y proyectos. Facilitó la asignación de tareas, el seguimiento de avances y la definición de prioridades de forma colaborativa. https://trello.com/signup
- Miro: Usado para la planificación visual del proyecto, incluyendo mapas mentales y diagramas de flujo para organizar ideas y procesos. https://miro.com/signup
- OneDrive: Utilizado para el almacenamiento y colaboración de documentos, archivos y recursos relacionados con el proyecto (sustituye el uso de Google Drive). https://www.microsoft.com/microsoft-365/onedrive/
- GitHub Desktop: Permitió la gestión de versiones del código fuente de manera eficiente, asegurando la colaboración fluida entre los miembros del equipo. https://desktop.github.com/

Requirements Management:
- Lucidchart: Usado para diagramar flujos y procesos relacionados con los requisitos de la aplicación. https://www.lucidchart.com/users/register
- Google Forms: Utilizado para recolectar retroalimentación y realizar encuestas que ayudaron a capturar necesidades de los usuarios y del cliente. https://www.google.com/forms/about/

Product UX/UI Design:
- Figma: Herramienta clave para el diseño de la interfaz de usuario y experiencia de usuario. Se crearon prototipos y wireframes que guiaron el desarrollo. https://www.figma.com/signup
- Canva: Usado para generar elementos gráficos adicionales como íconos, banners y recursos visuales. https://www.canva.com/signup

Software Development:
- Entorno de Desarrollo Integrado (IDE):
  - Visual Studio Code: Principal herramienta para el desarrollo. https://code.visualstudio.com/download
  - Android Studio: Usado para emulación y pruebas en Android. https://developer.android.com/studio
- Control de Versiones: Git, con integración a GitHub para colaboración, ramas y merges. https://git-scm.com/downloads
- Gestión de Dependencias:
  - Flutter Pub / Pub.dev: Para gestionar paquetes y bibliotecas. https://pub.dev/
- Herramientas de Construcción:
  - Gradle: Utilizado para la construcción y empaquetado cuando aplica. https://docs.gradle.org/current/userguide/userguide.html

Software Documentation:
- GitHub: Utilizado para documentar procesos mediante README.md y repositorios del proyecto. https://github.com/join
- Structurizr: Empleada para documentar la arquitectura de la solución técnica. https://structurizr.com/

Notas:
- Estas herramientas describen el entorno de trabajo recomendado y evidencian las plataformas usadas por el equipo durante el desarrollo y la colaboración.

### 7.1.2. Source Code Management
- Branching model (GitFlow).
- Reglas de pull request y revisión de código.
- Protección de ramas y políticas de merge.

### 7.1.3. Source Code Style Guide & Conventions
- Guías de estilo (ESLint/Prettier, PEP8, convenciones de commits).
- Plantillas de commit y mensajes.

### 7.1.4. Software Deployment Configuration
- Pipeline CI/CD (herramientas y pasos).
- Variables de entorno y gestión de secretos.
- Estrategias de despliegue (blue/green, rolling).

## 7.2. Solution Implementation

### 7.2.1. Sprint 1

#### 7.2.1.1. Sprint Planning 1
Se inicia la sección con una introducción y a continuación se coloca el cuadro de resumen del sprint planning meeting:
Sprint # | Sprint 1
---|---
<b>Sprint Planning Background | 
Date | YYYY-MM-DD
Time | HH:MM AM/PM
Location | (Descripción de la ubicación de la reunión, física o virtual)
Prepared By | Jiménez Rosas, Arturo Eduardo
Attendees (planning meeting) | Jiménez Rosas, Arturo Eduardo / Rodríguez Peña, Jorge Andrés / ...
Sprint n−1 — Review Summary | (Resumen del Sprint anterior: resultados entregados, feedback del Product Owner, comentarios del equipo)
Sprint n−1 — Retrospective Summary | (Lecciones aprendidas, aciertos y oportunidades de mejora en el proceso)
<b>Sprint Goal & User Stories |
Sprint n Goal | (Definir el Goal del Sprint n y la métrica de cumplimiento.)
Sprint n Velocity | (Velocidad establecida para el Sprint n en Story Points — cuántos SP puede aceptar el equipo.)
Sum of Story Points | (Suma total de Story Points comprometidos en este Sprint n.)

#### 7.2.1.2. Sprint Backlog 1
A continuación, la estructura de la tabla de control de estado para un Sprint:

Sprint # | Sprint 1 || | | | | 
---|---|---|---|---|---|---
<b>User Story Id | <b>User Story Title | <b>Work-Item Id | <b>Work-Item Title | <b>Description | <b>Estimation (Hours) | <b>Assigned To | <b>Status
US-001 |  | WI-001 |  |  |  | To-do / InProcess / ToReview / Done
US-002 |  | WI-002 |  |  |  | To-do / InProcess / ToReview / Done
US-003 |  | WI-003 |  |  |  | To-do / InProcess / ToReview / Done
US-004 |  | WI-004 |  |  |  | To-do / InProcess / ToReview / Done
US-005 |  | WI-005 |  |  |  | To-do / InProcess / ToReview / Done
US-006 |  | WI-006 |  |  |  | To-do / InProcess / ToReview / Done


#### 7.2.1.3. Development Evidence for Sprint Review
Registro de commits y evidencias relacionados al Sprint (rellenar con enlaces a repositorios, PRs y commits).

Repository | Branch | Commit Id | Commit Message | Commit Message Body | Committed on (Date)
---|---|---|---|---|---
user/repositoryname | feature/branch-name | 14ca4e3 | feat: título corto del cambio | Descripción extendida del commit (qué y por qué). | YYYY-MM-DD
user/repositoryname | feature/branch-name | 2b7f9a1 | fix: corrección pequeña | Detalles de la corrección y referencias a issues/PRs. | YYYY-MM-DD
user/repositoryname | develop | a9d4c33 | chore: tareas de mantenimiento | Tareas relacionadas con dependencia/scripts/configuración. | YYYY-MM-DD
user/repositoryname | release/v1.0 | 5f1b0d2 | docs: actualización de la documentación | Archivos modificados: README.md, docs/chapter-VII.md. | YYYY-MM-DD
user/repositoryname | main | e3c7b12 | merge: merge feature/xyz into main | Merge PR #123 — incluye feature xyz y pruebas asociadas. | YYYY-MM-DD

#### 7.2.1.4. Testing Suite Evidence for Sprint Review
- Pruebas automatizadas (unit, integration) y resultados.

#### 7.2.1.5. Execution Evidence for Sprint Review
- Logs, capturas y demo funcional.

#### 7.2.1.6. Services Documentation Evidence for Sprint Review
- Documentación de APIs y servicios (Swagger / OpenAPI links).

#### 7.2.1.7. Software Deployment Evidence for Sprint Review
- Despliegues realizados y URLs (staging/production).

#### 7.2.1.8. Team Collaboration Insights during Sprint
- Retrospectiva breve y lecciones aprendidas.

(Replicar estructura para Sprint 2..N según avance)

## 7.3. Validation Interviews

### 7.3.1. Diseño de Entrevistas
- Objetivos de validación y guion de preguntas.

### 7.3.2. Registro de Entrevistas
- Resumen de respuestas, audios/transcripciones y enlace a evidencias.

### 7.3.3. Evaluaciones según heurísticas
- Resultados de evaluación heurística y acciones recomendadas.

## 7.4. Video About-the-Product
- Enlace al video demostrativo y breve guion.


## 7.5. Conclusiones

En base al trabajo realizado en las secciones previas (requerimientos, diseño UX/UI y arquitectura), se presentan las siguientes conclusiones resumidas y accionables:

- La solución propuesta (ReStyle) cubre las necesidades principales de los dos segmentos objetivo: contratistas (buscadores de servicios) y remodeladores (prestadores). Las funcionalidades clave son: búsqueda filtrada, portafolios, gestión de solicitudes/cotizaciones, seguimiento por hitos y chatbot de apoyo.
- El diseño UX prioriza coherencia visual, legibilidad y accesibilidad (esquema tipográfico, paleta y sistema de espaciado). Estas decisiones facilitan la adopción por usuarios con distintas habilidades digitales.
- La arquitectura definida (bounded contexts + APIs) soporta escalabilidad y separación de responsabilidades: Identity & Profiles, Discovery, Project & Quotation, Execution & Feedback, Payment, Subscriptions & Notifications.
- La implementación práctica exige prioridades técnicas: (1) API REST segura e idempotente; (2) índice público para discovery (read-model/Elastic o Postgres+GIS); (3) integración con PSP para flujos de pagos y webhooks; (4) worker/cola para procesos asíncronos (notificaciones, reindex).
- El esquema de datos simplificado (SQL entregado) permite arrancar con un modelo relacional sólido y evolucionar hacia índices / read-models cuando la carga lo requiera.
- Recomendación inmediata: implementar un plan de pruebas (usabilidad, cargas p95) y una guía mínima de despliegue que incluya claves de seguridad (idempotency, validación de webhooks, encriptación de tokens).

## 7.6. Bibliografía

- INEI. Censos y estadísticas nacionales (referencias citadas en Capítulo I). https://www.inei.gob.pe  
- Ipsos Perú. Estudio Construcción 2018. https://www.ipsos.com  
- Microsoft News Center LATAM — Aceleración digital (citado en Capítulo I). https://news.microsoft.com/latam  
- Apple Human Interface Guidelines. https://developer.apple.com/design/human-interface-guidelines/  
- Material Design (Google) / Material You. https://material.io  
- PostgreSQL Documentation. https://www.postgresql.org/docs/  
- Nielsen Norman Group — Usability & UX guidance. https://www.nngroup.com  


## 7.5. Anexos

A continuación se listan todos los enlaces y artefactos relevantes adjuntados al proyecto.

- Despliegues / Aplicaciones
  - Landing Page (GitHub Pages): https://si0728-7281-grupo3.github.io/landingpage/
  - Front (Web app - Netlify): https://restyle-1asi0728-7281.netlify.app
  - Backend (Swagger / API): https://restyle-platform-bed4c3b3f3eug0ak.canadacentral-01.azurewebsites.net/swagger-ui/index.html

- Diagramas (Capítulo V)
  - Diagramas de clases - Enlaces en las Capturas de los Diagramas del Capítulo V.
  - Structurizr: https://structurizr.com/workspace/82630/dsl
