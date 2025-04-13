# 

**Acerca de arc42**

arc42, La plantilla de documentación para arquitectura de sistemas y de
software.

Por Dr. Gernot Starke, Dr. Peter Hruschka y otros contribuyentes.

Revisión de la plantilla: 7.0 ES (basada en asciidoc), Enero 2017

© Reconocemos que este documento utiliza material de la plantilla de
arquitectura arc42, <https://www.arc42.org>. Creada por Dr. Peter
Hruschka y Dr. Gernot Starke.

# Introducción y Metas {#section-introduction-and-goals}

El propósito de Savio Mobile es mejorar la accesibilidad y experiencia de los estudiantes, docentes y administradores, para ofrecer un mejor entorno en el cual los estudiantes y docentes puedan tener una mejor comunicación mediante el fácil acceso a cursos, material de estudio y actividades académicas. Esto traza como objetivo la digitalización y modernización de la plataforma, además que busca dar una experiencia intuitiva y eficiente.  y que la Savio mobile sea escalable y segura. 

Actualmente, Savio opera con Moodle pero su diseño web no está adaptado para dispositivos móviles, la implementación de Moodle App permitirá la mejora significativa de la navegación. La aplicación móvil servirá como una extensión de Savio, asegurando la compatibilidad de las funcionalidades esenciales. y garantizar un manejo de datos adecuado y compatibilidad de módulos existentes. 



## Vista de Requerimientos {#_vista_de_requerimientos}

Nuestros requerimientos serían
REQ-1: La aplicación debe permitir la autenticación con el correo institucional de la UTB.

REQ-2: Se debe poder acceder a los cursos e interactuar con los recursos que estos tengan. TBD.

REQ-3: La aplicación podrá enviar notificaciones sobre las actividades pendientes con información descriptiva. TBD.

REQ-4: El usuario podrá subir archivos cuando lo requiera para completar actividades. TBD


## Metas de Calidad {#_metas_de_calidad}

Para el proyecto se tienen en mente las siguientes metas
- plataforma estable para android y ios
- una app segura y rapida
 
## Partes interesadas (Stakeholders) {#_partes_interesadas_stakeholders}

| Rol/Nombre                | Contacto          | Expectativas                 |
|---------------------------|-------------------|-----------------------------|
| Willy Jaime Laza Barrios  | wlaza@utb.edu.co | Conexión Moodle App y Savio |

# Restricciones de la Arquitectura {#section-architecture-constraints}

El desarrollo de Savio Mobile debe cumplir con las siguientes restricciones:

1. **Compatibilidad con Moodle**: La aplicación debe integrarse con la API de Moodle para garantizar el acceso a cursos, recursos y actividades.
2. **Plataformas soportadas**: La aplicación debe ser compatible con Android (mínimo Android 8.0) y iOS (mínimo iOS 13).
3. **Lenguajes y Frameworks**: Se debe desarrollar usando Angular/Javascript para facilitar el soporte multiplataforma.
4. **Autenticación**: El login debe ser a través del correo institucional de la UTB, utilizando OAuth o SSO compatible con Moodle.
5. **Almacenamiento de Datos**: Debe evitarse el almacenamiento de datos sensibles en el dispositivo; en su lugar, usar almacenamiento en la nube con cifrado.
6. **Seguridad**:
7. **Desempeño**: La aplicación debe mantener tiempos de respuesta menores a 2 segundos en consultas estándar.
8. **Normativas y Políticas**: Cumplir con las políticas de seguridad y privacidad de datos de la UTB y las tiendas de aplicaciones (Google Play y App Store).

# Alcance y Contexto del Sistema {#section-context-and-scope}

## Alcance  
Savio Mobile estará disponible para estudiantes, docentes y administradores de la Universidad Tecnológica de Bolívar (UTB), permitiendo el acceso a cursos, material de estudio y actividades académicas desde dispositivos móviles.  

La aplicación se integrará con Moodle, asegurando la compatibilidad con la plataforma actual de la universidad. También incluirá funciones como notificaciones de actividades, subida de archivos y autenticación con el correo institucional.  

## Contexto  
El propósito de Savio Mobile es mejorar la experiencia de los usuarios al acceder a Savio desde dispositivos móviles, ya que actualmente la versión web de Moodle no está optimizada para estos dispositivos.  

La aplicación servirá como una extensión de la plataforma web, facilitando la navegación y el acceso rápido a información relevante, con una interfaz más intuitiva y adaptada a teléfonos y tablets. 
 
## Contexto de Negocio {#_contexto_de_negocio}

| Actor                 | Rol en el sistema                                  | Interacción con Savio Mobile                        |
|----------------------|------------------------------------------------|-------------------------------------------------|
| Estudiantes         | Usuarios principales de la app                   | Acceden a cursos, actividades, notificaciones y materiales. |
| Docentes           | Creadores y gestores de contenido académico      | Suben material, asignan actividades y envían avisos. |
| Administradores     | Gestionan la plataforma y usuarios               | Controlan accesos, configuración y soporte técnico. |
| Moodle UTB         | Plataforma LMS base                               | Proporciona los cursos, usuarios y datos académicos. |
| Servidores UTB     | Infraestructura de la universidad                | Manejan autenticación y almacenamiento de datos. |
| Dispositivos móviles | Medio de acceso                                 | Ejecutan la aplicación y muestran la interfaz de usuario. |



