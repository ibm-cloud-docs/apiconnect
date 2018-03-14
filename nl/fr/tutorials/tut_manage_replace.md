---

copyright:
  years: 2017
lastupdated: "2017-10-31"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Remplacement d'un produit d'API
**Durée**: 15 mn  
**Niveau de compétence** : Débutant  


## Prérequis

1. [Configurez votre instance {{site.data.keyword.apiconnect_full}}](tut_prereq_set_up_apic_instance.html).

2. Effectuez l'un des tutoriels suivants :
 
    - [Importation d'une spécification d'OpenAPI2.0 et passage par un proxy d'un service REST existant](tut_rest_landing.html)
**ou**  
    - [Ajout d'une nouvelle spécification d'API et appel d'un service REST existant](tut_rest_landing.html).

---
## Objectif
Dans ce tutoriel, vous mettrez à jour un produit d'API existant en le remplaçant par un plus récent. Lorsqu'un produit d'API est remplacé, les modifications prennent effet immédiatement et tous les abonnements à des applications sont automatiquement mis à jour.  


---
## Remplacement d'un produit d'API
{: #repl_api_prod}

1. Connectez-vous à {{site.data.keyword.Bluemix_short}}: [https://console.ng.bluemix.net/login ![Icône de lien externe](../../../icons/launch-glyph.svg "Icône de lien externe")](https://console.ng.bluemix.net/login){:new_window}.

2. Dans le tableau de bord {{site.data.keyword.Bluemix_notm}}, lancez le service {{site.data.keyword.apiconnect_short}}.
![](images/Bluemix.png)

3. Dans le gestionnaire d'API, si vous n'avez pas encore épinglé le panneau de navigation de l'interface utilisateur, cliquez sur l'icône **Accéder à** ![](images/navigate-to.png). Le panneau de navigation de l'interface utilisateur du gestionnaire d'API s'ouvre. Pour épingler le panneau de Navigation de l'interface utilisateur, cliquez sur l'icône **Epingler le menu** ![](images/pinned.png).

4. Cliquez sur **Brouillons** > **API**.

5. Dans le panneau API, cliquez sur **API Weather Provider** pour ouvrir l'API de proxy REST.  
![](images/rep-api-list.png)

6. Modifiez la **Version** en 2.0.0.  

7. Cliquez sur l'icône de disque pour sauvegarder les modifications apportées à l'API.  
![](images/rep-change-version.png)

8. Cliquez sur **Toutes les API**.  
![](images/rep-all-apis.png)

9. Cliquez sur **Produits**.  
![](images/rep-api-list-2.png)

10.	Sélectionnez **Produit d'API Weather Provider**.  
![](images/rep-draft-prod-list.png)

11.	Modifiez la **Version** en 2.0.0. Entrez `API mise à jour` dans la zone **Description**. Cliquez sur l'icône de disque pour sauvegarder les modifications.  
![](images/rep-update-prod.png)

12.	Cliquez sur l'icône **Transférer** pour télécharger la nouvelle version. Sélectionnez le catalogue **Bac à sable** s'il n'est pas déjà sélectionné.
![](images/rep-stage-prod-2.png)
    **Remarque** : Il est possible de transférer une nouvelle version dans un autre catalogue, ce qui permet de contrôler quels développeurs auront accès à cette version. Cette possibilité peut se révéler utile s'agissant de déplacer des produits d'API d'un environnement de développement vers un environnement de test, puis de production.

13.	Cliquez sur **>>** pour ouvrir le panneau de navigation, puis sélectionnez **Tableau de bord**.  
![](images/rep-dashboard.png)

14.	Cliquez sur **Bac à sable**.  

15.	Cliquez sur les points de suspension verticaux sur la ligne **Produit d'API Weather Provider 2.0.0 transféré**.  
![](images/rep-dash-prod-list-2.png)

16.	Sélectionnez **Remplacer un produit existant**.  
![](images/rep-replace-prod.png)

17.	Sélectionnez **Produit d'AP Weather Provider 1.0.0** dans la liste de produits affichée. Cliquez sur **Suivant**.  
![](images/rep-replace-dialog.png)

18.	Sélectionnez **Plan par défaut**. Cliquez sur **Remplacer**.  
![](images/rep-replace-dialog-2.png)

    Suite à cette opération, le produit d'API Weather Provider 1.0.0 est retiré et le produit d'API Weather Provider 2.0.0 est publié. **Remarque** : Il est possible de modifier le plan associé à ce produit au cours du processus de remplacement. C'est un moyen facile de modifier le plan d'un produit d'API. ![](images/rep-prod-retired.png) 
 

## Tâches exécutées dans ce tutoriel

Dans ce tutoriel, vous avez effectué les activités suivantes :
1. Mise à jour d'un produit d'API.
2. Remplacement d'un produit d'API existant par un produit d'API mis à jour.

---












