
# Capítulo IV: Product UX/UI Design

## 4.1. Strategic-Level Attribute-Driven Design

En esta sección detallamos el proceso de Attribute-Driven Design (ADD) aplicado en el desarrollo de la solución ReStyle. El objetivo del ADD es orientar el diseño arquitectónico basándose en atributos de calidad críticos para la plataforma, tales como usabilidad, disponibilidad, escalabilidad y seguridad, fundamentales para el éxito de la aplicación en la gestión integral de proyectos de remodelación del hogar.

Este enfoque metodológico permite crear una arquitectura sólida que facilite la conexión eficiente entre usuarios finales y profesionales del sector, optimizando la experiencia de remodelación a través de herramientas digitales avanzadas. La implementación del ADD garantiza que ReStyle pueda manejar el crecimiento de su base de usuarios mientras mantiene altos estándares de rendimiento y confiabilidad.

La aplicación de este diseño dirigido por atributos mejora significativamente el proceso tradicional de remodelación al proporcionar una plataforma centralizada que eleva la calidad del servicio, reduce tiempos de gestión y aumenta la transparencia en cada fase del proyecto. Esto resulta en una experiencia superior tanto para propietarios que buscan remodelar sus hogares como para profesionales que desean expandir su alcance comercial y optimizar sus operaciones.

### 4.1.1. Design Purpose

El propósito del diseño de ReStyle es crear una plataforma integral que revolucione la experiencia de remodelación del hogar mediante la conexión eficiente entre usuarios y profesionales especializados. El diseño busca establecer un ecosistema digital que simplifique y optimice cada etapa del proceso de remodelación, desde la conceptualización hasta la ejecución final.

El diseño busca satisfacer las siguientes necesidades:

- Proporcionar a los usuarios una herramienta centralizada para gestionar completamente sus proyectos de remodelación del hogar.
- Facilitar a los profesionales del sector una plataforma robusta para promocionar sus servicios y administrar sus operaciones comerciales.
- Garantizar transparencia y control total del proyecto mediante seguimiento en tiempo real y gestión integrada de recursos.
- Establecer una arquitectura escalable que soporte el crecimiento sostenido de la comunidad de usuarios y profesionales.

Este diseño busca transformar la industria de la remodelación doméstica, eliminando las fricciones tradicionales del sector y creando una experiencia fluida que beneficie tanto a propietarios como a prestadores de servicios, cumpliendo con las expectativas de eficiencia y calidad en el mercado actual.

### 4.1.2. Attribute-Driven Design Inputs 
En esta sección se detallan los tres tipos de entradas clave que guían el proceso de diseño arquitectónico bajo el enfoque de ADD. Estas entradas están directamente relacionadas con la funcionalidad principal, los atributos de calidad y las restricciones impuestas por el negocio y la tecnología.

---

#### 4.1.2.1. Primary Functionality (Primary User Stories).
Los User Stories seleccionados para esta sección tienen un impacto directo en las decisiones arquitectónicas, ya que representan la funcionalidad principal que debe soportar la plataforma para satisfacer las necesidades de los usuarios.

