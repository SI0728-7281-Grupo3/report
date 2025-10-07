# Capítulo V: Tactical-Level Software Design

## 5.1. Bounded Context: User Management
### 5.1.1. Domain Layer

Aggregate | Name | Category | Purpose
---|---:|:---:|---
User | User | Entity / Aggregate Root | Representa la cuenta de un usuario (propietario o remodelador). Mantiene identidad, credenciales y estado.
Profile | Profile | Entity (part of UserAggregate) | Datos públicos y privados del perfil del usuario.

Attributes (User)
Attribute | Data Type | Visibility | Description
---|---:|---:|---
id | UUID | Private | Identificador único.
email | Email (VO) | Private | Correo normalizado/validado.
passwordHash | String | Private | Hash de la contraseña.
role | Role (enum) | Private | Rol: OWNER, REMODELER, ADMIN.
status | UserStatus (enum) | Private | Estado: PENDING, ACTIVE, SUSPENDED.
createdAt | DateTime | Private | Fecha de creación.
lastLogin | DateTime | Private / Nullable | Último acceso.

Methods (User)
Method | Return Type | Visibility | Description
---|---:|---:|---
User(createCmd) | Constructor | Public | Crea usuario válido (usa UserFactory).
changeEmail(newEmail: Email) | void | Public | Cambia y valida email; emite evento.
verifyPassword(plain: String) | Boolean | Public | Verifica contraseña.
changePassword(newHash: String) | void | Public | Actualiza hash.
activate() | void | Public | Activa cuenta (valida invariantes).
suspend(reason: String) | void | Public | Suspende cuenta.
updateProfile(profileData) | void | Public | Actualiza datos del Profile agregado.

Domain Events
- UserRegistered { userId, occurredAt }
- UserEmailChanged { userId, oldEmail, newEmail }
- UserActivated { userId }
- PasswordChanged { userId }

Domain Repositories (interfaces)
Interface | Purpose / Methods (firma)
---|---
IUserRepository | findById(id: UUID): Optional<User>  · findByEmail(email: Email): Optional<User> · save(user: User): User · deleteById(id: UUID): void
IProfileRepository | findByUserId(userId: UUID): Optional<Profile> · save(profile: Profile): Profile

Invariants / Rules
- Email único (enforced via IUserRepository).
- Passwords deben cumplir la política (PasswordPolicyService).
- Sólo el Aggregate Root (User) modifica su estado transaccionalmente.

---

### 5.1.2. Interface Layer

Controller | Name | Category | Purpose
---|---:|---:|---
UserController | UserController | Controller (REST) | Exponer endpoints CRUD y gestión básica de cuentas.
AuthController | AuthController | Controller (REST) | Manejo de autenticación, refresh y recuperación.
ProfileController | ProfileController | Controller (REST) | Gestión de perfil público/privado del usuario.

Methods (UserController / AuthController / ProfileController)
Controller | Method | Return Type | Visibility | Description
---|---|---:|---:|---
UserController | register(CreateUserRequest) | ResponseEntity<UserResource> | Public | Registra nuevo usuario. 201 Created.
UserController | getUserById(id) | ResponseEntity<UserResource> | Public | Recupera info de usuario. 200/404.
UserController | updateUser(id, UpdateUserRequest) | ResponseEntity<UserResource> | Public | Actualiza datos (no contraseñas).
AuthController | login(LoginRequest) | ResponseEntity<AuthTokenResource> | Public | Autentica y devuelve tokens.
AuthController | refreshToken(RefreshRequest) | ResponseEntity<AuthTokenResource> | Public | Renueva tokens.
AuthController | forgotPassword(ForgotPasswordRequest) | ResponseEntity<Void> | Public | Inicia flujo de recuperación.
ProfileController | getProfile(userId) | ResponseEntity<ProfileResource> | Public | Obtiene perfil público.
ProfileController | updateProfile(userId, UpdateProfileRequest) | ResponseEntity<ProfileResource> | Public | Actualiza avatar, bio, contacto.

Notes
- Usar DTOs / Request/Response Resources (no devolver entidades).
- Manejo de errores estandarizado (HTTP codes + problem/json).
- Validación de entrada y autorización en esta capa.

---

### 5.1.3. Application Layer

Service / Handler | Layer Role | Purpose
---|---:|---
UserCommandServiceImpl | Command Service | Orquesta casos de uso de escritura (registro, cambio de email, cambio de contraseña).
UserQueryServiceImpl | Query Service | Provee consultas optimizadas (getById, search).
AuthCommandServiceImpl | Command Service | Orquesta flujos de autenticación (login, refresh, forgot password).

Methods (signatures)
Component | Method | Return Type | Visibility | Description
---|---|---:|---:|---
UserCommandServiceImpl | handle(RegisterUserCommand cmd) | UUID / Optional<UserResource> | Public | Crea usuario, persiste y publica UserRegistered.
UserCommandServiceImpl | handle(ChangeEmailCommand cmd) | Optional<UserResource> | Public | Valida e invoca aggregate.
UserCommandServiceImpl | handle(ChangePasswordCommand cmd) | boolean | Public | Valida política y actualiza password.
UserQueryServiceImpl | handle(GetUserByIdQuery q) | Optional<UserDto> | Public | Devuelve vista/DTO desde ReadModel o repositorio.
UserQueryServiceImpl | handle(SearchUsersQuery q) | List<UserDto> | Public | Búsqueda paginada.
AuthCommandServiceImpl | handle(AuthenticateCommand cmd) | AuthTokenDto | Public | Valida credenciales, genera tokens.

Responsibilities
- Orquestar Domain (factories, aggregates), usar repositorios de dominio (interfaces).
- Emitir/encolar Domain Events (a Message Broker) cuando corresponda.
- No contener lógica de persistencia concreta ni detalles infra.

---

### 5.1.4. Infrastructure Layer

Repository / Adapter | Name | Category | Purpose
---|---:|---:|---
Notification: (example) | (not used here) | |
UserRepositoryImpl | UserRepositoryImpl | Repository (Postgres/ORM) | Implementación concreta de IUserRepository; maneja persistencia y transacciones.
ProfileRepositoryImpl | ProfileRepositoryImpl | Repository (Postgres/ORM) | Persistencia de Profile.
UserReadModelRepository | UserReadModelRepository | Read Model / Query DB | Consultas optimizadas (materialized views / read DB).
MsgBrokerAdapter | MessageBroker Adapter | Adapter | Publica/consume eventos (Kafka/RabbitMQ).
EmailAdapter | Email Service Adapter | Adapter | Envío de emails (SendGrid/SMTP).
AuthProviderAdapter | External Auth Adapter | Adapter | Integración OAuth/OIDC.
Cache | Redis Adapter | Cache | Cacheo de sesiones / datos frecuentes.
FileStorageAdapter | File Storage Adapter | Adapter | Almacenamiento de avatares (S3/GCS).