## Contexto Técnico {#_contexto_t_cnico}

| Componente            | Descripción                                      | Tecnología/Protocolo |
|----------------------|------------------------------------------------|----------------------|
| Aplicación móvil    | Cliente principal para estudiantes y docentes   | Angular/Tonic        |
| Servidor de Moodle  | LMS que gestiona cursos y usuarios              | PHP, MySQL, API REST |
| Base de datos       | Almacena información de usuarios y cursos       | MySQL                |
| API de autenticación | Maneja el login con correo institucional       | OAuth 2.0, SSO  |
| Notificaciones push | Envía alertas sobre actividades académicas      | Moodle's Message API/Moodle's Push Notifications Server |
| Servidor UTB        | Infraestructura para gestionar la app           | Linux, Nginx |


# Estrategia de solución {#section-solution-strategy}

La solución se basa en la integración y extensión de la aplicación oficial Moodle App, desarrollada con Angular, JavaScript y Node.js. Esta aplicación móvil se comunicará con un backend ya existente sobre Moodle, alojado en un servidor Apache, utilizando PHP y MySQL.

Se aprovechará la arquitectura modular de Moodle para extender funcionalidades mediante plugins personalizados, sin modificar el núcleo del sistema. El intercambio de datos entre la aplicación y Moodle se realizará a través de las APIs REST oficiales, garantizando compatibilidad y seguridad.

La estrategia tecnológica incluye:
- Frontend móvil: Moodle App (Angular), adaptada mediante desarrollo de plugins Ionic.
- Backend: Moodle sobre servidor Apache, utilizando PHP 8.x y base de datos MySQL.
- Comunicación: API REST de Moodle con autenticación basada en tokens.
- Seguridad: Cifrado HTTPS, gestión de sesiones seguras y validación de roles.
- Extensibilidad: Plugins personalizados que amplían las capacidades del sistema Moodle para las necesidades específicas de la UTB.

El diseño busca garantizar compatibilidad con futuras versiones de Moodle, escalabilidad del servidor backend y una experiencia de usuario coherente dentro de la aplicación móvil.


# Vista de Bloques {#section-building-block-view}

## Sistema General de Caja Blanca {#_sistema_general_de_caja_blanca}

***Diagrama general***

Motivación
:   Facilitar la comunicación entre estudiantes y docentes mediante la integración de la app Moodle con los servicios backend de la UTB.

Bloques de construcción contenidos

:   Frontend móvil (Moodle App), Backend (servidor PHP en Apache), Base de datos (MySQL), API REST de Moodle.

Interfases importantes

:   API REST entre frontend y backend, conexión PHP-MySQL, y comunicación Angular-API.

### Moodle App {#__caja_negra_1}

Aplicación móvil desarrollada en Angular, usada por los estudiantes y docentes para acceder a recursos educativos y notificaciones.

**Interfases**: API REST de Moodle.

**Calidad**: Multiplataforma, responsiva, segura.

**Ubicación**: Repositorio oficial de Moodle Mobile.

**Requerimientos satisfechos**: Acceso remoto, interacción con plugins, recepción de mensajes.

### Backend PHP/Moodle {#__caja_negra_2}

Servidor que ejecuta el núcleo de Moodle y gestiona la lógica de negocio, incluyendo los plugins.

**Interfases**: API REST, conexión a MySQL, entrada desde App.

**Calidad**: Modular, extensible, segura.

**Ubicación**: Servidor Apache UTB.

**Requerimientos satisfechos**: Procesamiento de datos, autenticación, gestión de usuarios y contenido.

### Base de Datos MySQL {#__caja_negra_3}

Almacena toda la información del sistema: usuarios, cursos, mensajes, configuración de plugins.

**Interfases**: Conexión directa con PHP/Moodle.

**Calidad**: Alta disponibilidad, respaldo periódico.

**Ubicación**: Servidor de base de datos UTB.

**Requerimientos satisfechos**: Persistencia y consulta eficiente de datos.

#### API REST de Moodle {#__interfase_1}

Protocolo de comunicación basado en HTTP usado para el intercambio de datos entre la App y el backend Moodle.

#### Conexión PHP-MySQL {#__interfase_2}

Interfase estándar que permite al backend consultar, insertar o actualizar información en la base de datos.

## Nivel 2 {#_nivel_2}

#### Caja Blanca *Módulo de Autenticación* {#_caja_blanca_autenticacion}

Gestión de login y generación de tokens de acceso. Usa validación contra tabla de usuarios.

#### Caja Blanca *Módulo de Mensajería* {#_caja_blanca_mensajeria}

Encargado del envío/recepción de mensajes desde y hacia la app usando Message API.

#### Caja Blanca *Módulo de Cursos* {#_caja_blanca_cursos}

Maneja la creación, inscripción y acceso a cursos desde la base de datos.

