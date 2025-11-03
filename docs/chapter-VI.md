# Capítulo VI: Solution UX Design

## 6.1. Style Guidelines

La imagen visual de un producto juega un rol fundamental en el desarrollo de una identidad cohesiva y atractiva para la audiencia objetivo. Las directrices estéticas definen estándares que garantizan la coherencia de todos los elementos visuales —desde la selección tipográfica hasta la paleta cromática empleada—, manteniendo su consistencia sin importar la plataforma o medio de presentación. En las secciones siguientes, se detallarán las pautas de diseño establecidas para este proyecto.

### 6.1.1. General Style Guidelines

Definiremos criterios esenciales de diseño que funcionarán como base fundamental para desarrollar interfaces eficientes y funcionales, asegurando experiencias fluidas que fortalezcan la identidad corporativa.

**Coherencia Visual:** Mantener una apariencia homogénea en todos los elementos digitales, incorporando principios cromáticos, tipográficos y de composición. Esta armonización se extiende desde las microinteracciones hasta la estructura completa de la plataforma.

![Consitencia](../assets/img/chapter-VI/consistencia_visual.png)

**Claridad:** Enfatizar la claridad en el diseño para brindar una experiencia de usuario placentera, intuitiva y libre de complicaciones. Evitar elementos decorativos excesivos o superfluos que puedan confundir a los usuarios y obstaculizar la comprensión del contenido.

![Simplicidad](../assets/img/chapter-VI/simplicidad.png)

**Legibilidad:** Emplear tipografías claras y tamaños apropiados para asegurar que el contenido sea fácilmente comprensible en todas las plataformas y dispositivos. Conservar un contraste elevado entre texto y fondo para optimizar la legibilidad, especialmente para usuarios con limitaciones visuales.

![Legibilidad](../assets/img/chapter-VI/legibilidad.png)

**Imagen Corporativa:** Concretizar las características fundamentales de la marca a través de un esquema visual estratégico, donde la armonía entre colores, formas y texturas comunique de inmediato los principios institucionales.

![Identidad](../assets/img/chapter-VI/identidad_de_marca.png)

**Sistema Tipográfico:** Utilizar la familia Montserrat como elemento central, aprovechando su estructura neogrotesca para crear jerarquías de información precisas mediante cuatro aplicaciones específicas:

- Encabezados (H1-H6)
- Contenido textual
- Componentes interactivos
- Enlaces de navegación

![Tipografia](../assets/img/chapter-VI/tipografia.png)

