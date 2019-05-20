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

# Traitement des incidents
{: #apic_troubleshoot}

Voici les réponses aux questions fréquentes sur le traitement des incidents liés à l'utilisation d'{{site.data.keyword.apiconnect_long}} sur {{site.data.keyword.Bluemix_notm}}.
{:shortdesc}

## Nom d'utilisateur et mot de passe requis lors de l'ajout du service {{site.data.keyword.Bluemix_notm}} d'API Connect
{: #user_pw_apic_troubleshoot}

Une fois que vous avez ajouté le service à votre tableau de bord {{site.data.keyword.Bluemix_notm}}, un message vous demande d'entrer un nom d'utilisateur et un mot de passe lorsque vous voulez l'ouvrir. 

### Symptômes
{: #ts_sym_usernamepw_apic_troubleshoot}

Au lieu d'accéder directement au service {{site.data.keyword.Bluemix_notm}} lorsque vous ouvrez une nouvelle session {{site.data.keyword.apiconnect_short}}, vous devez vous connecter au gestionnaire d'API.

### Cause
{: #ts_cause_usernamepw_apic_troubleshoot}

Votre navigateur est configuré pour bloquer les cookies ou le niveau défini est plus restrictif que ne le requiert {{site.data.keyword.apiconnect_notm}}.

### Résolution
{: #ts_res_usernamepw_apic_troubleshoot}

Activez ou augmentez le niveau des cookies dans vos paramètres de navigateur jusqu'à ce que le service {{site.data.keyword.Bluemix_notm}} s'ouvre.

## Impossible d'installer le kit d'outils de développement
{: #unable_tk_apic_troubleshoot}

Après avoir mis à disposition le service API Connect, vous essayez d'installer le kit d'outils de développement, mais l'installation échoue.

### Symptômes
{: #ts_sym_noinstalltk_apic_troubleshoot}

Les erreurs suivantes s'affichent lors de l'installation du kit d'outils de développement :
```
npm ERR! Error: EACCES, mkdir '/usr/local/lib/node_modules/apiconnect'
...
npm ERR! Please try running this command again as root/Administrator
...
```

### Cause
{: #ts_cause_noinstalltk_apic_troubleshoot}

Vous ne disposez pas des droits requis pour créer des fichiers ou des répertoires.

### Résolution
{: #ts_res_noinstalltk_apic_troubleshoot}

Modifiez les droits pour les répertoires spécifiés, ou exécutez la commande à l'aide de `sudo`. Sur un système de développement local, il est plus judicieux de corriger les droits de répertoire comme suit :
```
sudo chown -R $USER /usr/local
```
{:codeblock}

Cette commande fait de votre compte utilisateur
le propriétaire du répertoire `/usr/local`. Ensuite, vous n'aurez pas besoin d'utiliser sudo pour installer Node ni d'installer des packages globalement à l'aide de npm. 
    **Remarque :** Le changement de propriété pour le répertoire n'est approprié que sur un système de développement local. Vous ne devez effectuer cette opération sur un système de serveur.

De plus, vous ne devez pas utiliser la commande `chown` précédente sur le répertoire `/usr/bin`, car cela risquerait de provoquer une configuration erronée du système.

Si vous devez utiliser `sudo`, exécutez la commande suivante :
```
sudo npm install -g --unsafe-perm install apiconnect
```
{:codeblock}

## Impossible d'installer le kit d'outils de développement sur Windows
{: #unable_tk_win_apic_troubleshoot}

Après avoir mis à disposition le service {{site.data.keyword.apiconnect_short}}, vous essayez d'installer le kit d'outils de développement, mais l'installation échoue.

### Symptômes
{: #ts_sym_noinstalltk_path_apic_troubleshoot}

Vous essayez d'installer le kit d'outils de développement sous Windows et vous recevez un message d'erreur indiquant que votre *chemin ne doit pas comporter plus de 248 caractères*.

### Cause
{: #ts_cause_noinstalltk_path_apic_troubleshoot}

Sous Windows, il existe une longueur de chemin maximale,
laquelle est dépassée lorsque vous essayez d'installer toutes les dépendances dans un dossier situé à un niveau très bas.

### Résolution
{: #ts_res_noinstalltk_path_apic_troubleshoot}

Pour résoudre ce problème, procédez de l'une des manières suivantes :

- Vérifiez que vous avez installé la version correcte de Node.js. Pour plus d'informations, voir [Installation du kit d'outils de développement](/docs/services/apiconnect?topic=apiconnect-creating_apis).

- Si vous été obligé de mettre à niveau un logiciel, relancez l'installation.

Si cela ne fonctionne pas, installez {{site.data.keyword.apiconnect_short}} à un niveau
supérieur au dossier `C:/program files/nodejs/bin/node_modules...`. Une installation dans un répertoire de niveau supérieur permet de résoudre cette erreur.

## Impossible d'installer le kit d'outils de développement sur Mac OS X
{: #unable_tk_mac_apic_troubleshoot}

Après avoir mis à disposition le service {{site.data.keyword.apiconnect_short}}, vous essayez d'installer le kit d'outils de développement, mais l'installation échoue.

### Symptômes
{: #ts_sym_noinstalltk_mac_apic_troubleshoot}

Les erreurs suivantes s'affichent lors de l'installation du kit d'outils de développement :
```
Agreeing to the Xcode/iOS license requires admin 
privileges, please re-run as root via sudo
```

### Cause
{: #ts_cause_noinstalltk_mac_apic_troubleshoot}

Vous avez récemment mis à niveau ou installé Xcode et vous n'avez pas encore accepté la licence.

### Résolution
{: #ts_res_noinstalltk_mac_apic_troubleshoot}

1. Entrez la commande suivante pour valider votre licence Xcode :
```
sudo xcode-select
```
{:codeblock}

2. Réinstaller le kit d'outils de développement.


## Impossible d'installer le kit d'outils de développement sur Ubuntu
{: #unable_tk_ubu_apic_troubleshoot}

Après avoir mis à disposition le service {{site.data.keyword.apiconnect_short}}, vous essayez d'installer le kit d'outils de développement, mais l'installation échoue.

### Symptômes
{: #ts_sym_noinstalltk_ubu_apic_troubleshoot}

Les erreurs suivantes s'affichent lors de l'installation du kit d'outils de développement :
```
sqlite3@3.1.1 install /usr/local/lib/node_modules/strong-pm/node_modules/minkelite/node_modules/sqlite3 
node-pre-gyp install --fallback-to-build 
/usr/bin/env: node: No such file or directory 
npm WARN This failure might be due to the use of legacy binary "node" 
npm WARN For further explanations, please read /usr/share/doc/nodejs/README.Debian 
npm ERR! weird error 127 
npm ERR! not ok code 0
```

### Résolution
{: #ts_res_noinstalltk_ubu_apic_troubleshoot}

Entrez la commande suivante pour résoudre le problème :
```
$ update-alternatives --install /usr/bin/node node /usr/bin/nodejs 99
```

## Impossible de déboguer l'échec de l'installation de npm
{: #unable_nmp_apic_troubleshoot}

Lorsque vous suivez la procédure pour installer le kit d'outils de développement, l'installation de npm échoue.

### Symptômes
{: #ts_sym_npmfail_apic_troubleshoot}

L'installation de npm échoue et aucune information utile concernant le débogage n'est fournie.

### Résolution
{: #ts_res_npmfail_apic_troubleshoot}

Lorsqu'une installation échoue, npm écrit une ligne dans le fichier `npm-debug.log</filepath>` pour indiquer à quel endroit s'est produite. Utilisez le fichier `npm-debug.log` pour déterminer
la cause de l'échec.

## Impossible d'ouvrir le concepteur d'API
{: #unable_apid_apic_troubleshoot}

Vous entrez la commande `apic edit` et le concepteur d'API ne s'ouvre pas.

### Symptômes
{: #ts_sym_noopenapid_apic_troubleshoot}

Vous ne pouvez pas ouvrir une instance du concepteur d'API après avoir entré la commande :
```
apic edit
```
et le message suivant s'affiche :
```
<time stamp>. 329Z ERROR apiConnect: listen EADDRINUSE <ip address>:9000
```

### Cause
{: #ts_cause_noopenapid_apic_troubleshoot}

Vous avez déjà démarré une instance du concepteur d'API à partir d'une autre fenêtre de commande.

### Résolution
{: #ts_res_noopenapid_apic_troubleshoot}

Pour remédier à ce problème, fermez l'autre fenêtre de commande comme indiqué dans la procédure suivante :

1. Dans l'autre fenêtre de commande, appuyez sur **Ctrl + C**.

2. Le message ci-après s'affiche.
```
Terminate Batch job (Y/N)?
```

3. Tapez `Y` et appuyez sur Entrée.

## Impossible de configurer les informations de facturation pour un produit
{: #cannot_bill_apic_troubleshoot}

Certaines des informations de facturation ne sont pas disponibles pour configuration ou validation en production. 

### Symptômes
{: #ts_sym_nobill_apic_troubleshoot}

  - Lorsque vous examinez la section Admin de votre produit, l'onglet Facturation n'est pas affiché.
  - Lorsque vous tentez de publier un produit avec les informations de facturation spécifiées, vous obtenez un message d'erreur. 

### Cause
{: #ts_cause_nobill_apic_troubleshoot}

Vous devez détenir le compte {{site.data.keyword.apiconnect_short}} et les droits appropriés pour activer les informations de facturation.

## Abonnement à un plan de facturation avec un produit impossible
{: #cannot_bill_plan_apic_troubleshoot}

Stripe limite chaque client à un maximum de 25 abonnements. Vérifiez que vous n'avez pas dépassé
cette limite. Si tel est le cas, vous ne pouvez ajouter cet abonnement que si vous en supprimez un autre.

### Symptômes
{: #ts_sym_nosubscribe_apic_troubleshoot}

Un message d'erreur s'affiche lorsque vous essayez de vous abonner à un plan avec facturation, alors que vous détenez d'autres plans configurés.

### Cause
{: #ts_cause_nosubscribe_apic_troubleshoot}

Le service de traitement des cartes de crédit Stripe autorise un maximum de 25 abonnements par compte.

### Résolution
{: #ts_res_nosubscribe_apic_troubleshoot}

Vérifiez que vous avez un compte de niveau Entreprise pour votre service {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.apiconnect_short}} et qu'il détient moins de 25 instances. Supprimez un service, si vous avez atteint le nombre maximum de services autorisé.

## Aide et support pour API Connect
{: #get_help_apic_troubleshoot}

Si vous rencontrez des problèmes ou si vous vous posez des questions lors de l'utilisation d'{{site.data.keyword.apiconnect_short}}, vous pouvez obtenir de l'aide en recherchant des informations ou en posant vos questions sur un forum. Vous pouvez également ouvrir un ticket de demande de service.

Si vous utilisez les forums pour poser une question, libellez votre question de sorte qu'elle soit vue par les équipes de développement {{site.data.keyword.Bluemix_notm}}. 

- Si vous avez des questions techniques sur le développement ou le déploiement d'une application avec {{site.data.keyword.apiconnect_short}}, publiez votre question sur Stack Overflow et marquez-la avec les étiquettes "ibm-cloud" et "api connect."

- Pour des questions relatives au service et aux instructions de mise en route, utilisez le forum IBM DeveloperWorks - dW Answers. Incluez les étiquettes "ibm cloud" et "api connect".
Voir Obtenir de l'aide pour plus de détails sur l'utilisation des forums. 

Pour obtenir des informations sur l'ouverture d'un ticket de demande de service IBM ou sur les niveaux de service disponibles et les degrés de gravité des tickets, voir la rubrique Contacter le service de support.



