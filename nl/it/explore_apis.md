---

copyright:
  years: 2017
lastupdated: "2017-09-05"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal

subcollection: apiconnect

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Esplorazione di API e prodotti
{: #explore_prods_apis}

1. Per visualizzare le API che sono state condivise con la tua organizzazione {{site.data.keyword.Bluemix_short}} vai alla schermata di destinazione delle API e fai clic su
**Esplora API**.

<img alt="Pagina di destinazione delle API con la scheda Esplora API evidenziata" src="images/ExploreAPIs_tab.png">

2. Espandi l'API per visualizzare ulteriori informazioni su di essa.

3. Per sottoscrivere un'API, fai clic su un prodotto API.
Viene aperto il portale sviluppatori, dove puoi sottoscrivere un piano per accedere a un'API. 

  **Nota**: se il piano che selezioni ha la fatturazione, devi fornire un numero di carta di credito per la tua organizzazione. Ciò richiede che tu disponga di privilegi di proprietario.

## Visualizzazione e verifica delle API nel portale sviluppatori
{: #view_test_apis_dev_port}

1. Dalla schermata principale del portale sviluppatori, fai clic su **Prodotti API**.

2. Per visualizzare ulteriori dettagli,f ai clic su **API** per il prodotto che contiene
l'API richiesta e fai quindi clic sull'API.

3. Ulteriori dettagli delle singole operazioni associate a un'API sono disponibili sotto l'intestazione **Operazioni API**.

4. Per visualizzare il codice di esempio di un'operazione:
    - Nella sezione Operazioni API, fai clic su **Percorsi** e fai clic sull'operazione per
cui vuoi visualizzare il codice di esempio.
    - Fai clic sulla scheda dell'operazione per espandere e visualizzare i dettagli a essa relativi, compresi gli esempi di codice. Puoi
visualizzare il codice di esempio per la tua operazione in diversi linguaggi.

Per verificare un'API, completa la seguente procedura.
1. Fai clic su **API**.
Vengono visualizzate tutte le API che possono essere utilizzate dagli sviluppatori di applicazioni.

2. Fai clic sul nome dell'API che vuoi verificare.

3. Trova l'operazione con cui vuoi lavorare sotto l'intestazione `Operazioni API`.

4. Fai clic su **Prova questa operazione**.

5. Fornisci i valori per le intestazioni o i parametri richiesti.

6. Se l'operazione è protetta con l'autenticazione di base, fornisci le credenziali.

7. Fai clic su **Invia richiesta**.
Il risultato viene visualizzato nel campo Corpo della risposta. Puoi continuare a verificare i diversi valori di parametro come necessario.

## Sottoscrizione per utilizzare le API
{: #subscrib_apis}

1. Nel portale sviluppatori, fai clic su **Prodotti API**.

2. Fai clic sul prodotto che contiene il piano con cui vuoi lavorare.

3. Nella sezione Piano del prodotto, fai clic sul piano che vuoi usare. Vengono
visualizzati i dettagli del piano selezionato.

4. Dopo che hai identificato il piano che vuoi usare, fai clic su **Utilizza questo piano**.
Viene visualizzata la finestra di dialogo Utilizza questo piano.

5. Seleziona l'applicazione che vuoi usare con questo piano e fai quindi clic su **Salva**.
Vengono visualizzati i dettagli dell'applicazione.

  **Nota**: se il piano che selezioni ha la fatturazione, devi fornire un numero di carta di credito per la tua organizzazione. Ciò richiede che tu disponga di privilegi di proprietario.

6. Per visualizzare le operazioni per le API incluse nei piani sottoscritti dall'applicazione, fai clic sul nome dell'API.

7. Se il piano non è limitato, puoi utilizzarlo immediatamente. Se il piano è limitato, viene visualizzato
come `Approvazione in sospeso` e non puoi utilizzare il piano richiesto finché l'amministratore non avrà approvato la tua richiesta.



