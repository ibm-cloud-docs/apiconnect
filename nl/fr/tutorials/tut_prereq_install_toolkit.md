---
copyright:
  years: 2017
lastupdated: "2017-10-31"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Installation du kit d'outils API Connect
**Durée**: 15 mn  
**Niveau de compétence** : Débutant  

## Ce dont vous avez besoin
1. Node.js
2. Node Product Manager (NPM)
3. {{site.data.keyword.apiconnect_full}} _Lite_

<table>
  <tr><td><b>Node.js</b> : Exécution JavaScript asynchrone pilotée par événement et utilisée pour générer et exécuter applications réseau évolutives
    <br>
    <b>Node Product Manager</b> : Gestionnaire de package et registre logiciel JavaScript<br>
    <b>{{site.data.keyword.apiconnect_short}} _Lite_</b> : Version gratuite d'{{site.data.keyword.apiconnect_short}} hébergée sur votre ordinateur portable</td></tr>
  </table>  


## Installation de node.js
1. Téléchargez et installez node.js à partir de l'une des deux sources suivantes :
   * [https://nodejs.org/en/download/ ![Icône de lien externe](../../../icons/launch-glyph.svg "Icône de lien externe")](https://nodejs.org/en/download/){:new_window} (Remarque : Téléchargez la version LTS pour votre plateforme, et non la plus récente, ou vous pourriez rencontrer des problèmes.)
      **OU**
   * [https://developer.ibm.com/node/sdk/v6/ ![Icône de lien externe](../../../icons/launch-glyph.svg "Icône de lien externe")](https://developer.ibm.com/node/sdk/v6/){:new_window}  

    _Le processus d'installation de node.js installe également **npm** (Node Package Manager)_.

2.  Une fois Node.js téléchargé et installé, vérifiez qu'il se trouve bien dans _PATH_.
    ![](images/verify-path.png)  

3. Mettez à jour **npm**. Sur une ligne de commande, entrez `npm install -g npm`.  
   **Remarque :** La définition de npm `--engine-strict` ou `npm config set engine-strict true` empêche l'installation de se terminer.


4. Vérifiez la version installée et le chemin.
   ![](images/screenshot_install_apic-1.png)  



## Installez le kit d'outils API Connect et Microgateway
1. Mettez à jour le fichier npm config afin d'autoriser l'utilisation de certificats non sécurisés.  
   `npm config -g set strict-ssl false`  

2. Installez le kit d'outils {{site.data.keyword.apiconnect_short}} à partir de **npm**.  
    `npm install -g apiconnect`

3. Vérifiez la version installée.  
    `apic -v`

4. Entrez la commande suivante sur la ligne de commande : `npm install -g microgateway`.

Nous utiliserons Microgateway comme serveur de test local.
