---
copyright:
  years: 2017
lastupdated: "2017-09-30"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Sécurisation de votre API avec un ID client et une valeur confidentielle du client à l'aide d'IBM Bluemix

**Durée :** 10 mn  
**Niveau de compétence :** Débutant


## Objectif

Ce tutoriel vous guidera tout au long du processus de sécurisation de votre API avec un ID client et une valeur confidentielle du client. Lorsque des applications sont enregistrées dans votre portail de développeur, un ID client est généré afin d'identifier l'application. Une valeur confidentielle du client, qui sert de mot de passe, peut éventuellement être aussi générée. Les applications devront fournir les clés ID client et Valeur confidentielle du client pour pouvoir accéder à votre API.


## Prérequis

Avant de commencer, vous devez avoir terminé l'un des tutoriels suivants : 
- [Importation d'une spécification d'OpenAPI2.0 et passage par un proxy d'un service REST existant](tut_rest_landing.html)  
**ou**  
- [Ajout d'une nouvelle spécification d'API et appel d'un service REST existant](tut_rest_landing.html)


## Définition du mécanisme d'identification de votre API

1. Accédez à la vue Concevoir de votre API comme suit :  
   a. Cliquez sur **Brouillons** dans le panneau de navigation de gauche  
   b. Cliquez ensuite sur l'onglet **API**  
   c. Cliquez sur l'_API Weather Provider_ que vous avez créée dans le précédent tutoriel. La vue **Concevoir** de cette API s'ouvre.  
   ![](images/1_goto_drafts_api.png)  

2. Dans la vue Concevoir :
    a. Faites défiler jusqu'à **Définitions de sécurité**.  
    b. Cliquez sur l'icône d'**ajout de définitions de sécurité** (+), puis sur **Clé d'API**.  
    c. Ajoutez les deux nouvelles clés d'API indiquées ci-dessous. Assurez-vous pour les deux clés que la zone "Situé dans" est définie sur "En-tête".  
      - Nom : ID client ;  Nom du paramètre : X-IBM-Client-Id  
      - Nom : Valeur confidentielle du client ;  Nom du paramètre : X-IBM-Client-Secret    
        ![](images/2_security_definitions.png)  

3. Faites défiler jusqu'au panneau **Sécurité** et ajoutez une nouvelle option de sécurité.  
    a. Sélectionnez les clés ID client et Valeur confidentielle du client que vous venez de créer.  
    b. Sauvegardez votre API.  
    c. Basculez sur l'onglet **Assembler**.   
    ![](images/3_security_option.png)  


## Test des modifications apportées à votre API

1. Dans l'onglet Assembler, cliquez sur le bouton ► pour tester vos modifications.

2. Dans le panneau de test/configuration, cliquez sur **Republier le produit** pour obtenir les dernières modifications. 
> Cette option met à jour votre produit d'API et le publie dans le catalogue de bac à sable.

3. Une fois le produit republié, cliquez sur l'opération **get /current** dans le panneau de test.
4. Faites défiler le panneau de test vers le bas ; vous remarquerez que les valeurs ID client et Valeur confidentielle du client sont déjà renseignées. 
> Ce sont des valeurs de test générées pour votre bac à sable et correspondant aux clés de l'application qui utilisera votre API.
> **Remarque :** Les clés ID client et Valeur confidentielle du client figurent également sous Tableau de bord > Catalogue > Paramètres > Noeuds finaux]_   
  
  ![](images/test_api_keys_1.png)

5. Faites défiler un peu plus vers le bas et entrez un code postal (par ex. 90210). 
6. Cliquez sur **Appeler**. _Vous devez obtenir une réponse 200 OK, accompagnée du corps du message qui renvoie les informations météorologiques._
7. Faites maintenant défiler vers le haut jusqu'à la zone ID client. 
8. Remplacez la valeur d'ID client par une valeur aléatoire.
9. Exécutez de nouveau le test en cliquant sur **Appeler**. _Vous obtiendrez une réponse 401, accompagnée du message "Client ID not registered"._  

    ![](images/test_api_keys_3.png)  


## Appel de votre API à l'aide de l'ID client et de la valeur confidentielle du client

Vous pouvez également tester les paramètres de sécurité à l'aide de l'outil Explorer qui appelle explicitement le noeud final de proxy et transmet les clés ID client et Valeur confidentielle du client en tant que valeurs d'en-tête.

1. Cliquez sur **Explorer**, puis sur **Bac à sable**.
    ![](images/explore_1.png)

2. Sélectionnez l'opération **GET /current** dans la liste.

3. Dans la colonne de droite, cliquez sur **Appeler une opération** pour réexécuter le test.
    ![](images/explore_3.png)

---

## Conclusion
Dans ce tutoriel, vous avez appris à configurer le mécanisme d'identification de votre API, tester les modifications apportées à votre API et appeler votre API en utilisant l'ID client et la valeur confidentielle du client. 

---

## Etape suivante 

Commencez à diffuser votre API sur les réseaux sociaux via la [création et configuration d'un portail de développeur](tut_config_dev_portal.html).

Création > Gestion > **Sécurisation** > Réseaux sociaux > Analyse
