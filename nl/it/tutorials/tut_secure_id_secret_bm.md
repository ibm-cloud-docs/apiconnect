---
copyright:
  years: 2017
lastupdated: "2017-10-31"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Proteggi la tua API con il segreto e l'ID client utilizzando {{site.data.keyword.Bluemix_notm}}

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

1. Passa alla vista di progettazione della tua API:  
   a. Fai clic su **Drafts** nel pannello di navigazione di sinistra  
   b. Poi fai clic sulla scheda **APIs**  
   c. Fai clic su _Weather Provider API_ che hai creato nella precedente esercitazione. Viene aperta la vista **Design** dell'API.  
   ![](images/1_goto_drafts_api.png)  

2. Nella vista di progettazione:
    a. Scorri fino a **Security Definitions**.  
    b. Fai clic sull'icona **Add Security Definitions** (+) e su **API Key**.  
    c. Aggiungi le due nuove chiavi API mostrate di seguito. Per entrambe le nuove chiavi, assicurati che il campo "Located In" sia impostato su "Header".  
      - Nome: ID client;  Nome parametro: X-IBM-Client-Id  
      - Nome: Segreto client;  Nome parametro: X-IBM-Client-Secret    
        ![](images/2_security_definitions.png)  

3. Scorri fino al pannello **Security** e aggiungi una nuova opzione di sicurezza.  
    a. Seleziona le chiavi segreto e ID client appena create.  
    b. Salva la tua API.  
    c. Passa alla scheda **Assemble**.  
    ![](images/3_security_option.png)  


## Verifica le modifiche apportate alla tua API

1. Nella scheda di assemblaggio, fai clic sul pulsante ► per verificare le tue modifiche.

2. Nel pannello Test / Setup, fai clic su **Republish product** per ottenere le ultime modifiche. 
> Questa opzione aggiorna il tuo prodotto API e inoltre lo pubblica nel catalogo Sandbox.

3. Dopo aver ripubblicato il prodotto, fai clic sull'operazione **get /current** nel pannello di verifica.
4. Scorri fino al pannello di verifica e controlla che i valori per il segreto e l'ID client siano stati popolati. 
> Questi sono i valori di verifica generati per il tuo sandbox e rappresentano le chiavi dell'applicazione che utilizzeranno la tua API.
> **Nota:** le chiavi segreto e ID client possono anche essere trovate in Dashboard > Catalog > Settings > Endpoints]_   
  
  ![](images/test_api_keys_1.png)

5. Scorri più in basso e immetti un codice postale (ad es. 90210). 
6. Fai clic su **Richiama**. _Dovresti ricevere una risposta 200 OK, con il corpo del messaggio contenente le informazioni meteo._
7. Ora ritorna al campo ID client. 
8. Sostituisci il valore ID client con un valore a caso.
9. Riesegui la verifica facendo clic su **Invoke**. _Riceverai una risposta 401 Unauthorized, insieme al messaggio "Client ID not registered"._  

    ![](images/test_api_keys_3.png)  


## Richiama la tua API utilizzando il segreto e l'ID client

Le impostazioni di sicurezza possono inoltre essere verificate utilizzando lo strumento Explore che richiama esplicitamente l'endpoint proxy e passa le chiavi segreto e ID client come valori di intestazione.

1. Fai clic su **Explore** e su **Sandbox**.
    ![](images/explore_1.png)

2. Fai clic sull'operazione **GET /current** dall'elenco.

3. Nella colonna di destra, fai clic su **Call operation** per rieseguire la verifica.
    ![](images/explore_3.png)

---

## Conclusioni
In questa esercitazione, hai imparato come configurare il meccanismo di identificazione, verificare le modifiche apportate alla tua API e richiamato la tua API utilizzando il segreto e l'ID client. 

---

## Passo successivo

Inizia a socializzare con la tua API [configurando un portale sviluppatori](tut_config_dev_portal.html).

Create > Manage > **Secure** > Socialize > Analyze
