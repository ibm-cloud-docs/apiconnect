---

copyright:
  years: 2017
lastupdated: "2017-10-10"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Archivado y supresión de Productos de API
**Duración**: 15 minutos  
**Nivel de habilidad**: Principiante 

## Requisitos previos

1. [Configurar la instancia de {{site.data.keyword.apiconnect_full}}](tut_prereq_set_up_apic_instance.html).

2. Complete la [guía de aprendizaje Reemplazar un producto de API](tut_manage_supercede.html).

---
## Objetivo
En esta guía de aprendizaje, suprimirá, archivará y retirará una API.

---
## Supresión de un Producto de API
1. Inicie sesión en {{site.data.keyword.Bluemix_short}}: [https://console.ng.bluemix.net/login ![Icono de enlace externo](../../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.ng.bluemix.net/login){:new_window}.

2. En el Panel de control de {{site.data.keyword.Bluemix_short}}, inicie el servicio de {{site.data.keyword.apiconnect_short}}.
![](images/Bluemix.png)

3. En API Manager, si no ha marcado anteriormente el panel de navegación de la IU, pulse el icono **Navegar a** ![](images/navigate-to.png). Se abrirá el panel de navegación de la IU de API Manager. Para marcar el panel de navegación de la IU, pulse el icono **de menú Marcar** ![](images/pinned.png).

4. Pulse **Recinto de pruebas** para abrir el catálogo Recinto de pruebas. **Nota**: Puede que necesite volver al Panel de control para ver los catálogos disponibles. Además, la página del panel de control puede mostrar catálogos como mosaicos en lugar de una lista.
![](images/del-sandbox-list.png)

5. Pulse los puntos suspensivos verticales en la línea **Weather Provider API 1.0.0**.  
![](images/del-prod-list1.png)

6. Seleccione **Suprimir del catálogo**.  
![](images/del-del-from-cat.png)

7. Pulse **Aceptar**.  
![](images/del-del-dialog.png)
    El producto desaparece de la lista de productos en el catálogo. No se puede recuperar en este momento.


## Archivado de un producto de API
1. Pulse los puntos suspensivos verticales en la línea **Weather Provider API 2.0.0**.  
![](images/del-prod-list2.png)

2. Seleccione **Retirar**.  
![](images/del-select-retire.png)

3. Pulse **Aceptar**.  
![](images/del-retire-dialog.png)

4. Pulse los puntos suspensivos verticales en la línea **Weather Provider API 2.0.0**.  
![](images/del-prod-list3.png)

5. Seleccionar **Archivar**.  
![](images/del-select-archive.png)

6. Pulse **Aceptar**.  
![](images/del-archive-dialog.png)
    El producto desaparece de la lista de productos en el catálogo. Puede recuperarse.

7. Pulse el icono de vista de lista.  
![](images/del-prod-list4.png)

8. Consulte **Archivado**.  
![](images/del-view-archived.png)

9. Pulse los puntos suspensivos verticales en la línea **Weather Provider API 2.0.0**.  
![](images/del-prod-list5.png)

10. Seleccione **Desarchivar**.  
![](images/del-unarchive.png)
    El estado del producto cambia a Retirado.
    ![](images/del-prod-list6.png)

 
 
## Qué ha hecho en esta guía de aprendizaje
En esta guía de aprendizaje, ha completado las actividades siguientes:

1. Se ha suprimido un producto de API
2. Se ha retirado un producto de API
3. Se ha archivado un producto de API
4. Se ha desarchivado un producto de API

---












