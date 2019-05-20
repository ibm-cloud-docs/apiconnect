---

copyright:
  years: 2017
lastupdated: "2017-12-15"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal

subcollection: apiconnect

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Resolución de problemas
{: #apic_troubleshoot}

A continuación se muestran las respuestas a preguntas habituales de resolución de problemas sobre el uso de {{site.data.keyword.apiconnect_long}} en {{site.data.keyword.Bluemix_notm}}.
{:shortdesc}

## Nombre de usuario y contraseña requeridos al añadir el servicio de API Connect {{site.data.keyword.Bluemix_notm}}
{: #user_pw_apic_troubleshoot}

Al añadir el servicio al Panel de control de {{site.data.keyword.Bluemix_notm}}, se le solicitará un nombre de usuario y una contraseña al abrirlo. 

### Síntomas
{: #ts_sym_usernamepw_apic_troubleshoot}

En lugar de acceder al servicio {{site.data.keyword.Bluemix_notm}} directamente cuando se abre un nuevo {{site.data.keyword.apiconnect_short}}, se necesitará iniciar sesión en API Manager.

### Motivo
{: #ts_cause_usernamepw_apic_troubleshoot}

Su navegador está configurado para bloquear las cookies, o el nivel se establece en un nivel más restringido del que {{site.data.keyword.apiconnect_notm}} necesita.

### Resolución
{: #ts_res_usernamepw_apic_troubleshoot}

Habilite o aumente el nivel de permiso de cookies en los valores de su navegador hasta que se abra el servicio de {{site.data.keyword.Bluemix_notm}}.

## No se puede instalar el kit de herramientas de desarrollador
{: #unable_tk_apic_troubleshoot}

Después de suministrar el servicio de API Connect, intenta instalar el kit de herramientas de desarrollador y la
instalación falla.

### Síntomas
{: #ts_sym_noinstalltk_apic_troubleshoot}

Se muestran los siguientes errores durante la instalación del kit de herramientas de desarrollador:
```
npm ERR! Error: EACCES, mkdir '/usr/local/lib/node_modules/apiconnect'
...
npm ERR! Please try running this command again as root/Administrator
...
```

### Motivo
{: #ts_cause_noinstalltk_apic_troubleshoot}

No tiene los derechos necesarios para crear archivos o directorios.

### Resolución
{: #ts_res_noinstalltk_apic_troubleshoot}

Cambie los derechos para los directorios especificados, o ejecute el mandato utilizando
`sudo`. En un sistema de desarrollo local, es mejor solucionar los derechos del directorio de la forma
siguiente:
```
sudo chown -R $USER /usr/local
```
{:codeblock}

Este mandato convierte a la cuenta de usuario
en la propietaria del directorio `/usr/local`. A continuación, no necesitará utilizar sudo para
instalar el Nodo ni instalar paquetes de forma global con npm. 
    **Nota:** La modificación de la propiedad de directorios es apropiada solo en un sistema de desarrollo local. No haga nunca esto en un sistema servidor.

Igualmente, no utilice el mandato
`chown` anterior en el directorio `/usr/bin`;
hacerlo puede desconfigurar seriamente el sistema.

Si tiene que utilizar `sudo`, utilice
el siguiente mandato:
```
sudo npm install -g --unsafe-perm install apiconnect
```
{:codeblock}

## No se puede instalar el kit de herramientas de desarrollador en Windows
{: #unable_tk_win_apic_troubleshoot}

Después de suministrar el servicio de {{site.data.keyword.apiconnect_short}}, intenta instalar el kit de herramientas de desarrollador y la instalación falla.

### Síntomas
{: #ts_sym_noinstalltk_path_apic_troubleshoot}

Está intentando instalar el kit de herramientas de desarrollador en Windows y recibe un mensaje de error que indica que la *vía de acceso debe tener menos de 248 caracteres*.

### Motivo
{: #ts_cause_noinstalltk_path_apic_troubleshoot}

En los sistemas Windows hay una longitud máxima para las vías de acceso, que se supera al intentar instalar todas las dependencias en una carpeta de nivel profundo.

### Resolución
{: #ts_res_noinstalltk_path_apic_troubleshoot}

Puede arreglar este problema de una de las siguientes formas:

- Asegúrese de que ha instalado la versión correcta de Node.js. Para obtener más información, consulte [Cómo instalar el kit de herramientas de desarrollador](/docs/services/apiconnect?topic=apiconnect-creating_apis).

- Si ha tenido que actualizar un programa, vuelva a intentar la instalación.

Si esto no funciona, instale {{site.data.keyword.apiconnect_short}} a un nivel superior que la carpeta `C:/archivos de programa/nodejs/bin/node_modules...`. Si efectúa la instalación en un directorio de nivel superior, no verá este error.

## No se puede instalar el kit de herramientas de desarrollador en Mac OS X
{: #unable_tk_mac_apic_troubleshoot}

Después de suministrar el servicio de {{site.data.keyword.apiconnect_short}}, intenta instalar el kit de herramientas de desarrollador y la instalación falla.

### Síntomas
{: #ts_sym_noinstalltk_mac_apic_troubleshoot}

Se muestran los siguientes errores durante la instalación del kit de herramientas de desarrollador:
```
Agreeing to the Xcode/iOS license requires admin 
privileges, please re-run as root via sudo
```

### Motivo
{: #ts_cause_noinstalltk_mac_apic_troubleshoot}

Ha actualizado o instalado de forma reciente Xcode y aún no ha aceptado la licencia.

### Resolución
{: #ts_res_noinstalltk_mac_apic_troubleshoot}

1. Escriba el siguiente mandato para validar la licencia de Xcode:
```
sudo xcode-select
```
{:codeblock}

2. Reinstale el kit de desarrollador.


## No se puede instalar el kit de herramientas de desarrollador en Ubuntu
{: #unable_tk_ubu_apic_troubleshoot}

Después de suministrar el servicio de {{site.data.keyword.apiconnect_short}}, intenta instalar el kit de herramientas de desarrollador y la instalación falla.

### Síntomas
{: #ts_sym_noinstalltk_ubu_apic_troubleshoot}

Se muestran los siguientes errores durante la instalación del kit de herramientas de desarrollador:
```
sqlite3@3.1.1 install /usr/local/lib/node_modules/strong-pm/node_modules/minkelite/node_modules/sqlite3 
node-pre-gyp install --fallback-to-build 
/usr/bin/env: node: No such file or directory 
npm WARN This failure might be due to the use of legacy binary "node" 
npm WARN For further explanations, please read /usr/share/doc/nodejs/README.Debian 
npm ERR! weird error 127 
npm ERR! not ok code 0
```

### Resolución
{: #ts_res_noinstalltk_ubu_apic_troubleshoot}

Escriba el siguiente mandato para resolver el
problema:
```
$ update-alternatives --install /usr/bin/node node /usr/bin/nodejs 99
```

## No se puede depurar el error de instalación de npm
{: #unable_nmp_apic_troubleshoot}

Cuando siga los pasos para instalar el kit de herramientas del desarrollador, la instalación de npm
fallará.

### Síntomas
{: #ts_sym_npmfail_apic_troubleshoot}

La instalación de npm fallará sin proporcionar ninguna información útil para depurar.

### Resolución
{: #ts_res_npmfail_apic_troubleshoot}

Cuando falla una instalación, npm escribe una línea en el archivo `npm-debug.log</filepath>`
para mostrar dónde está ubicado el error. Utilice el archivo `npm-debug.log` para determinar
la causa.

## No se puede abrir API Designer
{: #unable_apid_apic_troubleshoot}

Escribe el mandato `apic edit` y API Designer no se abre.

### Síntomas
{: #ts_sym_noopenapid_apic_troubleshoot}

No puede abrir una instancia de API Designer al escribir el mandato:
```
apic edit
```
y aparece el mensaje siguiente:
```
<indicación de fecha y hora>. 329Z ERROR apiConnect: listen EADDRINUSE <ip address>:9000
```

### Motivo
{: #ts_cause_noopenapid_apic_troubleshoot}

Ya ha iniciado una instancia de API Designer desde otra ventana de mandatos.

### Resolución
{: #ts_res_noopenapid_apic_troubleshoot}

Para arreglar este problema, debe cerrar la otra ventana de mandatos tal como se describe en los pasos siguientes:

1. En la otra ventana de mandatos, pulse **Ctrl + C**.

2. Se visualiza el mensaje siguiente.
```
Terminate Batch job (Y/N)?
```

3. Escriba `Y` y pulse Intro.

## No se puede configurar la información de facturación para un Producto
{: #cannot_bill_apic_troubleshoot}

Alguna de la información de facturación no está disponible para configurar o confirmar a la producción. 

### Síntomas
{: #ts_sym_nobill_apic_troubleshoot}

  - Cuando busque en la sección de administración de su producto, el separador de facturación no se visualizará.
  - Cuando intenta publicar un Producto con la información de facturación especificada, obtendrá un error. 

### Motivo
{: #ts_cause_nobill_apic_troubleshoot}

Debe tener la cuenta y los permisos correctos de {{site.data.keyword.apiconnect_short}} para habilitar la información de facturación.

## No puede suscribirse a un plan de facturación con un producto
{: #cannot_bill_plan_apic_troubleshoot}

Stripe limita cada cliente a un máximo de 25 suscripciones. Asegúrese de que no haya superado este límite. Si es así, sólo puede añadir esta suscripción si elimina otra suscripción.

### Síntomas
{: #ts_sym_nosubscribe_apic_troubleshoot}

Verá un error cuando intenta suscribirse a un plan de facturación, aunque haya configurado otros planes.

### Motivo
{: #ts_cause_nosubscribe_apic_troubleshoot}

El servicio de proceso de tarjetas de crédito de Stripe permite un máximo de 25 suscripciones por cuenta.

### Resolución
{: #ts_res_nosubscribe_apic_troubleshoot}

Asegúrese de que tenga una cuenta de nivel empresarial para el servicio de {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.apiconnect_short}}, y que haya menos de 25 instancias. Elimine un servicio, si tiene el número máximo de servicios.

## Obtención de ayuda y soporte para API Connect
{: #get_help_apic_troubleshoot}

Si tiene problemas o preguntas al utilizar
{{site.data.keyword.apiconnect_short}}, puede obtener ayuda buscando
información o preguntando a través de un foro. También puede abrir una incidencia de soporte.

Al utilizar los foros para realizar una pregunta, etiquete la pregunta, de forma que la vean
los equipos de desarrollo de {{site.data.keyword.Bluemix_notm}}. 

- Si tiene preguntas técnicas sobre cómo desarrollar o desplegar una app con {{site.data.keyword.apiconnect_short}}, publique la pregunta
en Stack Overflow y etiquétela con "ibm-cloud" y "api connect".

- Para formular preguntas sobre el servicio y obtener instrucciones de iniciación, utilice el foro IBM DeveloperWorks dW Answers. Incluya las etiquetas "ibm cloud" y "api connect".
Consulte Obtener ayuda para conseguir más detalles sobre cómo utilizar los foros. 

Para obtener información sobre cómo abrir una incidencia de soporte de IBM, o sobre los niveles de soporte y la gravedad de las incidencias, consulte Cómo obtener soporte.