| Epic / User Story ID | Título | Descripción | Criterios de Aceptación (resumen) | Epic ID |
|---|---|---|---|---|
| US-007 | Búsqueda de empresas remodeladoras | Como contratista, buscar remodeladoras por **ubicación** o **expertise** para obtener resultados personalizados. | Filtra por ubicación/expertise; sin filtros muestra todas las remodeladoras disponibles. | EPIC-001 |
| US-014 | Búsqueda de portafolios | Como contratista, buscar y abrir portafolios para revisar trabajos previos. | Lista de portafolios; al seleccionar uno, redirige al perfil del remodelador. | EPIC-001 |
| US-008 | Revisar críticas y opiniones | Como contratista, ver opiniones de otros clientes para evaluar calidad. | Lista de reviews en el perfil; navegación hacia portafolio desde una review. | EPIC-001 |
| US-009 | Agregar críticas y opiniones | Como contratista, publicar una reseña tras un proyecto. | Formulario con validación; guarda y confirma éxito; no guarda si no se confirma. | EPIC-001 |
| US-016 | Programar consulta con un remodelador | Como propietario, agendar una consulta para discutir necesidades y obtener recomendaciones. | Opción de contacto; confirmación/aviso de la consulta al usuario. | EPIC-001 |
| US-006 | Subir contenido a un portafolio | Como remodelador, subir multimedia a su portafolio para promocionar servicios y proyectos. | Muestra contenidos subidos; alerta si no guarda; valida límites de carga. | EPIC-005 |
| US-015 | Seguimiento de proyecto | Como remodelador, ver hitos/etapas y estado del proyecto. | Visualiza hitos; puede marcar cumplimiento; cerrar proyecto al completar todos. | EPIC-006 |
| US-023 | Interacción básica con el chatbot en app web | Como usuario, hacer preguntas básicas al chatbot para obtener respuestas rápidas. | Responde “¿Cómo cambio mi contraseña?” en **< 3 s**; sugiere reformular o derivar a humano. | EPIC-008 |
| US-024 | Consulta de presupuestos estimados vía chatbot | Como contratista, obtener un rango de costos (tipo, m², ubicación). | Flujo “Calcular presupuesto”; si es complejo, sugiere contactar/agendar. | EPIC-008 |
| US-025 | Derivación a soporte humano desde chatbot | Como usuario, ser derivado a un agente si el bot no resuelve. | Deriva con historial tras 2 intentos; fuera de horario permite dejar mensaje con promesa **< 24 h**. | EPIC-008 |
| US-010 | Gestión de solicitudes al servidor | Como desarrollador, asegurar que el API gestiona múltiples solicitudes concurrentes. | Bajo carga, mantiene tiempo de respuesta promedio y no hay caídas. | EPIC-003 |
| US-011 | Autorización y seguridad de acceso al API | Como desarrollador, configurar AuthN/AuthZ segura (solo **admin** a recursos críticos). | Acceso permitido con credenciales válidas; denegado y notificado en intentos inválidos. | EPIC-003 |

---

#### 4.1.2.2. Quality attribute Scenarios.
Los escenarios de atributos de calidad identificados tienen un impacto significativo en la arquitectura de la solución, ya que determinan cómo debe comportarse el sistema en términos de seguridad, escalabilidad, disponibilidad y rendimiento.

| Atributo | Fuente | Estímulo | Artefacto | Entorno | Respuesta | Medida |
|---|---|---|---|---|---|---|
| Seguridad | Usuario no autorizado | Intenta acceder a recursos del API reservados a **admin** | API + AuthN/AuthZ | Acceso público | Bloqueo de acceso y notificación | 0 accesos indebidos; registro del intento |
| Escalabilidad | Aumento de concurrencia | Solicitudes simultáneas desde varios dispositivos | API REST | Alta demanda | API opera sin errores/caídas | Tiempo de respuesta en rango promedio; servicio estable |
| Rendimiento | Usuario del chatbot | Pregunta frecuente en app web | Chatbot | Producción | Respuesta visible y útil | **p95 < 3 s** por respuesta |
| Continuidad de atención | Usuario del chatbot | Bot no entiende / no hay agentes disponibles | Chatbot ↔ Soporte humano | Operación | Derivación con historial u opción de dejar mensaje | Respuesta comprometida **< 24 h** |
| Exactitud (NLP) | Servicio de NLP | Mensaje con intención clara/ambigua | Motor NLP del bot | Normal | Identifica intención o marca “no reconocida” | Confianza ≥ **85%**; si < **60%**, pedir aclaración |
| Rendimiento (KB) | Consulta del bot | Búsqueda de FAQ/guías | Base de conocimientos | Normal | Devuelve respuesta precisa | Latencia **< 100 ms** por consulta |

---

#### 4.1.2.3. Constraints.
Las restricciones representan características no negociables impuestas por el cliente o por necesidades del negocio. En ReStyle, estas restricciones aseguran que la solución se ajuste a expectativas técnicas y operativas de la plataforma (especialmente para el **chatbot** y la **integración API**).

