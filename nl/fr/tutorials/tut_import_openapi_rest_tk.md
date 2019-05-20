---

copyright:
  years: 2017
lastupdated: "2017-10-31"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Importation de votre spécification d'API et passage par un proxy d'un service REST existant à l'aide du kit d'outils de développement
{: #tut_import_openapi_rest_tk}

Durée : 5 mn  
Niveau de compétence : Débutant  


## Objectif
{: #object_tut_import_openapi_rest_tk}

Ce tutoriel montre comment passer votre API existante sous contrôle de gestion avec {{site.data.keyword.apiconnect_full}}. Dans ce tutoriel, vous commencerez par importer une spécification d'OpenAPI, puis vous créerez un proxy d'API passe-système pour un service REST existant.

## Prérequis
{: #prereq_tut_import_openapi_rest_tk}

Avant de commencer, vous devez [configurer votre instance API Connect](tut_prereq_set_up_apic_instance.html) et [installer le kit d'outils API Connect](tut_prereq_install_toolkit.html).

---


## Exploration du modèle d'application et test des noeuds finaux cible
{: #explore_tut_import_openapi_rest_tk}

Un modèle d'application _weather provider_ a été créé pour ce tutoriel. La spécification d'API correspondante (Swagger 2.0) se trouve dans le fichier [weather-provider-api_1.yaml ![Icône de lien externe](../../../icons/launch-glyph.svg "Icône de lien externe")](https://raw.githubusercontent.com/IBM-Bluemix-Docs/apiconnect/master/tutorials/weather-provider-api_1.yaml){: #new_window}.

1. Pour explorer l'application, accédez à [http://gettingstartedweatherapp.mybluemix.net/ ![Icône de lien externe](../../../icons/launch-glyph.svg "Icône de lien externe")](http://gettingstartedweatherapp.mybluemix.net/){: #new_window}.  
2. Entrez un code postal américain en 5 chiffres valide pour en obtenir la _**météo actuelle**_ et les _**prévisions du jour**_.  
![](images/explore-weatherapp-1.png)S

3. Le modèle d'application de météo ci-dessus a été généré à l'aide d'API qui fournissent des données météorologiques. Le noeud final permettant d'obtenir les données météorologiques **en cours** est `https://myweatherprovider.mybluemix.net/current?zipcode={zipcode}`. Testez-le en accédant à [https://myweatherprovider.mybluemix.net/current?zipcode=90210 ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://myweatherprovider.mybluemix.net/current?zipcode=90210){: #new_window}.  

  ![](images/explore-weatherapp-2.png)

4. De même, le noeud final permettant d'obtenir les données prévisionnelles **d'aujourd'hui** est `https:// myweatherprovider.mybluemix.net/today?zipcode={zipcode}`. Testez-le en accédant à [https://myweatherprovider.mybluemix.net/today?zipcode=90210 ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://myweatherprovider.mybluemix.net/today?zipcode=90210){: #new_window}.  

  ![](images/explore-weatherapp-3.png)



---

## Importation de la spécification d'OpenAPI du modèle d'application pour créer un proxy d'API REST
{: #import_tut_import_openapi_rest_tk}

1. Lancez le **concepteur d'API**. Dans votre fenêtre de terminal, entrez la commande suivante : `apic edit`.
2. Connectez-vous à l'aide de votre IBMid.
    ![](images/screenshot_apic-edit_login.png)
3. Dans le **concepteur d'API**, vérifiez que le panneau de navigation est ouvert. S'il ne l'est pas, cliquez sur >> pour l'ouvrir.
4. Dans le panneau de navigation, cliquez sur **Brouillons**.
5. Cliquez sur l'onglet **API**.
6. Dans l'onglet API, cliquez sur **Ajouter**.
7. Dans le menu déroulant, sélectionnez **Importer l'API à partir d'un fichier ou d'une URL**.
   ![](images/toolkit-import-1.png)
8. Il existe une définition d'OpenAPI 2.0 de l'API weather que vous utiliserez pour ce tutoriel. Dans la boîte de dialogue
"Importer OpenAPI (Swagger)", entrez l'adresse URL suivante :
`https://raw.githubusercontent.com/IBM-Bluemix-Docs/apiconnect/master/tutorials/weather-provider-api_1.yaml`.
9. Laissez l'option _Ajouter un produit_ désélectionnée et cliquez sur **Importer**.  
    ![](images/screenshot_import-url.png)  

Une fois la spécification d'OpenAPI importée, la vue Concevoir de l'API s'affiche. Elle présente les diverses sections de la définition d'OpenAPI. Faites défiler pour l'examiner et notez la valeur de la zone Hôte. Vous pouvez également afficher l'OpenAPI dans l'onglet Source. 
_Vous voyez que la zone Hôte est définie sur `$(catalog.host)` _. Il s'agit de l'URL de base de votre proxy d'API._
 


## Test du proxy de votre API
{: #test_tut_import_openapi_rest_tk}

1. Démarrez le serveur de test local en sélectionnant l'icône de **démarrage des serveurs**. Une fois la passerelle démarrée, vous verrez que le statut est automatiquement mis à jour sur _**Exécution en cours**_.
    ![](images/screenshot_start-server-1.png)

2. Sélectionnez l'onglet **Assembler**.

3. Cliquez sur l'icône de lecture (>) pour tester l'appel de la cible du proxy de votre API.
   _Etant donné que pour ce tutoriel nous utiliserons la passerelle Micro Gateway imbriquée, vous devez vous assurer que **Règles Micro Gateway** est sélectionné.
    ![](images/screenshot_test-0.png)

4. Dans le panneau de test :
  - Sélectionnez l'opération **get /current**.  
  - Le paramètre zipcode étant nécessaire pour cette opération, entrez un code postal américain valide (par exemple, 90210).  
  - Sélectionnez **invoke** et vérifiez la réponse.

    Si vous obtenez une erreur CORS, suivez les instructions fournies dans le message d'erreur. Cliquez sur le lien fourni pour ajouter l'exception à votre navigateur et appuyez ensuite de nouveau sur le bouton **invoke**.
  
  - La réponse escomptée est **200 OK** accompagnée des données météorologiques pour le code postal 90210.
    ![](images/screenshot_test-1.png)    


## Conclusion
{: #conclusion_tut_import_openapi_rest_tk}

Dans ce tutoriel, vous avez vu comment appeler un service REST existant à l'aide d'un proxy passe-système d'API. Vous avez commencé par vérifier la disponibilité de l'exemple de service via le navigateur Web. Ensuite, vous avez créé dans {{site.data.keyword.apiconnect_short}} un proxy d'API que vous avez lié à l'exemple de
service à appeler. Enfin, vous avez testé ce service à l'aide des outils de test internes d'{{site.data.keyword.apiconnect_short}}.

---

## Etape suivante
{: #next_tut_import_openapi_rest_tk}

Sécurisation de votre API à l'aide d'une [limitation de débit](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_rate_limit), d'un [ID et d'une valeur confidentielle client](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_landing) ou [sécurisation à l'aide de OAuth 2.0](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_oauth_2).

Création > **Gestion** > Sécurisation > Réseaux sociaux > Analyse
