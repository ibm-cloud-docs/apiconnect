---

copyright:
  years: 2017
lastupdated: "2017-12-15"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Gestión de API
{: #managing_apis}

Puede utilizar API Connect para gestionar API en {{site.data.keyword.Bluemix}}, tanto si están en {{site.data.keyword.Bluemix_notm}} o se mantienen fuera de {{site.data.keyword.Bluemix_notm}}. La gestión de las API le permite controlar el uso, aumentar la adopción y seguir estadísticas.

Si es un cliente, puede gestionar cómo se utiliza en la interfaz de usuario de API Manager una vez que un desarrollador cree una API y envíe el producto a {{site.data.keyword.Bluemix_notm}}. Los temas siguientes describen cómo crear y gestionar productos en {{site.data.keyword.apiconnect_short}}.

## Exposición de API locales mediante una Secure Gateway
{: #expose_apis_sec_gate}

Puede crear una pasarela segura para exponer de forma segura las API locales en {{site.data.keyword.apiconnect_full}}.

Al crear una pasarela segura, integre las características del servicio de {{site.data.keyword.Bluemix_notm}}
{{site.data.keyword.SecureGateway}} con {{site.data.keyword.apiconnect_short}}. Esto significa que tiene una forma segura
de acceder a las API locales desde {{site.data.keyword.apiconnect_short}} a través de un pasaje seguro sin la necesidad de suministrar una instancia separada del servicio de {{site.data.keyword.SecureGateway}}. Cree de forma efectiva un túnel
a {{site.data.keyword.apiconnect_short}} en un entorno público
sin exponer los datos locales. Todo lo que debe hacer es crear la pasarela y adjuntarla a una API. El destino, el perfil de SSL y los certificados se crean automáticamente.
Para obtener más información sobre el servicio {{site.data.keyword.SecureGateway}}, consulte [Acerca de la {{site.data.keyword.SecureGateway}}](../../services/SecureGateway/sg_overview.html#sg_overview).
Para crear una pasarela segura, siga los pasos de los temas siguientes.

### Creación de una pasarela segura
{: #create_sec_gate notoc}

Cuando cree una pasarela segura, se generan automáticamente un ID de pasarela y una señal de seguridad.
También de configurar un cliente de pasarela segura en el entorno local con el que se conecte {{site.data.keyword.apiconnect_short}}. Una vez configurado el cliente, utilice el ID de pasarela y la señal de seguridad para conectar con el cliente a fin de poder acceder a las API locales.

Para crear una pasarela, lleve a cabo los pasos siguientes:

1. Pulse **Navegar a** <img alt="Icono Navegar a" src="images/navigate_to_icon.png"> > **Admin** > **Secure Gateways**.
Se mostrará la página `Secure Gateways` y se mostrará una visita guiada a Secure Gateways en
la esquina de la IU.

2. **Opcional**:
Pulse en cada paso de la visita guiada para completar la configuración de la pasarela.

3. Pulse **Añadir**.
Se mostrará el recuadro de diálogo `Crear Secure Gateway`.

4. Especifique un nombre para la pasarela.
    **Nota:** Sólo se permiten caracteres alfanuméricos y de subrayado.

5. Pulse **Guardar**.
La pasarela se muestra junto con el ID de pasarela y la señal de seguridad.

6. Pulse **Configurar**.
Al pulsar **Configurar** se permite descargar e instalar un cliente de pasarela segura en la estación de trabajo local
para conectar una red remota a una pasarela segura en la red de Bluemix&reg;.

    Se mostrará la ventana `Configurar clientes de Secure Gateway`.

7. Pulse el cliente que desea utilizar desde las siguientes opciones:

    - IBM&reg; Installers
    - Docker
    - IBM DataPower&reg;

8. Siga las direcciones en pantalla para instalar y ejecutar el cliente que ha seleccionado.
Para obtener más información sobre cómo configurar un cliente de pasarela segura, consulte [Configuración de un cliente](../../services/SecureGateway/sg_021.html#sg_021).

9. Cuando haya terminado de instalar el cliente, cierre la ventana **Configurar clientes de Secure Gateway**.

10. Actualice la página.

El cliente está conectado y se muestran el ID de pasarela y el estado. Ha finalizado la configuración de la pasarela y ha creado una pasarela segura.
A continuación, utilice la pasarela segura para acceder a las API locales.

### Utilización de la pasarela segura con las API
{: #using_sec_gate_apis notoc}

Cuando haya configurado la pasarela, podrá utilizarla con las API.
{:shortdesc}

Para utilizar la pasarela segura con las API, lleve a cabo los pasos siguientes:
1. Cree la API y el Producto como se describe en los pasos siguientes.
  - Pulse **Navegar a** <img src="images/navigate_to_icon.png" alt="Icono Navegar a" /> > **Borradores** > **API** > **Añadir**.
  - Seleccione el tipo de API que desea crear.
  - Seleccione o pulse **Añadir un producto**. **IMPORTANTE**: No publique el Producto todavía.
  - Pulse **Crear API**.
  La API se muestra en la vista `Diseño`.
  
2. Pulse **Ensamblar**.

3. Pulse la política **invoke** para abrir la paleta **invoke**.
**RESTRICCIÓN**: Los conmutadores lógicos, por ejemplo `Conmutador`, `Conmutador de
funcionamiento` y `Si`, no se pueden utilizar con API que utilizan una pasarela segura.

4. Seleccione **Acceder al URL mediante Secure Gateway**.

5. En el campo del URL, actualice el `target-url` con el nombre de host y el número de puerto locales. Por ejemplo,
```
target-url: http://onpremdb2.rtp.raleigh.ibm.com:3055$(request.path)$(request.search)
```

6. Pulse **Guardar** <img src="images/icon_save.png" alt="Icono Guardar" />.

7. Pulse el separador **Fuente**.  Advierta el campo `secure-gateway` con un valor `true`.

8. Pulse **Todas las API** > **Productos** y seleccione el Producto que ha creado anteriormente.

9. Pulse el icono **Publicar** para transferir el producto al catálogo elegido.

10. Seleccione el catálogo que desea utilizar.

11. Seleccione el producto transferido.

12. Pulse **Publicar** y seleccione **Asignaciones de Secure Gateway**.

Ha expuesto de forma segura la API local en {{site.data.keyword.apiconnect_short}}. Se añadirá cualquier perfil de TLS asociado
con un destino. Para comprobar los perfiles de TLS,
pulse **Navegar a** <img src="images/navigate_to_icon.png" alt="Icono Navegar a" /> > **Admin** > **Seguridad** > **Perfiles de TLS**.
Puede tener varias pasarelas para cada API. Puede decidir qué pasarela desea utilizar al publicar la API. Si ya ha suministrado el servicio de {{site.data.keyword.SecureGateway}}, podrá supervisar
los destinos en el Panel de control de {{site.data.keyword.SecureGateway}}. Sin embargo, no puede editar ningún destino de {{site.data.keyword.apiconnect_short}} creado mediante el servicio {{site.data.keyword.apiconnect_short}}.
A continuación, pruebe la API de {{site.data.keyword.SecureGateway}}.

### Probar la API de pasarela segura
{: test_sec_gate notoc}

Después de adjuntar la pasarela a una API, puede probar la API para asegurarse de que la pasarela funciona y que genera la respuesta correcta.

Para probar una API utilizando la pasarela segura, lleve a cabo los pasos siguientes:

1. Pulse <img alt="Icono Navegar a" src="images/navigate_to_icon.png" /> > **Borradores** > **API**
**<Su API>** > **Ensamblar**.

2. Pulse el icono **Probar** <img src="images/test_icon.png" alt="icono probar"/>.

3. Seleccione un Catálogo para probar dentro de la lista suministrada.

4. Seleccione una pasarela segura con la que probar desde la lista suministrada.

5. Elija un Producto existente de la lista suministrada y, a continuación, pulse **Volver a publicar
producto**.
   **Importante** Si este producto ya está publicado en un catálogo, se volverá a publicar con la nueva pasarela.

6. **Opcional**:
Proporcione un nombre para crear un Producto nuevo y, a continuación, pulse **Crear y
publicar**.

7. Pulse **Siguiente**.

8. Seleccione una operación para invocar de la lista suministrada.

9. Pulse **Invocar**.

Se mostrarán los resultados de la prueba.

## Transferir y publicar una aplicación LoopBack
{: #stage_publish_lb_app}

1. En el panel de navegación de API Designer, pulse **Productos**.
Se abre el separador Productos.

2. Seleccione la versión del Producto, asegúrese de pulsar la versión con la que desea trabajar.

3. Para publicar el tiempo de ejecución en {{site.data.keyword.Bluemix_notm}}, pulse **Publicar**.

4. Pulse **Añadir y gestionar destinos** > **Añadir destino de IBM Cloud**.

5. Seleccione la **Región** de {{site.data.keyword.Bluemix_notm}} en la que desea publicar e iniciar sesión.

6. Seleccione la **Organización** de {{site.data.keyword.Bluemix_notm}} en la que desea publicar.

7.  Se muestra una lista de catálogos. Seleccione el catálogo en el que desea efectuar la publicación.

8.  Pulse **Siguiente**.

9. Seleccione la aplicación de LoopBack que desee publicar.
Si es la primera vez que despliega el tiempo de ejecución en {{site.data.keyword.Bluemix_notm}}, añada un nombre y pulse el icono **Añadir**.

10.  Pulse **Guardar**.

11.  Vuelva a pulsar **Publicar** y seleccione **Publicar aplicación**.

12.  Pulse **Publicar**.

13. En la línea de mandatos, se especifica el URL de destino y el profile-tls invoke de la API.
Anote esta información. El tls-profile invoke de la API siempre es
`client:Loopback-client`, pero puede recuperar el URL de destino de la API tal como se describe en el siguiente paso.
    ```
    Deploying to Bluemix
    ...preparing project
    ...building package for deploy
    ...uploading package
    Runtime published successfully.
    Management URL: https://<domain name>/apps/33e7b062-092b-4227-af97-047499dab2e7
    API target urls: apiconnect-33e7b062-092b-4227-af97-047499dab2e7.<Bluemix org>-<Bluemix space>.apic.<domain name>
    API invoke tls-profile: client:Loopback-client
    Updated newapi_1.0.0.yaml with tls-profile and target-url.
    Updated notes.yaml with tls-profile and target-url.
    ```

14. En la UI de API Designer, realice los pasos siguientes:
    1. Pulse **API**.
    2. Seleccione su API.
    3. Pulse **Ensamblar**.
    4. En el editor de ensamblajes, pulse el icono **Filtrar políticas**.
    5. Seleccione **Políticas de DataPower Gateway**.
    6. Pulse **Guardar** para guardar la API.

15.  A continuación, debe publicarla en API Manager. Pulse **Publicar**.
    1. Seleccione **Publicar aplicación** y, a continuación, seleccione una de las siguientes opciones:
	    - **Sustituir aplicación existente**: Si tiene una aplicación publicada, seleccione esta opción para sobrescribir la app existente.
        - **Como nueva app (utilizando la ruta existente)**: Seleccione esta opción para crear una app nueva y proporcionarle un nombre en el
campo **Nueva app**. El servicio no se interrumpe.

    2. Seleccione las siguientes opciones:
	    - Transferir o publicar productos
        - Seleccionar productos específicos
        - _su producto_
 
    3. Pulse **Publicar**.

Para comprobar que la publicación ha funcionado, lleve a cabo los siguientes pasos:

1. Asegúrese de que la app de {{site.data.keyword.Bluemix_notm}} está en ejecución.

2. Abra una ventana del navegador y vaya a la dirección URL de destino de la API.
La aplicación está protegida con la validación del cliente. Si no proporciona el certificado de cliente correcto, se producirá un error (comportamiento previsto).

3. Vaya a la dirección URL expuesta de {{site.data.keyword.apiconnect_short}}.
Por ejemplo:
```
https://<domain>/<Bluemix org>-<Bluemix space>/<Catalog identifier>/api/notes
```
Se muestra la respuesta 200.

## Configuración de un catálogo

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
utiliza una aplicación de pruebas, con un ID de cliente y un secreto de cliente suministrado anteriormente,
que se suscribe automáticamente a todas las planificaciones en el catálogo, así que no tiene que especificar
una planificación o aplicación al realizar pruebas.**Nota:** La suscripción automática sólo está disponible para un catálogo de desarrollo.
  3. Si el catálogo es el catálogo de transferencia predeterminado, seleccione **Predeterminado**. A continuación, las llamadas a las API publicadas en este catálogo, pueden utilizar un URL más corto que no incluya
el nombre del catálogo
    **Nota:** Sólo puede seleccionar **Predeterminado** para un catálogo.
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
configurar la API para que la pasarela de API Connect la imponga. Para obtener más información, consulte [Cómo especificar un host alternativo para una API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){:new_window}.
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
que especifique al configurar la API. Para obtener más información, consulte [Cómo especificar un host alternativo para una API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){:new_window}.

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

Para utilizar la característica de sindicación en {{site.data.keyword.apiconnect_short}}, debe habilitar espacios en cualquier catálogo en el que necesite las funciones de sindicación.

Para habilitar espacios en un catálogo, lleve a cabo los pasos siguientes:
1. En el panel de control de la interfaz de usuario de API Manager, seleccione el catálogo con el que desee trabajar.

2. Pulse **Valores** > **Visión general** y pulse el control deslizante **Espacios**.

3. En la ventana **Habilitar espacios**, pulse **Habilitar** y luego pulse el icono **Guardar** <img src="images/icon_save.png" alt="icono guardar"/>.
Se muestra un enlace **Gestionar espacios** bajo el control deslizante **Espacios** y se añade un enlace **Espacios** al panel de navegación. Puede gestionar sus espacios pulsando en cualquiera de estos enlaces.

Los espacios se habilitan para el catálogo y se crea un espacio predeterminado llamado Nuevo espacio.

Para obtener más información sobre cómo utilizar la sindicación, consulte en los temas de Knowledge Center, [Utilización de la sindicación en IBM API Connect ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.apionprem.doc/capic_syndication_using.html){:new_window}.

## Configuración de un portal del desarrollador
{: #config_dev_portal}

Un portal del desarrollador es el lugar en el que se publican sus planes para que los desarrolladores de aplicaciones accedan a ellos y los utilicen.

Puede crear un portal del desarrollador personalizado para que lo utilicen los desarrolladores de aplicaciones. Cuenta con un control administrativo completo sobre el aspecto, el contenido, los valores de usuario y los valores de configuración.

Además de permitir que los desarrolladores de aplicaciones busquen y utilicen API, el portal del desarrollador ofrece más características, como, por ejemplo, foros, blogs, comentarios, valoraciones y una IU de Swagger para API.

1. En la interfaz de usuario de API Manager, seleccione el catálogo con el que desee trabajar.

2. Seleccione el separador **Valores**.

3. Pulse **Portal**.

4. En la sección **Configuración de portal**, seleccione **IBM Developer
Portal**. Se visualiza la dirección URL del portal.

5. Pulse **Guardar**. Recibirá un correo electrónico que contiene un enlace de inicio de sesión de un solo uso para el usuario administrador de la web del portal del desarrollador.

6. Pulse el enlace recibido en su correo electrónico y siga las instrucciones para restablecer la contraseña.

Se ha configurado el portal del desarrollador. Encontrará la dirección URL del portal del desarrollador en la línea de asunto del correo electrónico que ha recibido. También puede encontrar el URL en la interfaz de usuario de API Manager seleccionando
**Portal** > **Valores**.

Para obtener más información sobre las tareas que puede llevar a cabo en el portal del desarrollador, consulte los temas de IBM
Knowledge Center sobre el [Portal del desarrollador ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.devportal.doc/capim_devportal_overview.html){:new_window}.

## Configuración de permisos para roles
{: #config_permissions_roles}

Para configurar los permisos para los roles en API Manager, siga estos pasos.

1. En el **Panel de control** de API Manager, pulse el catálogo con el que desea trabajar.

2. Pulse **Valores** > **Permisos**.
Se muestran los permisos de gestión del producto a los que puede asignar roles:
  - **Etapa**: Permite transferir productos al catálogo.
  - **Ver**: Permite ver y enumerar productos en el catálogo.
  - **Gestionar**: Permite la gestión del ciclo de vida del producto (publicar, en desuso, retiro y archivado).
  - **Aprobar**: Habilita las aprobaciones de los cambios de estado de ciclo de vida del producto.
**Nota:** La aprobación de los cambios del estado de ciclo de vida del producto está inhabilitada en todos los
catálogos de desarrollo.

3. Para añadir un rol a los permisos **Stage**, **View** o
**Manage**, pulse el icono **+** correspondiente.
La lista siguiente muestra los roles disponibles predeterminados:
  - Administrador
  - Gestor de producto
  - Desarrollador de API
  - Publicador
El rol Propietario tiene todos los permisos.

4. Habilite las aprobaciones para los cambios del estado de ciclo de vida del producto marcando
los recuadros de selección necesarios, a continuación, pulse el icono
**+** correspondiente para asignar los roles que tengan permiso para aprobar
el cambio de estado de ciclo de vida.
Los cambios del estado de ciclo de vida que seleccione, son a los que quiere aplicar la aprobación.
Por ejemplo, si selecciona Publicar pero deja los otros sin marcar, se requerirá la aprobación cuando
alguien intente publicar un producto, pero no será necesaria la aprobación en ninguno de los cambios de
estado de ciclo de vida.
5. Para asignar los roles que tienen permiso para gestionar políticas definidas de usuario, pulse
el icono **+** en la sección **Gestión de políticas**.
Se muestran los permisos de gestión de política, habilitándole para asignar roles cuando sea necesario.
6. Pulse el icono **Guardar**.
