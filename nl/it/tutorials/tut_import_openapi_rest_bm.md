---
copyright:
  years: 2017
lastupdated: "2017-11-02"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Importa la tua specifica API e collegati tramite proxy a un servizio REST esistente con {{site.data.keyword.Bluemix_notm}}
Durata: 5 minuti  
Livello di competenza: Principiante  

## Obiettivo
Questa esercitazione ti aiuta ad iniziare ad utilizzare velocemente {{site.data.keyword.apiconnect_full}} illustrando come puoi portare la tua API esistente nel controllo di gestione. Inizieremo importando una specifica OpenAPI e poi creando un proxy API passthrough per un servizio REST esistente.

## Prerequisiti
Prima di iniziare, dovrai [configurare la tua istanza {{site.data.keyword.apiconnect_short}}](tut_prereq_set_up_apic_instance.html).

---


## Esplora l'applicazione di esempio e verifica gli endpoint di destinazione

È stata creata un'applicazione _weather provider_ di esempio per questa esercitazione. La specifica API corrispondente (Swagger 2.0) è nel file [weather-provider-api_1.yaml ![Icona link esterno](../../../icons/launch-glyph.svg "Icona link esterno")](https://raw.githubusercontent.com/IBM-Bluemix-Docs/apiconnect/master/tutorials/weather-provider-api_1.yaml){:new_window}.

1. Per esplorare l'applicazione, vai a [http://gettingstartedweatherapp.mybluemix.net/ ![Icona link esterno](../../../icons/launch-glyph.svg "Icona link esterno")](http://gettingstartedweatherapp.mybluemix.net/){:new_window}.  
2. Immetti un codice postale U.S. di 5 cifre valido per ottenere il tuo _**meteo corrente**_ e le _**previsioni di oggi**_.  
![](images/explore-weatherapp-1.png)

3. La precedente applicazione di esempio meteo è stata creata utilizzando API che forniscono dati meteo. L'endpoint per ottenere i dati meteo **correnti** è `https:// myweatherprovider<span></span>.mybluemix.net/current?zipcode={zipcode}`. Verifica visitando [https://myweatherprovider.mybluemix.net/current?zipcode=90210 ![Icona link esterno](../../../icons/launch-glyph.svg "Icona link esterno")](https://myweatherprovider.mybluemix.net/current?zipcode=90210){:new_window}.  

  ![](images/explore-weatherapp-2.png)

4. In modo simile, l'endpoint per ottenere i dati della previsione **di oggi** è `https:// myweatherprovider<span></span>.mybluemix.net/today?zipcode={zipcode}`. Verifica visitando [https://myweatherprovider.mybluemix.net/today?zipcode=90210 ![Icona link esterno](../../../icons/launch-glyph.svg "Icona link esterno")](https://myweatherprovider.mybluemix.net/today?zipcode=90210){:new_window}.  

  ![](images/explore-weatherapp-3.png)


---

## Importa la specifica OpenAPI dell'applicazione di esempio per creare un proxy API REST
1. Accedi a {{site.data.keyword.Bluemix_short}}: https://new-console.ng.bluemix.net/login.
2. Nel pannello di navigazione {{site.data.keyword.Bluemix_notm}}, seleziona **Services** e **Dashboard**. Avvia il servizio {{site.data.keyword.apiconnect_short}}. 
3. In {{site.data.keyword.apiconnect_short}}, assicurati che il pannello di navigazione nel lato sinistro sia aperto. Se non lo è, fai clic su **>>** per aprirlo.  
4. Seleziona **Drafts** nel pannello di navigazione.   
5. Nella scheda **APIs**, fai clic su **Add**. Dal menu a discesa, seleziona **Import API from a file or URL**.  
     ![](images/import-1.png)

6. Ora importeremo la definizione meteo OpenAPI. Nella finestra di dialogo "Import OpenAPI (Swagger)" che viene aperta, immetti il seguente URL:
`https://raw.githubusercontent.com/IBM-Bluemix-Docs/apiconnect/master/tutorials/weather-provider-api_1.yaml`. Lascia le altre opzioni con i rispettivi valori predefiniti e fai clic su **Import**.  
    ![](images/import-2.png)  

