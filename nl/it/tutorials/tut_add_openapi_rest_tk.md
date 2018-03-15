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

# Aggiungi una nuova specifica API e richiama un servizio REST esistente utilizzando il toolkit sviluppatori
**Durata**: 15 minuti  
**Livello di competenza**: Principiante  

## Obiettivo
Questa esercitazione ti aiuta ad iniziare ad utilizzare velocemente {{site.data.keyword.apiconnect_full}} illustrando come puoi portare la tua API esistente nel controllo di gestione. Inizierai creando una nuova specifica OpenAPI e poi creando un proxy API passthrough per un servizio REST esistente.

## Prerequisito
Prima di iniziare, dovrai [configurare la tua istanza API Connect](tut_prereq_set_up_apic_instance.html) e [installare il toolkit API Connect](tut_prereq_install_toolkit.html).

---


## Esplora l'applicazione di esempio e verifica gli endpoint di destinazione
È stata creata un'applicazione _weather provider_ di esempio per questa esercitazione.
1. Per esplorare l'applicazione, vai a [http://gettingstartedweatherapp.mybluemix.net/ ![Icona link esterno](../../../icons/launch-glyph.svg "Icona link esterno")](http://gettingstartedweatherapp.mybluemix.net/){:new_window}.  
2. Immetti un codice postale U.S. valido per ottenere il tuo _**meteo corrente**_ e le _**previsioni di oggi**_.  
![](images/explore-weatherapp-1.png)

3. La precedente applicazione di esempio meteo è stata creata utilizzando API che forniscono dati meteo. L'endpoint per ottenere i dati meteo **correnti** è _**https:// myweatherprovider<span></span>.mybluemix.net/current?zipcode={zipcode}**_. Verifica visitando [https://myweatherprovider.mybluemix.net/current?zipcode=90210 ![Icona link esterno](../../../icons/launch-glyph.svg "Icona link esterno")](https://myweatherprovider.mybluemix.net/current?zipcode=90210){:new_window}.  

  ![](images/explore-weatherapp-2.png)

4. In modo simile, l'endpoint per ottenere i dati della previsione **di oggi** è `https:// myweatherprovider<span></span>.mybluemix.net/today?zipcode={zipcode}`. Verifica visitando [https://myweatherprovider.mybluemix.net/today?zipcode=90210 ![Icona link esterno](../../../icons/launch-glyph.svg "Icona link esterno")](https://myweatherprovider.mybluemix.net/today?zipcode=90210){:new_window}.  

  ![](images/explore-weatherapp-3.png)

---

## Aggiungi una nuova specifica OpenAPI e richiama un servizio REST esistente
1. Avvia **API Designer**. Nel tuo terminale, immetti `apic edit`.
2. Accedi utilizzando il tuo ID IBM.
    ![](images/screenshot_apic-edit_login.png)
3.   In API Designer, assicurati che il pannello di navigazione sia aperto. Se non lo è, fai clic su >> per aprirlo. Nel pannello di navigazione di **API Designer**, seleziona **Drafts > APIs**.
4. Nel pannello **APIs**, seleziona **Add > New API**.
5. Nella finestra New API, immetti "Weather Provider API" per il titolo. _Il nome e il percorso di base vengono popolati automaticamente._.  
  ![](images/toolkit-add-new-api.png)   
6. Fai clic su **Create API** per completare la procedura guidata.  

7. Dopo aver creato la tua API, viene selezionata la scheda **Design**.

8. Scorri fino al pannello **Host**. Immetti `$(catalog.host)` come valore se il campo non viene compilato automaticamente.

9. Scorri fino alla scheda **Security** e elimina il valore "clientIDHeader (API Key)" che è stato generato automaticamente.  
_(Visiteremo la sicurezza con le chiavi API nella prossima esercitazione.)_  

10. Nel pannello **Paths** crea un nuovo percorso facendo clic su **+**.
  a. Denomina il nuovo percorso con "**/current**".  
  b. Nello stesso pannello **Paths**, seleziona la sezione **GET /current**.  
  c. Nella sezione **GET /current**, aggiungi un nuovo **Parameter**. Come hai notato durante l'esplorazione dell'applicazione di esempio, il servizio meteo necessita di un codice postale come parametro.
      - Nome: codice postale  
      - Ubicato in: query  
      - Obbligatorio: sì  
      - Tipo: stringa  
    ![](images/path-current-1.png)
  d. Salva la tua API.

11. Con i tuoi parametri di query definiti nel passo precedente, devi ora definire l'oggetto di risposta restituito quando richiami l'API meteo. Per far ciò, scorri fino al pannello **Definitions**.

  1. Aggiungi una nuova definizione. 
  2. Denomina la nuova definizione con _Current_.
  3. Imposta il tipo di _Object_.
  4. Aggiungi nuove proprietà per la definizione **Current**.
    - Nome: codice postale         /  Tipo: stringa
    - Nome: temperatura /  Tipo: numero intero
    - Nome: umidità    /  Tipo: numero intero
    - Nome: città        /  Tipo: stringa
    - Nome: stato       /  Tipo: stringa
    ![](images/definition-current-1.png)
  5. Salva la tua API.  

12. Nel passo precedente, hai definito l'oggetto di risposta. Successivamente dovrai assicurarti che l'oggetto di risposta venga associato al percorso **get /current**. Nel pannello di navigazione, scorri fino al pannello **Paths**.
  a. Apri l'operazione **GET /current** e scorri fino alla sezione **Responses**.
  b. Modifica lo schema della risposta 200OK da "object" in "**Current**".
  c. Salva la tua API.

