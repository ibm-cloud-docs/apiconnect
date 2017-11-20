---
copyright:
  years: 2017
lastupdated: "2017-09-19"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Installazione del toolkit API Connect
**Durata**: 15 minuti  
**Livello di competenza**: Principiante  

## Cosa ti serve
1. Node.js
2. Node Product Manager (NPM)
3. {{site.data.keyword.apiconnect_short}} _Lite_

<table>
  <tr><td><b>Node.js</b>: un evento asincrono guidato dal runtime JavaScript utilizzato per creare ed eseguire le applicazioni di rete scalabili.
    <br>
    <b>Node Product Manager</b>: gestore pacchetto JavaScript e registro software<br>
    <b>{{site.data.keyword.apiconnect_short}} _Lite_</b>: una versione gratuita di {{site.data.keyword.apiconnect_short}} ospitata nel tuo portatile</td></tr>
  </table>  


## Installa node.js
1. Scarica ed installa node.js da una di queste due risorse:
   * [https://nodejs.org/en/download/ ![Icona link esterno](../../../icons/launch-glyph.svg "Icona link esterno")](https://nodejs.org/en/download/){:new_window} (Nota: scarica la versione LTS per la tua piattaforma, non l'ultima o potresti riscontrare degli errori.)
      **OR**
   * [https://developer.ibm.com/node/sdk/v6/ ![Icona link esterno](../../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/node/sdk/v6/){:new_window}  

    _Installando node.js si installa anche **npm** (Node Package Manager)_.

2.  Dopo aver scaricato e installato Node.js, assicurarsi che sia in _PATH_.
    ![](images/verify-path.png)  

3. Aggiorna **npm**. Nella riga di comando, immetti `npm install -g npm`.  
   **Nota:** configurando npm `--engine-strict` o `npm config set engine-strict true` impedisci il completamento dell'installazione.


4. Controlla il percorso e la versione installati.
   ![](images/screenshot_install_apic-1.png)  



## Installa il toolkit API Connect e Microgateway
1. Aggiorna la configurazione di npm per consentire l'utilizzo di certificati non attendibili.  
   `npm config -g set strict-ssl false`  

2. Installa il toolkit {{site.data.keyword.apiconnect_short}} da **npm**.  
    `npm install -g apiconnect`

3. Controlla la versione installata.   
    `apic -v`

4. Immetti il seguente comando nella riga di comando: `npm install -g microgateway`.

Utilizzeremo Microgateway come un server di test locale.