7. Dopo aver importato la specifica OpenAPI, viene visualizzata la vista **Design** dell'API. Qui puoi visualizzare varie sezioni della definizione OpenAPI. Scorri per esplorare e prendi nota del valore **Host**. Puoi anche visualizzare OpenAPI nella scheda **Source**.
  _Nota: noterai che il valore host è impostato su _ `$(catalog.host)` _. Questo è l'URL di base del tuo proxy dell'API._
8. La tua API è stata salvata. 


## Verifica il tuo proxy API

### Verifica con _API Manager test tool_.
1. Nella scheda **Assemble**, fai clic sull'icona delle ulteriori azioni e seleziona **Generate a default product**.  
  ![](images/generate-default-product-1.png)   

2. Accetta le opzioni predefinite nella finestra di dialogo **New Product** e fai clic su **Create Product**. Viene creato e pubblicato **Weather Provider API product** nel catalogo Sandbox. Viene visualizzato un messaggio che indica la corretta generazione del prodotto.  
  ![](images/generate-default-product-2.png)  

  ![](images/generate-default-product-3.png)

  _In {{site.data.keyword.apiconnect_short}}, **Products** fornisce un modo per raggruppare le API intese per un utilizzo particolare. I prodotti sono pubblicati in un **Catalog**.  [Glossario {{site.data.keyword.apiconnect_short}}](../apic_glossary.html)_

3. Nella scheda Assemble, fai clic sull'icona di riproduzione per verificare il richiamo della destinazione del proxy dell'API.

4. Nel pannello di verifica, seleziona l'operazione **get /current**.  
    a. Codice postale è un parametro obbligatorio per questa operazione, per cui immetti un codice postale U.S. valido (ad esempio, 90210).  
    b. Fai clic su **invoke** e verifica di visualizzare:  
    ```
    - 200 OK response
    - Current weather data for 90210  
    ```
_Se riscontri un errore CORS, segui le istruzioni nel messaggio di errore. Fai clic sul link nell'errore per aggiungere l'eccezione al tuo browser e quindi nuovamente sul pulsante "invoke"._

    ![](images/test-invoke-1.png)


### Verifica con _Explore tool_.
_Lo strumento Explore consente agli utenti di verificare l'operazione corrente dell'API fornendo tutti i requisiti del parametro impostati nella definizione OpenAPI. Questa applicazione non viene eseguita nello strumento API Test trovato nella scheda dell'assemblaggio, per cui viene consentito all'utente di verificare il comportamento dell'API quando il parametro è mancate._

1. Per verificare i tuoi endpoint proxy dell'API, seleziona **Explore** e **Sandbox**.
    ![](images/test-explore-1.png)
2. Seleziona l'operazione **GET /current** dalla tavolozza.
3. Seleziona "Try it".  
4. Immetti un codice postale U.S. valido (ad es. 90210) nella casella di test.
5. Fai clic su **Call operation** per visualizzare la risposta.
  ![](images/test-explore-2.png)

    ![](images/test-explore-3.png)


### Conclusioni
In questa esercitazione hai visto come può essere richiamato un servizio REST esistente tramite un proxy passthrough dell'API. Hai iniziato verificando la disponibilità del servizio di esempio tramite il browser web. Poi hai creato un proxy API in {{site.data.keyword.apiconnect_short}} e collegato il proxy al servizio di esempio da richiamare. Hai impacchettato la tua API in un prodotto, pubblicato il prodotto nel catalogo e verificato il proxy.

---

## Passo successivo

Proteggi la tua API utilizzando [la limitazione di frequenza](tut_rate_limit.html), [il segreto e l'ID client](tut_secure_landing.html) o [la protezione tramite OAuth 2.0](tut_secure_oauth_2.html).

Create > **Manage** > Secure > Socialize > Analyze

