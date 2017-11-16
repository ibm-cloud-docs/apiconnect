---
copyright:
  years: 2017
lastupdated: "2017-10-19"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Importando APIs

É possível usar um arquivo de definição do Swagger para incluir uma API REST.
{:shortdesc}

## Pré-requisito
{: #prereq_import_swagger}

Antes de iniciar, assegure-se de que o arquivo esteja em conformidade com a versão
2.0 da especificação Swagger. O formato do arquivo pode ser JSON ou YAML.

Para incluir uma API REST carregando um arquivo Swagger, conclua as etapas
a seguir:

1. Na área de janela de navegação da UI do API Manager, clique em
**Rascunhos**; em seguida, clique em
**APIs**.
A guia APIs é aberta.

2. Clique em **+ Incluir** e, em seguida, selecione **Swagger 2.0**
na seção **Importar**.
A janela **Importar API do Swagger** é aberta.

3. **Opcional**:
para fazer upload de um arquivo de seu sistema de arquivos local, clique em **Selecionar arquivo** e, em
seu sistema de arquivos, selecione o arquivo que você deseja usar. Os arquivos `.json`,
`.yml` e `.yaml` serão suportados se contiverem uma
definição válida do Swagger.

4. **Opcional**:
para fazer upload de um arquivo de uma URL, clique em **Ou importar de URL** e, em seguida, forneça
a URL correta no campo **URL** que é apresentado. Se a autenticação for necessária para
acessar a URL, forneça um nome de usuário e uma senha. Os arquivos `.json`,
`.yml` e `.yaml` serão suportados se contiverem uma
definição válida do Swagger.

5. Clique em **Importar**.
Uma nova definição de API REST é criada, incluindo operações de Caminhos e
HTTP.

Quando a definição de API tiver sido importada, ela será mostrada na lista de
definições de API na guia **APIs** da página **Rascunhos**.
Em seguida, é possível editar a definição de API como você faria com qualquer
outra definição de API REST.

## Importando APIs do IBM Integration Bus
{: #tut_import_iib_apic}

Com este tutorial, é possível importar APIs de REST que você cria com o IBM Integration Bus no {{site.data.keyword.apiconnect_full}}, que torna mais fácil gerenciar e publicá-las.
{: shortdesc}

Antes de iniciar, assegure-se de que o arquivo API de REST esteja em conformidade com a versão 2.0 da especificação Swagger. O formato do arquivo pode ser JSON ou YAML.

É possível usar o IBM Integration Bus para criar APIs de REST, que
são aplicativos especializados que podem ser usados para expor integrações como um serviço da web RESTful e
podem ser chamados por clientes HTTP. Depois de criar as APIs, é possível importá-las no {{site.data.keyword.apiconnect_short}}
para gerenciá-las e publicá-las.

A lista a seguir contém algumas vantagens de gerenciar suas APIs no {{site.data.keyword.apiconnect_short}}:
* É possível monitorar o número de chamadas à API.
* É possível controlar o número de chamadas à API.
* É possível manter várias versões para cada API.

Para obter mais benefícios, veja [Gerenciando APIs](managing_apis.html).

Para criar uma API de REST no IBM Integration Bus e importá-la
para o {{site.data.keyword.apiconnect_short}}, conclua as etapas
a seguir:
1. Crie a API de REST usando o IBM Integration Bus. Restrição: é possível criar uma API de REST somente com o IBM Integration Toolkit, que é fornecido com a versão instalada do IBM Integration Bus.
	1. Crie uma API de REST usando o IBM Integration
Toolkit. Para obter mais informações sobre como concluir as tarefas para criação de uma API de REST com o IBM Integration Bus, veja [Desenvolvendo soluções de integração usando APIs de REST ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SSMKHH_10.0.0/com.ibm.etools.mft.doc/bi12016_.htm){: new_window} no IBM Knowledge Center.
		
	2. Abra o assistente Criar uma API de REST selecionando **Arquivo** > **Novo** > **API de REST**.
		
	3. Insira um nome para a API REST. O nome especificado é usado como o nome do projeto no
IBM Integration Toolkit.
		
	4. Selecione um dos métodos a seguir para criar a API de REST e conclua o procedimento:
		
	**Do zero, usando o Editor de API de REST fornecido com o IBM Integration Toolkit**:
		1. Selecione **Criar uma API REST e defina recursos
e operações você mesmo**.
		2. Dê um clique em **Finalizar**. O Editor de API
de REST para a nova API de REST é aberto automaticamente e deve ser
usado para definir recursos, modelos e operações.
		
	**De um documento Swagger 2.0 existente**:
		1. Selecione **Importar recursos e operações definidos em um documento Swagger** e clique em
**Avançar**.
		2. Selecione o caminho para o documento Swagger que descreve os
recursos e as operações que você deseja na API de REST. É possível importar o documento Swagger do sistema de arquivos ou de um projeto
existente na área de trabalho. O arquivo é validado para uso em uma API REST. Se algum erro for encontrado enquanto o documento Swagger
selecionado é validado, esse erro de validação será exibido no início do assistente. Não será possível continuar se forem localizados erros de validação no
documento Swagger selecionado.
		3. Selecione **Concluir** para criar a API.
	5. Implemente os subfluxos para a sua API de REST, que são as operações REST que você deseja incluir.
2. Inclua o projeto API de REST em um arquivo broker archive (BAR) novo ou existente do IBM Integration Bus.
3. Implemente o arquivo BAR no IBM Integration Bus on Cloud.
	1. Efetue login no IBM Integration Bus on Cloud usando seu IBMid, se você ainda não tiver efetuado login. Inscreva-se para criar uma conta se você não tiver uma.
	2. Clique em **Incluir integração** > **Fazer upload do arquivo BAR**.
	3. Selecione o arquivo BAR que você criou para seu projeto API de REST. Dica: é possível encontrar o local de seu arquivo BAR clicando nele com o botão direito no IBM Integration Toolkit e visualizando suas propriedades.
	4. Selecione **Salvar**.
	5. Selecione **Atualizar lista** para atualizar a tela.
	6. Verifique se o arquivo BAR foi transferido por upload com sucesso, visualizando o Fluxo de integração da API para a API na janela *Integrações* do IBM Integration Bus on Cloud.
4. Inicie o fluxo de integração selecionando o ícone de início ![Captura de tela que mostra o ícone iniciar.](images/a_play_button.jpg " "). A API é iniciada e exibe um status de `Running`.
5. Selecione a integração na lista de integrações para visualizar informações sobre ela. A árvore no menu Conteúdo exibe a API de REST e os subfluxos que estão associados a ela. Também é possível visualizar informações nas outras seções. Na seção Terminais públicos, é possível
visualizar a URL pública que o IBM Integration Bus on Cloud designou
para o seu fluxo de integração. Selecione **Mostrar URL completa** para visualizar a URL completa dessa operação.
6. Copie a URL completa da operação para sua área de transferência. Ela será necessária ao você configurar a API para trabalhar com o {{site.data.keyword.apiconnect_short}}. Se
você ativou a Autenticação Básica, observe também o nome de usuário e a senha designados.

### Integrar o IBM Integration Bus com o API Connect.
{: #integrateiibapic}

1. Importe o arquivo Swagger que está associado ao projeto API de REST no IBM Integration Toolkit para o serviço {{site.data.keyword.apiconnect_short}}. 
	1. Efetue login no serviço {{site.data.keyword.apiconnect_short}} {{site.data.keyword.Bluemix_notm}}.
	2. Na área de janela de navegação da UI do API Manager, selecione **Rascunhos** > **APIs**. A guia APIs é aberta.
	3. Selecione **+ Incluir** > **Importar API de um arquivo ou URL**. A janela *Importar OpenAPI (Swagger)* é aberta.
	4. Para fazer upload do arquivo que você criou de seu sistema de arquivos local, selecione **Selecionar arquivo** e selecione o arquivo que foi criado com o IBM Integratio Bus. Os arquivos com as extensões `.json`, `.yml` e `.yaml` serão
suportados se contiverem uma definição de swagger válida. Certifique-se de que a opção para **Incluir um produto** está selecionada. Opcionalmente, é possível publicar o produto, selecionando
**Publicar este produto em um catálogo**.
	5. Clique em **Importar**. Uma nova definição de API REST é criada, incluindo operações de Caminhos e
HTTP. Dica: cancele a importação, atualize seu navegador e tente importar novamente, se demorar mais de 1 minuto para importar. Sua sessão pode ter expirado.
2. Associe a API importada no {{site.data.keyword.apiconnect_short}} à API no IBM Integration Bus on Cloud.
	1. Acesse o Painel do {{site.data.keyword.apiconnect_short}}.
	2. Selecione **Rascunhos** > **APIs**.
	3. Clique na API de REST que você importou.
	4. Selecione a guia Montar e selecione **Criar
conjunto** para incluir a política de proxy.
	5. Arraste a política de **proxy** para a nova política vazia para ativá-la.
	6. Cole a URL para a API que você copiou da seção Terminais públicos do IBM Integration Bus on Cloud.
	7. Se você ativou a Autenticação básica para sua API de REST, insira o nome do usuário e a senha que foram gerados no IBM Integration Bus on Cloud.
	8. Salve as configurações da API.
3. Teste a API.
	1. Na guia Montar de sua API, selecione o botão Teste ![Test button](images/a_play_button.jpg "Screen capture that shows the test button icon.").
	2. Selecione **Publicar produto novamente**.
	3. Selecione a operação.
	4. Insira os parâmetros necessários.
	5. Selecione **Chamar**.
	6. Verifique se você recebe a resposta esperada da API. 
	
Quando a definição da API é importada e integrada, é possível
gerenciar e controlar as APIs como é feito com qualquer outra definição
de API de REST. Para obter mais informações sore as APIs, veja [Gerenciando APIs](managing_apis.html).

## Publicando APIs criadas com o IBM App Connect Professional no IBM API Connect

Com este tutorial, é possível publicar e gerenciar APIs de REST que você cria com o IBM&reg; App Connect Professional com o {{site.data.keyword.apiconnect_full}}.

### Pré-requisito
{: #prereq_pub_api_appconn}

Você precisa de contas válidas para o IBM&reg; App Connect
Professional on Cloud e para o IBM API Connect&trade; no
Bluemix&reg; para concluir este tutorial. Assegure-se de que seu arquivo de API de REST esteja em conformidade com a versão 2.0 da especificação de Swagger. O formato do arquivo pode ser JSON ou YAML.

É possível usar o IBM&reg; App Connect Professional para criar APIs de
REST, que são aplicativos especializados que podem ser usados para expor integrações, como um serviço da web
RESTful e que podem ser chamados por clientes HTTP. Após criar as APIs, será possível publicar e gerenciá-las usando o {{site.data.keyword.apiconnect_short}}.
A lista a seguir contém algumas vantagens de gerenciar suas APIs no {{site.data.keyword.apiconnect_short}}:

- É possível monitorar o número de chamadas à API.
- É possível controlar o número de chamadas à API.
- É possível manter várias versões para cada API.

Para obter mais benefícios, veja [Gerenciando APIs](managing_apis.html).
Para criar uma API de REST no IBM&reg; App Connect Professional e
publicá-la no {{site.data.keyword.apiconnect_short}}, conclua as
etapas a seguir:

1. Crie a API de REST usando o IBM &reg; App Connect
Professional.
  - Efetue login no [App Connect Professional Web Management Console ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://appconnect.ibmcloud.com/professional/){:new_window} com seu IBMid. Para obter mais informações sobre como concluir as tarefas para criar uma API de REST com o IBM&reg; App Connect Professional Web Management Console, veja [Sobre configurações do console de gerenciamento ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS3LC4_7.5.2.0/com.ibm.wci.appliance.doc/About_the_WMC/consoleSettings.html){:new_window} no IBM&reg; Knowledge Center.
  - Selecione a guia Produção, se ela ainda não estiver selecionada.
  - Selecione **Repositório** > **Configurações** no painel de navegação.
  - Na tela Configurações de projeto, selecione o projeto que estiver publicando em {{site.data.keyword.apiconnect_short}}.  Os Detalhes de configuração do projeto que está sendo publicado são exibidos.
  - Selecione **Enviar push para API Management**. 
      **Dica**: o botão **Enviar por push para API Management** está ativo somente quando o projeto que você está importando tem um status de execução ou implementado. Selecione o botão reproduzir para iniciar o projeto, se o link não for exibido.
  - Na tela Enviar push para API Management, insira as informações a seguir para criar uma conexão com o sistema de gerenciamento de API.

  <table><caption>Tabela 1. Informações de conexão para publicação de API no API Connect</caption>
  <thead>
  <tr>
  <th>Nome do Campo</th>
  <th>Descrição</th>
  </tr>
  </thead>
  <tbody>
  <tr><td>Host</td>
  <td>Especifica o nome do host do Cluster de gerenciamento, Servidor ou Endereço da nuvem. Para {{site.data.keyword.Bluemix_short}}, esta entrada é provavelmente us.apiconnect.ibmcloud.com.</td>
  </tr>
  <tr>
  <td>Porta</td>
  <td>Especifica o número da porta que é necessário para se conectar ao Cluster de gerenciamento, Servidor ou Endereço de nuvem.</td>
  </tr>
  <tr><td>ID do usuário</td>
  <td>Especifica o nome do usuário de autenticação que é usado para acessar o Cluster de gerenciamento, o Servidor ou o Endereço de nuvem. Este é provavelmente o seu IBMid que você usa para efetuar login no {{site.data.keyword.Bluemix_short}}.</td>
  </tr>
  <tr><td>Password</td>
  <td>Especifica a senha de autenticação que é usada para acessar o Cluster de gerenciamento, o Servidor ou o Endereço de nuvem. Este é provavelmente sua senha do IBMid que você usa para efetuar login no
{{site.data.keyword.Bluemix_short}}.</td>
  </tr>
  </tbody>
  </table>

2. Selecione **Carregar organizações** para preencher a lista de organizações associadas ao seu ID e senha.

3. Selecione **Organizações** para associar o projeto a uma das organizações que estiverem disponíveis.

4. Selecione **Enviar push para APIM** e, em seguida, selecione **Ok**.

5. Selecione **Fechar** para fechar a janela.
Uma nova guia do navegador se abre em seu navegador padrão e exibe sua API.

Associe o IBM&reg; App Connect API ao {{site.data.keyword.apiconnect_short}}.

#### Importar definição de API do Swagger

Para importar o arquivo Swagger que está associado ao projeto API de REST no IBM&reg; App Connect para o serviço {{site.data.keyword.apiconnect_short}}, siga estas etapas:

1. Efetue login no serviço {{site.data.keyword.apiconnect_short}}Bluemix&reg;.

1.  Na barra de título da UI do API Manager, selecione **Navegar para** > **Rascunhos**.

2. Selecione **APIs** na barra de menus.
A guia APIs é aberta.

3. Selecione sua API importada para abrir o API Designer.

4. Selecione **Montar** na janela de navegação.
Uma lista de políticas é exibida na janela de navegação.

5. Selecione **Criar conjunto**, se necessário.

6. Inclua a política **Chamar** arrastando-a até seu conjunto na janela principal.

7. Selecione a política **Chamar** na janela principal para modificar suas definições de configuração.

8. Configure o host/basePath para o campo de URL com as informações a seguir:

- **hostname**: configuração que depende de sua instância da nuvem. Para obter mais informações sobre essa configuração, veja
[IBM App Connect Professional ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://provide.castiron.ibmcloud.com){:new_window}.

- **basepath**: caminho que você especifica na nota de Solicitação httpReceive na orquestração do App Connect Professional.

9. Inclua e salve seu nome do usuário e senha do IBMid nos detalhes de autenticação básica de Http usados para o App Connect Professional.

#### Testar a API

Para testar a API, siga estas etapas:

1. Na guia Montar de sua API, selecione o botão Teste <img alt="Screen capture that shows the test button icon" src="images/a_play_button.jpg" />.
2. Selecione **Publicar produto novamente**.
3. Selecione a operação.
4.  Insira os parâmetros necessários.
5. Selecione **Chamar**.
6. Verifique se você recebe a resposta esperada da API.

Quando a definição da API é importada e integrada, é possível
gerenciar e controlar as APIs como é feito com qualquer outra definição
de API de REST. Para obter mais informações sore as APIs, veja [Gerenciando APIs](managing_apis.html).


