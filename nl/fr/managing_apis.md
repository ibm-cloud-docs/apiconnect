---

copyright:
  years: 2017
lastupdated: "2017-10-19"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Gestion des API
{: #managing_apis}

Vous pouvez utiliser API Connect pour gérer des API dans {{site.data.keyword.Bluemix}}, qu'elles se trouvent dans {{site.data.keyword.Bluemix_notm}} ou hors de {{site.data.keyword.Bluemix_notm}}. La gestion des API vous permet de contrôler l'utilisation, d'accroître l'adoption et d'assurer le suivi des statistiques.

Si vous êtes un client, vous pouvez gérer comment une API est utilisée dans l'interface utilisateur du gestionnaire d'API une fois qu'un développeur l'a créée et qu'il a envoyé le produit à {{site.data.keyword.Bluemix_short}}. Les rubriques ci-après expliquent comment créer et gérer des produits dans le concepteur
{{site.data.keyword.apiconnect_short}}.

## Exposition d'API sur site via une passerelle sécurisée
{: #expose_apis_sec_gate}

Vous pouvez créer une passerelle sécurisée pour exposer en toute sécurité des API sur site sur {{site.data.keyword.apiconnect_full}}.

Lorsque vous créez une passerelle sécurisée, vous intégrez les fonctions du service {{site.data.keyword.Bluemix_short}}
{{site.data.keyword.SecureGateway}} à {{site.data.keyword.apiconnect_short}}. Cela signifie que vous pouvez accéder de manière sécurisée à vos API sur site à partir d'{{site.data.keyword.apiconnect_short}} via un passage sécurisé sans avoir à mettre à disposition une instance distincte du service {{site.data.keyword.SecureGateway}}. En réalité, vous créez un tunnel vers {{site.data.keyword.apiconnect_short}} dans un environnement public sans exposer vos données sur site. Il
suffit de créer la passerelle et de la lier à une API. Vous avez déjà terminé
la création d'une destination, du profil SSL et des certificats.
Pour plus d'informations sur le service
{{site.data.keyword.SecureGateway}},
voir [A
propos de {{site.data.keyword.SecureGateway}}](../../services/SecureGateway/sg_overview.html#sg_overview).
Pour créer une passerelle sécurisée, procédez comme indiqué dans la rubrique
ci-après.

### Création d'une passerelle sécurisée
{: #create_sec_gate notoc}

Lorsque vous créez une passerelle sécurisée, un ID de passerelle et
un jeton de sécurité sont créés pour vous.
Vous configurez également un client de passerelle sécurisée dans votre
environnement sur site auquel
{{site.data.keyword.apiconnect_short}}
se connectera. Une fois le client configuré, utilisez l'ID de passerelle et le
jeton de sécurité pour vous connecter au client et ainsi accéder à vos API sur
site.

Pour créer une passerelle, procédez comme suit :

1. Cliquez sur **Accéder à** <img alt="Icône Accéder à" src="images/navigate_to_icon.png"> > **Admin** > **Passerelles sécurisées**.
La page `Secure Gateways` s'affiche et
une visite guidée de Secure Gateway apparaît dans l'angle de l'interface
utilisateur.

2. **Facultatif** :
Cliquez sur chaque étape de la visite guidée pour finaliser la configuration de votre passerelle.

3. Cliquez sur **Ajouter**.
La boîte de dialogue `Créer une passerelle Secure Gateway` s'affiche.

4. Indiquez un nom pour votre passerelle.

**Remarque :** Seuls les caractères alphanumériques et les traits de soulignement sont admis.

5. Cliquez sur **Sauvegarder**.
La passerelle apparaît, ainsi que l'ID de passerelle et le jeton
de sécurité.

6. Cliquez sur **Configurer**.
Cliquer sur **Configurer** vous permet de télécharger et d'installer un client de passerelle sécurisée
sur votre poste de travail sur site afin de connecter un réseau distant à une passerelle sécurisée au sein du réseau Bluemix&reg;.

    La fenêtre `Configurer des clients Secure Gateway` s'affiche.

7. Cliquez sur le client que vous souhaitez utiliser à partir des options suivantes :

    - Programmes d'installation IBM&reg;
    - Docker
    - IBM DataPower&reg;

8. Suivez les instructions à l'écran pour installer et exécuter le client que vous avez sélectionné.

Pour plus d'informations sur la configuration d'un client de passerelle
sécurisée, voir
[Configuration
d'un client](../../services/SecureGateway/sg_021.html#sg_021).

9. Lorsque vous avez terminé l'installation du client, fermez la fenêtre **Configurer des clients Secure Gateway**.

10. Actualisez la page.

Le client est connecté. L'ID de passerelle et le statut sont affichés. Vous
avez terminé la configuration de la passerelle et avez créé une passerelle
sécurisée.
A présent, utilisez la passerelle sécurisée pour accéder à vos API
sur site.

### Utilisation de la passerelle sécurisée avec vos API
{: #using_sec_gate_apis notoc}

Une fois la passerelle configurée, vous pouvez l'utiliser avec vos API.
{:shortdesc}

Pour utiliser votre passerelle sécurisée avec des API, procédez
comme suit :
1. Créez votre API et votre produit en procédant comme indiqué dans les étapes ci-après.
  - Cliquez sur **Accéder à** <img src="images/navigate_to_icon.png" alt="Icône Accéder à" /> > **Brouillons** > **API** > **Ajouter**.
  - Sélectionnez le type d'API que vous souhaitez créer.
  - Sélectionnez ou cliquez sur **Ajouter un produit**. **IMPORTANT** : Ne publiez pas encore le produit.
  - Cliquez sur **Créer une API**.
  L'API apparaît dans la vue `Conception`.
  
2. Cliquez sur **Assembler**.

3. Cliquez sur la stratégie **Appeler** pour ouvrir la palette **Appeler**.
**RESTRICTION** : Vous ne pouvez pas utiliser de commutateurs logiques, tels `Switch`, `Operation
Switch` et `If`, avec des API qui utilisent une passerelle sécurisée.

4. Sélectionnez **Accéder à l'URL via Secure Gateway**.

5. Dans la zone URL, mettez à jour `target-url` avec le nom d'hôte et le numéro de port sur site. Par exemple,
```
target-url: http://onpremdb2.rtp.raleigh.ibm.com:3055$(request.path)$(request.search)
```

6. Cliquez sur **Sauvegarder** <img src="images/icon_save.png" alt="Icône Sauvegarder" />.

7. Cliquez sur l'onglet **Source**.  Notez que la zone `secure-gateway` a pour valeur `true`.

8. Cliquez sur **Toutes les API** > **Produits**, puis sélectionnez le produit que vous avez créé précédemment.

9. Cliquez sur l'icône **Publier** pour transférer le
produit dans un catalogue choisi.

10. Sélectionnez le catalogue que vous souhaitez utiliser.

11. Sélectionnez le produit transféré.

12. Cliquez sur **Publier** et sélectionnez **Affectations Secure Gateway**.

Vous avez exposé votre API sur site de manière sécurisée sur {{site.data.keyword.apiconnect_short}}. Les éventuels profils TLS associés à une destination sont ajoutés. Pour vérifier les profils TLS,
cliquez sur **Accéder à** <img src="images/navigate_to_icon.png" alt="Icône Accéder à" /> > **Admin** > **Sécurité** > **Profils TLS**.
Vous pouvez disposer de plusieurs passerelles pour chaque API. Vous déterminez la passerelle à utiliser lorsque
vous publiez l'API. Si vous avez déjà mis le service {{site.data.keyword.SecureGateway}} à disposition, vous pouvez
surveiller vos destinations dans le tableau de bord {{site.data.keyword.SecureGateway}}. Vous
ne pouvez cependant pas éditer de destinations
{{site.data.keyword.apiconnect_short}}
créées par le service {{site.data.keyword.apiconnect_short}}.
A présent, testez votre API {{site.data.keyword.SecureGateway}}.

### Test de votre API de passerelle sécurisée
{: test_sec_gate notoc}

Après avoir associé la passerelle à une API, vous pouvez tester
l'API afin de vous assurer que la passerelle fonctionne et qu'elle génère la
réponse correcte.

Pour tester une API à l'aide de la passerelle sécurisée,
procédez comme suit :

1. Cliquez sur l'icône <img alt="Accéder à" src="images/navigate_to_icon.png" /> > **Brouillons** > **API**
**<Votre API>** > **Assembler**.

2. Cliquez sur l'icône **Test** <img src="images/test_icon.png" alt="Icône Test"/>.

3. Sélectionnez un catalogue à tester à partir de la liste fournie.

4. Sélectionnez une passerelle sécurisée à utiliser pour le test à partir de la liste fournie.

5. Choisissez un produit dans la liste fournie, puis cliquez sur **Republier le produit**.
   **Important** : Si le produit est déjà publié dans un catalogue, il sera à
   nouveau publié avec la nouvelle passerelle.

6. **Facultatif** :
Indiquez un nom pour créer un nouveau produit et cliquez sur **Créer et
publier**.

7. Cliquez sur **Suivant**.

8. Sélectionnez une opération à appeler à partir de la liste fournie.

9. Cliquez sur **Appeler**.

Les résultats du test s'affichent.

## Transfert et publication d'une application LoopBack
{: #stage_publish_lb_app}

1. Dans le panneau de navigation du concepteur d'API, cliquez sur **Produits**.
L'onglet Produits s'ouvre.

2. Sélectionnez la version du produit ; veillez à cliquer sur la version que vous souhaitez utiliser.

3. Pour publier l'environnement d'exécution sur {{site.data.keyword.Bluemix_short}}, cliquez sur **Publier**.

4. Cliquez sur **Ajouter et gérer des cibles** > **Ajouter une cible IBM Bluemix**.

5. Sélectionnez la **Région** {{site.data.keyword.Bluemix_short}} cible pour la publication et connectez-vous.

6. Sélectionnez l'**Organisation** {{site.data.keyword.Bluemix_short}} cible pour la publication. 

7.  Une liste de catalogues s'affiche. Sélectionnez le catalogue cible pour la
publication.

8.  Cliquez sur **Suivant**.

9. Sélectionnez l'application LoopBack que vous voulez publier.
Si vous déployez l'environnement d'exécution pour la première fois sur {{site.data.keyword.Bluemix_short}}, ajoutez un nom et cliquez sur l'icône **Ajouter**.

10.  Cliquez sur **Sauvegarder**.

11.  Cliquez de nouveau sur **Publier** et sélectionnez **Publier une application**.

12.  Cliquez sur **Publier**.

13. Sur la ligne de commande, l'URL cible d'API et le profil TLS d'appel d'API sont spécifiés pour l'API.
Notez ces informations. Le profil TLS d'appel d'API est toujours `client:Loopback-client`, mais vous pouvez extraire l'URL cible d'API comme indiqué ci-après.
    ```
    Deploying to Bluemix
    ...preparing project
    ...building package for deploy
    ...uploading package
    Runtime published successfully.
    Management URL: https://<domain name>/apps/33e7b062-092b-4227-af97-047499dab2e7
    API target urls: apiconnect-33e7b062-092b-4227-af97-047499dab2e7.<Bluemix org>-<Bluemix space>.apic.<domain name>
    API invoke tls-profile: client:Loopback-client
    Updated newapi_1.0.0.yaml with tls-profile and target-url.
    Updated notes.yaml with tls-profile and target-url.
    ```

14. Dans l'interface utilisateur du concepteur d'API, procédez comme suit :
    1. Cliquez sur **API**.
    2. Sélectionnez votre API.
    3. Cliquez sur **Assembler**.
    4. Dans l'éditeur d'assemblage, cliquez sur l'icône **Règles de filtrage**.
    5. Sélectionnez **Règles DataPower Gateway**.
    6. Cliquez sur **Sauvegarder** pour sauvegarder l'API.

15.  A présent, vous devez effectuer une publication sur le gestionnaire d'API. Cliquez sur **Publier**.
    1. Sélectionnez **Publier une application**, puis choisissez l'une des options suivantes :
	    - **Remplacer l'application existante** : Si vous disposez d'une application publiée, sélectionnez cette option pour remplacer l'application existante.
        - **En tant que toute nouvelle application (utilisant la route existante)** : Sélectionnez cette option pour créer une nouvelle application et indiquez un nom pour cette dernière dans la zone **Nouvelle application**. Le service n'est pas interrompu.

    2. Sélectionnez les options suivantes :
	    - Transférer ou publier des produits
        - Sélectionner des produits spécifiques
        - _votre produit_
 
    3. Cliquez sur **Publier**.

Pour vérifier que la publication a abouti, procédez comme suit :

1. Vérifiez que l'application {{site.data.keyword.Bluemix_short}} est en cours d'exécution.

2. Ouvrez une fenêtre de navigateur et accédez à l'URL cible de l'API.
L'application est sécurisée au moyen de la validation client. Si vous n'indiquez pas le certificat client approprié, une erreur est générée (comportement normal).

3. Accédez à l'URL {{site.data.keyword.apiconnect_short}} exposée.
Par exemple :
```
https://<domaine>/<org Bluemix>-<espace Bluemix>/<identificateur catalogue>/api/notes
```
Une réponse 200 s'affiche.

## Configuration d'un catalogue

Vous pouvez créer et configurer vos catalogues de gestionnaire
d'API. Les catalogues sont
utiles pour séparer les produits et les API que vous souhaitez tester avant de les mettre à disposition dans des organisations de développeurs.
Lorsque vous configurez un catalogue, vous pouvez également configurer des
données de marque personnalisées de manière à ne pas avoir à utiliser l'URL API
par défaut fournie par le gestionnaire d'API.

Pour créer votre catalogue, procédez comme suit :

1. Cliquez sur **Accéder à** <img alt="Icône Accéder à" src="images/navigate_to_icon.png"> > **Tableau de bord**.

2. Cliquez sur **+ Ajouter** > **Catalogue **.
La fenêtre **Ajouter un catalogue** s'affiche.

3.  Entrez le nom de votre nouveau catalogue dans la zone **Nom
d'affichage**.

4. Entrez le texte devant former le segment de catalogue de l'adresse URL
dans la zone **Nom**.
**Remarque :** La zone **Nom** ne peut comporter que des caractères alphanumériques minuscules (a à z
et 0 à 9) et des traits d'union (-). Le
trait d'union ne peut pas être le premier ou le dernier caractère du nom.

5. Cliquez sur **Ajouter**. Votre catalogue est créé et
affiché dans votre tableau de bord.

6. Pour configurer le catalogue, cliquez sur son nom, puis sur **Paramètres** > **Informations**, puis exécutez les étapes suivantes :
  1. Si le nouveau catalogue est un catalogue de développement, sélectionnez
**Mode de développement**.
Si vous sélectionnez le mode de développement, la constitution et la publication des actions sont forcées, ce qui signifie que si vous republiez un produit qui a déjà été publié, il est écrasé sans qu'aucun avertissement ne s'affiche. Si des
conflits sont détectés, ils sont automatiquement résolus par le système. L'annulation de la publication des actions s'effectue
automatiquement.
**Remarque :** Aucune zone d'approbation ne s'affiche pour les catalogues de développement. Vous ne pouvez pas activer le processus d'approbation pour les cycles de vie.
  2. Si vous souhaitez activer un abonnement automatique pour le catalogue,
sélectionnez **Abonnement automatique**.
L'activation d'un abonnement automatique facilite le test de vos API car une application de test
est utilisée, avec un ID client et une valeur confidentielle du client préfournis, et automatiquement abonnée à tous
les plans du catalogue. Par conséquent, vous n'avez pas à spécifier un plan ou une application lors
des tests. **Remarque :** La fonction d'abonnement automatique est disponible uniquement pour un catalogue de développement.
  3. Si le catalogue est le catalogue de transfert par défaut,
cliquez sur **Par défaut**. Ensuite, les appels d'API qui
sont publiés sur le catalogue peuvent utiliser une URL plus courte qui ne
comporte pas le nom de catalogue.
    **Remarque :** Vous ne pouvez sélectionner **Par défaut** que pour un seul catalogue.
  4. **Facultatif** : Cliquez sur **Noeuds finaux** et renseignez les zones suivantes :
        - **URL de la passerelle personnalisée** : Dans la zone de texte URL de l'API personnalisée, entrez une adresse URL. Vous utilisez l'URL de passerelle personnalisée si vous souhaitez créer une image de marque personnalisée pour les URL des API qui sont déployées sur {{site.data.keyword.apiconnect_short}} au lieu d'utiliser l'URL par défaut générée par le gestionnaire d'API.
        Par défaut, l'URL de passerelle {{site.data.keyword.apiconnect_short}} possède le format suivant :
        ```
        https://gateway_cluster_hostname/organization_name/Catalog_name
        ```
        Toutefois, vous pouvez ignorer le format par défaut en spécifiant une URL convenant mieux à votre entreprise, par exemple, `https://api.monentreprise.com`. Tout noeud final d'API affiché dans le portail de développeur reflétera l'URL spécifiée.
        **Remarques :**
		    - Vous devez configurer une entrée DNS qui mappe votre nom d'hôte et de domaine personnalisé à l'URL de passerelle par défaut.
		    - Pour que les noeuds finaux d'une API reflètent votre URL de passerelle personnalisée, vous devez configurer l'API qui doit être appliquée par la passerelle API Connect. Pour plus d'informations, voir [Specifying an alternative host for an API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){:new_window}.
		    - Assurez-vous que la même URL de passerelle personnalisée n'est pas
appliquée à plusieurs catalogues car le comportement dans ce scénario n'est pas
défini.
	        **CONSEIL** : Lorsque vous appelez l'API, vous pouvez également définir l'en-tête de l'hôte HTTP de la demande d'API
		    sur la valeur que vous avez spécifiée dans la zone URL de la passerelle personnalisée.

	    - **URL de l'API personnalisée**
	    Dans la zone de texte URL de l'API personnalisée, entrez une adresse URL. Vous utilisez cette zone pour spécifier l'URL des API qui sont déployées sur une passerelle tierce.

	    L'URL d'API personnalisée représente le noeud final sous lequel l'API est connue extérieurement, c'est-à-dire le noeud final publié dans le portail de développeur et utilisé par un développeur d'applications pour appeler ou promouvoir l'API.

	    Si vous utilisez une passerelle tierce ou un équilibreur de charge externe
dans ce catalogue, indiquez l'URL dans cette zone. Tout noeud final d'API affiché dans le portail de développeur reflétera l'URL spécifiée. Ces noeuds finaux existent sur la passerelle tierce ou sur l'équilibreur de charge et projettent une adresse virtuelle, exposée aux consommateurs de l'API, qui est mappée au proxy de l'API ou aux noeuds finaux de l'assemblage d'API sur la passerelle. Les noeuds finaux qui sont dérivés de l'URL d'API personnalisée sont généralement publiés dans les portails de développeur de production afin de faire la promotion de l'adresse de l'API.

	    **Remarque :** Si vous spécifiez une URL d'API personnalisée pour un catalogue, il est prioritaire sur n'importe quel nom d'hôte que vous
	    spécifiez lors de la configuration de l'API. Pour plus d'informations, voir [Specifying an alternative host for an API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){:new_window}.

	    - **Nom d'hôte des appels API du portail de développeur** :
	    Dans la zone de la fenêtre Noeud final d'API de port, entrez un nom d'hôte pour les appels d'API de portail de développeur. Le
nom d'hôte que vous entrez peut être celui de votre service de gestion. Pour accéder à l'API de portail de développeur dans le contexte d'un portail de développeur, vous devez configurer le nom d'hôte de base pour les appels d'API de portail de développeur. Cette action permet au gestionnaire d'API de mapper votre nom d'hôte à
l'organisation de type fournisseur et au catalogue des appels d'API du portail
de développeur et vous évite d'avoir à les rechercher et à les inclure dans vos
appels.

7. Cliquez sur l'icône **Sauvegarder**.

## Partitionnement d'un catalogue

Pour pouvoir utiliser la fonction de syndication dans
{{site.data.keyword.apiconnect_short}},
vous devez activer les espaces dans tous les catalogues dans lesquels vous avez
besoin de la syndication.

Pour activer les espaces dans un catalogue, procédez comme suit :
1. Dans le Tableau de bord de l'interface utilisateur du gestionnaire d'API,
sélectionnez le catalogue que vous souhaitez utiliser.

2. Cliquez sur **Paramètres** > **Vue d'ensemble**, puis sur le contrôle de curseur **Espaces**.

3. Dans la fenêtre **Activation des espaces**, cliquez sur **Activer**, puis sur l'icône **Sauvegarder** <img src="images/icon_save.png" alt="icône Sauvegarder"/>.
Un lien **Gérer les espaces** s'affiche
sous le contrôle de curseur **Espaces**, et un lien **Espaces** est ajouté au panneau de navigation. Vous
pouvez gérer vos espaces en cliquant sur l'un de ces liens.

Les espaces sont activés pour votre catalogue et un espace par défaut,
nommé New Space, est créé.

Pour plus d'informations sur l'utilisation de la syndication, reportez-vous aux rubriques du Knowledge Center, [Utilisation de la syndication dans IBM API Connect ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.apionprem.doc/capic_syndication_using.html){:new_window}.

## Configuration d'un portail de développeur
{: #config_dev_portal}

Un portail de développeur est là où vos plans sont publiés afin d'être accessibles et utilisables par les développeurs d'applications.

Vous pouvez créer un portail de développeur personnalisé pour vos développeurs d'applications. Vous disposez d'un contrôle administratif complet sur l'apparence, le contenu, les paramètres utilisateur et les paramètres de configuration.

Outre le fait qu'il permet aux développeurs d'applications de rechercher et d'utiliser des API, le portail de développeur fournit également des fonctions supplémentaires, telles que des forums, des blogues, des commentaires, des évaluations et une interface utilisateur swagger pour les API.

1. Dans l'interface utilisateur du gestionnaire d'API, sélectionnez le
catalogue que vous souhaitez utiliser.

2. Sélectionnez l'onglet **Paramètres**.

3. Cliquez sur **Portail**.

4. Dans la section **Configuration de portail**, sélectionnez **IBM Developer
Portal**. L'URL de portail s'affiche.

5. Cliquez sur **Sauvegarder**. Vous recevez un courrier électronique contenant un lien de connexion à usage unique pour l'administrateur Web du portail de développeur.

6. Cliquez sur le lien figurant dans le courrier électronique et suivez les instructions pour réinitialiser votre mot de passe.

Votre portail de développeur est configuré. L'URL du portail de développeur se trouve sur la ligne Objet du courrier électronique que vous avez reçu. L'URL est également disponible dans l'interface utilisateur du gestionnaire d'API ; vous pouvez y accéder en cliquant sur **Portail** > **Paramètres**.

Pour plus d'informations sur les tâches que vous pouvez exécuter dans le portail de développeur, consultez les rubriques de l'IBM
Knowledge Center relatives au [portail de développeur![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.devportal.doc/capim_devportal_overview.html){:new_window}.

## Configuration des droits des rôles
{: #config_permissions_roles}

Pour configurer les droits des rôles dans le gestionnaire d'API,
procédez comme indiqué ci-après.

1. Dans le **Tableau de bord** du gestionnaire d'API,
cliquez sur le catalogue que vous souhaitez utiliser.

2. Cliquez sur **Paramètres** > **Droits**.
Les droits de gestion du produit auxquels vous pouvez attribuer des rôles sont les suivants :
  - **Transférer** : Permet de transférer les produits dans le catalogue.
  - **Afficher** : Permet d'afficher et de répertorier les produits dans le catalogue.
  - **Gérer** : Permet de gérer le cycle de vie des produits (publication, dépréciation, retrait et archivage).
  - **Approuver** : Permet d'approuver les modifications d'état du cycle de vie des produits.
**Remarque :** L'approbation des changements d'état de cycle de vie du produit est désactivée pour tous les catalogues de développement.

3. Pour ajouter un rôle aux droits **Transférer**, **Afficher** ou **Gérer**, cliquez sur l'icône **+** correspondante.
La liste suivante présente les rôles disponibles par défaut :
  - Administrateur
  - Responsable produit
  - développeur d'API
  - Diffuseur de publications
Le rôle Propriétaire possède tous les droits.

4. Activez les approbations pour les modifications d'état du cycle de vie d'un produit en sélectionnant les cases à cocher appropriées, puis en cliquant
sur l'icône **+** correspondante afin d'affecter les rôles qui disposent des droits permettant d'approuver une modification d'état de cycle
de vie.
Les modifications d'état du cycle de vie sélectionnées sont celles pour lesquelles vous souhaitez appliquer l'approbation.
Par exemple, si vous
sélectionnez Publier mais que vous ne sélectionnez pas les autres options, l'approbation est alors requise lorsqu'un utilisateur tente de publier
un produit mais aucune approbation n'est requise pour les autres modifications d'état du cycle de vie.
5. Pour affecter les rôles disposant des droits de gestion des stratégies
définies par les utilisateurs, cliquez sur l'icône **+**
dans la section **Gestion des stratégies**.
Les droits de gestion des stratégies s'affichent alors et vous pouvez affecter les rôles comme bon vous semble.
6. Cliquez sur l'icône **Sauvegarder**.
