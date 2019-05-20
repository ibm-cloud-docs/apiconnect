---

copyright:
  years: 2019
lastupdated: "2017-3-15"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Remplacement d'un produit d'API
{: #tut_manage_replace}

**Durée**: 15 mn  
**Niveau de compétence** : Débutant  

## Objectif
{: #object_tut_manage_replace}
Dans ce tutoriel, vous mettrez à jour un produit d'API existant en le remplaçant par un plus récent. Lorsqu'un produit d'API est remplacé, les modifications prennent effet immédiatement et tous les abonnements à des applications sont automatiquement mis à jour.  

---
## Prérequis
{: #prereq_tut_manage_replace}

1. [Configurez votre instance {{site.data.keyword.apiconnect_full}}](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_set_up_apic_instance).

2. Effectuez l'un des tutoriels suivants :
 
    - [Importation d'une spécification d'OpenAPI2.0 et passage par un proxy d'un service REST existant](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_rest_landing)
**ou**  
    - [Ajout d'une nouvelle spécification d'API et appel d'un service REST existant](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_rest_landing).

---

## Remplacement d'un produit d'API
{: #repl_api_prod_tut_manage_replace}}

1. Connectez-vous à {{site.data.keyword.Bluemix_short}} : https://cloud.ibm.com.
2. Dans le **Tableau de bord** {{site.data.keyword.Bluemix_notm}}, cliquez sur **Cloud Foundary Services**. Lancez le service {{site.data.keyword.apiconnect_short}}. 
3. Dans {{site.data.keyword.apiconnect_short}}, vérifiez que le panneau de navigation est ouvert. S'il ne l'est pas, cliquez sur **>>** pour l'ouvrir.  

  ![](images/cloud-apic-dashboard.png)

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
 

## Conclusion
{: #conclusion_tut_manage_replace}

Dans ce tutoriel, vous avez effectué les activités suivantes :
1. Mise à jour d'un produit d'API.
2. Remplacement d'un produit d'API existant par un produit d'API mis à jour.

---












