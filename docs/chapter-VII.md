# Capítulo VII: Product Implementation, Validation & Deployment

## 7.1. Software Configuration Management

### 7.1.1. Software Development Environment Configuration
- Descripción de entornos (local, staging, production).
- Requisitos de herramientas (Node, Python, DB, Docker, etc.).
- Scripts de arranque y provisión.

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
- Objetivos del sprint.
- Criterios de aceptación.

#### 7.2.1.2. Sprint Backlog 1
- Lista de historias/tareas comprometidas.

#### 7.2.1.3. Development Evidence for Sprint Review
- Enlaces a commits, PRs y evidencias de funcionalidad.

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
