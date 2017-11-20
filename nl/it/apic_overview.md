---

copyright:
  years: 2017
lastupdated: "2017-07-18"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Informazioni su IBM API Connect

Utilizza il servizio {{site.data.keyword.apiconnect_full}} per creare
rapidamente API e microservizi basati sui runtime Java e Node.js. Una volta create, puoi gestire le tue API con controlli
a livello aziendale impostando diversi livelli di sicurezza, visibilità e limiti di frequenza quando le condividi con gli
sviluppatori di applicazioni. Il servizio {{site.data.keyword.apiconnect_short}} ti fornisce
anche gli strumenti per trasformare e ampliare la tua attività aziendale con informazioni approfondite tramite un'analisi dettagliata con
ricerche filtrate di tipo strutturato.

<object height="315" type="application/x-shockwave-flash" width="560"
data="https://www.youtube.com/v/lmxyiNMER5Y?version=3&amp;hl=en_US">
<desc>Questo video fornisce una panoramica del servizio {{site.data.keyword.apiconnect_short}} </desc>
<param name="movie" value="https://www.youtube.com/v/lmxyiNMER5Y?version=3&amp;hl=en_US"/>
<param name="allowFullScreen" value="true"/>
<param name="allowscriptaccess" value="always"/>
<param name="scale" value="noScale"/>
</object>

## Creazione di API

Con {{site.data.keyword.apiconnect_short}}, puoi
importare le API da definizioni Swagger oppure creare delle API utilizzando un URL proxy oppure
assemblando i dati da origini dati HTTP. Inoltre, {{site.data.keyword.apiconnect_short}} supporta la
creazione e la verifica di API non in linea. Nel toolkit sviluppatori è integrato un Micro Gateway che ti consente di
stabilire connessioni a origini dati back-end, come un database SQL, ed eseguire operazioni basate su creazione, lettura,
aggiornamento ed eliminazione.

Le API vengono create all'interno del toolkit sviluppatori. Il toolkit sviluppatori include una CLI e una GUI API Designer. Per accedere al toolkit sviluppatori, devi scaricarlo e installarlo da npm.
Quando installi il toolkit, inizi creando un progetto LoopBack. Il seguente diagramma illustra cosa è contenuto all'interno di un progetto LoopBack.

- **Progetto LoopBack**: il progetto LoopBack contiene l'applicazione LoopBack e il prodotto API.

- **Applicazione LoopBack**: l'applicazione LoopBack contiene l'endpoint API che fornisce l'accesso alla tua origine dati, alla risorsa aziendale o al servizio cloud.

- **Prodotto**: il prodotto è l'unità che ti consente di pubblicare le tue API. Un prodotto contiene un piano, che a sua volta contiene
l'API che richiama l'endpoint API quando viene chiamato.

Il seguente diagramma illustra dove vengono distribuiti l'applicazione LoopBack, l'API e il prodotto dopo la loro pubblicazione dall'interfaccia utente o dalla CLI del toolkit sviluppatori.

<img src="images/loopback_project.png" alt="Diagramma per mostrare cosa è contenuto all'interno di un progetto LoopBack"/>

- **Runtime {{site.data.keyword.Bluemix_short}}**:
l'applicazione LoopBack viene distribuita al runtime {{site.data.keyword.Bluemix_short}} da te scelto.

- **Gateway**: l'API viene distribuita al gateway.

**API Manager**: il prodotto viene distribuito all'API Manager dove puoi specificare come viene utilizzato.

<img src="images/Deployed.png" alt="Diagramma per mostrare dove vengono distribuiti l'applicazione LoopBack, l'API e il prodotto."/>

Per ulteriori informazioni sulle attività necessarie per creare le API, consulta [Creazione di API](creating_apis.html).

## Panoramica della gestione delle API  

Dopo che un prodotto è stato preparato e pubblicato, puoi aprire l'API Manager per gestire la sicurezza, i limiti di frequenza e le politiche e pubblicare quindi il prodotto in un portale sviluppatori.

