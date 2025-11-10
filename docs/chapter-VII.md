# Capítulo VII: Product Implementation, Validation & Deployment

## 7.1. Software Configuration Management

En este punto del informe se describen las decisiones y los principios que ayudarán al equipo a garantizar la coherencia durante el desarrollo de la solución.

### 7.1.1. Software Development Environment Configuration

En este apartado se listan las aplicaciones y productos de software usados durante el ciclo del proyecto, organizados por disciplina.

Project Management:
- Trello: Gestión de tareas y proyectos. https://trello.com/signup
- Miro: Planificación visual, mapas mentales y diagramas. https://miro.com/signup
- OneDrive: Almacenamiento y colaboración de documentos y recursos del proyecto (sustituye a Google Drive). https://www.microsoft.com/microsoft-365/onedrive/
- GitHub Desktop: Gestión local de repositorios y sincronización con GitHub. https://desktop.github.com/

Requirements Management:
- Lucidchart: Diagramado de flujos y requisitos. https://www.lucidchart.com/users/register
- Google Forms: Recolección de feedback y encuestas. https://www.google.com/forms/about/

Product UX/UI Design:
- Uxpressia: Mapas de impacto, Personas y Journey Maps. https://uxpressia.com
- Miro: Pizarra colaborativa para ideación y workshops. https://miro.com
- Figma: Prototipos, wireframes y diseños de UI. https://www.figma.com/signup
- Lucidchart / Overflow: Diagramación de flujos y userflows. https://www.lucidchart.com / https://overflow.io

Software Development:
- IDEs:
  - Visual Studio Code: principal IDE del equipo. https://code.visualstudio.com/download
  - Android Studio: emulación y pruebas móviles Android. https://developer.android.com/studio
- Control de Versiones: Git con integración a GitHub. https://git-scm.com/downloads
- Gestión de Dependencias:
  - Flutter Pub / Pub.dev (cuando aplica): https://pub.dev/
- Herramientas de Construcción:
  - Gradle (cuando aplica): https://docs.gradle.org/current/userguide/userguide.html

Software Testing:
- Lenguaje Gherkin para especificaciones ejecutables (BDD) y pruebas automatizadas.

Software Documentation:
- GitHub: documentación en README.md y wikis. https://github.com/join
- Structurizr: documentación de arquitectura. https://structurizr.com/

### 7.1.2. Source Code Management

Descripción del SCM adoptado y repositorios relevantes.

