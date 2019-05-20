---

copyright:
  years: 2019
lastupdated: "2017-3-18"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial


---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Reemplazo de Productos de API
{: #tut_manage_supercede}

**Duración**: 15 minutos  
**Nivel de habilidad**: Principiante  

## Objetivo
{: #object_tut_manage_supercede}

En esta guía de aprendizaje, reemplazará una API anterior por una nueva.

---
## Requisitos previos
{: #prereq_tut_manage_supercede}

1. [Configurar la instancia de {{site.data.keyword.apiconnect_full}}](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_set_up_apic_instance).

2. Complete la [guía de aprendizaje Sustituir un producto de API](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_manage_replace).

---

## Reemplazo de un Producto de API
{: #super_tut_manage_supercede}

1. Inicie sesión en {{site.data.keyword.Bluemix_short}}: https://cloud.ibm.com.
2. En el **Panel de control** de {{site.data.keyword.Bluemix_notm}}, pulse **Servicios de Cloud Foundry**. Inicie el servicio {{site.data.keyword.apiconnect_short}}. 
3. En {{site.data.keyword.apiconnect_short}}, asegúrese de que el panel de navegación está abierto. Si no lo está, pulse **>>** para abrirlo.  

  ![](images/cloud-apic-dashboard.png)

4. Pulse **Borradores** > **API**.

5. En el panel API, pulse **API de Weather Provider** para abrir la API de proxy REST.  
![](images/rep-api-list.png)

6. Cambie la **Versión** a 3.0.0.

7. Pulse el icono de disco para guardar los cambios de la API.  
![](images/sup-change-version.png)

8. Pulse **Todas las API**.  
![](images/rep-all-apis.png)

9. Pulse **Productos**.  
![](images/sup-prods.png)

10.	Seleccione **Weather Provider API Product 2.0.0**.  
![](images/sup-draft-prod-list.png)

11.	Cambie la **Versión** a 3.0.0. Pulse en el icono de disco para guardar los cambios. Pulse el icono **Etapa**.  
![](images/sup-change-prod-vers-3.png)

12.	Pulse **>>** para abrir el panel de navegación y, a continuación, seleccione **Panel de control**.  
![](images/rep-dashboard.png)

13.	Pulse **Recinto de pruebas**.

14.	Pulse **Comunidad**.  
![](images/sup-sand-dash.png)

15.	Pulse **Suscripciones**.  
![](images/sup-comm-orgs.png)

16.	Observe las suscripciones a aplicación a Weather Provider API Product 2.0.0. Pulse **Productos**.
![](images/sup-scriptions-200.png)  

17.	Pulse los puntos suspensivos verticales en la línea **Weather Provider API Product 3.0.0 Staged**.  
![](images/sup-stage-prod-3.png)

18.	Seleccione **Reemplazar un producto existente**.  
![](images/sup-super-prod.png)

19.	Seleccione **Weather Provider API Product 2.0.0** en la lista de productos presentados. Pulse **Siguiente**.  
![](images/sup-super-dialog-1.png)

20.	Seleccione **Plan predeterminado**. Pulse **Reemplazar**.  
![](images/sup-super-dialog-2.png)
    Como consecuencia de esta sustitución, Weather Provider API Product 2.0.0 está en desuso, y se ha publicado Weather Provider API Product 3.0.0.  
![](images/sup-dash-prods-3.png) 
 
21.	Pulse **Comunidad >> Suscripciones**.  
![](images/sup-scriptions-200.png)
 
22.	Pulse los puntos suspensivos verticales en la línea **Weather Provider API Product 2.0.0**. Seleccione **Gestionar**.  
![](images/sup-dots-manage.png) 

23.	Seleccione **Plan predeterminado** en Weather Provider API Product 3.0.0. Pulse **Migrar**.  
![](images/sup-migrate-dialog.png)
    Como consecuencia de esta migración, Weather Provider API Product 2.0.0 se migra a Weather Provider API Product 3.0.0.  
![](images/sup-migrated.png) 
 

 
## Conclusión
{: #conclusion_tut_manage_supercede}

En esta guía de aprendizaje, ha completado las actividades siguientes:

1. Ha actualizado un producto de API.
2. Ha reemplazado un producto de API anterior por un producto de API actualizado.
3. Ha migrado la suscripción al producto de API anterior al producto de API actualizado.

---












