---

copyright:
  years: 2017
lastupdated: "2017-09-28"

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Novedades

La {{site.data.keyword.apiconnect_full}} incluye las mejoras siguientes:

- **Se ha añadido soporte y una referencia para las API REST de Developer Portal para analíticas**: las API REST de Developer Portal le ayudan a analizar las API de catálogo. Para obtener más información, consulte [Analytics ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/analytics.html){:new_window}.

- **Se ha añadido la sección Analytics al crear una API**: Puede definir y especificar parámetros existentes para la API que se pueden utilizar para recopilar datos analíticos
sobre la API. Consulte [Cómo componer una definición de API REST ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html){:new_window} para obtener más información.

- **Se fomenta el uso de la autenticación de dos factores en el Developer Portal**: Puede alentar a los usuarios del Developer Portal a configurar la autenticación de dos factores (TFA) en
su cuenta aplicando un módulo de TFA Rules. Para obtener más información, consulte [Alentar a los usuarios a configurar la autenticación de dos factores en su cuenta de Developer Portal ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapim_portal_two_factor_auth_enforce.html){:new_window}.

- **Características añadidas a la facturación integrada y a la gestión de pago**:
    Administrador:
	* Crear planes de suscripción de facturación prepago mensual a los que se pueden suscribir los clientes de API con una tarjeta de crédito. Consulte [Facturación para el uso de los productos ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/capim_product_billing.html){:new_window} para obtener más información.
	* Aproveche una cuenta de Stripe para gestionar el pago de las suscripciones.
	* Especifique un número de días de prueba gratuita en el plan de suscripción para nuevos suscriptores. El pago comienza automáticamente una vez que caduquen los días de prueba.
	Cliente:
	* Suscríbase a los planes de pago del Developer Portal que le permiten utilizar productos que contienen una o varias API. Consulte [Guía de aprendizaje: Suscripción a un plan de precios de ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tutorial_portal_sub_paid_plan.html){:new_window} para obtener más información.

- **Invocar lo sustituido automáticamente en la pasarela**: La última invocación de su política se podría sustituir mediante un proxy. Esto lo realiza la pasarela automáticamente para mejorar el rendimiento. Para obtener más información, consulte: [Propiedades de API de ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){:new_window}.

- **El ámbito de OAuth se puede modificar mediante respuestas de terceros**: Puede configurar un servidor externo para sustituir el valor de ámbito de la API. Para obtener más información, consulte: [Ámbito de ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/con_oauth_scope.html){:new_window}.

- **Nuevos campos de sucesos de la API**: Se han añadido los siguientes campos de sucesos de la API:
    * billing.trial_period_days
	* billing.amount
	* billing.currency
	* billing.model
	* billing.provider
	* client_id
	* immediate_client_ip
	* latency_info2.task
	* latency_info2.ended

Consulte [Campo de registro de sucesos de la API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/rapim_analytics_apieventrecordfields.html){:new_window} y [Cómo obtener datos analíticos mediante llamadas de API REST ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/tapim_exportanalytics_api_calls.html){:new_window} para obtener más información.

- **Nuevos parámetros de consulta para el URL de redirección**: Se han añadido nuevos parámetros de consulta a la información disponible para un tercero. Los nuevos parámetros son <code>provider</code>, <code>providerid</code>, y
<code>g-transid</code>. Para obtener más información, consulte [Autenticación y autorización a través de un URL de redirección ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_redirect_form_.html){:new_window}.

- **Cómo evitar alertas de CORS del navegador en la herramienta de prueba**: La herramienta API Designer Test envía solicitudes desde el navegador que pueden desencadenar alertas de CORS. Para evitar
alertas CORS, se proporciona el recuadro de selección **Habilitar proxy** para enviar mensajes de prueba desde el servidor que aloja API Designer en lugar del navegador. Para obtener más información,
consulte [Cómo probar una API con la herramienta de prueba de API Designer ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_toolkit_testing.html){:new_window}.

- **API seguras con OAuth de terceros en lugar de Mobile First Foundation**: Proteja la API con un proveedor OAuth de terceros en lugar del servidor de autorizaciones de IBM MobileFirst&tm; Platform Foundation. Para obtener más información,
consulte [Cómo integrar el proveedor OAuth de terceros ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/con_oauth_introspection.html){:new_window}.

- **Proteger las API con OpenID Connect (OIDC)**: Puede proteger las API con OpenID Connect(OIDC) mediante
una API de proveedor de OAuth de muestra suministrado anteriormente que puede personalizar de acuerdo con la configuración de OIDC. Para obtener más información, consulte [Cómo proteger las API con OpenID Connect ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/tapic_sec_api_config_oidc.html){:new_window}.

- **La acción de actualización de SOAP ya no sobrescribe la API**: Al actualizar una API SOAP desde una definición de WSDL, sólo se sustituirán las secciones de la API afectadas
por el nuevo WSDL, el resto de las secciones permanecerán sin cambios. En releases anteriores, la acción de actualización
sobrescribió completamente la configuración de la definición de la API SOAP, incluidas todas las propiedades
de diseño y la configuración de ensamblaje. Para obtener más información, consulte [Cómo actualizar una API SOAP
![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/tapic_soap_update.html){:new_window}.

- **Utilizar Honeypot para la protección frente a spam en el Portal del desarrollador**: La protección de Honeypot proporciona mecanismos de seguridad para proteger al sitio del Portal del desarrollador del envío de formularios mediante robots de spam. Si se detecta actividad del robot de spam, se bloqueará el envío de formularios. Para obtener más información, consulte [Cómo utilizar Honeypot para la protección frente a spam ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapic_portal_honeypot.html){:new_window}.

- **Cómo utilizar el módulo Vistas en el Portal del desarrollador**: Cree nuevas vistas en el Portal del desarrollador, como por ejemplo listas de contenido de Productos, API y aplicaciones, utilizando el módulo de IU de Vistas. Para obtener más información, consulte [Cómo utilizar el módulo Vistas en el Portal del desarrollador ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/capic_portal_views.html){:new_window}.
