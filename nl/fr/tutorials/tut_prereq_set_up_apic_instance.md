---

copyright:
  years: 2019
lastupdated: "2019-3-14"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorials

subcollection: apiconnect

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Définition d'une instance API Connect
{: #tut_prereq_set_up_apic_instance}

**Durée**: 15 mn  
**Niveau de compétence** : Débutant  


## Prérequis
{: #prereq_tut_prereq_set_up_apic_instance}

1. Un IBMid
2. Un compte {{site.data.keyword.Bluemix_short}}
3. Une instance {{site.data.keyword.apiconnect_full}} avec au moins un plan _Lite_


<table>
  <tr><td><b>IBMid</b> : Utilisé pour accéder à toutes les applications, communautés, support et autres d'IBM
    <br>
    <b>{{site.data.keyword.Bluemix_notm}}</b> : Plateforme cloud d'IBM qui héberge {{site.data.keyword.apiconnect_short}} ainsi que d'autres applications et services<br>
    <b>{{site.data.keyword.apiconnect_short}}Lite</b> : Version gratuite d'{{site.data.keyword.apiconnect_short}} hébergée sur {{site.data.keyword.Bluemix_notm}}</td></tr>
  </table>  


---


1. Inscrivez-vous pour obtenir votre ID IBM Cloud à l'adresse URL suivante : [https://cloud.ibm.com/registration/ ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.ibm.com/registration/){: #new_window}.

	Vous avez déjà un IBMid ? Ignorez alors l'étape d'enregistrement et créez simplement votre compte {{site.data.keyword.Bluemix_short}} gratuit à l'adresse URL suivante : [https://cloud.ibm.com/ ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.ibm.com/){: #new_window}.  

2. Une fois en possession de votre IBMid et de votre compte {{site.data.keyword.Bluemix_notm}}, créez votre instance {{site.data.keyword.apiconnect_short}}.  
  a. Connectez-vous à {{site.data.keyword.Bluemix_notm}}: [https://cloud.ibm.com/login ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.ibm.com/login){: #new_window}.  
  ![](images/cloud_login_page.png)  
  b. Créez votre _organisation_ dans {{site.data.keyword.Bluemix_notm}}. Un message vous y invite lors de votre première connexion.  
  ![](images/prereqs-2.png)
  c. Créez votre _espace_.  
  ![](images/prereqs-3.png)
  d. Accédez à [https://console.ng.bluemix.net/catalog/services/api-connect ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://console.ng.bluemix.net/catalog/services/api-connect){: #new_window}.  
  ![](images/prereqs-4.png)  
  e. Sélectionnez le plan de tarification (gratuit) _Lite_, puis cliquez sur **Créer** pour démarrer.  
  ![](images/lite-plan.png)  