Repository Methods (UserRepositoryImpl)
Method | Return Type | Visibility | Description
---|---:|---:|---
save(user: User) | User | Public | Persiste o actualiza agregado.
findById(id: UUID) | Optional<User> | Public | Recupera usuario por id.
findByEmail(email: Email) | Optional<User> | Public | Buscar por email.
findAll() | List<User> | Public | Listado (paginado).
deleteById(id: UUID) | void | Public | Elimina por id.

Infrastructure Notes
- Implementaciones viven aquí y cumplen interfaces del dominio.
- Migraciones, constraints (PK, FK, unique email) y transacciones definidas en infra.
- Publicación de eventos y envío de correos se realizan mediante adapters.
- Leer/escribir optimizado mediante Read Model para consultas (CQRS).
- Secret management, monitoring y backups configurados en esta capa.


### 5.1.5. Bounded Context Software Architecture Component Level Diagrams

### 5.1.6. Bounded Context Software Architecture Code Level Diagrams

#### 5.1.6.1. Bounded Context Domain Layer Class Diagrams

#### 5.1.6.2. Bounded Context Database Design Diagram




## 5.2. Bounded Context: Discovery Context

### 5.2.1. Domain Layer

Aggregate | Name | Category | Purpose
---|---:|:---:|---
Search | Search | Entity / Aggregate Root | Representa una búsqueda y sus criterios; orquesta ejecución y resultados.
RemodelerProfile | RemodelerProfile | Entity | Perfil público de un remodelador usado en resultados de búsqueda.

Attributes (Search)
Attribute | Data Type | Visibility | Description
---|---:|---:|---
id | UUID | Private | Identificador único de la búsqueda (si se persiste).
criteria | SearchCriteria (VO) | Private | Criterios: location, expertise, rating, keywords, availability.
resultCount | Integer | Private | Número de resultados retornados.
createdAt | DateTime | Private | Fecha de creación.

Methods (Search)
Method | Return Type | Visibility | Description
---|---:|---:|---
Search(createCmd) | Constructor | Public | Crea instancia con criterios válidos.
applyFilter(filter: Filter) | void | Public | Aplica filtro a criterios y actualiza estado.
execute(): List<RemodelerProfile> | List<RemodelerProfile> | Public | Ejecuta la búsqueda orquestando repositorios / índices.

Value Objects
- SearchCriteria { location: LocationVO, expertise: List<String>, minRating: Float, keywords: String, radiusKm: Integer }
- LocationVO { lat: Float, lng: Float, city: String }

Domain Events
- RemodelersFound { searchId, resultCount, occurredAt }
- FilterApplied { searchId, filter, occurredAt }

Repository Interfaces (domain)
Interface | Purpose / Methods
---|---
ISearchRepository | save(search: Search): Search · findById(id: UUID): Optional<Search>
IRemodelerReadRepository | findByCriteria(criteria: SearchCriteria, pageable?): List<RemodelerProfile> · findByLocationAndExpertise(...): List<RemodelerProfile>

Invariants / Rules
- Debe incluir location o al menos una expertise.
- RadiusKm dentro de límites aceptables.
- Resultados deben paginarse y respetar privacidad del perfil.

---

### 5.2.2. Interface Layer

Controller | Name | Category | Purpose
---|---:|:---:|---
SearchController | SearchController | Controller (REST) / API | Exponer endpoints para ejecución de búsquedas y consultas de resultados.
FilterController | FilterController | Controller (REST) | Manejar aplicación de filtros a búsquedas existentes.

Endpoints / Methods
Controller | Method | HTTP | Request | Response | Description
---|---:|---:|---:|---:|---
SearchController | search(criteria) | POST /api/discovery/search | SearchRequest | SearchResultsResource | Ejecuta búsqueda con criterios; devuelve resultados paginados.
SearchController | getSearch(id) | GET /api/discovery/search/{id} | - | SearchResource | Recupera búsqueda guardada/estado.
SearchController | getProfiles(query) | GET /api/discovery/profiles | query params | List<RemodelerProfileResource> | Consulta directa de perfiles (filtros).
FilterController | applyFilter(searchId, filter) | POST /api/discovery/search/{id}/filters | FilterRequest | SearchResource | Aplica filtro a búsqueda y retorna vista actualizada.

Notes
- Usar DTOs/Resources (SearchRequest, SearchResultsResource, RemodelerProfileResource).
- Soporte para paginación, sorting y cache-control headers.
- Validación y rate limiting en API Gateway.

---

### 5.2.3. Application Layer

Service / Handler | Layer Role | Purpose
---|---:|---
SearchCommandHandler | Command Handler | Orquesta ejecución de búsquedas y publicación de eventos.
FilterCommandHandler | Command Handler | Aplica filtros sobre Search aggregate y actualiza estado.
SearchQueryHandler | Query Handler | Resuelve consultas de lectura usando ReadModel / SearchIndex.

Methods (signatures)
Component | Method | Return Type | Description
---|---:|---:|---
SearchCommandHandler | handle(ExecuteSearchCommand cmd) | SearchResultsDto | Valida criterios, consulta IRemodelerReadRepository / SearchIndex y retorna resultados.
FilterCommandHandler | handle(ApplyFilterCommand cmd) | SearchDto | Actualiza criterios en Search aggregate y publica FilterApplied event.
SearchQueryHandler | handle(GetProfilesQuery q) | List<RemodelerProfileDto> | Lee desde ReadModel / SearchIndex para respuestas rápidas.

Responsibilities
- Orquestar llamadas a repositorios de lectura y caches.
- Publicar eventos (RemodelersFound, FilterApplied) a través de broker.
- No contener lógica de persistencia concreta; usar interfaces de dominio.

Patterns / Considerations
- CQRS: separar commands (escritura/actualización) de queries (lectura).
- Uso de Search Index (Elasticsearch) y consultas geo para ubicación.
- Cache de resultados costosos en Redis.

---

