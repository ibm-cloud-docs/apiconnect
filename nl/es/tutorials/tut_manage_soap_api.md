---

copyright:
  years: 2019
lastupdated: "2019-3-11"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# Gestión de un servicio de SOAP
{: #tut_manage_soap_api}

**Duración**: 15 minutos
**Nivel de habilidad**: Principiante

---
## Objetivo
{: #object_tut_manage_soap_api}

En esta guía de aprendizaje, utilizará la API Manager para crear una API SOAP que es un proxy para un servicio meteorológico basado en SOAP.

## Requisitos previos
{: #prereq_tut_manage_soap_api}

- Antes de empezar, deberá [configurar la instancia de {{site.data.keyword.apiconnect_short}}](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_set_up_apic_instance).
- Antes de empezar, copie el archivo de [prueba weatherprovider.wsdl ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://raw.githubusercontent.com/IBM-Bluemix-Docs/apiconnect/master/tutorials/weatherprovider.wsdl){: #new_window} en el sistema de archivos local.
Nota: Puede pulsar **Sin procesar** y, a continuación, guardar la página resultante en el sistema local como un archivo `.wsdl`. Como el nombre sugiere, este servicio SOAP devuelve datos meteorológicos cuando se proporciona un código postal.

---
## Configuración de una definición de API SOAP
{: #setup_tut_manage_soap_api}

1. Inicie sesión en {{site.data.keyword.Bluemix_short}}: https://cloud.ibm.com.
2. En el **Panel de control** de {{site.data.keyword.Bluemix_notm}}, pulse **Servicios de Cloud Foundry**. 
3. Inicie el servicio {{site.data.keyword.apiconnect_short}}. 
4. En {{site.data.keyword.apiconnect_short}}, asegúrese de que esté abierto el panel de navegación del lado izquierdo. Si no lo está, pulse **>>** para abrirlo.  
5. Seleccione **Borradores** en el panel de navegación.   

6. En el menú desplegable, seleccione **API de un servicio SOAP**.
  ![Nueva API](images/newapi-menu2.png)

7. Se abrirá la nueva API desde el recuadro de diálogo WSDL. Pulse **Cargar archivo**.
  ![cargar el archivo .wsdl](images/4-uploadwsdl.png)

8. Seleccione el archivo `weatherprovider.wsdl` que ha guardado anteriormente.

9. Reaparecerá el recuadro de diálogo Nueva API de WSDL. Marque el recuadro de selección **weatherService**. Pulse **Listo**.
  ![seleccionar servicio meteorológico](images/newapi2.png)

10. Tras la importación correcta, se le dirigirá a la vista Diseño de la API. Además, puede ver la definición de OpenAPI en el separador Origen.
   _En el separador Origen, verá que el WSDL está envuelto dentro de la definición de OpenAPI._
  ![Página API Editor](images/designpage2.png)

11. Pulse el icono ![guardar](images/save.png) para guardar los cambios. Aparecerá momentáneamente una notificación de confirmación "API guardada".

12. En la barra de menús con el icono de guardar, el separador **Diseño** indicará la ubicación actual. Junto a esto, se encuentra el separador **Origen** donde puede ver directamente el archivo de Swagger (2.0) que representa la API, y después de ello, encontrará el separador **Ensamblar** que le lleva a una interfaz de arrastrar y soltar para el proceso de la API. Pulse **Ensamblar**.
  ![separador Ensamblar](images/assemble-clean.png)  

## Probar la definición de la API SOAP
{: #test_tut_manage_soap_api}

1. En el separador **Ensamblar**, pulse el icono **Más acciones** (tres puntos), y seleccione **Generar un producto predeterminado** en el menú.  
   ![menú Más acciones, abrir](images/gen-default-prod.png)

2. Acepte las opciones predeterminadas de la ventana emergente de diálogo **Nuevo producto**, y seleccione **Crear producto**. Se creará el **weatherService product 1.0.0** y se publicará en el catálogo del Recinto de pruebas.  
  ![crear un producto nuevo](images/12a-chooseproduct.png)
 
  _En {{site.data.keyword.apiconnect_short}}, **Productos** proporciona un mecanismo para agrupar API pensadas para un uso concreto. Los productos se publican en un **Catálogo**. Referencia: [Glosario de {{site.data.keyword.apiconnect_short}}](docs/services/apiconnect/tutorials/tut_expose_soap_service/apic_glossary.html)_

3. Guarde los cambios.  

4. Junto al recuadro de búsqueda, pulse el icono de prueba para probar el servicio de API. Aparecerá el menú Configuración.

5. En la lista de Productos, seleccione `weatherService product 1.0.0`.  
  ![seleccionar servicio meteorológico](images/12-chooseproduct.png)

6. Desplácese a la parte inferior y pulse **Siguiente**.

7. En la lista de operaciones, seleccione `post /weatherRequest`.  
  ![publicar una solicitud](images/13-selectoperation.png)

8. Desplácese hacia abajo. Escriba el siguiente xml en el campo body. Puede seleccionar y copiar el XML de ejemplo siguiente y, a continuación, pulsar el campo **body** para activar el campo y colocar el XML de ejemplo.  
  ```
  <?xml version="1.0" encoding="UTF-8"?>
  <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
  <wdata:WeatherRequest xmlns:wdata="http://www.ibm.com/wdata">
       <zipcode>10504</zipcode>
  </wdata:WeatherRequest>
   </soap:Body>
  </soap:Envelope>
  ```
 
  ![la solicitud](images/14-enterrequest.png)

9. Desplácese si es necesario, y pulse **Invocar**.
La API devuelve un **body** de respuesta que consta del tiempo actual.  
  ![](images/15-success.png)

## Conclusión
{: #conclusion_tut_manage_soap_api}

En esta guía de aprendizaje, ha realizado lo siguiente:
1. Ha configurado una definición de API SOAP
2. Ha probado la definición de API
3. Ha recibido un **body** de respuesta del punto final de la API de tiempo que indica el resultado de la solicitud.

---

## Paso siguiente
{: #next_tut_manage_soap_api}

[Exponer el servicio como una API REST](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_expose_soap_service) o proteger la API utilizando [protección utilizando OAuth 2.0](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_oauth_2).

Crear > **Gestionar** > Proteger > Socializar > Analizar
