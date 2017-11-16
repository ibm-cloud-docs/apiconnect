---

copyright:
  years: 2017
lastupdated: "2017-06-05"

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Glossaire

Glossaire des termes et définitions d'{{site.data.keyword.apiconnect_short}}.

- **abonnement** : L'abonnement est le moyen par lequel un développeur d'applications peut accéder aux ressources fournies par une API. Un développeur d'applications utilise le portail de développeur pour s'abonner au plan dans lequel l'API est publiée.

- **application** : Elément de code client qui accède aux API pour interagir avec un service, un système ou un contenu. Les applications sont généralement des applications Web ou des applications
mobiles.

- **assemblage** : Interface de programme d'application qui offre des fonctionnalités enrichies pour l'interaction avec une application : elle effectue des appels de côté à des services externes, puis transforme et agrège la réponse avant qu'une réponse soit relayée vers l'application appelante.

- **catalogue** :  Un catalogue est une cible de transfert qui se comporte comme une partition logique de la passerelle et du portail de développeur. Les URL des
appels d'API et du portail de développeur sont propres à un catalogue donné.

- **catalogue de bac à sable** :  Dans un catalogue de bac à sable, aucune approbation n'est requise pour la publication et les actions de cycle de vie. Les approbations en attente
sont annulées lorsqu'un catalogue autre qu'un catalogue de bac à sable est converti en bac en sable. Un catalogue de bac à sable est utilisé pour tester
les API en cours de développement.

- **chemin** : Un chemin définit la route via laquelle les utilisateurs accèdent aux API REST. Il se compose d'une ou de plusieurs opérations HTTP, telles que GET ou
POST.

- **communauté** : Ensemble d'organisations de développeurs. Utilisé en tant que
construction de groupement lors de la publication des API. Les communautés sont utilisés pour restreindre la visibilité et l'accessibilité des API. Une API peut être publiée pour certaines communautés sélectionnées, ce qui signifie que seuls les développeurs d'applications au sein de ces organisations peuvent visualiser l'API.

- **concepteur d'API (API Designer)** : Interface utilisateur permettant de créer des API.

- **définition de sécurité** : Une définition de sécurité spécifie tous les paramètres d'un aspect particulier de la sécurité d'une API ; par exemple, le registre d'utilisateurs que vous souhaitez utiliser pour authentifier l'accès à l'API.

- **développeur d'API**: Un développeur d'API crée et configure des API, des produits et des stratégies pour les organisations de type fournisseur dont il est membre. Un développeur d'API peut être membre d'une
ou de plusieurs organisations de type fournisseur. Le développeur d'API s'occupe davantage de l'implémentation technique des
API que des relations commerciales avec les développeurs d'applications.

- **extension de fournisseur** : Une extension de fournisseur est ajoutée à une API REST pour étendre la spécification OpenAPI (Swagger 2.0).

- **gestionnaire d'API** : Interface utilisateur permettant de gérer des API, des plans et des produits.

- **ID client** :  Elément d'information qui identifie une application individuelle. Une application peut appeler une API uniquement si elle transmet une clé d'application
qui est reconnue par le système {{site.data.keyword.apiconnect_short}} et est autorisée à accéder à l'API. La clé
d'application est transmise par le client à l'aide d'un paramètre de requête HTTP.

- **modèle LoopBack** : Un modèle LoopBack est un objet JavaScript qui représente des données d'application et inclut des règles de validation, des fonctions d'accès aux données et une logique métier. Les modèles LoopBack fournissent une API REST par défaut et se connectent à des sources de données pour accéder à des données de back end.

- **opération d'API** : Unité d'API REST qui peut être appelée. Une opération d'API comprend une instruction HTTP et un chemin d'URL subordonnés à la racine de contexte de l'API.

- **organisation** : Entité qui détient les API ou les applications utilisant des API. Une organisation de type fournisseur possède des API et les plans associés et peut en outre
posséder des applications. Une organisation de développeurs détient uniquement des applications. Une organisation comporte au moins un propriétaire. Une organisation peut être une
équipe projet, un service ou une division.

- **plan** : Construction de package par lequel les API sont accessibles aux développeurs. Un plan rend disponible une collection d'opérations d'une ou de plusieurs
API, et est publié pour des communautés de développeurs d'applications. Les développeurs d'applications
obtiennent un accès aux API en s'enregistrant auprès d'applications d'accès aux plans. Un plan s'accompagne d'une collection de paramètres de règle. Dans sa forme la plus basique, un plan définit une simple règle de quota qui s'applique à toutes les opérations d'API accessibles via le plan. Dans les cas plus évolués, des règles supplémentaires peuvent être
associées à un plan.

- **produit** : Les produits offrent une méthode permettant de regrouper des API dans un package destiné à une utilisation spécifique. De plus, ils contiennent les plans
qui peuvent être utilisés pour différencier les offres. Vous ne pouvez créer des plans que dans des produits qui sont ensuite publiés dans un catalogue.

- **profil SSL** : Un profil SSL permet de sécuriser la transmission de données par le biais de sites Web. Des certificats SSL garantissent que les informations
que vous soumettez aux sites Web ne seront pas volées ou falsifiées.

- **proxy** : Interface de programme d'application qui transfère les demandes à une ressource de back end définie par l'utilisateur et relaie les réponses en sens inverse vers l'application appelante.

- **publier** : Processus qui consiste à sortir une application ou un produit de la phase de transfert de sorte que les plans et les API qu'ils contiennent soient disponibles, accessibles et utilisables par les développeurs d'applications.

- **registre d'utilisateurs** : Un registre d'utilisateurs est un moyen de sécuriser l'accès aux catalogues et aux API. L'utilisateur peut protéger les API avec un registre
d'utilisateurs pour que les données d'identification utilisateur soient demandées lorsqu'une API est appelée.

- **règles** : Une stratégie est un élément de configuration qui contrôle un aspect spécifique du traitement sur le serveur de passerelle lors du traitement d'un appel API au moment de l'exécution. Les règles constituent les blocs de construction des flux d'assemblage. Grâce aux règles, il est possible de configurer des fonctions de sécurité, de
consignation, de routage des demandes vers des services cibles et de
transformation des données d'un format vers un autre. Les règles peuvent être configurées dans le contexte d'une API ou d'un plan.

- **rôle** : Un rôle définit les droits pouvant activer une fonctionnalité pour des utilisateurs. Chaque rôle possède un ensemble de droits différent.

- **source de données LoopBack** : Une source de données LoopBack est un objet JavaScript qui représente un service de back end, tel qu'une base de données, une API REST (à consommer) ou un service Web SOAP. Les sources de données sont sauvegardées par des connecteurs, qui communiquent ensuite directement avec la base de données ou d'autres services de back end.

- **transfert** : Processus qui consiste à déplacer une application ou un produit qui est à l'état Brouillon dans un catalogue afin de le préparer à être publié.

- **valeur confidentielle du client** : Elément d'information qui est utilisé conjointement avec la clé d'application pour vérifier l'identité d'une application. Une API peut être configurée
pour exiger que les applications client fournissent leur valeur confidentielle d'application
avec leur clé d'application. La valeur confidentielle d'application fonctionne efficacement
en tant que mot de passe connu uniquement de l'application. La valeur confidentielle
d'application est transmise par le client à l'aide d'un paramètre de requête HTTP.
