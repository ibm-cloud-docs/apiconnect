---

copyright:
  years: 2017
lastupdated: "2018-02-12"

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Nouveautés

{{site.data.keyword.apiconnect_full}} intègre les améliorations suivantes :

- **Suppression des comptes utilisateur et des organisations de développeurs dans le portail de
développeur** : Vous pouvez supprimer votre compte utilisateur et vos organisations de développeurs dans le portail de
développeur. Vous pouvez également changer la propriété de vos organisations de développeurs. Pour plus d'informations, voir [Deleting your Developer account ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapic_portal_delete_account.html){:new_window}, [Deleting a Developer organization ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapic_portal_delete_dev_org.html){:new_window} et [Changing the ownership of a Developer organization ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapic_portal_dev_org_ownership.dita){:new_window}.

- __Ajout de la zone d'événement d'API *endpoint_url* __: La zone d'événement d'API *endpoint_url* identifie l'URL de proxy ou l'URL cible d'appel sur laquelle la demande a échoué. 
Pour plus d'informations, voir [Deleting your Developer account ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/rapim_analytics_apieventrecordfields.html){:new_window}.</dd>

- **Ajout d'une prise en charge et d'une référence pour les API REST de portail de développeur pour des analyses** : Les API REST de portail de développeur vous aident à analyser vos API de catalogue. Pour plus d'informations, voir [Analyses ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/analytics.html){:new_window}.

- **Ajout de la section Analyses lors de la création d'une API** : Vous pouvez définir et spécifier pour votre API des paramètres existants utilisables pour rassembler des données d'analyse concernant l'API. Pour plus d'informations, voir [Composition d'une définitions d'API REST![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html){:new_window}.

- **Incitation à l'authentification à deux facteurs dans le portail de développeur** : Vous pouvez inciter les utilisateurs de votre portail de développeur à définir une authentification à deux facteurs sur leur compte en appliquant un module de règles d'authentification à deux facteurs. Pour plus d'informations, voir [Incitation des utilisateurs à définir une authentification à deux facteurs sur leur compte de portail de développeur ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapim_portal_two_factor_auth_enforce.html){:new_window}.

- **Fonctions ajoutées à la gestion intégrée de la facturation et des paiements** :  Administrateur :
	* Créez des plans d'abonnement mensuels prépayés pour la facturation auxquels les clients
de votre API peuvent s'abonner avec une carte de crédit. Pour plus d'informations, voir [Facturation pour l'utilisation de vos produits ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/capim_product_billing.html){:new_window}.
	* Exploitez un compte Stripe pour gérer les paiements de vos abonnements.
	* Spécifiez un certain nombre de jours d'évaluation gratuits dans votre plan d'abonnement pour les nouveaux abonnés. Le paiement commence automatiquement à la fin de la période d'évaluation.
	Client :
	* Abonnez-vous à des plans payants dans le portail de développeur, qui vous permettent d'utiliser des produits contenant une ou plusieurs API. Pour plus d'informations, voir [Tutoriel : Abonnement à un plan tarifé ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tutorial_portal_sub_paid_plan.html){:new_window}.

- **Appel automatiquement remplacé dans la passerelle** : Le dernier appel de votre stratégie peut être remplacé par un proxy. Cette opération est effectuée automatiquement par la passerelle pour améliorer les performances. Pour plus d'informations, voir [Propriétés d'API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){:new_window}.

- **Portée d'OAuth modifiable par des réponses de tiers** : Vous pouvez configurer un serveur externe afin de remplacer la valeur de portée de l'API. Pour plus d'informations, voir [Portée ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/con_oauth_scope.html){:new_window}.

- **Nouvelles zones d'événement d'API** : Les zones d'événement d'API suivantes ont été ajoutées :
    * billing.trial_period_days
	* billing.amount
	* billing.currency
	* billing.model
	* billing.provider
	* client_id
	* immediate_client_ip
	* latency_info2.task
	* latency_info2.ended

Pour plus d'informations, voir [Zones d'enregistrement d'événement d'API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/rapim_analytics_apieventrecordfields.html){:new_window} et [Obtention de données d'analyse à l'aide d'appels d'API REST ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/tapim_exportanalytics_api_calls.html){:new_window}.

- **Nouveaux paramètres de requête pour l'URL de redirection** : De nouveaux paramètres de requête ont été ajoutés aux informations disponibles pour une tierce partie. Ces nouveaux paramètres sont <code>provider</code>, <code>providerid</code> et
<code>g-transid</code>. Pour plus d'informations, voir [Authentification et autorisation via une adresse URL de redirection ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_redirect_form_.html){:new_window}.

- **Prévention des alertes CORS de navigateur dans l'outil de test** : L'outil de test du concepteur d'API envoie depuis le navigateur des requêtes qui peuvent déclencher des alertes CORS. Pour éviter les alertes CORS, la case à cocher
**Activer le proxy** est fournie pour envoyer les messages de test du serveur qui héberge le concepteur d'API plutôt que du navigateur. Pour plus d'informations, voir [Test d'une API à l'aide de l'outil de test d'API Designer ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_toolkit_testing.html){:new_window}.

- **Sécurisation des API à l'aide de protocole d'autorisation OAuth de tiers au lieu de MobileFirst Foundation** : Sécurisez votre API avec un fournisseur tiers OAuth au lieu du serveur d'autorisations IBM MobileFirst&tm; Platform Foundation. Pour plus d'informations, voir [Integrating third party OAuth provider ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/con_oauth_introspection.html){:new_window}.

- **Sécurisation de votre API à l'aide d'OpenID Connect (OIDC)** : Vous pouvez sécuriser vos API avec OpenID Connect(OIDC) en utilisant un exemple d'API de fournisseur OAuth préfourni que vous personnalisez en fonction de votre configuration OIDC. Pour
plus d'informations, voir [Securing your APIs with OpenID Connect![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/tapic_sec_api_config_oidc.html){:new_window}.

- **Action de mise à jour SOAP qui ne remplace plus l'API** : Lorsque vous mettez à jour une API SOAP à partir d'une définition WSDL, seules les sections de l'API concernées par la nouvelle WSDL sont remplacées, les autres sections restent inchangées. Dans les versions précédentes, l'action de
mise à jour remplaçait intégralement la configuration de la définition d'API SOAP, ainsi
que toutes les propriétés de conception et la configuration d'assemblage. Pour plus d'informations, voir [Updating a SOAP API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/tapic_soap_update.html){:new_window}.

- **Utilisation de Honeypot pour la protection anti spam dans le portail de développeur** : Protection Honeypot qui fournit des mécanismes de sécurité afin de protéger votre site de portail de développeur des soumissions émises par des robots de spam. Si
une activité de robot de spam est détectée, la soumission de formulaire est bloquée. Pour plus d'informations, voir [Using Honeypot for spam protection ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapic_portal_honeypot.html){:new_window}.

- **Utilisation du module Vues dans le portail de développeur** : Créez de nouvelles vues dans le portail de développeur, telles que des listes de contenu de produits, des API et des applications, à l'aide du module d'interface utilisateur Vues. Pour plus d'informations, voir[Using the Views module in the Developer Portal![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/capic_portal_views.html){:new_window}.
