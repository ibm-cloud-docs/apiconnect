---

copyright:
  years: 2017
lastupdated: "2017-06-05"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal

subcollection: apiconnect

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Glosario
{: #glossary_apic_glossary}

Glosario de términos y definiciones de {{site.data.keyword.apiconnect_short}}.

- **Desarrollador de API**: Un desarrollador de API crea y configura API, productos y políticas para organizaciones de proveedores
de las cuales es miembro. Un desarrollador de API puede ser miembro de una o más organizaciones de
proveedores. El desarrollador de API se centra más en la implementación técnica de las API que en la
relación comercial con los desarrolladores de aplicaciones.

- **Operación de API**: Unidad de una API REST que se puede invocar. Una operación de API se compone de un verbo HTTP y una vía de acceso de URL subordinada a la raíz de contexto de la API.

- **Diseñador de API**: La IU para crear API.

- **Gestor de API**: La IU para gestionar API, planificaciones y productos.

- **aplicación**: Fragmento de código de cliente que accede a las API para interactuar con un servicio, sistema o contenido. Las aplicaciones son normalmente aplicaciones web o apps móviles.

- **ensamblaje**: Interfaz de programación de aplicaciones que proporciona funcionalidad enriquecida
para interactuar con una aplicación: realiza llamadas complementarias a servicios externos
y, a continuación, transforma y agrega la respuesta antes de que se transmita
una respuesta a la aplicación de llamada.

- **Catálogo**: Un catálogo es un destino de transferencia y se comporta como una partición lógica de la pasarela
y el Portal del desarrollado. Los URL para llamadas API y para el Portal del desarrollador son específicos
de un catálogo concreto.

- **ID de cliente**: Información que identifica una aplicación individual. Una aplicación sólo puede invocar una API si pasa una clave de aplicación reconocida
por el sistema {{site.data.keyword.apiconnect_short}} y que tenga otorgado acceso a la API. El cliente pasa la clave de aplicación utilizando un parámetro de consulta
HTTP.

- **secreto de cliente**: Información que se utiliza junto con la clave de aplicación para verificar la
identidad de una aplicación. Una API se puede configurar para
requerir que las aplicaciones cliente suministren su secreto de aplicación con
su clave de aplicación. El secreto de aplicación funciona de forma efectiva como
una contraseña que solo conoce la aplicación. El cliente pasa el secreto de aplicación utilizando un parámetro de
consulta HTTP.

- **comunidad**: Un conjunto de organizaciones de desarrolladores. Se utiliza como una
construcción de agrupación cuando se publican APIS. Las comunidades se utilizan para restringir la visibilidad y la accesibilidad de API. Se puede publicar una API en comunidades
seleccionadas, lo que significa que sólo los desarrolladores de aplicaciones de esas organizaciones
pueden ver la API.

- **Modelo LoopBack**: Un modelo LoopBack es un objeto de JavaScript que representa datos de aplicación e incluye reglas
de validación, prestaciones de acceso a datos y lógica empresarial. Los modelos LoopBack proporcionan
una API REST de forma predeterminada y conecta con orígenes de datos para acceder a datos de fondo.

- **Origen de datos de LoopBack**: Un origen de datos de LoopBack es un objeto de JavaScript que representa un servicio
de fondo, como una base de datos, API REST (que se va a consumir) o servicio web de SOAP. Los conectores respaldan a los orígenes de datos, que se comunican directamente con la base de datos
u otros servicios de fondo.

- **organización**: La entidad que posee las API o aplicaciones que utilizan las API. Una organización
de proveedores posee API y planes asociados, y puede poseer aplicaciones de
forma adicional. Una organización de desarrolladores sólo posee aplicaciones. Una organización tiene por lo menos un propietario. Una organización puede ser un equipo de proyecto, departamento o división.

- **Vía de acceso**: Una vía de acceso define la ruta a través de la cual los usuarios acceden a las API REST. Una vía de acceso consta de
una o varias operaciones de HTTP, como GET o POST.

- **Plan**: La construcción empaquetada mediante la cual las API pasan a estar a disposición de los desarrolladores. Un plan deja disponible una recopilación de operaciones desde una o más API y se publica en comunidades de desarrolladores de aplicaciones. Los desarrolladores de aplicaciones obtienen
acceso a las API registrando aplicaciones para acceder a los planes. Un plan incluye una recopilación de valores de
política. En su forma más simple, un plan define una política de cuota única que se aplica a todas las operaciones de API a las que se accede mediante el plan. En
casos más avanzados, se pueden asociar políticas adicionales con un plan.

- **política**: Una política es un fragmento de configuración que controla un aspecto concreto del proceso en el servidor
de pasarela durante el manejo de una invocación de API en el tiempo de ejecución. Las políticas son los bloques de construcción de flujos de ensamblaje. Las políticas proporcionan
los medios para configurar prestaciones como la seguridad, el registro, el direccionamiento de solicitudes a servicios
de destino y la transformación de datos de un formato a otro. Las políticas se pueden configurar en el contexto de una API o en el contexto de un plan.

- **Producto**: Los productos proporcionan un método mediante el cual puede agrupar las API en un paquete destinado a un uso determinado. Además, contienen Planes, que se pueden utilizar para
diferenciar entre distintas ofertas. Solo puede crear planes dentro de los productos, y estos productos se publican en un catálogo.

- **proxy**: Interfaz de programación de aplicaciones que reenvía solicitudes a un recurso de fondo definido por el usuario y retransmite las respuestas a la aplicación de llamada.

- **publicar**: El proceso de mover una aplicación o producto desde la transferencia, de forma que las planificaciones y las
API incluidas estén disponibles para que los desarrolladores de aplicaciones accedan a ellas y las usen.

- **rol**: Un rol define los permisos que pueden habilitar la funcionalidad para los usuarios. Cada rol tiene un conjunto
de permisos distinto.

- **Catálogo de recinto de pruebas**: En un catálogo de recinto de pruebas, se omiten las aprobaciones para las acciones de publicación y ciclo de vida. Las aprobaciones
pendientes se cancelan cuando un catálogo no de recinto de pruebas se convierte en un recinto de pruebas. Los catálogos de recinto
de pruebas se utilizan para probar las API que están en desarrollo.

- **definición de seguridad**: Una definición de seguridad especifica todos los valores para un aspecto concreto de la seguridad de la API; por
ejemplo, el registro de usuarios que se utiliza para autenticar el acceso a la API.

- **Perfil SSL**: Los perfiles SSL se utilizan para proteger la transmisión de datos a través de sitios web. Los certificados SSL
garantizan que no se pueda robar o falsificar la información que se envía a sitios web.

- **transferir**: Proceso de mover una aplicación o producto desde el estado de borrador a un catálogo en
preparación para su publicación.

- **suscripción**: Una suscripción es el medio mediante el cual un desarrollador de aplicaciones obtiene acceso a los recursos proporcionados
por una API. Un desarrollador de aplicaciones utiliza el Portal del desarrollador para
suscribirse en la planificación en la que se publica la API.

- **registro de usuarios**: Un registro de usuarios es una forma de asegurar el acceso a los catálogos y las API. El usuario puede proteger las API con
un registro de usuarios, de modo que cuando se llame una API se deban proporcionar las credenciales de usuario.

- **ampliación de proveedor**: Una ampliación de proveedor se añade a una API REST para ampliar la especificación de OpenAPI (Swagger 2.0).
