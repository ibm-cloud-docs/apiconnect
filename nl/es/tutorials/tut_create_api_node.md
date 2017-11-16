---

copyright:
  years: 2017
lastupdated: "2017-10-19"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# Creación de una API en Node.js

**Duración**: 20 minutos  
**Nivel de habilidad**: Principiante  

---
## Objetivo

Esta guía de aprendizaje le guiará a través de la creación de una API en Node.js utilizando la infraestructura de LoopBack. La guía de aprendizaje describe cómo:
1. Crear un nuevo proyecto de LoopBack.
2. Añadir un nuevo origen de datos y modelo a un proyecto de LoopBack utilizando API Designer en el kit de herramientas de {{site.data.keyword.apiconnect_short}}.
3. Probar los puntos finales de la API utilizando la herramienta API Designer Explore.

---
## Requisitos previos

Antes de empezar, [instale el kit de herramientas de {{site.data.keyword.apiconnect_short}}](tut_prereq_install_toolkit.html).

---
## Crear un proyecto de Loopback

Puede crear un proyecto de Loopback utilizando la interfaz de línea de mandatos del kit de herramientas de desarrollador de {{site.data.keyword.apiconnect_short}} o la interfaz de API Designer. 
 
### Crear un proyecto de LoopBack utilizando la línea de mandatos del kit de herramientas

Para crear un proyecto de LoopBack utilizando la línea de mandatos del kit de herramientas de {{site.data.keyword.apiconnect_short}}, siga estos pasos:
1.  Desde la interfaz de línea de mandatos, especifique el mandato siguiente. Se utiliza para crear y gestionar aplicaciones de LoopBack.
	```bash 
	apic loopback
	```
	>![información]
	>Para esta guía de aprendizaje, creará un proyecto denominado weather-data.
2.  En el indicador, escriba `weather-data` como nombre de proyecto y pulse **Intro**.
	```bash
	? What's the name of your application? weather-data
	```
  	>![importante]
  	>En general, un nombre de proyecto puede contener cualquier carácter excepto espacio en blanco (" "), barra inclinada ("/"), carácter &amp; ("&"), arroba("@"), más ("+"), porcentaje ("%"), y dos puntos (":").
3.  Escriba el nombre del directorio en el que creará el proyecto. Pulse **Intro** para utilizar un directorio con el mismo nombre que el proyecto, o escriba un nombre nuevo y pulse **Intro**.
	```bash
	? Enter name of the directory to contain the project: weather-data
	```
4.  Seleccione la versión de LoopBack a utilizar. Elija la versión de producción actual: 3.x.
	```bash
	? Which version of LoopBack would you like to use? 
  	2.x (long term support) 
	? 3.x (current) 
	```
5.  Especifique el tipo de aplicación que desee crear utilizando las teclas de flecha para seleccionar **empty-server**.
	```bash
	? What kind of application do you have in mind? (Use arrow keys)
	? empty-server (An empty LoopBack API, without any configured models or datasources) 
  	hello-world (A project containing a basic working example, including a memory database) 
  	notes (A project containing a basic working example, including a memory database)
	```
6.  Pulse **Intro** para crear una API de LoopBack vacía. 

La herramienta muestra un número de mensajes a medida que crea el directorio del proyecto y añade a este un número de directorios y archivos. También ejecuta npm install para instalar todas las dependencias del proyecto, como se especifica en package.json. Este proceso crea un directorio node_modules y puede tardar un poco.

Un proyecto vacío de LoopBack contiene los directorios siguientes:
- server: contiene el modelo de servidor y las definiciones de origen de datos, y otro código de servidor
- definitions: contiene archivos de definición de YAML
- node_modules: creado por node.js


### Crear un proyecto de LoopBack utilizando la interfaz de API Designer

Para crear un proyecto de LoopBack utilizando el API Designer, siga estos pasos:
1.  Desde la interfaz de línea de mandatos, especifique el mandato siguiente para iniciar el API Designer:
	```bash
	apic edit
	```
	![](images/api-designer-1.png)
	>![información]
	>El mandato anterior inicia el kit de herramientas de APIC e inicia el API Designer en el navegador predeterminado cuando se realiza.
	>![información]
	>En esta guía de aprendizaje, creará un proyecto denominado weather-data.
