---

copyright:
  years: 2017
lastupdated: "2017-12-15"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal

subcollection: apiconnect

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Importation d'API
{: #importing_apis}

Vous pouvez utiliser un fichier de définition pour ajouter une API REST.
{:shortdesc}

## Prérequis
{: #prereq_import_swagger_importing_apis}

Avant de commencer, vérifiez que votre fichier est conforme à la version 2.0
de la spécification swagger. Le format du fichier peut être JSON ou YAML.

Pour ajouter une API REST en chargeant un fichier swagger, procédez
comme suit :

1. Dans le panneau de navigation de l'interface utilisateur du gestionnaire d'API, cliquez sur **Brouillons**,
puis sur **API**.
L'onglet API s'ouvre.

2. Cliquez sur **+ Ajouter**, puis sélectionnez **Swagger 2.0** dans
la section **Importer**.
La fenêtre **Importer une API swagger** s'ouvre.

3. **Facultatif** :
Pour télécharger un fichier à partir de votre système de fichiers local, cliquez sur **Sélectionner un fichier** puis, dans
votre système de fichiers, sélectionnez le fichier à utiliser. Les fichiers `.json`, `.yml` et `.yaml` sont pris en charge s'ils contiennent une définition swagger valide.

4. **Facultatif** :
Pour télécharger un fichier à partir d'une URL, cliquez sur **Ou importer à partir d'une URL**, puis indiquez
l'URL correcte dans la zone **URL** affichée. Si l'authentification est
requise pour accéder à l'URL, entrez un nom d'utilisateur et un mot de passe. Les fichiers `.json`, `.yml` et `.yaml` sont pris en charge s'ils contiennent une définition swagger valide.

5. Cliquez sur **Importer**.
Une nouvelle définition d'API REST est créée, ainsi que les chemins d'accès et les opérations HTTP.

Une fois que la définition d'API a été importée, elle s'affiche dans la liste des définitions d'API, dans l'onglet **API** de la page **Brouillons**.
Vous pouvez ensuite éditer votre définition d'API comme vous le feriez pour n'importe quel autre définition d'API REST.

## Importation d'API à partir d'IBM Integration Bus
{: #tut_import_iib_apic_importing_apis}

Ce tutoriel vous permet d'importer des API REST que vous créez avec IBM Integration Bus dans {{site.data.keyword.apiconnect_full}}, qui facilite leur gestion et leur publication. 
{: shortdesc}

Avant de commencer, assurez-vous que votre fichier d'API REST est
conforme à la version 2.0 de la spécification Swagger. Le format du fichier peut être JSON ou YAML.

Vous pouvez utiliser IBM Integration Bus pour créer des API REST, qui
sont des applications spécialisées pouvant servir à exposer des intégrations en tant que service Web RESTful et
qui peuvent être appelées par des clients HTTP. Après avoir créé les API, vous pouvez les importer dans
{{site.data.keyword.apiconnect_short}} pour les gérer et les publier.

La liste suivante décrit quelques avantages liés à la gestion des API dans
{{site.data.keyword.apiconnect_short}} :
* Vous pouvez surveiller le nombre d'appels vers votre API.
* Vous pouvez contrôler le nombre d'appels vers votre API.
* Vous pouvez gérer plusieurs versions d'une API.

Si vous souhaitez connaître plus d'avantages, voir [Gestion des API](/docs/services/apiconnect?topic=apiconnect-managing_apis).

Pour créer une API REST dans IBM Integration Bus et l'importer
dans {{site.data.keyword.apiconnect_short}}, procédez
comme suit :
1. Créez l'API REST à l'aide d'IBM Integration Bus. Restriction : Vous ne pouvez créer une API REST qu'avec IBM Integration Toolkit, fourni avec la version installée d'IBM Integration Bus.
	1. Créez l'API REST à l'aide d'IBM Integration
		Toolkit. Pour plus d'informations sur les tâches permettant de créer une API REST à l'aide d'IBM Integration Bus, voir [Developing integration solutions by using REST APIs ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/SSMKHH_10.0.0/com.ibm.etools.mft.doc/bi12016_.htm){: #new_window} dans l'IBM Knowledge Center.
		
	2. Ouvrez l'assistant Création d'une API REST en sélectionnant **Fichier** > **Nouveau** > **API REST**.
		
	3. Indiquez un nom pour l'API REST. Le nom que vous spécifiez est employé
comme le nom du projet dans IBM Integration Toolkit.
		
	4. Sélectionnez l'une des méthodes suivantes pour créer l'API REST, et
procédez comme suit :
		
	**A partir de rien, en utilisant l'éditeur d'API REST fourni avec IBM Integration Toolkit** :
		1. Sélectionnez **Créez une API REST et définissez vous-même des
ressources et des opérations **.
		2. Cliquez sur **Terminer**. L'éditeur d'API REST de la
nouvelle API REST s'ouvre automatiquement et vous devez l'utiliser pour définir
des ressources, des modèles et des opérations.
		
	**A partir d'un document Swagger 2.0 existant** :
		1. Sélectionnez **Importer les ressources et opérations définies
dans un document Swagger** et cliquez sur
**Suivant**.
		2. Sélectionnez le chemin du document Swagger qui décrit les ressources et
les opérations que vous souhaitez dans l'API REST. Vous pouvez importer le
document Swagger à partir du système de fichiers ou d'un projet existant
dans l'espace de travail. Le fichier est validé en vue d'une utilisation dans
une API REST. Si des erreurs sont détectées au cours de la validation du
document Swagger sélectionné, elles s'affichent au début de l'assistant. Vous
ne pouvez pas poursuivre si des erreurs de validation sont détectées dans le
document Swagger sélectionné.
		3. Sélectionnez **Terminer** pour créer l'API.
	5. Implémentez les flux secondaires de votre API REST, qui sont les
opérations REST que vous souhaitez inclure.
2. Ajoutez le projet d'API REST dans un fichier d'archive de courtier (BAR) existant d'IBM Integration Bus.
3. Déployez le fichier BAR dans IBM Integration Bus on Cloud.
	1. Connectez-vous à IBM Integration Bus on Cloud avec votre IBMid, si vous ne l'êtes pas déjà. Inscrivez-vous afin d'obtenir un compte si vous n'en disposez pas déjà.
	2. Cliquez sur **Ajouter une intégration** > **Transférer le fichier BAR**.
	3. Sélectionnez le fichier BAR que vous avez créé pour votre projet d'API
REST. Conseil : Pour connaître l'emplacement du fichier BAR, cliquez dessus avec le bouton droit de la souris dans IBM Integration Toolkit afin d'afficher ses propriétés.
	4. Sélectionnez **Sauvegarder**.
	5. Sélectionnez **Actualiser** pour mettre l'écran à jour.
	6. Vérifiez que le fichier BAR a été transféré avec succès en affichant le flux d'intégration de l'API dans la fenêtre *Intégrations* d'IBM Integration Bus on Cloud.
4. Démarrez le flux d'intégration en sélectionnant l'icône de démarrage ![Capture d'écran illustrant l'icône de démarrage](images/a_play_button.jpg " "). L'API démarre et affiche le statut `En cours de fonctionnement`.
5. Sélectionnez l'intégration dans la liste des intégrations pour afficher
les informations associées. L'arborescence du menu Sommaire affiche l'API REST et les flux
secondaires qui lui sont associés. Vous pouvez également afficher les
informations des autres sections. Dans la section Noeuds finaux publics, vous
pouvez afficher l'URL publique qu'IBM
Integration Bus on Cloud a affectée à votre flux d'intégration. Sélectionnez
**Afficher l'URL complète** pour visualiser l'URL complète
de cette opération.
6. Copiez l'URL complète de l'opération dans votre presse-papiers. Vous en aurez besoin lorsque vous configurerez l'API en vue de son
fonctionnement avec {{site.data.keyword.apiconnect_short}}. Si
vous avez activé l'authentification de base, notez également le nom
d'utilisateur et le mot de passe affectés.

### Intégrez l'API IBM Integration Bus à API Connect.
{: #integrateiibapic_importing_apis}

1. Importez le fichier Swagger associé au projet d'API REST dans IBM Integration Toolkit dans le service {{site.data.keyword.apiconnect_short}}. 
	1. Connectez-vous à votre service {{site.data.keyword.apiconnect_short}} {{site.data.keyword.Bluemix_notm}}.
	2. Dans le panneau de navigation de l'interface utilisateur du gestionnaire d'API, sélectionnez **Brouillons** > **API**. L'onglet API s'ouvre.
	3. Sélectionnez **+ Ajouter** > **Importer l'API à partir d'un fichier ou d'une URL**. La fenêtre *Importer OpenAPI (Swagger)*
s'ouvre.
	4. Pour transférer le fichier que vous avez créé à partir de votre système de fichiers local, sélectionnez **Sélectionner un fichier**, puis sélectionnez le fichier que vous avez créé avec IBM Integration Bus. Les fichiers dotés des extensions `.json`,
`.yml` et `.yaml` sont pris en
charge s'ils contiennent une définition Swagger valide. Assurez-vous que l'option for **Ajouter un produit**
est sélectionnée. Vous pouvez, si vous le souhaitez, publier le produit en
sélectionnant **Publier ce produit dans un catalogue**.
	5. Cliquez sur
**Importer**. Une nouvelle définition d'API REST est créée, ainsi que les chemins d'accès et les opérations HTTP. Conseil : Si l'importation dure plus d'une minute, annulez
l'importation, actualisez le navigateur et relancez l'importation. Votre
session a peut-être expiré.
2. Associez l'API importée dans {{site.data.keyword.apiconnect_short}} à l'API d'IBM Integration Bus on Cloud.
	1. Accédez au tableau de bord d'{{site.data.keyword.apiconnect_short}}.
	2. Sélectionnez **Brouillons** > **API**.
	3. Cliquez sur l'API REST que vous avez importée.
	4. Sélectionnez l'onglet Assembler, puis **Créer un
assemblage** pour ajouter la stratégie de proxy.
	5. Faites glisser la stratégie **Proxy** vers la nouvelle
stratégie vide afin de l'activer.
	6. Collez l'URL de votre API que vous avez copiée à partir de la section des noeuds finaux publics d'IBM Integration Bus on Cloud.
	7. Si vous avez activé l'authentification de base de votre API REST, entrez le nom d'utilisateur et le mot de passe générés dans IBM Integration Bus on Cloud.
	8. Sauvegardez les paramètres de l'API.
3. Testez l'API.
	1. Dans l'onglet Assembler de l'API, cliquez sur le bouton Test ![Bouton Test](images/a_play_button.jpg "Capture d'écran illustrant l'icône du bouton Test.").
	2. Sélectionnez **Republier le produit**.
	3. Sélectionnez l'Opération.
	4. Entrez les paramètres obligatoires.
	5. Sélectionnez **Appeler**.
	6. Vérifiez que vous recevez la réponse attendue en provenance de l'API. 
	
Une fois la définition d'API importée et intégrée, vous pouvez gérer et
gouverner les API comme vous le feriez pour n'importe quelle autre définition
d'API REST. Pour plus d'informations sur les API, voir [Gestion des API](/docs/services/apiconnect?topic=apiconnect-managing_apis).

## Publication des API créées avec IBM App Connect Professional dans IBM API Connect
{: #publish_importing_apis}

Ce tutoriel explique comment publier et gérer les API REST que vous créez à l'aide d'IBM App Connect Professional avec {{site.data.keyword.apiconnect_full}}.

### Prérequis
{: #prereq_pub_api_appconn_importing_apis}

Vous devez disposer de comptes valides pour IBM App Connect Professional on Cloud et pour {{site.data.keyword.apiconnect_short}} pour mener à bien ce tutoriel. Vérifiez
que votre fichier d'API REST est conforme à la version 2.0 de la spécification Swagger. Le format du fichier peut être JSON ou YAML.

Vous pouvez utiliser IBM App Connect Professional pour créer des API REST, qui sont des applications spécialisées pouvant servir à exposer des intégrations en tant que service Web RESTful et qui peuvent être appelées par des clients HTTP. Après avoir créé les API, vous pouvez les publier et les gérer à l'aide d'{{site.data.keyword.apiconnect_short}}.
La liste suivante décrit quelques avantages liés à la gestion des API dans
{{site.data.keyword.apiconnect_short}} :

- Vous pouvez surveiller le nombre d'appels vers votre API.
- Vous pouvez contrôler le nombre d'appels vers votre API.
- Vous pouvez gérer plusieurs versions d'une API.

Si vous souhaitez connaître plus d'avantages, voir [Gestion des API](/docs/services/apiconnect?topic=apiconnect-managing_apis).
Pour créer une API REST dans IBM App Connect Professional et la publier dans {{site.data.keyword.apiconnect_short}}, procédez comme suit :

1. Créez l'API REST à l'aide d'IBM App Connect Professional.
  - Connectez-vous à la [console
de gestion Web d'App Connect Professional ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud/app-connect){:new_window} avec votre IBMid. Pour plus d'informations sur les tâches permettant de créer une API REST avec la console de gestion Web d'IBM App Connect Professional, voir [About management console settings ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/SS3LC4_7.5.2.0/com.ibm.wci.appliance.doc/About_the_WMC/consoleSettings.html){:new_window} dans l'IBM Knowledge Center.
  - Sélectionnez l'onglet Production, s'il ne l'est pas déjà.
  - Sélectionnez **Référentiel** > **Configurations** dans le panneau de navigation.
  - Sur l'écran Project Configurations, sélectionnez le projet que vous publiez vers {{site.data.keyword.apiconnect_short}}.  Les détails de la configuration du projet en cours de publication
s'affichent.
  - Sélectionnez **Push to API Management**. 
      **Conseil** : Le bouton **Push to API Management** est actif uniquement lorsque le projet que vous importez a l'un des statuts suivants : cours d'exécution ou déployé. Cliquez sur le bouton de lecture pour démarrer le projet,
si le lien ne s'affiche pas.
  - Sur l'écran Push to API Management, entrez les informations suivantes afin de créer
une connexion au système de gestion des API.

  <table><caption>Tableau 1. Informations de connexion pour la publication des API dans {{site.data.keyword.apiconnect_short}}</caption>
  <thead>
  <tr>
  <th>Nom de zone</th>
  <th>Description</th>
  </tr>
  </thead>
  <tbody>
  <tr><td>Host</td>
  <td>Indique le nom d'hôte correspondant à l'adresse du cluster, du serveur ou du cloud de gestion. Pour {{site.data.keyword.Bluemix_notm}}, cette entrée est généralement us.apiconnect.ibmcloud.com.</td>
  </tr>
  <tr>
  <td>Port</td>
  <td>Indique le numéro de port nécessaire à la connexion à l'adresse du cluster, du serveur, du cloud de gestion.</td>
  </tr>
  <tr><td>User ID</td>
  <td>Indique le nom d'utilisateur d'authentification employé pour accéder à l'adresse du cluster, du serveur ou du cloud de gestion. Il s'agit généralement de votre IBMid, que vous utilisez pour vous connecter à {{site.data.keyword.Bluemix_notm}}.</td>
  </tr>
  <tr><td>Password</td>
  <td>Indique le mot de passe d'authentification utilisé pour accéder à l'adresse
du cluster, du serveur ou du cloud de gestion. Il s'agit généralement du mot de passe associé à votre IBMid, que vous utilisez pour vous connecter à
  {{site.data.keyword.Bluemix_notm}}.</td>
  </tr>
  </tbody>
  </table>

2. Sélectionnez **Load Organizations** pour alimenter la liste des
organisations associées à votre ID et votre mot de passe.

3. Sélectionnez **Organizations** pour associer le projet à l'une
des organisations disponibles.

4. Sélectionnez **Push to APIM**, puis **Ok**.

5. Sélectionnez **Fermer** pour fermer la fenêtre.
Un nouvel onglet de navigateur s'ouvre dans votre navigateur par défaut et affiche votre API.

Associez l'API IBM App Connect à {{site.data.keyword.apiconnect_short}}.

#### Importation de la définition d'API Swagger
{: #import_sw_importing_apis}

Pour importer dans le service {{site.data.keyword.apiconnect_short}} le fichier Swagger associé au projet d'API REST dans IBM App Connect, procédez comme suit :

1. Connectez-vous à votre service {{site.data.keyword.apiconnect_short}} {{site.data.keyword.Bluemix_notm}}.

1.  Dans la barre de titre de l'interface utilisateur du gestionnaire d'API, sélectionnez **Accéder à** > **Brouillons**.

2. Sélectionnez **API** dans la barre de menus.
L'onglet API s'ouvre.

3. Sélectionnez l'API que vous avez importée pour ouvrir API Designer.

4. Sélectionnez **Assembler** dans la fenêtre de navigation.
La liste des stratégies s'affiche dans la fenêtre de navigation.

5. Sélectionnez **Créer un assemblage**, si nécessaire.

6. Ajoutez la stratégie **Invoke** en la faisant glisser vers
votre assemblage dans la fenêtre principale.

7. Sélectionnez la stratégie **Invoke** dans la fenêtre
principale pour modifier ses paramètres de configuration.

8. Configurez l'hôte/le chemin de base de la zone d'URL avec les informations
suivantes :

- **hostname** : Paramètre qui dépend de votre instance cloud. Pour plus d'informations sur ce paramètre, voir
[IBM App Connect Professional ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SS3LC4_7.5.2.0/mapfiles/ic_home.html){:new_window}.

- **basepath** : Chemin que vous indiquez dans la note httpReceive Request dans l'orchestration App Connect Professional.

9. Ajoutez et sauvegardez votre IBMid (nom d'utilisateur et mot de passe) dans les
détails d'authentification Http Basic que vous utilisez pour App Connect Professional.

#### Test de l'API
{: #test_importing_apis}

Pour tester l'API, procédez comme suit :

1. Dans l'onglet Assembler de l'API, cliquez sur le bouton Test <img alt="Capture d'écran illustrant l'icône du bouton Test" src="images/a_play_button.jpg" />.
2. Sélectionnez **Republier le produit**.
3. Sélectionnez l'Opération.
4.  Entrez les paramètres obligatoires.
5. Sélectionnez **Appeler**.
6. Vérifiez que vous recevez la réponse attendue en provenance de l'API.

Une fois la définition d'API importée et intégrée, vous pouvez gérer et gouverner
les API comme vous le feriez pour n'importe quelle autre définition d'API REST. Pour plus d'informations sur les API, voir [Gestion des API](/docs/services/apiconnect?topic=apiconnect-managing_apis).


