---
copyright:
  years: 2019
lastupdated: "2019-3-9"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Añadir una especificación de API e invocar un servicio REST con {{site.data.keyword.Bluemix_notm}}
{: #tut_add_openapi_rest_bm}

**Duración**: 15 minutos  
**Nivel de habilidad**: Principiante  

## Objetivo
{: #object_tut_add_openapi_rest_bm}

Esta guía de aprendizaje le ayuda a comenzar rápidamente con {{site.data.keyword.apiconnect_full}}. Creará una nueva API en pocos minutos que actúe como un proxy de API de paso a través de un servicio REST existente.  La API que crea proporciona seguridad y supervisión.

## Requisito previo
{: #prereq_tut_add_openapi_rest_bm}

Antes de empezar, necesita [configurar la instancia de API Connect](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_set_up_apic_instance).

---

### Explorar la app de ejemplo y probar los puntos finales de destino
{: #expl_tut_add_openapi_rest_bm}

Se ha creado una app _weather provider_ de ejemplo para esta guía de aprendizaje.
1. Para explorar la app, vaya a [http://gettingstartedweatherapp.mybluemix.net/ ![Icono de enlace externo](../../../icons/launch-glyph.svg "Icono de enlace externo")](http://gettingstartedweatherapp.mybluemix.net/){: #new_window}.  
2. Especifique un código postal de Estados Unidos de 5 dígitos válido para obtener el _**tiempo actual**_ y la _**previsión de hoy**_.  
![](images/explore-weatherapp-1.png)

3. La app de tiempo de ejemplo anterior se ha creado utilizando API que proporcionan los datos meteorológicos. El punto final para obtener los datos meteorológicos **actuales** es _**https://myweatherprovider.mybluemix.net/current?zipcode={zipcode}**_. Pruébelo visitando [https://myweatherprovider.mybluemix.net/current?zipcode=90210 ![Icono de enlace externo](../../../icons/launch-glyph.svg "Icono de enlace externo")](https://myweatherprovider.mybluemix.net/current?zipcode=90210){: #new_window}.  

  ![](images/explore-weatherapp-2.png)

4. Asimismo, el punto final para obtener los datos de previsión **de hoy** es _**https:// myweatherprovider<span></span>.mybluemix.net/today?zipcode={zipcode}**_. Pruébelo yendo a [https://myweatherprovider.mybluemix.net/today?zipcode=90210 ![Icono de enlace externo](../../../icons/launch-glyph.svg "Icono de enlace externo")](https://myweatherprovider.mybluemix.net/today?zipcode=90210){: #new_window}.  

  ![](images/explore-weatherapp-3.png)


---

### Añadir una nueva especificación de OpenAPI parar crear un proxy de API REST  
{: #add_spec_tut_add_openapi_rest_bm}

1. Inicie sesión en {{site.data.keyword.Bluemix_short}}: https://cloud.ibm.com.
2. En el **Panel de control** de {{site.data.keyword.Bluemix_notm}}, pulse **Servicios de Cloud Foundry**. Inicie el servicio {{site.data.keyword.apiconnect_short}}. 
3. En {{site.data.keyword.apiconnect_short}}, asegúrese de que el panel de navegación está abierto. Si no lo está, pulse **>>** para abrirlo.  

  ![](images/cloud-apic-dashboard.png)

4. Seleccione **Borradores** en el panel de navegación.
5. En el separador **API**, pulse **Añadir**. Desde el menú desplegable, seleccione **Nueva API**.    
  ![](images/cloud-add-api-new.png)  
6. En la ventana *Nueva API*, especifique `Nueva API de Weather Provider` para el título.
_El Nombre y la Vía de acceso base se rellenan automáticamente_.  
  ![](images/bluemix-add-new-api2.png)
7. Pulse **Crear API** para completar el asistente.  
8. Después de crear la API, se seleccionará el separador **Diseño**. 
9. Desplácese al panel **Host**. Escriba `$(catalog.host)` como el valor si el campo no se rellena automáticamente.
10. En el panel **Vía de acceso base**, anote el valor rellenado automáticamente: `/new-weather-provider-api`. El URL de destino de la API se creará a partir de estos valores.  


11. Ahora debe definir el objeto de respuesta que se devuelve cuando se invoca la API meteorológica. Para ello, pulse **Definiciones** en la barra de navegación.   
    a. Añada una nueva definición.  
    b. Asigne un nombre a la nueva definición _Actual_.  
    c. Establezca el Tipo en _Objeto_.  
    d. Añada nuevas propiedades para la definición **Actual**.    
       - Nombre: código postal         /  Tipo: serie   
       - Nombre: temperatura /  Tipo: entero   
       - Nombre: humedad    /  Tipo: entero   
       - Nombre: ciudad        /  Tipo: serie   
       - Nombre: estado       /  Tipo: serie   
	   
    ![](images/definition-current-1.png)   
	
    e. Guarde la API.  

12. Cree una nueva definición: **Hoy**.

13. Añada nuevas propiedades para la definición **Hoy**.
    - Nombre: código postal / Tipo: serie
    - Nombre: hi / Tipo: entero
    - Nombre: lo / Tipo: entero
    - Nombre: nightHumidity / Tipo: entero
    - Nombre: dayHumidity / Tipo: entero
    - Nombre: ciudad / Tipo: serie
    - Nombre: estado / Tipo: serie

14. Con los formatos de datos definidos, podemos crear vías de acceso de invocación.  En la barra de navegación, pulse **Vías de acceso**. Cree una nueva vía de acceso pulsando **+**.     
    a. Dé un nombre a la nueva vía de acceso "**/current**".  
    b. En el mismo panel *Vías de acceso*, seleccione la sección **GET /current**.    
    c. En la sección **GET /current**, añada un nuevo **Parámetro**. Como ha percibido al explorar la app de ejemplo, el servicio meteorológico necesita un código postal como parámetro.   
      - Nombre: código postal  
      - Ubicado en: Consulta  
      - Obligatorio: Sí  
      - Tipo: serie   
	  
    ![](images/path-current-1.png)   
	
    d. Desplácese hacia abajo.  En la sección **Respuestas**, cambie el **ESQUEMA** a _Actual_.  
	
	![](images/path-current-responses.png)
	
	e. Guarde la API.  

15. Repita las acciones que realizó en el paso 11 para crear otra vía de acceso denominada "**/today**".  En este caso, establezca el esquema de **Respuestas** en _Actual_.  Guarde la API.

16. Guarde la API.

17. Cambie al separador **Ensamblar**. Ha creado dos operaciones hasta ahora: **GET /current** y **GET /today**. Para garantizar que se invoca el punto final de destino correcto, deberá crear la lógica que ejecutará supeditada a la operación que se llama. Vamos a utilizar la construcción lógica **Conmutador de funcionamiento** para hacerlo.  El **Conmutador de funcionamiento** proporciona un punto de decisión. Basándose en el par verbo/vía de acceso, deberá invocarse la operación apropiada.

    a. Suprima la política de **invocación** que ya se puede añadir al _lienzo_.  
    b. Desde la paleta, arrastre el **Conmutador de funcionamiento** y suéltelo en el lienzo.  
      - Para **caso 0**, asigne la operación **get /current**.
      - Añada un nuevo caso: **caso 1**.
      - Asigne la operación **get /today** a **caso 1**.
	  
	  
      ![](images/new-assemble-1.png)
	  
    c. Arrastre la política de **invocación** desde la paleta y suéltela en la línea de proceso debajo de **get /current**. _La acción de invocación se utiliza para llamar un servicio anterior desde dentro de una operación_.   
    d. Actualice el título de la acción a "**invoke-current**".  
    e. Actualice el campo URL con `https://myweatherprovider.mybluemix.net/current?zipcode=$(request.parameters.zipcode)`.  
	
	![](images/new-assemble-invoke1.png)
	
	
	f. Arrastre la política de **invocación** desde la paleta y suéltela en la línea de proceso debajo de **get /today**. 
    g. Actualice el título a "**invoke-today**".  
    h. Actualice el campo URL con `https://myweatherprovider.mybluemix.net/today?zipcode=$(request.parameters.zipcode)`.  
	
       ![](images/new-assemble-invoke2.png)
	   

18. Cierre el panel de configuración de la acción.  Guarde la API.

---

### Probar el proxy de la API
{: #test_proxy_tut_add_openapi_rest_bm}

1. En el separador **Ensamblar**, pulse el icono de más acciones, y luego seleccione **Generar un producto predeterminado**.  
   ![](images/generate-default-product-small.png) 

2. Acepte las opciones predeterminadas del recuadro de diálogo **Nuevo producto**, y pulse **Crear producto**. Se creará el producto de la API de Weather Provider y se publicará en el catálogo del recinto de pruebas. Se mostrará un mensaje que indica la generación correcta del producto.  

  ![](images/generate-default-product-new-weather.png) 

  - _En {{site.data.keyword.apiconnect_short}}, **Productos** proporcione una forma para agrupar API pensadas para un uso concreto. Los productos se publican en un **Catálogo**. [Glosario de {{site.data.keyword.apiconnect_short}}](../apic_glossary.html)_

3. En el separador Ensamblar, pulse el icono de reproducción para probar la invocación de destino del proxy de la API.

4. En el panel de prueba, seleccione la operación **get /current**.

	a. El código postal es un parámetro obligatorio para esta operación, por lo que especifique un código postal de Estados Unidos válido (p. ej., 10504). 
	
	![](images/test-invoke-params.png)  
		
	b. Pulse **Invocar**.   

	_Si ejecuta en un error de CORS, siga las instrucciones del mensaje de error. Pulse el enlace del error para añadir la excepción a su navegador, y a continuación pulse el botón "invocar" de nuevo._
  
    ![](images/test-invoke-new.png)  


---

### Conclusión
{: #conclusion_tut_add_openapi_rest_bm}

En esta guía de aprendizaje, ha aprendido cómo se puede invocar un servicio REST anterior mediante un proxy de paso a través de la API. Ha comenzado comprobando la disponibilidad del servicio de ejemplo mediante el explorador web. A continuación, ha creado una nueva especificación de OpenAPI en {{site.data.keyword.apiconnect_short}}, y la ha enlazado al servicio de ejemplo que se invocará. Ha empaquetado la API en un producto, ha publicado el producto en el catálogo y ha probado el proxy.

---

## Paso siguiente
{: #next_tut_add_openapi_rest_bm}

Proteger la API utilizando [protección utilizando OAuth 2.0](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_oauth_2).

Crear > **Gestionar** > Proteger > Socializar > Analizar
