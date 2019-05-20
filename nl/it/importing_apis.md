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

# Importazione di API
{: #importing_apis}

Puoi utilizzare il file di definizione Swagger per aggiungere un'API REST.
{:shortdesc}

## Prerequisiti
{: #prereq_import_swagger_importing_apis}

Prima di iniziare, accertati che il tuo file sia conforme alla versione 2.0 della specifica
Swagger. Il formato del file può essere JSON o YAML.

Per aggiungere un'API REST caricando un file Swagger, completa questa
procedura:

1. Nel riquadro di navigazione dell'interfaccia utente API Manager, fai clic su **Bozze** e fai quindi clic su
**API**.
Viene aperta la scheda API.

2. Fai clic su **+ Aggiungi** e seleziona quindi **Swagger 2.0** dalla sezione
**Importa**.
Viene visualizzata la finestra **Importa API Swagger**.

3. **Facoltativo**:
per caricare un file dal tuo file system locale, fai clic su **Seleziona file** e,
nel tuo file system, seleziona il file che vuoi utilizzare. I file `.json`,
`.yml` e `.yaml` sono supportati se contengono una definizione
Swagger valida.

4. **Facoltativo**:
per caricare un file da un URL, fai clic su **O importa da URL** e fornisci
quindi l'URL corretto nel campo **URL** che viene presentato. Se per accedere
all'URL è richiesta l'autenticazione, fornisci un nome utente e una password. I file `.json`,
`.yml` e `.yaml` sono supportati se contengono una definizione
Swagger valida.

5. Fai clic su **Importa**.
Viene creata una nuova definizione di API REST; compresi percorsi e operazioni HTTP.

Una volta importata, la definizione di API viene visualizzata nell'elenco di definizioni API
nella scheda **API** della pagina **Bozze**.
Puoi quindi modificare la tua definizione di API come faresti con qualsiasi altra definizione di API REST.

## Importazione di API da IBM Integration Bus
{: #tut_import_iib_apic_importing_apis}

Questa esercitazione ti consente di importare le API REST create con IBM Integration Bus in {{site.data.keyword.apiconnect_full}}, semplificandone così la gestione e la pubblicazione. 
{: shortdesc}

Prima di iniziare, assicurati che il tuo file dell'API REST sia conforme alla versione 2.0 della specifica Swagger. Il formato del file può essere JSON o YAML.

Puoi utilizzare IBM Integration Bus per creare le API REST, ossia
delle applicazioni specializzate che possono essere utilizzate per esporre le integrazioni in forma di servizio Web RESTful e
possono essere richiamate dai client HTTP. Dopo aver creato le API, puoi importarle in {{site.data.keyword.apiconnect_short}} per la loro gestione e pubblicazione.

Di seguito sono elencati alcuni vantaggi della gestione delle tue API in {{site.data.keyword.apiconnect_short}}:
* Puoi monitorare il numero di chiamate alla tua API.
* Puoi controllare il numero di chiamate alla tua API.
* Puoi mantenere più versioni di una API.

Per ulteriori vantaggi, vedi [Gestione delle API](/docs/services/apiconnect?topic=apiconnect-managing_apis).

Per creare un'API REST in IBM Integration Bus e importarla
in {{site.data.keyword.apiconnect_short}}, completa la seguente
procedura:
1. Crea l'API REST utilizzando IBM Integration Bus. Limitazione: puoi creare un'API REST solo utilizzando IBM Integration Toolkit, che viene fornito con la versione installata di IBM Integration Bus.
	1. Crea un'API REST utilizzando IBM Integration
		Toolkit. Per ulteriori informazioni su come completare le attività per la creazione di un'API REST con IBM Integration Bus, consulta [Developing integration solutions by using REST APIs ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSMKHH_10.0.0/com.ibm.etools.mft.doc/bi12016_.htm){: #new_window} nel IBM Knowledge Center.
		
	2. Apri la procedura guidata di creazione di un'API REST selezionando **File** > **Nuovo** > **API REST**.
		
	3. Immetti un nome per l'API REST. Il nome specificato viene utilizzato come nome del progetto
  in IBM Integration Toolkit.
		
	4. Seleziona uno dei seguenti metodi di creazione dell'API REST e completa la procedura:
		
	**Inizia da zero utilizzando l'Editor API REST fornito con IBM Integration Toolkit**:
		1. Seleziona **Crea un'API REST e definisci le risorse e le operazioni**.
		2. Fai clic su **Fine**. L'Editor API REST si aprirà automaticamente per la nuova API REST e dovrai utilizzarlo per definire risorse, modelli e operazioni.
		
	**Inizia da un documento Swagger 2.0 esistente**:
		1. Seleziona **Importa risorse e operazioni definite in un documento Swagger** e fai clic su **Avanti**.
		2. Seleziona il percorso del documento Swagger che descrive le risorse e le operazioni che desideri utilizzare nell'API REST. Puoi importare il documento Swagger dal file system o da un progetto esistente nello spazio di lavoro. Il file viene convalidato per l'utilizzo in un'API REST. Se durante la convalida del documento Swagger selezionato vengono riscontrati degli errori, questi errori di convalida vengono visualizzati all'inizio della procedura guidata. Se nel documento Swagger selezionato ci sono degli errori di convalida non puoi continuare con le operazioni.
		3. Seleziona **Fine** per creare l'API.
	5. Implementa i flussi secondari per la tua API REST, che sono le operazioni REST che desideri includere.
2. Aggiungi il progetto API REST a un file BAR (broker archive) nuovo o esistente di IBM Integration Bus.
3. Distribuisci il file BAR in IBM Integration Bus on Cloud.
	1. Accedi a IBM Integration Bus on Cloud utilizzando il tuo ID IBM. Registra un account (se non ne hai uno).
	2. Fai clic su **Aggiungi integrazione** > **Carica file BAR**.
	3. Seleziona il file BAR che hai creato per il tuo progetto API REST. Suggerimento: puoi trovare la posizione del tuo file BAR facendo clic con il tasto destro del mouse su di esso in IBM Integration Toolkit e visualizzandone le proprietà.
	4. Seleziona **Salva**.
	5. Seleziona **Aggiorna elenco** per aggiornare la schermata.
	6. Verifica che il file BAR sia stato caricato correttamente visualizzando il flusso di integrazione API per l'API nella finestra *Integrations* di IBM Integration Bus on Cloud.
4. Avvia il flusso di integrazione selezionando l'icona di avvio ![Acquisizione schermo che mostra l'icona di avvio](images/a_play_button.jpg " "). L'API viene avviata e visualizza lo stato `Running`.
5. Seleziona l'integrazione dall'elenco per visualizzare le relative informazioni. La struttura ad albero nel menu Contenuti visualizza l'API REST e i flussi secondari associati. Puoi visualizzare informazioni anche in altre sezioni. Nella sezione Endpoint pubblici, puoi
visualizzare l'URL pubblico assegnato da IBM Integration Bus on Cloud
al tuo flusso di integrazione. Seleziona **Mostra URL completo** per visualizzare l'URL completo per tale operazione.
6. Copia l'URL completo dell'operazione negli appunti. Ti servirà durante la configurazione dell'API per lavorare con {{site.data.keyword.apiconnect_short}}. Se hai abilitato l'autenticazione di base, prendi nota anche del nome utente e password assegnati.

### Integra IBM Integration Bus con API Connect.
{: #integrateiibapic_importing_apis}

1. Importa il file Swagger associato al progetto API REST in IBM Integration Toolkit all'interno del servizio {{site.data.keyword.apiconnect_short}}. 
	1. Accedi al tuo servizio {{site.data.keyword.apiconnect_short}} {{site.data.keyword.Bluemix_notm}}.
	2. Nel riquadro di navigazione dell'interfaccia utente API Manager, seleziona **Bozze** > **API**. Viene aperta la scheda API.
	3. Seleziona **+ Aggiungi** > **Importa API da un file o URL**. Viene visualizzata la finestra *Importa OpenAPI (Swagger)*.
	4. Per caricare il file da te creato dal tuo file system locale, fai clic su **Seleziona file** e seleziona il file che hai creato con IBM Integration Bus. I file con estensione `.json`, `.yml` e `.yaml` sono supportati se contengono una definizione Swagger valida. Assicurati che l'opzione **Aggiungi un prodotto** sia selezionata. Facoltativamente, puoi pubblicare il prodotto selezionando **Pubblica questo prodotto in un catalogo**.
	5. Fai clic su **Importa**. Viene creata una nuova definizione di API REST; compresi percorsi e operazioni HTTP. Suggerimento: se l'operazione di importazione impiega più di un minuto, annulla l'importazione, aggiorna il browser e tenta di nuovo l'operazione. La tua sessione potrebbe essere scaduta.
2. Associa l'API importata in {{site.data.keyword.apiconnect_short}} all'API in IBM Integration Bus on Cloud.
	1. Vai al Dashboard di {{site.data.keyword.apiconnect_short}}.
	2. Seleziona **Bozze** > **API**.
	3. Fai clic sull'API REST importata.
	4. Seleziona la scheda Assembla e fai clic su **Crea assemblaggio** per aggiungere la politica di proxy.
	5. Trascina la politica di **Proxy** alla nuova politica vuota per abilitarla.
	6. Incolla l'URL dell'API che hai copiato dalla sezione Endpoint pubblici di IBM Integration Bus on Cloud.
	7. Se hai abilitato l'autenticazione di base per la tua API REST, immetti il nome utente e password generati in IBM Integration Bus on Cloud.
	8. Salva le impostazioni dell'API.
3. Verifica l'API.
	1. Nella scheda Assembla della tua API, seleziona il pulsante Verifica ![Pulsante Verifica](images/a_play_button.jpg "Acquisizione schermo che mostra l'icona del pulsante di verifica.").
	2. Seleziona **Ripubblica prodotto**.
	3. Seleziona l'operazione.
	4. Immetti i parametri richiesti.
	5. Seleziona **Invoke**.
	6. Verifica di ricevere la risposta prevista dall'API. 
	
Una volta che la definizione API è stata importata e integrata, puoi gestire e regolare le API come qualsiasi altra definizione API REST. Per ulteriori informazioni sulle API, consulta [Gestione delle API](/docs/services/apiconnect?topic=apiconnect-managing_apis).

## Pubblicazione delle API create con IBM App Connect Professional in IBM API Connect
{: #publish_importing_apis}

Con questa esercitazione puoi pubblicare e gestire le API REST che crei con IBM App Connect Professional con {{site.data.keyword.apiconnect_full}}.

### Prerequisiti
{: #prereq_pub_api_appconn_importing_apis}

Hai bisogno di account validi per IBM App Connect
Professional on Cloud e per {{site.data.keyword.apiconnect_short}} per completare questa esercitazione. Assicurati che il tuo file API REST
sia conforme alla versione 2.0 della specifica Swagger. Il formato del file può essere JSON o
YAML.

Puoi utilizzare IBM App Connect Professional per creare le API REST,
ossia delle applicazioni specializzate che possono essere utilizzate per esporre le integrazioni in forma di servizio Web RESTful e
possono essere richiamate dai client HTTP. Dopo aver creato le API, puoi pubblicarle e gestirle utilizzando
{{site.data.keyword.apiconnect_short}}.
Di seguito sono elencati alcuni vantaggi della gestione delle tue API in {{site.data.keyword.apiconnect_short}}:

- Puoi monitorare il numero di chiamate alla tua API.
- Puoi controllare il numero di chiamate alla tua API.
- Puoi mantenere più versioni di una API.

Per ulteriori vantaggi, vedi [Gestione delle API](/docs/services/apiconnect?topic=apiconnect-managing_apis).
Per creare un'API REST in IBM App Connect Professional e pubblicarla in
{{site.data.keyword.apiconnect_short}}, completa la seguente
procedura:

1. Crea l'API REST utilizzando IBM App Connect
Professional.
  - Accedi alla [App Connect Professional Web Management Console ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/app-connect){:new_window} con il tuo ID IBM. Per ulteriori informazioni su come completare le attività per la creazione di un'API REST con IBM App Connect Professional Web Management Console, consulta [About management console settings ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SS3LC4_7.5.2.0/com.ibm.wci.appliance.doc/About_the_WMC/consoleSettings.html){:new_window} nel IBM Knowledge Center.
  - Seleziona la scheda Production, se non lo è già.
  - Seleziona **Repository** > **Configurazioni** nel pannello di navigazione.
  - Nella schermata Project Configurations, seleziona il progetto che stai pubblicando in {{site.data.keyword.apiconnect_short}}.  Vengono visualizzati i dettagli del progetto che sta venendo pubblicato.
  - Seleziona **Push to API Management**. 
      **Suggerimento**: il pulsante **Push to API Management** è attivo solo quando il progetto che stai importando ha lo stato in esecuzione o distribuito. Seleziona il pulsante di riproduzione per avviare il progetto, se il link non è visualizzato.
  - Nella schermata Push to API Management, immetti le seguenti informazioni per creare una connessione al sistema di gestione API.

  <table><caption>Tabella 1. Informazioni di connessione per la pubblicazione dell'API in {{site.data.keyword.apiconnect_short}}</caption>
  <thead>
  <tr>
  <th>Nome campo</th>
  <th>Descrizione</th>
  </tr>
  </thead>
  <tbody>
  <tr><td>Host</td>
  <td>Specifica il nome host dell'indirizzo cloud, del server o del cluster di gestione. Per {{site.data.keyword.Bluemix_notm}}, questa voce è molto probabilmente us.apiconnect.ibmcloud.com.</td>
  </tr>
  <tr>
  <td>Porta</td>
  <td>Specifica il numero di porta necessario per la connessione all'indirizzo cloud, al server o al cluster di gestione.</td>
  </tr>
  <tr><td>ID utente</td>
  <td>Specifica il nome utente di autenticazione utilizzato per l'accesso all'indirizzo cloud, al server o al cluster di gestione. Questo è molto probabilmente il tuo ID IBM che hai utilizzato per accedere a {{site.data.keyword.Bluemix_notm}}.</td>
  </tr>
  <tr><td>Password</td>
  <td>Specifica la password di autenticazione utilizzata per l'accesso
all'indirizzo cloud, al server o al cluster di gestione. Questa è molto probabilmente la tua password dell'ID IBM che hai utilizzato per accedere a
  {{site.data.keyword.Bluemix_notm}}.</td>
  </tr>
  </tbody>
  </table>

2. Seleziona **Load Organizations** per popolare l'elenco delle organizzazioni associate
alla tua password e al tuo ID.

3. Seleziona **Organizations** per associare il progetto a una delle organizzazioni
disponibili.

4. Seleziona **Push to APIM** e quindi **Ok**.

5. Seleziona **Close** per chiudere la finestra.
Si apre una nuova finestra nel tuo browser predefinito e viene visualizzata la tua API.

Associa l'API IBM App Connect a {{site.data.keyword.apiconnect_short}}.

#### Importa la definizione Swagger API
{: #import_sw_importing_apis}

Per importare il file Swagger associato al progetto dell'API REST in IBM App Connect nel servizio {{site.data.keyword.apiconnect_short}}, segui questa procedura:

1. Accedi al tuo servizio {{site.data.keyword.apiconnect_short}} {{site.data.keyword.Bluemix_notm}}.

1.  Nella barra del titolo della IU API Manager, seleziona **Passa a** > **Bozze**.

2. Seleziona **APIs** nella barra del menu.
Viene aperta la scheda API.

3. Seleziona la tua API importata per aprire API Designer.

4. Seleziona **Assemble** nella finestra di navigazione.
Viene visualizzato un elenco di politiche nella finestra di navigazione.

5. Seleziona **Create assembly**, se necessario.

6. Aggiungi la politica **Invoke** trascinandola nel tuo assemblaggio nella finestra principale.

7. Seleziona la politica **Invoke** nella finestra principale per modificarne le impostazioni di configurazione.

8. Configura l'host/percorso di base nel campo URL con le seguenti informazioni:

- **nome host**: impostazione che dipende dalla tua istanza cloud. Per ulteriori informazioni su questa impostazione, vedi
[IBM App Connect Professional ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/en/SS3LC4_7.5.2.0/mapfiles/ic_home.html){:new_window}.

- **Percorso di base**: il percorso che specifichi nella nota httpReceive Request nell'orchestrazione App Connect Professional.

9. Aggiungi e salva la tua password e il tuo nome utente dell'ID IBM nei dettagli di autenticazione di base HTTP che utilizzi
per App Connect Professional.

#### Verifica l'API
{: #test_importing_apis}

Per verificare l'API, segui questa procedura:

1. Nella scheda Assembla della tua API, seleziona il pulsante Verifica <img alt="Acquisizione schermo che mostra l'icona del pulsante di verifica" src="images/a_play_button.jpg" />.
2. Seleziona **Ripubblica prodotto**.
3. Seleziona l'operazione.
4.  Immetti i parametri richiesti.
5. Seleziona **Invoke**.
6. Verifica di ricevere la risposta prevista dall'API.

Una volta che la definizione API è stata importata e integrata, puoi gestire e regolare le API
a tuo piacimento come con qualsiasi altra definizione API REST. Per ulteriori informazioni sulle API, consulta [Gestione delle API](/docs/services/apiconnect?topic=apiconnect-managing_apis).


