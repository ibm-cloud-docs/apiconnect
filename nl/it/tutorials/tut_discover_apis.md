---

copyright:
  years: 2017
lastupdated: "2017-11-20"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Rilevamento API
{: #tut_discover_apis}

**Durata**: 25 minuti  
**Livello di competenza**: Principiante  

## Obiettivo
{: #object_tut_discover_apis}

In questa esercitazione, imparerai come un utente del portale può utilizzare le API nel portale sviluppatori {{site.data.keyword.apiconnect_full}}. Imparerai come un utente del portale esplora i prodotti e le API, visualizza le API di test e si sottoscrive ad esse. 

## Prerequisito
{: #prereq_tut_discover_apis}

Nessun prerequisito per questa esercitazione. Come amministratore del portale, puoi anche completare questa esercitazione mentre navighi nel tuo portale sviluppatori per provare come navigano i tuoi utenti del portale. Tieni presente che tutti i portali sviluppatori hanno diverse interfacce. 

Se non disponi di un portale sviluppatori esistente, puoi configurarne uno in {{site.data.keyword.Bluemix_short}} prima di procedere con questa esercitazione.

## Esplora prodotti e API
{: #explore_tut_discover_apis}

Questa sezione illustra come un utente del portale esplorerà i prodotti e le API nel portale sviluppatori.

1. In un browser, passa a **Portale sviluppatori API Connect**.
![Portale sviluppatori API Connect](images/11-developer-portal.png)

2. Nel portale sviluppatori {{site.data.keyword.apiconnect_short}}, seleziona la scheda dei prodotti API.
![Prodotti API](images/12-API-products.png)

3. Seleziona uno dei prodotti API disponibili per visualizzare i piani e le API disponibili per il prodotto.  
  ![Seleziona prodotto](images/13-product.png)

4. Seleziona un'API per visualizzare i dettagli delle API disponibili.  
  ![API prodotti](images/14-api.png)

5. Nella pagina dei dettagli di un'API, puoi visualizzare le operazioni disponibili con i rispettivi parametri e le risposte restituite. Alla fine della pagina, puoi visualizzare le definizioni utilizzate dall'API.  
  ![Dettagli API](images/15-details.png) 

6. Nel pannello degli esempi di codice, puoi visualizzare gli esempi in diversi linguaggi di codifica di come richiamare le richieste e le relative risposte. Seleziona uno degli esempi, come ad esempio **Node**, per visualizzare un esempio in tale linguaggio di codifica.  
  ![Dettagli API](images/16-examples.png) 

---

## Visualizza e verifica le API
{: #view_tut_discover_apis}

Questa sezione illustra come un utente del portale visualizzerà e verificherà le API disponibili per un prodotto. 

1. Passa ai dettagli dell'API nel portale sviluppatori {{site.data.keyword.apiconnect_short}} come descritto nella precedente sezione.  
  ![Dettagli API](images/21-details.png) 

2. Puoi scaricare e visualizzare le informazioni yaml dello Swagger API selezionando **Open API**.  
  ![Scarica yaml Swagger](images/22-swagger.png) 

3. Scorri fino ad un'operazione per visualizzarne i dettagli. Puoi anche fare clic sul link delle operazioni per aprirne la pagina.
![Operazione](images/23-operation.png)

4. Nel pannello di destra negli esempi, scorri fino alla sezione **Try this operation**. Immetti i parametri e seleziona **Call operation**.  
  ![Prova questa operazione](images/24-try-this-operation.png)

5. Scorri per visualizzare la richiesta e la risposta della chiamata dell'operazione. Viene restituita una risposta di **200 OK**
e viene visualizzato il corpo del messaggio, che indicano che la chiamata dell'operazione ha avuto esito positivo.  
  ![Risposta operazione](images/25-operation-response.png)

---

## Sottoscriversi alle API
{: #subscr_tut_discover_apis}

Questa sezione illustra come un utente del portale si sottoscriverà alle API nel portale sviluppatori. 

1. Seleziona **Create an account**.
![Prodotti API](images/31-create-account.png)

2. Compila i campi obbligatori e seleziona **Create new account** in fondo alla pagina. 
**Nota:** utilizza un indirizzo email diverso di quello utilizzato per creare il tuo portale sviluppatori nell'esercitazione precedente.
![Prodotti API](images/32-create-new-account.png)

3. Dopo aver creato il tuo account sviluppatori, accedi per visualizzare la homepage. Devi disporre di un'applicazione per sottoscriverti alle API. Seleziona **Apps** per andare alla pagina delle applicazioni registrate.  
  ![Prodotti API](images/33-login.png)

4. Per registrare una nuova applicazione, seleziona **Create new App**.  
  ![Registra nuova applicazione](images/34-create-new-app.png)

5. Immetti *Title* e *Description* per la tua applicazione e seleziona **Submit**.  
  ![Invia nuova applicazione](images/35-submit-new-app.png) 

6. Ora che disponi di un'applicazione, puoi sottoscrivere i piani del prodotto dell'API. Seleziona **available APIs** o **API Products** per sfogliare i piani del prodotto dell'API.  
  ![Dettagli API](images/36-api-products.png) 

7. Seleziona il prodotto dell'API a cui vuoi sottoscriverti.  
  ![Prodotto API](images/37-select-product.png) 

8. Seleziona **Subscribe** per sottoscrivere il piano del prodotto dell'API.  
  ![Piano prodotto API](images/38-subscribe-plan.png) 

9. Seleziona l'applicazione che desideri utilizzare per sottoscriverti al piano del prodotto e seleziona **Subscribe**.
  ![Piano sottoscrizione applicazione](images/39-subscribe-app-plan.png) 

10. La tua applicazione è stata correttamente sottoscritta al piano del prodotto.
  ![Sottoscrizione applicazione positiva](images/310-subscribe-success.png) 

## Conclusioni
{: #conclusion_tut_discover_apis}

In questa esercitazione, hai imparato come i tuoi utenti del portale potrebbero esplorare i prodotti e le API, visualizzare le API di test e sottoscriversi ad esse. 

---

## Passo successivo
{: #next_tut_discover_apis}

Impara [come ottenere informazioni approfondite da analisi di base](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_insights_analytics).

Create >Manage> Secure > ** Socialize ** > Analyze  