### 5.2.4. Infrastructure Layer

Repository / Adapter | Name | Category | Purpose
---|---:|:---:|---
RemodelerReadRepositoryImpl | IRemodelerReadRepository | Adapter (Search Index) | Implementación usando Elasticsearch o Postgres+GIS para búsquedas por ubicación y expertise.
SearchIndexAdapter | SearchIndex Adapter | Adapter | Indexa perfiles y habilita consultas full-text y geo.
SearchCache | Redis Cache | Cache | Cacheo de resultados de búsquedas frecuentes.
SearchJobWorker | Background Worker | Worker | Indexación y reindex asíncrona de perfiles/portafolios.
ApiGateway / Edge | API Gateway | Edge | Enrutamiento, rate limiting, caching headers.

Infra Methods (ejemplos)
Method | Return Type | Description
---|---:|---
findByCriteria(criteria, pageable) | List<RemodelerProfile> | Ejecuta consulta en Elastic/Postgres+GIS con scoring.
indexProfile(profile) | void | Indexa o actualiza perfil en search index.
getCachedResults(key) | Optional<SearchResults> | Recupera resultados cacheados.

Infra Notes
- Indexar campos: name, skills, city, location (geo_point), rating, portfolioCount.
- Mantener pipelines que actualicen índices cuando RemodelerProfile cambia.
- Supervisar latencias de búsqueda y tasa de cache hits.
- Proteger endpoints con rate limiting y circuit breakers.


### 5.2.5. Bounded Context Software Architecture Component Level Diagrams

### 5.2.6. Bounded Context Software Architecture Code Level Diagrams

#### 5.2.6.1. Bounded Context Domain Layer Class Diagrams

#### 5.2.6.2. Bounded Context Database Design Diagram





## 5.3. Bounded Context: Project & Quotation Context

### 5.3.1. Domain Layer

Aggregate | Name | Category | Purpose
---|---:|:---:|---
ProjectRequest | ProjectRequest | Entity / Aggregate Root | Representa la solicitud de proyecto iniciada por un propietario; orquesta estado del ciclo solicitud→visita→cotización.
Quotation | Quotation | Entity | Representa una cotización/propuesta económica asociada a una solicitud.
TechnicalVisit | TechnicalVisit | Entity | Registro de visita técnica programada y resultado técnico (mediciones, observaciones).

Attributes (ProjectRequest)
Attribute | Data Type | Visibility | Description
---|---:|---:|---
id | UUID | Private | Identificador único de la solicitud.
ownerId | UUID | Private | Identificador del propietario solicitante.
title | String | Private | Título o resumen de la solicitud.
description | String | Private | Descripción detallada del requerimiento.
status | RequestStatus (enum) | Private | Estado: NEW, SCHEDULED, QUOTED, ACCEPTED, REJECTED, CANCELLED.
createdAt | DateTime | Private | Fecha de creación.
preferredDate | DateTime | Private / Nullable | Fecha preferida para visita técnica.

Methods (ProjectRequest)
Method | Return Type | Visibility | Description
---|---:|---:|---
ProjectRequest(createCmd) | Constructor | Public | Valida y crea solicitud inicial.
scheduleVisit(date, technicianId) | void | Public | Programa visita técnica; cambia estado a SCHEDULED.
applyQuotation(quotationId) | void | Public | Asocia cotización y cambia estado a QUOTED.
acceptQuotation(quotationId) | void | Public | Marca solicitud como ACCEPTED.
rejectQuotation(quotationId) | void | Public | Marca solicitud como REJECTED.

Domain Events
- ProjectRequestCreated { requestId, ownerId, occurredAt }
- TechnicalVisitScheduled { visitId, requestId, scheduledAt }
- QuotationProvided { quotationId, requestId, amount }
- QuotationAccepted { quotationId, requestId }

Repository Interfaces (domain)
Interface | Purpose / Methods
---|---
IProjectRequestRepository | save(request: ProjectRequest): ProjectRequest · findById(id: UUID): Optional<ProjectRequest> · findByOwner(ownerId: UUID, pageable?): List<ProjectRequest>
IQuotationRepository | save(quotation: Quotation): Quotation · findById(id: UUID): Optional<Quotation> · findByRequestId(requestId: UUID): List<Quotation>
ITechnicalVisitRepository | save(visit: TechnicalVisit): TechnicalVisit · findByRequestId(requestId: UUID): List<TechnicalVisit>

Invariants / Rules
- Una solicitud puede tener 0..* cotizaciones; solo una puede ser aceptada.
- Solo solicitudes en estado NEW o SCHEDULED pueden recibir cotizaciones.
- Las operaciones que cambian estado deben validar transiciones permitidas.

---

### 5.3.2. Interface Layer

Controller | Name | Category | Purpose
---|---:|:---:|---
ProjectRequestController | ProjectRequestController | Controller (REST) | Gestiona CRUD de solicitudes y acciones (agendar visita, aceptar cotización).
QuotationController | QuotationController | Controller (REST) | Crear y consultar cotizaciones asociadas a solicitudes.
VisitController | VisitController | Controller (REST) | Programación y registro de visitas técnicas.

Endpoints / Methods (resumen)
Controller | Method (HTTP) | Request | Response | Description
---|---:|---:|---:|---
ProjectRequestController | POST /api/requests | CreateRequestDto | 201 Created + RequestResource | Crear nueva solicitud.
ProjectRequestController | GET /api/requests/{id} | - | 200 + RequestResource | Obtener detalle de solicitud.
ProjectRequestController | POST /api/requests/{id}/schedule | ScheduleVisitDto | 200 + VisitResource | Agendar visita técnica.
QuotationController | POST /api/requests/{id}/quotations | CreateQuotationDto | 201 + QuotationResource | Proveer cotización para solicitud.
QuotationController | GET /api/requests/{id}/quotations | - | 200 + List<QuotationResource> | Listar cotizaciones de una solicitud.
QuotationController | POST /api/quotations/{id}/accept | - | 200 + QuotationResource | Aceptar cotización (inicia flujo de pago).
VisitController | PUT /api/visits/{id}/report | VisitReportDto | 200 + VisitResource | Registrar resultado de visita técnica.

Notes
- Usar DTOs/Resources; no exponer entidades de dominio.
- Validaciones y autorización en esta capa (roles: OWNER, REMODELER, TECH).
- Respuestas estandarizadas con códigos HTTP apropiados.

---

