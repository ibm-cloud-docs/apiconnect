---

copyright:
  years: 2017-2019
lastupdated: "2018-05-23"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal

subcollection: apiconnect

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Novità
{: #apic_029}

{{site.data.keyword.apiconnect_full}} include i seguenti miglioramenti:


- **Nuovi casi di errore sono supportati dal costrutto catch di assemblaggio**: i seguenti nuovi casi di errore sono supportati dal costrutto catch in un assemblaggio API: *BadRequestError*, *UnauthorizedError* e *ForbiddenError*. Consulta [Error cases supported by assembly catches ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/ref_toolkit_catch_errors.html){: #new_window}.
- **Aggiunto il parametro di query useBytesSent a API selezionate**: è stato aggiunto il parametro *useBytesSent* che consente l'utilizzo del campo di analisi *bytes_sent* per calcolare l'utilizzo. Consulta [Return data usage information for all the resources used by a given application ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps__appID__data-usageGET.html){: #new_window}, [Return data usage information for all the resources used by all applications in the given organization ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps_data-usageGET.html){: #new_window}, [Return combined data usage for all resources used by a given application ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps__appID__data-usage_allGET.html){: #new_window} e [Return combined data usage for all the resources used by a given organization ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_data-usage_allGET.html){: #new_window} per ulteriori informazioni.
**Puoi codificare i caratteri + nei valori del parametro di query dell'URL di destinazione di una politica proxy o di richiamo**: è presente una nuova proprietà API *x-ibm-gateway-queryparam-encode-plus-char*; se impostata su un valore di *true*, tutti i caratteri "+" nei valori del parametro di query dell'URL di destinazione delle politiche proxy e di richiamo, vengono codificai con "%2F". Nelle release precedenti, + era sempre codificato con %2F. Ora, il comportamento predefinito è di non eseguire la codifica. Consulta [API properties ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){: #new_window}.
- **Puoi applicare il parser JSON alla regola della risposta per una politica proxy o di richiamo**: è presente una nuova proprietà API *x-ibm-gateway-api-enforce-response-limits*; impostandola su un valore di *true* si consente l'applicazione del parser JSON nella regola della risposta. Se la dimensione del corpo della risposta è maggiore del limite del parser JSON impostato nel dominio DataPower, viene restituito un codice di stato di 500. Consulta [API properties ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){: #new_window}.
- **Potenziale per il miglioramento delle prestazione della politica di associazione**: è presente una nuova proprietà API *x-ibm-gateway-optimize-schema-definition* che può fornire un miglioramento nelle prestazioni della politica di associazione quando viene fatto riferimento a una definizione dello schema molto complessa da una definizione di output della politica. Consulta [API properties ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){: #new_window}.