| Technical Story ID | Título | Descripción | Criterios de Aceptación | Epic ID |
|---|---|---|---|---|
| TS009 | Implementar API de integración del chatbot | API RESTful para integrar el chatbot con la app web (envío/recepción de mensajes e historial). | POST válido devuelve respuesta del bot (sessionId, intent, confidence); maneja errores 400 ante payload inválido; GET historial por sessionId. | EPIC-008 |
| TS010 | Implementar servicio de procesamiento de lenguaje natural | Servicio NLP para entender intenciones y extraer entidades. | Identifica intención con **≥85%** de confianza; si **<60%**, devuelve “intención_no_reconocida”; reentrenamiento sin downtime. | EPIC-008 |
| TS011 | Implementar base de conocimientos para chatbot | KB con preguntas frecuentes y contenido de soporte. | ≥50 FAQs; respuesta **<100 ms**; actualización vía API disponible de inmediato; registra consultas sin resultado. | EPIC-008 |
| TS012 | Implementar integración con sistema de soporte humano | Derivación fluida a agente con transferencia de historial. | Crea ticket, transfiere historial; si no hay agentes, informa ETA y ofrece contacto posterior. | EPIC-008 |

### 4.1.3. Architectural Drivers Backlog.

<table>
    <thead>
        <tr>
            <th>Driver ID</th>
            <th>Titulo de Driver</th>
            <th>Descripción </th>
            <th>Importancia para Stakeholders (High, Medium, Low)</th>
            <th>Impacto en Architecture Technical Complexity (High, Medium, Low)</th>
        </tr>
    </thead>
    <body>
        <tr>
            <td>QA-SEC-01</td>
            <td>Seguridad en acceso al API</td>
            <td>Garantizar autenticación y autorización robusta para proteger recursos críticos del sistema.</td>
            <td>High</td><td>High</td>
        </tr>
        <tr>
            <td>QA-SCA-01</td>
            <td>Escalabilidad bajo alta concurrencia</td>
            <td>El sistema debe manejar múltiples solicitudes simultáneas sin caída del servicio.</td>
            <td>High</td><td>High</td>
        </tr>
        <tr>
            <td>QA-PERF-01</td>
            <td>Rendimiento de chatbot</td>
            <td>El chatbot debe responder consultas frecuentes en menos de 3 segundos (p95).</td>
            <td>High</td><td>High</td>
        </tr>
        <tr>
            <td>QA-AV-01</td>
            <td>Continuidad de atención vía chatbot/soporte humano</td>
            <td>El sistema debe garantizar atención incluso si el bot falla, derivando al soporte humano.</td>
            <td>High</td><td>Medium</td>
        </tr>
        <tr>
            <td>QA-NLP-01</td>
            <td>Exactitud en interpretación del NLP</td>
            <td>El motor NLP debe identificar intenciones con ≥85% de confianza.</td>
            <td>High</td><td>Medium</td>
        </tr>
    </body>
</table>

### 4.1.4. Architectural Design Decisions. 