2.  Si no ha marcado anteriormente el panel de navegación de IU, pulse el icono Navegar a ![](images/navigate-to.png). Se abrirá el panel de navegación de la IU de API Manager. Para marcar el panel de navegación de la IU, pulse el icono de menú Marcar ![](images/pinned.png).
3.  En la barra lateral, pulse el icono Projects Plus ![](images/add-icon.png).
4.  Pulse **Crear proyecto de LoopBack**. Verá el diálogo **Añadir nuevo proyecto de LoopBack**.
5.  Seleccione **empty-server** como plantilla de proyecto.
6.  Para **Versión de LoopBack**, seleccione versión 3.x (la versión actual).
7.  Escriba `weather-data` para los campos Nombre de visualización y Nombre.
8.  Para el **Directorio de proyectos**, seleccione la carpeta `weather-data` creada en el paso 1 pulsando el botón **Examinar**.
	![](images/api-designer-2.png)
9. Pulse **Añadir** para añadir el proyecto.
	>![información]
	>Se mostrarán varios mensajes en la ventana **Añadir nuevo proyecto de LoopBack** a medida que crea el directorio del proyecto y añade varios directorios y archivos al mismo. También ejecuta npm install para instalar todas las dependencias del proyecto, como se especifica en package.json. Este proceso crea un directorio node_modules y puede tardar un poco.
	
	>Un proyecto vacío de LoopBack contiene los directorios siguientes:
	- server: contiene el modelo de servidor y las definiciones de origen de datos, y otro código de servidor
	- definitions: contiene archivos de definición de YAML
	- node_modules: creado por node.js
10. Pulse **Finalizado** para cerrar el recuadro de diálogo **Añadir nuevo proyecto de LoopBack**.
11. Salga de **API Designer** volviendo a la línea de mandatos del paso 1 y especificando `Ctrl + C`. Escriba `Y` para confirmar la salida.
12. Cierre la sesión del navegador.

---
## Añadir un nuevo origen de datos y modelo

Para añadir un nuevo modelo y origen de datos a un proyecto de LoopBack utilizando el API Designer, siga estos pasos:

### Añadir un origen de datos
Para añadir un nuevo origen de datos a un proyecto de LoopBack utilizando el API Designer, siga estos pasos.
1. También debe crear un proyecto de LoopBack (el proyecto "weather-data") tal como se describe en `Crear un proyecto de LoopBack desde la línea de mandatos` y asegurarse de que el directorio de trabajo actual es el directorio raíz de proyecto:
	```bash
	cd weather-data
	```
2. En la línea de mandatos, especifique el mandato siguiente:
	```bash
	apic edit
	```
	Transcurridos unos instantes, la consola mostrará este mensaje:
	```bash
	Express server listening on http://127.0.0.1:9000
	```
	API Designer se abrirá en el navegador web predeterminado, que muestra inicialmente la página de inicio de sesión si no ha iniciado la sesión recientemente.  
	>![información]
	>Puede iniciar sesión utilizando su cuenta de Bluemix o puede crear una.
3. Pulse el icono **Orígenes de datos** ![](images/datasource-icon.png).
4. Pulse **Añadir**. Se abrirá la ventana Nuevos orígenes de datos de LoopBack.
5. Escriba `weatherDS` en el campo de texto **Nombre**.
	>![información]
	>En el nombre de un origen de datos se puede utilizar cualquier carácter alfanumérico, guiones y subrayado.
