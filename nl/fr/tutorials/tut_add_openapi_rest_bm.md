---
copyright:
  years: 2019
lastupdated: "2019-3-9"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Ajout d'une spécification d'API et appel d'un service REST avec {{site.data.keyword.Bluemix_notm}}
{: #tut_add_openapi_rest_bm}

**Durée**: 15 mn  
**Niveau de compétence** : Débutant  

## Objectif
{: #object_tut_add_openapi_rest_bm}

Ce tutoriel vous aide à démarrer rapidement avec {{site.data.keyword.apiconnect_full}}. En quelques minutes, vous allez créer une API qui agit en tant que proxy d'API passe-système pour un service REST existant. L'API que vous créez offre des fonctions de sécurité et de surveillance. 

## Prérequis
{: #prereq_tut_add_openapi_rest_bm}

Avant de commencer, vous devez [configurer votre instance API Connect](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_set_up_apic_instance).

---

### Exploration du modèle d'application et test des noeuds finaux cible
{: #expl_tut_add_openapi_rest_bm}

Un modèle d'application _weather provider_ a été créé pour ce tutoriel.
1. Pour explorer l'application, accédez à [http://gettingstartedweatherapp.mybluemix.net/ ![Icône de lien externe](../../../icons/launch-glyph.svg "Icône de lien externe")](http://gettingstartedweatherapp.mybluemix.net/){: #new_window}.  
2. Entrez un code postal américain en 5 chiffres valide pour en obtenir la _**météo actuelle**_ et les _**prévisions du jour**_.  
![](images/explore-weatherapp-1.png)

3. Le modèle d'application de météo ci-dessus a été généré à l'aide d'API qui fournissent des données météorologiques. Le noeud final permettant d'obtenir les données météorologiques **en cours** est _**https://myweatherprovider.mybluemix.net/current?zipcode={zipcode}**_. Testez-le en accédant à [https://myweatherprovider.mybluemix.net/current?zipcode=90210 ![Icône de lien externe](../../../icons/launch-glyph.svg "Icône de lien externe")](https://myweatherprovider.mybluemix.net/current?zipcode=90210){: #new_window}.  

  ![](images/explore-weatherapp-2.png)

4. De même, le noeud final permettant d'obtenir les données prévisionnelles **d'aujourd'hui** est _**https:// myweatherprovider<span></span>.mybluemix.net/today?zipcode={zipcode}**_. Testez-le en accédant à [https://myweatherprovider.mybluemix.net/today?zipcode=90210 ![Icône de lien externe](../../../icons/launch-glyph.svg "Icône de lien externe")](https://myweatherprovider.mybluemix.net/today?zipcode=90210){: #new_window}.  

  ![](images/explore-weatherapp-3.png)


---

### Ajout d'une nouvelle spécification OpenAPI pour créer un proxy d'API REST  
{: #add_spec_tut_add_openapi_rest_bm}

1. Connectez-vous à {{site.data.keyword.Bluemix_short}} : https://cloud.ibm.com.
2. Dans le **Tableau de bord** {{site.data.keyword.Bluemix_notm}}, cliquez sur **Cloud Foundary Services**. Lancez le service {{site.data.keyword.apiconnect_short}}. 
3. Dans {{site.data.keyword.apiconnect_short}}, vérifiez que le panneau de navigation est ouvert. S'il ne l'est pas, cliquez sur **>>** pour l'ouvrir.  

  ![](images/cloud-apic-dashboard.png)

4. Sélectionnez **Brouillons** dans le panneau de navigation.
5. Dans l'onglet **API**, cliquez sur **Ajouter**. Dans le menu déroulant, sélectionnez **Nouvelle API**.    
  ![](images/cloud-add-api-new.png)  
6. Dans la fenêtre *Nouvelle API*, entrez `New Weather Provider API` comme titre.
_Les zones Nom et Chemin de base sont automatiquement renseignées_.  
  ![](images/bluemix-add-new-api2.png)
7. Cliquez sur **Créer une API** pour terminer la procédure de l'assistant.  
8. Une fois l'API créée, l'onglet **Conception** est sélectionné. 
9. Faites défiler jusqu'au panneau **Hôte**. Entrez la valeur `$(catalog.host)` si la zone n'est pas automatiquement renseignée.
10. Dans le panneau **Chemin de base**, notez que la valeur `/new-weather-provider-api` a été automatiquement renseignée. L'URL cible de votre API sera créée à partir de ces valeurs.  


11. Vous devez maintenant définir l'objet réponse renvoyé lorsque vous appelez l'API weather. Pour ce faire, cliquez sur **Définitions** dans la barre de navigation.    
    a. Ajoutez une nouvelle définition.  
    b. Nommez cette définition _Current_.  
    c. Définisse le type sur _Objet_.  
    d. Ajoutez de nouvelles propriétés pour la définition **Current**.    
       - Nom : zip         /  Type : chaîne   
       - Nom : température /  Type : entier   
       - Nom : humidité    /  Type : entier   
       - Nom : ville        /  Type : chaîne   
       - Nom : état / Type : chaîne   
	   
    ![](images/definition-current-1.png)   
	
    e. Sauvegardez votre API.  

12. Créez une nouvelle définition **Today**.

13. Ajoutez de nouvelles propriétés pour la définition **Today**.
    - Nom : zip / Type : chaîne
    - Nom : ha / Type : entier
    - Nom : ba / Type : entier
    - Nom : humidité nuit / Type : entier
    - Nom : humidité jour / Type : entier
    - Nom : ville        /  Type : chaîne
    - Nom : état / Type : chaîne

14. Une fois nos formats de données définis, nous pouvons créer des chemins d'appel. Dans la barre de navigation, cliquez sur **Chemins**. Créez un nouveau chemin en cliquant sur **+**.      
    a. Nommez le nouveau chemin "**/current**".  
    b. Dans le même panneau *Chemins*, sélectionnez la section **GET /current**.    
    c. Dans la section **GET /current**, ajoutez un nouveau **paramètre**. Comme vous l'avez remarqué lors de l'étude du modèle d'application, le service météo nécessite un paramètre code postal.   
      - Nom : code postal  
      - Situé dans : requête  
      - Obligatoire : oui  
      - Type : chaîne   
	  
    ![](images/path-current-1.png)   
	
    d. Faites défiler vers le bas.  Dans la section **Réponses**, affectez la valeur _En cours_ au **SCHEMA**.   
	
	![](images/path-current-responses.png)
	
	e. Sauvegardez votre API.  

15. Répétez les actions effectuées à l'étape 11 pour créer un autre chemin appelé "**/today**". Dans ce cas, définissez le schéma **Réponses** sur _Aujourd'hui_. Sauvegardez votre API.

16. Sauvegardez votre API.

17. Basculez sur l'onglet **Assembler**. Jusqu'à présent, vous avez créé deux opérations : **GET /current** et **GET /today**. Pour vous assurer que le noeud final cible approprié est appelé, vous devez créer une logique qui exécute des actions conditionnelles sur l'opération appelée. Pour ce faire, utilisons la construction logique **Permutation d'opération**.  La logique **Permutation d'opération** fournit un point de décision. Sur la base de la paire verb/path, l'opération appropriée doit être appelée.

    a. Supprimez la stratégie **invoke** qui a peut-être été ajoutée au _canevas_.  
    b. Depuis la palette, faites glisser la logique **Permutation d'opération** et déposez-la sur le canevas.  
      - Affectez au cas **case 0** l'opération **get /current**.
      - Ajoutez un nouveau cas : **case 1**.
      - Affectez l'opération **get /today** au cas **case 1**.
    
	  
	  
      ![](images/new-assemble-1.png)
	  
    c. Faites glisser la stratégie **invoke** depuis la palette et déposez-la sur la ligne de traitement sous **get /current**. _La stratégie invoke est utilisée pour appeler un service existant dans le cadre d'une opération_.   
    d. Mettez à jour le titre de l'action en "**invoke-current**".   
    e. Mettez à jour la zone URL avec `https://myweatherprovider.mybluemix.net/current?zipcode=$(request.parameters.zipcode)`.  
	
	![](images/new-assemble-invoke1.png)
	
	
	f. Faites glisser la stratégie **invoke** depuis la palette et déposez-la sur la ligne de traitement sous **get /today**.  
    g. Mettez à jour son titre en "**invoke-today**".  
    h. Mettez à jour la zone URL avec `https://myweatherprovider.mybluemix.net/today?zipcode=$(request.parameters.zipcode)`.  
	
       ![](images/new-assemble-invoke2.png)
	   

18. Fermez le panneau de configuration des actions. Sauvegardez votre API.

---

### Test du proxy de votre API
{: #test_proxy_tut_add_openapi_rest_bm}

1. Dans l'onglet **Assembler**, cliquez sur l'icône Plus d'actions, puis sélectionnez **Générer un produit par défaut**.  
   ![](images/generate-default-product-small.png) 

2. Acceptez les options par défaut de la boîte de dialogue **Nouveau produit**, puis cliquez sur **Créer un produit**. Le produit API Weather Provider est créé et publié dans le catalogue de bac à sable. Un message indiquant que la génération du produit a abouti s'affiche.  

  ![](images/generate-default-product-new-weather.png) 

  - _Dans {{site.data.keyword.apiconnect_short}}, **Produits** propose un mécanisme permettant de regrouper des API destinées à un usage particulier. Les produits sont publiés dans un **catalogue**. [Glossaire {{site.data.keyword.apiconnect_short}}](../apic_glossary.html)_

3. Dans l'onglet Assembler, cliquez sur l'icône de lecture pour tester l'appel de la cible du proxy de votre API.

4. Dans le panneau de test, sélectionnez l'opération **get /current**.

	a. Le paramètre zipcode étant nécessaire pour cette opération, entrez un code postal américain valide (par exemple, 10504).  
	
	![](images/test-invoke-params.png)  
		
	b. Cliquez sur **Appeler**.   

	_Si vous obtenez une erreur CORS, suivez les instructions fournies dans le message d'erreur. Cliquez sur le lien fourni pour ajouter l'exception à votre navigateur et appuyez ensuite de nouveau sur le bouton "invoke"._
  
    ![](images/test-invoke-new.png)  


---

### Conclusion
{: #conclusion_tut_add_openapi_rest_bm}

Dans ce tutoriel, vous avez vu comment appeler un service REST existant à l'aide d'un proxy passe-système d'API. Vous avez commencé par vérifier la disponibilité de l'exemple de service via le navigateur Web. Puis vous avez créé une nouvelle spécification OpenAPI dans {{site.data.keyword.apiconnect_short}} que vous avez liée à l'exemple de service à appeler. Vous avez conditionné votre API dans un produit, publié ce produit dans un catalogue et testé le proxy.

---

## Etape suivante
{: #next_tut_add_openapi_rest_bm}

Sécurisation d'une API [à l'aide d'OAuth 2.0](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_oauth_2).

Création > **Gestion** > Sécurisation > Réseaux sociaux > Analyse