- Modelo de ramas: GitFlow (main, develop, feature/*, release/*, hotfix/*).
- Reglas: Pull requests con revisión por pares, CI en cada PR y protección de ramas.
- Organización / Repositorios (ejemplos):
  - Organización: SI0728-7281-Grupo3 - https://github.com/SI0728-7281-Grupo3
  - Landing page: https://github.com/SI0728-7281-Grupo3/landingpage
  - Frontend: https://github.com/SI0728-7281-Grupo3/frontend-main
  - Backend: https://github.com/SI0728-7281-Grupo3/backend-main
  - Mobile: https://github.com/SI0728-7281-Grupo3/mobile-main

GitFlow y convenciones:
- Ramas principales: main, develop.
- Ramas de soporte: feature/* (desde develop -> a develop), release/*, hotfix/* (desde main).
- Nomenclatura de features: feature/<short-desc>
- Commits: utilizar Conventional Commits (feat, fix, chore, docs, refactor, test, etc.)

### 7.1.3. Source Code Style Guide & Conventions

Pautas generales para mantener la legibilidad y calidad del código:

- Linters y formatters: ESLint + Prettier para JS/TS, formato consistente para HTML/CSS, reglas de estilo para Java/Flutter según linters oficiales.
- Convenciones de commits: Conventional Commits.
- Nomenclatura: nombres en inglés, descriptivos y consistentes; usar camelCase en JS/TS, PascalCase en clases Java/TS.

Especificaciones por lenguaje (resumen):
- HTML: DOCTYPE HTML5, atributos con comillas dobles, mantener <title>, líneas en blanco entre secciones.
- CSS: uso de shorthand, punto y coma en declaraciones, espacio después de ":".
- JavaScript / TypeScript: punto y coma al final, espacios alrededor de operadores, funciones con llave en la misma línea.
- Java: clases como sustantivos en PascalCase, métodos en camelCase, tratar excepciones con justificación.
- Gherkin: Given-When-Then con sangría clara; uso de tablas para valores; reducción de ruido con valores por defecto entre comillas simples.

(Ver sección completa de convenciones en la documentación del repo para ejemplos y plantillas.)

### 7.1.4. Software Deployment Configuration

Pautas de CI/CD, gestión de secretos y estrategias de despliegue:

- Pipelines: cada repositorio debe incluir pipeline CI que ejecute lint, tests y build. PRs ejecutan CI; merges a main disparan CD.
- Variables y secretos: uso de GitHub Secrets / KeyVault / Azure App Configuration según entorno.
- Estrategias de despliegue: rolling/blue-green para servicios críticos; Canary releases para funciones nuevas.
- Documentación de pasos de despliegue en cada repo (README / docs/deploy.md).

## 7.2. Solution Implementation

### 7.2.1. Sprint 1

#### 7.2.1.1. Sprint Planning 1

Sprint # | Sprint 1
---|---
Sprint Planning Background |
Date | YYYY-MM-DD
Time | HH:MM AM/PM
Location | (Descripción de la ubicación de la reunión, física o virtual)
Prepared By | Jiménez Rosas, Arturo Eduardo
Attendees (planning meeting) | Jiménez Rosas, Arturo Eduardo / Rodríguez Peña, Jorge Andrés / ...
Sprint n−1 — Review Summary | (Resumen del Sprint anterior: resultados entregados, feedback del Product Owner)
Sprint n−1 — Retrospective Summary | (Lecciones aprendidas y oportunidades de mejora)
Sprint n Goal | (Definir el objetivo del Sprint n y la métrica de cumplimiento)
Sprint n Velocity | (Velocidad en Story Points que el equipo puede aceptar)
Sum of Story Points | (Suma total de Story Points comprometidos)

Notas:
- Definir criterios de aceptación antes de cerrar la planificación.
- Identificar dependencias y asignar responsables.
- Registrar enlaces a tablero, issues y PRs en "Development Evidence".

#### 7.2.1.2. Sprint Backlog 1

Sprint # | Sprint 1
---|---
User Story Id | User Story Title | Work-Item Id | Work-Item Title | Description | Estimation (Hours) | Assigned To | Status
US-001 |  | WI-001 |  |  |  |  | To-do / InProcess / ToReview / Done
US-002 |  | WI-002 |  |  |  |  | To-do / InProcess / ToReview / Done
US-003 |  | WI-003 |  |  |  |  | To-do / InProcess / ToReview / Done
US-004 |  | WI-004 |  |  |  |  | To-do / InProcess / ToReview / Done
US-005 |  | WI-005 |  |  |  |  | To-do / InProcess / ToReview / Done

(Agregar/duplicar filas según sea necesario.)

#### 7.2.1.3. Development Evidence for Sprint Review

Registro de commits y evidencias relacionados al Sprint (rellenar con enlaces reales):

Repository | Branch | Commit Id | Commit Message | Commit Message Body | Committed on (Date)
---|---|---|---|---|---
user/repositoryname | feature/branch-name | 14ca4e3 | feat: breve descripción | Descripción extendida del cambio y referencias a issues/PRs. | YYYY-MM-DD

(Incluir PRs, enlaces a issues y capturas de demo.)

#### 7.2.1.4. Testing Suite Evidence for Sprint Review
- Resultados de pruebas unitarias, integración y pruebas end-to-end. Referenciar reportes de CI (links) y capturas de la ejecución.

#### 7.2.1.5. Execution Evidence for Sprint Review
- Logs, capturas de pantalla, enlaces a demos y vídeos de la funcionalidad implementada.

#### 7.2.1.6. Services Documentation Evidence for Sprint Review
- Endpoints documentados en Swagger / OpenAPI. Incluir URL de Swagger en el anexo.

#### 7.2.1.7. Software Deployment Evidence for Sprint Review
- Despliegues realizados (staging/production) y URL de acceso. Incluir capturas y fecha/hora.

#### 7.2.1.8. Team Collaboration Insights during Sprint
- Retrospectiva breve y lecciones aprendidas.

(Replicar estructura para Sprint 2..N según avance.)

## 7.3. Validation Interviews

### 7.3.1. Diseño de Entrevistas
- Objetivos, guion de preguntas y criterios de selección de participantes.

### 7.3.2. Registro de Entrevistas
- Resumen de respuestas, transcripciones y enlaces a grabaciones/archivos.

### 7.3.3. Evaluaciones según heurísticas
- Resultados de evaluación heurística (Nielsen) y recomendaciones de mejora.

## 7.4. Video About-the-Product
- Enlace al video demostrativo y guion breve. (Incluir URL y timestamp de secciones clave.)

## 7.5. Conclusiones

En base al trabajo realizado en las secciones previas, se presentan las siguientes conclusiones y recomendaciones:

- La solución propuesta cubre las necesidades principales de los segmentos objetivo y prioriza funcionalidades esenciales: búsqueda, portafolios, solicitudes/cotizaciones, seguimiento por hitos.
- El diseño UX favorece coherencia, accesibilidad y adaptabilidad a dispositivos.
- La arquitectura en bounded contexts garantiza separación de responsabilidades y escalabilidad.
- Recomendaciones: (1) API segura e idempotente; (2) read-model para discovery; (3) integración robusta con PSP y validación de webhooks; (4) cola/worker para tareas asíncronas.
- Implementar plan de pruebas, validación de rendimiento y guía de despliegue segura.

## 7.6. Bibliografía

- INEI. https://www.inei.gob.pe  
- Ipsos Perú. https://www.ipsos.com  
- Microsoft News Center LATAM. https://news.microsoft.com/latam  
- Apple Human Interface Guidelines. https://developer.apple.com/design/human-interface-guidelines/  
- Material Design. https://material.io  
- PostgreSQL Documentation. https://www.postgresql.org/docs/  
- Nielsen Norman Group. https://www.nngroup.com

## 7.7. Anexos

Enlaces y artefactos relevantes del proyecto:

- Despliegues / Aplicaciones:
  - Landing Page (repo): https://github.com/SI0728-7281-Grupo3/landingpage
  - Frontend (repo): https://github.com/SI0728-7281-Grupo3/frontend-main
  - Backend (repo): https://github.com/SI0728-7281-Grupo3/backend-main
  - Mobile (repo): https://github.com/SI0728-7281-Grupo3/mobile-main

- Diagramas y documentación:
  - Diagramas del Capítulo V: report/assets/img/chapter-V/Diagrams-BC/
  - Vertabelo project: vertabelo-db-diagram/diagrams/vertabelo/vertabelo-project.vdb
  - SQL exports: vertabelo-db-diagram/diagrams/exports/ (erd.sql, erd.xml, erd.json)
  - Esquemas SQL: vertabelo-db-diagram/sql/schema/01_schema.sql, vertabelo-db-diagram/sql/schema/02_simple_schema.sql

- Repositorios (ejemplos):
  - Organización / repos: ver sección 7.1.2 (URLs)

- Checklist de entrega mínima:
  - Endpoints documentados en Swagger.
  - Esquema SQL aplicado en staging.
  - Webhooks con verificación HMAC y pruebas de idempotencia.
  - Worker/cola configurada para tareas asíncronas.
  - Plan de pruebas de usabilidad y pruebas de rendimiento básicas.

-- Fin de Capítulo VII
