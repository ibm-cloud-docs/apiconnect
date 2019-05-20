---

copyright:
  years: 2019
lastupdated: "2019-3-11"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# Gestione di un servizio SOAP
{: #tut_manage_soap_api}

**Durata**: 15 minuti
**Livello di competenza**: Principiante

---
## Obiettivo
{: #object_tut_manage_soap_api}

In questa esercitazione, utilizzerai API Manager per creare un'API SOAP che è un proxy di un servizio meteo basato su SOAP.

## Prerequisiti
{: #prereq_tut_manage_soap_api}

- Prima di iniziare, dovrai [configurare la tua istanza {{site.data.keyword.apiconnect_short}}](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_set_up_apic_instance).
- Prima di iniziare, copia il file di test [weatherprovider.wsdl ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://raw.githubusercontent.com/IBM-Bluemix-Docs/apiconnect/master/tutorials/weatherprovider.wsdl){: #new_window} nel tuo file system locale.
Nota: puoi fare clic su **Raw** e salvare la pagina risultante nel tuo sistema locale come un file `.wsdl`. Come suggerisce il nome, questo servizio SOAP restituisce i dati meteo quando viene fornito un codice postale.

---
## Configurazione di una definizione dell'API SOAP
{: #setup_tut_manage_soap_api}

1. Accedi a {{site.data.keyword.Bluemix_short}}: https://cloud.ibm.com.
2. Nel **Dashboard** {{site.data.keyword.Bluemix_notm}}, fai clic su **Cloud Foundary Services**.  
3. Avvia il servizio {{site.data.keyword.apiconnect_short}}. 
4. In {{site.data.keyword.apiconnect_short}}, assicurati che il pannello di navigazione nel lato sinistro sia aperto. Se non lo è, fai clic su **>>** per aprirlo.  
5. Seleziona **Drafts** nel pannello di navigazione.   

6. Nel menu a discesa, seleziona **API from a SOAP service**.
  ![Nuova API](images/newapi-menu2.png)

7. Viene aperta la finestra New API dalla finestra di dialogo WSDL. Fai clic su **Upload File**.
  ![carica il file .wsdl](images/4-uploadwsdl.png)

8. Seleziona il file `weatherprovider.wsdl` che hai salvato precedentemente.

9. Viene rivisualizzata la finestra New API dalla finestra di dialogo WSDL. Controlla la casella di spunta **weatherService**. Fai clic su **Done**.
  ![seleziona servizio meteo](images/newapi2.png)

10. Dopo una corretta importazione, viene visualizzata la vista di progettazione dell'API. Inoltre, puoi visualizzare la definizione OpenAPI nella scheda dell'origine.
   _Nella scheda dell'origine, vedrai che WSDL è incluso nella definizione OpenAPI._
  ![Pagina editor API](images/designpage2.png)

11. Fai clic sull'icona ![save](images/save.png) per salvare le tue modifiche. Viene visualizzata momentaneamente una notifica di conferma "API Saved".

12. Nella barra del menu con l'icona di salvataggio, la scheda **Design** indica la tua ubicazione presente. Accanto ad essa, trovi la scheda **Source** dove puoi direttamente visualizzare il file Swagger (2.0) che rappresenta la tua API e accanto ad esso trovi la scheda **Assemble** che ti porta a un'interfaccia di trascinamento e rilascio per l'elaborazione dell'API. Fai clic su **Assemble**.
  ![Scheda assemblaggio](images/assemble-clean.png)  

## Verifica della definizione dell'API SOAP
{: #test_tut_manage_soap_api}

1. Nella scheda **Assemble**, fai clic sull'icona **More actions** (tre punti) e seleziona **Generate a default product** dal menu.  
   ![Menu ulteriori azioni, apri](images/gen-default-prod.png)

2. Accetta le opzioni predefinite nella finestra a comparsa di dialogo **New Product** e seleziona **Create Product**. Viene creato e pubblicato **weatherService product 1.0.0** nel catalogo Sandbox.  
  ![crea un nuovo prodotto](images/12a-chooseproduct.png)
 
  _In {{site.data.keyword.apiconnect_short}}, **Products** fornisce un modo per raggruppare le API intese per un utilizzo particolare. I prodotti sono pubblicati in un **Catalog**. Riferimento: [Glossario {{site.data.keyword.apiconnect_short}}](docs/services/apiconnect/tutorials/tut_expose_soap_service/apic_glossary.html)_

3. Salva le tue modifiche.  

4. Accanto alla casella di ricerca, fai clic sull'icona di test per verificare il servizio API. Viene visualizzato il menu di configurazione.

5. Dall'elenco dei prodotti, scegli `weatherService product 1.0.0`.  
  ![scegli servizio meteo](images/12-chooseproduct.png)

6. Scorri fino alla fine e fai clic su **Next**.

7. Dall'elenco delle operazioni, seleziona `post /weatherRequest`.  
  ![inserisci una richiesta](images/13-selectoperation.png)

8. Scorri verso il basso. Immetti il seguente xml nel campo del corpo. Puoi selezionare e copiare il seguente XML di esempio e fare clic sul campo **body** per attivare il campo e posizionare l'XML di esempio.  
  ```
  <?xml version="1.0" encoding="UTF-8"?>
  <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
  <wdata:WeatherRequest xmlns:wdata="http://www.ibm.com/wdata">
       <zipcode>10504</zipcode>
  </wdata:WeatherRequest>
   </soap:Body>
  </soap:Envelope>
  ```
 
  ![la richiesta](images/14-enterrequest.png)

9. Scorri verso il basso se necessario e fai clic su **Invoke**.
L'API restituisce una risposta **body** formata dal meteo corrente.  
  ![](images/15-success.png)

## Conclusioni
{: #conclusion_tut_manage_soap_api}

In questa esercitazione, hai completato quanto segue:
1. Configurato una definizione API SOAP
2. Verificato la tua definizione API
3. Ricevuto una risposta **body** dall'endpoint dell'API meteo che indica il risultato della tua richiesta.

---

## Passo successivo
{: #next_tut_manage_soap_api}

[Esponi il tuo servizio come un'API REST](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_expose_soap_service) o proteggi la tua API utilizzando [la protezione tramite OAuth 2.0](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_oauth_2).

Create > **Manage** > Secure > Socialize > Analyze
