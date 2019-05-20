---

copyright:
  years: 2017-2019
lastupdated: "2018-05-23"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal

subcollection: apiconnect

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Novedades
{: #apic_029}

La {{site.data.keyword.apiconnect_full}} incluye las mejoras siguientes:


- **Se admiten nuevos casos de error en la construcción de detección de ensamblaje**: se admiten los siguientes casos de error nuevos en la construcción de detección en un ensamblaje de API: *BadRequestError*, *UnauthorizedError* y *ForbiddenError*. Consulte [Casos de error admitidos en detecciones de ensamblaje ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/ref_toolkit_catch_errors.html){: #new_window}.
- **Se ha añadido el parámetro de consulta useBytesSent a las API seleccionadas**: se ha añadido el parámetro *useBytesSent* que permite utilizar el campo de análisis *bytes_sent* para calcular el uso. Consulte [Devolver la información de uso de datos para todos los recursos utilizados por una aplicación determinada ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps__appID__data-usageGET.html){: #new_window}, [Devolver la información de uso de datos para todos los recursos utilizados por todas las aplicaciones en la organización determinada ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps_data-usageGET.html){: #new_window}, [Devolver el uso de datos combinado para todos los recursos utilizados por una aplicación determinada ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps__appID__data-usage_allGET.html){: #new_window} y [Devolver el uso de datos combinado para todos los recursos utilizados por una organización determinada ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_data-usage_allGET.html){: #new_window} para obtener más información.
**Puede codificar los caracteres + en los valores de parámetro de consulta del URL de destino de una política de invocación o proxy**: hay una nueva propiedad de API *x-ibm-gateway-queryparam-encode-plus-char*; si se define en un valor de *true*, todos los caracteres "+" de los valores de parámetro de consulta de target-url de las políticas de invocación y proxy se codifican como "%2F". En los releases anteriores, + siempre se codificaba como %2F. Ahora, el comportamiento predeterminado es no realizar la codificación. Consulte [Propiedades de API ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){: #new_window}.
- **Puede aplicar el analizador de JSON en la regla de respuesta para una política de invocación o proxy**: hay una nueva propiedad de API *x-ibm-gateway-api-enforce-response-limits*; al definir esta propiedad en un valor de *true*, se permite aplicar el analizador de JSON en la regla de respuesta. Si el tamaño del cuerpo de respuesta es mayor que el límite del analizador de JSON definido en el dominio DataPower, se devuelve el código de estado 500. Consulte [Propiedades de API ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){: #new_window}.
- **Potencial de mejora de rendimiento en la política de correlaciones**: hay una nueva propiedad de API *x-ibm-gateway-optimize-schema-definition* que permite proporcionar una mejora de rendimiento para la política de correlaciones cuando una definición de salida de política hace referencia a una definición de esquema muy compleja. Consulte [Propiedades de API ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){: #new_window}.
