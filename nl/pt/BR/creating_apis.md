---

copyright:
  years: 2017
lastupdated: "2017-12-15"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Criando APIs
{: #creating_apis}

É possível criar APIs fazendo download do kit de ferramentas do
desenvolvedor e usando a interface da linha de comandos (CLI) ou o API Designer.

## A CLI do kit de ferramentas do desenvolvedor
{: #dev_tk_cli notoc}

O kit de ferramentas do desenvolvedor fornece uma interface da linha de comandos que
pode ser usada para publicar APIs no
{{site.data.keyword.apiconnect_long}}.
Publique APIs incluindo-as em um Produto e, em seguida, publicando o Produto. Defina suas APIs e Produtos criando e validando arquivos de definição YAML no sistema de arquivos local. Será possível então interagir com o {{site.data.keyword.apiconnect_long}} usando os comandos do kit de ferramentas.

## API Designer
{: #designer notoc}

O API Designer é uma interface gráfica com o usuário off-line dentro do kit de
ferramentas do desenvolvedor e fornece funções para a criação e configuração de APIs.
O API Designer é executado usando o comando edit na interface da linha de comandos. Quando
o comando edit é usado, a API Designer é aberta em seu navegador padrão
ou pode ser acessada por meio da porta do host local que é exibida quando você executa o
comando.

## Instalando o kit de ferramentas do desenvolvedor
{: #install_dev_tk}

### Pré-requisito
{: #prereq_install_dev_tk}

Antes de iniciar, deve-se instalar o [Node.js ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://nodejs.org/en/){:new_window} na máquina em que
você deseja usar o kit de ferramentas e assegurar que `nó` esteja em seu `PATH`.

Os itens a seguir são instalados quando você instala o
kit de ferramentas do desenvolvedor.

- Ferramenta de linha de comandos do {{site.data.keyword.apiconnect_short}}
- Editor gráfico do {{site.data.keyword.apiconnect_short}}
- Microgateway local do
{{site.data.keyword.apiconnect_short}}


1. Para instalar o kit de ferramentas, abra o prompt de comandos como administrador e
insira o comando a seguir.

    ```
    npm install -g apiconnect
    ```
    {: codeblock}

    **Nota:** durante a instalação, você pode ver erros do módulo `node-gyp`. Esses
erros são de uma dependência opcional e a instalação será concluída com êxito.

2. Para visualizar um resumo da ajuda de uso de todos os comandos do kit de ferramentas, insira o comando a seguir:

    ```
    projeto
    ```
	{: codeblock}

3. Para visualizar a ajuda de uso para qualquer comando, utilize a opção `--help`.
    Por exemplo:

    ```
    apic validate --help
    ```
	{: codeblock}
	
## Instalando conectores LoopBack
{: #install_lb_conn}

Para que seja possível usar uma origem de dados LoopBack para acessar dados em um sistema backend, como um
banco de dados, deve-se instalar o conector de origem de dados. Os conectores na memória e de e-mail são integrados
ao LoopBack, portanto, não é necessário instalá-los.

### Pré-requisito
{: #prereq_install_lb_conn}

Os conectores Oracle, DB2 e SQLLite requerem ferramentas do compilador C para construir e instalar extensões
binárias. Os requisitos exatos dependem de seu sistema operacional, conforme descrito na tabela a
seguir.

<table summary="" id="apic_028__table_pre_reqs" class="defaultstyle style-scope doc-content">
<caption>Tabela 1. Requisitos de instalação específicos do sistema operacional</caption>
<thead>
<tr>
<th style="width: 33.3%" id="th_d70e208" class="thleft style-scope doc-content">Windows</th>
<th style="width: 33.3%" id="th_d70e210" class="thleft style-scope doc-content">Linux</th>
<th style="width: 33.3%" id="th_d70e212" class="thleft style-scope doc-content">MAC OS X</th>
</tr>
</thead>
<tbody >
<tr class="style-scope doc-content doc-tr-odd">
<td style="width: 33.3%" > [Microsoft .NET Framework 4 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.microsoft.com/en-us/download/details.aspx?id=17851)</td>
<td style="width: 33.3%">Python v2.7 (v3.x não é suportado)</td>
<td style="width: 33.3%" > [Liberações do Python para Mac OS X ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.python.org/downloads/mac-osx/)</td>
</tr>
<tr><td style="width: 33.3%" > [Visual Studio ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.visualstudio.com/downloads/download-visual-studio-vs)</td>
<td style="width: 33.3%">
<code>make</code>
</td>
<td style="width: 33.3%" > [Xcode ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.apple.com/xcode/?cm_mc_uid=46449280653414622613810&amp;cm_mc_sid_50200000=1459433716)</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 33.3%" > [Python v2.7.10 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.python.org/downloads/release/python-2710/)</td>
<td style="width: 33.3%">Uma cadeia de ferramentas do compilador C/C++, por exemplo, GCC versão 4.2 ou mais recente. </td>
<td style="width: 33.3%" >&nbsp;</td>
</tr>
<tr><td style="width: 33.3%" > [Microsoft Windows SDK para Windows 7 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.microsoft.com/en-gb/download/details.aspx?id=8279)</td>
<td style="width: 33.3%">Em distribuições Debian e derivadas de Debian (Ubuntu, Mint, etc.), use o comando:
<pre class="codeblock style-scope doc-content"><code>apt-get install build-essential</code></pre>
</td>
<td style="width: 33.3%" >&nbsp;</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 33.3%" >npm versão 3. Veja a nota a seguir.</td>
<td style="width: 33.3%">&nbsp;</td>
<td style="width: 33.3%" >&nbsp;</td>
</tr>
</tbody>
</table>

**Nota:** para instalações do Windows:

- Use
o Visual Studio Community, a menos que você queira comprar o
Visual Studio Enterprise. Execute o instalador, selecione "Visual C++" em "Linguagens de Programação" e
aceite o local da instalação padrão.

- Para construções de 64 bits de Node.js e módulos nativos, você também precisa do SDK do Windows&trade; 7 de 64 bits. Se a instalação falhar, tente desinstalar qualquer
redistribuível C++ 2010 x64&amp;x86 que tenha sido instalado primeiro. Se você obtém erros de que os compiladores
de 64 bits não estão instalados, também pode precisar da atualização do compilador para o Windows&trade; SDK 7.1.
- Insira o comando a seguir para instalar o npm versão
3:
  ```
  npm install -g npm
  ```
  {: codeblock}
  Em seguida, assegure-se de que o comando npm use a versão
correta:
  ```
  npm -v
  ```
  {: codeblock}
  Se a versão mostrada não for a 3.x.x, edite o PATH do sistema
para assegurar que `C:\Users\username\AppData\Roaming\npm` suplante quaisquer outras
entradas.


1. **Opcional**:
se você estiver usando o API Designer, abra uma nova janela shell.

2. Quando você tiver instalado as ferramentas do compilador que são necessárias para seu sistema operacional, instale
o conector inserindo o comando a seguir no diretório-raiz do projeto.

```
npm install --save <connector-package>
```
{: codeblock}
em que `<connector-package>` é o nome do pacote npm para o conector LoopBack, conforme mostrado na tabela.

<table summary="" id="apic_connectors_table_pre_reqs" class="defaultstyle style-scope doc-content">
<caption>Tabela 3. Conectores de LoopBack</caption>
<thead>
<tr class="style-scope doc-content doc-tr-even">
<th style="width: 50%" id="th_new_d70e1489" class="thleft style-scope doc-content">Fonte de dados</th>
<th style="width: 50%" id="th_new_d70e1491" class="thleft style-scope doc-content">Pacote do Conector</th>
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
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Microsoft
SQL Server</td>
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
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">Serviços da web SOAP</td>
<td style="width: 50%">loopback-connector-soap</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Serviços da Web do Representational State Transfer</td>
<td style="width: 50%">loopback-connector-rest</td>
</tr>
</tbody>
</table>

## Criando uma API LoopBack usando a CLI
{: #create_lb_api}

O procedimento a seguir descreve como criar uma API de LoopBack&reg; usando a interface da linha de comandos.


### Pré-requisito
{: #prereq_create_lb_api}

Antes de iniciar, tenha em mãos o identificador de catálogo do catálogo que você deseja usar. Para obter o identificador de catálogo, conclua as etapas a seguir:  

1. Acesse **Painel** do {{site.data.keyword.apiconnect_short}}.

2. Para o catálogo que você deseja usar, clique no ícone **Mostrar identificador de catálogo**
<img alt="Ícone do link de cadeia para exibir o identificador do catálogo" src="images/chain_link_icon.png">.

3. Copie o identificador de catálogo. Por exemplo:  
  ```
  apic config:set catalog=apic-catalog://<region>.apiconnect.ibmcloud.com/orgs/<username_string>-dev/catalogs/<catalog>
  ```
  {: codeblock}
    em que:

    - `<region>` é a região do {{site.data.keyword.Bluemix_notm}}.

    - `<username_string>` é seu ID de organização do {{site.data.keyword.Bluemix_notm}} sem nenhum símbolo. Por exemplo,
`joe@mycompany.com` seria `joemycompanycom`

    - `<catalog>` é o nome de seu catálogo  

Para criar uma API de LoopBack usando a CLI, conclua as etapas a seguir:

1. Para criar um projeto, abra uma linha de comandos e insira:
  ```
  apic loopback
  ```
  {: codeblock}

2. No prompt que se segue, você é solicitado a nomear seu aplicativo. Digite um nome e, em seguida, pressione
**Enter**.
  ```
  ? What's the name of your application? (<application name>)
  ```
    
    A ferramenta solicita que você insira o nome do diretório no qual criar o
projeto.
    ```
    ? Enter name of the directory to contain the project: (<project directory name>)
    ```
    
3. Pressione
**Enter** para usar o nome que você inseriu anteriormente ou digite um novo nome, em seguida,
pressione **Enter**. A ferramenta solicita que você selecione o tipo de aplicativo a ser
criado:
```
? What kind of application do you have in mind? (Usar teclas de seta) servidor vazio (Uma API de LoopBack vazia, sem nenhum modelo ou origem de dados configurado) > hello-world (Um projeto contendo um exemplo de trabalho básico, incluindo um banco de dados de memória)
```

4. Selecione o aplicativo que você deseja usar e pressione **Enter**.
A ferramenta exibe várias mensagens à medida que cria o diretório de projeto e inclui vários diretórios e arquivos nele. Ela também executa `npm install` para instalar todas as dependências do projeto, conforme especificado em `package.json`.
Este processo pode levar algum tempo.

5. Antes de poder criar um modelo, você precisa certificar-se de que seu diretório atualmente em funcionamento seja o
diretório de nível superior do projeto. Para fazer isso, insira o seguinte comando:
    ```
    cd <project directory name>
    ```
    {: codeblock}

6. Para criar um modelo, insira o comando a seguir:
    ```
    apic create --type model
    ```
    {: codeblock}

    A ferramenta solicitará o nome do modelo.

    ```
    ? Enter the model name:
    ```

7. Insira um nome para o modelo.
    Em geral, é possível usar quaisquer caracteres alfanuméricos além de traços e sublinhados em um
nome de modelo.
    Todas as origens de dados que você incluiu no projeto são listadas e a
ferramenta solicita que você selecione uma origem de dados a ser usada:
    ```
    ? Select the data-source to attach item to: (Use arrow keys)
    ```

8. Selecione a origem de dados que você deseja usar e pressione
**Enter**. A ferramenta solicita que você selecione classe base
do modelo:
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
    Para obter mais informações sobre cada opção, veja [Usando modelos integrados ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://loopback.io/doc/en/lb3/Using-built-in-models.html){:new_window}.

9. Selecione uma classe base e pressione **Enter**. A ferramenta pergunta se você deseja expor a API REST
do modelo.
```
? Expose branch via the REST API? (Y/n)
```
Se o modelo for exposto sobre REST, todas as operações padrão, criar, ler, atualizar e
excluir, estarão disponíveis por meio de terminais REST.

10. Insira sua seleção e pressione **Enter**.
Se você optou por expor o modelo sobre REST, a ferramenta solicitará a forma plural
do nome do modelo.
```
? Custom plural form (used to build REST URL):
```

11. Pressione **Enter** para usar as regras padrão de pluralização
em inglês.
A ferramenta pergunta se você deseja criar um modelo somente de servidor ou um modelo comum que
possa ser usado na API do LoopBack do servidor ou do cliente.
```
? Common model or server only? (Use arrow keys)
```

12. Use as teclas de seta para fazer sua seleção e pressione **Enter**.
A ferramenta solicita que você inclua propriedades no
modelo:
```
Let's add some branch properties now.
Enter an empty property name when done.
? Property name:
```

13. Informe um nome de propriedade.
A ferramenta solicita que você selecione o tipo de dados da
propriedade:
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

14. Selecione o tipo de sequência e pressione **Enter**.
A ferramenta pergunta se a propriedade é necessária:
```
? Required? (y/N)
```

15. Digite `y` ou `n` e pressione
**Enter**.
A ferramenta solicita que você inclua outra propriedade:
```
Let's add another branch property.
Enter an empty property name when done.
? Property name:
```

16. Se necessário, inclua outro nome de propriedade. Se você não precisar de mais
propriedades, pressione **Enter** para concluir a inclusão do modelo.

Por padrão, um projeto LoopBack vem configurado com uma origem de dados na memória, adequada para desenvolvimento e teste. Entretanto, em algum ponto, você desejará conectar
seus modelos a uma origem de dados real, como o servidor de banco de dados. Conclua
as etapas a seguir para incluir uma origem de dados:

1. Insira o comando a seguir:
```
apic create --type datasource
```
{: codeblock}
A ferramenta solicitará o nome da origem de dados.
```
? Enter the data-source name:
```

2. Insira um nome para a origem de dados.  É possível usar qualquer caractere alfanumérico, traços e sublinhados em um nome de origem de dados. A ferramenta solicita que você selecione o conector a ser usado para a origem
de dados:
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

3. Use as teclas de seta para selecionar o conector que você deseja usar; em
seguida, pressione **Enter**.
A ferramenta então inclui a origem de dados no projeto.

4. Insira o host, a porta, o usuário, a senha e as credenciais do banco de dados.
A ferramenta solicita que você instale o conector LoopBack.
```
Install loopback-connector-<connector>?
```

5. Digite `Sim`.
A ferramenta instala o conector.

NOTA: se você selecionou o conector Oracle, deve-se configurar uma variável de ambiente no
{{site.data.keyword.Bluemix_notm}} para o app Oracle ser iniciado. Para fazer isso, conclua as etapas a seguir:

1. Na UI (interface com o usuário) do {{site.data.keyword.Bluemix_notm}}, selecione
**Calcular**.

2. Em Aplicativos CF, selecione o aplicativo com o qual deseja trabalhar.

3. Clique em **Tempo de Execução**.

4. Selecione **Variáveis de ambiente**.

5. Na seção Definido pelo Usuário, clique em **INCLUIR**.

6. No campo **Nome**, insira `LD_LIBRARY_PATH`.

7. No campo **Valor**, insira
`$LD_LIBRARY_PATH:/home/vcap/app/node_modules/instantclient`.

8. Clique em **Salvar**.

### Testando um projeto LoopBack
{: #test_lb_proj}

Para testar um projeto LoopBack, conclua as etapas a seguir.

1. **Opcional**: certifique-se de que seu diretório atualmente em funcionamento seja o diretório de nível superior do projeto. Insira o comando a seguir:
```
cd <loopback-project-dir>
```
em que `<loopback-project-dir>` é o nome do diretório que contém o projeto.
2. Insira o comando a seguir:
```
apic start
```
Isso executa o projeto LoopBack (API) e o Micro Gateway localmente. As mensagens a seguir são exibidas:
```
Waiting for loopback-project to complete deployment.
Waiting for loopback-project-gw to complete deployment.
Service loopback-project (id 1) started on port 4001
Service loopback-project-gw (id 2) started on port 4002
```
em que: `<loopback-project>` é o nome do diretório que contém o projeto.

É possível então testar qualquer um dos terminais de API usando `curl`, por exemplo.
Se você desejar carregar a API usando um navegador da web, abra
`http://localhost:4001` em seu navegador. Para o projeto LoopBack
padrão (vazio ou hello-world), você verá algo como:
```
{"started":"2016-03-07T22:24:55.322Z","uptime":35.839}
```

### Publicando um aplicativo LoopBack no {{site.data.keyword.Bluemix_notm}} da CLI
{: #pub_lb_app_cli}

Para publicar um aplicativo LoopBack no {{site.data.keyword.Bluemix_short}} por meio da linha de comandos, conclua as etapas a seguir:

1. Insira o comando a seguir para assegurar-se de que você está no diretório de projeto Loopback.
```
cd <loopback-project-dir>
```
2. Insira o comando a seguir para efetuar login no {{site.data.keyword.apiconnect_short}} e {{site.data.keyword.Bluemix_notm}}.
```
apic login --server  <region>.apiconnect.ibmcloud.com -u <username> -p <password>
```
em que:
  * `<username>` é seu ID de organização do {{site.data.keyword.apiconnect_short}}.
  * `<password>` é sua senha do {{site.data.keyword.apiconnect_short}}.
3. Pressione a barra de espaço para abrir automaticamente a página do navegador de **Senha única**.
4. Clique em **Gerar novamente** e copie a senha única.
5. De volta na CLI, cole a senha para concluir seu login. A seguinte mensagem é exibida:
```
Logged into <region>.apiconnect.ibmcloud.com successfully
```
6. Insira o comando a seguir:
```
apic organizations -s <region>.apiconnect.ibmcloud.com
```
em que:
  * `<region>` é a região do {{site.data.keyword.Bluemix_notm}}. Por exemplo:
  * `eu` se você estiver usando o {{site.data.keyword.Bluemix_notm}} em Londres.
  * `us` se você estiver usando o {{site.data.keyword.Bluemix_notm}} em Dallas.
  * `au` se você estiver usando o {{site.data.keyword.Bluemix_notm}} em Sydney.

  Se você não tiver certeza, será possível localizar sua região clicando no ícone {{site.data.keyword.avatar}} <img src="images/i-avatar-icon.svg" alt="avatar icon"/> na barra de menus para abrir o widget Conta e suporte e verificar o campo de região.
7. Insira o comando a seguir para publicar seu aplicativo no
{{site.data.keyword.Bluemix_notm}}.
```
apic apps:publish –a <app> -o <org> -s <region>.apiconnect.ibmcloud.com
```
em que:
  * `<app>` é o nome de seu app
  * `<org>` é o nome de sua organização do {{site.data.keyword.Bluemix_notm}}
  * `<region>` é a região do {{site.data.keyword.Bluemix_notm}}
A saída a seguir é retornada:
  ```
  ...preparing project
  ...building package for deploy
  ...uploading package
  Runtime published successfully.
  Management URL: https://new-console.stage1.ng.bluemix.net/apps/3aa7087d-b454-4e13-bbc5-8228ebe00eef
  API target urls: apiconnect-3aa7087d-b454-4e13-bbc5-8228ebe00eef.pszetousibmcom-dev.apic.stage1.mybluemix.net
  API invoke tls-profile: client:Loopback-client
  ```

8. Em seguida, deve-se modificar as definições do Produto com os valores retornados durante o
tempo de publicação. Para fazer isso, conclua as etapas a seguir:

    1. Na UI do API Designer, clique em **APIs**.
    2. Selecione a API.
    3. Clique em **Montar**.
    4. No editor Montar, clique no ícone **Políticas de filtro**.
    5. Selecione **Políticas de gateway do DataPower**.
    6. Clique duas vezes em **Chamar**.
    7. Atualize os campos a seguir com os valores recuperados na etapa 7.
        - **Chamar URL**: insira a URL de destino da API. Deve-se especificar o protocolo seguro
HTTPS. Por exemplo:
        ```
        https://apiconnect-33e7b062-092b-4227-af97-047499dab2e7.<Bluemix org>-<Bluemix space>.apic.<domain name>$(request.path)
        ```
        Se você não anotou esse valor, é possível recuperá-lo acessando a URL de gerenciamento retornada na
        etapa 7. É possível também recuperá-lo efetuando login no {{site.data.keyword.Bluemix_notm}} e visualizando suas informações do app.
        - **Perfil do TLS**: insira a chamada de API tls-profile. Por exemplo:
        ```
        client:Loopback-client
        ```
    8. Clique em **Salvar** para salvar a API.

## Criando uma API LoopBack usando o API Designer
{: #create_lb_api_design}

O procedimento a seguir descreve como criar uma API LoopBack usando o API
Designer.
{:shortdesc}

### Pré-requisito
{: #prereq_create_lb_api_design}

**Nota**: as instruções a seguir presumem que você está usando a versão mais recente do
kit de ferramentas do desenvolvedor. Para verificar a versão mais recente, veja a página do pacote [npm ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.npmjs.com/package/apiconnect){:new_window}.

Primeiro, você precisa criar um projeto LoopBack usando a CLI. Conclua as etapas a seguir para fazer isso:

1. Para criar um projeto, abra uma linha de comandos e insira:
  ```
  apic loopback
  ```
  {: codeblock}

2. No prompt que se segue, você é solicitado a nomear seu aplicativo. Digite um nome e, em seguida, pressione
**Enter**.
  ```
  ? What's the name of your application? (<application name>)
  ```
    
    A ferramenta solicita que você insira o nome do diretório no qual criar o
projeto.
    ```
    ? Enter name of the directory to contain the project: (<project directory name>)
    ```
    
3. Pressione
**Enter** para usar o nome que você inseriu anteriormente ou digite um novo nome, em seguida,
pressione **Enter**. A ferramenta solicita que você selecione o tipo de aplicativo a ser
criado:
```
? What kind of application do you have in mind? (Usar teclas de seta) servidor vazio (Uma API de LoopBack vazia, sem nenhum modelo ou origem de dados configurado) > hello-world (Um projeto contendo um exemplo de trabalho básico, incluindo um banco de dados de memória)
```

4. Selecione o aplicativo que você deseja usar e pressione **Enter**.
A ferramenta exibe várias mensagens à medida que cria o diretório de projeto e inclui vários diretórios e arquivos nele. Ela também executa `npm install` para instalar todas as dependências do projeto, conforme especificado em `package.json`.
Este processo pode levar algum tempo.

5. Para poder criar um modelo, você precisa certificar-se de que seu diretório
atualmente em funcionamento seja o diretório de nível superior do projeto. Para fazer isso, insira o seguinte comando:
```
cd <project directory name>
```

**Nota**: tornar seu diretório atualmente em funcionamento o diretório de nível superior do projeto irá assegurar
que a opção para incluir modelos e origens de dados esteja disponível ao abrir o API Designer. Se você
abrir o API Designer sem mudar o diretório, não será capaz de incluir modelos e origens
de dados.

Para abrir o API Designer, conclua as etapas a seguir:
1. Abra uma linha de comandos e insira:
```
apic edit
```
    Após uma pausa breve, a mensagem a seguir será exibida.
    ```
    Express server listening on http://127.0.0.1:9000
    ```
    O API Designer é aberto no navegador da web padrão.

2. Na página de login, digite seu ID e senha do
{{site.data.keyword.Bluemix_notm}}. Clique em **Efetuar Sign In**.

3. Clique em **Modelos**.

4. Clique em **Incluir**. A janela **Modelo**
de LoopBack é aberta.

5. Insira um nome de modelo.
Em geral, é possível usar quaisquer caracteres alfanuméricos além de traços e sublinhados em um
nome de modelo.

6. Clique em **Novo**.

7. Na página do editor de modelo, acesse Propriedades e clique em
**Incluir**.

8. Insira o Nome da propriedade e selecione um Tipo

9. Quando terminar de inserir as Propriedades do modelo, clique em
**Salvar**.

Por padrão, um projeto LoopBack vazio não possui nenhuma origem de dados definida. Para definir uma fonte de dados, execute as seguintes etapas:
1. Clique em **Origens de Dados**.

2. Clique no ícone **Incluir**.
A janela Novo **modelo** de LoopBack é aberta.

3. Insira um nome da origem de dados. É possível usar qualquer caractere alfanumérico, traços e sublinhados em um nome de origem de dados.

4. Clique em **Novo**.
A origem de dados aparece na lista de origens de dados e o editor atualiza
o arquivo `server/datasources.json` com as configurações para a nova
origem de dados.

5. Clique em sua origem de dados para visualizar suas configurações.

6. Mude a configuração do Connector para o conector que você
precisa.

7. Volte para o console em que você iniciou o API Designer e
instale o Connector
inserindo o comando a seguir:
```
npm install --save <connector-package>
```
    em que `<connector-package>` é o nome do pacote npm para o conector LoopBack selecionado. Consulte a tabela a seguir para ver uma lista de
pacotes do Connector.

**Nota:** os conectores na memória e de e-mail estão integrados no LoopBack, portanto, não é necessário instalá-los.

<table>
<caption>Tabela 3. Conectores de LoopBack</caption>
<thead>
<tr class="style-scope doc-content doc-tr-even">
<th style="width: 50%" id="3rd_d70e1489" class="thleft style-scope doc-content">Fonte de dados</th>
<th style="width: 50%" id="3rd_d70e1491" class="thleft style-scope doc-content">Pacote do Conector</th>
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
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Microsoft
SQL Server</td>
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
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">Serviços da web SOAP</td>
<td style="width: 50%">loopback-connector-soap</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Serviços da Web do Representational State Transfer</td>
<td style="width: 50%">loopback-connector-rest</td>
</tr>
</tbody>
</table>

Para obter mais informações, veja [Documentação do LoopBack - Construindo um conector ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://loopback.io/doc/en/lb3/Defining-data-sources.html){:new_window}.

**Nota:** se você selecionou o conector Oracle, deve-se configurar uma variável de ambiente no
{{site.data.keyword.Bluemix_notm}} para o app Oracle ser iniciado. Para fazer isso, conclua as etapas a seguir:

1. Na UI (interface com o usuário) do {{site.data.keyword.Bluemix_notm}}, selecione
**Calcular**.

2. Em Aplicativos CF, selecione o aplicativo com o qual deseja trabalhar.

3. Clique em **Tempo de Execução**.

4. Selecione **Variáveis de ambiente**.

5. Na seção Definido pelo Usuário, clique em **INCLUIR**.

6. No campo **Nome**, insira `LD_LIBRARY_PATH`.

7. No campo **Valor**, insira
`$LD_LIBRARY_PATH:/home/vcap/app/node_modules/instantclient`.

8. Clique em **Salvar**.

Para testar um projeto LoopBack, conclua as etapas a seguir:
1. Clique no ícone **Iniciar os servidores**.
A seguinte mensagem é exibida:
```
http://localhost:<4001/>Running
```
Dependendo da configuração de seu projeto e de se outros processos estão em execução, um número de porta
diferente poderá ser exibido.

2. Clique em **localhost:4001** para exibir o terminal raiz da API. Para o projeto LoopBack
padrão (vazio ou hello-world), você verá algo como:
```
{"started":"2017-03-07T22:24:55.322Z","uptime":35.839}
```

Em seguida, é necessário criar um Produto. Para obter mais informações, consulte [Criando um produto](managing_products.html#create_product).
**Dica**: sempre que você iniciar um novo prompt de comandos, certifique-se de que seu diretório atualmente
em funcionamento seja o diretório de nível superior do projeto. Para fazer isso, insira o seguinte comando:
```
cd <project directory name>
```

## Desinstalando o kit de ferramentas do desenvolvedor
{: #uninstall_dev_tk}

### Pré-requisito
{: #prereq_uninstall_dev_tk}

Antes de iniciar, deve-se parar quaisquer apps que estão em execução localmente
inserindo o comando a seguir:
```
apic stop --all
```

Para desinstalar o kit de ferramentas do desenvolvedor, conclua as etapas a seguir:

1. Insira o comando a seguir:
```
npm rm -g apiconnect
```
{: codeblock}

2. Limpe o cache npm:
```
npm cache clean
```
{:codeblock}
  
Se estiver usando o Windows:

3. Exclua todos os arquivos cujos nomes iniciam com `npm-` em `\C:\Users\username\AppData\Local\Temp`
4. Exclua o diretório `<home_dir>\.apiconnect`, em que `<home_dir>` é o diretório inicial da conta do usuário sob a qual o kit de ferramentas foi instalado anteriormente.
