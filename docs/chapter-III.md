# Capítulo III: Requirements Specification

## 3.1. To-Be Scenario Mapping

[![To-be.jpg](https://i.postimg.cc/xjNjNJWt/To-be.jpg)](https://postimg.cc/qg0H9RB3)
[![To-be-2.jpg](https://i.postimg.cc/kMKsBYmv/To-be-2.jpg)](https://postimg.cc/8skMYHs7)

## 3.2. User Stories

<table>
      <thead>
            <tr>
                <th>Epic / Story ID</th>
                <th>Título</th>
                <th>Descripción</th>
                <th>Criterios de Aceptación</th>
                <th>Relacionado con (Epic ID)</th>
            </tr>
      </thead>
      <tbody>
            <tr>
                <td>EPIC-001</td>
                <td>Establecer comunicación con los remodeladores</td>
                <td>
                    <strong>Como</strong> usuario contratista, <strong>quiero</strong> establecer comunicación
                    efectiva con los remodeladores <strong>para</strong> poder expresar mis necesidades, expectativas
                    y recibir información actualizada sobre el proyecto de remodelación.
                </td>
                <td>N/A</td>
                <td>N/A</td>
            </tr>
            <tr>
                <td>EPIC-002</td>
                <td>Contratación de servicios de remodelación</td>
                <td>
                    <strong>Como</strong> usuario contratista, <strong>quiero</strong> contratar los servicios
                    de remodelación de manera eficiente y llevar un control <strong>para</strong> asegurar que el 
                    proyecto se realice acorde a mi presupuesto y necesidades.
                </td>
                <td>N/A</td>
                <td>N/A</td>
            </tr>
            <tr>
                <td>EPIC-003</td>
                <td>Implementar API RESTful</td>
                <td>
                <strong>Como</strong> desarrollador, <strong>quiero</strong> implementar una API RESTful
                <strong>para</strong> poder acceder a los datos del sistema de forma segura.
                </td>
                <td>N/A</td>
                <td>N/A</td>
            </tr>
            <tr>
                <td>EPIC-004</td>
                <td>Implementar Landing Page</td>
                <td>
                    <strong>Como</strong> vistante de la landing page, <strong>quiero</strong> acceder a una
                    Landing Page con distintas secciones informativas e interactivas que mencionen las características
                    y beneficios que obtendré <strong>para</strong> tener un conocimiento claro de la aplicación.
                </td>
                <td>N/A</td>
                <td>N/A</td>
            </tr>
            <tr>
                <td>EPIC-005</td>
                <td>Gestión de portafolio</td>
                <td>
                    <strong>Como</strong> usuario remodelador, <strong>quiero</strong> tener una herramienta
                    que me ayude a gestionar mi portafolio de proyectos de manera eficiente <strong>para</strong> poder 
                    compartir mi trabajo a los contratistas interesados en mi perfil.
                </td>
                <td>N/A</td>
                <td>N/A</td>
            </tr>
            <tr>
                <td>EPIC-006</td>
                <td>Gestión de proyecto</td>
                <td>
                    <strong>Como</strong> usuario remodelador, <strong>quiero</strong> tener una herramienta
                    que me ayude a gestionar el proyecto encargado por un contratista <strong>para</strong>
                    permitir el monitoreo de los avances y cumplimiento de los objetivos, presupuesto y cronograma.
                </td>
                <td>N/A</td>
                <td>N/A</td>
            </tr>
            <tr>
                <td>EPIC-007</td>
                <td>Gestión de suscripción</td>
                <td>
                    <strong>Como</strong> usuario remodelador, <strong>quiero</strong> contar con la posibilidad de 
                    suscribirme a un plan de pago <strong>para</strong> acceder a beneficios exclusivos y mejorar mi
                    experiencia en la aplicación.
                </td>
                <td>N/A</td>
                <td>N/A</td>
            </tr>
            <tr>
                <td>EPIC-008</td>
                <td>Implementación de Chatbot de Atención al Cliente en App Web</td>
                <td>
                    <strong>Como</strong> plataforma de servicios de remodelación, <strong>quiero</strong> incorporar un chatbot de atención al cliente en la aplicación web <strong>para</strong> brindar soporte automatizado e inmediato a usuarios (contratistas y remodeladores), ayudándoles con consultas frecuentes, estimaciones de presupuesto y derivación a soporte humano cuando sea necesario, mejorando así la experiencia de usuario y reduciendo la carga de atención directa.
                </td>
                <td>
                    - El chatbot debe estar disponible <strong>solo en la aplicación web</strong> (no en LP ni app móvil por ahora).<br>
                    - Debe responder en menos de 3 segundos.<br>
                    - Debe entender al menos 10 intenciones diferentes (ej: presupuesto, uso de app, contacto).<br>
                    - Debe integrarse con un sistema de soporte humano para escalado de consultas (ej: chat en vivo o ticket).<br>
                    - Debe incluir un sistema de feedback para calificar respuestas (ej: thumbs up/down).<br>
                    - Debe ser accesible desde todas las pantallas de la app web.
                </td>
                <td>N/A</td>
            </tr>
      </tbody>
</table>

<table>
    <thead>
        <tr>
            <th>Epic / Story ID</th>
            <th>Título </th>
            <th>Descripción</th>
            <th>Criterios de Aceptación</th>
            <th>Relacionado con (Epic ID)</th>
        </tr>
    </thead>
    <body  >
        <tr style="text-align:center">
            <td>US-001</td>
            <td>Hipervínculos en el encabezado</td>
            <!-- Descripción -->
            <td> 
            <strong>Como</strong> visitante de la landing page, 
            <strong>quiero</strong> que las opciones del encabezado me dirijan a las diferentes secciones de la Landing Page 
            <strong>para</strong>, poder navegar de forma rapida y fluida. 
            </td>
            <!-- ---------- -->
            <!-- Criterios de Aceptación -->
            <td> 
            <h5>Escenario 01: Navegación fluida.</h5>
            <strong>Dado</strong> Un usuario ha navegado a una sección de la Landing Page.
            <strong>cuando</strong> El usuario hace clic en otra opción del encabezado.
            <strong>Entonces</strong> La página se desplaza suavemente a la nueva sección seleccionada.
            <strong>Y</strong> La URL de la página cambia para reflejar la nueva sección.
            <!-- ---------- -->
            <h5>Escenario 02: Múltiples Dispositivos</h5>
            <strong>Dado</strong> Un usuario visita la landing page desde un dispositivo móvil.
            <strong>cuando</strong> El usuario hace clic en una opción del encabezado.
            <strong>Entonces</strong> La página se desplaza suavemente a la sección correspondiente, adaptándose al tamaño de la pantalla del dispositivo.
            </td>
            <td>EPIC-004</td>
        </tr>
        <tr style="text-align:center">
            <td>US-002 </td>
            <td>Información sobre beneficios de la aplicación</td>
            <!-- Descripción -->
            <td>
            <strong>Como</strong> usuario, 
            <strong>quiero</strong> saber más sobre los beneficios de la aplicación web 
            <strong>para</strong> considerar ser miembro de la aplicacion. 
            </td>
            <!-- Criterios de Aceptación -->
            <td>
            <h5>Escenario 01: Navegación a la sección de beneficios</h5>
            <strong>Dado</strong> Un usuario visita la página de inicio de la aplicación web.
            <strong>Cuando</strong> El usuario hace clic en la sección "Beneficios".
            <strong>Entonces</strong> Se muestra una página con información clara y concisa sobre los beneficios de la aplicación.
            <strong>Y</strong> La información incluye una lista de beneficios, imágenes ilustrativas y ejemplos concretos.
            <strong>Y</strong> La página ofrece la posibilidad de descargar la aplicación o registrarse para obtener una prueba gratuita. 
            Dado: Un usuario está leyendo la página de beneficios.
            <h5>Escenario 02: Información Clara y Concisa</h5>
            <strong>Dado</strong> Un usuario está leyendo la página de beneficios.
            <strong>Cuando</strong> El usuario lee la información sobre un beneficio específico.
            <strong>Entonces</strong> La información es fácil de entender y no contiene lenguaje técnico.
            <strong>Y</strong> La información se presenta de forma organizada y atractiva.
            </td>
            <td>EPIC-004 </td>
        </tr>
        <tr style="text-align:center">
            <td>US-003</td>
             <td>Mostrar los planes disponibles</td>
            <!-- Descripción -->
            <td>
            <strong>Como</strong> visitante del landing page, 
            <strong>quiero</strong> saber sobre los planes que tiene, 
            <strong>para</strong> poder analizar si el plan que me ofrecen se adecua a las necesidades de mi negocio.
            </td>
            <!-- Criterios de Aceptación -->
            <td> 
            <h5>Escenario 1: Información Clara y Concisa.</h5>
            <strong>Dado</strong> Un usuario está leyendo la página de un plan específico.
            <strong>Cuando</strong> El usuario lee la información sobre una función específica del plan.
            <strong>Entonces</strong> La información es fácil de entender y no contiene lenguaje técnico.
            <strong>Y</strong> La información se presenta de forma organizada y atractiva.
            <h5>Escenario 2: Comparación de Planes.</h5>
            <strong>Dado</strong> Un usuario está leyendo la página de un plan específico.
            <strong>Cuando</strong> El usuario quiere comparar el plan con otro plan.
            <strong>Entonces</strong> La página ofrece una herramienta para comparar los planes en paralelo, mostrando las diferencias en precio, funciones, beneficios y limitaciones.
            </td>
            <td> EPIC-004</td>
        </tr>
        <tr style="text-align:center">
            <td>US-004 </td>
            <td> Información útil en el footer </td>
            <!-- Descripción -->
            <td>
            <strong>Como</strong> usuario que visita la landing page, 
            <strong>quiero</strong> encontrar información útil en el footer 
            <strong>para</strong> poder contactarme con la empresa, conocer más sobre ella, leer sus políticas y seguirla en redes sociales.</td>
            <!-- Criterios de Aceptación -->
            <td>
            <h5>Escenario 01: Información de Contacto</h5>
            <strong>Dado </strong> Un usuario visita la landing page.
            <strong>Cuando</strong> El usuario busca información de contacto en el footer.
            <strong>Entonces</strong> El footer muestra la siguiente información de correo electrónico, teléfono y dirección
            <strong>Y</strong> La información de contacto está resaltada en un color diferente al resto del texto del footer.
            <h5>Escenario 02: Redes Sociales</h5>
            <strong>Dado</strong> Un usuario visita la landing page.
            <strong>Cuando</strong> El usuario busca los iconos de redes sociales en el footer.
            <strong>Entonces</strong> El footer muestra iconos de las redes sociales Facebook, Twitter e Instagram.
            <strong>Y</strong> Al hacer clic en un icono de red social, el usuario es dirigido a la página de la empresa en esa red social.
            <h5>Escenario 03: Navegación</h5>
            <strong>Dado</strong> Un usuario visita la landing page.
            <strong>Cuando</strong> El usuario decida visitar otras secciones desde el footer.
            <strong>Entonces</strong> El footer muestra las opciones de navegación de las secciones de la landing page
            <strong>Y</strong> Al hacer clic en alguna de las opciones, el usuario es dirigido a la sección correspondiente
            </td>
            <td>EPIC-004 </td>
        </tr>
        <tr style="text-align:center">
            <td> US-005</td>
            <td> Información sobre el producto </td>
            <!-- Descripción -->
            <td> 
            <strong>Como</strong> usuario que visita la landing page, 
            quiero entender claramente qué ofrece el producto 
            <strong>para</strong> poder tomar una decisión informada sobre si adquirirlo o no.
            </td>
             <!-- Criterios de Aceptación -->
            <td> 
            <h5>Escenario 1: Descripción Clara y Concisa</h5>
            <strong>Dado</strong> Un usuario visita la landing page.
            <strong>Cuando</strong> El usuario lee y visualiza un video sobre la descripción del producto 
            <strong>Entonces</strong> La descripción del producto debe ser:
            clara y concisa, resaltar los beneficios clave del producto, enfatizar las ventajas que ofrece el producto al usuario 
            <strong>Y</strong> así Motivar al usuario a adquirir el producto.
            <h5>Escenario 02: Llamado a la Acción</h5>
            <strong>Dado</strong> un usuario ha leído la información del producto.
            <strong>Cuando</strong> el usuario decide que quiere adquirir el producto.
            <strong>Entonces</strong> la sección del producto debe ofrecer un botón claro y visible para descargar e iniciar a utilizar el producto.
            </td>
            <td>EPIC-004 </td>
        </tr>
        <tr style="text-align:center">
            <td> US-006 </td>
            <td> Subir contenido a un portafolio </td>
           <!-- Descripción -->
            <td> 
            <strong>Como</strong> usuario remodelador,
            <strong> quiero </strong> poder subir contenido multimedia a mi portafolio online
            <strong>para</strong> poder promocionar servicios y proyectos pasados a mis posibles clientes.  
            </td>
            <!-- Criterios de Aceptación -->
            <td> 
            <h5>Escenario 01: </h5>
            <strong>Dado</strong> que el remodelador se encuentra en su portafolio dentro de su perfil de ReStyle
            <strong>Cuando</strong> sube contenido a la aplicación
            <strong>Y</strong> guarda los cambios
            <strong>Entonces</strong> el sistema muestra los contenidos subidos en la plataforma y le notifica al remodelador sobre los cambios realizados.
            <h5>Escenario 02: </h5>
            <strong>Dado</strong> que el remodelador se encuentra en su portafolio dentro de su perfil de ReStyle
            <strong>Cuando</strong> sube contenido a la aplicación
            <strong>Y</strong> no guarda los cambios
            <strong>Entonces</strong> el sistema le notifica al usuario que necesita guardar los cambios para ver los contenidos en la plataforma. 
            <h5>Escenario 03: </h5>
            <strong>Dado</strong> que el remodelador se encuentra en su portafolio dentro de su perfil de ReStyle
            <strong>Cuando</strong> intenta subir contenido a la aplicación que supera los límites de carga
            <strong>Entonces</strong> el sistema le notifica al usuario que necesita respetar los límites de carga para poder subir los contenidos a la plataforma. 
            </td>
            <td>EPIC-005 </td>
        </tr>
        <tr style="text-align:center">
            <td> US-007 </td>
            <td> Búsqueda de empresas remodeladoras </td>
           <!-- Descripción -->
            <td> 
            <strong>Como</strong> visitante del segmento contratista,
            <strong>quiero</strong> poder buscar remodeladoras por ubicación o expertise
            <strong>para</strong> obtener un resultado más personalizado.  
            </td>
            <!-- Criterios de Aceptación -->
            <td> 
            <h5>Escenario 01: </h5>
            <strong>Dado</strong> que el visitante del segmento contratista se encuentra en la plataforma de ReStyle
            <strong>Cuando</strong> realiza una búsqueda
            <strong>Y</strong> selecciona la ubicación mediante un filtro
            <strong>Entonces</strong> el sistema solo le muestra las remodeladoras que cumplen con los requisitos.
            <h5>Escenario 02: </h5>
            <strong>Dado</strong> que el visitante del segmento contratista se encuentra en la plataforma de ReStyle
            <strong>Cuando</strong> realiza una búsqueda
            <strong>E</strong> ingresa en la barra de busqueda el expertise de su preferencia
            <strong>Entonces</strong> el sistema solo le muestra las remodeladoras que cumplen con los requisitos.
            <h5>Escenario 03: </h5>
            <strong>Dado</strong> que el visitante del segmento contratista se encuentra en la plataforma de ReStyle
            <strong>Cuando</strong> realiza una búsqueda
            <strong>Y</strong> no selecciona ningún filtro
            <strong>Entonces</strong> el sistema le muestra todas las remodeladoras disponibles.
            </td>
            <td>EPIC-001 </td>
        </tr>
        <tr style="text-align:center">
            <td> US-008 </td>
            <td> Revisar críticas y opiniones </td>
           <!-- Descripción -->
            <td> 
            <strong>Como</strong> visitante del segmento contratista,
            <strong>quiero</strong> ver las opiniones de otros clientes
            <strong>para</strong> tener una idea de la calidad del trabajo del remodelador.  
            </td>
            <!-- Criterios de Aceptación -->
            <td> 
            <h5>Escenario 01: </h5>
            <strong>Dado</strong> que el visitante del segmento contratista se encuentra el perfil de un remodelador en la plataforma de ReStyle
            <strong>Cuando</strong> accede a la sección de reviews
            <strong>Entonces</strong> el sistema le muestra todas las reviews hechas al remodelador escogido.
            <h5>Escenario 02: </h5>
            <strong>Dado</strong> que el visitante del segmento contratista se encuentra el perfil de un remodelador en la plataforma de ReStyle
            <strong>Cuando</strong> accede a la sección de reviews
            <strong>Y</strong> selecciona un review
            <strong>Entonces</strong> el sistema le redirige al portafolio del remodelador para ver los proyectos.
            </td>
            <td>EPIC-001 </td>
        </tr>
        <tr style="text-align:center">
            <td> US-009 </td>
            <td> Agregar críticas y opiniones </td>
           <!-- Descripción -->
            <td> 
            <strong>Como</strong> visitante del segmento contratista,
            <strong>quiero</strong> agregar un review
            <strong>para</strong> poder compartir mi experiencia con otros usuarios sobre el remodelador con el que realicé un proyecto.  
            </td>
            <!-- Criterios de Aceptación -->
            <td> 
            <h5>Escenario 01: </h5>
            <strong>Dado</strong> que el visitante del segmento contratista se encuentra en la plataforma de ReStyle
            <strong>Cuando</strong> accede a su perfil
            <strong>Y</strong> selecciona la opción agregar reseña 
            <strong>Entonces</strong> el sistema le muestra un formulario donde puede agregar la información correspondiente
            <strong>Cuando</strong> el usuario ingresa la información requerida
            <strong>Y</strong> selecciona guardar
            <strong>Entonces</strong> el sistema guarda la reseña y muestra un mensaje de éxito.
            <h5>Escenario 02: </h5>
            <strong>Dado</strong> que el visitante del segmento contratista se encuentra en la plataforma de ReStyle
            <strong>Cuando</strong> accede a su perfil
            <strong>Y</strong> selecciona la opción agregar reseña 
            <strong>Entonces</strong> el sistema le muestra un formulario donde puede agregar la información correspondiente
            <strong>Cuando</strong> el usuario ingresa la información requerida
            <strong>Y</strong> no selecciona guardar
            <strong>Entonces</strong> el sistema no guarda la reseña y no muestra un mensaje de éxito.
            </td>
            <td>EPIC-001 </td>
        </tr>
        <tr style="text-align:center">
            <td> US-010 </td>
            <td> Gestión de solicitudes al servidor </td>
           <!-- Descripción -->
            <td> 
            <strong>Como</strong> desarrollador,
            <strong>quiero</strong> asegurarme de que el API pueda gestionar múltiples solicitudes de varios dispositivos
            <strong>para</strong> que el sistema funcione sin interrupciones durante temporadas de alta demanda.  
            </td>
            <!-- Criterios de Aceptación -->
            <td> 
            <h5>Escenario 01: </h5>
            <strong>Dado</strong> que el desarrollador realiza las pruebas de carga en el API
            <strong>Cuando</strong> envía múltiples solicitudes simultáneas
            <strong>Entonces</strong> el tiempo de respuesta está dentro del rango promedio
            <strong>Y</strong> no existen errores o caídas del sistema. 
            <h5>Escenario 02: </h5>
            <strong>Dado</strong> que el desarrollador realiza las pruebas de carga en el API
            <strong>Cuando</strong> envía múltiples solicitudes simultáneas de distintos dispositivos
            <strong>Entonces</strong> el tiempo de respuesta está dentro del rango promedio
            <strong>Y</strong> no existen errores o caídas del sistema. 
            </td>
            <td>EPIC-003 </td>
        </tr>
        <tr style="text-align:center">
            <td> US-011 </td>
            <td> Autorización y seguridad de acceso al API </td>
           <!-- Descripción -->
            <td> 
            <strong>Como</strong> desarrollador,
            <strong>quiero</strong> poder configurar una autenticación y autorización segura en el API
            <strong>para</strong> garantizar que solos los usuarios admin puedan acceder al sistema.  
            </td>
            <!-- Criterios de Aceptación -->
            <td> 
            <h5>Escenario 01: </h5>
            <strong>Dado</strong> que un usuario con rol admin quiere ingresar al API
            <strong>Cuando</strong> proporciona sus credenciales
            <strong>Y</strong> estas son válidas 
            <strong>Entonces</strong> el sistema le permite ingresar. 
            <h5>Escenario 02: </h5>
            <strong>Dado</strong> que un usuario con rol admin quiere ingresar al API
            <strong>Cuando</strong> proporciona sus credenciales
            <strong>Y</strong> estas no son válidas
            <strong>Entonces</strong> el sistema no le permite ingresar 
            <strong>Y</strong> le notifica que tiene 2 intentos restantes para ingresar al sistema.
            <h5>Escenario 03: </h5>
            <strong>Dado</strong> que un usuario con un rol distinto a admin quiere ingresar al API
            <strong>Cuando</strong> proporciona sus credenciales
            <strong>Y</strong> estas no son válidas
            <strong>Y</strong> superó los intentos restantes
            <strong>Entonces</strong> el sistema no le permite ingresar
            <strong>Y</strong> notifica a los administradores sobre el intento de acceso.  
            </td>
            <td>EPIC-003 </td>
        </tr>
        <tr style="text-align:center">
            <td> US-012 </td>
            <td> Crear cuenta contratista</td>
            <td> 
              <strong>Como</strong> usuario contratista, 
              <strong>quiero</strong> poder crear una cuenta en ReStyle 
              <strong>para</strong> poder acceder al mercado qué provee</td>
            <td>
              <h5>Escenario 01: </h5> 
              <strong>Dado</strong> que el usuario contratista se encuentra la pantalla inicial de ReStyle , 
              <strong>Cuando</strong> le de click al boton de Crear cuenta, 
              <strong>Entonces</strong> le aparecera la pantalla de Creacion de Cuenta Nueva. 
              <h5>Escenario 02:</h5>
              <strong>Dado</strong> que el usuario contratista se encuentra en la pantalla de Creacion de Cuenta nueva, 
              <strong>Cuando</strong> llene los datos solicitados 
              <strong>Y</strong> le de Click al Boton Aceptar 
              <strong>Entonces</strong> le aparecera la pantalla de Iniciar Sesion. 
              <h5>Escenario 03:</h5> 
              <strong>Dado</strong> que el usuario contratista se encuentra en la pantalla de Creacion de Cuenta Nueva 
              <strong>Y</strong> no haya llenado los datos solicitados, 
              <strong>Cuando</strong> le de click al boton Aceptar, 
              <strong>Entonces</strong> le aparecera un mensaje de error. </td>
            <td> EPIC-002</td>
        </tr>
        <tr style="text-align:center">
            <td> US-013 </td>
            <td> Crear cuenta remodelador</td>
            <td> 
              <strong>Como</strong> usuario remodelador, 
              <strong>quiero</strong> poder crear una cuenta en ReStyle 
              <strong>para</strong> poder promocionar mis servicios</td>
            <td>
              <h5>Escenario 01: </h5> 
              <strong>Dado</strong> que el usuario remodelador se encuentra la pantalla inicial de ReStyle , 
              <strong>Cuando</strong> le de click al boton de Crear cuenta, 
              <strong>Entonces</strong> le aparecera la pantalla de Creacion de Cuenta Nueva. 
              <h5>Escenario 02:</h5>
              <strong>Dado</strong> que el usuario remodelador se encuentra en la pantalla de Creacion de Cuenta nueva, 
              <strong>Cuando</strong> llene los datos solicitados 
              <strong>Y</strong> le de Click al Boton Aceptar 
              <strong>Entonces</strong> le aparecera la pantalla de Iniciar Sesion. 
              <h5>Escenario 03:</h5> 
              <strong>Dado</strong> que el usuario remodelador se encuentra en la pantalla de Creacion de Cuenta Nueva 
              <strong>Y</strong> no haya llenado los datos solicitados, 
              <strong>Cuando</strong> le de click al boton Aceptar, 
              <strong>Entonces</strong> le aparecera un mensaje de error. </td>
            <td> EPIC-002</td>
        </tr>
        <tr style="text-align:center">
            <td> US-014 </td>
            <td>Busqueda portafolios</td>
            <td> 
              <strong>Como</strong> usuario contratista, 
              <strong>quiero</strong> poder buscar proyectos hechos por remodeladores 
              <strong>para</strong> saber qué el remodelador con el qué trabajo puede hacer el proyecto qué me interesa</td>
            <td> 
              <h5>Escenario 01: </h5>
              <strong>Dado</strong> que el usuario contratista se encuentra en la pantalla de busqueda,
              <strong>Cuando</strong> selecciona la opcion portafolios
              <strong>Entonces</strong> el sistema mostrara todos los proyectos realizados por el remodelador. 
              <h5>Escenario 02: </h5>
              <strong>Dado</strong> que el usuario contratista se encuentra en el apartado de portafolios,
              <strong>Cuando</strong> selecciona un portafolio
              <strong>Entonces</strong> el sistema le redirige al perfil del remodelador que es dueño del portafolio.
            <td>EPIC-001</td>
        </tr>
        <tr style="text-align:center">
            <td> US-015 </td>
            <td>Seguimiento de proyecto</td>
            <td> 
              <strong>Como</strong> usuario remodelador, 
              <strong>quiero</strong> poder ver los hitos del seguimiento mi proyecto 
              <strong>para</strong> saber en qué estado y etapa se encuentra el proyecto de diseño</td>
            <td> 
              <h5>Escenario 01: </h5>
              <strong>Dado</strong> que el usuario remodelador se encuentra en la plataforma de reStyle,
              <strong>Cuando</strong> selecciona el apartado de mis proyectos
              <strong>Entonces</strong> el sistema le mostrará todos los hitos del proyecto. 
              <h5>Escenario 02: </h5>
              <strong>Dado</strong> que el usuario remodelador se encuentra en el apartado de mis proyectos,
              <strong>Cuando</strong> selecciona cumplir un hito
              <strong>Entonces</strong> el sistema le permite continuar al siguiente en la línea de tiempo. 
              <h5>Escenario 03: </h5>
              <strong>Dado</strong> que el usuario remodelador se encuentra en el apartado de mis proyectos,
              <strong>Cuando</strong> todos los hitos han sido culminados
              <strong>Entonces</strong> el sistema le permite guardar el proyecto como culminado. 
            <td>EPIC-006</td>
        </tr>
        <tr style="text-align:center">
            <td> US-016 </td>
            <td>Programar Consulta con un Remodelador</td>
            <td>
            <strong>Como</strong> propietario de vivienda interesado en remodelar, quiero poder programar uan consulta con un remodelador a través de la plataforma <strong>para</strong> discutir mis necesidades y obtener recomendaciones.
            </td>
            <td>
            <h5>Esceneario 1:</h5>
            <strong>Dado</strong> que soy un propietario de vivienda registrado en la plataforma, <strong>Cuando</strong> accedo al perfil de un remodelador. <strong>Entonces</strong> tengo la opción de contactarme con la empresa dejandole mis datos personales.
            <h5>Escenario 2:</h5>
            <strong>Dado</strong> que me he contactado con un remodelador, <strong>Cuando</strong> se confirma el mensaje. <strong>Entonces</strong> recibo una notificación por correo electrónico y/o mensaje en la plataforma confirmando la consulta.
            </td>
            <td>EPIC-001 </td>
        </tr>
        <tr style="text-align:center">
            <td> US-017 </td>
            <td>Visualizar home de la plataforma</td>
            <td>
            <strong>Como</strong> usuario de reStyle deseo poder acceder a un home de la aplicación<strong>para</strong> poder visualizar las opciones disponibles para mi rol.
            </td>
            <td>
            <h5>Esceneario 1:</h5>
            <strong>Dado</strong> que soy un propietario de vivienda registrado en la plataforma, <strong>Cuando</strong> accedo a la sección de inicio <strong>Entonces</strong> el sistema me redirige al home de la aplicación.
            <h5>Esceneario 2:</h5>
            <strong>Dado</strong> que soy un remodelador registrado en la plataforma, <strong>Cuando</strong> accedo a la sección de inicio <strong>Entonces</strong> el sistema me redirige al home de la aplicación.
            </td>
            <td>EPIC-002 </td>
        </tr>
        <tr style="text-align:center">
            <td> US-018 </td>
            <td>Visualizar una página no encontrada</td>
            <td>
            <strong>Como</strong> usuario de reStyle deseo saber qué páginas no están a mi alcance<strong>para</strong> poder visualizar las opciones disponibles para mi rol.
            </td>
            <td>
            <h5>Esceneario 1:</h5>
            <strong>Dado</strong> que soy un propietario de vivienda registrado en la plataforma, <strong>Cuando</strong> ingreso una ruta al azar en el buscador de mi navegador <strong>Entonces</strong> la aplicación me redirige a una página no encontrada.
            <h5>Esceneario 2:</h5>
            <strong>Dado</strong> que soy un remodelador registrado en la plataforma, <strong>Cuando</strong> ingreso una ruta al azar en el buscador de mi navegador <strong>Entonces</strong> la aplicación me redirige a una página no encontrada.
            </td>
            <td>EPIC-002 </td>
        </tr>
        <tr style="text-align:center">
            <td>US-019</td>
            <td>Cambiar idioma</td>
            <!-- Descripción -->
            <td>
            <strong>Como</strong> visitante del landing page, 
            <strong>quiero</strong> acceder a una versión en otro idioma, 
            <strong>para</strong> poder entender mejor la información y navegar con mayor facilidad.
            </td>
            <!-- Criterios de Aceptación -->
            <td> 
            <h5>Escenario 1: Información desplegada en español</h5>
            <strong>Dado</strong> que el usuario quiere acceder al contenido de la landing page en español
            <strong>Cuando</strong> el usuario presione el botón switch para cambiar idioma.
            <strong>Entonces</strong> La información será traducida 
            <strong>Y</strong> el contenido se presentará en el idioma elegido por el usuario.
            <h5>Escenario 2: Información desplegada en inglés </h5>
            <strong>Dado</strong> que el usuario quiere acceder al contenido de la landing page en inglés
            <strong>Cuando</strong> el usuario presione el botón switch para cambiar idioma.
            <strong>Entonces</strong> La información será traducida 
            <strong>Y</strong> el contenido se presentará en el idioma elegido por el usuario.
            </td>
            <td> EPIC-004</td>
        </tr>
         <tr style="text-align:center">
            <td>US-020</td>
            <td>Visualizar testimonios de los usuarios que han utilizado la aplicación </td>
            <!-- Descripción -->
            <td>
            <strong>Como</strong> usuario visitante de la landing page, 
            <strong>quiero</strong> saber la opinión de los usuarios que han utilizado la aplicación
            <strong>para</strong> tener una referencia de la experiencia de estos usuarios con el producto.
            </td>
            <!-- Criterios de Aceptación -->
            <td> 
            <h5>Escenario 1: Testimonios sobre los contratistas</h5>
            <strong>Dado</strong> que el usuario quiere conocer la opinión de los contratistas sobre la plataforma
            <strong>Cuando</strong> el usuario lea las reseñas de valoración
            <strong>Entonces</strong> podrá evaluar según los comentarios
            <strong>Y</strong> decidirá la posibilidad de uso de la aplicación.
            <h5>Escenario 2: Testimonio sobre los remodeladores </h5>
            <strong>Dado</strong> que el usuario quiere conocer la opinión de los remodeladores sobre la plataforma
            <strong>Cuando</strong> el usuario lea las reseñas de valoración
            <strong>Entonces</strong> podrá evaluar según los comentarios
            <strong>Y</strong> decidirá la posibilidad de uso de la aplicación.
            </td>
            <td> EPIC-004</td>
        </tr> 
        <tr style="text-align:center">
            <td>US-021</td>
            <td>Visualizar formulario de contacto </td>
            <!-- Descripción -->
            <td>
            <strong>Como</strong> usuario visitante de la landing page, 
            <strong>quiero</strong> contar con opciones de contacto con la startup
            <strong>para</strong> preguntar más información sobre el producto o servicio.
            </td>
            <!-- Criterios de Aceptación -->
            <td> 
            <h5>Escenario 1: Envío de mensaje exitoso</h5>
            <strong>Dado</strong> que el usuario se encuentra en la sección de contacto
            <strong>Cuando</strong> ingresa correctamente los datos solicitados en el formulario
            <strong>Entonces</strong> el mensaje es enviado con éxito
            <strong>Y</strong> se registrará su consulta
            <h5>Escenario 2: Error en envío de mensaje</h5>
            <strong>Dado</strong> que el usuario se encuentra en la sección de contacto
            <strong>Cuando</strong> el usuario ingresa los datos solicitados en el formulario de forma incorrecto o inconclusa
            <strong>Entonces</strong> su mensajé no será enviado
            </td>
            <td> EPIC-004</td>
        </tr> 
        <tr style="text-align:center">
            <td>US-022</td>
            <td>Integración de Validators en Formularios de la App Web</td>
            <!-- Descripción -->
            <td>
            <strong>Como</strong> usuario de ReStyle, 
            <strong>quiero</strong> que los formularios en la app web tengan validadores integrados
            <strong>para</strong> pasegurar la integridad de los datos que ingreso.
            </td>
            <!-- Criterios de Aceptación -->
            <td> 
            <h5>Escenario 1: Validar campos requeridos</h5>
            <strong>Dado</strong> que estoy en cualquier formulario de la web app
            <strong>Cuando</strong> iintento enviar el formulario sin completar campos requeridos
            <strong>Entonces</strong> debo ver un mensaje de error que indique los campos que necesitan ser completados
            <strong>Y</strong> los datos del formulario se tienen que eliminar para un nuevo regisro
            <h5>Escenario 2: Enviar formulario correctamente</h5>
            <strong>Dado</strong> que estoy en cualquier formulario de la web app
            <strong>Cuando</strong> ingreso datos válidos en todos los campos
            <strong>Entonces</strong> debo poder enviar el formulario correctamente
            <strong>Y</strong> el sistema muestra un mensaje de éxito
            </td>
            <td> EPIC-004</td>
        </tr>
        <tr style="text-align:center">
        <td>US-023</td>
        <td>Interacción básica con el chatbot en app web</td>
        <td>
            <strong>Como</strong> usuario de ReStyle, 
            <strong>quiero</strong> poder hacer preguntas básicas al chatbot 
            <strong>para</strong> obtener respuestas rápidas sobre el uso de la plataforma.
        </td>
        <td> 
            <h5>Escenario 1: Chatbot responde pregunta frecuente</h5>
            <strong>Dado</strong> que he abierto el chatbot en la app web<br>
            <strong>Cuando</strong> escribo "¿Cómo cambio mi contraseña?"<br>
            <strong>Entonces</strong> el chatbot me responde con los pasos para cambiar la contraseña<br>
            <strong>Y</strong> la respuesta aparece en menos de 3 segundos<br>
            <h5>Escenario 2: Chatbot no entonde la pregunta</h5>
            <strong>Dado</strong> que he hecho una pregunta muy específica o compleja<br>
            <strong>Cuando</strong> el chatbot no puede entender mi intención<br>
            <strong>Entonces</strong> me sugiere reformular la pregunta<br>
            <strong>Y</strong> me ofrece la opción de contactar con un agente humano
        </td>
        <td>EPIC-008</td>
    </tr>
    <tr style="text-align:center">
        <td>US-024</td>
        <td>Consulta de presupuestos estimados vía chatbot</td>
        <td>
            <strong>Como</strong> usuario contratista de ReStyle, 
            <strong>quiero</strong> consultar al chatbot un estimado de presupuesto para mi proyecto 
            <strong>para</strong> tener una idea inicial de costos.
        </td>
        <td> 
            <h5>Escenario 1: Solicitud de presupuesto básico</h5>
            <strong>Dado</strong> que he iniciado una conversación con el chatbot<br>
            <strong>Cuando</strong> selecciono la opción "Calcular presupuesto"<br>
            <strong>Entonces</strong> el chatbot me pregunta por el tipo de remodelación, metros cuadrados y ubicación<br>
            <strong>Y</strong> al proporcionar los datos, recibo un rango de precios estimado<br>
            <h5>Escenario 2: Proyecto complejo</h5>
            <strong>Dado</strong> que mi proyecto requiere múltiples servicios<br>
            <strong>Cuando</strong> el chatbot detecta alta complejidad<br>
            <strong>Entonces</strong> me sugiere contactar con un remodelador para una cotización precisa<br>
            <strong>Y</strong> me ofrece agendar una cita
        </td>
        <td>EPIC-008</td>
    </tr>
    <tr style="text-align:center">
        <td>US-025</td>
        <td>Derivación a soporte humano desde chatbot</td>
        <td>
            <strong>Como</strong> usuario de ReStyle, 
            <strong>quiero</strong> que el chatbot me derive a un agente humano cuando no pueda resolver mi consulta 
            <strong>para</strong> no quedarme bloqueado.
        </td>
        <td> 
            <h5>Escenario 1: Derivación exitosa</h5>
            <strong>Dado</strong> que el chatbot no puede responder mi pregunta después de 2 intentos<br>
            <strong>Cuando</strong> selecciono "Hablar con agente"<br>
            <strong>Entonces</strong> el chatbot recopila el historial de la conversación<br>
            <strong>Y</strong> me conecta con un agente humano junto con el contexto<br>
            <h5>Escenario 2: Agente no disponible</h5>
            <strong>Dado</strong> que solicito hablar con un agente fuera del horario de atención<br>
            <strong>Cuando</strong> no hay agentes disponibles<br>
            <strong>Entonces</strong> el chatbot me ofrece dejar un mensaje<br>
            <strong>Y</strong> me promete una respuesta en menos de 24 horas
        </td>
        <td>EPIC-008</td>
    </tr>   
        <tr style="text-align:center">
            <td> TS001 </td>
            <td> Obtener Usuarios </td>
            <td> 
            <strong> Como </strong> desarrollador backend en reStyle,
            <strong> quiero </strong> obtener la información de los usuarios remodeladores y contratistas a través de una API <strong> para </strong> permitir al equipo de frontend utilizar los datos del usuario en la interfaz. </td>
            <td> 
            <h5>Escenario 01: Obtener Usuarios Exitosamente</h5>
            <strong> Dado </strong> que tengo autorización en el uso de la API y al endpoint de Usuarios,
            <strong> Cuando </strong> envío una solicitud GET para la obtención de datos del usuario, <strong> Entonces </strong>  el servidor responde con un código de estado 200 OK <strong> Y </strong> recibo la información de los usuarios en un response de formato JSON que contiene al menos un usuario con los siguientes campos: <br> 
            - Id: {ID del usuario}<br>
            - Email: {Email del usuario}<br>
            - Password: {Contraseña del usuario}<br>
            - Type: {Segmento objetivo del usuario}<br>
            - First name: {Nombre del usuario}<br>
            - Paternal Surname: {Apellido paterno del usuario}<br>
            - Maternal Surname: {Apellido materno del usuario}<br>
            - Image: {Foto del usuario}<br>
            <h5>Escenario 02: Obtener Usuarios con Parámetro Erróneo</h5>            
            <strong> Dado </strong> que tengo autorización en el uso de la API y al endpoint de Usuarios,
            <strong> Cuando </strong>envío una solicitud GET para la obtención de datos del usuario con un parámetro erróneo o inexistente,
            <strong> Entonces </strong> 
            el servidor responde con un código de estado 400 Bad Request <strong> Y </strong> recibo un mensaje de error en el response indicando que el parámetro es incorrecto o no existe.
            </td>
            <td> </td>
        </tr>
        <tr style="text-align:center">
            <td> TS002 </td>
            <td> Obtener Remodeladores</td>
            <td> 
                <strong> Como </strong> desarrollador backend en reStyle,
                <strong> quiero </strong> obtener la información de los remodeladores a través de una API
                <strong> para </strong> permitir al equipo de frontend utilizar los datos del remodelador en la interfaz de usuario.
            </td>
            <td> 
                <h5> Escenario 01:  Obtener Remodeladores </h5>
                <strong> Dado </strong> qque tengo autorización en el uso de la API y al endpoint de Remodeladores,
                <strong> Cuando </strong> envío una solicitud GET para la obtención de datos del remodelador,
                <strong> Entonces </strong>  el servidor responde con un código de estado 200 OK
                <strong>Y</strong> recibo la información del remodelador en un response de formato JSON que contiene los siguientes campos:<br>
                - ID: {ID del remodelador}<br>
                - User Id: {Id de usuario del remodelador}<br>
                - Phone: {Numero de telefono del remodelador}<br>
                - Description: {Descripción del remodelador}<br>
                - Subscription: {Subscripción del remodelador}<br>
                - Business Id: {Id de la empresa del remodelador}<br>
                <h5> Escenario 02: Obtener Remodeladores con Parámetro de ID</h5>            
                <strong> Dado </strong> que tengo autorización en el uso de la API y al endpoint de Remodeladores by ID,
                <strong> Cuando </strong> envío una solicitud GET para la obtención de datos del remodelador con un parámetro de ID correcto,
                <strong> Entonces </strong> 
                el servidor responde con un código de estado 200 OK
                <strong> Y </strong> recibo la información del remodelador correspondiente en un response de formato JSON.
                <h5> Escenario 03: Obtener Remodeladores con Parámetro de ID Erróneo o inexistente</h5>            
                <strong> Dado </strong> que tengo autorización en el uso de la API y al endpoint de Remodeladores by ID,
                <strong> Cuando </strong> envío una solicitud GET para la obtención de datos del remodelador con un parámetro de ID erróneo o inexistente,
                <strong> Entonces </strong> 
                el servidor responde con un código de estado 400 Bad Request
                <strong> Y </strong> recibo un mensaje de error en el response indicando que el parámetro de ID es incorrecto o no existe.
            </td>
            <td> </td>
        </tr>
        <tr style="text-align:center">
            <td> TS003 </td>
            <td>  Obtener Contratistas </td>
            <td> 
                <strong> Como </strong> desarrollador backend en reStyle,
                <strong> quiero </strong> obtener los datos de los contratistas a través de una API
                <strong> para </strong> permitir al equipo de frontend utilizar los datos del contratista y mostrarlo a los usuarios  
            </td>
            <td> 
                <h5> Escenario 02: Obtener Datos de los contratistas</h5>
                <strong> Dado </strong> que tengo autorización en el uso de la API y al endpoint de Contratistas,
                <strong> Cuando </strong> envío una solicitud GET para la obtención de datos del contratista,
                <strong> Entonces </strong>  el servidor responde con un código de estado 200 OK <strong> Y </strong> recibo la información de los Contratistas actuales en un response de formato JSON que contiene los siguientes campos:<br>
                - ID: {ID del contratista}<br>
                - User Id: {Id de usuario del contratista}<br>
                - Phone: {Numero de telefono del contratista}<br>
                - Description: {Descripción del contratista}<br>
                <h5> Escenario 02: Obtener Datos del contratista Exitosamente por ID </h5>
                <strong> Dado </strong> que tengo autorización en el uso de la API y al endpoint de Contratistas by ID,
                <strong> Cuando </strong> envío una solicitud GET para la obtención de datos del contratista por su ID,
                <strong> Entonces </strong>  el servidor responde con un código de estado 200 OK <strong> Y </strong> recibo la información del contratista actual en un response de formato JSON.<br>
                <h5> Escenario 03: Obtener Datos del contratista con Parámetro de ID Erróneo</h5>            
                <strong> Dado </strong> que tengo autorización en el uso de la API y al endpoint de Contratistas by ID,
                <strong> Cuando </strong> envío una solicitud GET para la obtención de datos del contratista con un parámetro de ID erróneo o inexistente,
                <strong> Entonces </strong> el servidor responde con un código de estado 400 Bad Request
                <strong> Y </strong> recibo un mensaje de error en el response indicando que el parámetro de ID es incorrecto o no existe.
            </td>
            <td> </td>
        </tr>
          <tr style="text-align:center">
            <td> TS004 </td>
            <td>  Obtener Empresas </td>
            <td> 
                <strong> Como </strong> desarrollador backend en reStyle,
                <strong> quiero </strong> obtener los datos de las Empresas a través de una API
                <strong> para </strong> permitir al equipo de frontend utilizar los datos de la empresa y mostrarlo a los usuarios  
            </td>
            <td> 
                <h5> Escenario 02: Obtener Datos de las Empresas</h5>
                <strong> Dado </strong> que tengo autorización en el uso de la API y al endpoint de Empresas,
                <strong> Cuando </strong> envío una solicitud GET para la obtención de datos de la empresa,
                <strong> Entonces </strong>  el servidor responde con un código de estado 200 OK <strong> Y </strong> recibo la información de las Empresas actuales en un response de formato JSON que contiene los siguientes campos:<br>
                - ID: {ID de la empresa}<br>
                - Remodeler Id: {Id de remodeler de la empresa}<br>
                - Expertise: {Expertise de la empresa}<br>
                - Address: {Direccion de la empresa}<br>
                - City: {Ciudad donde se ubica la empresa}<br>
                - Name: {Nombre de la empresa}<br>
                - Image: {Foto de la empresa}<br>
                - Description: {Descripción de la empresa}<br>
                <h5> Escenario 02: Obtener Datos de la empresa Exitosamente por ID </h5>
                <strong> Dado </strong> que tengo autorización en el uso de la API y al endpoint de Empresas by ID,
                <strong> Cuando </strong> envío una solicitud GET para la obtención de datos de la empresa por su ID,
                <strong> Entonces </strong>  el servidor responde con un código de estado 200 OK <strong> Y </strong> recibo la información de la empresa actual en un response de formato JSON.<br>
                <h5> Escenario 03: Obtener Datos de la empresa con Parámetro de ID Erróneo</h5>            
                <strong> Dado </strong> que tengo autorización en el uso de la API y al endpoint de Empresas by ID,
                <strong> Cuando </strong> envío una solicitud GET para la obtención de datos de la empresa con un parámetro de ID erróneo o inexistente,
                <strong> Entonces </strong> el servidor responde con un código de estado 400 Bad Request
                <strong> Y </strong> recibo un mensaje de error en el response indicando que el parámetro de ID es incorrecto o no existe.
            </td>
            <td> </td>
        </tr>
        <tr style="text-align:center">
            <td> TS005 </td>
            <td>  Obtener Proyectos </td>
            <td> 
                <strong> Como </strong> desarrollador backend en reStyle,
                <strong> quiero </strong> obtener los datos de los Proyectos a través de una API
                <strong> para </strong> permitir al equipo de frontend utilizar los datos del proyecto y mostrarlo a los usuarios  
            </td>
            <td> 
                <h5> Escenario 02: Obtener Datos de las Proyectos</h5>
                <strong> Dado </strong> que tengo autorización en el uso de la API y al endpoint de Proyectos,
                <strong> Cuando </strong> envío una solicitud GET para la obtención de datos del proyecto,
                <strong> Entonces </strong>  el servidor responde con un código de estado 200 OK <strong> Y </strong> recibo la información de los Proyectos actuales en un response de formato JSON que contiene los siguientes campos:<br>
                - ID: {ID del proyecto}<br>
                - Business Id: {Id de empresa que realiza el proyecto}<br>
                - Contractor Id: {Id del contratista que solicito el proyecto}<br>
                - Start Date: {Fecha de inicio del proyecto}<br>
                - Finish Date: {Fecha de fin del proyecto}<br>
                - Name: {Nombre del proyecto}<br>
                - Image: {Foto del proyecto}<br>
                - Description: {Descripción del proyecto}<br>
                <h5> Escenario 02: Obtener Datos del proyecto Exitosamente por ID </h5>
                <strong> Dado </strong> que tengo autorización en el uso de la API y al endpoint de Proyectos by ID,
                <strong> Cuando </strong> envío una solicitud GET para la obtención de datos del proyecto por su ID,
                <strong> Entonces </strong>  el servidor responde con un código de estado 200 OK <strong> Y </strong> recibo la información del proyecto actual en un response de formato JSON.<br>
                <h5> Escenario 03: Obtener Datos del proyecto con Parámetro de ID Erróneo</h5>            
                <strong> Dado </strong> que tengo autorización en el uso de la API y al endpoint de Proyectos by ID,
                <strong> Cuando </strong> envío una solicitud GET para la obtención de datos del proyecto con un parámetro de ID erróneo o inexistente,
                <strong> Entonces </strong> el servidor responde con un código de estado 400 Bad Request
                <strong> Y </strong> recibo un mensaje de error en el response indicando que el parámetro de ID es incorrecto o no existe.
        </tr>
        <tr style="text-align:center">
            <td> TS006 </td>
            <td> Obtener Reviews </td>
            <td> 
                <strong>Como</strong> desarrollador backend en reStyle,
                <strong>Quiero</strong> obtener la información del portafolio de las reseñas creadas por los contratistas a través de una API
                <strong>Para</strong> permitir al equipo de frontend utilizar los datos de la reseña.
            </td>
            <td> 
                <h5>Escenario 01: Obtener Reseñas Exitosamente</h5>
                <strong>Dado</strong> que tengo autorización en el uso de la API y al endpoint de Reviews,
                <strong>Cuando</strong> envío una solicitud GET para la obtención de datos de las reseñas de los usuarios,
                <strong>Entonces</strong> el servidor responde con un código de estado 200 OK
                <strong>Y</strong> recibo la información de las reseñas en un response de formato JSON que contiene al menos una reseña con los siguientes campos:<br>
                - ID: {ID de la reseña}<br>
                - Contractor Id: {Id del contratista que creó la reseña}<br>
                - Project Id: {Id del proyecto del que se creó la reseña}<br>
                - Comment: {Contenido de la reseña}<br>
                - Image: {Foto de la reseña}<br>
                - Duration: {Duracion del proyecto}<br>
                - Rating: {Puntuación de la reseña}<br>
                <h5>Escenario 02: Obtener Reseñas con Parámetro Erróneo</h5>
                <strong>Dado</strong> que tengo autorización en el uso de la API y al endpoint de Reviews,
                <strong>Cuando</strong> envío una solicitud GET para la obtención de datos de las reseñas de los usuarios con un parámetro erróneo o inexistente,
                <strong>Entonces</strong> el servidor responde con un código de estado 400 Bad Request
                <strong>Y</strong> recibo un mensaje de error en la solicitud indicando que el parámetro es incorrecto o no existe.
            </td>
            <td> </td>
        </tr>
      <tr style="text-align:center">
            <td> TS007 </td>
            <td> Obtener Projects Requests </td>
            <td> 
                <strong>Como</strong> desarrollador backend en reStyle,
                <strong>Quiero</strong> obtener la información de los Projects Requests creados por los contratistas a través de una API
                <strong>Para</strong> permitir al equipo de frontend utilizar los datos del mismo.
            </td>
            <td> 
                <h5>Escenario 01: Obtener Projects Request Exitosamente</h5>
                <strong>Dado</strong> que tengo autorización en el uso de la API y al endpoint de Projects Request,
                <strong>Cuando</strong> envío una solicitud GET para la obtención de datos de los Projects Request,
                <strong>Entonces</strong> el servidor responde con un código de estado 200 OK
                <strong>Y</strong> recibo la información de los Projects Request en un response de formato JSON que contiene al menos una solicitud con los siguientes campos:<br>
                - ID: {ID de la solicitud}<br>
                - Contractor Id: {Id del contratista que creó la solicitud}<br>
                - Business Id: {Id de la empresa a la que se le solicita el proyecto}<br>
                - Name: {Nombre del contratista}<br>
                - Surname: {Apellido del contratista}<br>
                - Email: {Email del contratista}<br>
                - Phone: {Telefono del contratista}<br>
                - Address: {Direccion del contratista}<br>
                - City: {Ciudad donde reside el contratista}<br>
                - Deadline Date: {Fecha para la que se necesita el proyecto}<br>
                - Budget: {Presupuesto para el proyecto}<br>
                - Rooms: {Numero de cuartos para el proyecto}<br>
                - Summary: {Descripcion de la solicitud para el proyecto}<br>
                <h5> Escenario 02: Obtener Projects Request Exitosamente por ID </h5>
                <strong> Dado </strong> que tengo autorización en el uso de la API y al endpoint de  Projects Request by ID,
                <strong> Cuando </strong> envío una solicitud GET para la obtención de datos del Project Request por su ID,
                <strong> Entonces </strong>  el servidor responde con un código de estado 200 OK <strong> Y </strong> recibo la información del Project Request actual en un response de formato JSON.<br>
                <h5>Escenario 03: Obtener Projects Request por ID con Parámetro Erróneo </h5>
                <strong>Dado</strong> que tengo autorización en el uso de la API y al endpoint de Projects Request by ID,
                <strong>Cuando</strong> envío una solicitud GET para la obtención de datos del Project Request con un ID de parámetro erróneo o inexistente,
                <strong>Entonces</strong> el servidor responde con un código de estado 400 Bad Request
                <strong>Y</strong> recibo un mensaje de error en la solicitud indicando que el ID de parámetro es incorrecto o no existe.
            </td>
            <td> </td>
        </tr>
           <tr style="text-align:center">
            <td> TS008 </td>
            <td> Obtener Tracking </td>
            <td> 
                <strong>Como</strong> desarrollador backend en reStyle,
                <strong>Quiero</strong> obtener la información de Tracking creados por los remodeladores a través de una API
                <strong>Para</strong> permitir al equipo de frontend utilizar los datos del mismo.
            </td>
            <td> 
                <h5>Escenario 01: Obtener Tracking Exitosamente</h5>
                <strong>Dado</strong> que tengo autorización en el uso de la API y al endpoint de Tracking,
                <strong>Cuando</strong> envío una solicitud GET para la obtención de datos de Tracking,
                <strong>Entonces</strong> el servidor responde con un código de estado 200 OK
                <strong>Y</strong> recibo la información del Tracking en un response de formato JSON que contiene al menos un Tracking con los siguientes campos:<br>
                - ID: {ID de Trackingd}<br>
                - Contractor Id: {Id del contratista}<br>
                - Remodeler Id: {Id del remodelador que realizo el proyecto}<br>
                - Requirements: {
                  - Job Title: {Nombre de la tarea}<br>
                  - Job Description: {Descripcion de la tarea}<br>
                  - Job Requirements: {Requerimientos de la tarea}<br>
                  - Accepted: {Estado de finalizacion la tarea}<br>
                }<br>
                - Technical Visit: {
                  - Price: {Precio de la visita tecnica}<br>
                  - Date: {Fecha de la visita tecnica}<br>
                  - Additional Details: {Detalles de la visita tecnica}<br>
                }<br>
                - Quote: [{
                  - Price: {Precio de la cotizacion}<br>
                  - Description: {Descripcion de la cotizacion}<br>
                  - Details: {Detalles de la cotizacion}<br>
                }]<br>
                - Project Approval: {Aprobacion del proyecto}<br>
                <h5> Escenario 02: Obtener Tracking Exitosamente por ID </h5>
                <strong> Dado </strong> que tengo autorización en el uso de la API y al endpoint de Tracking by ID,
                <strong> Cuando </strong> envío una solicitud GET para la obtención de datos del Tracking por su ID,
                <strong> Entonces </strong>  el servidor responde con un código de estado 200 OK <strong> Y </strong> recibo la información del Tracking actual en un response de formato JSON.<br>
                <h5>Escenario 03: Obtener Tracking por ID con Parámetro Erróneo </h5>
                <strong>Dado</strong> que tengo autorización en el uso de la API y al endpoint de Tracking by ID,
                <strong>Cuando</strong> envío una solicitud GET para la obtención de datos del Tracking con un ID de parámetro erróneo o inexistente,
                <strong>Entonces</strong> el servidor responde con un código de estado 400 Bad Request
                <strong>Y</strong> recibo un mensaje de error en la solicitud indicando que el ID de parámetro es incorrecto o no existe.
            </td>
            <tr style="text-align:center">
        </tr>
        <tr style="text-align:center">
            <td>TS009</td>
            <td>Implementar API de integración del chatbot</td>
            <td> 
                <strong>Como</strong> desarrollador backend en reStyle,
                <strong>Quiero</strong> implementar una API RESTful para integrar el chatbot con la app web
                <strong>Para</strong> permitir el envío y recepción de mensajes en tiempo real.
            </td>
            <td> 
                <h5>Escenario 01: Envío de mensaje exitoso</h5>
                <strong>Dado</strong> que tengo autorización en el uso de la API y al endpoint de chatbot,
                <strong>Cuando</strong> envío una solicitud POST con un mensaje de usuario en formato JSON,
                <strong>Entonces</strong> el servidor responde con un código de estado 200 OK
                <strong>Y</strong> recibo la respuesta del chatbot en un response de formato JSON que contiene los siguientes campos:<br>
                - sessionId: {ID de la sesión de chat}<br>
                - messageId: {ID único del mensaje}<br>
                - timestamp: {Fecha y hora de la respuesta}<br>
                - response: {Texto de la respuesta del chatbot}<br>
                - intent: {Intención detectada del usuario}<br>
                - confidence: {Nivel de confianza de la respuesta}<br>
                <h5>Escenario 02: Envío de mensaje con error</h5>
                <strong>Dado</strong> que tengo autorización en el uso de la API y al endpoint de chatbot,
                <strong>Cuando</strong> envío una solicitud POST con un mensaje vacío o mal formado,
                <strong>Entonces</strong> el servidor responde con un código de estado 400 Bad Request
                <strong>Y</strong> recibo un mensaje de error indicando que el mensaje no puede ser procesado.<br>
                <h5>Escenario 03: Obtener historial de conversación</h5>
                <strong>Dado</strong> que tengo autorización en el uso de la API y al endpoint de historial de chatbot,
                <strong>Cuando</strong> envío una solicitud GET con el sessionId válido,
                <strong>Entonces</strong> el servidor responde con un código de estado 200 OK
                <strong>Y</strong> recibo el historial completo de la conversación en formato JSON.
            </td>
            <td>EPIC-008</td>
        </tr>
        <tr style="text-align:center">
            <td>TS010</td>
            <td>Implementar servicio de procesamiento de lenguaje natural</td>
            <td> 
                <strong>Como</strong> desarrollador backend en reStyle,
                <strong>Quiero</strong> implementar un servicio de NLP para el chatbot
                <strong>Para</strong> que pueda entender las intenciones del usuario y generar respuestas precisas.
            </td>
            <td> 
                <h5>Escenario 01: Procesamiento de intención exitoso</h5>
                <strong>Dado</strong> que el servicio de NLP está funcionando correctamente,
                <strong>Cuando</strong> recibe un mensaje del usuario con una intención clara (ej: "presupuesto para baño"),
                <strong>Entonces</strong> el servicio identifica la intención principal con al menos 85% de confianza
                <strong>Y</strong> extrae las entidades relevantes (tipo: "baño", acción: "presupuesto").<br>
                <h5>Escenario 02: Intención con baja confianza</h5>
                <strong>Dado</strong> que el servicio de NLP recibe un mensaje ambiguo o poco claro,
                <strong>Cuando</strong> el nivel de confianza es menor al 60%,
                <strong>Entonces</strong> el servicio devuelve un código de "intención_no_reconocida"
                <strong>Y</strong> sugiere al chatbot pedir clarificación al usuario.<br>
                <h5>Escenario 03: Entrenamiento del modelo</h5>
                <strong>Dado</strong> que se han recolectado nuevos datos de conversaciones,
                <strong>Cuando</strong> se ejecuta el proceso de re-entrenamiento del modelo,
                <strong>Entonces</strong> el servicio genera un nuevo modelo con métricas mejoradas
                <strong>Y</strong> se despliega automáticamente sin interrumpir el servicio.
            </td>
            <td>EPIC-008</td>
        </tr>
        <tr style="text-align:center">
            <td>TS011</td>
            <td>Implementar base de conocimientos para chatbot</td>
            <td> 
                <strong>Como</strong> desarrollador backend en reStyle,
                <strong>Quiero</strong> implementar una base de conocimientos para el chatbot
                <strong>Para</strong> que pueda acceder a información actualizada sobre servicios y preguntas frecuentes.
            </td>
            <td> 
                <h5>Escenario 01: Consulta exitosa a la base de conocimientos</h5>
                <strong>Dado</strong> que la base de conocimientos está poblada con al menos 50 preguntas frecuentes,
                <strong>Cuando</strong> el chatbot consulta por una pregunta común (ej: "¿Cómo cambio mi contraseña?"),
                <strong>Entonces</strong> el sistema devuelve la respuesta precisa en menos de 100ms
                <strong>Y</strong> incluye enlaces relevantes si son necesarios.<br>
                <h5>Escenario 02: Actualización de la base de conocimientos</h5>
                <strong>Dado</strong> que un administrador necesita agregar nueva información,
                <strong>Cuando</strong> se envía una solicitud PUT a la API de administración con datos válidos,
                <strong>Entonces</strong> el sistema actualiza la base de conocimientos
                <strong>Y</strong> la nueva información está disponible inmediatamente para el chatbot.<br>
                <h5>Escenario 03: Búsqueda sin resultados</h5>
                <strong>Dado</strong> que el usuario hace una pregunta muy específica no cubierta en la base,
                <strong>Cuando</strong> la consulta no devuelve resultados relevantes,
                <strong>Entonces</strong> el sistema registra la pregunta para revisión posterior
                <strong>Y</strong> sugiere derivar al usuario a soporte humano.
            </td>
            <td>EPIC-008</td>
        </tr>
        <tr style="text-align:center">
            <td>TS012</td>
            <td>Implementar integración con sistema de soporte humano</td>
            <td> 
                <strong>Como</strong> desarrollador backend en reStyle,
                <strong>Quiero</strong> implementar la integración entre el chatbot y el sistema de soporte humano
                <strong>Para</strong> permitir derivaciones fluidas cuando el chatbot no pueda resolver una consulta.
            </td>
            <td> 
                <h5>Escenario 01: Derivación exitosa a agente humano</h5>
                <strong>Dado</strong> que el chatbot detecta la necesidad de derivación,
                <strong>Cuando</strong> se inicia el proceso de transferencia a un agente humano,
                <strong>Entonces</strong> el sistema crea un ticket en el sistema de soporte
                <strong>Y</strong> transfiere el historial completo de la conversación al agente.<br>
                <h5>Escenario 02: Agente no disponible</h5>
                <strong>Dado</strong> que no hay agentes disponibles en el momento,
                <strong>Cuando</strong> se intenta una derivación,
                <strong>Entonces</strong> el sistema informa al usuario del tiempo estimado de espera
                <strong>Y</strong> ofrece la opción de ser contactado posteriormente por email.<br>
                <h5>Escenario 03: Recolección de información previa a la derivación</h5>
                <strong>Dado</strong> que se requiere información adicional antes de la derivación,
                <strong>Cuando</strong> el chatbot identifica que la consulta es compleja,
                <strong>Entonces</strong> solicita al usuario información de contacto y detalles específicos
                <strong>Y</strong> guarda esta información en el ticket de soporte.
            </td>
            <td>EPIC-008</td>
        </tr>
    </body>
</table>


## 3.3. Product Backlog

Utilizamos la escala de Fibonacci para la estimación de los Story Points.

<table>
        <thead>
            <tr>
                <th>Orden</th>
                <th>User Story Id</th>
                <th>Título</th>
                <th>Descripción</th>
                <th>Story Points (1/2/3/5/8)</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>1</td>
                <td>US-018</td>
                <td>Cambiar idioma</td>
                <td>Como visitante del landing page, quiero acceder a una versión en otro idioma, 
                    para poder entender mejor la información y navegar con mayor facilidad.</td>
                <td>5</td>
            </tr>
            <tr>
                <td>2</td>
                <td>US-001</td>
                <td>Hipervínculos en el encabezado</td>
                <td>Como visitante de la landing page, quiero que las opciones del encabezado me dirijan a las 
                diferentes secciones de la Landing Page para, poder navegar de forma rapida y fluida.</td>
                <td>1</td>
            </tr>
            <tr>
                <td>3</td>
                <td>US-005</td>
                <td>Información sobre el producto</td>
                <td> Como usuario que visita la landing page, quiero entender claramente qué ofrece el producto
                para poder tomar una decisión informada sobre si adquirirlo o no.</td>
                <td>2</td>
            </tr>
            <tr>
                <td>4</td>
                <td>US-002</td>
                <td>Información sobre beneficios de la aplicación</td>
                <td>Como usuario, quiero saber más sobre los beneficios de la aplicación web para considerar 
                ser miembro de la aplicacion.</td>
                <td>2</td>
            </tr>
            <tr>
                <td>5</td>
                <td>US-003</td>
                <td>Mostrar los planes disponibles</td>
                <td>Como visitante del landing page, quiero saber sobre los planes que tiene, para poder analizar 
                si el plan que me ofrecen se adecua a las necesidades de mi negocio.</td>
                <td>1</td>
            </tr>
            <tr>
                <td>6</td>
                <td>US-025</td>
                <td>Visualizar testimonios de los usuarios que han utilizado la aplicación</td>
                <td>Como usuario visitante de la landing page, quiero saber la opinión de los usuarios que han
                utilizado la aplicación para tener una referencia de la experiencia de estos usuarios con el producto.</td>
                <td>3</td>
            </tr>
            <tr>
                <td>7</td>
                <td>US-004</td>
                <td>Información útil en el footer</td>
                <td>Como usuario que visita la landing page, quiero encontrar información útil en el footer para
                poder contactarme con la empresa, conocer más sobre ella, leer sus políticas y seguirla en redes sociales.</td>
                <td>1</td>
            </tr>
            <tr>
                <td>8</td>
                <td>US-26</td>
                <td>Visualizar formulario de contacto</td>
                <td>Como usuario visitante de la landing page, quiero contar con opciones de contacto con la startup para preguntar más información sobre el producto o servicio.</td>
                <td>2</td>
            </tr>
            <tr>
                <td>9</td>
                <td>US-006</td>
                <td>Subir contenido a un portafolio</td>
                <td>Como usuario remodelador, quiero poder subir contenido multimedia a mi portafolio online para poder promocionar servicios y proyectos pasados a mis posibles clientes.</td>
                <td>5</td>
            </tr>
            <tr>
                <td>10</td>
                <td>US-007</td>
                <td>Búsqueda de empresas remodeladoras</td>
                <td>Como visitante del segmento contratista, quiero poder buscar remodeladoras por ubicación o expertise para obtener un resultado más personalizado.</td>
                <td>3</td>
            </tr>
            <tr>
                <td>11</td>
                <td>US-012</td>
                <td>Crear cuenta contratista</td>
                <td>Como usuario contratista, quiero poder crear una cuenta en ReStyle para poder acceder al mercado qué provee</td>
                <td>3</td>
            </tr>
            <tr>
                <td>12</td>
                <td>US-013</td>
                <td>Crear cuenta remodelador</td>
                <td>Como usuario remodelador, quiero poder crear una cuenta en ReStyle para poder acceder al mercado qué provee</td>
                <td>3</td>
            </tr>
            <tr>
                <td>13</td>
                <td>US-008</td>
                <td>Revisar críticas y opiniones</td>
                <td>Como visitante del segmento contratista, quiero ver las opiniones de otros clientes para tener una idea de la calidad del trabajo del remodelador.</td>
                <td>3</td>
            </tr>
            <tr>
                <td>14</td>
                <td>US-016</td>
                <td>Programar Consulta con un Remodelador</td>
                <td>Como propietario de vivienda interesado en remodelar, quiero poder programar uan consulta con un remodelador a través de la plataforma para discutir mis necesidades y obtener recomendaciones</td>
                <td>3</td>
            </tr>
            <tr>
                <td>15</td>
                <td>US-015</td>
                <td>Seguimiento de proyecto</td>
                <td>Como usuario remodelador, quiero poder ver los hitos del seguimiento mi proyecto para saber en qué estado y etapa se encuentra el proyecto de diseño.</td>
                <td>3</td>
            </tr>
            <tr>
                <td>16</td>
                <td>US-027</td>
                <td>Interacción básica con el chatbot en app web</td>
                <td>Como usuario de ReStyle, quiero poder hacer preguntas básicas al chatbot para obtener respuestas rápidas sobre el uso de la plataforma.</td>
                <td>5</td>
            </tr>
            <tr>
                <td>17</td>
                <td>US-028</td>
                <td>Consulta de presupuestos estimados vía chatbot</td>
                <td>Como usuario contratista de ReStyle, quiero consultar al chatbot un estimado de presupuesto para mi proyecto para tener una idea inicial de costos.</td>
                <td>8</td>
            </tr>
            <tr>
                <td>18</td>
                <td>US-029</td>
                <td>Derivación a soporte humano desde chatbot</td>
                <td>Como usuario de ReStyle, quiero que el chatbot me derive a un agente humano cuando no pueda resolver mi consulta para no quedarme bloqueado.</td>
                <td>3</td>
            </tr>
            <tr>
                <td>19</td>
                <td>US-10</td>
                <td>Gestión de solicitudes al servidor</td>
                <td>Como desarrollador, quiero asegurarme de que el API pueda gestionar múltiples solicitudes de varios dispositivos para que el sistema funcione sin interrupciones durante temporadas de alta demanda.</td>
                <td>5</td>
            </tr>
            <tr>
                <td>20</td>
                <td>US-11</td>
                <td>Autorización y seguridad de acceso al API</td>
                <td>Como desarrollador, quiero poder configurar una autenticación y autorización segura en el API para garantizar que solos los usuarios admin puedan acceder al sistema.</td>
                <td>3</td>
            </tr>
            <tr>
                <td>21</td>
                <td>US-009</td>
                <td>Establecer comunicación con remodeladores</td>
                <td>Como usuario contratista, quiero establecer comunicación efectiva con los remodeladores para poder expresar mis necesidades y recibir información actualizada sobre el proyecto.</td>
                <td>5</td>
            </tr>
            <tr>
                <td>22</td>
                <td>US-014</td>
                <td>Contratación de servicios de remodelación</td>
                <td>Como usuario contratista, quiero contratar servicios de remodelación de manera eficiente para asegurar que el proyecto se realice acorde a mi presupuesto y necesidades.</td>
                <td>8</td>
            </tr>
            <tr>
                <td>23</td>
                <td>US-017</td>
                <td>Gestión de portafolio</td>
                <td>Como usuario remodelador, quiero gestionar mi portafolio de proyectos de manera eficiente para poder compartir mi trabajo con contratistas interesados.</td>
                <td>5</td>
            </tr>
            <tr>
                <td>24</td>
                <td>US-019</td>
                <td>Gestión de proyecto</td>
                <td>Como usuario remodelador, quiero gestionar el proyecto encargado por un contratista para permitir el monitoreo de avances y cumplimiento de objetivos.</td>
                <td>8</td>
            </tr>
            <tr>
                <td>25</td>
                <td>US-020</td>
                <td>Gestión de suscripción</td>
                <td>Como usuario remodelador, quiero suscribirme a un plan de pago para acceder a beneficios exclusivos y mejorar mi experiencia en la aplicación.</td>
                <td>3</td>
            </tr>
            <tr>
                <td>26</td>
                <td>US-021</td>
                <td>Implementar API RESTful</td>
                <td>Como desarrollador, quiero implementar una API RESTful para poder acceder a los datos del sistema de forma segura.</td>
                <td>8</td>
            </tr>
            <tr>
                <td>27</td>
                <td>US-022</td>
                <td>Implementar Landing Page</td>
                <td>Como visitante, quiero acceder a una Landing Page con secciones informativas para tener un conocimiento claro de la aplicación.</td>
                <td>5</td>
            </tr>
        </tbody>
</table>

## 3.4. Impact Mapping
