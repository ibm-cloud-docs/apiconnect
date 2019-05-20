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

# Configurazione di un catalogo
{: #create_catalog}

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
L'abilitazione della sottoscrizione automatica rende più semplice l'esecuzione
dei test delle tue API in quanto viene utilizzata un'applicazione di test
con un segreto e un ID client preforniti. L'applicazione di test viene automaticamente sottoscritta a tutti i piani nel catalogo,
in questo modo non devi specificare un piano o un'applicazione quando esegui la verifica. 
    **Nota:** la sottoscrizione automatica è disponibile solo per un catalogo di sviluppo.
  3. Se il catalogo è il catalogo di preparazione predefinito, seleziona **Predefinito**. Quindi,
il richiamo delle API pubblicate nel catalogo può utilizzare un URL più breve che non include il nome del catalogo.
    **Nota:** puoi selezionare **Predefinito** solo per un catalogo.
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
in modo che venga forzata dal gateway di API Connect. Per ulteriori informazioni, vedi [Specifying an alternative host for an API ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){: #new_window}.
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
quando configuri l'API. Per ulteriori informazioni, vedi [Specifying an alternative host for an API ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){: #new_window}.

	    - **Nome host per le chiamate API del portale sviluppatori**:
	    nell'area della finestra dell'endpoint API della porta, immetti un nome host per le chiamate API del portale sviluppatori. Il nome host
che immetti può essere il nome host del tuo servizio di gestione. Per accedere all'API del portale sviluppatori
nel contesto di un portale sviluppatori, devi configurare il nome host di base per le
chiamate API del portale sviluppatori. Questa azione consente a API Manager di associare il tuo nome host
all'organizzazione provider e al catalogo delle chiamate API del portale sviluppatori invece di richiederti
di ricercarli e includerli nelle tue chiamate.

7. Fai clic sull'icona **Salva**.

## Partizionamento di un catalogo
{: #apic_spaces_create_catalog}

Per utilizzare la funzione di diffusione in {{site.data.keyword.apiconnect_short}}, devi abilitare gli spazi
in ogni catalogo in cui hai bisogno delle funzionalità di diffusione.

Per abilitare gli spazi in un catalogo, completa la seguente procedura:
1. Nel dashboard dell'interfaccia utente API Manager, seleziona il catalogo con cui vuoi lavorare.

2. Fai clic su **Impostazioni** > **Panoramica** e fai clic sul controllo del dispositivo di scorrimento **Spazi**.

3. Nella finestra **Abilita spazi**, fai clic su **Abilita**, e fai quindi clic sull'icona **Salva**
<img src="images/icon_save.png" alt="icona salva"/>.
Viene visualizzato un link **Gestisci spazi** sotto il controllo del dispositivo di scorrimento
**Spazi** e un link **Spazi** viene aggiunto al pannello di
navigazione. Puoi gestire i tuoi spazi facendo clic su questi link.

Gli spazi vengono abilitati per il tuo catalogo e viene creato un spazio predefinito denominato nuovo spazio.

Per ulteriori informazioni sull'utilizzo della diffusione, consulta gli argomenti del Knowledge Center, [Using syndication in IBM API Connect ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.apionprem.doc/capic_syndication_using.html){: #new_window}.
