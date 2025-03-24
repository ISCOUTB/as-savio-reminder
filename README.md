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
->plataforma estable para android y ios
->una app segura y rapida
 
## Partes interesadas (Stakeholders) {#_partes_interesadas_stakeholders}

| Rol/Nombre                | Contacto          | Expectativas                 |
|---------------------------|-------------------|-----------------------------|
| Willy Jaime Laza Barrios  | wlaza@utb.edu.co | Conexión Moodle App y Savio |

# Restricciones de la Arquitectura {#section-architecture-constraints}

El desarrollo de Savio Mobile debe cumplir con las siguientes restricciones:

1. **Compatibilidad con Moodle**: La aplicación debe integrarse con la API de Moodle para garantizar el acceso a cursos, recursos y actividades.
2. **Plataformas soportadas**: La aplicación debe ser compatible con Android (mínimo Android 8.0) y iOS (mínimo iOS 13).
3. **Lenguajes y Frameworks**: Se debe desarrollar usando Flutter/Dart para facilitar el soporte multiplataforma.
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
|----------------------|------------------------------------------------|--------------------|
| Aplicación móvil    | Cliente principal para estudiantes y docentes   | Flutter/Dart      |
| Servidor de Moodle  | LMS que gestiona cursos y usuarios              | PHP, MySQL, API REST |
| Base de datos       | Almacena información de usuarios y cursos       | MySQL/PostgreSQL  |
| API de autenticación | Maneja el login con correo institucional        | OAuth 2.0, SSO    |
| Notificaciones push | Envía alertas sobre actividades académicas      | Firebase Cloud Messaging |
| Servidor UTB        | Infraestructura para gestionar la app           | Linux, Nginx      |


# Estrategia de solución {#section-solution-strategy}

# Vista de Bloques {#section-building-block-view}

## Sistema General de Caja Blanca {#_sistema_general_de_caja_blanca}

***\<Diagrama general>***

Motivación

:   *\<Explicación en texto>*

Bloques de construcción contenidos

:   *\<Desripción de los bloques de construcción contenidos (Cajas
    negras)>*

Interfases importantes

:   *\<Descripción de las interfases importantes>*

### \<Caja Negra 1> {#__caja_negra_1}

*\<Propósito/Responsabilidad>*

*\<Interfase(s)>*

*\<(Opcional) Características de Calidad/Performance>*

*\<(Opcional) Ubicación Archivo/Directorio>*

*\<(Opcional) Requerimientos Satisfechos>*

*\<(Opcional) Riesgos/Problemas/Incidentes Abiertos>*

### \<Caja Negra 2> {#__caja_negra_2}

*\<plantilla de caja negra>*

### \<Caja Negra N> {#__caja_negra_n}

*\<Plantilla de caja negra>*

### \<Interfase 1> {#__interfase_1}

...

### \<Interfase m> {#__interfase_m}

## Nivel 2 {#_nivel_2}

### Caja Blanca *\<bloque de construcción 1>* {#_caja_blanca_emphasis_bloque_de_construcci_n_1_emphasis}

*\<plantilla de caja blanca>*

### Caja Blanca *\<bloque de construcción 2>* {#_caja_blanca_emphasis_bloque_de_construcci_n_2_emphasis}

*\<plantilla de caja blanca>*

...

### Caja Blanca *\<bloque de construcción m>* {#_caja_blanca_emphasis_bloque_de_construcci_n_m_emphasis}

*\<plantilla de caja blanca>*

## Nivel 3 {#_nivel_3}

### Caja Blanca \<\_bloque de construcción x.1\_\> {#_caja_blanca_bloque_de_construcci_n_x_1}

*\<plantilla de caja blanca>*

### Caja Blanca \<\_bloque de construcción x.2\_\> {#_caja_blanca_bloque_de_construcci_n_x_2}

*\<plantilla de caja blanca>*

### Caja Blanca \<\_bloque de construcción y.1\_\> {#_caja_blanca_bloque_de_construcci_n_y_1}

*\<plantilla de caja blanca>*

# Vista de Ejecución {#section-runtime-view}

## \<Escenario de ejecución 1> {#__escenario_de_ejecuci_n_1}

-   *\<Inserte un diagrama de ejecución o la descripción del escenario>*

-   *\<Inserte la descripción de aspectos notables de las interacciones
    entre los bloques de construcción mostrados en este diagrama.\>*

## \<Escenario de ejecución 2> {#__escenario_de_ejecuci_n_2}

## ... {#_}

## \<Escenario de ejecución n> {#__escenario_de_ejecuci_n_n}

# Vista de Despliegue {#section-deployment-view}

## Nivel de infraestructura 1 {#_nivel_de_infraestructura_1}

***\<Diagrama General>***

Motivación

:   *\<Explicación en forma textual>*

Características de Calidad/Rendimiento

:   *\<Explicación en forma textual>*

    Mapeo de los Bloques de Construcción a Infraestructura

    :   *\<Descripción del mapeo>*

## Nivel de Infraestructura 2 {#_nivel_de_infraestructura_2}

### *\<Elemento de Infraestructura 1>* {#__emphasis_elemento_de_infraestructura_1_emphasis}

*\<diagrama + explicación>*

### *\<Elemento de Infraestructura 2>* {#__emphasis_elemento_de_infraestructura_2_emphasis}

*\<diagrama + explicación>*

...

### *\<Elemento de Infraestructura n>* {#__emphasis_elemento_de_infraestructura_n_emphasis}

*\<diagrama + explicación>*

# Conceptos Transversales (Cross-cutting) {#section-concepts}

## *\<Concepto 1>* {#__emphasis_concepto_1_emphasis}

*\<explicación>*

## *\<Concepto 2>* {#__emphasis_concepto_2_emphasis}

*\<explicación>*

...

## *\<Concepto n>* {#__emphasis_concepto_n_emphasis}

*\<explicación>*

# Decisiones de Diseño {#section-design-decisions}

# Requerimientos de Calidad {#section-quality-scenarios}

## Árbol de Calidad {#__rbol_de_calidad}

## Escenarios de calidad {#_escenarios_de_calidad}

# Riesgos y deuda técnica {#section-technical-risks}

# Glosario {#section-glossary}

+-----------------------+-----------------------------------------------+
| Término               | Definición                                    |
+=======================+===============================================+
| *\<Término-1>*        | *\<definicion-1>*                             |
+-----------------------+-----------------------------------------------+
| *\<Término-2>*        | *\<definicion-2>*                             |
+-----------------------+-----------------------------------------------+