Come visualizzato nel seguente diagramma, un prodotto contiene un piano, che contiene un'API.

<img src="images/Product.png" alt="diagramma per mostrare cosa è contenuto in un prodotto"/>

### Piani

Per rendere un'API disponibile a un cliente, è necessario che sia inclusa in un piano. I piani vengono
utilizzati per distinguere tra loro le diverse offerte. I piani possono condividere delle API, ma il fatto che l'approvazione
della sottoscrizione sia richiesta dipende dal piano stesso. Inoltre, puoi implementare dei limiti di frequenza tramite i
piani o tramite operazioni nelle API di un piano che sovrascrivono il limite di frequenza del piano.

### Prodotti

I piani e le API sono raggruppati in prodotti. Tramite i prodotti, puoi gestire la disponibilità
e la visibilità di API e piani. Utilizza l'API Designer per creare, modificare e preparare il tuo prodotto. Utilizza
l'API Manager per gestire il ciclo di vita del tuo prodotto.

Il seguente diagramma illustra come sono correlati tra loro prodotti, piani e API. Nota come i
piani appartengono solo a un singolo prodotto, possono avere API diverse per altri piani nello stesso
prodotto e possono condividere delle API con i piani da qualsiasi prodotto. Figura per mostrare la gerarchia di prodotti, piani e API. <img src="images/plan_product_hierarchy.png" alt="Figura per mostrare la gerarchia di prodotti, piani e API."/>

Puoi creare dei piani solo nei prodotti e tali prodotti vengono quindi pubblicati in un catalogo. Un responsabile
del ciclo di vita può quindi controllare la disponibilità e la visibilità di API e piani tramite
l'API Manager. Tramite il portale sviluppatori, il cliente può quindi sottoscrivere uno dei piani
a sua disposizione, come determinato nell'API Manager. L'utente può sottoscrivere solo un
singolo piano da uno specifico prodotto. Più piani in un singolo prodotto sono utili se possono
soddisfare scopi simili ma con livelli di prestazioni differenti. Ad esempio, puoi avere un
"Piano demo", che rende disponibile una singola API, e un "Piano completo", che ne rende disponibili diverse.

Oltre a controllare quali API può usare un cliente, i diversi piani possono essere utilizzati per
implementare dei limiti di frequenza. Un limite di frequenza può essere implementato come una frequenza
predefinita in un intero piano oppure per specifiche operazioni di un'API in tale piani, esentandole dal
limite di frequenza del piano. Piani diversi possono avere limiti di frequenza differenti, sia tra le operazioni che
per il limite generale. Ciò è utile per fornire livelli di servizio diversi ai clienti. Ad esempio, un "Piano demo" può
implementare un limite di frequenza di 10 chiamate al minuto mentre un "Piano completo" può consentire fino a
1000 chiamate al minuto.

**Nota:**  l'applicazione di limite di frequenza a livello del piano crea un limite di frequenza predefinito che
si applica a ciascuna operazione nel piano. Se devi impostare dei limiti di frequenza specifici per delle specifiche operazioni,
devi impostarli nelle operazioni stesse; tali impostazioni sovrascrivono quelle a livello del piano.

IBM API Connect supporta anche l'implementazione di più versioni dei prodotti. Puoi scegliere i numeri versione e utilizzarli come
ausilio nello sviluppo dei tuoi prodotti e dei tuoi piani.

**Nota:** la versione per un prodotto è distinta dalla versione delle eventuali API contenute nei piani associati. I piani non possono essi stessi avere una loro versione; utilizzano la versione del loro prodotto principale.

Per ulteriori informazioni sulle attività necessarie per gestire le API, consulta [Gestione delle API](managing_apis.html).

### Cataloghi

I prodotti devono essere preparati in un catalogo e quindi pubblicati nelle organizzazioni dello sviluppatore per diventare
disponibili per gli sviluppatori dell'applicazione. In {{site.data.keyword.apiconnect_short}}, puoi creare più cataloghi. I cataloghi sono utili per separare
i prodotti e le API e per verificarli prima di renderli disponibili per le organizzazioni degli sviluppatori.