### 5.3.3. Application Layer

Service / Handler | Layer Role | Purpose
---|---:|---
CreateProjectRequestHandler | Command Handler | Orquesta creación de solicitudes, persistencia y publicación de ProjectRequestCreated.
ScheduleVisitHandler | Command Handler | Programa visitas, crea TechnicalVisit y publica TechnicalVisitScheduled.
ProvideQuotationHandler | Command Handler | Crea cotización asociada; valida estado de solicitud y publica QuotationProvided.
AcceptQuotationHandler | Command Handler | Marca cotización como aceptada, actualiza solicitud y publica QuotationAccepted; inicia flujo de pago (evento).
GetRequestQueryHandler | Query Handler | Recupera vistas/DTOs optimizadas para lectura.

Methods (firmas)
Component | Method | Return Type | Description
---|---:|---:|---
CreateProjectRequestHandler | handle(CreateProjectRequestCommand cmd) | UUID | Crea solicitud y retorna id.
ScheduleVisitHandler | handle(ScheduleVisitCommand cmd) | UUID | Programa visita y retorna visitId.
ProvideQuotationHandler | handle(ProvideQuotationCommand cmd) | UUID | Persiste cotización y retorna id.
AcceptQuotationHandler | handle(AcceptQuotationCommand cmd) | boolean | Valida y acepta cotización; retorna success.
GetRequestQueryHandler | handle(GetRequestByIdQuery q) | Optional<ProjectRequestDto> | Devuelve DTO desde ReadModel.

Responsibilities
- Orquestar agregados y factories, validar reglas de negocio, emitir Domain Events.
- Coordinar con infra (repositorios, message broker, external services).
- Mantener separación Commands vs Queries (posible CQRS).

---

### 5.3.4. Infrastructure Layer

Repository / Adapter | Name | Category | Purpose
---|---:|:---:|---
ProjectRequestRepositoryImpl | ProjectRequestRepositoryImpl | Repository (Postgres/ORM) | Implementación de IProjectRequestRepository; maneja transacciones.
QuotationRepositoryImpl | QuotationRepositoryImpl | Repository (Postgres/ORM) | Persistencia de cotizaciones.
TechnicalVisitRepositoryImpl | TechnicalVisitRepositoryImpl | Repository (Postgres/ORM) | Persistencia de visitas técnicas.
PaymentIntegrationAdapter | Payment Adapter | Adapter | Integración con pasarela de pago (inicio de cobros tras aceptación).
MsgBrokerAdapter | Message Broker Adapter | Adapter | Publica eventos domain (QuotationAccepted, ProjectRequestCreated).
ReadModelRepository | ReadModel / Materialized Views | Adapter | Vistas optimizadas para consultas (requests + latest quotation).
FileStorageAdapter | File Storage | Adapter | Almacena fotos/reportes de visita (S3/GCS).

Infra Methods (ejemplos)
Method | Return Type | Description
---|---:|---
save(request: ProjectRequest) | ProjectRequest | Persiste o actualiza solicitud.
findByRequestId(requestId: UUID) | List<Quotation> | Recupera cotizaciones.
initiatePayment(requestId, amount) | PaymentResponse | Invoca pasarela de pagos cuando se acepta cotización.
indexRequestView(requestId) | void | Actualiza read model / búsqueda.

Infra Notes
- Definir constraints en BD: FK entre requests y quotations; unique constraints según negocio.
- Garantizar atomicidad en aceptación de cotización y creación de pago (sagas/transactions).
- Publicar eventos para orquestación entre bounded contexts (p. ej. Payment Context).
- Registrar auditoría y trazabilidad (audit logs) para solicitudes y cotizaciones.

### 5.3.5. Bounded Context Software Architecture Component Level Diagrams

### 5.3.6. Bounded Context Software Architecture Code Level Diagrams

#### 5.3.6.1. Bounded Context Domain Layer Class Diagrams

#### 5.3.6.2. Bounded Context Database Design Diagram




## 5.4. Bounded Context: Payment Context

### 5.4.1. Domain Layer

Aggregate | Name | Category | Purpose
---|---:|:---:|---
Payment | Payment | Entity / Aggregate Root | Representa el flujo de pago asociado a una cotización/servicio: autorización, captura y liquidación.
PaymentMethod | PaymentMethod | Value Object / Entity | Datos del método de pago tokenizado (tarjeta, wallet).
Charge | Charge | Entity | Registro de transacción (amount, currency, status, externalId).

Attributes (Payment)
Attribute | Data Type | Visibility | Description
---|---:|:---:|---
id | UUID | Private | Identificador único del pago.
requestId | UUID | Private | Referencia al ProjectRequest o Quotation asociado.
amount | Decimal | Private | Monto a cobrar.
currency | String | Private | Moneda (ej. PEN, USD).
status | PaymentStatus (enum) | Private | Estado: AUTHORIZED, CAPTURED, FAILED, REFUNDED.
paymentMethod | PaymentMethod (VO) | Private | Método de pago tokenizado.
externalReference | String | Private / Nullable | Id del proveedor de pagos.
createdAt | DateTime | Private | Fecha de creación.
updatedAt | DateTime | Private | Última actualización.

Methods (Payment)
Method | Return Type | Visibility | Description
---|---:|---:|---
Payment(createCmd) | Constructor | Public | Crea y valida un pago inicial.
authorize(paymentDetails) | AuthorizationResult | Public | Intenta autorizar fondos (invoca gateway via domain service).
capture() | CaptureResult | Public | Captura fondos previamente autorizados.
refund(amount) | RefundResult | Public | Inicia reembolso parcial/total.
markFailed(reason) | void | Public | Marca pago como FALLIDO y emite evento.

Domain Events
- PaymentAuthorized { paymentId, externalReference, occurredAt }
- PaymentCaptured { paymentId, amount, occurredAt }
- PaymentFailed { paymentId, reason, occurredAt }
- PaymentRefunded { paymentId, amount, occurredAt }

Repository Interfaces (domain)
Interface | Purpose / Methods
---|---
IPaymentRepository | save(payment: Payment): Payment · findById(id: UUID): Optional<Payment> · findByRequestId(requestId: UUID): List<Payment>
IChargeRepository | save(charge: Charge): Charge · findByExternalReference(externalId: String): Optional<Charge>

