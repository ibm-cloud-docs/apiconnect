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

# Resolução de Problemas
{: #troubleshoot}

Aqui estão as respostas às perguntas comuns de resolução de problemas sobre o
uso do {{site.data.keyword.apiconnect_long}} no
{{site.data.keyword.Bluemix_notm}}.
{:shortdesc}

## Nome do usuário e senha necessários ao incluir o serviço API Connect {{site.data.keyword.Bluemix_notm}}

Depois de incluir o serviço em seu Painel do {{site.data.keyword.Bluemix_notm}}, um nome de usuário e uma senha são solicitados quando você tenta abri-lo. 

### Sintomas
{: #ts_sym_usernamepw}

Em vez de acessar o serviço {{site.data.keyword.Bluemix_notm}} diretamente ao abrir um novo {{site.data.keyword.apiconnect_short}}, ele requer que você efetue login no API Manager.

### Causa
{: #ts_cause_usernamepw}

Seu navegador está configurado para bloquear cookies ou o nível está configurado para um nível mais restrito do que o {{site.data.keyword.apiconnect_notm}} requer.

### Resolução
{: #ts_res_usernamepw}

Ative ou aumente o nível de permissão de cookies em suas configurações do navegador até que ele abra o serviço {{site.data.keyword.Bluemix_notm}}.

## Não é possível instalar o kit de ferramentas do desenvolvedor

Após a provisão do serviço API Connect, você tenta instalar o kit de ferramentas do desenvolvedor e
a instalação falha.

### Sintomas
{: #ts_sym_noinstalltk}

Os erros a seguir são exibidos durante a instalação do kit de ferramentas do
desenvolvedor:
```
npm ERR! Error: EACCES, mkdir '/usr/local/lib/node_modules/apiconnect'
...
npm ERR! Please try running this command again as root/Administrator
...
```

### Causa
{: #ts_cause_noinstalltk}

Você não tem os direitos necessários para criar arquivos ou diretórios.

### Resolução
{: #ts_res_noinstalltk}

Mude os direitos para os diretórios especificados ou execute o comando usando
`sudo`. Em um sistema de desenvolvimento local, é melhor corrigir os direitos do diretório como
a seguir:
```
sudo chown -R $USER /usr/local
```
{:codeblock}

Esse comando torna sua conta do usuário
a proprietária do diretório `/usr/local`. Em seguida, não será necessário usar sudo para
instalar o Node ou instalar pacotes globalmente com npm. 
    **Nota:** mudar a propriedade do diretório é apropriado somente em um sistema de desenvolvimento local. Nunca faça isso em um sistema servidor.

Além disso, não use o comando
`chown` anterior no diretório `/usr/bin`;
fazer isso pode causar uma configuração incorreta grave no sistema.

Se for necessário usar `sudo`, use
o comando a seguir:
```
sudo npm install -g --unsafe-perm install apiconnect
```
{:codeblock}

## Não é possível instalar o kit de ferramentas do desenvolvedor no Windows

Após a provisão do serviço do
{{site.data.keyword.apiconnect_short}}, você
tenta instalar o kit de ferramentas do desenvolvedor e a instalação falha.

### Sintomas
{: #ts_sym_noinstalltk_path}

Você está tentando instalar o kit de ferramentas do desenvolvedor no Windows e recebe uma mensagem de erro que indica que o *caminho deve ter menos de 248 caracteres*.

### Causa
{: #ts_cause_noinstalltk_path}

Em sistemas Windows, há um comprimento máximo de caminho
que é excedido quando você tenta instalar todas as dependências em uma pasta de nível profundo.

### Resolução
{: #ts_res_noinstalltk_path}

É possível corrigir esse problema de uma das seguintes formas:

- Assegure-se de que tenha instalado a versão correta de Node.js. Para obter mais informações, veja [Instalando o Developer Toolkit](creating_apis.html).

- Se for necessário fazer upgrade de um programa, tente a instalação novamente.

Se isso não funcionar, instale o {{site.data.keyword.apiconnect_short}} em um nível
maior do que a provável pasta `C:/program files/nodejs/bin/node_modules...`. Se você instalar em um diretório de nível
superior, não verá esse erro.

## Não é possível instalar o kit de ferramentas do desenvolvedor no Mac OS X

Após a provisão do serviço do
{{site.data.keyword.apiconnect_short}}, você
tenta instalar o kit de ferramentas do desenvolvedor e a instalação falha.

### Sintomas
{: #ts_sym_noinstalltk_mac}

Os erros a seguir são exibidos durante a instalação do kit de ferramentas do
desenvolvedor:
```
Agreeing to the Xcode/iOS license requires admin
privileges, please re-run as root via sudo
```

### Causa
{: #ts_cause_noinstalltk_mac}

Recentemente você fez upgrade ou instalou o Xcode e não concordou com a licença
ainda.

### Resolução
{: #ts_res_noinstalltk_mac}

1. Insira o comando a seguir para validar sua licença do Xcode:
```
sudo xcode-select
```
{:codeblock}

2. Reinstale o kit de ferramentas do desenvolvedor.


## Não é possível instalar o kit de ferramentas do desenvolvedor no Ubuntu

Após a provisão do serviço do
{{site.data.keyword.apiconnect_short}}, você
tenta instalar o kit de ferramentas do desenvolvedor e a instalação falha.

### Sintomas
{: #ts_sym_noinstalltk_ubu}

Os erros a seguir são exibidos durante a instalação do kit de ferramentas do
desenvolvedor:
```
sqlite3@3.1.1 install /usr/local/lib/node_modules/strong-pm/node_modules/minkelite/node_modules/sqlite3
node-pre-gyp install --fallback-to-build
/usr/bin/env: node: No such file or directory
npm WARN This failure might be due to the use of legacy binary "node"
npm WARN For further explanations, please read /usr/share/doc/nodejs/README.Debian
npm ERR! weird error 127
npm ERR! not ok code 0
```

### Resolução
{: #ts_res_noinstalltk_ubu}

Insira o comando a seguir para resolver o
problema:
```
$ update-alternatives --install /usr/bin/node node /usr/bin/nodejs 99
```

## Não é possível depurar a falha de instalação de npm

Ao seguir as etapas para instalar o kit de ferramentas do
desenvolvedor, a instalação
de npm falhará.

### Sintomas
{: #ts_sym_npmfail}

A instalação de npm falha sem fornecer informações úteis para
depuração.

### Resolução
{: #ts_res_npmfail}

Quando uma instalação falha, o npm grava uma linha no arquivo `npm-debug.log</filepath>`
para mostrar onde o erro está localizado. Use o arquivo `npm-debug.log` para determinar
a causa.

## Não é possível abrir o API Designer

Você insere o comando `apic edit` e a API
Designer não é aberta.

### Sintomas
{: #ts_sym_noopenapid}

Não é possível abrir uma instância do API Designer depois que você insere o comando:
```
apic edit
```
e a mensagem a seguir é exibida:
```
<time stamp>. 329Z ERROR apiConnect: listen EADDRINUSE <ip address>:9000
```

### Causa
{: #ts_cause_noopenapid}

Você já
iniciou uma instância do API Designer em outra janela de comando.

### Resolução
{: #ts_res_noopenapid}

Para
corrigir esse problema, é necessário fechar a outra janela de comando conforme
descrito nas etapas a seguir:

1. Na outra janela de comando, pressione **Ctrl + C**.

2. A seguinte
mensagem é exibida.
```
Terminate Batch job (Y/N)?
```

3. Digite `Y` e pressione Enter.

## Não é possível configurar informações de faturamento de um Produto

Algumas das informações de faturamento não estão disponíveis para configurar ou confirmar a produção. 

### Sintomas
{: #ts_sym_nobill}

  - Quando você olha para a seção Administração de seu Produto, a guia Faturamento não é exibida.
  - Quando tenta publicar um Produto com as informações de faturamento especificadas, você obtém um erro. 

### Causa
{: #ts_cause_nobill}

Deve-se ter a conta e as permissões corretas do {{site.data.keyword.apiconnect_short}} para ativar informações de faturamento.

## Não é possível assinar um Plano de faturamento com um Produto

A faixa limita cada cliente a um máximo de 25 assinaturas. Assegure-se de que você não tenha excedido
esse limite. Se sim, será possível incluir essa assinatura se você remover outra assinatura.

### Sintomas
{: #ts_sym_nosubscribe}

Você vê um erro quando tenta assinar um Plano com faturamento, embora tenha outros Planos configurados.

### Causa
{: #ts_cause_nosubscribe}

O serviço de processamento de cartão de crédito de Faixa permite um máximo de 25 assinaturas por conta.

### Resolução
{: #ts_res_nosubscribe}

Assegure-se de que você tenha uma conta no nível Corporativo para seu serviço {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.apiconnect_short}} e que existam menos de 25 instâncias. Remova um serviço, se você tiver o número máximo de serviços.

## Obtendo ajuda e suporte para o API Connect

Se você tiver problemas ou perguntas ao usar o
{{site.data.keyword.apiconnect_short}},
poderá obter ajuda procurando por informações ou fazendo perguntas
através de um fórum. Também é possível abrir um chamado de suporte.

Ao usar os fóruns para fazer uma pergunta, marque a sua pergunta
para que ela possa ser vista pelas equipes de desenvolvimento do {{site.data.keyword.Bluemix_notm}}. 

- Se você tiver questões técnicas sobre como desenvolver ou implementar um app com o {{site.data.keyword.apiconnect_short}}, poste sua pergunta no Stack Overflow e identifique-a com "ibm-cloud" e "api connect".

- Para perguntas sobre o serviço e instruções de introdução, use o IBM DeveloperWorks dW Answers. Inclua as tags "ibm cloud" e "api connect".
Veja Obtendo ajuda para obter mais detalhes sobre como usar os fóruns. 

Para obter informações sobre como abrir um chamado de suporte IBM ou sobre os níveis de suporte e as severidades de chamados, veja Entrando em contato com o suporte.



