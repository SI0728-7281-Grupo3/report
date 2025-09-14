
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

### 4.1.2. Attribute-Driven Design Inputs. STEFANO
#### 4.1.2.1. Primary Functionality (Primary User Stories).
#### 4.1.2.2. Quality attribute Scenarios.
### 4.1.3. Architectural Drivers Backlog. Carlos
### 4.1.4. Architectural Design Decisions. Carlos
### 4.1.5. Quality Attribute Scenario Refinements. Carlos
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



## 4.3. Software Architecture. STEFANO
### 4.3.1. Software Architecture System Landscape Diagram.
### 4.3.1. Software Architecture Context Level Diagrams.
### 4.3.2. Software Architecture Container Level Diagrams.
### 4.3.3. Software Architecture Deployment Diagrams.