Un catalogo è un destinazione di preparazione che si comporta come una partizione logica del gateway
e del portale sviluppatori. L'URL per le chiamate API e il portale sviluppatori sono specifici
per un catalogo particolare. In una configurazione tipica, un'organizzazione provider API utilizza un catalogo di sviluppo
per verificare le API durante lo sviluppo e un catalogo di produzione per ospitare le API
pronte per l'utilizzo completo. Un approccio comune è di disporre di un cloud di sviluppo con un catalogo di sviluppo,
alcuni cataloghi di verifica e un cloud di produzione che può avere il proprio catalogo di verifica.

#### Impostazioni del catalogo

Puoi applicare le seguenti impostazioni a un catalogo:

- **Sviluppo**: per impostazione predefinita, ti viene fornito
un catalogo di sviluppo. Un catalogo di sviluppo deve essere utilizzato solo per scopi di verifica. In un catalogo di sviluppo,
le azioni di preparazione e pubblicazione vengono forzate, il che significa
che se ripubblichi un prodotto precedentemente pubblicato, viene sovrascritto senza alcun avvertimento. Se vengono trovati dei conflitti,
vengono automaticamente risolti dal sistema. L'azione di annullamento della pubblicazione si verifica automaticamente. Quando utilizzi
lo strumento di verifica in un catalogo di sviluppo, tutti i prodotti che verifichi vengono forzati e sovrascritti dai prodotti pubblicati e preparati
anche se le operazioni stanno venendo utilizzate nel portale sviluppatori. Un portale sviluppatori
creato da un catalogo di sviluppo deve essere utilizzato solo per scopi di verifica
e non per casi reali.

- **Sottoscrizione automatica**: se abiliti la sottoscrizione automatica per un catalogo, la verifica delle tue API nell'interfaccia utente del gestore delle API
viene resa più semplice perché viene utilizzata un'applicazione di verifica,
con un segreto e un ID client preforniti, che vengono automaticamente sottoscritti a tutti i piani nel catalogo,
in questo modo non devi specificare un piano o un'applicazione quando esegui la verifica. L'applicazione di test non è soggetta ai limiti di frequenza. La sottoscrizione automatica è disponibile solo per un catalogo di sviluppo.

- **Predefinito**: puoi configurare uno dei tuoi cataloghi in modo che sia il catalogo predefinito. Quindi,
il richiamo delle API pubblicate nel catalogo può utilizzare un URL più breve che non include il nome del catalogo.

Per ulteriori informazioni sull'utilizzo del portale sviluppatori, vedi [Discovering and using APIs](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/capim_devportal_overview.dita).

### Diffusione

Con la funzione di diffusione {{site.data.keyword.apiconnect_full}},
puoi partizionare i tuoi cataloghi in spazi. Ogni spazio viene utilizzato da un team di sviluppo del provider API diverso
e con la propria serie di funzionalità di gestione correlate nello specifico
alle API che il team associato pubblica su tale spazio, abilitando ogni team a gestire
le proprie API indipendentemente.

Quando prepari o pubblichi un'API in un catalogo con gli spazi abilitati, specifichi lo spazio
all'interno del catalogo che vuoi preparare o pubblicare. Tuttavia, gli sviluppatori dell'applicazione che accedono
al portale sviluppatori per il catalogo non sono a conoscenza del partizionamento dello spazio del catalogo
e visualizzano le API come offerte coordinate.
Ogni spazio dispone dei propri gestione del ciclo di vita del prodotto, delle approvazioni di sottoscrizione e dei dati di analisi.
Utilizza il controllo di accesso specifico per lo spazio per limitare l'accesso utente a ciascuno spazio; ad esempio,
uno sviluppatore nel team Flights può preparare solo le API dello spazio Flights.

**Nota:** per impostazione predefinita, gli spazi sono disabilitati in un catalogo. Abilita gli spazi modificando le impostazioni del catalogo.

Per partizionare un catalogo, consulta [Partizionamento di un catalogo](create_catalog.html#apic_spaces).