Invariants / Rules
- Un payment pasa por transiciones válidas: CREATED -> AUTHORIZED -> CAPTURED -> REFUNDED.
- Sólo se captura si existe autorización válida.
- Montos y moneda deben coincidir con la cotización asociada.
- ExternalReference único por transacción con proveedor.

---

### 5.4.2. Interface Layer

Controller | Name | Category | Purpose
---|---:|:---:|---
PaymentController | PaymentController | Controller (REST) | Exponer endpoints para iniciar autorización, captura, consulta y reembolso.
WebhookController | WebhookController | Controller (HTTP) | Recibir callbacks/webhooks del proveedor de pagos.

Endpoints / Methods (resumen)
Controller | Method (HTTP) | Request | Response | Description
---|---:|---:|---:|---
PaymentController | POST /api/payments/authorize | AuthorizePaymentRequest | 201 Created + PaymentResource | Inicia autorización de fondos.
PaymentController | POST /api/payments/{id}/capture | CaptureRequest | 200 OK + PaymentResource | Captura fondos autorizados.
PaymentController | GET /api/payments/{id} | - | 200 OK + PaymentResource | Consulta estado del pago.
PaymentController | POST /api/payments/{id}/refund | RefundRequest | 200 OK + PaymentResource | Solicita reembolso.
WebhookController | POST /api/payments/webhook | ProviderWebhook | 200 OK | Recibe notificaciones de proveedor; valida firma.

Notes
- WebhookController debe validar firma/hmac y procesar asynchronously.
- No exponer datos sensibles del método de pago; manejar tokens.
- Respuestas con códigos HTTP adecuados y Resource/DTO.

---

### 5.4.3. Application Layer

Service / Handler | Layer Role | Purpose
---|---:|---
AuthorizePaymentHandler | Command Handler | Orquesta autorización: valida request, crea Payment aggregate, invoca PaymentGatewayService.
CapturePaymentHandler | Command Handler | Ejecuta captura sobre pago autorizado y actualiza estado.
RefundPaymentHandler | Command Handler | Maneja reembolsos parciales/ totales.
PaymentQueryHandler | Query Handler | Devuelve estado y transacciones asociadas.

Methods (firmas)
Component | Method | Return Type | Description
---|---:|---:|---
AuthorizePaymentHandler | handle(AuthorizePaymentCommand cmd) | PaymentDto | Crea Payment, solicita autorización al gateway, persiste y publica PaymentAuthorized.
CapturePaymentHandler | handle(CapturePaymentCommand cmd) | PaymentDto | Solicita captura al gateway, actualiza Payment y publica PaymentCaptured.
RefundPaymentHandler | handle(RefundPaymentCommand cmd) | PaymentDto | Solicita reembolso y publica PaymentRefunded.
PaymentQueryHandler | handle(GetPaymentByIdQuery q) | Optional<PaymentDto> | Retorna vista/DTO para UI/consumers.

Responsibilities
- Orquestar interacciones entre Payment aggregate y domain services (PaymentGatewayService).
- Publicar Domain Events a broker para coordinar con otros contexts (p. ej. Project lifecycle).
- Manejar errores y políticas de reintento en casos transaccionales (usar sagas cuando aplica).

Sagas / Long-running flows
- Aceptación de cotización -> crear Payment -> autorizar -> al confirmarse captura -> notificar a Project Context -> emitir factura.

---

### 5.4.4. Infrastructure Layer

Repository / Adapter | Name | Category | Purpose
---|---:|---:|---
PaymentRepositoryImpl | PaymentRepositoryImpl | Repository (Relational DB / ORM) | Implementación de IPaymentRepository; persiste pagos y estados.
ChargeRepositoryImpl | ChargeRepositoryImpl | Repository | Persistencia de charges/transactions externas.
PaymentGatewayAdapter | External Payment Gateway Adapter | Adapter | Implementación concreta contra proveedor (Stripe, PayU, Culqi). Maneja authorize/capture/refund APIs.
WebhookProcessor | WebhookProcessor | Adapter / Worker | Valida y procesa callbacks, publica eventos internos.
TransactionLogStore | Audit/Log Store | Adapter | Registro de transacciones y respuestas del proveedor.
DbMigrations | Migrations | Tooling | Gestiona esquema (payments, charges, indexes).

Infra Methods (ejemplos)
Method | Return Type | Description
---|---:|---
authorize(payment: Payment): AuthorizationResult | Invoca API del proveedor para reservar fondos.
capture(externalRef, amount): CaptureResult | Ejecuta captura en proveedor.
refund(externalRef, amount): RefundResult | Ejecuta reembolso.
save(payment: Payment): Payment | Persiste estado actualizado del aggregate.

Infra Notes
- Tabla payments: id PK, request_id FK, amount, currency, status, payment_method_token, external_reference (unique), created_at, updated_at.
- Tabla charges: id PK, payment_id FK, provider_response, provider_code, amount, created_at.
- Manejar idempotencia en endpoints (use idempotency keys al llamar gateway).
- Webhooks deben validar firma y procesar en colas para resiliencia.
- Considerar cifrado/seguridad para tokens y cumplimiento PCI (no almacenar PAN).
- Implementar reconciliación periódica entre registros locales y proveedor.

### 5.4.5. Bounded Context Software Architecture Component Level Diagrams

### 5.4.6. Bounded Context Software Architecture Code Level Diagrams

#### 5.4.6.1. Bounded Context Domain Layer Class Diagrams

#### 5.4.6.2. Bounded Context Database Design Diagram





##  5.5. Bounded Context: Execution & Feedback Context

#### 5.5.1. Domain Layer

Aggregate | Name | Category | Purpose
---|---:|:---:|---
ProjectExecution | ProjectExecution | Entity / Aggregate Root | Representa la ejecución de un proyecto: hitos, estado, progreso y cierre.
Milestone | Milestone | Entity | Hito del proyecto con entregables, estado y fecha.
Review | Review | Entity | Reseña y calificación dejada por el propietario al finalizar el proyecto.
Issue | Issue | Entity | Registro de incidencias/observaciones durante la ejecución.

Attributes (ProjectExecution)
Attribute | Data Type | Visibility | Description
---|---:|:---:|---
id | UUID | Private | Identificador único del proyecto en ejecución.
requestId | UUID | Private | Referencia al ProjectRequest aceptado.
remodelerId | UUID | Private | ID del remodelador/contratista a cargo.
status | ExecutionStatus (enum) | Private | Estado: NOT_STARTED, IN_PROGRESS, ON_HOLD, COMPLETED, CANCELLED.
milestones | List<Milestone> | Private | Lista de hitos asociados.
progress | Integer (0-100) | Private | Porcentaje de avance.
startedAt | DateTime | Private / Nullable | Fecha de inicio.
completedAt | DateTime | Private / Nullable | Fecha de finalización.

