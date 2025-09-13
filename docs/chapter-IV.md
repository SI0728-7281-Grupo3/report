# Capítulo IV: Strategic-Level Software Design.

## 4.1. Strategic-Level Attribute-Driven Design. Luciano
### 4.1.1. Design Purpose. Luciano
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

<img src="assets/img/chapter-IV-j/4.1.png" alt="EventStorming — tablero general" width="800">

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

<img src="assets/img/chapter-IV-j/4.2.png" alt="Candidate Context Discovery sobre el timeline" width="800">

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

<img src="assets/img/chapter-IV-j/4.3.png" alt="Domain Storytelling — escenario integrado" width="800">

---

### 4.2.4. Bounded Context Canvases.


**Identity & Profiles**  
– Propósito: autenticar usuarios y administrar perfiles públicos.  
– Decisiones: email único/verificado, consentimiento para perfil público, solo perfiles completos se indexan.  
<img src="assets/img/chapter-IV-j/4.41.png" alt="Canvas — Identity & Profiles" width="800">

**Discovery (Search & Indexing)**  
– Propósito: encontrar remodeladores e indexar perfiles/proyectos.  
– Decisiones: ranking por *score* (distancia + rating + actividad + completitud).  
<img src="assets/img/chapter-IV-j/4.42.png" alt="Canvas — Discovery (Search & Indexing)" width="800">

**Project & Quotation**  
– Propósito: gestionar solicitud, visitas, cotizaciones y aceptación.  
– Decisiones: solo 1 cotización aceptada; vigencia; visita técnica requerida.  
<img src="assets/img/chapter-IV-j/4.43.png" alt="Canvas — Project & Quotation" width="800">

**Payment**  
– Propósito: autorizar, capturar y reembolsar pagos.  
– Decisiones: idempotencia por `RequestId`, reglas de captura, reembolsos parciales.  
<img src="assets/img/chapter-IV-j/4.44.png" alt="Canvas — Payment" width="800">

**Execution & Feedback**  
– Propósito: controlar hitos/evidencias y reseñas al cierre.  
– Decisiones: cerrar hito con evidencia; reseña solo tras `ProjectCompleted`.  
<img src="assets/img/chapter-IV-j/44.png" alt="Canvas — Execution & Feedback" width="800">

---

### 4.2.5. Context Mapping.

**Baseline (seleccionada)**
- **Identity & Profiles → Discovery**: **Conformist (events)** para cambios de perfil indexables.
- **Project & Quotation → Payment**: **Customer/Supplier (Authorize)**.
- **Execution & Feedback → Payment**: **Customer/Supplier (Capture/Refund)**.
- **Subscriptions & Notifications ↔ Payment**: **Customer/Supplier (Recurring/Dunning)**.
- Gateways + **ACL** hacia **External IdP** y **PSP**.

<img src="assets/img/chapter-IV-j/4.5.png" alt="Context Mapping — baseline y relaciones" width="800">

**Alternativas analizadas (resumen)**
- **Discovery dividido (Indexer + Search API):** +escala/+experimentos; −más contratos.
- **Shared Kernel entre Project & Execution:** +consistencia; −acoplamiento.



## 4.3. Software Architecture. STEFANO
### 4.3.1. Software Architecture System Landscape Diagram.
### 4.3.1. Software Architecture Context Level Diagrams.
### 4.3.2. Software Architecture Container Level Diagrams.
### 4.3.3. Software Architecture Deployment Diagrams.