13. Il percorso e l'operazione appena creati devono richiamare i dati meteo correnti. Ora dovrai creare un'operazione e un percorso simili per richiamare i dati meteo di oggi. In modo simile a come hai creato il percorso **/current** al passo 11, crea un nuovo percorso: **/today**. 

14. Aggiungi un nuovo parametro nell'operazione **GET /today**.
    - Nome parametro: codice postale  
    - Ubicato in: query  
    - Obbligatorio: sì  
    - Tipo: stringa  

15. Crea una nuova definizione: **Today**.

16. Aggiungi nuove proprietà per la definizione **Today**.
  - Nome: codice postale         /  Tipo: stringa
  - Nome: alta    /  Tipo: numero intero
  - Nome: bassa    /  Tipo: numero intero
  - Nome: umidità notturna    /  Tipo: numero intero
  - Nome: umidità giorno    /  Tipo: numero intero
  - Nome: città        /  Tipo: stringa
  - Nome: stato       /  Tipo: stringa

17. Aggiorna lo schema di risposta nella sezione **GET /today** in "Today".

18. Salva la tua API.

19. Passa alla scheda **Assemble**. Hai creato due operazioni finora: **GET /current** e **GET /today**. Per assicurarti che venga richiamato l'endpoint corretto, dovrai creare della logica che verrà eseguita in modo condizionale nell'operazione che sta venendo richiamata. Utilizza il costrutto di logica **Operation Switch** per farlo.  

    a. Elimina la politica **invoke** che potrebbe già essere stata aggiunta ai _canvas_.  
    b. Dalla _tavolozza_, trascina **Operation Switch** e rilascialo nel canvas.  
      - Per **case 0**, assegna l'operazione **get /current**.
      - Aggiungi un nuovo caso: **case 1**.
      - Assegna l'operazione **get /today** a **case 1**.
      ![](images/assemble-1.png)
    **Operation Switch** fornisce un punto di decisione. In base alla coppia verbo/percorso, deve essere richiamata l'operazione appropriata.  
    c. Trascina la politica **invoke** dalla tavolozza e rilasciala nel canvas. Rilascia un'azione di richiamo nel percorso **/get current** e una in **/get today**.
    d. Seleziona la politica **invoke** nel percorso **/get current** e aggiornane il titolo con "**invoke-current**".  
    e. Aggiorna il campo URL con: `https://myweatherprovider.mybluemix.net/current?zipcode=$(request.parameters.zipcode)`.
    f. Seleziona la politica **invoke** nel percorso **/get today** e aggiornane il titolo con "**invoke-today**".  
    g. Aggiorna il campo URL con: `https://myweatherprovider.mybluemix.net/today?zipcode=$(request.parameters.zipcode)`.  

20. Salva la tua API.

---

## Verifica il tuo proxy API

### Verifica con _API Manager test tool_.
1. Avvia il server di test locale facendo clic sull'icona di avvio dei server (>) nella parte in basso sinistra del designer. Una volta che il gateway è stato avviato, visualizzerai lo stato automaticamente aggiornato con in esecuzione.

    ![](images/screenshot_start-server-1.png)

2. Nella scheda **Assemble**, fai clic sull'icona di riproduzione (>) per verificare il richiamo della destinazione del proxy dell'API. _Per questa esercitazione, utilizzeremo il Micro Gateway integrato, per cui assicurati che siano selezionate le politiche Micro Gateway._

    ![](images/screenshot_test-0.png)

3. Nel pannello di verifica, seleziona l'operazione **get /current**.  
  a. Codice postale è un parametro obbligatorio per questa operazione, per cui immetti un codice postale U.S. valido (ad esempio, 90210).  
  b. Fai clic su **invoke** e verifica di visualizzare:
  ```
  200 OK response
  Current weather data for 90210  
  ```
    ![](images/screenshot_test-2.png)  

_Se riscontri un errore CORS, segui le istruzioni nel messaggio di errore. Fai clic sul link nell'errore per aggiungere l'eccezione al tuo browser e quindi nuovamente sul pulsante "invoke"._

### Verifica con _Explore tool_.  
1. Per verificare i tuoi endpoint del proxy dell'API, seleziona _Explore_.
2. Seleziona l'operazione **GET /current** dalla tavolozza.
3. Immetti un codice postale U.S. valido (ad es. 90210) nella casella di test.
4. Fai clic su **Call operation** per visualizzare la risposta.  
  ![](images/screenshot_explore.png)  
  
---

## Conclusioni
In questa esercitazione hai visto come può essere richiamato un servizio REST esistente tramite un proxy passthrough dell'API. Hai iniziato verificando la disponibilità del servizio di esempio tramite il browser web. Poi hai creato una nuova specifica OpenAPI in {{site.data.keyword.apiconnect_short}} e l'hai collegata al servizio di esempio da richiamare. Infine, hai verificato il proxy dell'API con lo strumento di verifica integrato.

---

## Passo successivo

Proteggi la tua API utilizzando [la limitazione di frequenza](tut_rate_limit.html), [il segreto e l'ID client](tut_secure_landing.html) o [la protezione tramite OAuth 2.0](tut_secure_oauth_2.html).

Create > **Manage** > Secure > Socialize > Analyze

