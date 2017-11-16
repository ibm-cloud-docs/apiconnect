---

copyright:
  years: 2017
lastupdated: "2017-09-26"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Création d'API
{: #creating_apis}

Vous pouvez créer des API en téléchargeant le kit d'outils de développement et en utilisant l'interface de ligne de commande (CLI) ou le concepteur d'API.

## Interface de ligne de commande du kit d'outils de développement
{: #dev_tk_cli notoc}

Le kit d'outils de développement fournit une interface de ligne de commande que vous pouvez utiliser pour publier des API sur {{site.data.keyword.apiconnect_long}}.
Vous publiez des API en les plaçant dans un produit, puis en publiant
le produit. Vous définissez des API et des produits en créant et validant
des fichiers de définition YAML dans votre système de fichiers local. Ensuite,
vous pouvez interagir avec
{{site.data.keyword.apiconnect_long}} en
utilisant les commandes du kit d'outils.

## Concepteur d'API
{: #designer notoc}

Le concepteur d'API est une interface graphique autonome qui figure dans le kit d'outils de développement et qui fournit des fonctions de création et de configuration d'API.
Le concepteur d'API est exécuté à l'aide de la commande edit à partir de l'interface de ligne de commande. Lorsque la commande edit est utilisée, le concepteur d'API s'ouvre dans votre navigateur par défaut ou est accessible via le port d'hôte local qui est affiché lorsque vous exécutez la commande.

## Installation du kit d'outils de développement
{: #install_dev_tk}

### Prérequis
{: #prereq_install_dev_tk}

Avant de commencer, vous devez installer [Node.js ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://nodejs.org/en/){:new_window} sur la machine où
vous prévoyez d'utiliser le kit d'outils. Assurez-vous également que `node` se trouve dans votre `PATH`.

Les éléments suivants sont installés lors de l'installation du kit d'outils de développement :

- Outil de ligne de commande d'{{site.data.keyword.apiconnect_short}}
- Editeur graphique d'{{site.data.keyword.apiconnect_short}}
- {{site.data.keyword.apiconnect_short}} Micro-gateway (en local)


1. Pour installer le kit d'outils, ouvrez votre invite de commande en tant qu'administrateur et tapez la commande suivante :

    ```
    npm install -g apiconnect
    ```
    {: codeblock}

    **Remarque :** Lors de l'installation, il est possible que des erreurs du module `node-gyp` s'affichent. Elles sont dues à une dépendance optionnelle qui ne gêne en rien la réussite de l'installation.

2. Pour afficher l'aide récapitulative relative à l'utilisation de toutes les
commandes du kit d'outils, entrez la commande suivante :

    ```
    apic
    ```
	{: codeblock}

3. Pour afficher l'aide sur la syntaxe d'une commande, utilisez l'option `--help`.
    Par exemple :

    ```
    apic validate --help
    ```
	{: codeblock}
	
## Installation des connecteurs LoopBack
{: #install_lb_conn}

Avant de pouvoir utiliser
une source de données LoopBack pour accéder aux données d'un système d'arrière-plan tel
qu'une base de données, vous devez installer le connecteur de
source de données. Les connecteurs de messagerie (e-mail) et les
connecteurs en mémoire sont intégrés à LoopBack, par conséquent, il n'est pas nécessaire
de les installer.

### Prérequis
{: #prereq_install_lb_conn}

Les connecteurs Oracle, DB2 et SQLLite requièrent des outils de compilation C pour
générer et installer les extensions binaires. Les besoins exacts dépendent de votre système d'exploitation, comme le décrit
le tableau suivant.

<table summary="" id="apic_028__table_pre_reqs" class="defaultstyle style-scope doc-content">
<caption>Tableau 1. Conditions requises pour l'installation sous différents systèmes d'exploitation</caption>
<thead>
<tr>
<th style="width: 33.3%" id="th_d70e208" class="thleft style-scope doc-content">Windows</th>
<th style="width: 33.3%" id="th_d70e210" class="thleft style-scope doc-content">Linux</th>
<th style="width: 33.3%" id="th_d70e212" class="thleft style-scope doc-content">MAC OS X</th>
</tr>
</thead>
<tbody >
<tr class="style-scope doc-content doc-tr-odd">
<td style="width: 33.3%" > [Microsoft .NET Framework 4 ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.microsoft.com/en-us/download/details.aspx?id=17851) <a href="https://www.microsoft.com/en-us/download/details.aspx?id=17851" rel="external" target="blank" title="(s'ouvre dans un nouvel onglet ou une nouvelle fenêtre)" >Microsoft .NET Framework 4</a></td>
<td style="width: 33.3%">Python v2.7 (v3.x non prise en charge)</td>
<td style="width: 33.3%" > [Python Releases for Mac OS X ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.python.org/downloads/mac-osx/) <a href="https://www.python.org/downloads/mac-osx/" rel="external" target="blank" title="(s'ouvre dans un nouvel onglet ou une nouvelle fenêtre)" >Python
Releases for Mac OS X</a></td>
</tr>
<tr><td style="width: 33.3%" > [Visual Studio ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.visualstudio.com/downloads/download-visual-studio-vs) <a href="https://www.visualstudio.com/downloads/download-visual-studio-vs" rel="external" target="blank" title="(s'ouvre dans un nouvel onglet ou une nouvelle fenêtre)" >Visual Studio</a></td>
<td style="width: 33.3%">
<code>make</code>
</td>
<td style="width: 33.3%" > [Xcode ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://developer.apple.com/xcode/?cm_mc_uid=46449280653414622613810&amp;cm_mc_sid_50200000=1459433716) <a href="https://developer.apple.com/xcode/?cm_mc_uid=46449280653414622613810&amp;cm_mc_sid_50200000=1459433716" rel="external" target="blank" title="(s'ouvre dans un nouvel onglet ou une nouvelle fenêtre)" >Xcode</a></td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 33.3%" > [Python v2.7.10 ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.python.org/downloads/release/python-2710/) <a href="https://www.python.org/downloads/release/python-2710/" rel="external" target="blank" title="(s'ouvre dans un nouvel onglet ou une nouvelle fenêtre)" >Python v2.7.10</a></td>
<td style="width: 33.3%">Une chaîne d'outils de compilateur C/C++, par exemple, GCC version 4.2 ou ultérieure. </td>
<td style="width: 33.3%" >&nbsp;</td>
</tr>
<tr><td style="width: 33.3%" > [Microsoft Windows SDK for Windows 7 ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.microsoft.com/en-gb/download/details.aspx?id=8279) <a href="https://www.microsoft.com/en-gb/download/details.aspx?id=8279" rel="external" target="blank" title="(s'ouvre dans un nouvel onglet ou une nouvelle fenêtre)">Microsoft Windows SDK for Windows 7</a></td>
<td style="width: 33.3%">Sur les distributions Debian et dérivées (Ubuntu, Mint, etc.),
utilisez la commande suivante :
<pre class="codeblock style-scope doc-content"><code>apt-get install build-essential</code></pre>
</td>
<td style="width: 33.3%" >&nbsp;</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 33.3%" >npm version 3. Voir Remarque.</td>
<td style="width: 33.3%">&nbsp;</td>
<td style="width: 33.3%" >&nbsp;</td>
</tr>
</tbody>
</table>

**Remarque :** Pour les installations Windows :

- Utilisez Visual Studio Community sauf si vous souhaitez acheter Visual Studio Enterprise. Exécutez
le programme d'installation, cochez "Visual C++" sous "Langages de programmation" et
acceptez l'emplacement d'installation par défaut.

- Pour les compilations 64 bits de Node.js et des modules natifs, il vous faut également le SDK pour Windows&trade; 7 64 bits. Si l'installation échoue, essayez de désinstaller l'éventuel
package C++ 2010
x64&amp;x86 Redistributable que vous avez installé en premier. Si vous obtenez des erreurs signalant que
les compilateurs 64 bits ne sont pas installés, c'est peut-être parce qu'il vous faut aussi la mise à jour du compilateur pour Windows&trade; SDK 7.1.
- Entrez la commande suivante pour installer npm version 3 :
  ```
  npm install -g npm
  ```
  {: codeblock}
  Vérifiez ensuite que la commande npm
utilise la version correcte :
  ```
  npm -v
  ```
  {: codeblock}
  Si la version affichée n'est pas la
3.x.x, éditez votre variable système PATH
de sorte que `C:\Users\username\AppData\Roaming\npm` prenne le pas sur toute autre
entrée.


1. **Facultatif** :
Si vous utilisez le concepteur d'API, ouvrez une nouvelle fenêtre d'interpréteur de commande.

2. Une fois que vous avez installé les outils de compilation requis par votre système d'exploitation,
installez le connecteur en utilisant la commande suivante dans le répertoire racine du projet.

```
npm install --save <connector-package>
```
{: codeblock}
où `<connector-package>` est le nom du package npm pour le connecteur LoopBack, comme indiqué dans le tableau.

<table summary="" id="apic_connectors_table_pre_reqs" class="defaultstyle style-scope doc-content">
<caption>Tableau 3. Connecteurs LoopBack</caption>
<thead>
<tr class="style-scope doc-content doc-tr-even">
<th style="width: 50%" id="th_new_d70e1489" class="thleft style-scope doc-content">Source de données</th>
<th style="width: 50%" id="th_new_d70e1491" class="thleft style-scope doc-content">Package de connecteurs</th>
</tr>
</thead>
<tbody>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Cloudant</td>
<td style="width: 50%">loopback-connector-cloudant</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">DashDB</td>
<td style="width: 50%">loopback-connector-dashdb</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">DB2</td>
<td style="width: 50%">loopback-connector-db2</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">DB2 for zOS</td>
<td style="width: 50%">loopback-connector-db2z</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Microsoft SQL Server</td>
<td style="width: 50%">loopback-connector-mssql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">MongoDB</td>
<td style="width: 50%">loopback-connector-mongodb</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">MySQL</td>
<td style="width: 50%">loopback-connector-mysql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">Oracle</td>
<td style="width: 50%">loopback-connector-oracle</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">PostgreSQL</td>
<td style="width: 50%">loopback-connector-postgresql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">Services Web SOAP</td>
<td style="width: 50%">loopback-connector-soap</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Services web REST</td>
<td style="width: 50%">loopback-connector-rest</td>
</tr>
</tbody>
</table>

## Création d'une API LoopBack à l'aide de l'interface de ligne de commande
{: #create_lb_api}

La procédure ci-après explique comment créer une API LoopBack&reg; à l'aide de l'interface de ligne de commande.


### Prérequis
{: #prereq_create_lb_api}

Avant de commencer, procurez-vous l'identificateur du catalogue que vous souhaitez utiliser. Pour l'obtenir, effectuez les étapes suivantes :  

1. Accédez au **tableau de bord** d'{{site.data.keyword.apiconnect_short}}.

2. Pour le catalogue que vous souhaitez utiliser, cliquez sur l'icône **Afficher l'identificateur du catalogue**
<img alt="icône de chaîne pour afficher l'identificateur du catalogue" src="images/chain_link_icon.png">.

3. Copiez l'identificateur du catalogue. Par exemple :  
  ```
  apic config:set catalog=apic-catalog://<region>.apiconnect.ibmcloud.com/orgs/<username_string>-dev/catalogs/<catalog>
  ```
  {: codeblock}
    où :

    - `<region>` est la région {{site.data.keyword.Bluemix_short}}.

    - `<username_string>` est l'ID d'organisation {{site.data.keyword.Bluemix_short}}, sans aucun symbole. Par exemple,
`joe@mycompany.com` deviendrait `joemycompanycom`

    - `<catalog>` est le nom du catalogue  

Pour créer une API LoopBack à l'aide de l'interface de ligne de commande, procédez comme suit :

1. Pour créer un projet, ouvrez une ligne de commande et entrez ce qui suit :
  ```
  apic loopback
  ```
  {: codeblock}

2. Dans l'invite qui s'affiche ensuite, le système vous demande de spécifier un nom pour votre application. Tapez un nom et appuyez sur **Entrée**.
  ```
  ? Quel est le nom de votre application ? (<nom_application>)
  ```
    
    L'outil vous invite à entrer le nom du répertoire dans lequel vous souhaitez créer le projet.
    ```
    ? Entrez le nom du répertoire destiné à contenir le projet : (<nom_répertoire_projet>)
    ```
    
3. Appuyez
sur **Entrée** pour utiliser le nom que vous avez précédemment entré
ou entrez un nouveau nom, puis appuyez sur **Entrée**. L'outil vous invite à sélectionner le type d'application à créer :
```
? Quel type d'application avez-vous en tête ? (Utiliser les touches fléchées)
  empty-server (API LoopBack vide, sans aucun modèle ou source de données configuré(e))
> hello-world (Projet contenant un exemple de base, incluant une base de données de mémoire)
```

4. Sélectionnez l'application que vous souhaitez utiliser et appuyez sur **Entrée**.
L'outil affiche un certain nombre de messages à mesure qu'il crée le répertoire du projet et y ajoute
des répertoires et des fichiers. Il exécute également `npm install` pour
installer toutes les dépendances du projet, telles que spécifiées dans `package.json`.
Ce processus peut prendre un certain temps.

5. Avant de créer un modèle, vous devez vous assurer que votre répertoire de travail en cours est le
répertoire de niveau supérieur du projet. Pour ce faire, entrez la commande suivante :
    ```
    cd <project directory name>
    ```
    {: codeblock}

6. Pour créer un modèle, tapez la commande suivante :
    ```
    apic create --type model
    ```
    {: codeblock}

    L'outil vous invite à entrer le nom du modèle.

    ```
    ? Entrer le nom du modèle :
    ```

7. Entrez un nom pour le modèle.
    En général, vous pouvez utiliser tous les caractères
alphanumériques, ainsi que les tirets et les traits de soulignement, dans un nom de
modèle.
    Toutes les sources de données que vous avez ajoutées au projet sont répertoriées et l'outil vous invite à sélectionner une source de données à utiliser :
    ```
    ? Sélectionner la source de données à laquelle associer l'élément : (Utiliser les touches fléchées)
    ```

8. Sélectionnez la source de données que vous souhaitez utiliser et appuyez sur **Entrée**. L'outil vous invite à sélectionner la classe de base du modèle :
    ```
    ? Select model's base class (Use arrow keys)
       Model
    < PersistedModel
      ACL
      AccessToken
      Application
      Change
      Checkpoint
    (Move up and down to reveal more choices)
    ```
    Pour plus d'informations sur chaque option, voir [Utilisation de modèles intégrés ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://loopback.io/doc/en/lb3/Using-built-in-models.html){:new_window}.

9. Sélectionnez une classe de base et appuyez sur **Entrée**. L'outil vous demande si vous souhaitez présenter l'API REST du modèle.
```
? Exposer branch via l'API REST ? (O/n)
```
Si le modèle est exposé via REST, toutes les opérations standard create, read, update et delete sont disponibles via des noeuds finaux REST.

10. Entrez votre sélection et appuyez sur **Entrée**.
Si vous choisissez d'exposer le modèle sur REST, l'outil vous invite à utiliser le pluriel pour le nom de modèle.
```
? Forme plurielle personnalisée (utilisée pour générer l'URL REST) :
```

11. Appuyez sur **Entrée** pour utiliser les règles de mise au pluriel par défaut de la langue anglaise.
L'outil vous demande si vous souhaitez créer un modèle serveur uniquement ou un
modèle commun qui puisse être utilisé dans l'API LoopBack&reg;
serveur ou client.
```
? Modèle commun ou serveur uniquement ? (Utiliser les touches fléchées)
```

12. Utilisez les touches de déplacement du curseur pour effectuer votre sélection et appuyez sur **Entrée**.
L'outil vous invite à ajouter les propriétés du modèle :
```
Ajoutez maintenant des propriétés branch.
Entrer un nom de propriété vide une fois que vous avez terminé.
? Nom de la propriété :
```

13. Entrez un nom de propriété.
L'outil vous invite à sélectionner le type de données de la propriété :
```
? Property type: (Use arrow keys)
> string
  number
  boolean
  object
  array
  date
  buffer
```

14. Sélectionnez le type de chaîne et appuyez sur **Entrée**.
L'outil vous demande si la propriété est obligatoire :
```
? Obligatoire ? (o/N)
```

15. Tapez `o` ou `n` et appuyez sur **Entrée**.
L'outil vous invite à ajouter une autre propriété :
```
Ajoutez une autre propriété branch.
Entrer un nom de propriété vide une fois que vous avez terminé.
? Nom de la propriété :
```

16. Si besoin, ajoutez un autre nom de propriété. Si vous n'avez pas besoin d'autres propriétés, appuyez sur **Entrée** pour finir d'ajouter le modèle.

Par défaut, un projet LoopBack&reg; est préconfiguré avec une source de données en mémoire, qui convient au développement et aux tests. Cependant, à un moment donné, vous souhaiterez connecter vos modèles à une source de données réelle, telle qu'un serveur de base de données. Pour ajouter une source de données, procédez comme suit :

1. Entrez la commande suivante :
```
apic create --type datasource
```
{: codeblock}
L'outil vous invite à entrer le nom de la source de données.
```
? Entrer le nom de la source de données :
```

2. Entrez un nom pour la source de données.  Dans un nom de source de données, vous pouvez utiliser tous les caractères alphanumériques, ainsi que les tirets et les traits de
soulignement. L'outil vous invite à sélectionner le connecteur à utiliser pour la source de données :
```
? Select the connector for myds: (Use arrow keys)
> In-memory db (supported by StrongLoop)
  Email (supported by StrongLoop)
  MySQL (supported by StrongLoop)
  PostgreSQL (supported by StrongLoop)
  Oracle (supported by StrongLoop)
  Microsoft SQL (supported by StrongLoop)
  MongoDB (supported by StrongLoop)
(Move up and down to reveal more choices)
```

3. Utilisez les touches de déplacement du curseur pour sélectionner le connecteur que vous voulez utiliser et appuyez sur **Entrée**.
L'outil ajoute la source de données au projet.

4. Entrez vos données d'identification d'hôte, de port, d'utilisateur, de mot de passe et de base de données.
L'outil vous invite à installer le connecteur LoopBack&reg;.
```
Install loopback-connector-<connector>?
```

5. Tapez `Oui`.
L'outil installe le connecteur.

Si vous avez sélectionné le connecteur Oracle, vous devez définir une variable d'environnement dans
{{site.data.keyword.Bluemix_short}} pour que l'application Oracle puisse démarrer. Pour ce faire, effectuez les étapes suivantes :

1. Dans l'interface utilisateur
{{site.data.keyword.Bluemix_short}}, sélectionnez
**Calcul**.

2. Dans Applications CF, choisissez les applications avec lesquelles vous souhaitez
travailler.

3. Cliquez sur **Exécution**.

4. Sélectionnez **Variables d'environnement**.

5. Dans la section Défini par l'utilisateur, cliquez sur **Ajouter**.

6. Dans le champ **Nom**, entrez `LD_LIBRARY_PATH`.

7. Dans le champ **Valeur**, entrez
`$LD_LIBRARY_PATH:/home/vcap/app/node_modules/instantclient`.

8. Cliquez sur **Sauvegarder**.

### Test d'un projet LoopBack
{: #test_lb_proj}

Pour tester un projet LoopBack&reg;, procédez comme indiqué ci-après.

1. **Facultatif** : Assurez-vous que votre répertoire de travail en cours est le répertoire de niveau supérieur du projet. Entrez la commande suivante :
```
cd <loopback-project-dir>
```
où `<loopback-project-dir>` est le nom du répertoire qui contient le projet.
2. Entrez la commande suivante :
```
apic start
```
Cette commande exécute le projet LoopBack&reg; (API) et Micro Gateway en local. Les messages suivants s'affichent :
```
En attente de loopback-project pour terminer le déploiement.
En attente de loopback-project-gw pour terminer le déploiement.
Service loopback-project (id 1) démarré sur le port 4001
Service loopback-project-gw (id 2) démarré sur le port 4002
```
où : `<loopback-project>` est le nom du répertoire qui
contient le projet.

Vous pouvez maintenant tester n'importe lequel des points finaux d'API à l'aide de `curl`, par exemple.
si vous souhaitez charger l'API à l'aide d'un navigateur Web, ouvrez `http://localhost:4001` dans votre navigateur. Pour le projet LoopBack&reg; par défaut (vide ou hello-world), un message semblable au suivant s'affiche :
```
{"started":"2016-03-07T22:24:55.322Z","uptime":35.839}
```

### Publication d'une application LoopBack sur Bluemix à partir de l'interface de ligne de commande
{: #pub_lb_app_cli}

Pour publier une application LoopBack sur {{site.data.keyword.Bluemix_short}} à partir de la ligne de commande, procédez comme suit :

1. Entrez la commande suivante pour vérifier que vous vous trouvez bien dans le répertoire du projet LoopBack :
```
cd <loopback-project-dir>
```
2. Entrez la commande suivante pour vous connecter à {{site.data.keyword.apiconnect_short}} et {{site.data.keyword.Bluemix_short}}.
```
apic login --server  <region>.apiconnect.ibmcloud.com -u <username> -p <password>
```
où :
  * `<username>` est l'ID d'organisation {{site.data.keyword.apiconnect_short}}.
  * `<password>` est le mot de passe {{site.data.keyword.apiconnect_short}}.
3. Appuyez sur la barre d'espacement pour ouvrir automatiquement la page du navigateur **Code d'accès unique**.
4. Cliquez sur **Régénérer** et copiez le code d'accès unique.
5. De retour dans l'interface de ligne de commande, collez le code d'accès pour terminer votre connexion. Le message suivant s'affiche :
```
La connexion à <region>.apiconnect.ibmcloud.com a abouti
```
6. Entrez la commande suivante :
```
apic organizations -s <region>.apiconnect.ibmcloud.com
```
où :
  * `<region>` est la région {{site.data.keyword.Bluemix_short}}.Par exemple :
  * `eu`, si vous utilisez {{site.data.keyword.Bluemix_short}} London.
  * `us`, si vous utilisez {{site.data.keyword.Bluemix_short}} Dallas.
  * `au`, si vous utilisez {{site.data.keyword.Bluemix_short}} Sydney.

  En cas de doute, vous pouvez localiser votre région en cliquant sur l'icône {{site.data.keyword.avatar}} <img src="images/i-avatar-icon.svg" alt="icône d'avatar"/> dans la barre de menus pour ouvrir le widget Compte et support et vérifier la zone de région.
7. Entrez la commande suivante pour publier votre application sur {{site.data.keyword.Bluemix_short}}.
```
apic apps:publish –a <app> -o <org> -s <région>.apiconnect.ibmcloud.com
```
où :
  * `<app>` est le nom de l'application.
  * `<org>` est le nom de l'organisation {{site.data.keyword.Bluemix_short}}.
  * `<region>` est la région {{site.data.keyword.Bluemix_short}}.
La sortie suivante est renvoyée :
  ```
  ...preparing project
  ...building package for deploy
  ...uploading package
  Runtime published successfully.
  Management URL: https://new-console.stage1.ng.bluemix.net/apps/3aa7087d-b454-4e13-bbc5-8228ebe00eef
  API target urls: apiconnect-3aa7087d-b454-4e13-bbc5-8228ebe00eef.pszetousibmcom-dev.apic.stage1.mybluemix.net
  API invoke tls-profile: client:Loopback-client
  ```

8. Ensuite, vous devez modifier les définitions de produit avec les valeurs renvoyées lors de la publication. Pour ce faire, procédez comme suit :

    1. Dans l'interface utilisateur du concepteur d'API, cliquez sur **API**.
    2. Sélectionnez votre API.
    3. Cliquez sur **Assembler**.
    4. Dans l'éditeur d'assemblage, cliquez sur l'icône **Règles de filtrage**.
    5. Sélectionnez **Règles DataPower Gateway**.
    6. Cliquez deux fois sur **invoke**.
    7. Mettez à jour les zones suivantes avec les valeurs que vous avez extraites à l'étape 7.
        - **URL d'appel** : Insérez l'URL cible de l'API. Vous devez spécifier le protocole sécurisé HTTPS. Par exemple :
        ```
        https://apiconnect-33e7b062-092b-4227-af97-047499dab2e7.<org Bluemix>-<espace Bluemix>.apic.<nom de domaine>$(request.path)
        ```
        Si vous n'avez pas noté cette valeur, vous pouvez l'extraire en accédant à l'URL de gestion qui a été renvoyée à
l'étape 7. Vous pouvez également l'extraire en vous connectant à {{site.data.keyword.Bluemix_short}} et en affichant les informations sur votre application.
        - **Profil TLS** : Insérez le profil TLS d'appel d'API. Par exemple :
        ```
        client:Loopback-client
        ```
    8. Cliquez sur **Sauvegarder** pour sauvegarder l'API.

## Création d'une API LoopBack à l'aide du concepteur d'API
{: #create_lb_api_design}

La procédure ci-après explique comment créer une API LoopBack&reg; à l'aide du concepteur d'API.
{:shortdesc}

### Prérequis
{: #prereq_create_lb_api_design}

**Remarque** : Les instructions qui suivent  partent du principe que vous utilisez la dernière version du
kit d'outils de développement. Pour savoir quelle est la dernière version, voir la page du package [npm ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.npmjs.com/package/apiconnect){:new_window}.

Vous devez commencer par créer un projet LoopBack&reg; à l'aide de l'interface de ligne de commande. Pour ce faire, procédez comme suit :

1. Pour créer un projet, ouvrez une ligne de commande et entrez ce qui suit :
  ```
  apic loopback
  ```
  {: codeblock}

2. Dans l'invite qui s'affiche ensuite, le système vous demande de spécifier un nom pour votre application. Tapez un nom et appuyez sur **Entrée**.
  ```
  ? Quel est le nom de votre application ? (<nom_application>)
  ```
    
    L'outil vous invite à entrer le nom du répertoire dans lequel vous souhaitez créer le projet.
    ```
    ? Entrez le nom du répertoire destiné à contenir le projet : (<nom_répertoire_projet>)
    ```
    
3. Appuyez
sur **Entrée** pour utiliser le nom que vous avez précédemment entré
ou entrez un nouveau nom, puis appuyez sur **Entrée**. L'outil vous invite à sélectionner le type d'application à créer :
```
? Quel type d'application avez-vous en tête ? (Utiliser les touches fléchées)
  empty-server (API LoopBack vide, sans aucun modèle ou source de données configuré(e))
> hello-world (Projet contenant un exemple de base, incluant une base de données de mémoire)
```

4. Sélectionnez l'application que vous souhaitez utiliser et appuyez sur **Entrée**.
L'outil affiche un certain nombre de messages à mesure qu'il crée le répertoire du projet et y ajoute
des répertoires et des fichiers. Il exécute également `npm install` pour
installer toutes les dépendances du projet, telles que spécifiées dans `package.json`.
Ce processus peut prendre un certain temps.

5. Avant de créer un modèle, vous devez vous assurer que votre répertoire de travail en cours est le répertoire de niveau supérieur du projet. Pour ce faire, entrez la commande suivante :
```
cd <project directory name>
```

**Remarque** : En désignant votre répertoire de travail actuel comme répertoire de premier niveau du projet, vous êtes certain de disposer de l'option d'ajout de modèles et de sources de données
lorsque vous ouvrirez le concepteur d'API. Si, au contraire, vous ouvrez le concepteur d'API sans changer de répertoire,
vous ne pourrez pas ajouter de modèles ni de sources de données.

Pour ouvrir le concepteur d'API, procédez comme suit :
1. Ouvrez une ligne de commande et tapez ce qui suit :
```
apic edit
```
    Après un court moment, le message suivant s'affiche :
    ```
    Le serveur Express est à l'écoute sur http://127.0.0.1:9000
    ```
    Le concepteur d'API s'ouvre dans votre navigateur Web par défaut.

2. Sur la page de connexion, entrez vos ID et mot de passe Bluemix&reg;. Cliquez sur **Ouvrir la session**.

3. Cliquez sur **Modèles**.

4. Cliquez sur **Ajouter**. La fenêtre **Modèle** LoopBack&reg; s'ouvre.

5. Tapez un nom de modèle.
En général, vous pouvez utiliser tous les caractères
alphanumériques, ainsi que les tirets et les traits de soulignement, dans un nom de
modèle.

6. Cliquez sur **Nouveau**.

7. Sur la page de l'éditeur de modèle, accédez à Propriétés et cliquez sur **Ajouter**.

8. Tapez un nom de propriété et sélectionnez un type.

9. Lorsque vous avez terminé de saisir les propriétés du modèle, cliquez sur **Sauvegarder**.

Par défaut, aucune source de données n'est définie pour un projet LoopBack&reg; vide. Pour définir une source de données, procédez comme suit :
1. Cliquez sur **Sources de données**.

2. Cliquez sur l'icône **Ajouter**.
La fenêtre Nouveau **modèle** LoopBack&reg; s'ouvre.

3. Tapez un nom de source de données. Dans un nom de source de données, vous pouvez utiliser tous les caractères alphanumériques, ainsi que les tirets et les traits de
soulignement. 

4. Cliquez sur **Nouveau**.
La source de données apparaît dans la liste de sources de données, et l'éditeur met à jour le fichier `server/datasources.json` avec les paramètres de la nouvelle source de données.

5. Cliquez sur la source de données pour afficher ses paramètres.

6. Remplacez le connecteur par celui-ci dont vous avez besoin.

7. Revenez à la console à partir de laquelle vous avez démarré le concepteur d'API et installez le connecteur à l'aide de la commande suivante :
```
npm install --save <connector-package>
```
    où `<connector-package>` est le nom du package npm pour le connecteur LoopBack&reg; que vous avez sélectionné. Consultez le tableau ci-après pour voir la liste des packages de connecteurs.

**Remarque :** Les connecteurs de messagerie (e-mail) et les connecteurs en mémoire sont intégrés à LoopBack&reg; ; il n'est donc pas nécessaire de les installer.

<table>
<caption>Tableau 3. Connecteurs LoopBack</caption>
<thead>
<tr class="style-scope doc-content doc-tr-even">
<th style="width: 50%" id="3rd_d70e1489" class="thleft style-scope doc-content">Source de données</th>
<th style="width: 50%" id="3rd_d70e1491" class="thleft style-scope doc-content">Package de connecteurs</th>
</tr>
</thead>
<tbody>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Cloudant</td>
<td style="width: 50%">loopback-connector-cloudant</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">DashDB</td>
<td style="width: 50%">loopback-connector-dashdb</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">DB2</td>
<td style="width: 50%">loopback-connector-db2</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">DB2 for zOS</td>
<td style="width: 50%">loopback-connector-db2z</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Microsoft SQL Server</td>
<td style="width: 50%">loopback-connector-mssql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">MongoDB</td>
<td style="width: 50%">loopback-connector-mongodb</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">MySQL</td>
<td style="width: 50%">loopback-connector-mysql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">Oracle</td>
<td style="width: 50%">loopback-connector-oracle</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">PostgreSQL</td>
<td style="width: 50%">loopback-connector-postgresql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">Services Web SOAP</td>
<td style="width: 50%">loopback-connector-soap</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Services web REST</td>
<td style="width: 50%">loopback-connector-rest</td>
</tr>
</tbody>
</table>

Pour plus d'informations, voir [LoopBack Documentation - Building a connector ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://http://loopback.io//doc/en/lb3/Defining-data-sources.html){:new_window}.

**Remarque :** Si vous avez sélectionné le connecteur Oracle, vous devez définir une variable d'environnement dans
{{site.data.keyword.Bluemix_short}} pour que l'application Oracle puisse démarrer. Pour ce faire, effectuez les étapes suivantes :

1. Dans l'interface utilisateur
{{site.data.keyword.Bluemix_short}}, sélectionnez
**Calcul**.

2. Dans Applications CF, choisissez les applications avec lesquelles vous souhaitez
travailler.

3. Cliquez sur **Exécution**.

4. Sélectionnez **Variables d'environnement**.

5. Dans la section Défini par l'utilisateur, cliquez sur **Ajouter**.

6. Dans le champ **Nom**, entrez `LD_LIBRARY_PATH`.

7. Dans le champ **Valeur**, entrez
`$LD_LIBRARY_PATH:/home/vcap/app/node_modules/instantclient`.

8. Cliquez sur **Sauvegarder**.

Pour tester un projet LoopBack&reg;, procédez comme suit :
1. Cliquez sur l'icône de **démarrage des serveurs**.
Le message suivant s'affiche :
```
http://localhost:<4001/>Running
```
En fonction de la configuration de votre projet et selon que d'autres processus sont en
cours d'exécution ou non, un autre numéro de port peut être affiché.

2. Cliquez sur **localhost:4001** pour afficher le noeud final racine de l'API. Pour le projet
LoopBack&reg; par défaut (vide ou hello-world), un message
semblable au suivant s'affiche :
```
{"started":"2017-03-07T22:24:55.322Z","uptime":35.839}
```

A présent, vous devez créer un produit. Pour plus d'information, voir [Création de produits](managing_products.html#create_products).
**Conseil** : Chaque fois que vous ouvrez une nouvelle invite de commande, vérifiez que le répertoire de travail en cours
est le répertoire de niveau supérieur du projet. Pour ce faire, entrez la commande suivante :
```
cd <project directory name>
```

## Désinstallation du kit d'outils de développement
{: #uninstall_dev_tk}

### Prérequis
{: #prereq_uninstall_dev_tk}

Avant de commencer, vous devez arrêter toutes les applications qui sont en cours d'exécution localement en entrant la commande suivante :
```
apic stop --all
```

Pour désinstaller le kit d'outils de développement, procédez comme suit :

1. Entrez la commande suivante :
```
npm rm -g apiconnect
```
{: codeblock}

2. Effacez votre cache npm :
```
npm cache clean
```
{:codeblock}
  
Sous Windows :

3. Supprimez tous les fichiers dont le nom commence par `npm-` dans `C:\Users\username\AppData\Local\Temp`
4. Supprimez le répertoire `<home_dir>\.apiconnect`, où `<home_dir>` est le répertoire de base du compte utilisateur sous lequel le kit d'outils a été installé.
