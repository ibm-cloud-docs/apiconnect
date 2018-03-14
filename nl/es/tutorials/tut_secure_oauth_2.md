---
copyright:
  years: 2017
lastupdated: "2017-12-13"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Protección de la API con OAuth de dos vías

Duración: 10 minutos  
Nivel de habilidad: Principiante

## Objetivo

Esta guía de aprendizaje le guiará por la protección de la API utilizando un flujo de OAuth 2.0 de dos vías. En este flujo de aplicaciones, el cliente de OAuth inicia una solicitud con el servidor de autorización, y ha recibido una señal de acceso. El cliente de OAuth podrá entonces utilizar la señal para acceder a los recursos protegidos mediante la API.

## Requisitos previos

Antes de empezar, debe haber completado la siguiente guía de aprendizaje.  
- [Protección de una API con las claves Client-ID y Client-Secret con {{site.data.keyword.Bluemix}}](tut_secure_id_secret_bm.html)
o
- [Protección de una API con las claves Client-ID y Client-Secret con Toolkit](tut_secure_id_secret_tk.html)

Nota: en esta guía de aprendizaje se muestran los pasos y las capturas de pantalla para completar la tarea en la interfaz de usuario de {{site.data.keyword.Bluemix}}. También puede realizar el mismo procedimiento utilizando la línea de mandatos. Puede consultar el procedimiento en el [IBM Knowledge Center](https://www.ibm.com/support/knowledgecenter/SSMNED_5.0.0/com.ibm.apic.toolkit.doc/tutorial_apionprem_security_OAuth_v506.html). 

## Procedimiento

1. Cree una API de proveedor de OAuth y seleccione el esquema de OAuth.  
	a. Abra **Borradores**, seleccione **API**, y pulse **Añadir** > **API de proveedor de OAuth 2.0**.  
    ![](images/oauth_provider_1.png)
	b. Titúlelo "API de punto final de OAuth". El nombre y la vía de acceso base se deben rellenar automáticamente.  
	c. Seleccione **Crear API**.  
	d. En la API de punto final de OAuth recién creada, navegue hasta el panel **OAuth 2** (o desplácese hasta él), y seleccione "Confidencial" como Tipo de cliente.  
	e. En Ámbitos, cambie el nombre de _scope1_ a _view_current_. Suprima _scope2_ y _scope3_.  
	f. En **Concesiones**, deseleccione **Implícito**, **Contraseña** y **Código de acceso**. Deje **Aplicación** seleccionado.  
	![](images/oauth_provider_2.png)  
	g. Guarde la API.  

2. Actualice la definición de seguridad de Weather Provider API para incluir OAuth.  
	a. Conmute a _Weather Provider API_. (Vuelva a las API y seleccione _Weather Provider API_).  
	b. En Definiciones de seguridad, añada una nueva definición para OAuth. Dele el nombre "Definición de OAuth".  
	c. En el campo Flujo, seleccione **Aplicación**.  
	d. Especifique el URL de señal _<su URL base>/oauth-endpoint-api/oauth2/token_.  
	e. Añada un nuevo ámbito: view_current.  
	![](images/oauth_security_definition_1.png)
	f. En **Seguridad**, seleccione **Definición de OAuth** y **view_current**, y mantenga seleccionado el ID de cliente y el Secreto de cliente.  
	![](images/oauth_security_definition_2.png)
	g. Pulse Guardar.  
	h. Vaya a **Borradores** y seleccione **Productos**. Añada la API de punto final de OAuth al producto Weather Provider.  
	i. Guarde el producto, y transfiéralo al Recinto de pruebas.  
	![](images/oauth_security_definition_3a.png)

3. Pruebe la configuración de seguridad de OAuth.  
	a. Publique su producto actualizado al recinto de pruebas. Pulse **Panel de control > Recinto de pruebas**, y a continuación publique el producto.  
	  ![](images/test_oauth_1.png)
	b. Pulse **Explorar > Recinto de pruebas**.  
      ![](images/test_oauth_2.png)
	c. En **Weather Provider API**, pulse **GET /current** en la lista de operaciones.  
	d. En el panel de la derecha, observe que el ID de cliente y el Secreto de cliente ya estén rellenos.  
	e. En la sección **Parámetros**, escriba un código postal.  
      ![](images/test_oauth_3.png)
	f. En la sección **Autorización**, pulse **Autorizar** para obtener la señal de acceso.  
	g. Una vez que haya recibido la señal de acceso, pulse **Llamar operación** para completar la prueba.  
      ![](images/test_oauth_4.png)

4. Observe que la solicitud incluye la señal de acceso, el ID de cliente y el Secreto de cliente. Para pasar sólo la señal de acceso en la solicitud, deberá eliminar el ID y el Secreto de cliente de los requisitos de seguridad para Weather Provider API.  
    ![](images/test_oauth_5.png)

5. Guarde Weather Provider API. A continuación, transfiéralo y publíquelo en el Recinto de pruebas. Desde la herramienta Explorar, ejecute la misma prueba anterior.  
    ![](images/test_oauth_6.png)
    
## Conclusión
En esta guía de aprendizaje, ha aprendido a crear una API de proveedor de OAuth, a actualizar la definición de seguridad de una API para incluir OAuth, y a probar la configuración de seguridad.

---

## Paso siguiente

Empiece por socializar su API mediante [establecimiento y configuración de un portal del desarrollador](tut_config_dev_portal.html).

Crear > Gestionar > **Proteger** > Socializar > Analizar