Methods (ProjectExecution)
Method | Return Type | Visibility | Description
---|---:|:---:|---
ProjectExecution(createCmd) | Constructor | Public | Crea ejecución válida y asigna primer estado.
start() | void | Public | Marca inicio (emite ProjectStarted).
addMilestone(m: Milestone) | void | Public | Agrega un hito al aggregate.
completeMilestone(milestoneId) | void | Public | Marca hito como COMPLETED; recalcula progreso; emite MilestoneCompleted.
completeProject() | void | Public | Valida todos los hitos completados y marca proyecto COMPLETED; emite ProjectCompleted.
reportIssue(issueCmd) | Issue | Public | Registra incidencia y emite IssueReported.

Attributes & Methods (Review)
Attribute / Method | Data Type / Return | Visibility | Description
---|---:|:---:|---
id | UUID | Private | Identificador de la reseña.
projectExecutionId | UUID | Private | Referencia al proyecto ejecutado.
authorId | UUID | Private | ID del propietario que escribe la reseña.
rating | Integer | Private | Calificación (1..5).
comment | String | Private | Comentario de la reseña.
createdAt | DateTime | Private | Fecha de envío.
Review(createCmd) | Constructor | Public | Crea y valida la reseña (emite ReviewSubmitted).

Domain Events
- ProjectStarted { executionId, requestId, occurredAt }
- MilestoneCompleted { executionId, milestoneId, occurredAt }
- ProjectCompleted { executionId, occurredAt }
- IssueReported { executionId, issueId, occurredAt }
- ReviewSubmitted { reviewId, executionId, rating, occurredAt }

Repository Interfaces (domain)
Interface | Purpose / Methods
---|---
IProjectExecutionRepository | save(exec: ProjectExecution): ProjectExecution · findById(id: UUID): Optional<ProjectExecution> · findByRequestId(requestId: UUID): Optional<ProjectExecution> · findByRemodeler(remodelerId: UUID, pageable?): List<ProjectExecution>
IMilestoneRepository | save(m: Milestone): Milestone · findById(id: UUID): Optional<Milestone> · findByExecutionId(execId: UUID): List<Milestone>
IReviewRepository | save(review: Review): Review · findByProjectExecutionId(execId: UUID): List<Review> · findById(id: UUID): Optional<Review>
IIssueRepository | save(issue: Issue): Issue · findByExecutionId(execId: UUID): List<Issue>

Invariants / Rules
- No se puede completar proyecto sin todos los hitos en estado COMPLETED.
- Solo remodelador asignado o roles con permiso pueden marcar hitos completados.
- Reviews sólo permitidas cuando projectExecution.status == COMPLETED.
- Issue lifecycle: OPEN -> IN_PROGRESS -> RESOLVED / CLOSED.

---

#### 5.5.2. Interface Layer

Controller | Name | Category | Purpose
---|---:|:---:|---
ProjectExecutionController | ProjectExecutionController | Controller (REST) | Endpoints para seguimiento (start, progress, complete) y consulta de tracking.
MilestoneController | MilestoneController | Controller (REST) | Gestión de hitos: crear, actualizar estado, listar.
ReviewController | ReviewController | Controller (REST) | Envío y consulta de reseñas finales.
IssueController | IssueController | Controller (REST) | Reporte y seguimiento de incidencias durante ejecución.

Endpoints / Methods (resumen)
Controller | Method (HTTP) | Request | Response | Description
---|---:|---:|---:|---
ProjectExecutionController | POST /api/executions/{id}/start | - | 200 OK + ExecutionResource | Inicia ejecución.
ProjectExecutionController | GET /api/executions/{id} | - | 200 OK + ExecutionResource | Consulta estado/avance.
ProjectExecutionController | POST /api/executions/{id}/complete | - | 200 OK + ExecutionResource | Marca proyecto como completado.
MilestoneController | POST /api/executions/{id}/milestones | CreateMilestoneRequest | 201 + MilestoneResource | Agrega nuevo hito.
MilestoneController | POST /api/milestones/{id}/complete | - | 200 + MilestoneResource | Marca hito como completado.
ReviewController | POST /api/executions/{id}/reviews | CreateReviewRequest | 201 + ReviewResource | Envía reseña final.
ReviewController | GET /api/executions/{id}/reviews | - | 200 + List<ReviewResource> | Lista reseñas del proyecto.
IssueController | POST /api/executions/{id}/issues | CreateIssueRequest | 201 + IssueResource | Reporta incidencia.

Notes
- Controllers usan DTOs/Resources; validación y autorización (OWNER vs REMODELER).
- Eventos asíncronos (e.g. cuando milestone complete) deben encolarse para notificaciones y tracking.
- Endpoints idempotentes donde aplique (marcar hito completado).

---

#### 5.5.3. Application Layer

Service / Handler | Layer Role | Purpose
---|---:|---
StartProjectHandler | Command Handler | Orquesta inicio de ejecución; crea ProjectExecution aggregate; publica ProjectStarted.
CompleteMilestoneHandler | Command Handler | Gestiona cierre de hito, actualiza progreso y publica MilestoneCompleted.
CompleteProjectHandler | Command Handler / Saga | Valida cierre del proyecto, publica ProjectCompleted y dispara post-flows (facturación, encuestas).
SubmitReviewHandler | Command Handler | Valida y persiste Review; publica ReviewSubmitted.
ProjectQueryHandler | Query Handler | Provee vistas/DTOs para tracking, timeline y métricas.

Methods (firmas)
Component | Method | Return Type | Description
---|---:|---:|---
StartProjectHandler | handle(StartProjectCommand cmd) | UUID | Crea ejecución y retorna id.
CompleteMilestoneHandler | handle(CompleteMilestoneCommand cmd) | MilestoneDto | Marca hito completado, recalcula progreso.
CompleteProjectHandler | handle(CompleteProjectCommand cmd) | ExecutionDto | Marca proyecto completo y coordina saga (notifications, payment finalization).
SubmitReviewHandler | handle(SubmitReviewCommand cmd) | ReviewDto | Persiste reseña y notifica al remodeler.
ProjectQueryHandler | handle(GetExecutionByIdQuery q) | Optional<ExecutionDto> | Retorna DTO con timeline y hitos.

