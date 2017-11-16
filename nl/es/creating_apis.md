---

copyright:
  years: 2017
lastupdated: "2017-09-26"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Creación de API
{: #creating_apis}

Puede crear API descargando el kit de herramientas de desarrollador y utilizando la interfaz de línea de mandatos (CLI) o API Designer.

## CLI del kit de herramientas de desarrollador
{: #dev_tk_cli notoc}

El kit de herramientas de desarrollador proporciona una interfaz de línea de mandatos que puede utilizar para publicar API en {{site.data.keyword.apiconnect_long}}.
Puede publicar las API incluyéndolas en un producto y publicándolo. Puede definir las API y los productos creando y validando archivos de definición YAML en el sistema de archivos local. A continuación, puede interactuar con {{site.data.keyword.apiconnect_long}} utilizando los mandatos del kit de herramientas.

## API Designer
{: #designer notoc}

API Designer es una interfaz gráfica de usuario fuera de línea incluida en el kit de herramientas de desarrollador que proporciona funciones para crear y configurar API.
API Designer se ejecuta con el mandato de edición desde la interfaz de línea de mandatos. Al utilizarlo, API Designer se abre en el navegador predeterminado; también se puede acceder a él mediante el puerto de host local que se visualiza al ejecutar el mandato.

## Instalación del kit de herramientas de desarrollador
{: #install_dev_tk}

### Requisitos previos
{: #prereq_install_dev_tk}

Antes de comenzar, debe instalar [Node.js ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://nodejs.org/en/){:new_window} en la máquina en la que desee
utilizar el kit de herramientas y asegurarse de que `node` está en `PATH`.

Al instalar el kit de herramientas de desarrollador se instalan los siguientes elementos:

- Herramienta de línea de mandatos de {{site.data.keyword.apiconnect_short}}
- Editor gráfico de {{site.data.keyword.apiconnect_short}}
- Micro-gateway local de {{site.data.keyword.apiconnect_short}}


1. Para instalar el kit de herramientas, abra el indicador de mandatos como administrador y especifique el mandato siguiente:

    ```
    npm install -g apiconnect
    ```
    {: codeblock}

    **Nota:** Durante la instalación, es posible que detecte errores en el módulo `node-gyp`. Estos errores proceden de una dependencia opcional y la instalación se completará correctamente.

2. Para ver la ayuda del uso resumido de todos los mandatos del kit de herramientas, especifique el siguiente mandato:

    ```
    apic
    ```
	{: codeblock}

3. Para ver la ayuda de uso de cualquier mandato, utilice la opción `--help`.
    Por ejemplo:

    ```
    apic validate --help
    ```
	{: codeblock}
	
## Instalación de conectores de LoopBack
{: #install_lb_conn}

Para poder utilizar un origen de datos de LoopBack para acceder a los datos en un sistema de fondo como una base de datos, debe instalar el conector de origen de datos. Los conectores en memoria y de correo electrónico están integrados en LoopBack, por lo que no es necesario instalarlos.

### Requisitos previos
{: #prereq_install_lb_conn}

Los conectores de Oracle, DB2 y SQLLite requieren herramientas de compilador C para compilar e instalar extensiones binarias. Los requisitos exactos dependen del sistema operativo, según se describe en la tabla siguiente.

<table summary="" id="apic_028__table_pre_reqs" class="defaultstyle style-scope doc-content">
<caption>Tabla 1. Requisitos de instalación específicos del sistema operativo</caption>
<thead>
<tr>
<th style="width: 33.3%" id="th_d70e208" class="thleft style-scope doc-content">Windows</th>
<th style="width: 33.3%" id="th_d70e210" class="thleft style-scope doc-content">Linux</th>
<th style="width: 33.3%" id="th_d70e212" class="thleft style-scope doc-content">MAC OS X</th>
</tr>
</thead>
<tbody >
<tr class="style-scope doc-content doc-tr-odd">
<td style="width: 33.3%" > [Microsoft .NET Framework 4 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.microsoft.com/en-us/download/details.aspx?id=17851) <a href="https://www.microsoft.com/en-us/download/details.aspx?id=17851" rel="external" target="blank" title="(Se abre en un nuevo separador o ventana)" >Microsoft .NET Framework 4</a></td>
<td style="width: 33.3%">Python v2.7 (no hay soporte para v3.x)</td>
<td style="width: 33.3%" > [Python Releases for Mac OS X ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.python.org/downloads/mac-osx/) <a href="https://www.python.org/downloads/mac-osx/" rel="external" target="blank" title="(Se abre en un nuevo separador o ventana)" >Python
Releases for Mac OS X</a></td>
</tr>
<tr><td style="width: 33.3%" > [Visual Studio ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.visualstudio.com/downloads/download-visual-studio-vs) <a href="https://www.visualstudio.com/downloads/download-visual-studio-vs" rel="external" target="blank" title="(Se abre en un nuevo separador o ventana)" >Visual Studio</a></td>
<td style="width: 33.3%">
<code>make</code>
</td>
<td style="width: 33.3%" > [Xcode ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.apple.com/xcode/?cm_mc_uid=46449280653414622613810&amp;cm_mc_sid_50200000=1459433716) <a href="https://developer.apple.com/xcode/?cm_mc_uid=46449280653414622613810&amp;cm_mc_sid_50200000=1459433716" rel="external" target="blank" title="(Se abre en un nuevo separador o ventana)" >Xcode</a></td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 33.3%" > [Python v2.7.10 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.python.org/downloads/release/python-2710/) <a href="https://www.python.org/downloads/release/python-2710/" rel="external" target="blank" title="(Se abre en un nuevo separador o ventana)" >Python v2.7.10</a></td>
<td style="width: 33.3%">Una cadena de herramientas de compilador C/C++, por ejemplo, GCC versión 4.2 o posterior. </td>
<td style="width: 33.3%" >&nbsp;</td>
</tr>
<tr><td style="width: 33.3%" > [Microsoft Windows SDK for Windows 7 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.microsoft.com/en-gb/download/details.aspx?id=8279) <a href="https://www.microsoft.com/en-gb/download/details.aspx?id=8279" rel="external" target="blank" title="(Se abre en un nuevo separador o ventana)">Microsoft Windows SDK for Windows 7</a></td>
<td style="width: 33.3%">En Debian y en las distribuciones derivadas de Debian (Ubuntu, Mint, etc.), utilice el siguiente mandato:
<pre class="codeblock style-scope doc-content"><code>apt-get install build-essential</code></pre>
</td>
<td style="width: 33.3%" >&nbsp;</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 33.3%" >npm versión 3. Consulte la nota siguiente.</td>
<td style="width: 33.3%">&nbsp;</td>
<td style="width: 33.3%" >&nbsp;</td>
</tr>
</tbody>
</table>

**Nota:** Para instalaciones Windows:

- Utilice Visual Studio Community a menos que desee adquirir Visual Studio Enterprise. Ejecute el instalador, marque "Visual C++" en "Lenguajes de programación" y acepte la ubicación de instalación predeterminada.

- Para compilaciones de 64 bits de Node.js y módulos nativos, también es necesario el SDK de Windows&trade; 7 de 64 bits. Si la instalación falla, intente desinstalar cualquier C++ 2010
x64&amp;x86 redistribuible que haya instalado en primer lugar. Si se producen errores que indican que los compiladores de 64 bits no están instalados, es posible que también necesite la actualización de compilador para Windows&trade; SDK 7.1.
- Especifique el mandato siguiente para instalar npm versión
3:
  ```
  npm install -g npm
  ```
  {: codeblock}
  A continuación, asegúrese de que el mandato npm utiliza la versión correcta:
  ```
  npm -v
  ```
  {: codeblock}
  Si la versión mostrada no es la 3.x.x, edite el PATH del sistema para asegurarse de que
`C:\Users\username\AppData\Roaming\npm` sustituye a cualquier otra entrada.


1. **Opcional**:
Si utiliza API Designer, abra una nueva ventana de shell.

2. Cuando haya instalado las herramientas de compilador necesarias para su sistema operativo, instale el conector especificando el mandato siguiente en el directorio raíz del proyecto.

```
npm install --save <connector-package>
```
{: codeblock}
donde `<connector-package>` es el nombre del paquete npm del conector de LoopBack seleccionado.

<table summary="" id="apic_connectors_table_pre_reqs" class="defaultstyle style-scope doc-content">
<caption>Tabla 3. Conectores LoopBack</caption>
<thead>
<tr class="style-scope doc-content doc-tr-even">
<th style="width: 50%" id="th_new_d70e1489" class="thleft style-scope doc-content">Origen de datos</th>
<th style="width: 50%" id="th_new_d70e1491" class="thleft style-scope doc-content">Paquete de conectores</th>
</tr>
</thead>
<tbody>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Cloudant</td>
<td style="width: 50%">loopback-connector-cloudant</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">DashDB</td>
<td style="width: 50%">loopback-connector-dashdb</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">DB2</td>
<td style="width: 50%">loopback-connector-db2</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">DB2 para zOS</td>
<td style="width: 50%">loopback-connector-db2z</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Microsoft SQL Server</td>
<td style="width: 50%">loopback-connector-mssql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">MongoDB</td>
<td style="width: 50%">loopback-connector-mongodb</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">MySQL</td>
<td style="width: 50%">loopback-connector-mysql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">Oracle</td>
<td style="width: 50%">loopback-connector-oracle</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">PostgreSQL</td>
<td style="width: 50%">loopback-connector-postgresql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">Servicios web SOAP</td>
<td style="width: 50%">loopback-connector-soap</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Servicios web REST</td>
<td style="width: 50%">loopback-connector-rest</td>
</tr>
</tbody>
</table>

## Creación de una API de LoopBack con la CLI
{: #create_lb_api}

En el procedimiento siguiente se describe cómo crear una API de LoopBack&reg; con la interfaz de línea de mandatos.


### Requisitos previos
{: #prereq_create_lb_api}

Antes de empezar, debe tener a mano el identificador del catálogo que desee utilizar. Para obtener el identificador de catálogo, lleve a cabo los siguientes pasos:  

1. Vaya al **panel de control** de {{site.data.keyword.apiconnect_short}}.

2. Para el catálogo que desee utilizar, pulse el icono **Mostrar identificador de catálogo**
<img alt="Encadenar enlace para mostrar el identificador de catálogo" src="images/chain_link_icon.png">.

3. Copie el identificador de catálogo. Por ejemplo:  
  ```
  apic config:set catalog=apic-catalog://<region>.apiconnect.ibmcloud.com/orgs/<username_string>-dev/catalogs/<catalog>
  ```
  {: codeblock}
    donde:

    - `<region>` es la región de {{site.data.keyword.Bluemix_short}}.

    - `<username_string>` es su ID de organización de {{site.data.keyword.Bluemix_short}} sin símbolos. Por ejemplo,
`joe@mycompany.com` sería `joemycompanycom`

    - `<catalog>` es el nombre de su catálogo  

Para crear una API de LoopBack utilizando la CLI, realice los pasos siguientes:

1. Para crear un proyecto, abra una línea de mandatos y especifique lo siguiente:
  ```
  apic loopback
  ```
  {: codeblock}

2. En la solicitud que aparece después, se le indicará que especifique un nombre para la aplicación. Especifique un nombre y, a continuación, pulse **Intro**.
  ```
  ? What's the name of your application? (<nombre_aplicación>)
  ```
    
    La herramienta le solicita que escriba el nombre del directorio en el que se creará el proyecto.
    ```
    ? Enter name of the directory to contain the project: (<nombre_directorio_proyecto>)
    ```
    
3. Pulse **Intro** para utilizar el nombre que ha especificado antes o escriba un nombre nuevo y pulse **Intro**. La herramienta le solicita que seleccione el tipo de aplicación que se va a crear:
```
? What kind of application do you have in mind? (Use arrow keys)
  empty-server (An empty LoopBack API, without any configured models or datasources)
> hello-world (A project containing a basic working example, including a memory database)
```

4. Seleccione la aplicación que desea utilizar y pulse **Intro**.
La herramienta muestra un número de mensajes a medida que crea el directorio del proyecto y añade a este un número de directorios y archivos. También ejecuta `npm install` para
instalar todas las dependencias del proyecto, tal como se especifica en `package.json`.
Este proceso puede tardar un poco.

5. Antes de crear un modelo, debe asegurarse de que el directorio de trabajo actual es el directorio de nivel superior del proyecto. Para ello, escriba el siguiente mandato:
    ```
    cd <nombre_directorio_proyecto>
    ```
    {: codeblock}

6. Para crear un modelo, especifique el siguiente mandato:
    ```
    apic create --type model
    ```
    {: codeblock}

    La herramienta le solicita el nombre del modelo.

    ```
    ? Enter the model name:
    ```

7. Escriba un nombre para el modelo.
    En general, en el nombre de un modelo se puede utilizar cualquier carácter alfanumérico, guiones y subrayados.
    Aparecen todos los orígenes de datos que ha añadido al proyecto y la herramienta le solicita que seleccione un origen de datos:
    ```
    ? Select the data-source to attach item to: (Use arrow keys)
    ```

8. Seleccione el origen de datos que desea utilizar y pulse **Intro**. La herramienta le solicita que seleccione la clase base del modelo:
    ```
    ? Select model's base class (Use arrow keys)
       Model
    < PersistedModel
      ACL
      AccessToken
      Application
      Change
      Checkpoint
    (Move up and down to reveal more choices)
    ```
    Para obtener más información sobre cada opción, consulte [Utilización de modelos incorporados ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://loopback.io/doc/en/lb3/Using-built-in-models.html){:new_window}.

9. Seleccione una clase base y pulse **Intro**. La herramienta le pregunta si desea exponer la API REST del modelo.
```
? Expose branch via the REST API? (Y/n)
```
Si el modelo se expone a través de REST, todas las operaciones estándar create, read, update y delete estarán disponibles a través de puntos finales REST.

10. Indique su selección y pulse **Intro**.
Si elige exponer el modelo sobre REST, la herramienta solicitará la forma plural del nombre del modelo.
```
? Personalizar forma plural (utilizado para construir URL de REST):
```

11. Pulse **Intro** para utilizar las reglas de inglés estándar predeterminadas para
la pluralización.
La herramienta le solicita si desea crear un modelo de solo servidor o un modelo común que se pueda utilizar en la API de LoopBack&reg;
del servidor y del cliente.
```
? Common model or server only? (Use arrow keys)
```

12. Utilice las teclas de flecha para especificar su selección y pulse **Intro**.
La herramienta le solicita que añada las propiedades al modelo:
```
Let's add some branch properties now.
Enter an empty property name when done.
? Property name:
```

13. Escriba un nombre para la propiedad.
La herramienta le solicita que seleccione el tipo de datos de la propiedad:
```
? Property type: (Use arrow keys)
> string
  number
  boolean
  object
  array
  date
  buffer
```

14. Seleccione el tipo de cadena y pulse **Intro**.
La herramienta le pregunta si la propiedad es obligatoria:
```
? Required? (y/N)
```

15. Escriba `y` o `n` y pulse
**Intro**.
La herramienta le solicita que añada otra propiedad:
```
Let's add another branch property.
Enter an empty property name when done.
? Property name:
```

16. Si es necesario, añada otro nombre de propiedad. Si no es el caso, pulse **Intro** para acabar de añadir el modelo.

De forma predeterminada, los proyectos de LoopBack&reg; se entregan configurados con un origen de datos en memoria, adecuado para las tareas de desarrollo y de pruebas. Sin embargo, en algún momento deseará conectar los modelos a un origen de datos real (por ejemplo, a un servidor de bases de datos). Lleve a cabo los siguientes pasos para añadir un origen de datos:

1. Escriba el mandato siguiente:
```
apic create --type datasource
```
{: codeblock}
La herramienta le solicita el nombre del origen de datos.
```
? Enter the data-source name:
```

2. Escriba un nombre para el origen de datos. En el nombre de un origen de datos se puede utilizar cualquier carácter alfanumérico, guiones y subrayado. La herramienta le solicita que seleccione el conector que utilizará para el origen de datos:
```
? Select the connector for myds: (Use arrow keys)
> In-memory db (supported by StrongLoop)
  Email (supported by StrongLoop)
  MySQL (supported by StrongLoop)
  PostgreSQL (supported by StrongLoop)
  Oracle (supported by StrongLoop)
  Microsoft SQL (supported by StrongLoop)
  MongoDB (supported by StrongLoop)
(Move up and down to reveal more choices)
```

3. Utilice las teclas de flecha para seleccionar el conector que desea utilizar y pulse **Intro**.
La herramienta añade el origen de datos al proyecto.

4. Indique el host, el puerto, el usuario, la contraseña y las credenciales de la base de datos.
La herramienta le solicita que instale el conector de LoopBack&reg;.
```
Install loopback-connector-<connector>?
```

5. Escriba `Yes`.
La herramienta instala el conector.

NOTA: Si ha seleccionado el conector de Oracle, debe establecer una variable de entorno en
{{site.data.keyword.Bluemix_short}} para que se inicie la app de Oracle. Para ello, realice los pasos siguientes:

1. En la interfaz de usuario de {{site.data.keyword.Bluemix_short}}, seleccione
**Calcular**.

2. En Aplicaciones CF, seleccione la aplicación con la que desee trabajar.

3. Pulse **Tiempo de ejecución**.

4. Seleccione **Variables de entorno**.

5. En la sección Definidas por el usuario, pulse **Añadir**.

6. En el campo **Nombre**, especifique `LD_LIBRARY_PATH`.

7. En el campo **Valor**, especifique `$LD_LIBRARY_PATH:/home/vcap/app/node_modules/instantclient`.

8. Pulse **Guardar**.

### Prueba de un proyecto de LoopBack
{: #test_lb_proj}

Para probar un proyecto de LoopBack&reg;, lleve a cabo los pasos siguientes.

1. **Opcional**: Asegúrese de que el directorio de trabajo actual es el directorio de nivel superior del proyecto. Escriba el mandato siguiente:
```
cd <directorio-proyecto-loopback>
```
donde `<loopback-project-dir>` es el nombre del directorio que contiene el proyecto.
2. Escriba el mandato siguiente:
```
apic start
```
Se ejecuta de forma local el proyecto de LoopBack&reg; (API) y Micro Gateway. Aparecen los mensajes siguientes:
```
Waiting for loopback-project to complete deployment.
Waiting for loopback-project-gw to complete deployment.
Service loopback-project (id 1) started on port 4001
Service loopback-project-gw (id 2) started on port 4002
```
donde: `<loopback-project>` es el nombre del directorio que contiene el proyecto.

Puede probar cualquier punto final de la API mediante `curl`, por ejemplo.
Si desea cargar la API utilizando un navegador web, abra `http://localhost:4001` en el navegador. En cuanto al proyecto predeterminado de LoopBack&reg; (vacío o "Hello world"), verá algo parecido a esto:
```
{"started":"2016-03-07T22:24:55.322Z","uptime":35.839}
```

### Publicación de una aplicación de LoopBack en Bluemix desde la CLI
{: #pub_lb_app_cli}

Para publicar una aplicación de LoopBack en {{site.data.keyword.Bluemix_short}} desde la línea de mandatos,
realice los pasos siguientes:

1. Especifique el mandato siguiente para asegurarse de que está en el directorio de proyecto de Loopback.
```
cd <directorio-proyecto-loopback>
```
2. Escriba el mandato para iniciar sesión en {{site.data.keyword.apiconnect_short}} y {{site.data.keyword.Bluemix_short}}.
```
apic login --server  <región>.apiconnect.ibmcloud.com -u <nombre_usuario> -p <contraseña>
```
donde:
  * `<username>` es el ID de su organización de {{site.data.keyword.apiconnect_short}}.
  * `<password>` es la contraseña de {{site.data.keyword.apiconnect_short}}.
3. Pulse la barra espaciadora para abrir automáticamente la página del navegador de **Código de
acceso de un solo uso**.
4. Pulse **Volver a generar** y copie el código de acceso de un solo uso.
5. De nuevo en la CLI, pegue el código de acceso para completar el inicio de sesión. Se muestra el siguiente mensaje:
```
Logged into <region>.apiconnect.ibmcloud.com successfully
```
6. Escriba el mandato siguiente:
```
apic organizations -s <región>.apiconnect.ibmcloud.com
```
donde:
  * `<region>` es la región de {{site.data.keyword.Bluemix_short}}. Por ejemplo:
  * `eu` si está utilizando {{site.data.keyword.Bluemix_short}} Londres.
  * `us` si está utilizando {{site.data.keyword.Bluemix_short}} Dallas.
  * `au` si está utilizando {{site.data.keyword.Bluemix_short}} Sydney.

  Si no está seguro, puede localizar la región pulsando el icono {{site.data.keyword.avatar}} <img src="images/i-avatar-icon.svg" alt="icono de avatar"/> en la barra de menús para abrir
el widget Cuenta y soporte y comprobar el campo región.
7. Escriba el siguiente mandato para publicar la aplicación en {{site.data.keyword.Bluemix_short}}.
```
apic apps:publish –a <app> -o <org> -s <region>.apiconnect.ibmcloud.com
```
donde:
  * `<app>` es el nombre de la app
  * `<org>` es el nombre de la organización de {{site.data.keyword.Bluemix_short}}
  * `<region>` es la región de {{site.data.keyword.Bluemix_short}}
Se devuelve la salida siguiente:
  ```
  ...preparing project
  ...building package for deploy
  ...uploading package
  Runtime published successfully.
  Management URL: https://new-console.stage1.ng.bluemix.net/apps/3aa7087d-b454-4e13-bbc5-8228ebe00eef
  API target urls: apiconnect-3aa7087d-b454-4e13-bbc5-8228ebe00eef.pszetousibmcom-dev.apic.stage1.mybluemix.net
  API invoke tls-profile: client:Loopback-client
  ```

8. A continuación, debe modificar las definiciones del Producto con los valores que se han devuelto
durante la publicación. Para ello, lleve a cabo los siguientes pasos:

    1. En la interfaz de usuario de API Designer, pulse **API**.
    2. Seleccione su API.
    3. Pulse **Ensamblar**.
    4. En el editor de ensamblajes, pulse el icono **Filtrar políticas**.
    5. Seleccione **Políticas de DataPower Gateway**.
    6. Efectúe una doble pulsación en **invoke**.
    7. Actualice los siguientes campos con los valores recuperados en el paso 7.
        - **Invocar URL**: Inserte el URL de destino de la API. Debe especificar el protocolo de seguridad HTTPS. Por ejemplo:
        ```
        https://apiconnect-33e7b062-092b-4227-af97-047499dab2e7.<Organización_Bluemix>-<Espacio_Bluemix>.apic.<Nombre_dominio>$(request.path)
        ```
        Si no ha anotado
este valor, puede recuperarlo yendo al URL de gestión devuelto en el
paso 7. También puede recuperarlo iniciando sesión
en {{site.data.keyword.Bluemix_short}} y visualizando la información de la app.
        - **TLS Profile**: Inserte el tls-profile invoke de la API. Por ejemplo:
        ```
        client:Loopback-client
        ```
    8. Pulse **Guardar** para guardar la API.

## Creación de una API de LoopBack con API Designer
{: #create_lb_api_design}

En el procedimiento siguiente se describe cómo crear una API de LoopBack&reg; con API Designer.
{:shortdesc}

### Requisitos previos
{: #prereq_create_lb_api_design}

**Nota**: En las instrucciones siguientes se da por supuesto que está utilizando la última
versión del kit de herramientas del desarrollador. Para comprobar la versión más reciente, consulte la página del paquete [npm ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.npmjs.com/package/apiconnect){:new_window}.

Primero debe crear un proyecto de LoopBack&reg; utilizando la CLI. Para ello, lleve a cabo los siguientes pasos:

1. Para crear un proyecto, abra una línea de mandatos y especifique lo siguiente:
  ```
  apic loopback
  ```
  {: codeblock}

2. En la solicitud que aparece después, se le indicará que especifique un nombre para la aplicación. Especifique un nombre y, a continuación, pulse **Intro**.
  ```
  ? What's the name of your application? (<nombre_aplicación>)
  ```
    
    La herramienta le solicita que escriba el nombre del directorio en el que se creará el proyecto.
    ```
    ? Enter name of the directory to contain the project: (<nombre_directorio_proyecto>)
    ```
    
3. Pulse **Intro** para utilizar el nombre que ha especificado antes o escriba un nombre nuevo y pulse **Intro**. La herramienta le solicita que seleccione el tipo de aplicación que se va a crear:
```
? What kind of application do you have in mind? (Use arrow keys)
  empty-server (An empty LoopBack API, without any configured models or datasources)
> hello-world (A project containing a basic working example, including a memory database)
```

4. Seleccione la aplicación que desea utilizar y pulse **Intro**.
La herramienta muestra un número de mensajes a medida que crea el directorio del proyecto y añade a este un número de directorios y archivos. También ejecuta `npm install` para
instalar todas las dependencias del proyecto, tal como se especifica en `package.json`.
Este proceso puede tardar un poco.

5. Antes de crear un modelo, debe asegurarse de que el directorio de trabajo actual es el directorio de nivel superior del proyecto. Para ello, escriba el siguiente mandato:
```
cd <nombre_directorio_proyecto>
```

**Nota**: Al hacer que su directorio de trabajo actual sea el directorio de nivel superior del proyecto, se garantizará que la opción de añadir modelos y orígenes de datos esté disponible cuando abra API Designer. Si abre
API Designer sin cambiar el directorio, no podrá añadir modelos ni orígenes de datos.

Para abrir API Designer, lleve a cabo los pasos siguientes:
1. Abra una línea de mandatos y escriba lo siguiente:
```
apic edit
```
    Transcurridos unos instantes, aparece el siguiente mensaje:
    ```
    Express server listening on http://127.0.0.1:9000
    ```
    API Designer se abre en su explorador web predeterminado.

2. En la página de inicio de sesión, escriba su ID y su contraseña de Bluemix&reg;. Pulse **Iniciar sesión**.

3. Pulse **Modelos**.

4. Pulse **Añadir**. Se abre la ventana &reg; **Modelo** de LoopBack.

5. Escriba un nombre para el modelo.
En general, en el nombre de un modelo se puede utilizar cualquier carácter alfanumérico, guiones y subrayados.

6. Pulse **Nuevo**.

7. En la página del editor de modelos, vaya a Propiedades y pulse **Añadir**.

8. Escriba el nombre de la propiedad y seleccione un tipo.

9. Cuando termine de indicar las propiedades del modelo, pulse **Guardar**.

De forma predeterminada, un proyecto vacío de LoopBack&reg; no tiene ningún origen de datos definido. Para definir un origen de datos, lleve a cabo los pasos siguientes:
1. Pulse **Orígenes de datos**.

2. Pulse el icono **Añadir**.
Se abre la ventana &reg; **Nuevo modelo de LoopBack**.

3. Escriba un nombre para la fuente de datos. En el nombre de un origen de datos se puede utilizar cualquier carácter alfanumérico, guiones y subrayado.

4. Pulse **Nuevo**.
El origen de datos aparece en la lista de orígenes de datos y el editor actualiza el archivo
`server/datasources.json` con los valores del origen de datos nuevo.

5. Pulse el origen de datos para visualizar sus valores.

6. Cambie el valor Conector por el conector que desee.

7. Vuelva a la consola en la que ha iniciado API Designer e instale el conector especificando el siguiente mandato:
```
npm install --save <connector-package>
```
    donde `<connector-package>` es el nombre del paquete npm del conector de LoopBack&reg; seleccionado. Consulte la tabla siguiente para obtener una lista de paquetes de conectores.

**Nota:** Los conectores en memoria y de correo electrónico están integrados en LoopBack&reg;, por lo que no es necesario instalarlos.

<table>
<caption>Tabla 3. Conectores LoopBack</caption>
<thead>
<tr class="style-scope doc-content doc-tr-even">
<th style="width: 50%" id="3rd_d70e1489" class="thleft style-scope doc-content">Origen de datos</th>
<th style="width: 50%" id="3rd_d70e1491" class="thleft style-scope doc-content">Paquete de conectores</th>
</tr>
</thead>
<tbody>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Cloudant</td>
<td style="width: 50%">loopback-connector-cloudant</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">DashDB</td>
<td style="width: 50%">loopback-connector-dashdb</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">DB2</td>
<td style="width: 50%">loopback-connector-db2</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">DB2 para zOS</td>
<td style="width: 50%">loopback-connector-db2z</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Microsoft SQL Server</td>
<td style="width: 50%">loopback-connector-mssql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">MongoDB</td>
<td style="width: 50%">loopback-connector-mongodb</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">MySQL</td>
<td style="width: 50%">loopback-connector-mysql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">Oracle</td>
<td style="width: 50%">loopback-connector-oracle</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">PostgreSQL</td>
<td style="width: 50%">loopback-connector-postgresql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">Servicios web SOAP</td>
<td style="width: 50%">loopback-connector-soap</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Servicios web REST</td>
<td style="width: 50%">loopback-connector-rest</td>
</tr>
</tbody>
</table>

Para obtener más información, consulte [Documentación de LoopBack - Cómo crear un conector ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://http://loopback.io//doc/en/lb3/Defining-data-sources.html){:new_window}.

**Nota:** Si ha seleccionado el conector de Oracle, debe establecer una variable de entorno en
{{site.data.keyword.Bluemix_short}} para que se inicie la app de Oracle. Para ello, realice los pasos siguientes:

1. En la interfaz de usuario de {{site.data.keyword.Bluemix_short}}, seleccione
**Calcular**.

2. En Aplicaciones CF, seleccione la aplicación con la que desee trabajar.

3. Pulse **Tiempo de ejecución**.

4. Seleccione **Variables de entorno**.

5. En la sección Definidas por el usuario, pulse **Añadir**.

6. En el campo **Nombre**, especifique `LD_LIBRARY_PATH`.

7. En el campo **Valor**, especifique `$LD_LIBRARY_PATH:/home/vcap/app/node_modules/instantclient`.

8. Pulse **Guardar**.

Para probar un proyecto de LoopBack&reg;, siga estos pasos:
1. Pulse el icono **Iniciar los servidores**.
Se muestra el siguiente mensaje:
```
http://localhost:<4001/>Running
```
En función de la configuración del proyecto y de si hay otros procesos en ejecución, puede aparecer un número de puerto distinto.

2. Pulse **localhost:4001** para visualizar el punto final raíz de la API. En cuanto al proyecto predeterminado de LoopBack&reg; (vacío o "Hello world"), verá algo parecido a esto:
```
{"started":"2017-03-07T22:24:55.322Z","uptime":35.839}
```

A continuación, debe crear un producto. Para obtener más información, consulte [Creación de productos](managing_products.html#create_products).
**Sugerencia**: Siempre que inicie un indicador de mandatos nuevo, asegúrese que el directorio de trabajo actual es el
directorio de nivel superior del proyecto. Para ello, escriba el siguiente mandato:
```
cd <nombre_directorio_proyecto>
```

## Desinstalación del kit de herramientas de desarrollador
{: #uninstall_dev_tk}

### Requisitos previos
{: #prereq_uninstall_dev_tk}

Antes de empezar, debe detener cualquier app que se esté ejecutando de forma local; para ello, escriba el siguiente mandato:
```
apic stop --all
```

Para desinstalar el kit de herramientas de desarrollador, siga estos pasos:

1. Escriba el mandato siguiente:
```
npm rm -g apiconnect
```
{: codeblock}

2. Borre la memoria caché npm:
```
npm cache clean
```
{:codeblock}
  
Si está utilizando Windows:

3. Suprima todos los archivos cuyos nombres empiecen por `npm-` en `C:\Usuarios\nombre_usuario\AppData\Local\Temp`
4. Suprima el directorio `<home_dir>\.apiconnect`, donde `<home_dir>` es el directorio de inicio de la cuenta de usuario
en la que se ha instalado el kit de herramientas.
