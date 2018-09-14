---
copyright:
  years: 2017
lastupdated: "2017-12-15"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Gain de connaissances à partir d'analyses basiques
Durée : 30 mn  
Niveau de compétence : Débutant

## Objectif
Introduction de base aux analyses d'API dans {{site.data.keyword.apiconnect_full}}. Nous ferons le tour des tableaux de bord d'analyse disponibles et vous pourrez continuer avec vos propres API.


## Prérequis
pour pouvoir afficher vos propres analyses d'API, vous devez avoir créé et publié un produit d'API. En outre, vous devrez appeler votre API plusieurs fois afin de générer des données d'analyse, de préférence avec un identificateur client issu d'une application enregistrée (et non de l'application de test pré-provisionnée).

Pour générer les données dans ce tutoriel, nous avons utilisé *Collection Runner* de Postman pour appeler plusieurs fois une API, avec des données et des ID client différents. Vous pouvez utiliser le même type d'outil (par exemple, HttpRequester pour Firefox) ou utiliser simplement cURL pour appeler plusieurs fois votre API depuis la ligne de commande. Pour obtenir des exemples de demande pour votre API, cliquez sur le lien **Explorer** dans {{site.data.keyword.apiconnect_short}}.

## Introduction aux analyses de catalogue
En tant que propriétaire d'API, vous devez pouvoir évaluer la réussite et les performances des API que vous offrez. Le principal emplacement où rechercher des analyses est le niveau catalogue. Si vous n'avez pas l'habitude des catalogues, voir [Utilisation de catalogues ![Icône de lien externe](../../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/conref_working_with_env.html){:new_window} dans l'IBM Knowledge Center pour une introduction. 

Vous pouvez également, ainsi que vos développeurs d'applications, accéder à des analyses spécifique d'applications dans le portail de développeur mais, dans ce tutoriel, nous nous concentrons sur les analyses de catalogue.

Vous pouvez accéder à 90 jours d'informations en temps réel et historiques concernant vos API et produits publiés dans ce catalogue. Il indique également qui les appelle. Si votre catalogue contient plusieurs espaces, vous pouvez naviguer jusqu'au niveau Espace.

Ce tutoriel se compose de quatre activités qui montrent comment effectuer les tâches suivantes :
* Afficher les analyses
* Afficher les détails des enregistrements d'événement
* Générer de nouveaux tableaux de bord
* Créer de nouvelles visualisations


## Activité 1 : Affichage des analyses de boîte
1. Dans le service {{site.data.keyword.apiconnect_short}} dans {{site.data.keyword.Bluemix_short}}, lancez votre tableau de bord et sélectionnez le catalogue que vous voulez ouvrir. 
2. Cliquez sur l'onglet *Analyse*.

   ![](./images/analyticstab.png) 
  
Le tableau de bord par défaut Vue d'ensemble s'affiche. Il présente deux visualisation de graphique à barres qui contiennent les données suivantes issues des 7 derniers jours :
* 5 produits les plus actifs 
* 5 API les plus actives 

3. Survolez l'une des barres pour afficher des détails supplémentaires, tels que le nombre d'API, les noms d'API, etc.

   ![](./images/defaultoverview.png) 

4. Utilisez la barre de recherche pour filtrer les données affichées. Vous pouvez également sélectionner un autre filtre temporel et/ou taux d'actualisation automatique. Les visualisations sont mises à jour afin de répercuter vos sélections.

D'autres tableaux de bord prêts à l'emploi sont fournis.

5. Cliquez sur l'icône de dossier pour charger un tableau de bord sauvegardé, puis sélectionnez **api_default** dans la liste déroulante.

   ![](./images/api_default.png) 

Ce tableau de bord propose un autre ensemble de visualisations qui affichent le statut des API, les erreurs, les temps de réponse, le nombre total d'appels et les appels par jour.

   ![](./images/sandbox-api_default.png) 


## Activité 2 : Affichage des détails d'événement

Les visualisations sont un bon moyen pour obtenir une présentation utile des données, mais il vous faut également un moyen pour naviguer entre les enregistrement d'événement qui alimentent les graphiques.

1. Survolez l'icône en forme de flèche située dans l'angle inférieur gauche de chaque visualisation. Une petite flèche apparaît.
2. Cliquez sur la flèche pour afficher un tableau des données utilisées dans cette visualisation. 
3. Cliquez sur le libellé **Afficher événements** pour naviguer jusqu'à 100 enregistrements de détails d'événements individuels.

   ![](./images/statuscodetable.png) 

Vous pouvez éditer, déplacer et supprimer des visualisations dans votre tableau de bord.

## Activité 3 : Génération de nouveaux tableaux de bord

Maintenant, créons un nouveau tableau de bord qui fournira une vue des modèles de trafic d'API. Ils sont tous disponibles via les visualisations intégrées. 

1. Cliquez sur l'icône du nouveau tableau de bord, puis cliquez sur le lien **Choose from existing visualizations**. 

   ![](./images/newdashboard.png) 
    La liste des visualisations disponibles s'affiche.

2. Sélectionnez quelques visualisations à ajouter à votre tableau de bord.  Par exemple :
  * Subscribed Apps
  * Apps per Plan 
  * Success Rate
  * API Calls per Day
  
  **Conseil** Lorsque vous sélectionnez chaque visualisation, l'onglet de sélection bloque votre vue du tableau de bord et il est possible que vous ne voyiez que la visualisation a été ajoutée au tableau de bord. Sélectionnez les visualisations l'une après l'autre en fermant ensuite chaque fois l'onglet de sélection de manière à voir les modifications apportées à votre tableau de bord.

3. Cliquez sur **Sauvegarder** et attribuez un nom à votre tableau de bord : `Subscriber Dashboard`.

   ![](./images/savedashboard.png)

   ![](./images/namedashboard.png) 


## Activité 4 : Création de nouvelles visualisations
Dans le tableau de bord d'abonné (Subscriber Dashboard) que nous avons créé, nous avons inclus la visualisation intégrée qui affiche les appels API par jour (API Calls per Day). Lorsque nous observons toutes les informations présentées ensemble, vous aimeriez connaître leur utilisation par application. Créons une nouvelle visualisation qui donne cette information.

1. Cliquez sur **New Visualization** et sélectionnez le lien **Create Visualizations**.
   ![](./images/newvisualization.png) 

2. Sélectionnez **Graphique à courbes** comme type de visualisation. Le graphique à courbes initialisé présente un axe des Y qui correspond au nombre d'appels API. Cette option est appropriée pour notre graphique.

3. Sélectionnez les éléments suivants :
	* Type de compartiments : **Axe des X**
	* Agrégation : **Date Histogram**
	* Libellé personnalisé : **Horodatage** 
4. Cliquez sur **Exécuter** pour afficher votre graphique. **Conseil** : Vous devrez peut-être ajuster la période pour voir les données.

   ![](./images/apichart1.png)

Ce graphique (jusqu'à présent) affiche une série temporelle d'appels API. Nous voulons voir les appels API par nom d'application.

5. Cliquez sur le bouton **Add sub-buckets**.
6. Sélectionnez les éléments suivants :
	* Type de compartiments : **Split Lines**
	* Sous-agrégation : **Conditions**
	* Zone : **app_name**
	* Libellé personnalisé : **App**
	
   ![](./images/subbucket.png)
8. Cliquez sur **Exécuter** pour afficher votre graphique.
9. Cliquez sur **Sauvegarder** et attribuez un nom à votre graphique `API Calls by App`.
10. Pour voir votre visualisation en contexte, ajoutez-la dans le tableau de bord d'abonnés.

   ![](./images/apichartfinal.png)
 
D'autres informations sont disponibles pour visualiser les détails concernant les appels API, les appelants, etc. La liste complète des événements d'API est disponible dans le Knowledge Center d'API Connect ou dans la liste des conditions lorsque vous créez des visualisations.

## Conclusion

La possibilité de visualiser des analyses d'API dans différents styles et combinaisons vous permet de tirer des conclusions ou d'analyser plus en profondeur vos données d'API. Vous pouvez utiliser ces analyses pour prendre des décisions concernant les API à proposer, le moment où remplacer ou retirer une API, les personnes consommatrices de vos API, etc.

Par exemple, des API version 1 (v1) et version 2 (v2) d'un fournisseur nommé "ACME" ont été exécutées pendant plusieurs années. La version 1 est devenue obsolète au moment de la publication de la version 2. Le fournisseur s'est assuré que les consommateurs de la version 1 étaient avertis qu'ils disposaient d'un certain délai pour passer à la version 2. Lorsque cette échéance approche, ACME veut savoir à quelle vitesse les consommateurs quittent la version 1, de manière à offrir une assistance à des partenaire de choix. 

En s'appuyant sur une visualisation semblable à celle que nous venons de développer, ACME obtient cette information en un clin d'oeil.

Dans ce tutoriel, nous avons parcouru un certains nombre d'activités pour vous aider à créer des combinaison utiles d'API et de données sur les consommateurs. A l'aide des visualisations et des tableaux de bord, nous avons rapidement créé des outils qui fournissent des données permettant de garantir que nous offrons la combinaison idéale d'API.

---

## Etape suivante

Apprenez à [gérer vos API et vos versions](tut_manage_version_landing.html).

Création > Gestion >Sécurisation> Réseaux sociaux > **Analyse**  
