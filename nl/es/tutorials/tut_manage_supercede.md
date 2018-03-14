---

copyright:
  years: 2017
lastupdated: "2017-10-31"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Reemplazo de Productos de API
**Duración**: 15 minutos  
**Nivel de habilidad**: Principiante  

## Requisitos previos

1. [Configurar la instancia de {{site.data.keyword.apiconnect_full}}](tut_prereq_set_up_apic_instance.html).

2. Complete la [guía de aprendizaje Sustituir un producto de API](tut_manage_replace.html).

---
## Objetivo
En esta guía de aprendizaje, reemplazará una API anterior por una nueva.

---
## Reemplazo de un Producto de API
1. Inicie sesión en {{site.data.keyword.Bluemix_short}}: [https://console.ng.bluemix.net/login ![Icono de enlace externo](../../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.ng.bluemix.net/login){:new_window}.

2. En el Panel de control de {{site.data.keyword.Bluemix_notm}}, inicie el servicio de {{site.data.keyword.apiconnect_short}}.
![](images/Bluemix.png)

3. En API Manager, si no ha marcado anteriormente el panel de navegación de la IU, pulse el icono **Navegar a** ![](images/navigate-to.png). Se abrirá el panel de navegación de la IU de API Manager. Para marcar el panel de navegación de la IU, pulse el icono **de menú Marcar** ![](images/pinned.png).

4. Pulse **Recinto de pruebas** para abrir el catálogo Recinto de pruebas. **Nota**: La pantalla puede mostrar mosaicos en lugar de una lista de catálogos.
![](images/del-sandbox-list.png)

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
 

 
## Qué ha hecho en esta guía de aprendizaje
En esta guía de aprendizaje, ha completado las actividades siguientes:

1. Ha actualizado un producto de API.
2. Ha reemplazado un producto de API anterior por un producto de API actualizado.
3. Ha migrado la suscripción al producto de API anterior al producto de API actualizado.

---












