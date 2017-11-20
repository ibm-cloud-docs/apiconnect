---
copyright:
  years: 2017
lastupdated: "2017-09-30"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Proteggi la tua API con il segreto e l'ID client utilizzando il toolkit 


**Durata:** 10 minuti  
**Livello di competenza:** Principiante


## Obiettivo

Questa esercitazione ti guiderà su come proteggere la tua API con il segreto e l'ID client. Quando le applicazioni vengono registrate nel tuo portale sviluppatori, viene generato un ID client per identificare l'applicazione. Facoltativamente, un segreto client, che funge da password, può essere generato. Le applicazioni dovranno fornire le chiavi del segreto e dell'ID client per poter accedere alla tua API.


## Prerequisiti
Prima di iniziare, devi aver completato una delle seguenti esercitazioni:
- [Importa una specifica OpenAPI2.0 e collegati tramite proxy a un servizio REST esistente](tut_rest_landing.html)
       **o**  
- [Aggiungi una nuova specifica API e richiama un servizio REST esistente](tut_rest_landing.html)


## Configura il meccanismo di identificazione della tua API

1. Avvia API Designer (se non è già aperto):  
   a. Apri il tuo terminale.  
   b. Immetti `apic edit` nella riga di comando. _API Designer viene avviato nel tuo browser_    
   c. Fai clic su **Sign in with Bluemix**.  
   d. Immetti le tue informazioni di accesso {{site.data.keyword.Bluemix_short}}.  

2. Passa alla vista di progettazione della tua API:
    a. Fai clic su **Drafts** nel pannello di navigazione di sinistra 
    b. Poi fai clic sulla scheda **APIs**
    c. Fai clic su _Weather Provider API_ che hai creato nella precedente esercitazione. Viene aperta la vista **Design** dell'API.  
    ![](images/1_goto_drafts_api.png)  

3. Nella vista di progettazione:  
   a. Scorri fino a **Security Definitions**.  
    ![](images/1b.png) 

   b. Fai clic sull'icona **Add Security Definitions** (+) e su **API Key**.  
      - Nome: ID client;  Nome parametro: X-IBM-Client-ID  
      - Nome: Segreto client;  Nome parametro: X-IBM-Client-Secret  
      - Per entrambe le nuove chiavi, assicurati che il campo **Located In** sia impostato su "Header".  
      ![](images/2a.png)    

4. Scorri fino al pannello **Security** e aggiungi una nuova opzione di sicurezza.  
   a. Seleziona le chiavi segreto e ID client appena create.  
   b. Salva la tua API.  
   c. Passa alla scheda **Assemble**.  
    ![](images/3a.png) 

## Verifica le modifiche apportate alla tua API

1. Nella scheda di assemblaggio, fai clic su ► per verificare le tue modifiche.
2. Nel pannello di verifica, fai clic sull'operazione **get /current**.
3. Scorri fino al pannello di verifica e controlla che i valori per il segreto e l'ID client siano stati popolati. _Questi sono i valori di verifica generati per il tuo sandbox e rappresentano le chiavi dell'applicazione che utilizzeranno la tua API._  
> Nota: queste chiavi segreto e ID client possono anche essere trovate in  **Dashboard** > **Catalog** > **Settings** > **Endpoints**  

 ![](images/test_api_keys_1.png)

4. Scorri più in basso e immetti un codice postale (ad es. 90210). 
5. Quindi fai clic su **Invoke**. _Dovresti ricevere una risposta 200 OK, con il corpo del messaggio contenente le informazioni meteo._  
6. Ritorna al campo ID client e sostituisci il valore ID client con un valore a caso (per visualizzare il comportamento quando viene passato un valore ID client non corretto)  
7. Riesegui la verifica facendo clic su **Invoke**. _Riceverai una risposta 401 Unauthorized, insieme al messaggio "Client ID not registered"._  
  ![](images/test_api_keys_3.png)  
  

## Richiama la tua API utilizzando il segreto e l'ID client

Le impostazioni di sicurezza possono inoltre essere verificate utilizzando lo strumento Explore che richiama esplicitamente l'endpoint proxy e passa le chiavi segreto e ID client come valori di intestazione.


1. Fai clic su **Explore** e su **Sandbox**.  
    ![](images/explore_1.png)

2. Fai clic sull'operazione **GET /current** dall'elenco.  

3. Nella colonna di destra, fai clic su **Call operation** per rieseguire la verifica.  
    ![](images/4.png)  
    
---

### Conclusioni
In questa esercitazione, hai imparato come configurare il meccanismo di identificazione, verificare le modifiche apportate alla tua API e richiamato la tua API utilizzando il segreto e l'ID client.  

---

## Passo successivo

Inizia a socializzare con la tua API [configurando un portale sviluppatori](tut_config_dev_portal.html).

Create > Manage > **Secure** > Socialize > Analyze