Responsibilities
- Orquestar aggregates y domain services (e.g. ProgressCalculationService).
- Emitir Domain Events hacia Message Broker para notificaciones y métricas.
- Coordinar sagas de cierre que interactúan con Payment/Notification/Subscription contexts.

Sagas / Long-running flows
- Proyecto completado -> generar encuesta -> enviar notificación al propietario -> esperar review -> actualizar reputación del remodeler.

---

#### 5.5.4. Infrastructure Layer

Repository / Adapter | Name | Category | Purpose
---|---:|:---:|---
ProjectExecutionRepositoryImpl | ProjectExecutionRepositoryImpl | Repository (Postgres/ORM) | Persistencia de ProjectExecution y transacciones.
MilestoneRepositoryImpl | MilestoneRepositoryImpl | Repository | Persistencia de hitos.
ReviewRepositoryImpl | ReviewRepositoryImpl | Repository | Persistencia de reseñas (indexar para consultas).
IssueRepositoryImpl | IssueRepositoryImpl | Repository | Persistencia de incidencias.
ExecutionReadModelRepo | ReadModel / Materialized Views | Adapter | Vistas optimizadas para tracking y timeline.
MsgBrokerAdapter | Message Broker Adapter | Adapter | Publica events: MilestoneCompleted, ProjectCompleted, ReviewSubmitted, IssueReported.
NotificationAdapter | Notification Adapter | Adapter | Envío de notificaciones (emails, in-app).
FileStorageAdapter | File Storage Adapter | Adapter | Almacena fotos/reportes de hitos (S3/GCS).
Worker / JobQueue | Background Workers | Worker | Procesamiento asíncrono (reindex, notifications, surveys).
Monitoring / Metrics | Observability | Adapter | Métricas de progreso, SLAs y alertas.

Infra Methods (ejemplos)
Method | Return Type | Description
---|---:|---
save(exec: ProjectExecution) | ProjectExecution | Persiste o actualiza ejecución.
findById(execId: UUID) | Optional<ProjectExecution> | Recupera ejecución.
save(m: Milestone) | Milestone | Persiste hito.
save(review: Review) | Review | Persiste reseña y actualiza índices/search.
publishEvent(event) | void | Publica a Message Broker (idempotente).

Infra Notes
- Tablas: project_executions, milestones, reviews, issues; FK y constraints para integridad.
- Implementar colas para procesar eventos (notificaciones, reindex).
- Storage para evidencias de hitos (fotos, PDFs) con permisos y expiración.
- Auditoría y trazabilidad para cambios de estado (who/when).
- Políticas de retención de reviews e issues y GDPR/privacidad conforme aplique.


### 5.5.5. Bounded Context Software Architecture Component Level Diagrams

### 5.5.6. Bounded Context Software Architecture Code Level Diagrams

#### 5.5.6.1. Bounded Context Domain Layer Class Diagrams

#### 5.5.6.2. Bounded Context Database Design Diagram



## 5.6. Bounded Context: Subscription & Notification Context

### 5.6.1. Domain Layer

Aggregate | Name | Category | Purpose
---|---:|:---:|---
Subscription | Subscription | Entity / Aggregate Root | Representa la suscripción de un usuario a un plan (estado, facturación, vencimiento).
Notification | Notification | Entity | Representa una notificación enviada a un destinatario (tipo, canal, estado).
NotificationPreference | NotificationPreference | Value Object / Entity | Preferencias de canal y frecuencia del usuario.

Attributes (Subscription)
Attribute | Data Type | Visibility | Description
---|---:|---:|---
id | UUID | Private | Identificador único de la suscripción.
userId | UUID | Private | Referencia al usuario suscriptor.
planId | UUID | Private | Identificador del plan suscrito.
status | SubscriptionStatus (enum) | Private | Estado: ACTIVE, PAST_DUE, CANCELLED, EXPIRED.
startedAt | DateTime | Private | Fecha de inicio.
nextBillingAt | DateTime | Private | Próxima fecha de facturación.
cancelledAt | DateTime | Private / Nullable | Fecha de cancelación.
billingMethod | BillingMethod (VO) | Private | Método de cobro tokenizado.

Methods (Subscription)
Method | Return Type | Visibility | Description
---|---:|---:|---
Subscription(createCmd) | Constructor | Public | Crea suscripción válida y programa facturación.
activate() | void | Public | Marca ACTIVE y emite SubscriptionActivated.
renew() | void | Public | Renueva periodo; actualiza nextBillingAt; emite SubscriptionRenewed.
cancel(effectiveAt) | void | Public | Cancela suscripción; emite SubscriptionCancelled.
isPastDue(): Boolean | Boolean | Public | Indica si hay pago pendiente.

Attributes (Notification)
Attribute | Data Type | Visibility | Description
---|---:|:---:|---
id | UUID | Private | Identificador único de la notificación.
recipientId | UUID | Private | Usuario destinatario.
type | NotificationType (enum) | Private | Tipo: EMAIL, IN_APP, SMS, PUSH.
payload | JSON / String | Private | Contenido estructurado de la notificación.
status | NotificationStatus (enum) | Private | Estado: PENDING, SENT, FAILED, READ.
createdAt | DateTime | Private | Fecha de creación.

Domain Events
- SubscriptionActivated { subscriptionId, userId, occurredAt }
- SubscriptionRenewed { subscriptionId, userId, occurredAt }
- SubscriptionCancelled { subscriptionId, userId, occurredAt }
- NotificationSent { notificationId, recipientId, channel, occurredAt }
- NotificationFailed { notificationId, reason, occurredAt }

Repository Interfaces (domain)
Interface | Purpose / Methods
---|---
ISubscriptionRepository | save(s: Subscription): Subscription · findById(id: UUID): Optional<Subscription> · findByUserId(userId: UUID): List<Subscription> · findActiveByUser(userId: UUID): Optional<Subscription>
INotificationRepository | save(n: Notification): Notification · findByRecipientId(recipientId: UUID, pageable?): List<Notification> · findPendingByChannel(channel): List<Notification>
INotificationPrefRepository | findByUserId(userId: UUID): Optional<NotificationPreference> · save(pref: NotificationPreference): NotificationPreference

