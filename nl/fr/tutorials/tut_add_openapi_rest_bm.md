---
copyright:
  years: 2017
lastupdated: "2017-10-19"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Ajout d'une nouvelle spécification d'API et appel d'un service REST existant à l'aide d'IBM Bluemix
**Durée**: 15 mn  
**Niveau de compétence** : Débutant  

## Objectif
Ce tutoriel vous aide à démarrer rapidement avec {{site.data.keyword.apiconnect_full}}. Nous commencerons par créer une nouvelle spécification OpenAPI puis à créer un proxy d'API passe-système pour un service REST existant.

## Prérequis
Avant de commencer, vous devez [configurer votre instance API Connect](tut_prereq_set_up_apic_instance.html).

---

### Exploration du modèle d'application et test des noeuds finaux cible
Un modèle d'application _weather provider_ a été créé pour ce tutoriel.
1. Pour explorer l'application, accédez à [http://gettingstartedweatherapp.mybluemix.net/ ![Icône de lien externe](../../../icons/launch-glyph.svg "Icône de lien externe")](http://gettingstartedweatherapp.mybluemix.net/){:new_window}.  
2. Entrez un code postal américain en 5 chiffres valide pour en obtenir la _**météo actuelle**_ et les _**prévisions du jour**_.  
![](images/explore-weatherapp-1.png)

3. Le modèle d'application de météo ci-dessus a été généré à l'aide d'API qui fournissent des données météorologiques. Le noeud final permettant d'obtenir les données météorologiques **en cours** est _**https:// myweatherprovider<span></span>.mybluemix.net/current?zipcode={zipcode}**_. Testez-le en accédant à [https://myweatherprovider.mybluemix.net/current?zipcode=90210 ![Icône de lien externe](../../../icons/launch-glyph.svg "Icône de lien externe")](https://myweatherprovider.mybluemix.net/current?zipcode=90210){:new_window}.  

  ![](images/explore-weatherapp-2.png)

4. De même, le noeud final permettant d'obtenir les données prévisionnelles **d'aujourd'hui** est _**https:// myweatherprovider<span></span>.mybluemix.net/today?zipcode={zipcode}**_. Testez-le en accédant à [https://myweatherprovider.mybluemix.net/today?zipcode=90210 ![Icône de lien externe](../../../icons/launch-glyph.svg "Icône de lien externe")](https://myweatherprovider.mybluemix.net/today?zipcode=90210){:new_window}.  

  ![](images/explore-weatherapp-3.png)


---

### Ajout d'une nouvelle spécification OpenAPI pour créer un proxy d'API REST  
1. Connectez-vous à {{site.data.keyword.Bluemix_short}} : https://new-console.ng.bluemix.net/login.
2. Dans le panneau de navigation {{site.data.keyword.Bluemix_short}}, sélectionnez **Services**, puis **Tableau de bord**. Lancez le service {{site.data.keyword.apiconnect_short}}.
3. Dans {{site.data.keyword.apiconnect_short}}, vérifiez que le panneau de navigation est ouvert. S'il ne l'est pas, cliquez sur **>>** pour l'ouvrir.   
4. Sélectionnez **Brouillons** dans le panneau de navigation.
5. Dans l'onglet **API**, cliquez sur **Ajouter**. Dans le menu déroulant, sélectionnez **Nouvelle API**.    
  ![](images/create-new-1.png)  
6. Dans la fenêtre *Nouvelle API*, entrez `API Weather Provider` comme titre.
_Les zones Nom et Chemin de base sont automatiquement renseignées_.  
  ![](images/bluemix-add-new-api.png)
7. Cliquez sur **Créer une API** pour terminer la procédure de l'assistant.  
8. Une fois l'API créée, l'onglet **Conception** est sélectionné. 
9. Faites défiler jusqu'au panneau **Hôte**. Entrez la valeur `$(catalog.host)` si la zone n'est pas automatiquement renseignée.
10. Dans le panneau **Chemin de base**, notez que la valeur `/weather-provider-api` a été automatiquement renseignée. L'URL cible de votre API sera créée à partir de ces valeurs.  

