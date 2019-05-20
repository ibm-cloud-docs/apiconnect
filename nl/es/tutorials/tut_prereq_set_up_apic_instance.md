---

copyright:
  years: 2019
lastupdated: "2019-3-14"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorials

subcollection: apiconnect

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Configuración de una instancia de API Connect
{: #tut_prereq_set_up_apic_instance}

**Duración**: 15 minutos  
**Nivel de habilidad**: Principiante  


## Requisitos previos
{: #prereq_tut_prereq_set_up_apic_instance}

1. Un IBMid
2. Una cuenta de {{site.data.keyword.Bluemix_short}}
3. Una instancia de {{site.data.keyword.apiconnect_full}} con al menos un plan _Lite_


<table>
  <tr><td><b>IBMid</b>: Se utiliza para acceder a todas las apps, comunidades, soporte, etc., de IBM
    <br>
    <b>{{site.data.keyword.Bluemix_notm}}</b>: La plataforma de nube de IBM que aloja a {{site.data.keyword.apiconnect_short}} junto con otras apps y servicios<br>
    <b>{{site.data.keyword.apiconnect_short}} Lite</b>: Una versión gratuita de {{site.data.keyword.apiconnect_short}} alojada en {{site.data.keyword.Bluemix_notm}}</td></tr>
  </table>  


---


1. Regístrese para obtener un ID de IBM Cloud en el siguiente URL: [https://cloud.ibm.com/registration/ ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/registration/){: #new_window}.

	¿Ya tiene un IBMid? Entonces, omita el registro, y tan sólo cree su cuenta gratuita de {{site.data.keyword.Bluemix_short}} en el siguiente URL: [https://cloud.ibm.com/ ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/){: #new_window}.  

2. Cuando tenga su IBMid y su cuenta de {{site.data.keyword.Bluemix_notm}}, cree la instancia de {{site.data.keyword.apiconnect_short}}.  
  a. Inicie sesión en {{site.data.keyword.Bluemix_notm}}: [https://cloud.ibm.com/login ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/login){: #new_window}.  
  ![](images/cloud_login_page.png)  
  b. Cree su _organización_ en {{site.data.keyword.Bluemix_notm}}. Se le solicitará que haga esto la primera vez que inicie sesión.  
  ![](images/prereqs-2.png)
  c. Cree su _espacio_.  
  ![](images/prereqs-3.png)
  d. Vaya a [https://console.ng.bluemix.net/catalog/services/api-connect ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://console.ng.bluemix.net/catalog/services/api-connect){: #new_window}.  
  ![](images/prereqs-4.png)  
  e. Seleccione el plan de precios de _Lite_ (gratuito), y pulse **Crear** para empezar.  
  ![](images/lite-plan.png)  
