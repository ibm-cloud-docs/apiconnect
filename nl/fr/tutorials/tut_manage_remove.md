---

copyright:
  years: 2017
lastupdated: "2017-10-10"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Archivage et suppression de produits d'API
**Durée**: 15 mn  
**Niveau de compétence** : Débutant 

## Prérequis

1. [Configurez votre instance {{site.data.keyword.apiconnect_full}}](tut_prereq_set_up_apic_instance.html).

2. Exécutez le [tutoriel Substitution d'un produit d'API](tut_manage_supercede.html).

---
## Objectif
Dans ce tutoriel, vous allez supprimer, archiver et retirer une API.

---
## Suppression d'un produit d'API
1. Connectez-vous à {{site.data.keyword.Bluemix_short}}: [https://console.ng.bluemix.net/login ![Icône de lien externe](../../../icons/launch-glyph.svg "Icône de lien externe")](https://console.ng.bluemix.net/login){:new_window}.

2. Dans le tableau de bord {{site.data.keyword.Bluemix_short}}, lancez le service {{site.data.keyword.apiconnect_short}}.
![](images/Bluemix.png)

3. Dans le gestionnaire d'API, si vous n'avez pas encore épinglé le panneau de navigation de l'interface utilisateur, cliquez sur l'icône **Accéder à** ![](images/navigate-to.png). Le panneau de navigation de l'interface utilisateur du gestionnaire d'API s'ouvre. Pour épingler le panneau de Navigation de l'interface utilisateur, cliquez sur l'icône **Epingler le menu** ![](images/pinned.png).

4. Cliquez sur **Bac à sable** pour ouvrir le catalogue de bac à sable. **Remarque** : Vous devrez peut-être revenir dans le tableau de bord pour voir les catalogues disponibles. Il est également possible que votre page de tableau de bord affiche les catalogues sous forme de mosaïques au lieu d'une liste.
![](images/del-sandbox-list.png)

5. Cliquez sur les points de suspension verticaux sur la ligne **API Weather Provider 1.0.0**.  
![](images/del-prod-list1.png)

6. Sélectionnez **Supprimer du catalogue**.  
![](images/del-del-from-cat.png)

7. Cliquez sur **OK**.  
![](images/del-del-dialog.png)
    Le produit disparaît de la liste des produits dans le catalogue. Il ne peut pas être récupéré à ce stade.


## Archivage d'un produit d'API
1. Cliquez sur les points de suspension verticaux sur la ligne **API Weather Provider 2.0.0**.  
![](images/del-prod-list2.png)

2. Sélectionnez **Retirer**.  
![](images/del-select-retire.png)

3. Cliquez sur **OK**.  
![](images/del-retire-dialog.png)

4. Cliquez sur les points de suspension verticaux sur la ligne **API Weather Provider 2.0.0**.  
![](images/del-prod-list3.png)

5. Sélectionnez **Archiver**.  
![](images/del-select-archive.png)

6. Cliquez sur **OK**.  
![](images/del-archive-dialog.png)
    Le produit disparaît de la liste des produits dans le catalogue. Il peut être récupéré.

7. Cliquez sur l'icône de vue de liste.  
![](images/del-prod-list4.png)

8. Cochez **Archivé**.  
![](images/del-view-archived.png)

9. Cliquez sur les points de suspension verticaux sur la ligne **API Weather Provider 2.0.0**.  
![](images/del-prod-list5.png)

10. Sélectionnez **Désarchiver**.  
![](images/del-unarchive.png)
    Le produit passe à l'état Retiré.
    ![](images/del-prod-list6.png)

 
 
## Tâches exécutées dans ce tutoriel
Dans ce tutoriel, vous avez effectué les activités suivantes :

1. Suppression d'un produit d'API
2. Retrait d'un produit d'API
3. Archivage d'un produit d'API
4. Désarchivage d'un produit d'API

---












