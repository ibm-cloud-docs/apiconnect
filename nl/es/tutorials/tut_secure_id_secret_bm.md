---

copyright:
  years: 2017
lastupdated: "2017-10-31"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorials

subcollection: apiconnect

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Protección de la API con el ID de cliente y el Secreto de cliente utilizando {{site.data.keyword.Bluemix_notm}}
{: #tut_secure_id_secret_bm}

**Duración:** 10 minutos  
**Nivel de habilidad:** Principiante


## Objetivo
{: #object_tut_secure_id_secret_bm}
Esta guía de aprendizaje le guiará en la protección de la API con el ID de cliente y el Secreto de cliente. Cuando las aplicaciones se registran en el Portal del desarrollador, un ID de cliente se genera para identificar la aplicación. Opcionalmente, un secreto de cliente, que sirve como contraseña, también puede generarse. Las aplicaciones necesitarían facilitar las claves del ID de cliente y del Secreto de cliente generados para acceder a la API.


## Requisitos previos
{: #prereq_tut_secure_id_secret_bm}

Antes de empezar, debe haber completado una de las siguientes guías de aprendizaje: 
- [Importar una especificación de OpenAPI2.0 y proxy en un servicio REST anterior](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_rest_landing)  
**o bien**  
- [Añadir una nueva especificación de API e invocar un servicio REST existente](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_rest_landing)


## Establecer el mecanismo de identificación de la API
{: #set_id_tut_secure_id_secret_bm}

1. Vaya a la vista Diseño de la API:  
   a. Pulse en **Borradores** en el panel de navegación izquierdo  
   b. A continuación, pulse en el separador **API**  
   c. Pulse en _Weather Provider API_ que ha creado en la guía de aprendizaje anterior. Esto abre la vista **Diseño** de la API.  
   ![](images/1_goto_drafts_api.png)  

2. En la vista Diseño:
    a. Desplácese hasta **Definiciones de seguridad**.  
    b. Pulse el icono **Añadir definiciones de seguridad** (+) y, a continuación, pulse **Clave de API**.  
    c. Añada las dos nuevas claves de API que se muestran a continuación. Para las dos nuevas claves, asegúrese de que el campo "Ubicado en" esté establecido en "Cabecera".  
      - Nombre: ID de cliente; Nombre de parámetro: X-IBM-Client-Id  
      - Nombre: Secreto de cliente; Nombre de parámetro: X-IBM-Client-Secret    
        ![](images/2_security_definitions.png)  

3. Desplácese hasta el panel **Seguridad** y añada una nueva opción de seguridad.  
    a. Seleccione las claves ID de cliente y Secreto de cliente recién creadas.  
    b. Guarde la API.  
    c. Cambie al separador **Ensamblar**.  
    ![](images/3_security_option.png)  


## Probar los cambios realizados en la API
{: #test_tut_secure_id_secret_bm}

1. En el separador Ensamblar, pulse el botón ► para probar los cambios.

2. En el panel Prueba / Configuración, pulse **Volver a publicar producto** para obtener los cambios más recientes. 
> Esta opción actualiza el producto de la API, y también lo publica en el catálogo del recinto de pruebas.

3. Una vez que se haya vuelto a publicar el producto, pulse en la operación **get /current** en el panel de pruebas.
4. Desplácese hacia abajo en el panel de pruebas, y observe que los valores ID de cliente y Secreto de cliente ya se hayan rellenado. 
> Estos son valores de prueba generados para su recinto de pruebas, y representan las claves de la aplicación que la API utilizará.
> **Nota:** Las claves ID de cliente y Secreto de cliente también se pueden encontrar en Panel de control > Catálogo > Configuración > Puntos finales]_   
  
  ![](images/test_api_keys_1.png)

5. Desplácese más abajo y especifique un código postal (p. ej. 90210). 
6. Pulse **Invocar**. _Debería obtener una respuesta 200 Aceptar, junto con el cuerpo del mensaje que devuelve la información meteorológica._
7. Ahora, desplácese de nuevo hacia arriba al campo ID de cliente. 
8. Sustituya el valor ID de cliente por uno aleatorio.
9. Vuelva a ejecutar la prueba pulsando **Invocar**. _Verá una respuesta 401 Unauthorized, junto con el mensaje "ID de cliente no registrado"._  

    ![](images/test_api_keys_3.png)  


## Llame a la API utilizando el ID de cliente y el Secreto de cliente
{: #call_tut_secure_id_secret_bm}

Los valores de seguridad también puede se pueden probar utilizando la herramienta Explorar que explícitamente llama al punto final de proxy, y pasa las claves ID de cliente y Secreto de cliente como valores de cabecera.

1. Pulse **Explorar** y, a continuación, pulse **Recinto de pruebas**.
    ![](images/explore_1.png)

2. Pulse en la operación **GET /current** de la lista.

3. En la columna de la derecha, pulse **Llamar operación** para volver a ejecutar la prueba.
    ![](images/explore_3.png)

---

## Conclusión
{: #conclusion_tut_secure_id_secret_bm}

En esta guía de aprendizaje, ha aprendido a establecer el mecanismo de identificación de la API, a probar los cambios realizados en la API, y a llamar a la API mediante el ID de cliente y el Secreto de cliente. 

---

## Paso siguiente
{: #next_tut_secure_id_secret_bm}

Empiece por socializar su API mediante [establecimiento y configuración de un portal del desarrollador](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_config_dev_portal).

Crear > Gestionar > **Proteger** > Socializar > Analizar