<table>
    <thead>
        <tr>
            <th rowspan="2">Drive ID</th>
            <th rowspan="2">Titulo de Driver</th>
            <th colspan="2">MVC</th>
            <th colspan="2">Capas</th>
            <th colspan="2">Cliente-Servidor</th>
        </tr>
        <tr>
            <th>Pros</th>
            <th>Contras</th>
            <th>Pros</th>
            <th>Contras</th>
            <th>Pros</th>
            <th>Contras</th>
        </tr>
    </thead>
    <body>
        <tr>
            <td>QA-SEC-01</td>
            <td>Seguridad en acceso al API</td>
            <td>Separación clara de responsabilidades; facilita integrar validaciones en controladores; frameworks maduros (Spring, Django).</td>
            <td>Seguridad depende de configuración adicional (middlewares, filtros); no es intrínsecamente seguro.</td>
            <td>Seguridad puede centralizarse en la capa de negocio/servicios; permite aislar la lógica de autorización.</td>
            <td>Posible sobrecarga en validaciones repetidas entre capas; mayor complejidad en trazabilidad de accesos.</td>
            <td>Control centralizado de accesos en el servidor; fácil de auditar; clientes no exponen lógica sensible.</td>
            <td>Escalabilidad limitada si todo pasa por un servidor central; el cliente depende totalmente de la robustez del servidor.</td>
        </tr>
        <tr>
            <td>QA-SCA-01</td>
            <td>Escalabilidad bajo alta concurrencia</td>
            <td>Fácil escalado horizontal de controladores; frameworks ofrecen soporte a múltiples requests concurrentes.</td>
            <td>No maneja concurrencia masiva por sí solo; requiere balanceadores externos.</td>
            <td>Permite distribuir carga entre capas (ej. balancear capa web y capa de datos); flexible para crecer.</td>
            <td>Cada capa añade latencia; complejidad en coordinar escalado independiente.</td>
            <td>Modelo simple; clientes múltiples pueden conectarse a un servidor.</td>
            <td>El servidor es cuello de botella; escalabilidad limitada sin replicación o clusterización.</td>
        </tr>
        <tr>
            <td>QA-PERF-01</td>
            <td>Rendimiento de chatbot</td>
            <td>Controladores ligeros permiten respuestas rápidas; caching fácil en capa de presentación/control.</td>
            <td>Si la lógica NLP es pesada, MVC no mitiga la latencia; depende del backend.</td>
            <td>Optimización por capas (capa de aplicación puede cachear, capa de datos optimizar consultas).</td>
            <td>Latencia añadida si las capas no están bien optimizadas; riesgo de sobreingeniería.</td>
            <td>Comunicación directa cliente-servidor minimiza intermediarios; rápido en escenarios simples.</td>
            <td>No soporta fácilmente concurrencia alta; depende de la potencia del servidor.</td>
        </tr>
        <tr>
            <td>QA-AV-01</td>
            <td>Continuidad de atención vía chatbot/soporte humano</td>
            <td>Permite redirigir tráfico desde controlador a chatbot o soporte humano sin romper flujo.</td>
            <td>Manejo de fallback puede complejizarse; no está diseñado para resiliencia.</td>
            <td>Cada capa puede manejar fallbacks; facilita desacoplar chatbot de soporte.</td>
            <td>Riesgo de latencia por pasos extra; aumenta puntos de falla intermedios.</td>
            <td>Sencillo: si el servidor falla, se deriva a otro canal humano.</td>
            <td>Depende de disponibilidad del servidor principal; no asegura continuidad automatizada.</td>
        </tr>
        <tr>
            <td>QA-NLP-01</td>
            <td>Exactitud en interpretación del NLP</td>
            <td>Controladores permiten encapsular y probar distintos modelos NLP en el backend; fácil integración.</td>
            <td>No facilita combinar múltiples motores NLP; poca flexibilidad en flujo ML complejo.</td>
            <td>La capa de negocio puede concentrar lógica NLP y facilitar reentrenamiento; escalable en la capa de aplicación.</td>
            <td>Aumenta latencia si el flujo atraviesa varias capas; más difícil debug de errores NLP.</td>
            <td>NLP centralizado en el servidor, simplifica mantenimiento y mejora exactitud al usar un modelo único.</td>
            <td>Escalabilidad y tiempos de respuesta limitados; el servidor es único punto de falla.</td>
        </tr>
    </body>
</table>

### 4.1.5. Quality Attribute Scenario Refinements.
Tras culminar el Quality Attribute Workshop (QAW), el equipo priorizó los escenarios de atributos de calidad que representan los principales riesgos y preocupaciones arquitectónicas para nuestra plataforma ReStyle. La discusión se centró en los drivers seleccionados
Durante el proceso, se refinaron los escenarios considerando los objetivos de negocio, las fuentes de estímulos más probables, los artefactos involucrados y las respuestas esperadas con medidas cuantitativas. El resultado es la versión final de escenarios refinados, organizados en orden de prioridad según impacto en stakeholders y complejidad técnica.