11. Faites défiler jusqu'à l'onglet **Sécurité** et supprimez "clientIDHeader (API Key)", clé d'API automatiquement générée.  
_(Nous traiterons de la sécurité avec les clés d'API dans le prochain tutoriel.)_  

12. Dans le panneau de navigation, faites défiler vers le bas jusqu'au panneau **Chemins** et créez un nouveau chemin en cliquant sur **+**.     
    a. Nommez le nouveau chemin **/current**".  
    b. Dans le même panneau *Chemins*, sélectionnez la section **GET /current**.    
    c. Dans la section **GET /current**, ajoutez un nouveau **paramètre**. Comme vous l'avez remarqué lors de l'étude du modèle d'application, le service météo nécessite un paramètre code postal.   
      - Nom : code postal  
      - Situé dans : requête  
      - Obligatoire : oui  
      - Type : chaîne   
    ![](images/path-current-1.png)   
    d. Sauvegardez votre API.  

13. Une fois les paramètres de requête définis à l'étape précédente, vous devez définir l'objet réponse renvoyé lorsque vous appelez l'API weather. Pour ce faire, faites défiler vers le bas jusqu'au panneau **Définitions**.   
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

14. A l'étape précédente, vous avez défini l'objet réponse. Vous devez ensuite vous assurer que cet objet réponse est associé au chemin **get /current**. Dans le panneau de navigation, faites défiler vers le haut jusqu'au panneau **Chemins**.
    a. Ouvrez l'opération **GET /current** et faites défiler jusqu'à la section **Réponses**.
    b. Modifiez le schéma de réponse 200OK de "object" en "**Current**".
    c. Sauvegardez votre API en cliquant sur l'icône de sauvegarde. Une notification de confirmation "API sauvegardée" s'affiche brièvement. 

15. Le chemin et l'opération que vous venez de créer visent à obtenir les données météorologiques en cours. Vous devez maintenant créer un chemin et une opération similaires pour obtenir les données météorologiques d'aujourd'hui. Comme vous avez créé le chemin **/current** à l'étape 12, créez un nouveau chemin **/today**.

16. Ajoutez un nouveau paramètre sous l'opération **GET /today**.
    - Nom du paramètre : code postal  
    - Situé dans : requête  
    - Obligatoire : oui  
    - Type : chaîne  

17. Créez une nouvelle définition **Today**.

18. Ajoutez de nouvelles propriétés pour la définition **Today**.
    - Nom : zip / Type : chaîne
    - Nom : ha / Type : entier
    - Nom : ba / Type : entier
    - Nom : humidité nuit / Type : entier
    - Nom : humidité jour / Type : entier
    - Nom : ville / Type : chaîne
    - Nom : état / Type : chaîne
19. Mettez à jour le schéma de réponse dans la section **GET /today** avec "Today".
20. Sauvegardez votre API.

21. Basculez sur l'onglet **Assembler**. Jusqu'à présent, vous avez créé deux opérations : **GET /current** et **GET /today**. Pour vous assurer que le noeud final cible approprié est appelé, vous devez créer une logique qui exécute des actions conditionnelles sur l'opération appelée. Pour ce faire, utilisons la construction logique **Permutation d'opération**.  
    a. Supprimez la stratégie **invoke** qui a peut-être été ajoutée au _canevas_.  
    b. Depuis la palette, faites glisser la logique **Permutation d'opération** et déposez-la sur le canevas.  
      - Affectez au cas **case 0** l'opération **get /current**.
      - Ajoutez un nouveau cas : **case 1**.
      - Affectez l'opération **get /today** au cas **case 1**.
    ![](images/assemble-1.png)
    La logique **Permutation d'opération** fournit un point de décision. Sur la base de la paire verb/path, l'opération appropriée doit être appelée.
    c. Faites glisser la stratégie **invoke** depuis la palette et déposez-la sur le canevas. _La stratégie invoke est utilisée pour appeler un service existant dans le cadre d'une opération_.  Déposez une stratégie invoke dans le chemin **/get current** et une dans le chemin **/get today**.   
    d. Sélectionnez la stratégie **invoke** dans le chemin **/get current** et mettez à jour son titre avec "**invoke-current**".  
    e. Mettez à jour la zone URL avec `https://myweatherprovider.mybluemix.net/current?zipcode=$(request.parameters.zipcode)`.  
    f. Sélectionnez la stratégie **invoke** dans le chemin **/get today** et mettez à jour son titre avec "**invoke-today**".  
    g. Mettez à jour la zone URL avec `https://myweatherprovider.mybluemix.net/today?zipcode=$(request.parameters.zipcode)`.  
       ![](images/assemble-2.png)

22. Sauvegardez votre API.

---

### Test du proxy de votre API
1. Dans l'onglet **Assembler**, cliquez sur l'icône Plus d'actions, puis sélectionnez **Générer un produit par défaut**.  
   ![](images/generate-default-product-1.png) 

2. Acceptez les options par défaut de la boîte de dialogue **Nouveau produit**, puis cliquez sur **Créer un produit**. Le produit API Weather Provider est créé et publié dans le catalogue de bac à sable. Un message indiquant que la génération du produit a abouti s'affiche.  
  ![](images/generate-default-product-2.png)  
  
  ![](images/generate-default-product-3.png) 

  - _Dans {{site.data.keyword.apiconnect_short}}, **Produits** propose un mécanisme permettant de regrouper des API destinées à un usage particulier. Les produits sont publiés dans un **catalogue**. [Glossaire {{site.data.keyword.apiconnect_short}}](../apic_glossary.html)_

3. Dans l'onglet Assembler, cliquez sur l'icône de lecture pour tester l'appel de la cible du proxy de votre API.

4. Dans le panneau de test, sélectionnez l'opération **get /current**.
	a. Le paramètre zipcode étant nécessaire pour cette opération, entrez un code postal américain valide (par exemple, 90210). 
	b. Cliquez sur **invoke** et observez les informations qui s'affichent : 
  ```
  200 OK response
  Current weather data for 90210
  ```
  
    ![](images/test-invoke-1.png)  

    ![](images/test-invoke-2.png)  

    ![](images/test-invoke-3.png)

---

### Conclusion
Dans ce tutoriel, vous avez vu comment appeler un service REST existant à l'aide d'un proxy passe-système d'API. Vous avez commencé par vérifier la disponibilité de l'exemple de service via le navigateur Web. Puis vous avez créé une nouvelle spécification OpenAPI dans API Connect que vous avez liée à l'exemple de service à appeler. Vous avez conditionné votre API dans un produit, publié ce produit dans un catalogue et testé le proxy.

---

## Etape suivante 

Sécurisation de votre API à l'aide d'une [limitation de débit](tut_rate_limit.html), d'un [ID et d'une valeur confidentielle client](tut_secure_landing.html) ou [sécurisation à l'aide de OAuth 2.0](tut_secure_oauth_2.html).

Création > **Gestion** > Sécurisation > Réseaux sociaux > Analyse
