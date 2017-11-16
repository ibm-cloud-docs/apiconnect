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

# Instalando o kit de ferramentas do API Connect
**Duração**: 15 min  
**Nível de qualificação**: iniciante  

## O que você precisará
1. Node.js
2. Node Product Manager (NPM)
3. {{site.data.keyword.apiconnect_short}} _Lite_

<table>
  <tr><td><b>Node.js</b>: um tempo de execução JavaScript acionado por evento assíncrono usado para construir e executar aplicativos de rede escalável
    <br>
    <b>Node Product Manager</b>: gerenciador de pacote do JavaScript e registro de software<br>
    <b>{{site.data.keyword.apiconnect_short}} _Lite_</b>: uma versão grátis do {{site.data.keyword.apiconnect_short}} que é hospedada em seu laptop</td></tr>
  </table>  


## Instalar o node.js
1. Faça download e instale o node.js de uma das duas origens:
   * [https://nodejs.org/en/download/ ![External link icon](../../../icons/launch-glyph.svg "External link icon")](https://nodejs.org/en/download/){:new_window} (Nota: faça download da versão LTS para sua plataforma, não a mais recente ou você poderá ter erros.)
      **OU**
   * [https://developer.ibm.com/node/sdk/v6/ ![External link icon](../../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/node/sdk/v6/){:new_window}  

    _Instalando o node.js também instala o **npm** (Node Package Manager)_.

2.  Quando o Node.js é transferido por download e instalado, verifique se ele está em seu _PATH_.
![](images/verify-path.png)  

3. Atualize o **npm**. Em uma linha de comandos, insira `npm install -g npm`.  
   **Nota:** configurar o npm `--engine-strict` ou `npm config set engine-strict true` evita que a instalação seja concluída.


4. Verifique a versão instalada e o caminho.
   ![](images/screenshot_install_apic-1.png)  



## Instalar o kit de ferramentas do API Connect e o Microgateway
1. Atualize a configuração npm para permitir o uso de certificados não confiáveis.  
   `npm config -g set strict-ssl false`  

2. Instale o kit de ferramentas do {{site.data.keyword.apiconnect_short}} do **npm**.  
    `npm install -g apiconnect`

3. Verifique a versão instalada.  
    `apic -v`

4. Insira o comando a seguir na linha de comandos: `npm install -g microgateway`.

Usaremos o Microgateway como um servidor de teste local.