<table>
    <thead>
        <tr>
            <th colspan="3">Scenario Refinement for Scenario 1</th>
        </tr>
    </thead>
    <body>
        <tr>
            <td colspan="2">Scenarios:</td>
            <td>Intento de acceso indebido al API con credenciales inválidas.</td>
        </tr>
        <tr>
            <td colspan="2">Business Goals:</td>
            <td>Proteger recursos críticos y garantizar confianza en la plataforma.</td>
        </tr>
        <tr>
            <td colspan="2">Relevant Quality Attributes:</td>
            <td>Seguridad.</td>
        </tr>
        <tr>
            <td rowspan="7">Scenario Components</td>
        </tr>
        <tr>
            <td>Stimulus:</td>
            <td>Usuario no autorizado intenta acceder al endpoint reservado a administradores.</td>
        </tr>
        <tr>
            <td>Stimulus Source:</td>
            <td>Usuario externo no autenticado.</td>
        </tr>
        <tr>
            <td>Environment:</td>
            <td>Producción, acceso público a la API.</td>
        </tr>
        <tr>
            <td>Artifact (if Known)</td>
            <td>API Gateway</td>
        </tr>
        <tr>
            <td>Response:</td>
            <td>Bloqueo de acceso, registro del intento, notificación de alerta.</td>
        </tr>
        <tr>
            <td>Response Measure:</td>
            <td>0 accesos indebidos permitidos; 100% intentos loggeados.</td>
        </tr>
        <tr>
            <td colspan="2">Questions:</td>
            <td>¿Qué nivel de logging es suficiente sin comprometer rendimiento?</td>
        </tr>
        <tr>
            <td colspan="2">Issues:</td>
            <td>Equilibrar seguridad estricta con experiencia de usuario (falsos positivos).</td>
        </tr>
    </body>
</table>

<table>
    <thead>
        <tr>
            <th colspan="3">Scenario Refinement for Scenario 2</th>
        </tr>
    </thead>
    <body>
        <tr>
            <td colspan="2">Scenarios:</td>
            <td>Múltiples usuarios realizan solicitudes concurrentes a la API.</td>
        </tr>
        <tr>
            <td colspan="2">Business Goals:</td>
            <td>Garantizar que la plataforma escale con el crecimiento de usuarios.</td>
        </tr>
        <tr>
            <td colspan="2">Relevant Quality Attributes:</td>
            <td>Escalabilidad.</td>
        </tr>
        <tr>
            <td rowspan="7">Scenario Components</td>
        </tr>
        <tr>
            <td>Stimulus:</td>
            <td>Aumento repentino de solicitudes simultáneas desde clientes web y móviles.</td>
        </tr>
        <tr>
            <td>Stimulus Source:</td>
            <td>Usuarios concurrentes.</td>
        </tr>
        <tr>
            <td>Environment:</td>
            <td>Producción, hora pico.</td>
        </tr>
        <tr>
            <td>Artifact (if Known)</td>
            <td>API REST, balanceador de carga.</td>
        </tr>
        <tr>
            <td>Response:</td>
            <td>Sistema procesa solicitudes sin errores ni caídas.</td>
        </tr>
        <tr>
            <td>Response Measure:</td>
            <td>Tiempo de respuesta ≤ 2 s bajo 1000 solicitudes concurrentes.</td>
        </tr>
        <tr>
            <td colspan="2">Questions:</td>
            <td>¿Cuáles son los límites de escalado automático aceptables en costo?</td>
        </tr>
        <tr>
            <td colspan="2">Issues:</td>
            <td>Riesgo de saturación si la infraestructura cloud no escala a tiempo.</td>
        </tr>
    </body>
</table>

<table>
    <thead>
        <tr>
            <th colspan="3">Scenario Refinement for Scenario 3</th>
        </tr>
    </thead>
    <body>
        <tr>
            <td colspan="2">Scenarios:</td>
            <td>Usuario hace una consulta frecuente al chatbot.</td>
        </tr>
        <tr>
            <td colspan="2">Business Goals:</td>
            <td>Proporcionar experiencia de atención rápida y confiable.</td>
        </tr>
        <tr>
            <td colspan="2">Relevant Quality Attributes:</td>
            <td>Rendimiento.</td>
        </tr>
        <tr>
            <td rowspan="7">Scenario Components</td>
        </tr>
        <tr>
            <td>Stimulus:</td>
            <td>Usuario ingresa pregunta común.</td>
        </tr>
        <tr>
            <td>Stimulus Source:</td>
            <td>Usuario final.</td>
        </tr>
        <tr>
            <td>Environment:</td>
            <td>Producción, app web.</td>
        </tr>
        <tr>
            <td>Artifact (if Known)</td>
            <td>Chatbot + motor NLP + base de conocimientos.</td>
        </tr>
        <tr>
            <td>Response:</td>
            <td>Chatbot responde de forma precisa y rápida.
