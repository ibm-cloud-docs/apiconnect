---

copyright:
  years: 2017
lastupdated: "2017-09-28"

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Novità

{{site.data.keyword.apiconnect_full}} include i seguenti miglioramenti:

- **Aggiunto il supporto e un riferimento per le API REST del portale sviluppatori per le analisi**: le API REST del portale sviluppatori ti aiutano nell'analisi delle tue API del catalogo. Per ulteriori informazioni, consulta [Analytics ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/analytics.html){:new_window}.

- **Aggiunta la sezione Analytics durante la creazione di un'API**: puoi definire e specificare i parametri esistenti per la tua API che possono essere utilizzati per raccogliere
i dati di analisi sull'API. Consulta [Composing a REST API definition ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html){:new_window} per ulteriori informazioni.

- **Incoraggiato l'utilizzo dell'autenticazione a due fattori nel portale sviluppatori**: puoi incoraggiare gli utenti del tuo portale sviluppatori
a configurare l'autenticazione a due fattori (TFA) nei loro account applicando un modulo delle regole TFA. Per ulteriori informazioni, consulta [Encouraging users to set up two-factor authentication on their Developer Portal account ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapim_portal_two_factor_auth_enforce.html){:new_window}.

- **Aggiunte le funzioni per la fatturazione integrata e la gestione del pagamento**:
    Amministratore:
	* Crea piani di sottoscrizione di fatturazione pre-pagati mensili a cui i tuoi clienti dell'API possono sottoscriversi con una carta di credito. Consulta [Billing for the use of your Products ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/capim_product_billing.html){:new_window} per ulteriori informazioni.
	* Sfrutta un account Stripe per gestire i pagamenti per le tue sottoscrizioni.
	* Specifica un numero di giorni di prova gratuita al tuo piano di sottoscrizione per i nuovi sottoscrittori. Il pagamento automatico inizia dopo la scadenza dei giorni di prova.
	Cliente:
	* Sottoscrivi i piani a pagamento nel portale sviluppatori che ti consentono di utilizzare i prodotti che contengono una o più API. Consulta [Tutorial: Subscribing to a Plan with pricing ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tutorial_portal_sub_paid_plan.html){:new_window} per ulteriori informazioni.

- **Richiama la sostituzione automatica nel gateway**: l'ultimo richiamo nella tua politica può essere sostituito da un proxy. Questa operazione viene eseguita automaticamente dal
per migliorare le prestazioni. Per ulteriori informazioni, consulta: [API properties ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){:new_window}.

- **L'ambito OAuth può essere modificato da risposte di terze parti**: puoi configurare un server esterno per sovrascrivere il valore dell'ambito dell'API. Per ulteriori informazioni, consulta: [Scope ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/con_oauth_scope.html){:new_window}.

- **Nuovi campi evento API**: aggiunti i seguenti campi evento dell'API:
    * billing.trial_period_days
	* billing.amount
	* billing.currency
	* billing.model
	* billing.provider
	* client_id
	* immediate_client_ip
	* latency_info2.task
	* latency_info2.ended

Consulta [API event record fields ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/rapim_analytics_apieventrecordfields.html){:new_window} e [Obtaining analytics data by using REST API calls ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/tapim_exportanalytics_api_calls.html){:new_window} per ulteriori informazioni.

- **Nuovi parametri di query per l'URL di reindirizzamento**: sono stati aggiunti dei nuovi parametri della query alle informazioni disponibili per una terza parte. I nuovi parametri sono <code>provider</code>, <code>providerid</code> e
<code>g-transid</code>. Per ulteriori informazioni, consulta [Authenticating
and authorizing through a redirect URL ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_redirect_form_.html){:new_window}.

- **Blocco degli avvisi CORS del browser nello strumento di test**: lo strumento API Designer Test invia le richieste dal browser che può attivare gli eventi CORS. Per bloccare
gli avvisi CORS, viene fornita la casella di spunta **Enable Proxy** per inviare messaggi di test dal server che ospita API Designer invece che dal browser. Per ulteriori informazioni, consulta
[Testing an API with the API Designer test tool ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_toolkit_testing.html){:new_window}.

- **API sicure con OAuth di terze parti invece di Mobile First Foundation**: proteggi la tua API con un provider OAuth di terze parti invece del server di autorizzazione IBM MobileFirst&tm; Platform Foundation. Per ulteriori informazioni, consulta
[Integrating third party OAuth provider ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/con_oauth_introspection.html){:new_window}.

- **Proteggi le tue API con OIDC (OpenID Connect)**: puoi proteggere le tue API con OIDC (OpenID Connect)
utilizzando un'API del provider OAuth di esempio prefornito che personalizzi in base alla tua configurazione OIDC. Per ulteriori informazioni, consulta
[Securing your APIs with OpenID Connect ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/tapic_sec_api_config_oidc.html){:new_window}.

- **L'azione di aggiornamento SOAP non sovrascrive più l'API**: quando aggiorni un'API SOAP da una definizione WSDL,
vengono sostituite solo le sezioni dell'API influenzate dal nuovo WSDL, le altre sezioni rimangono non modificate. Nelle precedenti release,
l'azione di aggiornamento sovrascriveva completamente la configurazione della definizione dell'API SOAP, incluse
tutte le proprietà di progettazione e la configurazione di assemblaggio. Per ulteriori informazioni, consulta [Updating a SOAP
API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/tapic_soap_update.html){:new_window}.

- **Utilizzo di Honeypot per la protezione da spam nel portale sviluppatori**: la protezione Honeypot fornisce meccanismi di sicurezza
per la protezione del tuo sito del portale sviluppatori dall'invio di spam. Se viene individuata attività di spam, l'inoltro del modulo viene bloccato. Per ulteriori informazioni, consulta
[Using Honeypot for spam protection ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapic_portal_honeypot.html){:new_window}.

- **Utilizzo del modulo delle visualizzazioni nel portale sviluppatori**: crea nuove visualizzazioni nel portale sviluppatori, come gli elenchi di contenuti dei prodotti, delle API e delle applicazioni
utilizzando il modulo Views UI. Per ulteriori informazioni, consulta [Using the Views module in the Developer Portal ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/capic_portal_views.html){:new_window}.
