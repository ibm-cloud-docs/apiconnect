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

# Gestione delle API
{: #managing_apis}

Puoi utilizzare API Connect per gestire le API in {{site.data.keyword.Bluemix}}, anche se sono in {{site.data.keyword.Bluemix_notm}} o conservate al di fuori di {{site.data.keyword.Bluemix_notm}}. La gestione delle API ti consente di controllare l'utilizzo, aumentare l'adozione e tenere traccia delle statistiche.

Se sei un cliente, puoi gestire come
viene utilizzato nell'interfaccia utente API Manager dopo che uno sviluppatore ha creato un'API e ha eseguito il push del prodotto a {{site.data.keyword.Bluemix_notm}}. I seguenti argomenti descrivono come creare e gestire i prodotti all'interno di {{site.data.keyword.apiconnect_short}}.

## Esposizione di API installate in loco tramite un gateway sicuro
{: #expose_apis_sec_gate}

Puoi creare un gateway sicuro per esporre in sicurezza le API installate in loco in  {{site.data.keyword.apiconnect_full}}.

Quando crei un gateway sicuro, integri le funzioni del servizio {{site.data.keyword.Bluemix_notm}}
{{site.data.keyword.SecureGateway}} con {{site.data.keyword.apiconnect_short}}. Ciò significa che disponi di un metodo
sicuro per accedere alle tue API installate in loco da {{site.data.keyword.apiconnect_short}} attraverso un passaggio protetto
senza la necessità di effettuare il provisioning di un'istanza separata del servizio {{site.data.keyword.SecureGateway}}. Crei effettivamente un tunnel
a {{site.data.keyword.apiconnect_short}} su un ambiente pubblico
senza esporre i tuoi dati installati in loco. Tutto ciò che devi fare è di creare il gateway e collegarlo
a un'API. La creazione di una destinazione, del profilo SSL e dei certificati sono già stati completati per te.
Per ulteriori informazioni sul servizio {{site.data.keyword.SecureGateway}}, consulta
[About {{site.data.keyword.SecureGateway}}](../../services/SecureGateway/sg_overview.html#sg_overview).
Per creare un gateway sicuro, completa la procedura nei seguenti argomenti.

### Creazione di un gateway sicuro
{: #create_sec_gate notoc}

Quando crei un gateway sicuro, ti vengono generati un token di sicurezza e un ID gateway.
Puoi inoltre impostare un client del gateway sicuro sul tuo ambiente in loco per {{site.data.keyword.apiconnect_short}} a cui collegarti. Dopo aver configurato il client,
utilizza l'ID gateway e il token di sicurezza per collegarti al client in modo da poter accedere
alle tue API in loco.

Per creare un gateway, completa la seguente procedura:

1. Fai clic su **Passa a** <img alt="Passa all'icona" src="images/navigate_to_icon.png"> > **Ammin** > **Gateway sicuri**.
Si apre la pagina `Gateway sicuri` e viene visualizzato un tour guidato dei gateway sicuri nell'angolo
dell'interfaccia utente.

2. **Facoltativo**:
fai clic in ogni passo del tour guidato per completare la configurazione del tuo gateway.

3. Fai clic su **Aggiungi**.
Viene visualizzata la finestra di
dialogo `Crea gateway sicuro`.

4. Fornisci un nome per il gateway.
    **Nota:** sono consentiti solo caratteri alfanumerici e di sottolineatura.

5. Fai clic su **Salva**.
Il gateway viene visualizzato con l'ID gateway e il token di sicurezza.

6. Fai clic su **Configura**.
Facendo clic su **Configura** potrai scaricare e installare un client del gateway sicuro
sulla tua workstation installata in loco per connettere una rete remota a un gateway sicuro nella rete Bluemix&reg;.

    Viene visualizzata la finestra `Configura client
del gateway sicuro`.

7. Fai clic sul client da utilizzare scegliendo tra le seguenti opzioni:

    - IBM&reg; Installers
    - Docker
    - IBM DataPower&reg;

8. Segui le istruzioni su schermo per installare ed eseguire il client selezionato.
Per ulteriori informazioni sulla configurazione di un client del gateway sicuro, consulta
[Impostazione di un client](../../services/SecureGateway/sg_021.html#sg_021).

9. Al termine dell'installazione del client, chiudi la finestra **Configura client
del gateway sicuro**.

10. Aggiorna la pagina.

Il client è connesso e vengono visualizzati l'ID e lo stato del gateway. Hai completato la tua configurazione del gateway
e hai creato un gateway sicuro.
Successivamente, utilizza il gateway sicuro per accedere alle tue API in loco.

### Utilizzo del gateway sicuro con le tue API
{: #using_sec_gate_apis notoc}

Dopo aver configurato il gateway, puoi utilizzarlo con le tue API.
{:shortdesc}

Per utilizzare il tuo gateway sicuro, completa la seguente procedura:
1. Crea l'API e il prodotto come descritto nella seguente procedura.
  - Fai clic su **Passa a** <img src="images/navigate_to_icon.png" alt="Passa all'icona" /> > **Bozze** > **API** > **Aggiungi**.
  - Seleziona il tipo di API che vuoi creare.
  - Seleziona **Aggiungi un prodotto**. **IMPORTANTE**: non pubblicare ancora il prodotto.
  - Fai clic su **Crea API**.
  L'API viene visualizzata nella vista `Progettazione`.
  
2. Fai clic su **Assembla**.

3. Fai clic sulla politica **richiama** per aprire la tavolozza
**richiama**.
**LIMITAZIONE**: non è possibile utilizzare gli switch logici, come adempio `Switch`, `Operation
Switch` e `If`, con le API che usano un gateway sicuro.

4. Seleziona **Accedi all'URL tramite il gateway sicuro**.

5. Nel campo URL, aggiorna il `target-url` con il nome dell'host installato in loco
e il numero di porta. Ad esempio,
```
target-url: http://onpremdb2.rtp.raleigh.ibm.com:3055$(request.path)$(request.search)
```

6. Fai clic su **Salva** <img src="images/icon_save.png" alt="icona Salva" />.

7. Fai clic sulla scheda **Origine**.  Nota il campo `secure-gateway` con un
valore `true`.

8. Fai clic su **Tutte le API** > **Prodotti** e seleziona il prodotto creato in precedenza.

9. Fai clic sull'icona **Pubblica** per preparare il prodotto su un catalogo di tua scelta.

10. Seleziona il catalogo che vuoi utilizzare.

11. Seleziona il prodotto preparato.

12. Fai clic su **Pubblica** e seleziona **Assegnazioni
gateway sicuro**.

Hai esposto in modo sicuro la tua API installata in loco in {{site.data.keyword.apiconnect_short}}. Vengono aggiunti tutti i profili TLS
associati a una destinazione. Per controllare i profili TLS,
fai clic su **Passa a** <img src="images/navigate_to_icon.png" alt="Passa all'icona" /> > **Ammin** > **Sicurezza** > **Profili TLS**.
Puoi disporre di più gateway per ciascuna API. Decidi tu quale gateway utilizzare quando pubblichi
l'API.Se disponi già del servizio  {{site.data.keyword.SecureGateway}} con provisioning, sarai in grado di
monitorare le tue destinazioni nel dashboard {{site.data.keyword.SecureGateway}}. Tuttavia,
non puoi modificare alcuna destinazione {{site.data.keyword.apiconnect_short}} creata dal servizio
{{site.data.keyword.apiconnect_short}}.
Successivamente, verifica la tua API {{site.data.keyword.SecureGateway}}.

### Verifica la tua API del gateway sicuro
{: test_sec_gate notoc}

Dopo aver collegato il gateway a un'API, puoi verificare l'API per essere sicuro che il gateway
funzioni e che produca la risposta corretta.

Per verificare un'API utilizzando un gateway sicuro, completa la seguente procedura:

1. Fai clic su <img alt="Passa all'icona" src="images/navigate_to_icon.png" /> > **Bozze** > **API**
**<La tua API>** > **Assembla**.

2. Fai clic sull'icona **Verifica** <img src="images/test_icon.png" alt="icona Verifica"/>.

3. Seleziona un catalogo da verificare dall'elenco fornito.

4. Seleziona un gateway sicuro da verificare dall'elenco fornito.

5. Scegli un prodotto esistente dall'elenco e fai clic su **Ripubblica
prodotto**.
   **Importante** se questo prodotto è già stato pubblicato in un catalogo, sarà ripubblicato
con il nuovo gateway.

6. **Facoltativo**:
fornisci un nome per creare un nuovo prodotto e fai clic su **Crea e
pubblica**.

7. Fai clic su **Avanti**.

8. Seleziona un'operazione da richiamare dall'elenco fornito.

9. Fai clic su **Richiama**.

Vengono visualizzati i risultati della verifica.

## Preparazione e pubblicazione di un'applicazione LoopBack
{: #stage_publish_lb_app}

1. Nel riquadro di navigazione dell'API Designer, fai clic su **Prodotti**.
Viene aperta la scheda Prodotti.

2. Seleziona la versione del prodotto, accertati di fare clic sulla versione con cui vuoi lavorare.

3. Per pubblicare il runtime in {{site.data.keyword.Bluemix_notm}}, fai clic su **Pubblica**.

4. Fai clic su **Aggiungi e gestisci destinazioni** > **Aggiungi destinazione IBM Cloud**.

5. Seleziona la **Regione** {{site.data.keyword.Bluemix_notm}} in cui vuoi eseguire la pubblicazione e accedi.

6. Seleziona l'**Organizzazione** {{site.data.keyword.Bluemix_notm}} in cui vuoi eseguire la pubblicazione.

7.  Viene visualizzato un elenco di cataloghi. Seleziona il catalogo in cui vuoi eseguire la pubblicazione.

8.  Fai clic su **Avanti**.

9. Seleziona l'applicazione LoopBack che vuoi pubblicare.
Se questa è la prima volta che stai distribuendo il runtime a {{site.data.keyword.Bluemix_notm}}, aggiungi un nome e fai
clic sull'icona **Aggiungi**.

10.  Fai clic su **Salva**.

11.  Fai nuovamente clic su **Pubblica** e seleziona **Pubblica applicazione**.

12.  Fai clic su **Pubblica**.

13. Nella riga di comando, per l'API sono specificati l'URL di destinazione API e il profilo TLS (tls-profile) di richiamo API.
Annota queste informazioni. Il profilo TLS (tls-profile) di richiamo API è sempre `client:Loopback-client`, ma puoi richiamare l'URL di destinazione API come descritto nel seguente passo.
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
    Aggiornamento di notes.yaml con tls-profile e target-url.
    ```

14. Nell'interfaccia utente API Designer, completa la seguente procedura:
    1. Fai clic su **API**.
    2. Seleziona la tua API.
    3. Fai clic su **Assembla**.
    4. Nell'editor di assemblaggio, fai clic sull'icona **Politiche di filtro**.
    5. Seleziona **Politiche DataPower Gateway**.
    6. Fai clic su **Salva** per salvare l'API.

15.  Devi quindi eseguire la pubblicazione nell'API Manager. Fai clic su **Pubblica**.
    1. Seleziona **Pubblica applicazione** e scegli una delle seguenti opzioni:
	    - **Sostituisci l'applicazione esistente**: se disponi di un'applicazione pubblicata, seleziona questa opzione per sovrascrivere l'applicazione esistente.
        - **Come una nuova applicazione (utilizzando la rotta esistente)**: seleziona questa opzione per creare una nuova applicazione e forniscile un nome nel campo
**Nuova applicazione**. Il servizio non viene interrotto.

    2. Seleziona le seguenti opzioni:
	    - Prepara o pubblica prodotti
        - Seleziona specifici prodotti
        - _il tuo prodotto_
 
    3. Fai clic su **Pubblica**.

Per verificare che la pubblicazione abbia funzionato, completa la seguente procedura:

1. Accertati che l'applicazione {{site.data.keyword.Bluemix_notm}} sia in esecuzione.

2. Apri una finestra del browser e passa all'URL di destinazione API.
L'applicazione viene protetta con la convalida client. Se non fornisci il certificato client corretto, si verificherà una condizione di errore (ciò è previsto).

3. Passa all'URL {{site.data.keyword.apiconnect_short}} esposto.
Ad
esempio:
```
https://<domain>/<Bluemix org>-<Bluemix space>/<Catalog identifier>/api/notes
```
Viene visualizzata una risposta 200.

## Configurazione di un catalogo

Puoi creare un catalogo e configurare i tuoi cataloghi API Manager. I cataloghi sono utili per separare
i prodotti e le API e per verificarli prima di renderli disponibili per le organizzazioni degli sviluppatori.
Quando configuri un catalogo, puoi anche configurare il branding personalizzato in modo da non dover utilizzare
l'URL dell'API predefinito fornito da API Manager.

Per aggiungere un catalogo, completa questa procedura:

1. Fai clic su **Passa a** <img alt="Passa all'icona" src="images/navigate_to_icon.png"> > **Dashboard**.

2. Fai clic su **+ Aggiungi** > **Catalogo **.
Viene visualizzata la finestra **Aggiungi catalogo**.

3.  Immetti il nome del tuo nuovo catalogo nel campo **Nome visualizzazione**.

4. Immetti il testo che desideri formi il segmento del catalogo dell'URL, nel campo
**Nome**.
**Nota:** il campo **Nome** può contenere solo caratteri alfanumerici minuscoli (a-z
e 0-9) o i caratteri trattino (-). Un trattino non può essere utilizzato come primo o ultimo carattere nel nome.

5. Fai clic su **Aggiungi**. Il tuo catalogo è stato creato e viene visualizzato nel tuo dashboard.

6. Per configurare il catalogo, fai clic sul nome del catalogo, quindi fai clic su **Impostazioni** > **Informazioni** e procedi con i seguenti passi:
  1. Se il nuovo catalogo è un catalogo di sviluppo, seleziona **Modalità di sviluppo**.
Se selezioni la modalità di sviluppo, le azioni di preparazione e pubblicazione vengono forzate, il che significa
che se ripubblichi un prodotto precedentemente pubblicato, viene sovrascritto senza alcun avvertimento. Se vengono trovati dei conflitti,
vengono automaticamente risolti dal sistema. L'azione di annullamento della pubblicazione si verifica automaticamente.
**Nota:** le caselle di approvazione non vengono visualizzate per i cataloghi di sviluppo. Non puoi abilitare il processo di approvazione
per i cicli di vita.
  2. Se desideri abilitare la sottoscrizione automatica per il catalogo, seleziona **Sottoscrizione automatica**.
L'abilitazione della sottoscrizione automatica rende la verifica delle tue API più semplice perché viene utilizzata un'applicazione di verifica,
con un segreto e un ID client preforniti, che vengono automaticamente sottoscritti a tutti i piani nel catalogo,
in questo modo non devi specificare un piano o un'applicazione quando esegui la
verifica.**Nota:** la sottoscrizione automatica è disponibile solo per un catalogo di sviluppo.
  3. Se il catalogo è il catalogo di preparazione predefinito, seleziona **Predefinito**. Quindi,
il richiamo delle API pubblicate nel catalogo può utilizzare un URL più breve che non include il nome del catalogo
    **Nota:** Puoi selezionare **Predefinito** solo per un catalogo.
  4. **Facoltativo**: fai clic su **Endpoint** e riempi i seguenti campi:
        - **URL gateway personalizzato**: nel campo di testo URL gateway personalizzato immetti un URL. Utilizza l'URL gateway personalizzato se desideri
archiviare il branding personalizzato degli URL per le API distribuite a {{site.data.keyword.apiconnect_short}},
invece di utilizzare l'URL predefinito generato da API Manager.
        Per impostazione predefinita, l'URL gateway {{site.data.keyword.apiconnect_short}}
ha il seguente formato:
        ```
        https://gateway_cluster_hostname/organization_name/Catalog_name
        ```
        Tuttavia,
puoi sovrascrivere il valore predefinito specificando un URL più appropriato per la tua azienda;
ad esempio, `https://api.mycompany.com`. Ogni endpoint API visualizzato nel portale sviluppatori
rifletterà quindi l'URL specificato.
        **Note:**
		    - Devi configurare una voce DNS che associa i tuoi nome host e dominio personalizzati all'URL gateway predefinito.
		    - In modo che gli endpoint di un'API riflettano il tuo URL gateway personalizzato, devi configurare l'API
in modo che venga forzata dal gateway di API Connect. Per ulteriori informazioni, vedi [Specifying an alternative host for an API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){:new_window}.
		    - Assicurati che lo stesso URL gateway personalizzato non sia applicato a più cataloghi poiché il comportamento
in tale caso non è definito.
	        **SUGGERIMENTO**: quando chiami l'API, puoi anche impostare l'intestazione host HTTP della richiesta API
sul valore che hai specificato nel campo URL gateway personalizzato.

	    - **URL API personalizzato**
	    Nel campo di testo URL API personalizzato immetti l'URL. Utilizza l'URL API personalizzato per specificare l'URL
per le API distribuite a un gateway di terze parti.

	    l'URL API personalizzato rappresenta l'endpoint su cui è conosciuta l'API esternamente; che corrisponde
all'endpoint pubblicato nel portale sviluppatori e utilizzato da uno sviluppatore dell'applicazione
per richiamare o pubblicare l'API.

	    Se stai utilizzando un gateway di terze parti o un bilanciamento del carico esterno in questo catalogo, fornisci l'URL
in questo campo. Ogni endpoint API visualizzato nel portale sviluppatori
rifletterà quindi l'URL specificato. Questi endpoint sono presenti sul gateway di terze parti o sul bilanciamento del carico e creano
un indirizzo virtuale, esposto ai clienti API, associato al proxy dell'API o agli endpoint di assemblaggio dell'API
sul gateway. Gli endpoint derivati dall'URL API personalizzato sono normalmente pubblicati nei portali
sviluppatori di produzione per annunciare l'indirizzo dell'API.

	    **Nota:** se specifici un URL API personalizzato per un catalogo, ha la precedenza su tutti i nomi host che specifichi
quando configuri l'API. Per ulteriori informazioni, vedi [Specifying an alternative host for an API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){:new_window}.

	    - **Nome host per le chiamate API del portale sviluppatori**:
	    nell'area della finestra dell'endpoint API della porta, immetti un nome host per le chiamate API del portale sviluppatori. Il nome host
che immetti può essere il nome host del tuo servizio di gestione. Per accedere all'API del portale sviluppatori
nel contesto di un portale sviluppatori, devi configurare il nome host di base per le
chiamate API del portale sviluppatori. Questa azione consente a API Manager di associare il tuo nome host
all'organizzazione provider e al catalogo delle chiamate API del portale sviluppatori invece di richiederti
di ricercarli e includerli nelle tue chiamate.

7. Fai clic sull'icona **Salva**.

## Partizionamento di un catalogo

Per utilizzare la funzione di diffusione in {{site.data.keyword.apiconnect_short}}, devi abilitare gli spazi
in ogni catalogo in cui hai bisogno delle funzionalità di diffusione.

Per abilitare gli spazi in un catalogo, completa la seguente procedura:
1. Nel dashboard dell'interfaccia utente API Manager, seleziona il catalogo con cui vuoi lavorare.

2. Fai clic su **Impostazioni** > **Panoramica** e fai clic sul controllo dello slider **Spazi**.

3. Nella finestra **Abilita spazi**, fai clic su **Abilita**, e fai quindi clic sull'icona **Salva**
<img src="images/icon_save.png" alt="icona salva"/>.
Viene visualizzato un link **Gestisci spazi** sotto il controllo dello slider
**Spazi** e un link **Spazi** viene aggiunto al pannello di
navigazione. Puoi gestire i tuoi spazi facendo clic su questi link.

Gli spazi vengono abilitati per il tuo catalogo e viene creato un spazio predefinito denominato nuovo spazio.

Per ulteriori informazioni sull'utilizzo della diffusione, consulta gli argomenti del Knowledge Center, [Using syndication in IBM API Connect ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.apionprem.doc/capic_syndication_using.html){:new_window}.

## Configurazione di un portale sviluppatori
{: #config_dev_portal}

Un portale sviluppatori è l'area in cui vengono pubblicati i tuoi piani per consentire agli sviluppatori di applicazioni di accedervi e farne uso.

Puoi creare un portale sviluppatori personalizzato che gli sviluppatori di applicazioni possono utilizzare. Hai il pieno
controllo amministrativo su aspetto, contenuto, impostazioni utente e di configurazione.

Oltre a consentire agli sviluppatori di applicazioni di trovare e utilizzare le API, il portale sviluppatori
fornisce ulteriori funzioni quali forum, blog, commenti, classificazioni e un'interfaccia utente Swagger per le API.

1. Nell'interfaccia utente API Manager, seleziona il catalogo con cui vuoi lavorare.

2. Seleziona la scheda **Impostazioni**.

3. Fai clic su **Portale**.

4. Nella sezione **Configurazione portale**, seleziona **Portale sviluppatori IBM**. Viene visualizzato l'URL del portale.

5. Fai clic su **Salva**. Ti viene inviata una email che contiene un link di accesso monouso per l'utente amministrativo web del portale sviluppatori.

6. Fai clic sul link inviato nella email e attieniti alle istruzioni per reimpostare la tua password.

Il tuo portale sviluppatori è configurato. Puoi trovare l'URL per il portale sviluppatori nella
riga dell'oggetto della email che hai ricevuto. Puoi anche trovare l'URL nell'interfaccia utente API Manager facendo
clic su **Portale** > **Impostazioni**.

Per ulteriori informazioni sulle attività che puoi completare nel portale sviluppatori, consulta gli argomenti
dell'IBM Knowledge Center relativi al [portale sviluppatori ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.devportal.doc/capim_devportal_overview.html){:new_window}.

## Configurazione delle autorizzazioni per i ruoli
{: #config_permissions_roles}

Per configurare le autorizzazioni per i ruoli in API Manager, completa la seguente procedura.

1. Nel **Dashboard** API Manager, fai clic sul catalogo con cui vuoi lavorare.

2. Fare clic su **Impostazioni** > **Autorizzazioni**.
Vengono visualizzate le autorizzazioni per la gestione del prodotto a cui puoi assegnare i ruoli:
  - **Prepara**: consenti la preparazione dei prodotti nel catalogo.
  - **Visualizza**: consenti la visualizzazione e l'elenco dei prodotti nel catalogo.
  - **Gestisci**: consenti la gestione del ciclo di vita del prodotto (pubblicazione, deprecazione, ritiro e archivio).
  - **Approva**: abilita le approvazioni per le modifiche allo stato del ciclo di vita del prodotto.
**Nota:** l'approvazione per le modifiche allo stato del ciclo di vita del prodotto viene disabilitata per tutti i cataloghi di sviluppo.

3. Per aggiungere un ruolo alle autorizzazioni **Preparazione**, **Visualizzazione** o
**Gestione**, fai clic sulla corrispondente icona **+**.
Il seguente elenco mostra i ruoli disponibili predefiniti:
  - Amministratore
  - Gestore prodotto
  - Sviluppatore API
  - Editore
Il ruolo Proprietario dispone di tutte le autorizzazioni.

4. Abilita le approvazioni per le modifiche allo stato del ciclo di vita del prodotto selezionando le caselle di spunta richieste,
facendo clic sull'icona **+** corrispondente per assegnare i ruoli con
l'autorizzazione per approvare le modifiche allo stato del ciclo di vita.
Le modifiche allo stato del ciclo di vita selezionate sono quelle per cui desideri forzare l'approvazione.
Ad esempio, se selezioni Pubblicazione ma lasci la altre vuote, l'approvazione viene richiesta quando chiunque
tenta di pubblicare un prodotto ma nessuna approvazione è richiesta per le altre modifiche
allo stato del ciclo di vita.
5. Per assegnare i ruoli con i permessi per gestire le politiche definite dall'utente, fai clic sull'icona
**+** nella sezione **Gestione politica**.
Le autorizzazioni di gestione della politica vengono visualizzate, abilitandoti ad assegnare i ruoli come richiesto.
6. Fai clic sull'icona **Salva**.
