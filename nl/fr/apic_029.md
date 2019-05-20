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

# Nouveautés
{: #apic_029}

{{site.data.keyword.apiconnect_full}} intègre les améliorations suivantes :


- **Les nouveaux cas d'erreur sont pris en charge par la construction d'interception d'assemblage** : Les nouveaux cas d'erreur suivants sont pris en charge par la construction d'interception dans un assemblage d'API : *BadRequestError*, *UnauthorizedError* et *ForbiddenError*. Voir [Error cases supported by assembly catches ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/ref_toolkit_catch_errors.html){: #new_window}.
- **Paramètre de requête useBytesSent ajouté à certaines API** : Le paramètre *useBytesSent* permettant l'utilisation de la zone d'analyse *bytes_sent* pour calculer l'utilisation a été ajouté. Voir [Return data usage information for all the resources used by a given application ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps__appID__data-usageGET.html){: #new_window}, [Return data usage information for all the resources used by all applications in the given organization ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps_data-usageGET.html){: #new_window}, [Return combined data usage for all resources used by a given application ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps__appID__data-usage_allGET.html){: #new_window} et [Return combined data usage for all the resources used by a given organization ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_data-usage_allGET.html){: #new_window} pour plus d'informations.
**Vous pouvez coder des caractères + dans les valeurs de paramètre de requête de l'URL cible d'une règle Invoke ou Proxy** : Il existe une nouvelle propriété d'API *x-ibm-gateway-queryparam-encode-plus-char* ; si elle est définie sur la valeur *true*, tous les caractères "+" figurant dans les valeurs de paramètre de requête de l'URL cible des règles Invoke et Proxy sont codés en "%2F". Dans les éditions précédentes, les caractères + étaient toujours codés en %2F. Désormais, le codage n'est pas effectué par défaut. Voir [API properties ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){: #new_window}.
- **Vous pouvez appliquer l'analyseur JSON à la règle de réponse pour une stratégie Invoke ou Proxy** : Il existe une nouvelle propriété d'API *x-ibm-gateway-api-enforce-response-limits* ; l'affectation de la valeur *true* à cette propriété permet d'appliquer l'analyseur JSON à la règle de réponse. Si la taille du corps de la réponse est supérieure à la limite définie pour l'analyseur JSON dans le domaine DataPower, le code d'état 500 est renvoyé. Voir [API properties ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){: #new_window}.
- **Potentiel d'amélioration des performances de la stratégie de mappage**: Il existe une nouvelle propriété d'API *x-ibm-gateway-optimize-schema-definition* qui peut améliorer les performances de la stratégie de mappage lorsqu'une définition de schéma très complexe est référencée par une définition de sortie de stratégie. Voir [API properties ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){: #new_window}.
