---

copyright:
  years: 2019
lastupdated: "2019-3-14"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Protección de la API con OAuth de dos vías
{: #tut_secure_oauth_2}

Duración: 10 minutos  
Nivel de habilidad: Principiante

## Objetivo
{: #object_tut_secure_oauth_2}

Esta guía de aprendizaje le guiará por la protección de la API utilizando un flujo de OAuth 2.0 de dos vías. En este flujo de aplicaciones, el cliente de OAuth inicia una solicitud con el servidor de autorización, y ha recibido una señal de acceso. El cliente de OAuth podrá entonces utilizar la señal para acceder a los recursos protegidos mediante la API.

## Requisitos previos
{: #prereq_tut_secure_oauth_2}

Antes de empezar, debe haber completado la siguiente guía de aprendizaje.  
- [Protección de una API con las claves Client-ID y Client-Secret con {{site.data.keyword.Bluemix}}](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_id_secret_bm)
o
- [Protección de una API con las claves Client-ID y Client-Secret con Toolkit](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_id_secret_tk)

Nota: en esta guía de aprendizaje se muestran los pasos y las capturas de pantalla para completar la tarea en la interfaz de usuario de {{site.data.keyword.Bluemix}}. También puede realizar el mismo procedimiento utilizando la línea de mandatos. Puede consultar el procedimiento en el [IBM Knowledge Center ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SSMNED_5.0.0/com.ibm.apic.toolkit.doc/tutorial_apionprem_security_OAuth_v506.html){: #new_window}. 

## Procedimiento
{: #steps_tut_secure_oauth_2}

1. Cree una API de proveedor de OAuth y seleccione el esquema de OAuth.  
	a. Abra **Borradores**, seleccione **API**, y pulse **Añadir** > **API de proveedor de OAuth 2.0**.  
    ![](images/oauth_provider_1.png)
	b. Titúlelo "API de punto final de OAuth". El nombre y la vía de acceso base se deben rellenar automáticamente.  
	c. Seleccione **Crear API**.  
	d. En la API de punto final de OAuth recién creada, navegue hasta el panel **OAuth 2** (o desplácese hasta él), y seleccione "Confidencial" como Tipo de cliente.  
	e. En Ámbitos, cambie el nombre de _scope1_ a _view_current_. Suprima _scope2_ y _scope3_.  
	![](images/oauth_provider_type_scope.png) 
	
	f. En **Concesiones**, deseleccione **Implícito**, **Contraseña** y **Código de acceso**. Deje **Aplicación** seleccionado.  
	![](images/oauth_provider_grants.png)  
	
	g. Guarde la API.  

2. Actualice la definición de seguridad de Weather Provider API para incluir OAuth.  
	a. Cambie a su _Weather Provider API_. (Vuelva a las API y seleccione _Weather Provider API_).  
	![](images/oauth_weatherapi_info.png)
	
	b. En Definiciones de seguridad, pulse el icono **+** y añada una nueva definición para OAuth.
	![](images/oauth_add_security.png)
	c. Establezca el nombre "Definición de OAuth".  
	d. En el campo Flujo, seleccione **Aplicación**.  
	e. Especifique el URL de señal _**su URL base**/oauth-endpoint-api/oauth2/token_.  
	![](images/oauth_secdef_top.png)
	
	f. Añada un nuevo ámbito: view_current.  
	![](images/oauth_secdef_scopes.png)
	g. En **Seguridad**, seleccione **Definición de OAuth** y **view_current**, y mantenga seleccionado el ID de cliente y el Secreto de cliente.  
	![](images/oauth_security_oauth.png)
	
	h. Pulse Guardar.  
	
	i. Vaya a **Borradores** y seleccione **Productos**.  Abra el **Producto de API de Weather Provider**.
	![](images/weatherapi_prod_info.png)
	
	j. Pulse **API** en la barra de navegación. Pulse el icono **+** y añada una nueva API. Añada la API de punto final de OAuth al producto Weather Provider.  
	![](images/weatherapi_prod_apis.png)
	k. Guarde el producto, y transfiéralo al Recinto de pruebas.  
	![](images/oauth_security_definition_3a.png)

3. Pruebe la configuración de seguridad de OAuth.  
	a. Publique su producto actualizado al recinto de pruebas. Pulse **Panel de control > Recinto de pruebas**, y a continuación publique el producto.  
	  ![](images/test_oauth_1.png)
	b. Acepte los valores predeterminados en el diálogo Visibilidad.  Pulse **Publicar**.
	![](images/pub_visibility.png)
	  
	c. Pulse **Explorar > Recinto de pruebas**.  
      ![](images/test_oauth_2.png)
	d. En **Weather Provider API**, pulse **GET /current** en la lista de operaciones. 
	
	e. Pulse **Pruébelo**. 
	
	f. En el panel de la derecha, observe que el ID de cliente y el Secreto de cliente ya estén rellenos.  
	
	g. En la sección **Parámetros**, escriba _10504_ en el campo **zipcode**.  
	  ![](images/weather_oauth_explorer_param.png)
	
	h. En la sección **Autorización**, pulse **Autorizar** para obtener la señal de acceso.
	  ![](images/weather_oauth_explorer_auth.png)
	
	i. Una vez que haya recibido la señal de acceso, pulse **Llamar operación** para completar la prueba.  
      ![](images/test_oauth_4.png)

4. Observe que la solicitud incluye la señal de acceso, el ID de cliente y el Secreto de cliente. Para pasar sólo la señal de acceso en la solicitud, deberá eliminar el ID y el Secreto de cliente de los requisitos de seguridad para Weather Provider API.  
    ![](images/test_oauth_5.png)

5. Guarde Weather Provider API. A continuación, transfiéralo y publíquelo en el Recinto de pruebas. Desde la herramienta Explorar, ejecute la misma prueba anterior.  
    ![](images/test_oauth_6.png)
    
## Conclusión
{: #conclusion_tut_secure_oauth_2}

En esta guía de aprendizaje, ha aprendido a crear una API de proveedor de OAuth, a actualizar la definición de seguridad de una API para incluir OAuth, y a probar la configuración de seguridad.

---

## Paso siguiente
{: #next_tut_secure_oauth_2}

Empiece por socializar su API mediante [establecimiento y configuración de un portal del desarrollador](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_config_dev_portal).

Crear > Gestionar > **Proteger** > Socializar > Analizar