**Esquema Cromático:** Nuestra gama de colores representa la esencia de nuestra marca y transmite efectivamente nuestra propuesta a los usuarios. Empleamos un azul tenue (#3F51B5) como tono principal y un púrpura sutil (#757de8) como color complementario. Estos matices se combinan con acentos como el azul brillante (#2196F3) y azul profundo (#003f8f) para destacar elementos importantes y brindar retroalimentación visual durante las interacciones. Asimismo, utilizamos fondos luminosos (#FFFFFF), fondos secundarios ligeramente atenuados (#f5f5f5) y fondos más intensos (#cccccc) para sostener una experiencia visual uniforme y atractiva en toda la aplicación.

![Colores](../assets/img/chapter-VI/Colores.png)

**Distribución Espacial:** Aplicar un sistema fundamentado en múltiplos de 8px para conseguir composiciones equilibradas, balanceando espacios vacíos y ocupados mediante proporciones doradas que faciliten el escaneo visual y la navegación táctil.

Esta metodología prioriza la generación de patrones identificables que refuercen la identidad digital manteniendo adaptabilidad flexible ante diversos contextos de aplicación.

![Espaciado](../assets/img/chapter-VI/Espaciado.png)

### 6.1.2. Web, Mobile & Devices Style Guidelines

**Diseño Adaptativo:** Es fundamental crear una interfaz flexible que se ajuste dinámicamente a múltiples dispositivos y resoluciones, garantizando una navegación suave y una experiencia de usuario consistente en smartphones, tablets y computadoras de escritorio. El objetivo principal es preservar la funcionalidad y estética independientemente del canal de acceso.

![Resposive](../assets/img/chapter-VI/responsive_design.png)

**Interfaz Orientada a la Usabilidad:** Desarrollar elementos de diseño familiares (botones claros, menús desplegables, barras de búsqueda fáciles de usar) para minimizar el tiempo de aprendizaje. La uniformidad visual y espacial en la organización de componentes entre páginas reforzará la familiaridad y productividad durante el uso.

![Interface](../assets/img/chapter-VI/interfaz_intuitiva.png)

**Compatibilidad Cross-browser:** Asegurar un funcionamiento homogéneo en navegadores principales (Chrome, Firefox, Safari, Edge) a través de evaluaciones técnicas exhaustivas. Esto abarca verificar funciones avanzadas, representación visual y adaptabilidad para brindar una experiencia libre de discrepancias, sin importar la plataforma seleccionada por el usuario.

![Compatibility](../assets/img/chapter-VI/compatibilidad_con_navegadores.jpg)

**Estructura Visual en Z:** Utilizar el recorrido visual instintivo en forma de "Z" para distribuir contenidos de manera estratégica: elementos principales (logotipos, botones de acción) en áreas laterales izquierdas (arriba/abajo), y componentes de apoyo (iconos, vínculos) en zonas derechas. Esta organización dirige la atención y mejora la claridad del mensaje.

![Patern](../assets/img/chapter-VI/Patron_Z.jpg)

**Mejora de Rendimiento:** Optimizar el funcionamiento del sitio web para lograr tiempos de carga veloces y una experiencia de usuario ininterrumpida. Esto contempla la optimización de imágenes, implementación de técnicas de compresión y reducción del código para disminuir el tiempo de carga de páginas.

![Optimization](../assets/img/chapter-VI/velocidad_de_carga_optimizada.png)

**Protección y Privacidad:** Integrar medidas de seguridad y privacidad en el diseño del producto para salvaguardar la información sensible de los usuarios. Esto incluye el empleo de conexiones HTTPS, cifrado de datos y cumplimiento de normativas de privacidad.

![Security](../assets/img/chapter-VI/seguridad_privacidad.png)

#### iOS Mobile Style Guidelines

**Conformidad con las Directrices de Apple (HIG):**

**Áreas Táctiles y Ergonomía:**
- Elementos de contacto mínimos de **44x44 puntos**
- Áreas de interacción ergonómicas para el pulgar
- Separación entre elementos interactivos

**Sistema Tipográfico:**
- **San Francisco** como tipografía principal del sistema
- Estructura clara con **Dynamic Type**
- Adaptabilidad con escalado de texto

**Esquema de Color y Temas:**
- Integración con **modo claro/oscuro** del sistema
- Colores de marca adaptados a **directrices iOS**
- Contraste mínimo de **4.5:1** para texto

**Elementos y Patrones de Navegación:**
- **Navigation Bars** con títulos descriptivos
- **Tab Bars** para navegación primaria
- **Gestos de deslizamiento** estándar de iOS

**Diseño Responsivo:**
- Compatibilidad con **Safe Areas**
- Ajuste a diversos tamaños de iPhone
- **Auto Layout** adaptativo

**Accesibilidad:**
- Integración con **VoiceOver**
- Compatibilidad con **Dynamic Type**
- Etiquetas de accesibilidad informativas

#### Android Mobile Style Guidelines

**Conformidad con Material Design 3 (Material You):**

**Objetivos Táctiles y Densidad Visual:**
- Elementos de contacto mínimos de **48x48 dp**
- Sistema de cuadrícula basado en **8dp**
- Densidades ajustables según dispositivo

**Sistema Tipográfico:**
- **Roboto** como tipografía fundamental del sistema
- Escalas tipográficas **Material Type Scale**
- Compatibilidad con diferentes densidades

**Sistema Cromático Dinámico:**
- Integración con **Material Theme Builder**
- Compatibilidad con **Dynamic Color** (Android 12+)
- Paleta que se adapta según fondo de pantalla del usuario

**Elementos y Navegación:**
- **FAB (Floating Action Button)** para acciones primarias
- **Navigation Drawer** para menús laterales
- **Bottom Navigation** para secciones principales

**Patrones de Interacción:**
- **Ripple Effect** en elementos seleccionables
- **Shared Element Transitions**
- **Back Gesture** nativo de Android

**Optimización para Dispositivos:**
- **ConstraintLayout** para diseños eficientes
- Compatibilidad con pantallas plegables
- Adaptación a diferentes densidades

**Accesibilidad y Localización:**
- Integración con **TalkBack**
- Texto escalable en unidades **sp**
- Compatibilidad **RTL (Right-to-Left)**

## 6.2. Information Architecture

La estructura de información resulta esencial para organizar y estructurar contenidos de manera intuitiva, asegurando accesibilidad y entendimiento para el usuario. Esta sección establece los fundamentos que sostienen la experiencia: esquemas de organización, etiquetado, SEO, búsqueda y navegación. Su aplicación estratégica mejora la fluidez y eficacia en la interacción, facilitando que los usuarios localicen información pertinente con mínima resistencia.

### 6.2.1. Organization Systems

Ordenan el contenido de forma lógica y jerárquica para simplificar su exploración:

- **Estructura informativa:** Subdivide el contenido en capas (categorías > subcategorías), facilitando una navegación gradual y sistemática.

- **Clasificación temática:** Organiza la información en módulos temáticos interconectados para una búsqueda contextual.

- **Jerarquización estratégica:** Resalta contenidos esenciales (ej: promociones, actualizaciones) en ubicaciones destacadas para optimizar su visibilidad.

- **Clasificación semántica:** Vincula términos clave o etiquetas al contenido para mejorar su localización mediante búsquedas o filtros.

### 6.2.2. Labeling Systems

Los esquemas de etiquetado resultan esenciales para simplificar la navegación y localización de información dentro del producto. Existen diversas metodologías para categorizar el contenido dentro de un producto y su selección depende de los requerimientos específicos del usuario.

- **Etiquetas explicativas:** Emplean lenguaje directo y específico para caracterizar contenidos (ej: "Manual de configuración detallado").

- **Etiquetas adaptadas:** Modifican la terminología según el tipo de usuario (ej: "Para creativos" vs. "Para programadores").

- **Etiquetas automáticas:** Crean automáticamente tags fundamentados en tendencias, interacciones o relevancia algorítmica (ej: "Novedades 2024").

### 6.2.3. Searching Systems

Los mecanismos de búsqueda constituyen elementos fundamentales en un producto que facilitan a los usuarios localizar rápidamente la información deseada. En esta área, se describirán los diversos tipos de sistemas de búsqueda empleados, así como las mejores prácticas para mejorar la eficacia y precisión de la búsqueda dentro del producto:

- **Búsqueda elemental:** Coincidencias directas o semánticas de términos clave.

- **Filtros de criterios múltiples:** Refinan resultados por fecha, formato de archivo o categoría.

- **Búsqueda por facetas:** Facilita combinar atributos (ej: costo + color + marca).

- **Clasificación por importancia:** Prioriza resultados usando IA/ML según historial del usuario.

### 6.2.4. SEO Tags and Meta Tags

Las etiquetas SEO (Optimización para Motores de Búsqueda) y las metaetiquetas juegan un papel fundamental en la visibilidad y posicionamiento del contenido en buscadores web. Hay diversos tipos de etiquetas SEO y metaetiquetas, se mostrarán algunos de los más relevantes:

- **Etiqueta de Título (Title Tag):** Esta constituye una de las etiquetas más cruciales para SEO. Establece el título de una página web y se muestra como el título principal en los resultados de búsqueda. Es fundamental que el título sea descriptivo, pertinente y contenga términos clave relacionados con el contenido de la página.

- **Metaetiqueta de Descripción (Meta Description Tag):** Esta etiqueta ofrece una descripción concisa del contenido de la página. Aunque no impacta directamente en el ranking de búsqueda, una meta descripción bien elaborada puede influir en la tasa de click (CTR) al brindar a los usuarios una perspectiva clara del contenido de la página.

- **Etiqueta de Encabezado (Header Tags):** Estas etiquetas como H1, H2, H3, etc., se emplean para establecer la estructura y jerarquía del contenido de una página. Los motores de búsqueda utilizan los encabezados para comprender la organización del contenido y su importancia para los usuarios.

- **Etiqueta de Lenguaje (Language Tag):** Esta etiqueta se emplea para indicar el idioma principal del contenido de la página. Es beneficiosa para la clasificación en búsquedas locales y para asistir a los motores de búsqueda a interpretar el idioma del contenido.

- **Metaetiqueta de Robots (Meta Robots Tag):** Esta etiqueta instruye a los motores de búsqueda sobre cómo indexar y rastrear la página. Puede determinar si se debe indexar la página, seguir los enlaces o si se deben aplicar ciertas directrices específicas.

### 6.2.5. Navigation Systems

Los mecanismos de navegación resultan fundamentales para facilitar que los usuarios exploren y se desplacen por el contenido del producto de forma efectiva. Existen varios tipos de sistemas de navegación que se pueden implementar para facilitar la exploración y accesibilidad del contenido, se mostrarán algunos de los más frecuentes:

- **Menús estructurados:** Desplegables o mega-menús para contenido complejo.

- **Navegación por secciones:** Organiza áreas sin recargar la página.

- **Simbolos intuitivos:** Íconos universales (ej: carrito de compras, lupa de búsqueda).

- **Desplazamiento continuo:** Apropiado para flujos de contenido (ej: redes sociales, blogs).

## 6.3. Landing Page UI Design

La página de aterrizaje es fundamental para captar el interés de los usuarios y orientarlos hacia acciones específicas, como suscribirse, adquirir un producto o informarse sobre un servicio. En esta sección, se abordará el diseño de la interfaz de usuario de la página de aterrizaje, enfocándose en elementos esenciales para optimizar la experiencia del usuario, proporcionando una página dinámica e intuitiva.

### 6.3.1. Landing Page Wireframe

El esquema de la página de aterrizaje constituye una representación visual estructural que ilustra la organización básica y el diseño de la página. Este esquema funciona como un plan para el diseño final y ofrece una guía clara para la ubicación de los elementos principales en la página de aterrizaje.

El esquema de la página de aterrizaje contemplará:

- **Cabecera:** Esta área contendrá el logotipo de la marca y posiblemente un lema o mensaje conciso para captar el interés del usuario.

- **Área de Beneficios:** Resaltará las principales características o ventajas del producto o servicio ofrecido, empleando imágenes y texto conciso para comunicar el mensaje de manera efectiva.

- **Llamado a la Acción (CTA):** Se incorporará un botón de llamado a la acción destacado que motive a los usuarios a ejecutar una acción específica, como suscribirse, comprar u obtener más detalles.

- **Testimoniales o Valoraciones:** Esta área puede exhibir testimonios de clientes satisfechos o valoraciones positivas para crear confianza y credibilidad en el producto o servicio.

- **Área de Contacto o Formulario:** Facilitará a los usuarios comunicarse con la empresa o enviar consultas directamente desde la página de aterrizaje, ofreciendo una forma práctica de interactuar.

El esquema funcionará como punto de referencia para el diseño visual y la implementación de la página de aterrizaje, garantizando una experiencia de usuario coherente y efectiva.

### 6.3.2. Landing Page Mock-up

**Sección Principal de la aplicación:** El área principal diseñada para nuestro informe sobre ReStyle muestra una imagen de fondo que exhibe diversos proyectos de diseño de interiores, complementada con un botón de llamado a la acción "¡Comienza ya!" para estimular la participación. Con un título impactante y una descripción concisa, esta sección introduce a los visitantes en la esencia de nuestra compañía, mientras que una barra de navegación ofrece acceso directo a las diferentes secciones del informe, proporcionando una experiencia de lectura fluida y envolvente.

![Hero](../assets/img/chapter-VI/landing-page-header.png)

**Imagen y Razones de la aplicación:** En esta área, destacaremos las razones persuasivas por las cuales los clientes deberían seleccionarnos para renovar sus departamentos. Nuestro enfoque centrado en la excelencia e innovación, respaldado por un equipo de especialistas en diseño de interiores, asegura resultados excepcionales que exceden las expectativas. Los propietarios nos eligen para transformar sus espacios en hogares contemporáneos y funcionales, gracias a nuestra atención minuciosa al detalle y nuestro compromiso con la calidad en cada proyecto que desarrollamos.

![Images](../assets/img/chapter-VI/landing-page-imagenymotivos.png)

**Cobertura de la aplicación:** En el área dedicada a nuestros paquetes de servicio, mostramos tres alternativas diseñadas para cubrir las necesidades de nuestros clientes: Paquete Crece+, Paquete Pro y Paquete Pro+. Cada paquete brinda una variedad única de servicios y beneficios ajustados a diferentes presupuestos y metas de diseño.

![Alcance](../assets/img/chapter-VI/landing-page-alcance.png)

**Información de la aplicación:** En el área dedicada a nuestra aplicación, brindamos una descripción concisa de nuestra propuesta de valor, destacando cómo nuestra aplicación facilita y enriquece la experiencia de diseño de interiores para nuestros usuarios. Acompañando esta descripción, mostramos una imagen de nuestra aplicación junto con dos atractivos botones de llamado a la acción, uno para descargar desde Google Play y otro desde la App Store, ofreciendo a los usuarios acceso rápido y práctico a nuestra plataforma desde cualquier dispositivo móvil.

![Images](../assets/img/chapter-VI/landing-page-acerdade.png)

**Comentarios de la aplicación:** En el área de comentarios, compartimos las experiencias genuinas de nuestros clientes satisfechos. Cada comentario está acompañado de una imagen del cliente junto con una descripción breve que resalta cómo nuestra empresa transformó sus espacios y excedió sus expectativas. Estos comentarios ofrecen evidencia tangible de la calidad e impacto positivo de nuestro trabajo, contribuyendo a generar confianza y credibilidad entre nuestros potenciales clientes.

![Images](../assets/img/chapter-VI/landing-page-testimonios.png)

**Comunicación de la aplicación:** En nuestra área de Comunicación, te proporcionamos una forma simple y práctica de contactarte con nosotros. Mostramos un formulario donde puedes ingresar tu nombre completo, correo electrónico y un mensaje describiendo cómo podemos asistirte. Esta herramienta nos facilita comprender tus requerimientos de manera exacta y responder de forma eficaz, brindándote la mejor ayuda posible. Estamos dedicados a proporcionarte un servicio personalizado y atento en cada etapa del proceso.

![Images](../assets/img/chapter-VI/landing-page-contactanos.png)

**Nuestro equipo:** En el área Nuestro Equipo, te invitamos a conocer más sobre las personas dedicadas que hacen realidad nuestra empresa. Mostramos un video que brinda una perspectiva íntima y genuina de nuestro equipo, resaltando nuestras competencias, experiencia y dedicación con la excelencia en el diseño de interiores. A través de este video, deseamos compartir nuestra trayectoria, valores y visión, mostrándote la esencia y el espíritu de nuestra empresa.

![Images](../assets/img/chapter-VI/landing-page-sobreNosotros.png)

**Pie de página de la aplicación:** En nuestro Pie de página, te proporcionamos acceso directo a nuestras redes sociales y métodos de contacto adicionales. Mostramos nuestro logo característico de la empresa, junto con enlaces para seguirnos en Twitter, Facebook e Instagram, manteniéndote informado de nuestras últimas novedades y proyectos. Además, ofrecemos un número telefónico de referencia para que nos contactes directamente y un correo electrónico de nuestra empresa, garantizando múltiples canales de comunicación para satisfacer tus necesidades y consultas.

![Images](../assets/img/chapter-VI/landing-page-footer.png)

**Enlaces del proyecto (referencias rápidas):**
- Landing Page: https://si0728-7281-grupo3.github.io/landingpage/
- Front (App web): https://restyle-1asi0728-7281.netlify.app
- Backend (Swagger / API): https://restyle-platform-bed4c3b3f3eug0ak.canadacentral-01.azurewebsites.net/swagger-ui/index.html

## 6.4. Applications UX/UI Design

### 6.4.1. Applications Wireframes

#### Mobile Applications Wireframes

**Área de Bienvenida: Registro e Inicio de Sesión**

En esta área, los usuarios podrán observar una pantalla con las alternativas de registrarse o iniciar sesión en la aplicación.

![Welcome](../assets/img/chapter-VI/welcome.png)

**Área de Bienvenida: Registro de Usuarios**

En esta área, el usuario podrá registrarse suministrando su nombre completo, correo electrónico, contraseña y confirmación de la misma. Después de completar estos campos, podrá seleccionar el botón "Regístrate". Además, se proporcionará una alternativa para recuperar su cuenta en caso de haber olvidado la contraseña.

![Register](../assets/img/chapter-VI/register.png)

**Área de Bienvenida: Inicio de Sesión**

En esta área, el usuario podrá iniciar sesión proporcionando su correo electrónico y contraseña. Tendrá la alternativa de marcar "Recordar cuenta" para simplificar futuros accesos, o emplear la opción "Olvidé mi contraseña" si necesita recuperar su cuenta. Si los datos son correctos, la sesión se iniciará exitosamente.

![Login](../assets/img/chapter-VI/login.png)

**Área de Recuperación de Contraseña**

Si el usuario no recuerda su contraseña, tendrá la alternativa de recuperarla proporcionando su correo electrónico. Al completar este dato, se enviará un enlace o instrucciones para proceder con la recuperación de la cuenta directamente desde la aplicación.

![Recover password](../assets/img/chapter-VI/recover_password.png)

**Área de Publicaciones y Búsqueda**

En esta área, el usuario podrá observar una barra de búsqueda para simplificar la navegación. También se mostrarán las publicaciones disponibles para mayor interactividad. La ubicación y el logo de "ReStyle" estarán claramente visibles para asegurar una mejor comprensión, flexibilidad y familiaridad con la marca.

![Start Search](../assets/img/chapter-VI/start_search.png)

**Área de Perfil del Usuario**

En esta área, el usuario podrá visualizar su perfil, que incluye una foto representativa y sus datos personales, como nombre completo, correo electrónico, teléfono, dirección y una descripción breve. Si el usuario está conforme con la información mostrada, podrá seleccionar el botón "Guardar" para confirmar y actualizar su perfil.

![Profile](../assets/img/chapter-VI/profile.png)

**Área de Detalles de la Aplicación**

En esta área, el usuario podrá observar información adicional sobre la aplicación, evaluarla y publicar su reseña. También tendrá la alternativa de visualizar más detalles para obtener una comprensión más completa de las características y funcionalidades de la aplicación.

![Review Portfolio](../assets/img/chapter-VI/review_portfolio.png)

![Review](../assets/img/chapter-VI/review.png)

**Área de Foro de Ayuda y Contacto**

En esta área, el usuario podrá acceder a un foro de ayuda donde encontrará preguntas y respuestas a dudas frecuentes. Además, tendrá la alternativa de contactarnos completando un formulario con su nombre completo, correo electrónico y un mensaje detallado sobre su inquietud. Al finalizar, podrá seleccionar "Enviar mensaje" para transmitir su consulta.

![Support](../assets/img/chapter-VI/support.png)

#### Web Applications Wireframes

**Acceso de la aplicación**

![Wireframe login](../assets/img/chapter-VI/wifreframe-login.png)

**Crear perfil de propietario**

![Wireframe propietario](../assets/img/chapter-VI/wifreframe-perfil-propietario.png)

**Crear perfil de remodelador**

![wireframe remodelador](../assets/img/chapter-VI/wifreframe-perfil-remodelador.png)

**Modificar perfil de propietario**

![wireframe editar propietario](../assets/img/chapter-VI/wifreframe-editar-propietario.png)

**Modificar perfil de propietario mensaje**

![wireframe editar propietario](../assets/img/chapter-VI/wifreframe-editar-propietario-exito.png)

**Modificar perfil de remodelador**

![Wireframe editar remodelador](../assets/img/chapter-VI/wifreframe-editar-remodelador.png)

**Modificar perfil de remodelador mensaje**

![Wireframe editar remodelador](../assets/img/chapter-VI/wifreframe-editar-remodelador-exito.png)

**Localización de remodeladores**

![Wireframe Busqueda remodelador](../assets/img/chapter-VI/wireframe-busqueda.png)

**Localización de remodeladores por filtro**

![Wireframe Filtro](../assets/img/chapter-VI/wireframe-busqueda-por-filtro.png)

**Contratar remodelador**

![Wireframe Contratar remodelador](../assets/img/chapter-VI/wireframe-contratar-remodelador.png)

**Contratar remodelador y enviar formulario**

![Wireframe Envio formulario](../assets/img/chapter-VI/wireframe-enviar-form-contratar.png)

**Comunicación con remodelador**

![Wireframe Mensajes](../assets/img/chapter-VI/wireframe-mensajes-con-remodelador.png)

**Portafolio remodelador**

![Wireframe Portfolio](../assets/img/chapter-VI/wireframe-portafolio.png)

**Modificar portafolio**

![Wireframe Editar Portfolio](../assets/img/chapter-VI/wireframe-portafolio-editar.png)

**Monitoreo de proyecto**

![Wireframe seguimiento](../assets/img/chapter-VI/wireframe-seguimiento-proyecto.png)

**Detalles del monitoreo de proyecto**

![Wireframe detalles seguimiento](../assets/img/chapter-VI/wireframe-seguimiento-proyecto-detalle.png)

**Administración de solicitudes de proyectos**

![Wireframe gestion](../assets/img/chapter-VI/wireframe-gestion-solicitudes.png)

**Valoraciones**

![Wireframe reviews](../assets/img/chapter-VI/wifreframe-reviews.png)

**Detalles de valoraciones**

![Wireframe detalle reviews](../assets/img/chapter-VI/wifreframe-reviews-detalle.png)

**Crear valoración**

![Wireframe crear reviews](../assets/img/chapter-VI/wireframe-crear-review.png)

**Crear valoración con éxito**

![Wireframe crear reviews con exito](../assets/img/chapter-VI/wireframe-crear-review-exito.png)

### 6.4.2. Applications Wireflow Diagrams

Los Wireflows se emplean principalmente en el diseño UX o experiencia de usuario y especialmente para aplicaciones que incluyen flujos de trabajo e interacciones complejas.

#### Mobile Applications Wireflow Diagrams

**Objetivo del Usuario: Acceder a la pantalla principal de la aplicación**

![Goal 1](../assets/img/chapter-VI/goal1.png)

**Objetivo del Usuario: Visualizar y modificar el perfil de usuario**

![Goal 2](../assets/img/chapter-VI/goal2.png)

**Objetivo del Usuario: Visualización de Valoraciones y Portafolio de una empresa remodeladora**

![Goal 3](../assets/img/chapter-VI/goal3.png)

#### Web Applications Wireflow Diagrams

![Wireflows](../assets/img/chapter-VI/wireflow-diagram.png)