## Nivel 3 {#_nivel_3}

#### Caja Blanca *Login Controller* {#_caja_blanca_bloque_de_construccion_1_1}

Controlador en PHP que valida credenciales y retorna el token al frontend.

#### Caja Blanca *Message API Handler* {#_caja_blanca_bloque_de_construccion_2_1}

Controlador que gestiona la lógica de envío y recepción de mensajes mediante la API de Moodle.

#### Caja Blanca *DBQuery Cursos* {#_caja_blanca_bloque_de_construccion_3_1}

Funciones SQL que consultan información de cursos activos, inscritos y disponibles.


# Vista de Ejecución {#section-runtime-view}

## \<Escenario de ejecución 1> {#__escenario_de_ejecuci_n_1}

 Descripción: Un estudiante abre la app e ingresa su correo institucional y contraseña. La app redirige a la API de autenticación (OAuth 2.0/SSO). Si es válido, el sistema devuelve un token y carga la vista principal.*

-   App → API de autenticación (login)

-   API → Moodle (verificación de usuario)

-   API → App (token de acceso)

-   App → Moodle API (consulta de cursos)

## \<Escenario de ejecución 2> {#__escenario_de_ejecuci_n_2}

Descripción: Un docente sube una nueva tarea. Moodle envía la actualización al sistema de notificaciones. La API Moodle's Messages entrega la alerta push al móvil del estudiante.

- MoodleServer →  registro del *message producer* en db/messages.php 

- MoodleServer →  App móvil, notificacion push


# Vista de Despliegue {#section-deployment-view}

## Nivel de infraestructura 1 {#_nivel_de_infraestructura_1}

***\<Diagrama General>***

Motivación: Garantizar un despliegue eficiente, seguro y escalable de la app, con acceso estable desde cualquier dispositivo móvil.

calidad/Rendimiento:

baja latencia.

alta disponibilidad (≥ 99.5%).

escalabilidad horizontal (carga creciente de usuarios).

mapeo:

-  App móvil → Dispositivo del usuario (Android/iOS)

-  API REST → Servidores UTB (Linux/Nginx)

-  Moodle + Base de datos → Infraestructura UTB

-  Notificaciones →  Moodle's Message API


## Nivel de Infraestructura 2 {#_nivel_de_infraestructura_2}

### *\<Elemento de Infraestructura 1>* {#__emphasis_elemento_de_infraestructura_1_emphasis}

Dispositivos Móviles

- Ejecutan MoodleApp.

- Android 8.0+ / iOS 13+.

- Acceden mediante red pública o WiFi institucional.

### *\<Elemento de Infraestructura 2>* {#__emphasis_elemento_de_infraestructura_2_emphasis}

Servidores UTB

- Almacenan Moodle, APIs, base de datos.

- Firewall institucional, protocolos seguros (HTTPS, TLS). 

# Conceptos Transversales (Cross-cutting) {#section-concepts}

###  Seguridad
- Uso de OAuth 2.0 para autenticación.

- HTTPS en todas las comunicaciones.

- No se almacenan datos sensibles en el dispositivo.

###  Escalabilidad
- Arquitectura basada en microservicios para crecimiento modular.

- Infraestructura con balanceo de carga.

### Experiencia de usuario (UX)
- Interfaz intuitiva, con navegación simple.

- Notificaciones claras y útiles.

- Diseño adaptado a móviles.

### Internacionalización
Posibilidad de soporte multilenguaje (ES/EN).

Recursos en archivos externos fácilmente modificables.


# Requerimientos de Calidad {#section-quality-scenarios}

### Árbol de Calidad
- Seguridad

- Autenticación segura

- Protección de datos personales

### Rendimiento

Tiempo de respuesta < 2 segundos

### Usabilidad

- Navegación intuitiva

- Interfaz accesible

### Portabilidad

- Soporte en Android/iOS

### Escalabilidad

- Infraestructura adaptable

## Escenarios de calidad {#_escenarios_de_calidad}

# Riesgos y deuda técnica {#section-technical-risks}



# Glosario {#section-glossary}

| Término               | Definición                                                                                  |
|-----------------------|---------------------------------------------------------------------------------------------|
| *Servidor*            | Computadora o sistema que proporciona servicios a otros programas o dispositivos.          |
| *Message API*         | Interfaz de programación utilizada por Moodle para gestionar el envío y recepción de mensajes. |
| *Moodle App*          | Aplicación móvil oficial de Moodle, basada en Angular, que permite el acceso remoto.       |
| *Plugin*              | Extensión modular de Moodle que permite añadir o modificar funcionalidades.                |
| *REST API*            | Estilo de arquitectura para intercambio de datos mediante HTTP.                            |
| *Token de acceso*     | Cadena generada por el servidor que permite a un cliente autenticarse de forma segura.     |
| *Apache*              | Servidor HTTP de código abierto usado para alojar aplicaciones web.                        |
| *MySQL*               | Sistema de gestión de bases de datos relacional usado por Moodle.                          |
| *PHP*                 | Lenguaje de programación de lado servidor utilizado en el backend de Moodle.               |
