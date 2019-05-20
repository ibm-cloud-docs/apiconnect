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

# Sécurisation de votre API avec un protocole d'autorisation OAuth à deux acteurs
{: #tut_secure_oauth_2}

Durée : 10 mn  
Niveau de compétence : Débutant

## Objectif
{: #object_tut_secure_oauth_2}

Ce tutoriel vous guidera tout au long du processus de sécurisation de votre API avec un protocole d'autorisation OAuth 2.0 à deux acteurs. Dans ce flux d'application, le client OAuth envoie une demande au serveur d'autorisations et reçoit un jeton d'accès. Le client OAuth peut ensuite utiliser ce jeton pour accéder à des ressources protégées via votre API.

## Prérequis
{: #prereq_tut_secure_oauth_2}

Avant de commencer, vous devez avoir terminé l'un des tutoriels suivants :  
- [Sécurisation de votre API avec un ID client et une valeur confidentielle du client à l'aide d'{{site.data.keyword.Bluemix}}](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_id_secret_bm) ou
- [Sécurisation de votre API avec un ID client et une valeur confidentielle du client à l'aide du kit d'outils](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_id_secret_tk)

Remarque : Ce tutoriel montre les étapes et les captures d'écran permettant de réaliser la tâche dans l'interface utilisateur d'{{site.data.keyword.Bluemix}}. Vous pouvez également effectuer la même procédure à partir de la ligne de commande. Vous pouvez afficher cette procédure dans [IBM Knowledge Center ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/SSMNED_5.0.0/com.ibm.apic.toolkit.doc/tutorial_apionprem_security_OAuth_v506.html){: #new_window}. 

## Procédure
{: #steps_tut_secure_oauth_2}

1. Créez une API de fournisseur OAuth et sélectionnez votre schéma OAuth.  
	a. Ouvrez **Brouillons**, sélectionnez **API**, puis cliquez sur **Ajouter** > **API du fournisseur OAuth 2.0**.  
    ![](images/oauth_provider_1.png)
	b. Intitulez-la "API OAuth Endpoint". Le nom et le chemin de base doivent être automatiquement renseignés.  
	c. Sélectionnez **Créer une API**.  
	d. Dans la nouvelle API OAuth Endpoint, accédez au panneau **OAuth 2** (ou faites défiler vers le bas jusqu'au panneau), puis sélectionnez "Confidentiel" comme type de client.  
	e. Sous Portées, renommez _scope1_ en _view_current_. Supprimez _scope2_ et _scope3_.  
	![](images/oauth_provider_type_scope.png) 
	
	f. Sous **Accords**, désélectionnez **Implicite**, **Mot de passe** et **Code d'accès**. Conservez la sélection de **Application**.  
	![](images/oauth_provider_grants.png)  
	
	g. Sauvegardez votre API.  

2. Mettez à jour la définition de sécurité de votre API Weather Provider afin d'y inclure OAuth.  
	a. Accédez à votre _API Weather Provider_. (Revenez dans l'écran API et sélectionnez _API Weather Provider_.)  
	![](images/oauth_weatherapi_info.png)
	
	b. Sous Définitions de sécurité, cliquez sur l'icône **+** pour ajouter une nouvelle définition pour OAuth.
	![](images/oauth_add_security.png)
	c. Définissez le nom sur "Définition OAuth".   
	d. Dans la zone Flux, sélectionnez **Application**.  
	e. Entrez l'URL de jeton _**votre URL de base**/oauth-endpoint-api/oauth2/token_.  
	![](images/oauth_secdef_top.png)
	
	f. Ajoutez la nouvelle portée view_current.  
	![](images/oauth_secdef_scopes.png)
	g. Sous **Sécurité**, sélectionnez **Définition OAuth** et **view_current**, et conservez la sélection de ID client et Valeur confidentielle du client.  
	![](images/oauth_security_oauth.png)
	
	h. Cliquez sur Sauvegarder.  
	
	i. Revenez dans **Brouillons** et sélectionnez **Produits**. Ouvrez le **produit Weather Provider API**.
	![](images/weatherapi_prod_info.png)
	
	j. Cliquez sur **API** dans la barre de navigation. Cliquez sur l'icône **+** pour ajouter une nouvelle API. Ajoutez l'API OAuth Endpoint à votre produit Weather Provider.  
	![](images/weatherapi_prod_apis.png)
	k. Sauvegardez le produit, puis transférez-le dans votre bac à sable.  
	![](images/oauth_security_definition_3a.png)

3. Testez votre configuration de la sécurité OAuth.  
	a. Publiez votre produit mis à jour dans le bac à sable. Cliquez sur **Tableau de bord > Bac à sable** et publiez votre produit.  
	  ![](images/test_oauth_1.png)
	b. Acceptez les valeurs par défaut dans la boîte de dialogue Visibilité. Cliquez sur **Publier**.
	  ![](images/pub_visibility.png)
	  
	c. Cliquez sur **Explorer > Bac à sable**.  
      ![](images/test_oauth_2.png)
	d. Dans votre **API Weather Provider**, cliquez sur **GET /current** dans la liste des opérations. 
	
	e. Cliquez sur **Essayez-la**.  
	
	f. Dans le panneau de droite, vous remarquerez que les valeurs ID client et Valeur confidentielle du client sont déjà renseignées.  
	
	g. Dans la section **Paramètres**, entrez _10504_ dans la zone **zipcode**.   
	  ![](images/weather_oauth_explorer_param.png)
	
	h. Dans la section **Autorisation**, cliquez sur **Autoriser** pour obtenir votre jeton d'accès.
	  ![](images/weather_oauth_explorer_auth.png)
	
	i. Une fois que vous avez reçu le jeton d'accès, cliquez sur **Appeler une opération** pour terminer le test.  
      ![](images/test_oauth_4.png)

4. Notez que la demande inclut le jeton d'accès, l'ID client et la valeur confidentielle du client. Pour que seul le jeton d'accès soit transmis dans la demande, vous devez supprimer l'ID client et la valeur confidentielle du client des exigences de sécurité associées à l'API Weather Provider.  
    ![](images/test_oauth_5.png)

5. Sauvegardez votre API Weather Provider. Puis transférez-la et publiez-la dans le bac à sable. Exécutez le même test à partir de l'outil Explorer.  
    ![](images/test_oauth_6.png)
    
## Conclusion
{: #conclusion_tut_secure_oauth_2}

Dans ce tutoriel, vous avez appris comment créer une API OAuth Provider, mettre à jour la définition d'une API pour y inclure OAuth et tester votre configuration de la sécurité.

---

## Etape suivante
{: #next_tut_secure_oauth_2}

Commencez à diffuser votre API sur les réseaux sociaux via la [création et configuration d'un portail de développeur](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_config_dev_portal).

Création > Gestion > **Sécurisation** > Réseaux sociaux > Analyse