</td>
        </tr>
        <tr>
            <td>Response Measure:</td>
            <td>Tiempo de respuesta p95 < 3 s.</td>
        </tr>
        <tr>
            <td colspan="2">Questions:</td>
            <td>¿Qué ocurre con consultas complejas que requieren soporte humano?</td>
        </tr>
        <tr>
            <td colspan="2">Issues:</td>
            <td>Latencia si el motor NLP está sobrecargado.</td>
        </tr>
    </body>
</table>

<table>
    <thead>
        <tr>
            <th colspan="3">Scenario Refinement for Scenario 4</th>
        </tr>
    </thead>
    <body>
        <tr>
            <td colspan="2">Scenarios:</td>
            <td>El chatbot no entiende la consulta y no hay agentes disponibles.</td>
        </tr>
        <tr>
            <td colspan="2">Business Goals:</td>
            <td>Garantizar continuidad de atención para no perder usuarios.</td>
        </tr>
        <tr>
            <td colspan="2">Relevant Quality Attributes:</td>
            <td>Disponibilidad.</td>
        </tr>
        <tr>
            <td rowspan="7">Scenario Components</td>
        </tr>
        <tr>
            <td>Stimulus:</td>
            <td>Usuario recibe respuesta “intención no reconocida” y no hay agentes conectados.</td>
        </tr>
        <tr>
            <td>Stimulus Source:</td>
            <td>Usuario final.</td>
        </tr>
        <tr>
            <td>Environment:</td>
            <td>Producción, fuera de horario laboral.</td>
        </tr>
        <tr>
            <td>Artifact (if Known)</td>
            <td>Chatbot, integración con sistema de soporte humano.</td>
        </tr>
        <tr>
            <td>Response:</td>
            <td>Opción de dejar mensaje/ticket con confirmación de respuesta < 24 h.</td>
        </tr>
        <tr>
            <td>Response Measure:</td>
            <td>100% consultas no resueltas quedan registradas y con ETA informado.</td>
        </tr>
        <tr>
            <td colspan="2">Questions:</td>
            <td>¿Cómo garantizar respuesta real dentro de las 24 h?</td>
        </tr>
        <tr>
            <td colspan="2">Issues:</td>
            <td>Riesgo de frustración del usuario si no se cumple SLA.</td>
        </tr>
    </body>
</table>

<table>
    <thead>
        <tr>
            <th colspan="3">Scenario Refinement for Scenario 5</th>
        </tr>
    </thead>
    <body>
        <tr>
            <td colspan="2">Scenarios:</td>
            <td>Chatbot recibe mensaje ambiguo y el NLP debe interpretarlo.</td>
        </tr>
        <tr>
            <td colspan="2">Business Goals:</td>
            <td>Mejorar exactitud de interpretación para evitar errores en respuestas.</td>
        </tr>
        <tr>
            <td colspan="2">Relevant Quality Attributes:</td>
            <td>Exactitud (NLP).</td>
        </tr>
        <tr>
            <td rowspan="7">Scenario Components</td>
        </tr>
        <tr>
            <td>Stimulus:</td>
            <td>Usuario envía mensaje con intención ambigua.</td>
        </tr>
        <tr>
            <td>Stimulus Source:</td>
            <td>Usuario final.</td>
        </tr>
        <tr>
            <td>Environment:</td>
            <td>Producción, interacción normal.</td>
        </tr>
        <tr>
            <td>Artifact (if Known)</td>
            <td>Motor NLP del chatbot.</td>
        </tr>
        <tr>
            <td>Response:</td>
            <td>El motor NLP identifica intención con confianza ≥ 85% o solicita aclaración.</td>
        </tr>
        <tr>
            <td>Response Measure:</td>
            <td>≥ 85% precisión en intenciones reconocidas; si confianza < 60%, se pide reformulación.</td>
        </tr>
        <tr>
            <td colspan="2">Questions:</td>
            <td>¿Qué dataset es necesario para mantener precisión ≥ 85%?</td>
        </tr>
        <tr>
            <td colspan="2">Issues:</td>
            <td>Riesgo de sesgos en el modelo NLP; costo de reentrenamiento frecuente.</td>
        </tr>
    </body>