6. Pulse **Nuevo**.
7. De forma predeterminada, el valor **Conector** indica **In-memory db** y los demás valores están en blanco. Mantenga los valores predeterminados por ahora, y API Designer guardará automáticamente el nuevo origen de datos.
	>![información]
	>El origen de datos en memoria está incorporado en LoopBack y solo es adecuado si se van a efectuar tareas de desarrollo y de pruebas iniciales. Cuando esté listo para conectar los modelos a un origen de datos real como un servidor de bases de datos, cambie el valor de **Conector** en consecuencia e instale el conector de origen de datos siguiendo las instrucciones de [Instalación de conectores de LoopBack ![Icono de enlace externo](../../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SSMNED_5.0.0/com.ibm.apic.toolkit.doc/tapim-connector-install.html#task_i2p_dnw_vv){:new_window}. Especifique los valores del conector (nombre de host, puerto, nombre de base de datos, nombre de usuario, contraseña) como sea apropiado para su tipo de Conector, y pulse el icono **Guardar** ![](images/save-icon.png). API Designer probará automáticamente la conexión en el origen de datos. Si la prueba es correcta, mostrará el mensaje **Success - Data source connection test succeeded**.
8. Pulse el icono Probar conexión ![](images/db-test-icon.png) para probar la conexión de origen de datos. Se mostrará el mensaje "Data source connection test succeeded".
9. Pulse **Todos los orígenes de datos**. El origen de datos aparecerá en la lista de orígenes de datos, y el editor actualizará el archivo server/datasources.json con los valores para el nuevo origen de datos.

### Añadir un modelo

Para añadir un nuevo modelo a un proyecto de LoopBack utilizando el API Designer, siga estos pasos:
1. Pulse el icono **Modelos** ![](images/models-icon.png).
2. Pulse **Añadir**. Se abre la ventana Nuevo modelo de LoopBack.
3. Escriba `weather` en el campo de texto **Nombre** y, a continuación, pulse **Nuevo**.
4. En el campo **Origen de datos**, seleccione **weatherDS**.
	![](images/new-model-1.png)
5. En las **Propiedades**, pulse el icono **Añadir propiedad** ![](images/add-icon.png).
6. En el campo de texto **Nombre de propiedad**, escriba `código_postal`.
7. Para **Tipo**, seleccione **número**.
8. Seleccione **Necesario** para convertir la propiedad en necesaria. Esto significa que debe tener un valor cuando añada o actualice una instancia de modelo. Por ahora, mantenga los valores predeterminados para los demás valores:
	- **Es matriz**: Si la propiedad es una matriz JavaScript con elementos del tipo especificado.
	- **ID**: Si la propiedad es un identificador exclusivo.
	- **Índice**: Si la propiedad representa una columna (campo) que es un índice de base de datos.
	- **Descripción**: Descripción en texto de la propiedad.
9. Pulse el icono **Añadir propiedad** ![](images/add-icon.png) de nuevo para añadir otra propiedad. Haga referencia a la tabla siguiente para completar el resto de las propiedades:
	![](images/new-model-property-1.png)
10. Pulse el icono **Guardar** ![](images/save-icon.png) para guardar los cambios.
11. Pulse **Todos los modelos** para terminar de editar el modelo.

Lo anterior completa la adición de un nuevo origen de datos y modelo para el proyecto de LoopBack weather-data.

---

## Probar el proyecto de LoopBack

>![información]
	>Puede ir directamente al paso 2 siguiente si no ha salido del diseñador de {{site.data.keyword.apiconnect_short}} después de completar la sección "Añadir un nuevo modelo y origen de datos".
	
Para probar los puntos finales de la API utilizando la herramienta Explorar de API Designer, siga estos pasos:
1. En la línea de mandatos, especifique el mandato siguiente:
	```bash
	apic edit
	```
	Transcurridos unos instantes, la consola mostrará este mensaje:
	```bash
	Express server listening on http://127.0.0.1:9000
	```
	API Designer se abrirá en el navegador web predeterminado, que muestra inicialmente la página de inicio de sesión si no ha iniciado la sesión recientemente.
	
2. Inicie los servidores de prueba locales.
	a. En la consola de prueba de la parte inferior de la pantalla, pulse el icono **Iniciar los servidores** ![](images/test-icon.png):
	![](images/start-server-1.png)
	b. Espere hasta que se muestre el mensaje En ejecución:
	![](images/running-server-1.png)

	>![información]
	>Dependiendo de la configuración del proyecto y de si hay otros procesos en ejecución, puede que se muestren distintos números de puerto.
3. Pulse **http://127.0.0.1:port_number** para visualizar el punto final raíz de la API. En cuanto al proyecto predeterminado de LoopBack (vacío o "Hello world"), verá algo parecido a esto:
	```bash
	{"started":"2017-05-24T19:21:47.807Z","uptime":80.876}
	```
	>![información]
	>Para detener el proyecto, pulse el icono **Detener los servidores** ![](images/stop-icon.png):
	>![](images/stop-server-1.png)
	
	>Para reiniciarlo, pulse el icono **Reiniciar los servidores** ![](images/restart-icon.png):
	>![](images/restart-server-1.png)
	
4. Pulse el icono **Explorar** ![](images/explore-icon.png) para ver la herramienta Explorar de API Designer. La barra lateral muestra todas las operaciones REST para los modelos de LoopBack en la API. Los modelos basados en PersistedModel de forma predeterminada tienen un [conjunto estándar de operaciones crear, leer, actualizar y suprimir ![Icono de enlace externo](../../../icons/launch-glyph.svg "Icono de enlace externo")](http://loopback.io/doc/en/lb2/PersistedModel-REST-API){:new_window}.

5. Pulse la operación **weather.create** en el panel izquierdo para mostrar el punto final.
![](images/explore-test-1.png)
El panel central muestra información de resumen sobre el punto final, incluidos sus parámetros, seguridad, datos de instancia del modelo y códigos de respuesta. El panel derecho proporciona código de plantilla para llamar al punto final utilizando el mandato curl, y lenguajes como Ruby, Python, Java y Node.

6. Para probar los puntos finales REST en la herramienta Explorar de API Designer, en el panel derecho pulse **Probarlo**. Desplácese hasta **Parámetros** y pulse **Generar** para generar algunos datos ficticios. De forma predeterminada, entre los datos generados se incluyen las propiedades `zip_code`, `current_temperature`, `current_humidity`, `tonight_temperature_low`, `tonight_temperature_high`, `tonight_humidity_low`, `tonight_humidity_high` e `id`. La propiedad `id` la crea LoopBack para un modelo determinado y el valor se genera automáticamente. Elimine la propiedad `id` de los datos de ejemplo, actualice los datos generados según sea necesario, y pulse **Llamar operación**.
![](images/explore-test-2.png)
>![resolución de problemas]
>Si ve un mensaje de error debido a un certificado no de confianza para localhost, pulse el enlace proporcionado en el mensaje de error de la herramienta Explorar de API Designer para aceptar el certificado y, a continuación, siga llamando las operaciones en el navegador web. El procedimiento exacto depende del navegador web que está utilizando. Si carga los puntos finales REST directamente en el navegador, verá el mensaje: {"name":"PreFlowError","message":"unable to process the request"}. Debe utilizar la herramienta Explorar de API Designer para probar los puntos finales REST en el navegador porque incluye las cabeceras necesarias y otros parámetros de solicitud.
>
>![resolución de problemas]
>Si obtiene un código de respuesta de **422 - Unprocessable Entity** con la carga útil siguiente:
>![](images/explore-test-3.png)
>
>el elemento de datos `id` no se ha eliminado de los datos generados. Elimine el elemento de datos `id` y vuelva a ejecutar la prueba.
>![resolución de problemas]
>Si recibe el error **no se ha podido analizar el cuerpo de la solicitud**, debe eliminar la coma después del último número de `humidity_high`.
7. Edite los valores de JSON que se muestran en la sección **datos**. Intente cambiar los datos ficticios generados, y pulse **Llamar operación** de nuevo. Debería ver los parámetros de solicitud y respuesta, junto con los datos de instancia de JSON que ha especificado.
![](images/explore-test-4.png)

8. Para confirmar que la operación ha añadido una instancia de modelo, pulse **weather.find**. Pulse **Llamar operación** para mostrar todas las instancias meteorológicas. Por ejemplo (con las instancias de modelo):

	![](images/explore-test-5.png)
---

### Qué ha hecho en esta guía de aprendizaje
En esta guía de aprendizaje, ha realizado lo siguiente:
1. Ha creado un nuevo proyecto de LoopBack utilizando la línea de mandatos del kit de herramientas de {{site.data.keyword.apiconnect_short}}.
2. Ha añadido un nuevo modelo y origen de datos a un proyecto de LoopBack utilizando el API Designer en el kit de herramientas de {{site.data.keyword.apiconnect_short}}.
3. Ha probado los puntos finales de API utilizando la herramienta Explorar de API Designer.


---

## Paso siguiente

[Gestionar un servicio REST](tut_rest_landing.html) o [Gestionar un servicio SOAP](tut_manage_soap_api.html).

Crear > **Gestionar** > Proteger > Socializar > Analizar

 
[important]: ./images/important.png "¡Importante!"
[info]: ./images/info.png "Información"
[troubleshooting]: ./images/troubleshooting.png "Resolución de problemas" 

