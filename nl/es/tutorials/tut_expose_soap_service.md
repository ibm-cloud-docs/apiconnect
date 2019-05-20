---

copyright:
years: 2019
lastupdated: "2019-3-12"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
 

# Exponer un servicio SOAP como una API REST
{: #tut_expose_soap_service}

**Duración**: 20 minutos  
**Nivel de habilidad**: Principiante  

---
## Objetivo
{: #object_tut_expose_soap_service}

En API Manager, creará una API REST que accederá a un Servicio SOAP anterior y lo expondrá como una API REST.

## Requisitos previos
{: #prereq_tut_expose_soap_service}

1. Antes de empezar, deberá [configurar la instancia de {{site.data.keyword.apiconnect_full}}](/docs/services/apiconnect?topic=apiconnect-tut_prereq_set_up_apic_instance).
2. Antes de empezar, copie el archivo de [prueba weatherprovider.wsdl ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://raw.githubusercontent.com/IBM-Bluemix-Docs/apiconnect/master/tutorials/weatherprovider.wsdl){: #new_window} en el sistema de archivos local.
	>![images/info.png]
	>Puede pulsar **Sin procesar** y, a continuación, guardar la página resultante en el sistema local como un archivo `.wsdl`.

---
## Configuración de una definición de API REST
{: #setup_tut_expose_soap_service}

1. Inicie sesión en {{site.data.keyword.Bluemix_short}}: https://cloud.ibm.com.
2. En el **Panel de control** de {{site.data.keyword.Bluemix_notm}}, pulse **Servicios de Cloud Foundry**. Inicie el servicio {{site.data.keyword.apiconnect_short}}. 
3. En {{site.data.keyword.apiconnect_short}}, asegúrese de que el panel de navegación está abierto. Si no lo está, pulse **>>** para abrirlo.  

  ![](images/cloud-apic-dashboard.png)

4. Seleccione **Borradores** en el panel de navegación.
5. Seleccione **Añadir +** > **Nueva API**.

    ![](images/cloud-add-api-new.png)  

	
6. Especifique información básica sobre la API.
	- En el campo **Título**, escriba `Weather Data`.
	- Debe el campo **Nombre** como `weather-data` cuando se rellene al escribir el título.	
	- Deje el campo Vía de acceso **Base** como `/weather-data`.
	- Deje el campo **Versión** como `1.0.0`.
7. Expanda **Propiedades adicionales** para especificar propiedades adicionales para la API.
	- Desde el campo **Plantilla de API**, seleccione **Predeterminado** para indicar que desea utilizar la plantilla predeterminada para crear la definición de la API.
	- Deje los campos restantes sin cambiar.
	![](images/new-api-1.png)
8. Añada la API a un nuevo Producto y, a continuación, cree la definición de la API.
	- Seleccione **Añadir un producto**.
	- En el campo **Título**, utilice `producto Weather Data` como el valor predeterminado.
	- Deje los campos **Nombre** y **Versión** sin cambiar.
	- Asegúrese de que esté seleccionado el recuadro de selección **Publicar este producto en un catálogo** y, a continuación, seleccione **Recinto de pruebas** como Catálogo de destino.
	![](images/new-api-2.png)
	- Pulse **Crear API**. Se abrirá el separador **Diseño** para el borrador de la definición de la API.
9. La API se ha creado ahora. Se muestra la página Diseño.

   ![](images/design-new-1.png)

10. Pulse **Definiciones** en la barra de navegación. Pulse el icono **Añadir definición** ![](images/add-icon.png).

11. Expanda la nueva definición pulsando en ella.
12. Asigne un nombre a la definición `Salida de Weather Data`.
13. La definición tendrá cinco propiedades. Pulse **Añadir propiedad** cuatro veces para añadir las propiedades adicionales. Cambie el nombre de `Nombre de propiedad` utilizando lo siguiente como guía y utilice el valor predeterminado para la `Descripción`, el `Tipo` y el `Ejemplo`:
    a. Añada nuevas propiedades para la definición **Salida de Weather Data**.    
       - Nombre: código postal         /  Tipo: serie   
       - Nombre: temperatura /  Tipo: entero   
       - Nombre: humedad    /  Tipo: entero   
       - Nombre: ciudad        /  Tipo: serie   
       - Nombre: estado       /  Tipo: serie   

	![](images/definition-new-1.png)
14. Pulse **Vías de acceso** en la barra de navegación. Pulse el icono **Añadir vía de acceso** ![](images/add-icon.png).
15. Establezca el **Título** de la vía de acceso recién creada en `/getweatherdata`.
16. Expanda la operación **GET /getweatherdata** pulsándola.
	![](images/path-new-1.png)
17. Para la operación **GET /getweatherdata**, pulse **Añadir parámetro** y, a continuación, pulse **Añadir nuevo parámetro**.
18. Designe un nombre para el nuevo parámetro `zip_code` y deje el resto como predeterminado.
19. En la columna **Esquema** de la respuesta **200 Aceptar** de la sección **Respuestas**, seleccione la definición **Salida de Weather Data**. Para la respuesta a la llamada de API, el objeto definido por la **Salida de Weather Data** será el objeto de respuesta.
	![](images/path-new-2.png)
20. Pulse el icono Guardar ![](images/save-icon.png) para guardar los cambios.

---
## Añadir y configurar la invocación de servicio web
{: #add_web_tut_expose_soap_service}

Para añadir y configurar las políticas de invocación y de correlación que integran el servicio web en la definición de API, siga los pasos siguientes.
1. En la sección **Servicios**, pulse el icono **Añadir servicio** ![](images/add-icon.png). Se abrirá la ventana `Importar servicio web desde WSDL`.
	![](images/upload-file-1.png)
2. Seleccione **Cargar archivo**.
3. En la ventana **Carga de archivos**, especifique la ubicación en el archivo `weatherprovider.wsdl` que ha descargado en el `paso 2` de la sección **Requisitos previos** y pulse **Abrir** para continuar.
4. Seleccione el servicio SOAP **weatherService** y pulse **Listo**. En la sección **Servicios**, el servicio web **WeatherService** aparecerá con una única operación **weatherRequest**.
	![](images/upload-file-2.png)

	![](images/services-add-1.png)	
5. Navegue al separador **Ensamblar** y asegúrese de que **Políticas de DataPower Gateway** esté seleccionado.
6. Suprima la política de **invocación** anterior en el lienzo pasando el cursor sobre la política y, a continuación, pulsando el icono **Suprimir política** ![](images/delete-icon.png).
	![](images/delete-invoke-1.png)	
7. En la paleta, arrastre el servicio web **weatherRequest** al recuadro discontinuo que se muestra en el lienzo. Se coloca una política de invocación y dos políticas de correlación en el ensamblado. La primera política de correlación asigna variables a la entrada de la invocación del servicio web, mientras que la segunda política asigna salidas de la invocación del servicio web a variables. Las salidas de la primera correlación y las entradas de la segunda correlación se generan a partir del WSDL proporcionado en el paso 4.
	![](images/services-add-2.png)	
8. Pulse la política de correlación **weatherRequest: entrada** y, a continuación, pulse el icono **Editar entradas** ![](images/edit-icon.png) en la columna Entrada de la hoja de propiedades.
	![](images/services-add-3.png)	
9. Pulse **+ parámetros de operación** y seleccione `get /getweatherdata`.
10. Pulse **Listo** para añadir el parámetro `zip_code`.
	![](images/webservice-input-1.png)
11. Pulse el círculo correspondiente a **serie zip_code** en el lado de entrada y, a continuación, pulse el círculo correspondiente a **serie de código postal** en el lado de salida.  
	![](images/webservice-input-2.png)
12. Cierre la hoja de propiedades.
13. Pulse la política de correlación de **weatherRequest: salida** en la paleta y, a continuación, pulse el icono **Editar salidas** ![](images/edit-icon.png) en la columna Salida de la hoja de propiedades.
14. Seleccione **+ salidas de operación** y seleccione `get /getweatherdata`.
15. Seleccione **Listo** para añadir la definición de salida `Salida de Weather Data`.
	![](images/webservice-output-1.png)
16. Pulse el círculo correspondiente a **serie de código postal** en el lado de entrada y, a continuación, pulse el círculo correspondiente a **serie de código postal** en el lado de salida. Correlacione los parámetros restantes utilizando lo siguiente como guía.
	![](images/webservice-output-2.png)
17. Pulse el icono **Guardar** ![](images/save-icon.png) para guardar los cambios.

Ha incluido la invocación del servicio web en el ensamblado y ha correlacionado un parámetro de entrada con la parte apropiada de la solicitud SOAP y ha correlacionado la parte apropiada de la respuesta de SOAP a una salida JSON.

---
## Probar la definición de API
{: #test_tut_expose_soap_service}

Para probar la definición de API utilizando la herramienta de prueba de API Manager, siga estos pasos.
1. Pulse el icono **Probar** ![](images/test-icon.png) debajo del separador **Ensamblar** para revelar el panel de prueba.
	![](images/test-pane-1.png)
2. Si ha utilizado la herramienta de prueba antes, pulse **Cambiar la configuración**.
3. Seleccione `Producto Weather Data 1.0.0` de la lista de productos.
	![](images/choose-product-1.png)
4. Pulse **Volver a publicar producto**.
5. Pulse **Siguiente**.
6. Seleccione `get /getweatherdata` de la lista de operaciones.  
	![](images/select-operation-1.png)
7. Desplácese hasta el campo **zip_code**, escriba `10504`.  
	![](images/test-api-1.png)
8. Pulse **Invocar**. La API devuelve el tiempo actual.  
	![](images/test-wdata-result.png)

---
## Conclusión
{: #conclusion_tut_expose_soap_service}

En esta guía de aprendizaje, ha completado las actividades siguientes:
1. Ha configurado una definición de API REST
2. Ha configurado una API para invocar un servicio web existente y ha devuelto su salida
3. Ha probado la definición de API

---

## Paso siguiente
{: #next_tut_expose_soap_service}

Proteger la API utilizando [protección utilizando OAuth 2.0](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_oauth_2).

Crear > **Gestionar** > Proteger > Socializar > Analizar

[important]: ./images/important.png "¡Importante!"
[info]: ./images/info.png "Información"
[troubleshooting]: ./images/troubleshooting.png "Resolución de problemas" 