</table>

## 4.2. Strategic-Level Domain-Driven Design.

### 4.2.1. EventStorming.


**Resumen del recorrido**
- **Onboarding & Perfiles:** registro de contratistas/remodeladores y publicación de perfiles.
- **Discovery:** búsqueda y filtrado por ubicación, expertise y reputación.
- **Solicitud & Cotización:** request → visita técnica → cotizaciones → aceptación.
- **Pagos:** autorización/captura/reembolso bajo reglas de negocio.
- **Ejecución:** hitos, evidencias, cierre.
- **Reseñas y Notificaciones.**
- **Suscripciones** (planes premium).

**Reglas visibles**
- `QuoteAccepted` ⇒ habilita **Authorize/Capture** en *Payment*.
- `ReviewSubmitted` solo si `ProjectCompleted`.
- Indexar únicamente perfiles **públicos y completos**.

<img src="..\assets/img/chapter-IV-j/4.1.png" alt="EventStorming — tablero general" width="800">

---

### 4.2.2. Candidate Context Discovery.


**Bounded Contexts candidatos**
1. **Identity & Profiles** — autenticación y perfiles públicos.
2. **Discovery (Search & Indexing)** — indexación/consulta de proveedores.
3. **Project & Quotation** — solicitud, visitas, cotizaciones y aceptación.
4. **Execution & Feedback** — hitos, evidencias, cierre y reseñas.
5. **Payment** — autorización/captura/reembolso con PSP externo.
6. **Subscriptions & Notifications** — planes premium y orquestación de email/push.

**Eventos pivote que delimitan contextos**
- `QuoteAccepted`, `PaymentCaptured`, `ProjectCompleted`.

<img src="..\assets/img/chapter-IV-j/4.2.png" alt="Candidate Context Discovery sobre el timeline" width="800">

---

### 4.2.3. Domain Message Flows Modeling.

> **Escenario narrado (Domain Storytelling):** *Contratar una remodelación en ReStyle*.

**Historia resumida**
1. *Contractor* crea cuenta → **Identity & Profiles** (IdP externo).
2. Busca remodeladores → **Discovery** devuelve resultados.
3. Envía solicitud → **Project & Quotation** crea `ProjectRequest`.
4. *Remodeler* cotiza; *Contractor* acepta → `QuoteAccepted`.
5. **Project & Quotation** solicita **Payment.Authorize**; al confirmar agenda → **Payment.Capture**.
6. **Execution & Feedback** inicia proyecto, completa hitos con evidencias.
7. *Contractor* publica reseña.
8. **Subscriptions & Notifications** envía notificaciones y gestiona planes.

**Sistemas externos:** *Payment Gateway* (PSP), *Email/Push Service*.

<img src="..\assets/img/chapter-IV-j/4.3.png" alt="Domain Storytelling — escenario integrado" width="800">

---

### 4.2.4. Bounded Context Canvases.


**Identity & Profiles**  
– Propósito: autenticar usuarios y administrar perfiles públicos.  
– Decisiones: email único/verificado, consentimiento para perfil público, solo perfiles completos se indexan.  
<img src="..\assets/img/chapter-IV-j/4.41.png" alt="Canvas — Identity & Profiles" width="800">

**Discovery (Search & Indexing)**  
– Propósito: encontrar remodeladores e indexar perfiles/proyectos.  
– Decisiones: ranking por *score* (distancia + rating + actividad + completitud).  
<img src="..\assets/img/chapter-IV-j/4.42.png" alt="Canvas — Discovery (Search & Indexing)" width="800">

