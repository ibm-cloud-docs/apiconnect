---

copyright:
  years: 2019
lastupdated: "2019-3-14"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Proteggi la tua API con OAuth a due fasi
{: #tut_secure_oauth_2}

Durata: 10 minuti  
Livello di competenza: Principiante

## Obiettivo
{: #object_tut_secure_oauth_2}

Questa esercitazione ti guiderà su come proteggere la tua API con un flusso OAuth 2.0 a due fasi. In questo flusso dell'applicazione, il client OAuth inizia una richiesta con il server di autorizzazione e ha ricevuto un token di accesso. Il client OAuth può quindi utilizzare il token per accedere alle risorse protette tramite la tua API.

## Prerequisiti
{: #prereq_tut_secure_oauth_2}

Prima di iniziare, devi aver completato la seguente esercitazione.  
- [Proteggi un'API con le chiavi segreto e ID client con {{site.data.keyword.Bluemix}}](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_id_secret_bm)
o
- [Proteggi un'API con le chiavi segreto e ID client con il toolkit](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_id_secret_tk)

Nota: questa esercitazione mostra i passi e le schermate per eseguire l'attività all'interno della IU {{site.data.keyword.Bluemix}}. Puoi anche completare la stessa procedura utilizzando la riga di comando. Puoi visualizzare questa procedura nell'[IBM Knowledge Center ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSMNED_5.0.0/com.ibm.apic.toolkit.doc/tutorial_apionprem_security_OAuth_v506.html){: #new_window}. 

## Procedura
{: #steps_tut_secure_oauth_2}

1. Crea un'API provider OAuth e seleziona il tuo schema OAuth.  
	a. Apri **Drafts**, seleziona **APIs** e fai clic su **Add** > **OAuth 2.0 Provider API**.  
    ![](images/oauth_provider_1.png)
	b. Denominala "OAuth Endpoint API". Il nome e il percorso di base dovrebbe venire popolati automaticamente.  
	c. Seleziona **Create API**.  
	d. Nell'API endpoint OAuth appena creata, passa al pannello **OAuth 2** (o scorri fino ad esso) e seleziona "Confidential" come tipo di client.  
	e. In Scopes, ridenomina _scope1_ con _view_current_. Elimina _scope2_ e _scope3_.  
	![](images/oauth_provider_type_scope.png) 
	
	f. In **Grants**, deseleziona **Implicit**, **Password** e **Access Code**. Lascia **Application** selezionato.  
	![](images/oauth_provider_grants.png)  
	
	g. Salva la tua API.  

2. Aggiorna la definizione di sicurezza della tua API Weather Provider per includere OAuth.  
	a. Passa a _Weather Provider API_. (Torna alle API e seleziona _Weather Provider API_.)  
	![](images/oauth_weatherapi_info.png)
	
	b. Nelle definizioni di sicurezza, fai clic sull'icona **+** e aggiungi una nuova definizione per OAuth.
	![](images/oauth_add_security.png)
	c. Imposta il nome su "OAuth definition".  
	d. Nel campo del flusso, seleziona **Application**.  
	e. Immetti l'URL del token _**your base URL**/oauth-endpoint-api/oauth2/token_.  
	![](images/oauth_secdef_top.png)
	
	f. Aggiungi un nuovo ambito: view_current.  
	![](images/oauth_secdef_scopes.png)
	g. In **Security**, seleziona **OAuth Definition** e **view_current** e lascia il segreto e l'ID client selezionati.  
	![](images/oauth_security_oauth.png)
	
	h. Fai clic su Save.  
	
	i. Ritorna a **Drafts** e seleziona **Products**.  Apri il **prodotto Weather Provider API**.
	![](images/weatherapi_prod_info.png)
	
	j. Fai clic su **APIs** sulla barra di navigazione. Fai clic sull'icona **+** e aggiungi una nuova API. Aggiungi l'API endpoint OAuth al tuo prodotto Weather Provider.  
	![](images/weatherapi_prod_apis.png)
	k. Salva il prodotto e preparalo nel tuo Sandbox.  
	![](images/oauth_security_definition_3a.png)

3. Verifica la tua configurazione di sicurezza di OAuth.  
	a. Pubblica il tuo prodotto aggiornato nel sandbox. Fai clic su **Dashboard > Sandbox** e pubblica il tuo prodotto.  
	  ![](images/test_oauth_1.png)
	b. Accetta le impostazioni predefinite nella finestra di dialogo Visibility.  Fai clic su **Publish**.
	  ![](images/pub_visibility.png)
	  
	c. Fai clic su **Explore > Sandbox**.  
      ![](images/test_oauth_2.png)
	d. In **Weather Provider API**, fai clic su **GET /current** dall'elenco delle operazioni. 
	
	e. Fai clic su **Try It**. 
	
	f. Nel pannello di destra, controlla che il segreto e l'ID client siano già popolati.  
	
	g. Nella sezione **Parameters**, immetti _10504_ nel campo **zipcode**.  
	  ![](images/weather_oauth_explorer_param.png)
	
	h. Nella sezione **Authorization**, fai clic su **Authorize** per richiamare il tuo token di accesso.
	  ![](images/weather_oauth_explorer_auth.png)
	
	i. Dopo aver ricevuto il tuo token di accesso, fai clic su **Call operation** per completare la tua verifica.  
      ![](images/test_oauth_4.png)

4. Controlla che la richiesta includa il token di accesso, l'ID e il segreto client. Per passare solo il token di accesso alla richiesta, dovrai rimuovere il segreto e l'ID client dai requisiti di sicurezza dell'API Weather Provider.  
    ![](images/test_oauth_5.png)

5. Salva la tua API Weather Provider. Quindi preparala e pubblicala nel Sandbox. Dallo strumento Explore, esegui la stessa verifica come effettuato precedentemente.  
    ![](images/test_oauth_6.png)
    
## Conclusioni
{: #conclusion_tut_secure_oauth_2}

In questa esercitazione, hai imparato come creare un'API provider OAuth, aggiornare la definizione di sicurezza di un'API per includere OAuth e verificato la tua configurazione di sicurezza.

---

## Passo successivo
{: #next_tut_secure_oauth_2}

Inizia a socializzare con la tua API [configurando un portale sviluppatori](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_config_dev_portal).

Create > Manage > **Secure** > Socialize > Analyze
