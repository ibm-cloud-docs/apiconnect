---

copyright:
  years: 2019
lastupdated: "2017-3-18"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial


---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Remplacement de produits d'API
{: #tut_manage_supercede}

**Durée**: 15 mn  
**Niveau de compétence** : Débutant  

## Objectif
{: #object_tut_manage_supercede}

Dans ce tutoriel, vous allez remplacer une API existante par une nouvelle API.

---
## Prérequis
{: #prereq_tut_manage_supercede}

1. [Configurez votre instance {{site.data.keyword.apiconnect_full}}](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_set_up_apic_instance).

2. Exécutez le [tutoriel Remplacement d'un produit d'API](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_manage_replace).

---

## Remplacement d'un produit d'API
{: #super_tut_manage_supercede}

1. Connectez-vous à {{site.data.keyword.Bluemix_short}} : https://cloud.ibm.com.
2. Dans le **Tableau de bord** {{site.data.keyword.Bluemix_notm}}, cliquez sur **Cloud Foundary Services**. Lancez le service {{site.data.keyword.apiconnect_short}}. 
3. Dans {{site.data.keyword.apiconnect_short}}, vérifiez que le panneau de navigation est ouvert. S'il ne l'est pas, cliquez sur **>>** pour l'ouvrir.  

  ![](images/cloud-apic-dashboard.png)

4. Cliquez sur **Brouillons** > **API**.

5. Dans le panneau API, cliquez sur **API Weather Provider** pour ouvrir l'API de proxy REST.  
![](images/rep-api-list.png)

6. Modifiez la **Version** en 3.0.0.

7. Cliquez sur l'icône de disque pour sauvegarder les modifications apportées à l'API.  
![](images/sup-change-version.png)

8. Cliquez sur **Toutes les API**.  
![](images/rep-all-apis.png)

9. Cliquez sur **Produits**.  
![](images/sup-prods.png)

10.	Sélectionnez **Produit d'API Weather Provider 2.0.0**.  
![](images/sup-draft-prod-list.png)

11.	Modifiez la **Version** en 3.0.0. Cliquez sur l'icône de disque pour sauvegarder les modifications. Cliquez sur l'icône **Transférer**.  
![](images/sup-change-prod-vers-3.png)

12.	Cliquez sur **>>** pour ouvrir le panneau de navigation, puis sélectionnez **Tableau de bord**.  
![](images/rep-dashboard.png)

13.	Cliquez sur **Bac à sable**.

14.	Cliquez sur **Communauté**.  
![](images/sup-sand-dash.png)

15.	Cliquez sur **Abonnements**.  
![](images/sup-comm-orgs.png)

16.	Notez les abonnements d'application au produit d'API Weather Provider 2.0.0. Cliquez sur **Produits**.
![](images/sup-scriptions-200.png)  

17.	Cliquez sur les points de suspension verticaux sur la ligne **Produit d'API Weather Provider 3.0.0 transféré**.  
![](images/sup-stage-prod-3.png)

18.	Sélectionnez **Substituer un produit existant**.  
![](images/sup-super-prod.png)

19.	Sélectionnez **Produit d'API Weather Provider 2.0.0** dans la liste de produits affichée. Cliquez sur **Suivant**.  
![](images/sup-super-dialog-1.png)

20.	Sélectionnez **Plan par défaut**. Cliquez sur **Substituer**.  
![](images/sup-super-dialog-2.png)
    Suite à cette opération, le produit d'API Weather Provider 2.0.0 devient obsolète et le produit d'API Weather Provider 3.0.0 est publié.  
![](images/sup-dash-prods-3.png) 
 
21.	Cliquez sur **Communauté >> Abonnements**.  
![](images/sup-scriptions-200.png)
 
22.	Cliquez sur les points de suspension verticaux sur la ligne **Produit d'API Weather Provider 2.0.0**. Sélectionnez **Gérer**.  
![](images/sup-dots-manage.png) 

23.	Sélectionnez **Plan par défaut** sous Produit d'API Weather Provider 3.0.0 . Cliquez sur **Migrer**.  
![](images/sup-migrate-dialog.png)
    Suite à cette opération, le produit d'API Weather Provider 2.0.0 est migré vers le produit d'API Weather Provider 3.0.0.  
![](images/sup-migrated.png) 
 

 
## Conclusion
{: #conclusion_tut_manage_supercede}

Dans ce tutoriel, vous avez effectué les activités suivantes :

1. Mise à jour d'un produit d'API.
2. Remplacement d'un produit d'API existant par un produit d'API mis à jour.
3. Migration de l'abonnement au produit d'API existant vers le produit d'API mis à jour.

---