**Project & Quotation**  
– Propósito: gestionar solicitud, visitas, cotizaciones y aceptación.  
– Decisiones: solo 1 cotización aceptada; vigencia; visita técnica requerida.  
<img src="..\assets/img/chapter-IV-j/4.43.png" alt="Canvas — Project & Quotation" width="800">

**Payment**  
– Propósito: autorizar, capturar y reembolsar pagos.  
– Decisiones: idempotencia por `RequestId`, reglas de captura, reembolsos parciales.  
<img src="..\assets/img/chapter-IV-j/4.44.png" alt="Canvas — Payment" width="800">

**Execution & Feedback**  
– Propósito: controlar hitos/evidencias y reseñas al cierre.  
– Decisiones: cerrar hito con evidencia; reseña solo tras `ProjectCompleted`.  
<img src="..\assets/img/chapter-IV-j/44.png" alt="Canvas — Execution & Feedback" width="800">

---

### 4.2.5. Context Mapping.

**Baseline (seleccionada)**
- **Identity & Profiles → Discovery**: **Conformist (events)** para cambios de perfil indexables.
- **Project & Quotation → Payment**: **Customer/Supplier (Authorize)**.
- **Execution & Feedback → Payment**: **Customer/Supplier (Capture/Refund)**.
- **Subscriptions & Notifications ↔ Payment**: **Customer/Supplier (Recurring/Dunning)**.
- Gateways + **ACL** hacia **External IdP** y **PSP**.

<img src="..\assets/img/chapter-IV-j/4.5.png" alt="Context Mapping — baseline y relaciones" width="800">

**Alternativas analizadas (resumen)**
- **Discovery dividido (Indexer + Search API):** +escala/+experimentos; −más contratos.
- **Shared Kernel entre Project & Execution:** +consistencia; −acoplamiento.



## 4.3. Software Architecture
Esta sección presenta la arquitectura de ReStyle siguiendo C4. Incluye el panorama global del ecosistema (System Landscape), el contexto del sistema (System Context) y el desglose de contenedores internos (Container). Al final se deja el espacio para el diagrama de despliegue (Deployment).

Structurizr: https://structurizr.com/workspace/82630/dsl

### 4.3.1. Software Architecture System Landscape Diagram.
El diagrama de landscape muestra los **actores principales** (Propietario, Profesional, Administrador), el **sistema ReStyle** y los **sistemas externos** (pasarela de pagos, identidad, almacenamiento de objetos, etc.), así como sus relaciones a alto nivel.

![System Landscape Diagram](../assets/img/chapter-IV-j/C4%20-%20Diagrams/System%20Landscape%20Diagram.png)

---

### 4.3.1. Software Architecture Context Level Diagrams.
El diagrama de contexto detalla las **interacciones** entre los actores y el sistema ReStyle, así como las **dependencias** con servicios externos (LLM, visión por computador, mapas, notificaciones, etc.).

![System Context Diagram](../assets/img/chapter-IV-j/C4%20-%20Diagrams/System%20Context%20Diagram.png)

---

### 4.3.2. Software Architecture Container Level Diagrams.
El diagrama de contenedores describe los **bounded contexts / microservicios**, el **API Gateway**, los **frontends** (Web/Mobile) y las **persistencias**. Permite entender responsabilidades y límites de cada contenedor.

![System Container Diagram](../assets/img/chapter-IV-j/C4%20-%20Diagrams/System%20Container%20Diagram.png)

---

### 4.3.3. Software Architecture Deployment Diagrams.
Este diagrama de despliegue muestra la topología **simple y vertical** de ReStyle en producción: 
el **cliente** (navegador/app móvil) se comunica vía **HTTPS** con la **capa de ingreso** (API Gateway), 
que enruta al **Servidor de Aplicaciones**. La aplicación persiste datos en el **Servidor de BD** y 
gestiona archivos en el **Almacenamiento de Objetos** (CDN/Bucket). Además, se anotan las 
integraciones externas críticas: **Pasarela de Pagos** y **LLM (ChatGPT)**.

![Deployment Diagram](../assets/img/chapter-IV-j/C4%20-%20Diagrams/Deployment%20Diagram.png)

---
