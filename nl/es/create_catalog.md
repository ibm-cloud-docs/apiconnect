---

copyright:
  years: 2017
lastupdated: "2017-10-24"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal

subcollection: apiconnect

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Configuración de un catálogo
{: #create_catalog}

Puede crear y configurar catálogos de API Manager. Los catálogos son útiles para separar
productos y API para probarlos antes de hacerlos disponibles a organizaciones de desarrolladores.
Cuando configure un catálogo, también puede configurar una marca personalizada, de forma que no tenga
que utilizar el URL de la API predeterminada, proporcionada por API Manager.

Realice los pasos siguientes para crear el catálogo:

1. Pulse **Navegar a** <img alt="Icono Navegar a" src="images/navigate_to_icon.png"> > **Panel de control**.

2. Pulse **+ Añadir** > **Catálogo **.
Aparece la ventana **Añadir catálogo**.

3.  Especifique el nombre del catálogo nuevo en el campo **Mostrar nombre**.

4. Especifique el texto que quiere que forme el segmento del catálogo del URL, en el campo
**Nombre**.
	**Nota:** El campo **Nombre** puede contener sólo caracteres alfanuméricos en minúscula (a-z y 0-9) o guiones (-). Un guión no se puede utilizar ni como primer ni como último carácter en el nombre.

5. Pulse **Añadir**. Se ha creado el catálogo y se muestra en el panel de control.

6. Para configurar el catálogo, pulse el nombre del catálogo, a continuación, pulse **Valores** > **Información** y siga con los pasos siguientes:
  1. Si el catálogo nuevo es un catálogo de desarrollo, seleccione **Modalidad de desarrollo**.
Si selecciona la modalidad de desarrollo, las acciones de transferencia y publicación se fuerzan,
es decir, si vuelve a publicar un producto publicado anteriormente, se sobrescribe sin aviso. Si se encuentra
algún conflicto, el sistema lo resuelve automáticamente. Las acciones de anulación de publicación se producen
de forma automática.
	**Nota:** Los recuadros de aprobación no se muestran para los catálogos de desarrollo. No puede habilitar el proceso de aprobación para los ciclos de vida.
  2. Si quiere habilitar la suscripción automática para el catálogo, seleccione **Suscripción
automática**.
Al habilitar la suscripción automática, hace que las pruebas a las API sean más fáciles, porque se
utiliza una aplicación de pruebas, con un ID de cliente y un secreto de cliente suministrado anteriormente. La aplicación de pruebas se suscribe automáticamente a todas las planificaciones en el catálogo, por lo que no tiene que especificar una planificación o aplicación al realizar pruebas. 
    **Nota:** La suscripción automática sólo está disponible para un catálogo de desarrollo.
  3. Si el catálogo es el catálogo de transferencia predeterminado, seleccione **Predeterminado**. A continuación, las llamadas a las API publicadas en el catálogo, pueden utilizar un URL más corto que no incluye
el nombre del catálogo.
    **Nota:** Solo puede seleccionar **Predeterminado** para un catálogo.
  4. **Opcional**: Pulse **Puntos finales** y rellene los campos siguientes:
        - **URL de pasarela personalizado**: En el campo de texto URL de pasarela personalizado, especifique un URL. Utilice el URL de pasarela
personalizado si quiere conseguir marca personalizada de los URL para las API desplegadas en
{{site.data.keyword.apiconnect_short}}, en lugar de utilizar el
URL predeterminado que genera API Manager.
        De forma predeterminada, el URL de la pasarela de
{{site.data.keyword.apiconnect_short}} tiene el formato siguiente:
        ```
        https://gateway_cluster_hostname/organization_name/Catalog_name
        ```
        No obstante, puede sobrescribir el predeterminado especificando un URL más adecuado a su empresa, por
ejemplo, `https://api.mycompany.com`. Cualquier punto final de la API que se muestre en el
Portal del desarrollador reflejará entonces el URL especificado.
			**Notas:**
		    - Debe configurar una entrada DNS que correlacione el dominio y nombre de host personalizado con el
URL de la pasarela predeterminado.
		    - Para que los puntos finales de una API reflejen el URL de la pasarela personalizada, debe
configurar la API para que la pasarela de API Connect la imponga. Para obtener más información, consulte [Cómo especificar un host alternativo para una API ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){: #new_window}.
		    - Asegúrese de que el mismo URL de la pasarela personalizada no se aplique a varios catálogos ya que
el comportamiento en ese caso no estará definido.
				**SUGERENCIA**: Cuando invoque la API, también puede establecer la cabecera de host HTTP en la solicitud de la API
en el valor que haya especificado en el campo URL de Custom Gateway.

	    - **URL de API personalizado**
	    En el campo de texto URL de API personalizado, especifique el URL. Utilice el URL de API personalizado, para
especificar el URL de las API desplegadas en una pasarela de terceros.

	    URL de API personalizado representa el punto final por la que la API se conoce externamente, es decir,
el punto final publicado en el Portal del desarrollador y que utiliza un desarrollador de aplicación para
invocar o publicar la API.

	    Si está utilizando una pasarela de terceros o equilibrador de carga externo en este catálogo,
proporcione el URL en este campo. Cualquier punto final de la API que se muestre en el
portal del desarrollador reflejará entonces el URL especificado. Esos puntos finales existen en la pasarela
de terceros o en el equilibrador de carga y proyectan una dirección virtual, expuesta a consumidores API,
correlacionada con los puntos finales de ensamblaje de la API o el proxy de la API en la pasarela. Los puntos finales derivados desde URL de API personalizado, se publican normalmente en portales de
desarrolladores de producción para publicar la dirección de la API.

	    **Nota:** Si especifica un URL de API personalizado para un catálogo, prevalece sobre los nombres de host
que especifique al configurar la API. Para obtener más información, consulte [Cómo especificar un host alternativo para una API ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){: #new_window}.

	    - **Nombre de host para las llamadas de API del portal de desarrolladores**:
	    En el área de ventana Punto final de API del puerto, especifique un nombre de host para las
llamadas de la API del Portal del desarrollador. El nombre de host que especifique puede ser el nombre
de host del servicio de gestión. Para acceder a la API del Portal del desarrollador dentro del
contexto de un Portal del desarrollador, debe configurar el nombre de host base para las llamadas de la
API del Portal del desarrollador. Esta acción permite a API Manager correlacionar el nombre de
host con el catálogo y organización del proveedor de las llamadas de la API del Portal del desarrollador,
en lugar de tener que buscarlo e incluirlo en las llamadas.

7. Pulse el icono **Guardar**.

## Particionamiento de un catálogo
{: #apic_spaces_create_catalog}

Para utilizar la característica de sindicación en {{site.data.keyword.apiconnect_short}}, debe habilitar espacios en cualquier catálogo en el que necesite las funciones de sindicación.

Para habilitar espacios en un catálogo, lleve a cabo los pasos siguientes:
1. En el panel de control de la interfaz de usuario de API Manager, seleccione el catálogo con el que desee trabajar.

2. Pulse **Valores** > **Visión general** y pulse el control deslizante **Espacios**.

3. En la ventana **Habilitar espacios**, pulse **Habilitar** y luego pulse el icono **Guardar** <img src="images/icon_save.png" alt="icono guardar"/>.
Se muestra un enlace **Gestionar espacios** bajo el control deslizante **Espacios** y se añade un enlace **Espacios** al panel de navegación. Puede gestionar sus espacios pulsando en cualquiera de estos enlaces.

Los espacios se habilitan para el catálogo y se crea un espacio predeterminado llamado Nuevo espacio.

Para obtener más información sobre cómo utilizar la sindicación, consulte en los temas de Knowledge Center, [Utilización de la sindicación en IBM API Connect ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.apionprem.doc/capic_syndication_using.html){: #new_window}.