Invariants / Rules
- Un usuario puede tener varias suscripciones pero solo una activa por plan.
- Renovaciones deben validar método de pago y manejar idempotencia.
- Preferencias del usuario determinan canales y frecuencia; respetarlas antes de enviar.

---

### 5.6.2. Interface Layer

Controller | Name | Category | Purpose
---|---:|:---:|---
SubscriptionController | SubscriptionController | Controller (REST) | Gestiona alta, renovación, cancelación y consulta de suscripciones.
NotificationController | NotificationController | Controller (REST) | Exponer historial y estado de notificaciones (in-app).
WebhookController | BillingWebhookController | Controller (HTTP) | Recibir callbacks del proveedor de pagos.

Endpoints / Methods (resumen)
Controller | Method (HTTP) | Request | Response | Description
---|---:|---:|---:|---
SubscriptionController | POST /api/subscriptions | CreateSubscriptionRequest | 201 + SubscriptionResource | Crear/activar suscripción.
SubscriptionController | POST /api/subscriptions/{id}/renew | - | 200 + SubscriptionResource | Forzar renovación.
SubscriptionController | POST /api/subscriptions/{id}/cancel | CancelRequest | 200 + SubscriptionResource | Cancelar suscripción.
SubscriptionController | GET /api/users/{id}/subscriptions | - | 200 + List<SubscriptionResource> | Listar suscripciones de usuario.
NotificationController | GET /api/notifications?recipientId={id} | - | 200 + List<NotificationResource> | Historial de notificaciones.
NotificationController | POST /api/notifications/send | SendNotificationRequest | 202 Accepted | Encolar notificación para envío.
WebhookController | POST /api/payments/subscriptions/webhook | ProviderWebhook | 200 OK | Procesar eventos de facturación (payment_succeeded, payment_failed).

Notes
- Usar DTOs/Resources; no exponer entidades de dominio.
- Idempotency keys para endpoints que inician cobros/renovaciones.
- Validar y autenticar webhooks (firma HMAC).

---

### 5.6.3. Application Layer

Service / Handler | Layer Role | Purpose
---|---:|---
CreateSubscriptionHandler | Command Handler | Orquesta creación y activación de suscripciones; valida pago inicial si aplica.
RenewSubscriptionHandler | Command Handler | Gestiona renovaciones automatizadas/manuales; coordina cobro y emite events.
CancelSubscriptionHandler | Command Handler | Ejecuta cancelación y reglas de prorrateo.
SendNotificationHandler | Command Handler | Orquesta envío de notificaciones conforme preferencias (enqueues to channels).
SubscriptionQueryHandler | Query Handler | Provee vistas/DTOs de suscripciones y status.

Methods (firmas)
Component | Method | Return Type | Description
---|---:|---:|---
CreateSubscriptionHandler | handle(CreateSubscriptionCommand cmd) | UUID | Crea suscripción, inicia cobro si necesario, publica SubscriptionActivated.
RenewSubscriptionHandler | handle(RenewSubscriptionCommand cmd) | SubscriptionDto | Ejecuta cobro; al éxito publica SubscriptionRenewed; en fallo publica SubscriptionPastDue.
CancelSubscriptionHandler | handle(CancelSubscriptionCommand cmd) | SubscriptionDto | Aplica política de cancelación y publica SubscriptionCancelled.
SendNotificationHandler | handle(SendNotificationCommand cmd) | NotificationDto | Evalúa preferencias, encola a channel-specific adapters.
SubscriptionQueryHandler | handle(GetSubscriptionsByUserQuery q) | List<SubscriptionDto> | Devuelve DTOs desde ReadModel.

Responsibilities
- Orquestar cobros recurrentes y manejar reintentos (retry/backoff).
- Respetar preferencias de notificación antes de enviar.
- Publicar events y encolar tareas asíncronas para envío (email/sms/push).
- Coordinar con Payment Context para cobros y con Notification adapters para entregas.

Patterns / Considerations
- Use scheduled workers for recurrent billing; implement circuit-breaker/rate-limit for provider calls.
- Ensure idempotency and saga patterns for billing + subscription state transitions.

---

### 5.6.4. Infrastructure Layer

Repository / Adapter | Name | Category | Purpose
---|---:|---:|---
SubscriptionRepositoryImpl | SubscriptionRepositoryImpl | Repository (Postgres/ORM) | Implementación de ISubscriptionRepository.
NotificationRepositoryImpl | NotificationRepositoryImpl | Repository | Persistencia de notificaciones e historial.
BillingGatewayAdapter | BillingGatewayAdapter | Adapter | Integración con pasarela de cobros recurrentes (Stripe, PayU, etc.).
EmailAdapter | EmailAdapter | Adapter | Envía emails (SendGrid/SMTP); encola y maneja retries.
SmsAdapter | SmsAdapter | Adapter | Envío de SMS (Twilio).
PushAdapter | PushAdapter | Adapter | Envío de push notifications (FCM/APNs).
MessageBroker | Message Broker | Broker | Cola para procesamiento asíncrono (Kafka/RabbitMQ).
Scheduler / Worker | Scheduler | Worker | Ejecuta tareas recurrentes (cron jobs) para renovaciones.
WebhookProcessor | WebhookProcessor | Adapter | Valida y procesa callbacks del proveedor.
ReadModelRepo | ReadModel / Materialized Views | Adapter | Vistas optimizadas para consulta rápida (user subscriptions, notification log).

Infra Methods (ejemplos)
Method | Return Type | Description
---|---:|---
chargePayment(methodToken, amount, idempotencyKey) | PaymentResult | Invoca gateway para cobro recurrente.
enqueueNotification(notification) | void | Publica notificación a MessageBroker.
getPendingNotifications(channel) | List<Notification> | Recupera notificaciones pendientes por canal.
save(subscription: Subscription) | Subscription | Persiste estado actualizado.

Infra Notes
- Almacenar only tokens / references para métodos de pago (no almacenar PAN); cumplir PCI.
- Implementar idempotency keys y reconciliación con gateway.
- Webhooks deben ser validados y procesados en colas para resiliencia.
- Mantener logs y audit trail para renovaciones y notificaciones (auditoría).
- Configurar políticas de retención para logs y historiales conforme normativa.

### 5.6.5. Bounded Context Software Architecture Component Level Diagrams

### 5.6.6. Bounded Context Software Architecture Code Level Diagrams

#### 5.6.6.1. Bounded Context Domain Layer Class Diagrams

#### 5.6.6.2. Bounded Context Database Design Diagram
