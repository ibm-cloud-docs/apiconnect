---

copyright:
  years: 2017
lastupdated: "2017-10-24"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal

subcollection: apiconnect

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Configuration d'un catalogue
{: #create_catalog}

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
L'activation d'un abonnement automatique facilite le test de vos API car une application de test est utilisée avec un ID client et une valeur confidentielle du client préfournis. Cette application de test est automatiquement abonnée à tous les plans du catalogue. Par conséquent, vous n'avez pas à spécifier de plan ni d'application lors des tests. 
    **Remarque :** La fonction d'abonnement automatique est disponible uniquement pour un catalogue de développement.
  3. Si le catalogue est le catalogue de transfert par défaut,
cliquez sur **Par défaut**. Dans ce cas, les appels API qui sont publiés dans le
catalogue peuvent utiliser une adresse URL plus courte qui ne comporte pas le nom de
catalogue.
    **Remarque :** Vous ne pouvez sélectionner **Default** que pour un seul catalogue.
  4. **Facultatif** : Cliquez sur **Noeuds finaux** et renseignez les zones suivantes :
        - **URL de la passerelle personnalisée** : Dans la zone de texte URL de l'API personnalisée, entrez une adresse URL. Vous utilisez l'URL de passerelle personnalisée si vous souhaitez créer une image de marque personnalisée pour les URL des API qui sont déployées sur {{site.data.keyword.apiconnect_short}} au lieu d'utiliser l'URL par défaut générée par le gestionnaire d'API.
        Par défaut, l'URL de passerelle {{site.data.keyword.apiconnect_short}} possède le format suivant :
        ```
        https://gateway_cluster_hostname/organization_name/Catalog_name
        ```
        Toutefois, vous pouvez ignorer le format par défaut en spécifiant une URL convenant mieux à votre entreprise, par exemple, `https://api.monentreprise.com`. Tout noeud final d'API affiché dans le portail de développeur reflétera l'URL spécifiée.
			**Remarques :**
		    - Vous devez configurer une entrée DNS qui mappe votre nom d'hôte et de domaine personnalisé à l'URL de passerelle par défaut.
		    - Pour que les noeuds finaux d'une API reflètent votre URL de passerelle personnalisée, vous devez configurer l'API qui doit être appliquée par la passerelle API Connect. Pour plus d'informations, voir [Specifying an alternative host for an API ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){: #new_window}.
		    - Assurez-vous que la même URL de passerelle personnalisée n'est pas
appliquée à plusieurs catalogues car le comportement dans ce scénario n'est pas
défini.
				**CONSEIL** : Lorsque vous appelez l'API, vous pouvez également définir l'en-tête de l'hôte HTTP de la demande d'API sur la valeur que vous avez spécifiée dans la zone URL de la passerelle personnalisée.

	    - **URL de l'API personnalisée**
	    Dans la zone de texte URL de l'API personnalisée, entrez une adresse URL. Vous utilisez cette zone pour spécifier l'URL des API qui sont déployées sur une passerelle tierce.

	    L'URL d'API personnalisée représente le noeud final sous lequel l'API est connue extérieurement, c'est-à-dire le noeud final publié dans le portail de développeur et utilisé par un développeur d'applications pour appeler ou promouvoir l'API.

	    Si vous utilisez une passerelle tierce ou un équilibreur de charge externe
dans ce catalogue, indiquez l'URL dans cette zone. Tout noeud final d'API affiché dans le portail de développeur reflétera l'URL spécifiée. Ces noeuds finaux existent sur la passerelle tierce ou sur l'équilibreur de charge et projettent une adresse virtuelle, exposée aux consommateurs de l'API, qui est mappée au proxy de l'API ou aux noeuds finaux de l'assemblage d'API sur la passerelle. Les noeuds finaux qui sont dérivés de l'URL d'API personnalisée sont généralement publiés dans les portails de développeur de production afin de faire la promotion de l'adresse de l'API.

	    **Remarque :** Si vous spécifiez une URL d'API personnalisée pour un catalogue, il est prioritaire sur n'importe quel nom d'hôte que vous
	    spécifiez lors de la configuration de l'API. Pour plus d'informations, voir [Specifying an alternative host for an API ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){: #new_window}.

	    - **Nom d'hôte des appels API du portail de développeur** :
	    Dans la zone de la fenêtre Noeud final d'API de port, entrez un nom d'hôte pour les appels d'API de portail de développeur. Le
nom d'hôte que vous entrez peut être celui de votre service de gestion. Pour accéder à l'API de portail de développeur dans le contexte d'un portail de développeur, vous devez configurer le nom d'hôte de base pour les appels d'API de portail de développeur. Cette action permet au gestionnaire d'API de mapper votre nom d'hôte à
l'organisation de type fournisseur et au catalogue des appels d'API du portail
de développeur et vous évite d'avoir à les rechercher et à les inclure dans vos
appels.

7. Cliquez sur l'icône **Sauvegarder**.

## Partitionnement d'un catalogue
{: #apic_spaces_create_catalog}

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

Pour plus d'informations sur l'utilisation de la syndication, reportez-vous aux rubriques du Knowledge Center, [Utilisation de la syndication dans IBM API Connect ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.apionprem.doc/capic_syndication_using.html){: #new_window}.
