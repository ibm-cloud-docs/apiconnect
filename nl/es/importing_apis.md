---
copyright:
  years: 2017
lastupdated: "2017-12-15"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Importación de API

Puede utilizar un archivo de definición de Swagger para añadir una API REST.
{:shortdesc}

## Requisitos previos
{: #prereq_import_swagger}

Antes de empezar, asegúrese de que el archivo se ajusta a la versión 2.0 de la especificación de Swagger. El formato del archivo puede ser JSON o YAML.

Para añadir una API REST cargando un archivo de Swagger, lleve a cabo los pasos siguientes:

1. En el panel de navegación de IU de API Manager, pulse **Borradores** y en **API**.
Se abre el separador API.

2. Pulse **+ Añadir** y seleccione **Swagger 2.0** en la sección **Importar**.
Se abre la ventana **Importar API de Swagger**.

3. **Opcional**:
Para cargar un archivo desde el sistema de archivos local, pulse **Seleccionar archivo** y, en
el sistema de archivos, seleccione el archivo que desea utilizar. Se admiten los archivos `.json`,
`.yml` y `.yaml` siempre y cuando contengan una definición de Swagger válida.

4. **Opcional**:
Para cargar un archivo desde un URL, pulse **O importar desde URL** e indique
la dirección URL correcta en el campo **URL** que se presenta. Si se solicita la autenticación para acceder a la dirección URL, escriba un nombre de usuario y una contraseña. Se admiten los archivos `.json`,
`.yml` y `.yaml` siempre y cuando contengan una definición de Swagger válida.

5. Pulse **Importar**.
Se crea una nueva definición de API REST, incluyendo las vías de acceso y las operaciones HTTP.

Una vez importada la definición de la API, aparece en la lista de definiciones de API del separador **API** de la página **Borradores**.
Después puede editar la definición de API como lo haría con cualquier otra definición de API REST.

## Importación de API desde IBM Integration Bus
{: #tut_import_iib_apic}

Con esta guía de aprendizaje, puede importar API REST que haya creado con IBM Integration Bus en {{site.data.keyword.apiconnect_full}}, lo que facilita su gestión y
publicación. 
{: shortdesc}

Antes de empezar, asegúrese de que el archivo API REST se ajusta a la versión 2.0 de la especificación de Swagger. El formato del archivo puede ser JSON o YAML.

Puede utilizar IBM Integration Bus para crear API REST, que son
aplicaciones especializadas que se pueden utilizar para exponer integraciones como un servicio web RESTful y las pueden invocar
los clientes HTTP. Una vez que cree las API, podrá importarlas en {{site.data.keyword.apiconnect_short}} para gestionarlas y publicarlas.

La lista siguiente contiene algunas ventajas de gestionar las API en {{site.data.keyword.apiconnect_short}}:
* Puede supervisar el número de llamadas de su API.
* Puede controlar el número de llamadas de su API.
* Puede mantener varias versiones de una API.

Para obtener más beneficios, consulte [Gestión de API](managing_apis.html).

Para crear una API REST en IBM Integration Bus e importarla
en {{site.data.keyword.apiconnect_short}}, siga estos
pasos:
1. Cree la API REST utilizando IBM Integration Bus. Restricción: Puede crear una API REST sólo con el IBM Integration Toolkit, que se proporciona con la versión instalada de IBM Integration Bus.
	1. Cree una API REST utilizando el IBM Integration
		Toolkit. Para obtener más información sobre cómo completar las tareas para crear una API REST con IBM Integration Bus, consulte [Desarrollo de soluciones de integración con las API REST ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SSMKHH_10.0.0/com.ibm.etools.mft.doc/bi12016_.htm){: new_window} en el IBM Knowledge Center.
		
	2. Abra el asistente Crear una API REST seleccionando **Archivo** > **Nuevo** > **API REST**.
		
	3. Especifique un nombre para la API REST. El nombre que especifique se utilizará como el nombre del proyecto en
		el IBM Integration Toolkit.
		
	4. Seleccione uno de los métodos siguientes de creación de la API REST y complete el procedimiento:
		
	**Desde cero, utilizando el REST API Editor que se proporciona con el IBM Integration Toolkit**:
		1. Seleccione **Crear una API REST y definir los recursos y operaciones**.
		2. Pulse **Finalizar**. El REST API Editor para la nueva API REST se abrirá
automáticamente, lo que debe utilizar para definir recursos, modelos y operaciones.
		
	**Desde un documento de Swagger 2.0 anterior**:
		1. Seleccione **Importar recursos y operaciones definidos en un documento de Swagger** y
pulse **Siguiente**.
		2. Seleccione la vía de acceso al documento de Swagger que describe los recursos y operaciones que desee
en la API REST. Puede importar el documento de Swagger desde el sistema de archivos o desde un proyecto existente
del espacio de trabajo. El archivo se valida para su uso en una API REST. Si se encuentran errores mientras
se valida el documento de Swagger seleccionado, dichos errores de validación se mostrarán al principio
del asistente. No podrá continuar si se encuentran errores de validación en el documento de Swagger
seleccionado.
		3. Seleccione **Finalizar** para crear la API.
	5. Implemente los subflujos para la API REST, que son las operaciones REST que desea incluir.
2. Añada el proyecto de la API REST a un archivo BAR (broker archive) nuevo o existente del IBM Integration Bus.
3. Despliegue el archivo BAR en IBM Integration Bus on
Cloud.
	1. Inicie sesión en IBM Integration Bus on Cloud mediante el
ID de IBM, si aún no ha iniciado sesión. Regístrese para una cuenta si no tiene una.
	2. Pulse **Añadir integración** > **Cargar archivo BAR**.
	3. Seleccione el archivo BAR que haya creado para el proyecto de la API REST. Sugerencia: Puede encontrar la ubicación del archivo BAR pulsándolo con el botón derecho del ratón en el IBM Integration Toolkit, y visualizando sus propiedades.
	4. Seleccione **Guardar**.
	5. Seleccione **Renovar listado** para actualizar la pantalla.
	6. Compruebe que el archivo BAR se haya cargado correctamente viendo el API Integration Flow para la API en la ventana *Integraciones* de IBM Integration Bus on Cloud.
4. Inicie el flujo de integración seleccionando el icono Inicio ![Captura de pantalla que muestra el icono Inicio.](images/a_play_button.jpg " "). La API inicia y muestra un estado de `En ejecución`.
5. Seleccione la integración desde la lista de integraciones para ver información sobre ella. El árbol del menú Contenido muestra la API REST y los subflujos asociados con la
misma. También puede ver información en el resto de las secciones. En la sección Public Endpoints, puede ver
el URL público que IBM Integration Bus on Cloud ha asignado
al flujo de integración. Seleccione **Mostrar URL completo** para ver el URL completo para
dicha operación.
6. Copie el URL completo para la operación al portapapeles. Lo necesitará al configurar la API para trabajar con {{site.data.keyword.apiconnect_short}}. Si ha habilitado la Autenticación básica,
anote también el nombre de usuario y la contraseña asignados.

### Integre IBM Integration Bus con API Connect.
{: #integrateiibapic}

1. Importe el archivo de Swagger asociado con el proyecto de la API REST en el IBM Integration Toolkit en el servicio de {{site.data.keyword.apiconnect_short}}. 
	1. Inicie sesión en el servicio de {{site.data.keyword.Bluemix_notm}} de {{site.data.keyword.apiconnect_short}}.
	2. En el panel de navegación de IU de API Manager, seleccione **Borradores** > **API**. Se abre el separador API.
	3. Seleccione **+ Añadir** > **Importar API desde un archivo o URL**. Se abre la ventana *Importar OpenAPI (Swagger)*.
	4. Para cargar el archivo que ha creado desde el sistema de archivos local, seleccione **Seleccionar archivo** y seleccione el archivo que ha creado con IBM Integration Bus. Se admiten los archivos con las extensiones `.json`, `.yml` y
`.yaml` siempre y cuando contengan una definición de Swagger válida. Asegúrese de que esté seleccionada la opción para **Añadir un producto**. Opcionalmente, puede
publicar el producto seleccionando **Publicar este producto en un
catálogo**.
	5. Pulse **Importar**. Se crea una nueva definición de API REST, incluyendo las vías de acceso y las operaciones HTTP. Sugerencia: Cancele la importación, renueve el navegador e intente importar de nuevo si la importación lleva más
de 1 minuto. Puede que su sesión caduque.
2. Asocie la API importada de {{site.data.keyword.apiconnect_short}} con la API de IBM Integration Bus on Cloud.
	1. Vaya al Panel de control de {{site.data.keyword.apiconnect_short}}.
	2. Seleccione **Borradores** > **API**.
	3. Pulse la API REST que haya importado.
	4. Seleccione el separador Ensamblar y seleccione **Crear ensamblaje** para añadir la política de proxy.
	5. Arrastre la política **Proxy** a la nueva política vacía para habilitarla.
	6. Pegue el URL para la API que ha copiado desde la sección Public Endpoints de IBM Integration Bus on Cloud.
	7. Si ha habilitado Basic Authentication para la API REST, especifique el nombre de usuario y la contraseña generados
en IBM Integration Bus on Cloud.
	8. Guarde los valores de la API.
3. Pruebe la API.
	1. En el separador Ensamblar de la API, seleccione el botón Probar ![Botón Probar](images/a_play_button.jpg "Captura de pantalla que muestra el icono del botón Probar.").
	2. Seleccione **Volver a publicar producto**.
	3. Seleccione la Operación.
	4. Especifique los parámetros necesarios.
	5. Seleccione **Invocar**.
	6. Compruebe que haya recibido la respuesta esperada de la API. 
	
Cuando se importe y se integre la definición de la API, podrá gestionar y gobernar las API como lo hacía
con cualquier otra definición de API REST. Para obtener más información sobre las API, consulte [Gestión de API](managing_apis.html).

## Publicación de API creadas con IBM App Connect Professional en IBM API Connect

Con esta guía de aprendizaje, puede publicar y gestionar API REST creadas con IBM App Connect Professional con {{site.data.keyword.apiconnect_full}}.

### Requisitos previos
{: #prereq_pub_api_appconn}

Necesita cuentas válidas para IBM App Connect
Professional on Cloud y para {{site.data.keyword.apiconnect_short}} para completar esta guía de aprendizaje. Asegúrese de que el archivo API REST se ajuste a la versión 2.0 de la especificación Swagger. El formato del archivo puede ser JSON o YAML.

Puede utilizar IBM App Connect Professional para crear API REST,
que son aplicaciones especializadas que se pueden utilizar para exponer integraciones como un servicio web RESTful
y a las que pueden llamar los clientes HTTP. Después de crear las API, puede publicarlas y gestionarlas mediante {{site.data.keyword.apiconnect_short}}.
La lista siguiente contiene algunas ventajas de gestionar las API en {{site.data.keyword.apiconnect_short}}:

- Puede supervisar el número de llamadas de su API.
- Puede controlar el número de llamadas de su API.
- Puede mantener varias versiones de una API.

Para obtener más beneficios, consulte [Gestión de API](managing_apis.html).
Para crear una API REST en IBM App Connect Professional y publicarla
en {{site.data.keyword.apiconnect_short}}, siga estos
pasos:

1. Cree la API REST mediante IBM App Connect
Professional.
  - Inicie sesión en [App Connect Professional Web Management Console ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://appconnect.ibmcloud.com/professional/){:new_window} con su ID de IBM. Para obtener más información sobre cómo realizar las tareas para crear una API REST con IBM App Connect Professional Web Management Console, consulte [Sobre los valores de la consola de gestión ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SS3LC4_7.5.2.0/com.ibm.wci.appliance.doc/About_the_WMC/consoleSettings.html){:new_window} de IBM Knowledge Center.
  - Seleccione el separador Producción si todavía no está seleccionado.
  - Seleccione **Repositorio** > **Configuraciones** en el panel de navegación.
  - En la pantalla Configuración del proyecto, seleccione el proyecto que esté publicando en {{site.data.keyword.apiconnect_short}}.  Se muestran los detalles de configuración del proyecto que se está publicando.
  - Seleccione **Enviar a Gestión de API**. 
      **Sugerencia**: El botón **Enviar a Gestión de API** solo estará activo si el proyecto que se esté importando esté en ejecución o en despliegue. Seleccione el botón de reproducción para iniciar el proyecto si no se inicia el enlace.
  - En la pantalla Enviar a Gestión de API, escriba la información siguiente para crear una conexión al sistema de gestión de la API.

  <table><caption>Tabla 1. Información de conexión para la publicación de API en {{site.data.keyword.apiconnect_short}}</caption>
  <thead>
  <tr>
  <th>Nombre del campo</th>
  <th>Descripción</th>
  </tr>
  </thead>
  <tbody>
  <tr><td>Host</td>
  <td>Especifica el nombre del host de la dirección del clúster de gestión, el servidor o la nube. Para {{site.data.keyword.Bluemix_notm}}, esta entrada probablemente sea us.apiconnect.ibmcloud.com.</td>
  </tr>
  <tr>
  <td>Puerto</td>
  <td>Especifica el número de puerto necesario para conectarse a la dirección del clúster de gestión, el servidor o la nube.</td>
  </tr>
  <tr><td>ID Usuario</td>
  <td>Especifica el nombre de usuario de autenticación que se utiliza para conectarse a la dirección del clúster de gestión, el servidor o la nube. Probablemente es el ID de IBM que se utiliza para iniciar sesión en {{site.data.keyword.Bluemix_notm}}.</td>
  </tr>
  <tr><td>Contraseña</td>
  <td>Especifica la contraseña de autenticación que se utiliza para conectarse a la dirección del clúster de gestión, el servidor o la nube. Probablemente es la contraseña del ID de IBM que se utiliza para iniciar sesión en
  {{site.data.keyword.Bluemix_notm}}.</td>
  </tr>
  </tbody>
  </table>

2. Seleccione **Cargar organizaciones** para completar la lista de organizaciones asociadas con su ID y contraseña.

3. Seleccione **Organizaciones** para asociar el proyecto a una de las organizaciones disponibles.

4. Seleccione **Enviar a APIM** y, a continuación, **Aceptar**.

5. Seleccione **Cerrar** para cerrar la ventana.
Se abre un separador nuevo en el navegador predeterminado y en el que se muestra la API.

Asocie la API de IBM App Connect con {{site.data.keyword.apiconnect_short}}.

#### Importar definición de API de Swagger

Para importar el archivo Swagger asociado con el proyecto de la API REST en el IBM App Connect en el servicio de {{site.data.keyword.apiconnect_short}}, siga estos pasos:

1. Inicie sesión en el servicio de {{site.data.keyword.Bluemix_notm}} de {{site.data.keyword.apiconnect_short}}.

1.  En la barra de título de la interfaz de usuario de API Manager, seleccione **Navegar a** > **Borradores**.

2. Seleccione **API** en la barra de menús.
Se abre el separador API.

3. Seleccione la API importada para abrir API Designer.

4. Seleccione **Ensamblar** en la ventana de navegación.
Se muestra una lista de políticas en la ventana de navegación.

5. Seleccione **Crear ensamblaje** si es necesario.

6. Añada la política **Invocar** arrastrándola al conjunto de la ventana principal.

7. Seleccione la política **Invocar** en la ventana principal para modificar los valores de configuración.

8. Configure el host/basePath en el campo URL con la información siguiente:

- **nombre de host**: Valor que depende de la instancia de la nube. Para obtener más información sobre este valor, consulte
[IBM App Connect Professional ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://provide.castiron.ibmcloud.com){:new_window}.

- **vía de acceso base**: Vía de acceso que se especifica en la nota httpReceive de la orquestación de App Connect Professional.

9. Añada y guarde el nombre de usuario y contraseña de IBMid en los detalles de autenticación HTTP básica que utiliza para App Connect Professional.

#### Probar la API

Para probar la API, siga estos pasos:

1. En el separador Ensamblar de la API, seleccione el botón Probar <img alt="Captura de pantalla que muestra el icono del botón Probar" src="images/a_play_button.jpg" />.
2. Seleccione **Volver a publicar producto**.
3. Seleccione la Operación.
4.  Especifique los parámetros necesarios.
5. Seleccione **Invocar**.
6. Compruebe que haya recibido la respuesta esperada de la API.

Cuando se importe y se integre la definición de la API, podrá gestionar y gobernar las API como lo haría
con cualquier otra definición de API REST. Para obtener más información sobre las API, consulte [Gestión de API](managing_apis.html).


