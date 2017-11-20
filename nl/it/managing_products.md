---
copyright:
  years: 2017
lastupdated: "2017-09-25"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Gestione dei prodotti

Per informazioni dettagliate sulle modalità in cui puoi gestire i tuoi prodotti, nella documentazione dell'IBM&reg; Knowledge Center consulta
[Managing your Products ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.apionprem.doc/task_product_management.html){:new_window}.

## Ciclo di vita del prodotto
{: #prod_lifecycle}

Quando gestisci le tue versioni del prodotto, le fai passare per una serie di stati del
ciclo di vita, dalla preparazione iniziale di una bozza della versione del prodotto a un ambiente, fino
ad arrivare alla pubblicazione, per rendere la versione del prodotto disponibile ai tuoi sviluppatori delle
applicazioni, e all'eventuale ritiro o archiviazione. La tabella e il diagramma di seguito descrivono i vari
stati del ciclo di vita del prodotto per una versione del prodotto.

<table summary="" id="apic_004__table_lym_rxj_gv" class="defaultstyle"><caption class="style-scope doc-content">Tabella 1. Stati del ciclo di vita del prodotto di gestione API</caption>
<thead class="style-scope doc-content">
<tr class="style-scope doc-content doc-tr-even">
<th style="width: 11.25%" id="d3569e1968" class="thleft thbot style-scope doc-content">Stato</th>
<th style="width: 88.75%" id="d3569e1970" class="thleft thbot style-scope doc-content">Descrizione</th>
</tr>
</thead>
<tbody class="style-scope doc-content">
<tr class="style-scope doc-content doc-tr-odd">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">Bozza</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">Il prodotto non viene distribuito e non è associato a un catalogo API Connect.</td>
</tr>
<tr class="style-scope doc-content doc-tr-even">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">Preparato</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">Una copia immutabile della versione del prodotto viene distribuita all'ambiente
di destinazione. Quello di "Preparato" è lo stato iniziale quando prepari una bozza del prodotto. Quando un
prodotto è nello stato "Preparato", non è ancora visibile, o sottoscrivibile, per gli sviluppatori.</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">Pubblicato</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">La versione del prodotto è visibile, e sottoscrivibile, per gli sviluppatori o le community di destinazione.</td>
</tr>
<tr class="style-scope doc-content doc-tr-even">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">Obsoleto</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">La versione del prodotto è visibile solo agli sviluppatori le cui applicazioni
sono attualmente sottoscritte. Non sono possibili nuove sottoscrizioni del prodotto.</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">Ritirato</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">La versione del prodotto non può essere visualizzata o sottoscritta, e tutte le API
associate vengono arrestate. Una versione del prodotto ritirata viene visualizzata per impostazione predefinita
nella pagina Prodotti nell'interfaccia utente API Manager. </td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">Archiviato</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">La versione del prodotto non può essere visualizzata o sottoscritta, e tutte le API
associate vengono arrestate. La versione del prodotto non viene visualizzata per impostazione predefinita
nella pagina Prodotti nell'interfaccia utente API Manager. </td>
</tr>
</tbody>
</table>

### Flussi del ciclo di vita del prodotto

Il seguente diagramma mostra i possibili stati
del ciclo di vita per una versione del prodotto e le operazioni di gestione prodotto che fanno passare una
versione del prodotto da uno stato del ciclo di vita all'altro; ad esempio, l'operazione Ritira sposta una
versione del prodotto dallo stato Pubblicato a quello Ritirato.

<img alt="Diagramma degli stati del ciclo di vita per la versione del prodotto" src="images/apic_plan_lifecycle.png">


## Creazione di un prodotto
{: #create_product}

Crea un prodotto per raccogliere un set di API e piani in una singola offerta che rendi disponibile per
i tuoi sviluppatori. Un piano include delle impostazioni di limite di frequenza che possono essere applicate al piano nel suo insieme oppure specificate per ciascuna operazione in un'API. Tramite i prodotti e i piani, hai un maggiore controllo su quali sono le API a cui hanno accesso i tuoi sviluppatori. Dopo che hai creato un prodotto, è necessario prepararlo. La preparazione di un prodotto lo fa passare a uno stato attivo che ti consente di richiamare e verificare le API in esso incluse. Quando un prodotto viene preparato, non è ancora visibile agli sviluppatori.

**Suggerimento**: oltre a utilizzare il metodo descritto in questa attività, puoi anche creare un prodotto quando
crei un'API. Se crei un'API utilizzando l'interfaccia riga di comando Toolkit sviluppatori, un prodotto viene
creato automaticamente per tuo conto. Puoi quindi modificare qualsiasi specifica impostazione aprendo il nuovo prodotto
nella pagina **Prodotti** dell'API Designer.

Per creare un prodotto utilizzando l'API Designer, completa la seguente procedura:
1. Per aprire l'interfaccia utente API Designer, apri una riga di comando e immetti il seguente comando:
```
apic edit
```
L'API Designer viene aperto nel tuo browser predefinito.

2. Nel riquadro di navigazione dell'API Designer, fai clic su **Prodotti**.
Viene aperta la scheda Prodotti.

3. Fai clic su **Aggiungi** e quindi fai clic su **Nuovo prodotto**.
Viene visualizzata la finestra Aggiungi un nuovo prodotto.

4. Completa i seguenti campi:
    - Titolo
    - Nome
    - Versione

5. Fai clic su **Aggiungi**.
Viene aperta la scheda Progettazione per il nuovo prodotto.

6. **Facoltativo**:
immetti le informazioni relative a descrizione, contatto, licenza e condizioni per l'utilizzo del servizio per il prodotto
nella sezione **Informazioni**.

7. Nella sezione **Visibilità**, specifica gli utenti per cui desideri sia visibile
il prodotto. Puoi scegliere **Pubblici**, **Utenti autenticati**
o **Personalizzato**. Se selezioni **Personalizzato**,
utilizza il campo **Tipo da aggiungere** per cercare le organizzazioni o le community di
sviluppatori per cui desideri che siano visibili i piani nel prodotto.

    **Nota:**
    per cercare organizzazioni o community di sviluppatori, il nome prodotto deve essere nello stato
di preparato, pubblicato od obsoleto. Se il catalogo in cui è preparato, pubblicato od obsoleto
non è un catalogo sandbox, non puoi apportare altre modifiche al prodotto mentre è in uno di
questi stati. Per ulteriori informazioni, consulta [Ciclo di vita del prodotto](#prod_lifecycle}).

8. Specifica gli utenti che possono sottoscrivere il prodotto. Puoi scegliere **Utenti
autenticati ** o **Personalizzato**. Se selezioni **Personalizzato**,
usa il campo **Tipo da aggiungere** per cercare le organizzazioni o le community di sviluppatori
che desideri possano sottoscrivere i piani nel prodotto.

9. Nella sezione API, specifica le API che vuoi includere nel prodotto.
    1. Fai clic sull'icona **Aggiungi API**.
    2. Seleziona le API che vuoi includere e fai quindi clic su **Applica**. Le
API selezionate vengono elencate.

10. Per rendere un'API disponibile agli sviluppatori di applicazioni, devi includerla in un piano. Per aggiungere
uno o più piani al prodotto, fai clic sull'icona **Aggiungi piano**.
    1. Espandi il nuovo piano che è stato creato. Se già hai aggiunto delle API al tuo prodotto,
esse vengono incluse automaticamente.
    2. Ridenomina il tuo piano nei campi **Titolo** e **Nome** e,
facoltativamente, aggiungi una descrizione.
    **Nota:** un piano predefinito viene creato automaticamente per tuo conto e puoi includere la tua
API in questo piano, se non vuoi crearne uno tuo. Tuttavia, se decidi di non utilizzare il piano
predefinito, devi eliminarlo, poiché non è possibile preparare un prodotto se comprende dei piani che non includono delle API.

11. Verifica che le API da te richieste siano incluse nel piano.
    1. Espandi il piano in cui vuoi aggiungere un'API.
    2. Sotto API incluse, accertati che le caselle di spunta delle API da te richieste siano selezionate. Se ci
sono delle API già selezionate, e non desideri includerle nel piano che stai mettendo a punto,
deseleziona tali caselle di spunta.

12. **Facoltativo**:
aggiungi le informazioni di fatturazione al tuo piano. Per aggiungere le informazioni di fatturazione, devi creare un account con un servizio di elaborazione della carta di credito in modo che i tuoi clienti possano pagare con una carta di credito. I piani di fatturazione mensile vengono addebitati nella stessa data per ogni mese.

13. **Facoltativo**:
se vuoi personalizzare quali operazioni da un'API sono incluse nel piano, passa il puntatore del
mouse sull'API che contiene l'operazione. Fai clic sull'icona **Visualizza operazioni** e
quindi seleziona o deseleziona le caselle di spunta per le operazioni che vuoi includere o escludere.

14. **Facoltativo**:
per aggiungere un limite di frequenza al tuo piano, deseleziona la casella di spunta **Illimitato** e
specifica quindi il limite di frequenza che vuoi applicare. Se la casella di spunta **Applica limite rigido**
è selezionata, il piano impedirà alle applicazioni di richiamare l'API dopo che è stato raggiunto il limite di frequenza;
altrimenti, verrà presentata un'avvertenza.

    **Nota:**  l'applicazione di limite di frequenza a livello del piano crea un limite di frequenza predefinito che
si applica a ciascuna operazione nel piano. Se devi impostare dei limiti di frequenza specifici per delle specifiche operazioni,
devi impostarli nelle operazioni stesse; tali impostazioni sovrascrivono quelle a livello del piano.

15. **Facoltativo**:
specifica se il tuo piano richiede l'approvazione della sottoscrizione. Se vuoi che le sottoscrizioni
da parte degli sviluppatori richiedano l'approvazione tramite l'interfaccia utente API Manager,
seleziona **Richiedi approvazione della sottoscrizione**; altrimenti, accertati che la casella di spunta sia deselezionata.

16. **Facoltativo**:
aggiungi un limite di frequenza a un'operazione.
    1. Punta il cursore del mouse sull'API che contiene l'operazione e fai clic sull'icona **Visualizza operazioni**.
    2. Punta il cursore del mouse sull'operazione a cui vuoi applicare un limite di frequenza. fai clic sull'icona **Modifica limite di frequenza**.
    3. Accertati che la casella di spunta **Illimitato** sia deselezionata e specifica quindi il limite di frequenza
che desideri applicare. Se la casella di spunta **Applica limite rigido**
è selezionata, il piano impedirà alle applicazioni di richiamare l'API dopo che è stato raggiunto il limite di frequenza;
altrimenti, verrà presentata un'avvertenza.

- Fai clic sull'icona **Salva** per salvare le modifiche da te apportate.

Hai creato un prodotto e specificato un set di API e piani in una singola offerta che puoi ora rendere disponibile ai tuoi sviluppatori.
Procedi quindi alla preparazione del tuo prodotto in un catalogo. Per ulteriori informazioni, consulta [Preparazione di un prodotto](#stage_product}).


## Preparazione di un prodotto
{: #stage_product}

Prepara un prodotto per crearne una specifica versione in un catalogo prima della pubblicazione. Quando un
prodotto è nello stato "Preparato", non è ancora visibile, o sottoscrivibile, per gli sviluppatori.

**Nota:** l'interfaccia utente API Manager include anche la capacità di preparare prodotti; tuttavia, il metodo
preferito per tali attività consiste nell'utilizzare l'interfaccia utente API Designer, come descritto nella seguente procedura.

1. Nel riquadro di navigazione dell'API Designer, fai clic su **Prodotti**.
Viene aperta la scheda Prodotti.

2. Fai clic sul **Prodotto** con cui vuoi lavorare. Se hai più di una
versione del prodotto, accertati di fare clic sulla versione con cui vuoi lavorare.

3. Fai clic sull'icona **Pubblica**.

4. Se il catalogo in cui vuoi preparare il prodotto viene visualizzato nell'elenco:
    1. Seleziona il catalogo di cui hai bisogno.  
    2. Seleziona **Prepara solamente (i prodotti non verranno pubblicati)**, seguito da **Pubblica**. Il tuo prodotto è stato preparato.

5. Se il catalogo in cui vuoi preparare il prodotto non è visualizzato nell'elenco:
    1. Fai clic su **Aggiungi e gestisci destinazioni**.
    2. Fai clic su **Aggiungi destinazione IBM Bluemix**.
    3. Seleziona la **Regione** {{site.data.keyword.Bluemix_short}}
in cui vuoi eseguire la pubblicazione.
    4. Seleziona l'**Organizzazione** {{site.data.keyword.Bluemix_short}} in cui vuoi eseguire la pubblicazione.
    5. Viene visualizzato un elenco di cataloghi. Seleziona il catalogo in cui vuoi eseguire la pubblicazione.
    6. Fai clic su **Avanti**.
    7. Se hai un'applicazione LoopBack che vuoi pubblicare, seleziona l'applicazione in cui eseguire la pubblicazione.
Altrimenti, seleziona **Nessuno**.
    8. Fai clic su **Salva**.
    9. Fai nuovamente clic su **Pubblica** e seleziona la destinazione che hai appena aggiunto.
    10. Seleziona il catalogo richiesto
    11. Seleziona **Prepara solamente**.
    12. Fai clic su **Pubblica**.

Il tuo prodotto è stato preparato in un catalogo. Per visualizzare lo stato del prodotto nel catalogo, apri
l'interfaccia utente API Manager, seleziona la sezione Dashboard nel riquadro di navigazione e fai clic sul catalogo
richiesto. Il prodotto viene visualizzato con uno stato di Preparato.

- Apri il **Dashboard** {{site.data.keyword.Bluemix_short}}. Nella sezione Applicazioni vedrai il tile dell'applicazione.

Apri l'API Manager per pubblicare il tuo prodotto in una community per consentire agli sviluppatori di applicazioni di accedervi nel portale sviluppatori. Per ulteriori informazioni, consulta [Pubblicazione di un prodotto](#publish_proj}).


## Pubblicazione di un prodotto
{: #publish_proj}

Le API diventano visibili e accessibili agli sviluppatori di applicazioni
dopo la pubblicazione di un piano.
La pubblicazione di un prodotto lo rende visibile nel **Catalogo** {{site.data.keyword.Bluemix_short}}
e nel portale sviluppatori integrato e disponibile per l'utilizzo da parte degli sviluppatori di applicazioni.

### Prerequisiti
{: #prereq_publish_proj}

Devi preparare un prodotto, prima che possa essere pubblicato. Per ulteriori informazioni sulla preparazione di prodotti, vedi
[Preparazione di un prodotto](#stage_product).

Per pubblicare un prodotto, completa questa procedura:

1. Nel riquadro di navigazione dell'API Manager, espandi la sezione **Cataloghi** e
seleziona il catalogo con cui vuoi lavorare. Viene aperta la scheda Prodotti del catalogo e vengono
visualizzati tutti i prodotti disponibili nel catalogo. Puoi selezionare quali stati vengono visualizzati
utilizzando le caselle di spunta di filtro sulla destra dello schermo.

2. Accanto alla versione del prodotto con cui vuoi lavorare, fai clic sull'icona **Gestisci** e fai quindi clic su **Pubblica**. Viene visualizzata la finestra di dialogo Modifica visibilità e sottoscrittori.

3. Specifica le seguenti opzioni:
    - `Visibile a`: puoi scegliere **Utenti pubblici**, **Utenti autenticati**
o **Personalizzato**. Se selezioni `Personalizzato`, puoi utilizzare il campo **Digita per aggiungere...** per
cercare organizzazioni o community per cui desideri sia visibile il tuo prodotto.
    - `Sottoscrivibile da`: puoi scegliere **Utenti autenticati** o **Personalizzato**. Se selezioni `Personalizzato`, puoi utilizzare il campo **Digita per aggiungere...** per
cercare organizzazioni o community per cui desideri sia visibile il tuo prodotto.

4. Fai clic su **Pubblica**.
    Se è richiesta l'approvazione per la pubblicazione di prodotti in questo catalogo, viene
inviata una richiesta di approvazione e il prodotto passa allo stato In sospeso; il prodotto viene pubblicato
quando la richiesta viene approvata. Se non è richiesta l'approvazione, la versione del prodotto viene pubblicata
immediatamente e passa allo stato Pubblicato.

Il tuo prodotto è nello stato Pubblicato.Il tuo prodotto viene pubblicato nel tuo catalogo ed è
disponibile per le organizzazioni o le community da te specificate. Gli sviluppatori delle applicazioni nei gruppi da te selezionati
possono vedere e utilizzare le API contenute nel prodotto.Tutte le richieste di sviluppatori
di applicazioni di utilizzare il tuo prodotto sono visualizzate nella scheda Approvazioni nel catalogo contenitore, dove puoi
rifiutarle o accettarle.


## Pubblicazione di un prodotto in Bluemix

Per visualizzare i tuoi prodotti nella sezione **Esplora API** del
Dashboard {{site.data.keyword.apiconnect_short}}, completa la seguente procedura.

### Prerequisiti

Prima di iniziare, se vuoi pubblicare un'API REST implementata con LoopBack, accertati di aver
pubblicato il runtime della tua applicazione e di aver preparato il tuo prodotto con il proxy di richiamo
che punta alla nuova applicazione. Per ulteriori informazioni su come eseguire tale operazione, vedi
[Preparazione e pubblicazione di un'applicazione Loopback](managing_apis.html#stage_publish_lb_app).

1. Nell'interfaccia utente API Manager, fai clic su **Aggiungi** > **Catalogo**. Viene visualizzata la finestra **Aggiungi catalogo**.

2. Completa i seguenti campi e poi fai clic su **Aggiungi**:
    - Nome visualizzazione
    - Nome
	
3. Seleziona il catalogo da te creato. 

4. Fai clic sull'icona **Impostazioni**.

5. Fai clic su **Portale** e seleziona una delle seguenti opzioni:
    - **Portale sviluppatori IBM**. Se selezioni questa opzione, viene
visualizzato l'URL del portale.
    - **Altro**. Se selezioni questa opzione, immetti l'URL per il portale
che vuoi utilizzare.

6. Nella sezione Registro utenti e invito, fai clic sulla freccia **Registro utenti**
e seleziona **SAML**.

7. Nel riquadro di navigazione, fai clic sull'icona **Sviluppatori**.

8. Fai clic su **Aggiungi organizzazione Bluemix**.

9. Aggiungi il tuo indirizzo email di utente {{site.data.keyword.Bluemix_short}} e fai clic su **Aggiungi**.

10. Viene inviato un invito al tuo indirizzo email. 

11. Fai clic sul link nell'email per accettare l'invito.
Viene aperta l'interfaccia utente {{site.data.keyword.Bluemix_short}}.

12. Seleziona la tua organizzazione {{site.data.keyword.Bluemix_short}} e fai clic su **Conferma**.

13. Nell'interfaccia utente API Manager, fai clic sull'icona **Prodotti**.

14. Accanto alla versione del prodotto con cui vuoi lavorare, fai clic sull'icona **Gestisci** e fai quindi clic su **Pubblica**. Viene visualizzata la finestra di dialogo Modifica visibilità e sottoscrittori.

15. Specifica le seguenti opzioni:
    - **Visibile a:** scegli **Personalizzato** e utilizza il campo **Digita per aggiungere...** per selezionare
la tua organizzazione sviluppatore e le eventuali altre che vuoi aggiungere.
    - **Sottoscrivibile da:** scegli **Personalizzato** utilizza il campo **Digita per aggiungere...** per selezionare
la tua organizzazione sviluppatore e le eventuali altre che vuoi aggiungere.

16. Fai clic su **Pubblica**.

Se è richiesta l'approvazione per la pubblicazione di prodotti in questo catalogo, viene
inviata una richiesta di approvazione e il prodotto passa allo stato In sospeso; il prodotto viene pubblicato
quando la richiesta viene approvata. Se non è richiesta l'approvazione, la versione del prodotto viene pubblicata
immediatamente e passa allo stato Pubblicato.

Il tuo prodotto viene visualizzato nella scheda **Esplora API** del **Dashboard** {{site.data.keyword.apiconnect_short}}. Se fai clic sul link Prodotto, passerai al prodotto nel portale sviluppatori.
