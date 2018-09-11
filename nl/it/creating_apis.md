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

# Creazione di API
{: #creating_apis}

Puoi creare delle API scaricando il toolkit sviluppatori e utilizzando l'interfaccia riga di comando (CLI) oppure l'API Designer.

## Interfaccia riga di comando del toolkit sviluppatori
{: #dev_tk_cli notoc}

Il toolkit sviluppatori fornisce un'interfaccia riga di comando che puoi usare per pubblicare delle
API in {{site.data.keyword.apiconnect_long}}.
Pubblichi le API includendole in un prodotto e procedendo quindi alla sua pubblicazione. Definisci le tue
API e i tuoi prodotti creando e convalidando dei file di definizione YAML nel tuo file system
locale. Puoi quindi interagire con {{site.data.keyword.apiconnect_long}} utilizzando
i comandi del toolkit.

## API Designer
{: #designer notoc}

L'API Designer è una GUI (graphical user interface) non in linea nel toolkit sviluppatori che fornisce funzioni per la creazione e la configurazione di API.
L'API Designer viene eseguito utilizzando il comando edit dall'interfaccia riga di comando. Quando viene utilizzato
il comando edit, l'API Designer viene aperto nel tuo browser predefinito oppure è possibile accedervi tramite la porta
host locale visualizzata quando esegui il comando.

## Installazione del toolkit sviluppatori
{: #install_dev_tk}

### Prerequisiti
{: #prereq_install_dev_tk}

Prima di iniziare, devi installare [Node.js ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://nodejs.org/en/){:new_window} sul computer sul quale vuoi utilizzare il toolkit e accertarti che
`node` sia nel tuo `PATH`.

Quando installi il toolkit sviluppatori vengono installati i seguenti elementi.

- Strumento di riga di comando {{site.data.keyword.apiconnect_short}}
- Editor grafico {{site.data.keyword.apiconnect_short}}
- Micro-gateway {{site.data.keyword.apiconnect_short}} locale


1. Per installare il toolkit, apri il prompt dei comandi come amministratore e immetti questo comando.

    ```
    npm install -g apiconnect
    ```
    {: codeblock}

    **Nota:** durante l'installazione, potresti vedere degli errori dal modulo `node-gyp`. Questi errori provengono da
una dipendenza facoltativa e l'installazione verrà completata correttamente.

2. Per visualizzare una guida all'utilizzo di riepilogo per tutti i comandi toolkit, immetti questo comando:

    ```
    apic
    ```
	{: codeblock}

3. Per visualizzare la guida all'utilizzo per un qualsiasi comando, utilizzare l'opzione `--help`.
    Ad
esempio:

    ```
    apic validate --help
    ```
	{: codeblock}
	
## Installazione dei connettori LoopBack
{: #install_lb_conn}

Prima che tu possa usare un'origine dati LoopBack per accedere ai dati in un sistema di backend come un database, devi installare il connettore di origine dati. I connettori email e in memoria sono integrati in LoopBack e non hai bisogno di installarli.

### Prerequisiti
{: #prereq_install_lb_conn}

I connettori Oracle, DB2 e SQLLite richiedono gli strumenti del compilatore C per creare e installare estensioni binarie. Gli esatti requisiti dipendono dal tuo sistema operativo, come descritto nella seguente tabella.

<table summary="" id="apic_028__table_pre_reqs" class="defaultstyle style-scope doc-content">
<caption>Tabella 1. Requisiti di installazione specifici per i sistemi operativi</caption>
<thead>
<tr>
<th style="width: 33.3%" id="th_d70e208" class="thleft style-scope doc-content">Windows</th>
<th style="width: 33.3%" id="th_d70e210" class="thleft style-scope doc-content">Linux</th>
<th style="width: 33.3%" id="th_d70e212" class="thleft style-scope doc-content">MAC OS X</th>
</tr>
</thead>
<tbody >
<tr class="style-scope doc-content doc-tr-odd">
<td style="width: 33.3%" > [Microsoft .NET Framework 4 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.microsoft.com/en-us/download/details.aspx?id=17851)</td>
<td style="width: 33.3%">Python v2.7 (la v3.x non è supportata)</td>
<td style="width: 33.3%" > [Python Releases for Mac OS X ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.python.org/downloads/mac-osx/)</td>
</tr>
<tr><td style="width: 33.3%" > [Visual Studio ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.visualstudio.com/downloads/download-visual-studio-vs)</td>
<td style="width: 33.3%">
<code>make</code>
</td>
<td style="width: 33.3%" > [Xcode ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.apple.com/xcode/?cm_mc_uid=46449280653414622613810&amp;cm_mc_sid_50200000=1459433716)</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 33.3%" > [Python v2.7.10 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.python.org/downloads/release/python-2710/)</td>
<td style="width: 33.3%">Una toolchain di compilatore C/C++, ad esempio GCC versione 4.2 o successive. </td>
<td style="width: 33.3%" >&nbsp;</td>
</tr>
<tr><td style="width: 33.3%" > [Microsoft Windows SDK for Windows 7 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.microsoft.com/en-gb/download/details.aspx?id=8279)</td>
<td style="width: 33.3%">Su Debian e su distribuzioni derivate da Debian (Ubuntu, Mint eccetera), utilizza il comando:
<pre class="codeblock style-scope doc-content"><code>apt-get install build-essential</code></pre>
</td>
<td style="width: 33.3%" >&nbsp;</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 33.3%" >npm versione 3. Consulta la seguente nota.</td>
<td style="width: 33.3%">&nbsp;</td>
<td style="width: 33.3%" >&nbsp;</td>
</tr>
</tbody>
</table>

**Nota:** per le installazioni Windows:

- Utilizza Visual Studio Community a meno che tu non voglia acquistare Visual Studio Enterprise. Esegui il programma di installazione, seleziona "Visual C++" in "Programming Languages" e accetta l'ubicazione di installazione predefinita.

- Per le build a 64 bit di Node.js e i moduli nativi, ti occorre anche l'SDK Windows&trade; 7 a 64 bit. Se l'installazione non riesce, prova prima a disinstallare gli eventuali ridistribuibili C++ 2010 x64&amp;x86 che avevi installato. Se ricevi un errore che indica che i compilatori a 64 bit
non sono installati, potresti aver bisogno anche dell'aggiornamento del compilatore per Windows&trade; SDK 7.1.
- Immetti il seguente comando per installare npm versione
3:
  ```
  npm install -g npm
  ```
  {: codeblock}
  Assicurati quindi che il comando npm utilizzi la
versione corretta:
  ```
  npm -v
  ```
  {: codeblock}
  Se la versione visualizzata non è 3.x.x, modifica il tuo PATH
di sistema per accertarti che `C:\Users\username\AppData\Roaming\npm` rimpiazzi qualsiasi altra voce.


1. **Facoltativo**:
se stai utilizzando l'API Designer, apri una nuova finestra della shell.

2. Dopo aver installato gli strumenti del compilatore necessari per il tuo sistema operativo, installa
il connettore immettendo il seguente comando nella directory root del progetto.

```
npm install --save <pacchetto-connettore>
```
{: codeblock}
dove `<connector-package>` è il nome del pacchetto npm per il connettore LoopBack, come mostrato nella tabella.

<table summary="" id="apic_connectors_table_pre_reqs" class="defaultstyle style-scope doc-content">
<caption>Tabella 3. Connettori LoopBack</caption>
<thead>
<tr class="style-scope doc-content doc-tr-even">
<th style="width: 50%" id="th_new_d70e1489" class="thleft style-scope doc-content">Origine dati</th>
<th style="width: 50%" id="th_new_d70e1491" class="thleft style-scope doc-content">Pacchetto connettore</th>
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
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">DB2 per zOS</td>
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
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">Sevizi web SOAP</td>
<td style="width: 50%">loopback-connector-soap</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Sevizi web REST</td>
<td style="width: 50%">loopback-connector-rest</td>
</tr>
</tbody>
</table>

## Creazione di un'API LoopBack utilizzando la CLI
{: #create_lb_api}

La seguente procedura descrive come creare un'API LoopBack&reg; utilizzando l'interfaccia riga di comando.


### Prerequisiti
{: #prereq_create_lb_api}

Prima di iniziare, devi avere a portata di mano l'identificativo per il catalogo che vuoi utilizzare. Per ottenere l'identificativo del catalogo, completa questa procedura:  

1. Vai al **Dashboard** {{site.data.keyword.apiconnect_short}}.

2. Per il catalogo che vuoi utilizzare, fai clic sull'icona **Mostra identificativo del catalogo**
<img alt="Link a catena per visualizzare l'identificativo del catalogo" src="images/chain_link_icon.png">.

3. Copia l'identificativo del catalogo. Ad
esempio:  
  ```
  apic config:set catalog=apic-catalog://<region>.apiconnect.ibmcloud.com/orgs/<username_string>-dev/catalogs/<catalog>
  ```
  {: codeblock}
    dove:

    - `<region>` è la regione {{site.data.keyword.Bluemix_notm}}.

    - `<username_string>` è il tuo ID organizzazione {{site.data.keyword.Bluemix_notm}} senza alcun simbolo. Ad esempio, `joe@mycompany.com` sarebbe `joemycompanycom`

    - `<catalog>` è il nome del tuo catalogo  

Per creare un LoopBack utilizzando la CLI, completa la seguente procedura:

1. Per creare un progetto, apri una riga di comando e immetti:
  ```
  apic loopback
  ```
  {: codeblock}

2. Nel prompt che segue, ti viene richiesto di denominare la tua applicazione. Immetti un nome quindi premi
**Invio**.
  ```
  ? What's the name of your application? (<nome applicazione>)
  ```
    
    Lo strumento ti richiede di immettere il nome della directory in cui creare il progetto.
    ```
    ? Enter name of the directory to contain the project: (<project directory name>)
    ```
    
3. Premi **Invio** per utilizzare il nome da te immesso in precedenza oppure digita un nuovo nome
e premi quindi **Invio**. Lo strumento ti richiede di selezionare il tipo di applicazione da creare:
```
? What kind of application do you have in mind? (Use arrow keys)
  empty-server (An empty LoopBack API, without any configured models or datasources)
> hello-world (A project containing a basic working example, including a memory database)
```

4. Seleziona l'applicazione che vuoi utilizzare e premi **Invio**.
Lo strumento visualizza diversi messaggi mentre crea la directory di progetto e aggiunge
a essa un certo numero di directory e file.Esegue inoltre `npm install`
per installare tutte le dipendenze del progetto, come specificato in `package.json`.
Questo processo potrebbe richiedere del tempo.

5. Prima di poter creare un modello, devi accertarti che la tua directory di lavoro corrente sia la directory di livello
superiore del progetto. Per farlo, immetti questo comando:
    ```
    cd <project directory name>
    ```
    {: codeblock}

6. Per creare un modello, immetti il seguente comando:
    ```
    apic create --type model
    ```
    {: codeblock}

    Lo strumento ti richiede il nome del modello.

    ```
    ? Enter the model name:
    ```

7. Immetti un nome per il modello.
    In generale, in un nome di modello puoi usare qualsiasi carattere alfanumerico, più i trattini e i segni di sottolineatura.
    Tutte le origini dati che sono state aggiunte al progetto sono elencate e lo strumento ti richiede di selezionare
un'origine dati da utilizzare:
    ```
    ? Select the data-source to attach item to: (Use arrow keys)
    ```

8. Seleziona l'origine dati che vuoi utilizzare e premi **Invio**. Lo strumento ti richiede di selezionare la classe di base del modello:
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
    Per ulteriori informazioni su ciascuna opzione, vedi [Using built-in models ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://loopback.io/doc/en/lb3/Using-built-in-models.html){:new_window}.

9. Seleziona una classe di base e premi **Invio**. Lo strumento ti richiede se desideri esporre l'API REST del modello.
```
? Expose branch via the REST API? (Y/n)
```
Se il modello viene esposto su REST, tutte le operazioni di creazione, lettura,
aggiornamento ed eliminazione standard sono disponibili tramite gli endpoint REST.

10. Immetti la tua selezione e premi **Invio**.
Se scegli di esporre il modello in REST, lo strumento ti richiede
la forma plurale del nome del modello.
```
? Personalizza la forma plurale (utilizzata per creare l'URL REST):
```

11. Premi **Invio** per utilizzare le regole inglesi standard per la pluralizzazione.
Lo strumento ti richiede se vuoi creare un modello solo server oppure un modello comune
che può essere utilizzato sia nell'API LoopBack;
server che in quella client.
```
? Common model or server only? (Use arrow keys)
```

12. Utilizza i tasti freccia per operare la tua selezione e premi **Invio**.
Lo strumento ti richiede di aggiungere le proprietà al modello:
```
Let's add some branch properties now.
Enter an empty property name when done.
? Property name:
```

13. Immetti un nome proprietà.
Lo strumento richiede di selezionare il tipo di dati della proprietà:
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

14. Seleziona il tipo string e premi **Invio**.
Lo strumento richiede se la proprietà è obbligatoria:
```
? Required? (y/N)
```

15. Immetti `y` o `n` e premi quindi **Invio**.
Lo strumento ti richiede di aggiungere un'altra proprietà:
```
Let's add another branch property.
Enter an empty property name when done.
? Property name:
```

16. Se richiesto, aggiungi un altro nome proprietà. Se non ti servono ulteriori proprietà, premi **Invio** per terminare l'aggiunta al modello.

Per impostazione predefinita, un progetto LoopBack; è già configurato con un'origine dati in memoria, adatta per lo sviluppo
e la verifica. Tuttavia, a un certo punto, vorrai connettere i tuoi modelli a un'origine dati reale, come un server di database. Per aggiungere un'origine dati, completa questa procedura:

1. Immetti il seguente comando:
```
apic create --type datasource
```
{: codeblock}
Lo strumento ti richiede il nome dell'origine dati.
```
? Enter the data-source name:
```

2. Immetti il nome per l'origine dati.  In un nome di origine dati puoi usare qualsiasi carattere alfanumerico, più i trattini e i segni di sottolineatura. Lo strumento ti richiede di selezionare il connettore da utilizzare per l'origine dati:
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

3. Utilizza i tasti freccia per selezionare il connettore che vuoi utilizzare e premi quindi **Invio**.
Lo strumento aggiunge quindi l'origine dati al progetto.

4. Immetti le tue credenziali host, porta, utente, password e database.
Lo strumento ti richiede di installare il connettore LoopBack.
```
Install loopback-connector-<connector>?
```

5. Immetti `Yes`.
Lo strumento installa il connettore.

NOTA: se hai selezionato il connettore Oracle, devi impostare una variabile di ambiente
in {{site.data.keyword.Bluemix_notm}} perché venga avviata l'applicazione Oracle. Per effettuare questa operazione,
completa la seguente procedura:

1. Nell'interfaccia utente {{site.data.keyword.Bluemix_notm}}, seleziona **Calcola**.

2. In Applicazioni CF, seleziona l'applicazione con cui vuoi lavorare.

3. Fai clic su **Runtime**.

4. Seleziona **Variabili di ambiente**.

5. Nella sezione Definita dall'utente, fai clic su **AGGIUNGI**.

6. Nel campo **Nome**, immetti `LD_LIBRARY_PATH`.

7. Nel campo **Valore**, immetti `$LD_LIBRARY_PATH:/home/vcap/app/node_modules/instantclient`.

8. Fai clic su **Salva**.

### Verifica di un progetto LoopBack
{: #test_lb_proj}

Per verificare un progetto LoopBack, completa questa procedura.

1. **Facoltativo**: accertati che la tua directory di lavoro corrente sia la directory di livello superiore del progetto. Immetti il seguente comando:
```
cd <loopback-project-dir>
```
dove `<loopback-project-dir>` è il nome della directory che contiene il progetto.
2. Immetti il seguente comando:
```
apic start
```
Questo esegue il progetto LoopBack (API) e il Micro Gateway in locale. Vengono visualizzati i seguenti messaggi:
```
Waiting for loopback-project to complete deployment.
Waiting for loopback-project-gw to complete deployment.
Service loopback-project (id 1) started on port 4001
Service loopback-project-gw (id 2) started on port 4002
```
dove: `<loopback-project>` è il nome della directory che contiene il progetto.

Puoi quindi verificare gli endpoint API che desideri utilizzando, ad esempio `curl`.
Se vuoi caricare l'API utilizzando un browser web, apri
`http://localhost:4001` nel tuo browser. Per il progetto LoopBack predefinito (vuoto o
hello-world), vedi qualcosa di simile a questo:
```
{"started":"2016-03-07T22:24:55.322Z","uptime":35.839}
```

### Pubblicazione di un'applicazione LoopBack in {{site.data.keyword.Bluemix_notm}} dalla CLI
{: #pub_lb_app_cli}

Per pubblicare un'applicazione LoopBack in {{site.data.keyword.Bluemix_short}} dalla riga di comando, completa
la seguente procedura:

1. Immetti il seguente comando per assicurarti di essere nella directory del progetto Loopback.
```
cd <loopback-project-dir>
```
2. Immetti il seguente comando per accedere a {{site.data.keyword.apiconnect_short}} e {{site.data.keyword.Bluemix_notm}}.
```
apic login --server  <region>.apiconnect.ibmcloud.com -u <username> -p <password>
```
dove:
  * `<username>` è il tuo ID organizzazione {{site.data.keyword.apiconnect_short}}.
  * `<password>` è la tua password {{site.data.keyword.apiconnect_short}}.
3. Premi la barra spaziatrice per aprire automaticamente la pagina del browser **Passcode monouso**.
4. Fai clic su **Rigenera** e copia la passcode monouso.
5. Torna alla CLI e incolla la passcode per completare l'accesso. Viene
visualizzato il seguente messaggio:
```
Logged into <regione>.apiconnect.ibmcloud.com successfully
```
6. Immetti il seguente comando:
```
apic organizations -s <regione>.apiconnect.ibmcloud.com
```
dove:
  * `<region>` è la regione {{site.data.keyword.Bluemix_notm}}. Ad
esempio:
  * `eu` se stai utilizzando {{site.data.keyword.Bluemix_notm}} London.
  * `us` se stai utilizzando {{site.data.keyword.Bluemix_notm}} Dallas.
  * `au` se stai utilizzando {{site.data.keyword.Bluemix_notm}} Sydney.

  Se non sei sicuro, puoi individuare la tua regione
facendo clic sull'icona {{site.data.keyword.avatar}} <img src="images/i-avatar-icon.svg" alt="icona avatar"/> nella barra del menu per aprire il widget Account e supporto e controllare il campo regione.
7. Immetti il seguente comando per pubblicare la tua applicazione in {{site.data.keyword.Bluemix_notm}}.
```
apic apps:publish –a <app> -o <org> -s <region>.apiconnect.ibmcloud.com
```
dove:
  * `<app>` è il nome della tua applicazione
  * `<org>` è il nome della tua organizzazione {{site.data.keyword.Bluemix_notm}}
  * `<region>` è la regione {{site.data.keyword.Bluemix_notm}}
Viene restituito il seguente output:
  ```
  ...preparing project
  ...building package for deploy
  ...uploading package
  Runtime published successfully.
  Management URL: https://new-console.stage1.ng.bluemix.net/apps/3aa7087d-b454-4e13-bbc5-8228ebe00eef
  API target urls: apiconnect-3aa7087d-b454-4e13-bbc5-8228ebe00eef.pszetousibmcom-dev.apic.stage1.mybluemix.net
  API invoke tls-profile: client:Loopback-client
  ```

8. Devi quindi modificare le definizioni del prodotto con i valori restituiti durante la fase di pubblicazione. Per eseguire questa operazione, completa la seguente procedura:

    1. Nell'interfaccia utente API Designer, fai clic su **API**.
    2. Seleziona la tua API.
    3. Fai clic su **Assembla**.
    4. Nell'editor di assemblaggio, fai clic sull'icona **Politiche di filtro**.
    5. Seleziona **Politiche DataPower Gateway**.
    6. Fai doppio clic su **richiama**.
    7. Aggiorna i seguenti campi con i valori che hai richiamato nel passo 7.
        - **Richiama l'URL**: inserisci l'URL di destinazione API. Devi specificare il protocollo sicuro HTTPS. Ad esempio:
        ```
        https://apiconnect-33e7b062-092b-4227-af97-047499dab2e7.<organizzazione Bluemix>-<spazio Bluemix>.apic.<nome dominio>$(request.path)
        ```
        Se non hai annotato questo valore, puoi richiamarlo andando all'URL di gestione restituito nel
passo 7. Puoi anche richiamarlo accedendo a {{site.data.keyword.Bluemix_notm}} e visualizzando le informazioni sulla tua applicazione.
        - **Profilo TLS**: inserisci profilo TLS (tls-profile) di richiamo API. Ad esempio:
        ```
        client:Loopback-client
        ```
    8. Fai clic su **Salva** per salvare l'API.

## Creazione di un'API LoopBack utilizzando l'API Designer
{: #create_lb_api_design}

La seguente procedura descrive come creare un'API LoopBack utilizzando l'API Designer.
{:shortdesc}

### Prerequisiti
{: #prereq_create_lb_api_design}

**Nota**: le seguenti istruzioni presumono che tu stia utilizzando l'ultima versione del toolkit
sviluppatori. Per controllare l'ultima versione, consulta la pagina del pacchetto [npm ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.npmjs.com/package/apiconnect){:new_window}.

Devi prima creare un progetto LoopBack utilizzando la CLI. Per eseguire tale operazione, completa
questa procedura:

1. Per creare un progetto, apri una riga di comando e immetti:
  ```
  apic loopback
  ```
  {: codeblock}

2. Nel prompt che segue, ti viene richiesto di denominare la tua applicazione. Immetti un nome quindi premi
**Invio**.
  ```
  ? What's the name of your application? (<nome applicazione>)
  ```
    
    Lo strumento ti richiede di immettere il nome della directory in cui creare il progetto.
    ```
    ? Enter name of the directory to contain the project: (<project directory name>)
    ```
    
3. Premi **Invio** per utilizzare il nome da te immesso in precedenza oppure digita un nuovo nome
e premi quindi **Invio**. Lo strumento ti richiede di selezionare il tipo di applicazione da creare:
```
? What kind of application do you have in mind? (Use arrow keys)
  empty-server (An empty LoopBack API, without any configured models or datasources)
> hello-world (A project containing a basic working example, including a memory database)
```

4. Seleziona l'applicazione che vuoi utilizzare e premi **Invio**.
Lo strumento visualizza diversi messaggi mentre crea la directory di progetto e aggiunge
a essa un certo numero di directory e file.Esegue inoltre `npm install`
per installare tutte le dipendenze del progetto, come specificato in `package.json`.
Questo processo potrebbe richiedere del tempo.

5. Prima di poter creare un modello, devi accertarti che la tua directory di lavoro corrente sia la directory di livello
superiore del progetto. Per farlo, immetti questo comando:
```
cd <project directory name>
```

**Nota**: fare in modo che la tua directory di lavoro corrente sia la directory di livello superiore del progetto assicurerà che l'opzione per aggiungere modelli e origini dati sia disponibile quando apri l'API Designer. Se apri l'API Designer senza cambiare la directory, non sarai in grado di aggiungere modelli e origini dati.

Per aprire l'API Designer, completa la seguente procedura:
1. Apri una riga di comando e immetti:
```
apic edit
```
    Dopo una breve pausa, viene visualizzato questo messaggio.
    ```
    Express server listening on http://127.0.0.1:9000
    ```
    L'API Designer viene aperto nel browser web predefinito.

2. Nella pagina di accesso, immetti i tuoi ID e password {{site.data.keyword.Bluemix_notm}}. Fai clic su **Accedi**.

3. Fai clic su **Modelli**.

4. Fai clic su **Aggiungi**. Viene visualizzata la finestra **Modello** di LoopBack.

5. Immetti un nome di modello.
In generale, in un nome di modello puoi usare qualsiasi carattere alfanumerico, più i trattini e i segni di sottolineatura.

6. Fai clic su **Nuovo**.

7. Nella pagina dell'editor di modelli, vai a Proprietà e fai clic su **Aggiungi**.

8. Immetti il nome proprietà e seleziona un tipo

9. Dopo che hai finito di immettere le proprietà per il modello, fai clic su **Salva**.

Per impostazione predefinita, per un progetto LoopBack vuoto non è definita alcuna origine dati. Per definire un'origine dati, completa la seguente procedura:
1. Fai clic su **Origini dati**.

2. Fai clic sull'icona **Aggiungi**.
Viene visualizzata la finestra di nuovo **Modello** di LoopBack.

3. Immetti un nome di origine dati. In un nome di origine dati puoi usare qualsiasi carattere alfanumerico, più i trattini e i segni di sottolineatura.

4. Fai clic su **Nuovo**.
L'origine dati è presente nell'elenco di origini dati e l'editor aggiorna il file `server/datasources.json` con le impostazioni per la nuova origine dati.

5. Fai clic sull'origine dati per visualizzarne le impostazioni.

6. Modifica l'impostazione Connettore nel connettore che ti serve.

7. Torna alla console dove hai avviato l'API Designer e installa il connettore immettendo questo comando:
```
npm install --save <pacchetto-connettore>
```
    dove `<connector-package>` è il nome del pacchetto npm per il connettore LoopBack da te selezionato. Per un elenco dei pacchetti connettore consulta la seguente tabella.

**Nota:** i connettori email e in memoria sono integrati in LoopBack e non hai bisogno di installarli.

<table>
<caption>Tabella 3. Connettori LoopBack</caption>
<thead>
<tr class="style-scope doc-content doc-tr-even">
<th style="width: 50%" id="3rd_d70e1489" class="thleft style-scope doc-content">Origine dati</th>
<th style="width: 50%" id="3rd_d70e1491" class="thleft style-scope doc-content">Pacchetto connettore</th>
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
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">DB2 per zOS</td>
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
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">Sevizi web SOAP</td>
<td style="width: 50%">loopback-connector-soap</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Sevizi web REST</td>
<td style="width: 50%">loopback-connector-rest</td>
</tr>
</tbody>
</table>

Per ulteriori informazioni, consulta [LoopBack Documentation - Building a connector ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://loopback.io/doc/en/lb3/Defining-data-sources.html){:new_window}.

**Nota:** se hai selezionato il connettore Oracle, devi impostare una variabile di ambiente
in {{site.data.keyword.Bluemix_notm}} perché venga avviata l'applicazione Oracle. Per effettuare questa operazione,
completa la seguente procedura:

1. Nell'interfaccia utente {{site.data.keyword.Bluemix_notm}}, seleziona **Calcola**.

2. In Applicazioni CF, seleziona l'applicazione con cui vuoi lavorare.

3. Fai clic su **Runtime**.

4. Seleziona **Variabili di ambiente**.

5. Nella sezione Definita dall'utente, fai clic su **AGGIUNGI**.

6. Nel campo **Nome**, immetti `LD_LIBRARY_PATH`.

7. Nel campo **Valore**, immetti `$LD_LIBRARY_PATH:/home/vcap/app/node_modules/instantclient`.

8. Fai clic su **Salva**.

Per testare un progetto LoopBack, completa questa procedura:
1. Fai clic sull'icona **Avvia i server**.
Viene
visualizzato il seguente messaggio:
```
http://localhost:<4001/>Running
```
A seconda della configurazione del tuo progetto e dal fatto che siano o meno in esecuzione altri processi,
potrebbe essere visualizzato un numero porta differente.

2. Fai clic su **localhost:4001** per visualizzare l'endpoint della root API. Per il progetto LoopBack predefinito (vuoto o
hello-world), vedi qualcosa di simile a questo:
```
{"started":"2017-03-07T22:24:55.322Z","uptime":35.839}
```

Devi quindi creare un prodotto. Per ulteriori informazioni, consulta [Creazione di un prodotto](managing_products.html#create_product).
**Suggerimento**: quando avvii un nuovo prompt dei comandi, devi accertarti che la tua directory di lavoro corrente sia la directory di livello
superiore del progetto. Per farlo, immetti questo comando:
```
cd <project directory name>
```

## Disinstallazione del toolkit sviluppatori
{: #uninstall_dev_tk}

### Prerequisiti
{: #prereq_uninstall_dev_tk}

Prima di iniziare, devi arrestare le applicazioni in esecuzione in locale immettendo questo comando:
```
apic stop --all
```

Per disinstallare il toolkit di sviluppo, completa la seguente procedura:

1. Immetti il seguente comando:
```
npm rm -g apiconnect
```
{: codeblock}

2. Cancella i dati nella tua cache npm:
```
npm cache clean
```
{:codeblock}
  
Se stai utilizzando Windows:

3. Elimina tutti i file i cui nomi iniziano con `npm-` in `C:\Users\username\AppData\Local\Temp`
4. Elimina la directory `<home_dir>\.apiconnect`, dove `<home_dir>` è la directory home dell'account utente con il quale il toolkit era stato precedentemente installato.
