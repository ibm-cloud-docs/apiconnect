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

# Importation de votre spécification d'API et passage par un proxy d'un service REST existant à l'aide d'{{site.data.keyword.Bluemix_notm}}
Durée : 5 mn  
Niveau de compétence : Débutant  

## Objectif
Ce tutoriel vous aide à démarrer rapidement avec {{site.data.keyword.apiconnect_full}} en vous montrant comment passer une API existante sous contrôle de gestion. Nous commencerons par importer une spécification d'OpenAPI, puis nous créerons un proxy d'API passe-système pour un service REST existant.

## Prérequis
Avant de commencer, vous devez [configurer votre instance {{site.data.keyword.apiconnect_short}}](tut_prereq_set_up_apic_instance.html).

---


## Exploration du modèle d'application et test des noeuds finaux cible

Un modèle d'application _weather provider_ a été créé pour ce tutoriel. La spécification d'API correspondante (Swagger 2.0) se trouve dans le fichier [weather-provider-api_1.yaml ![Icône de lien externe](../../../icons/launch-glyph.svg "Icône de lien externe")](https://raw.githubusercontent.com/IBM-Bluemix-Docs/apiconnect/master/tutorials/weather-provider-api_1.yaml){:new_window}.

1. Pour explorer l'application, accédez à [http://gettingstartedweatherapp.mybluemix.net/ ![Icône de lien externe](../../../icons/launch-glyph.svg "Icône de lien externe")](http://gettingstartedweatherapp.mybluemix.net/){:new_window}.  
2. Entrez un code postal américain en 5 chiffres valide pour en obtenir la _**météo actuelle**_ et les _**prévisions du jour**_.  
![](images/explore-weatherapp-1.png)

3. Le modèle d'application de météo ci-dessus a été généré à l'aide d'API qui fournissent des données météorologiques. Le noeud final permettant d'obtenir les données météorologiques **en cours** est `https:// myweatherprovider<span></span>.mybluemix.net/current?zipcode={zipcode}`. Testez-le en accédant à [https://myweatherprovider.mybluemix.net/current?zipcode=90210 ![Icône de lien externe](../../../icons/launch-glyph.svg "Icône de lien externe")](https://myweatherprovider.mybluemix.net/current?zipcode=90210){:new_window}.  

  ![](images/explore-weatherapp-2.png)

4. De même, le noeud final permettant d'obtenir les données prévisionnelles **d'aujourd'hui** est `https:// myweatherprovider<span></span>.mybluemix.net/today?zipcode={zipcode}`. Testez-le en accédant à [https://myweatherprovider.mybluemix.net/today?zipcode=90210 ![Icône de lien externe](../../../icons/launch-glyph.svg "Icône de lien externe")](https://myweatherprovider.mybluemix.net/today?zipcode=90210){:new_window}.  

  ![](images/explore-weatherapp-3.png)


---

## Importation de la spécification d'OpenAPI du modèle d'application pour créer un proxy d'API REST
1. Connectez-vous à {{site.data.keyword.Bluemix_short}} : https://new-console.ng.bluemix.net/login.
2. Dans le panneau de navigation {{site.data.keyword.Bluemix_notm}}, sélectionnez **Services**, puis **Tableau de bord**. Lancez le service {{site.data.keyword.apiconnect_short}}. 
3. Dans {{site.data.keyword.apiconnect_short}}, vérifiez que le panneau de navigation sur la gauche est ouvert. S'il ne l'est pas, cliquez sur **>>** pour l'ouvrir.  
4. Sélectionnez **Brouillons** dans le panneau de navigation.   
5. Dans l'onglet **API**, cliquez sur **Ajouter**. Dans le menu déroulant, sélectionnez **Importer l'API à partir d'un fichier ou d'une URL**.  
     ![](images/import-1.png)

6. Nous allons maintenant importer la définition de météo d'OpenAPI. Dans la boîte de dialogue "Importer OpenAPI (Swagger)" qui s'ouvre, entrez l'adresse URL suivante : `https://raw.githubusercontent.com/IBM-Bluemix-Docs/apiconnect/master/tutorials/weather-provider-api_1.yaml`. Conservez les valeurs par défaut des autres options et cliquez sur **Importer**.  
    ![](images/import-2.png)  

7. Une fois la spécification d'OpenAPI importée, la vue **Concevoir** de l'API s'affiche. Elle présente les diverses sections de la définition d'OpenAPI. Faites défiler pour l'examiner et notez la valeur de la zone **Hôte**. Vous pouvez également afficher l'OpenAPI dans l'onglet **Source**.
  _Remarque : La zone Hôte est définie sur _ `$(catalog.host)` _. Il s'agit de l'URL de base de votre proxy d'API._
8. Votre API est sauvegardée. 


## Test du proxy de votre API

### Test avec l'_outil de test du gestionnaire d'API_.
1. Dans l'onglet **Assembler**, cliquez sur l'icône Plus d'actions, puis sélectionnez **Générer un produit par défaut**.  
  ![](images/generate-default-product-1.png)   

2. Acceptez les options par défaut de la boîte de dialogue **Nouveau produit**, puis cliquez sur **Créer un produit**. Le **produit API Weather Provider** est créé et publié dans le catalogue de bac à sable. Un message indiquant que la génération du produit a abouti s'affiche.  
  ![](images/generate-default-product-2.png)  

  ![](images/generate-default-product-3.png)

  _Dans {{site.data.keyword.apiconnect_short}}, **Produits** propose un mécanisme permettant de regrouper des API destinées à un usage particulier. Les produits sont publiés dans un **catalogue**.  [Glossaire {{site.data.keyword.apiconnect_short}}](../apic_glossary.html)_

3. Dans l'onglet Assembler, cliquez sur l'icône de lecture pour tester l'appel de la cible du proxy de votre API.

4. Dans le panneau de test, sélectionnez l'opération **get /current**.  
    a. Le paramètre zipcode étant nécessaire pour cette opération, entrez un code postal américain valide (par exemple, 90210).  
    b. Cliquez sur **invoke** et observez les informations qui s'affichent :  
    ```
    - 200 OK response
    - Current weather data for 90210  
    ```
_Si vous obtenez une erreur CORS, suivez les instructions fournies dans le message d'erreur. Cliquez sur le lien fourni pour ajouter l'exception à votre navigateur et appuyez ensuite de nouveau sur le bouton "invoke"._

    ![](images/test-invoke-1.png)


### Test avec l'_outil Explorer_.
_L'outil Explorer permet aux utilisateurs de tester le bon fonctionnement de l'API en imposant chacun des paramètres définis dans la définition d'OpenAPI. Ce contrôle n'étant pas effectué avec l'outil de test d'API de l'onglet Assembler, l'utilisateur peut ainsi vérifier le comportement de l'API lorsqu'un paramètre est manquant._

1. Pour tester les noeuds finaux du proxy d'API, sélectionnez **Explorer**, puis **Bac à sable**.
    ![](images/test-explore-1.png)
2. Sélectionnez l'opération **GET /current** dans la palette.
3. Sélectionnez "Essayer".  
4. Entrez un code postal américain valide (par ex. 90210) dans la zone de test.
5. Cliquez sur **Appeler une opération** pour afficher la réponse.
  ![](images/test-explore-2.png)

    ![](images/test-explore-3.png)


### Conclusion
Dans ce tutoriel, vous avez vu comment appeler un service REST existant à l'aide d'un proxy passe-système d'API. Vous avez commencé par vérifier la disponibilité de l'exemple de service via le navigateur Web. 
Ensuite, vous avez créé dans {{site.data.keyword.apiconnect_short}} un proxy d'API que vous avez lié à l'exemple de
service à appeler. Vous avez conditionné votre API dans un produit, publié ce produit dans un catalogue et testé le proxy.

---

## Etape suivante

Sécurisation de votre API à l'aide d'une [limitation de débit](tut_rate_limit.html), d'un [ID et d'une valeur confidentielle client](tut_secure_landing.html) ou [sécurisation à l'aide de OAuth 2.0](tut_secure_oauth_2.html).

Création > **Gestion** > Sécurisation > Réseaux sociaux > Analyse

