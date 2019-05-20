---

copyright:
  years: 2017
lastupdated: "2017-06-05"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal

subcollection: apiconnect

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Glossario
{: #glossary_apic_glossary}

Il glossario {{site.data.keyword.apiconnect_short}}
dei termini e definizioni.

- **Sviluppatore API**: uno sviluppatore API crea e configura le API, i prodotti e le politiche per le organizzazioni provider
delle quali è membro. Uno sviluppatore API può essere membro di organizzazioni provider. Lo sviluppatore API si focalizza sull'implementazione tecnica delle API più che sul creare
relazioni di business con gli sviluppatori dell'applicazione.

- **Operazione API**: un'unità di un API REST che può essere richiamata. Un'operazione API comprende un verbo HTTP e un percorso URL
subordinati alla root del contesto dell'API.

- **API Designer**: la IU per la creazione delle API.

- **API Manager**: la IU per la gestione delle API, i piani e i prodotti.

- **applicazione**: una parte del codice client che accede alle API per interagire con un servizio, sistema o contenuto. Le applicazioni sono normalmente applicazioni web o mobili.

- **assemblaggio**: l'interfaccia di programmazione dell'applicazione che fornisce una funzionalità rilevante per interagire con un'applicazione:
effettua chiamate a servizi esterni e quindi trasforma e aggrega la risposta
prima che sia trasmessa all'applicazione chiamante.

- **Catalogo**:  un catalogo è un destinazione di preparazione che si comporta come una partizione logica del gateway
e del portale sviluppatori. Gli URL per le chiamate API per il portale sviluppatori sono specifici
per un catalogo particolare.

- **ID client**:  una parte delle informazioni che identifica una singola applicazione. Un'applicazione può richiamare un'API
solo se viene trasmessa una chiave applicazione riconosciuta dal sistema {{site.data.keyword.apiconnect_short}}
e a cui è stato concesso l'accesso all'API. La chiave applicazione viene trasmessa dal client utilizzando un parametro di query HTTP.

- **segreto client**:  una parte delle informazioni utilizzata con la chiave applicazione per verificare l'identità
di un'applicazione. Un'API può essere configurata per richiedere che le applicazioni client forniscano
il loro segreti applicazione con le loro chiavi applicazione. Il segreto applicazione funziona effettivamente come una password
conosciuta soltanto dall'applicazione. Il segreto applicazione viene trasmesso dal client utilizzando un parametro di query
HTTP.

- **community**: una raccolta di organizzazioni di sviluppatori. Viene utilizzato come costrutto di raggruppamento quando si pubblicano le
API. Le community sono utilizzate per limitare la visibilità e l'accessibilità alle API.Un'API può essere pubblicata
da community selezionate, il che significa che solo gli sviluppatori dell'applicazione in quelle organizzazioni
possono visualizzare l'API.

- **Modello LoopBack**: un modello LoopBack è un oggetto JavaScript che rappresenta i dati dell'applicazione e include le regole di convalida,
le funzionalità di accesso ai dati e la logica di business. I modelli LoopBack forniscono per impostazione predefinita un'API REST
e si collegano alle origini dati per l'accesso ai dati di backend.

- **Origine dati LoopBack**: un'origine dati LoopBack è un oggetto JavaScript che rappresenta un servizio di backend come un database,
un'API REST (da utilizzare) o un servizio web SOAP. Le origini dati vengono sottoposte a backup dai connettori
e comunicano direttamente con il database o con altri servizi di backend.

- **organizzazione**: l'entità proprietaria delle API o delle applicazioni che utilizzano le API. Un'organizzazione provider che gestisce le API e i piani associati,
e che può anche essere proprietaria delle applicazioni. Un'organizzazione di sviluppatori proprietaria solo
delle applicazioni. Un'organizzazione ha almeno un proprietario. Un'organizzazione può essere un team del progetto, dipartimento
o divisione.

- **Percorso**: un percorso definisce la rotta con cui gli utenti accedono alle API REST. Un percorso è formato da una o più operazioni
HTTP come GET o POST.

- **Piano**: il costrutto di impacchettamento dal quale le API sono state rese disponibili dagli sviluppatori. Un piano rende disponibile
una raccolta di operazioni da una o più API, ed è pubblicato alle community degli sviluppatori
dell'applicazione. Gli sviluppatori dell'applicazione ottengono l'accesso alle API registrando le applicazioni per accedere ai piani. Un piano viene fornito con una raccolta di impostazioni della politica. Nel formato semplice, un piano definisce una politica di quota singola
che si applica a tutte le operazioni API a cui si accede dal piano. In
alcuni casi avanzati, possono essere associate ulteriori politiche a un piano.

- **politica**: una politica è una parte della configurazione che controlla un aspetto preciso del processo
nel server gateway durante la gestione di un richiamo API al runtime. Le politiche sono i blocchi di creazione
dei flussi di assemblaggio. Le politiche forniscono gli strumenti per configurare funzionalità, come la sicurezza,
per registrare, instradare le richieste ai servizi di destinazione e per la trasformazione dei dati da un formato
a un altro. Le politiche possono essere configurate nel contesto di un'API o nel contesto di un piano.

- **Prodotto**: i prodotti forniscono un metodo con cui puoi raggruppare le API in un pacchetto con uno scopo
di utilizzo particolare. In aggiunta, contengono dei piani, che possono essere
utilizzati per distinguere tra loro le diverse offerte. Puoi creare dei piani solo nei prodotti e tali prodotti vengono quindi pubblicati in un catalogo.

- **proxy**: l'interfaccia di programmazione dell'applicazione che inoltra le richieste a una risorsa di backend definita dall'utente
e restituisce le risposte all'applicazione chiamante.

- **pubblica**: il processo di spostamento di un'applicazione o prodotto dalla fase di preparazione in modo che i piani e le API in essa inclusi
siano disponibili per l'accesso e l'utilizzo degli sviluppatori dell'applicazione.

- **ruolo**: un ruolo definisce le autorizzazioni che possono essere abilitate funzionalmente agli utenti. Ogni ruolo dispone di una serie
di autorizzazioni differente.

- **Catalogo Sandbox**:  in un catalogo Sandbox, le approvazioni sono bypassate per la pubblicazione e le azioni del ciclo di vita. Le approvazioni in attesa
vengono annullate quando un catalogo non Sandbox viene convertito in un Sandbox. Un catalogo Sandbox
viene utilizzato per la verifica delle API che sono in fase di sviluppo.

- **definizione di sicurezza**: una definizione di sicurezza specifica tutte le impostazioni di un aspetto particolare di sicurezza dell'API;
ad esempio, il registro utente che utilizzi per l'autenticazione dell'accesso all'API.

- **Profilo SSL**: un profilo SSL viene utilizzato per rendere sicura la trasmissione dei dati tramite i siti web. I certificati SSL
garantiscono che le informazioni che invii ai siti web non saranno rubate o manomesse.

- **preparazione**: il processo di spostamento di un'applicazione o prodotto dallo stato di bozza al catalogo in preparazione della
pubblicazione.

- **sottoscrizione**:  una sottoscrizione è lo strumento con cui uno sviluppatore dell'applicazione concede l'accesso alle risorse
fornite da un'API. Uno sviluppatore dell'applicazione utilizza il portale sviluppatori per sottoscriversi ai piani
nei quali è pubblicata l'API.

- **registro utenti**: un registro utenti è il metodo di sicurezza per accedere ai cataloghi e alle API. L'utente può proteggere le API con un registro utenti
in modo che debbano essere fornite le credenziali utente quando viene richiamata un'API.

- **estensione fornitore**:  un'estensione fornitore viene aggiunta all'API REST per estendere la
specifica OpenAPI (Swagger 2.0).
