---

copyright:
  years: 2018
lastupdated: "2019-01-17"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal

subcollection: apiconnect

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Gerenciando APIs
{: #managing_apis}

É possível usar o API Connect para gerenciar APIs no {{site.data.keyword.Bluemix}}, quer elas estejam no {{site.data.keyword.Bluemix_notm}} ou mantidas fora do {{site.data.keyword.Bluemix_notm}}. Gerenciar suas APIs permite controlar o uso, aumentar a adoção e rastrear as estatísticas.

Se você é um cliente, é possível gerenciar como ela é usada na UI do API Manager depois que um desenvolvedor cria uma API e envia por push o produto para o {{site.data.keyword.Bluemix_notm}}. Os tópicos a seguir descrevem como criar e gerenciar produtos no {{site.data.keyword.apiconnect_short}}.

## Expondo APIs no local por meio de um Secure Gateway
{: #expose_apis_sec_gate_managing_apis}

É possível criar um gateway seguro para expor as APIs no local de forma segura para o {{site.data.keyword.apiconnect_full}}.

Quando você cria um gateway seguro e, em seguida, fornece um endereço para o `<host>:<port>` do Cloud ou do cliente, você integra os recursos do serviço {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.SecureGateway}} ao {{site.data.keyword.apiconnect_short}}. Isso significa que você tem uma maneira segura de acessar suas APIs no local do {{site.data.keyword.apiconnect_short}} por meio de uma passagem segura. Você cria efetivamente um túnel para {{site.data.keyword.apiconnect_short}} em um ambiente público sem expor seus dados no local. Basta criar e configurar o serviço Secure Gateway no IBM Cloud e fornecer um endereço para ele em uma API.

Para obter mais informações sobre o serviço {{site.data.keyword.SecureGateway}} e como configurá-lo, consulte [Sobre o {{site.data.keyword.SecureGateway}}![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.ibm.com/docs/services/SecureGateway?topic=index#getting-started-with-sg){: #new_window}.

### Usando o Secure Gateway com suas APIs
{: #using_sec_gate_apis_managing_apis notoc}

Quando você tiver configurado o gateway, será possível usá-lo com suas APIs.
{:shortdesc}

Para usar o seu gateway seguro com as APIs, conclua as etapas a seguir.
1. Crie sua API e Produto, conforme descrito nas etapas a seguir.
  - Clique em **Navegar para** <img src="images/navigate_to_icon.png" alt="ícone Navegar para" /> > **Rascunhos** > **APIs** > **Incluir**.
  - Selecione o tipo de API que você deseja criar.
  - Selecione ou clique em **Incluir um produto**. **IMPORTANTE**: não publique o Produto ainda.
  - Clique em **Criar API**.
  A API é exibida na visualização `Design`.
  
2. Clique em **Montar**.

3. Clique na política **invoke** para
abrir a paleta
**invoke**.
**RESTRIÇÃO**: comutadores lógicos, por exemplo, `Switch`, `Operation Switch` e
`If`, não podem ser usados com as APIs que usam um Secure Gateway.

4. **Não** marque a caixa de seleção **Acessar URL por meio do Secure Gateway**.
**IMPORTANTE**: essa caixa de seleção é para um recurso descontinuado que não é suportado para produção e está sujeito à remoção a qualquer momento. Em vez disso, você fornecerá um endereço para a URL do Secure Gateway diretamente, sem marcar essa caixa de seleção.

5. No campo URL, atualize o `target-url` com o nome de host da nuvem e o número da porta, por exemplo:
```
target-url: cap-sg-prd-5.securegateway.appdomain.cloud:18579
```

6. Clique em **Salvar** <img src="images/icon_save.png" alt="ícone Salvar" />.

7. Clique em **Todas as APIs** > **Produtos** e selecione o Produto que você criou anteriormente.

8. Clique em **Publicar** para montar o produto em um catálogo selecionado.

9. Selecione o Catálogo que você deseja usar.

10. Selecione o Produto montado.

11. Clique em **Publicar**.

Você expôs com segurança a API no local para
{{site.data.keyword.apiconnect_short}}. Em seguida, teste a API do {{site.data.keyword.SecureGateway}}.

### Testando a API do Secure Gateway
{: test_sec_gate_managing_apis notoc}

Após o fornecimento de um endereço para o {{site.data.keyword.SecureGateway}} em uma API, será possível testar a API para garantir que o gateway esteja funcionando e produza a resposta correta.

Para testar uma API usando o Secure Gateway, conclua as etapas a seguir:

1. Clique em <img alt="ícone Navegar para" src="images/navigate_to_icon.png" /> > **Rascunhos** > **APIs**
**<Sua API>** > **Montar**.

2. Clique no ícone **Teste** <img src="images/test_icon.png" alt="ícone de teste"/>.

3. Selecione um catálogo para testar de dentro da lista fornecida.

4. Certifique-se de que a URL forneça um endereço para o `<cloud_host>:<port>` correto do Secure Gateway e que o destino do serviço Secure Gateway tenha sido configurado corretamente, conforme descrito na documentação do [{{site.data.keyword.SecureGateway}}![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.ibm.com/docs/services/SecureGateway?topic=index#getting-started-with-sg){: #new_window}.

5. Escolha um Produto existente na lista que é fornecida, em
seguida, clique em **Publicar produto
novamente**.
   **Importante** se esse Produto já estiver publicado em um Catálogo, ele será publicado novamente
com o novo gateway.

6. **Opcional**:
forneça um nome para criar um novo Produto, em seguida, clique em **Criar e
publicar**.

7. Clique em **Avançar**.

8. Selecione uma operação para chamar a partir da lista fornecida.

9. Clique em **Chamar**.

Os resultados do teste são
exibidos.

## Preparando e publicando um aplicativo LoopBack
{: #stage_publish_lb_app_managing_apis}

1. Na área de janela de navegação do API Designer, clique em
**Produtos**.
A guia Produtos é aberta.

2. Selecione a versão do Produto, assegure-se de clicar na versão com a qual você deseja trabalhar.

3. Para publicar o tempo de execução no
{{site.data.keyword.Bluemix_notm}}, clique em
**Publicar**.

4. Clique em **Incluir e gerenciar destinos** > **Incluir destino do IBM Cloud**.

5. Selecione a **Região** do {{site.data.keyword.Bluemix_notm}} que você deseja publicar e assinar.

6. Selecione a **Organização** do {{site.data.keyword.Bluemix_notm}} na qual você deseja publicar.

7.  Uma lista de Catálogos é exibida. Selecione o Catálogo no qual deseja publicar.

8.  Clique em **Avançar**.

9. Selecione o aplicativo LoopBack que você deseja publicar.
Se esta for a primeira vez que você está implementando o tempo de execução no
{{site.data.keyword.Bluemix_notm}}, inclua um
nome e clique no ícone **Incluir**.

10.  Clique em **Salvar**.

11.  Clique em **Publicar** novamente e selecione **Publicar
aplicativo**.

12.  Clique em **Publicar**.

13. Na linha de comandos, a URL de destino e o perfil tls de chamada da API são
especificados para a API.
Tome nota dessas informações. O perfil tls de chamada da API
é sempre `client:Loopback-client`, mas é possível recuperar a URL de
destino da API conforme descrito na etapa a seguir.
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

14. Na UI do API Designer, conclua as etapas a seguir:
    1. Clique em **APIs**.
    2. Selecione a API.
    3. Clique em **Montar**.
    4. No editor Montar, clique no ícone **Políticas de filtro**.
    5. Selecione **Políticas de gateway do DataPower**.
    6. Clique em **Salvar** para salvar a API.

15.  Em seguida, você precisa publicar na API Manager. Clique em **Publicar**.
    1. Selecione **Publicar aplicativo** e escolha uma das opções a seguir:
	    - **Substituir app existente**: se você tiver um aplicativo publicado, selecione essa opção para sobrescrever o app existente.
        - **Como um app novo (usando a rota existente)**: selecione esta opção para criar um novo app e forneça um nome para ele no campo **Novo app**. O serviço não é interrompido.

    2. Selecione as opções a seguir:
	    - Preparar ou publicar produtos
        - Selecionar produtos específicos
        - _seu produto_
 
    3. Clique em **Publicar**.

Para testar se a publicação funcionou, conclua as etapas a seguir:

1. Assegure-se de que o app
{{site.data.keyword.Bluemix_notm}} esteja em
execução.

2. Abra uma janela do navegador e navegue até a URL da API.
O aplicativo é seguro com a validação do cliente. Se você não fornecer o
certificado de cliente correto, ele resultará em erro (isso é esperado).

3. Navegue até a URL exposta do
{{site.data.keyword.apiconnect_short}}.
Por exemplo:
```
https://<domain>/<Bluemix org>-<Bluemix space>/<Catalog identifier>/api/notes
```
Uma resposta 200 é exibida.

## Configurando um Catálogo
{: #config_cat_managing_apis}

É possível criar e configurar seus Catálogos do API Manager. Os catálogos são úteis para
separar Produtos e APIs para teste antes de torná-los disponíveis para Organizações do desenvolvedor.
Ao configurar um Catálogo, também é possível configurar a marca customizada para que você
não tenha que usar a URL da API padrão fornecida pelo API Manager.

Conclua as etapas a seguir para criar seu Catálogo:

1. Clique em **Navegar para** <img alt="Ícone Navegar para" src="images/navigate_to_icon.png"> > **Painel**.

2. Clique em **+ Incluir** > **Catálogo**.
A janela **Incluir catálogo** é exibida.

3.  Insira o nome de seu novo Catálogo no campo **Nome de exibição**.

4. Insira o texto desejado para formar o segmento do Catálogo da URL no campo
**Nome**.
**Nota:** o campo **Nome** pode conter somente caracteres alfanuméricos minúsculos (a-z
e 0-9) ou caracteres de hífen (-). Um hífen
não pode ser usado como o primeiro ou último caractere no nome.

5. Clique em **Incluir**. Seu Catálogo é criado e exibido no painel.

6. Para configurar o Catálogo, clique no nome do Catálogo e, em seguida, clique em **Configurações** > **Informações** e continue com as etapas a seguir:
  1. Se o novo Catálogo for um de desenvolvimento, selecione **Modo de desenvolvimento**.
Se você selecionar o modo de desenvolvimento, as ações de preparação e publicação serão forçadas, ou seja,
se você publicar novamente um Produto publicado anteriormente, ele será sobrescrito sem aviso. Se forem localizados
conflitos, eles serão resolvidos automaticamente pelo sistema. Ações de cancelamento de publicação acontecem automaticamente.
**Nota:** as caixas de aprovação não são exibidas para catálogos de desenvolvimento. Não é possível ativar o processo de
aprovação para ciclos de vida.
  2. Se você desejar ativar a assinatura automática para o Catálogo, selecione
**Assinatura automática**.
Ativar a assinatura automática facilita o teste de suas APIs porque um aplicativo de teste é usado com um identificador de cliente e um segredo do cliente fornecidos previamente, que são inscritos automaticamente em todos os Planos no Catálogo, portanto, não é necessário especificar um plano ou um aplicativo ao testar.**Nota:** a assinatura automática está disponível somente para um Catálogo de desenvolvimento.
  3. Se o Catálogo for o de preparação padrão, selecione **Padrão**. Em seguida, as chamadas para as APIs publicadas no Catálogo podem usar uma URL mais curta que não inclui o nome do Catálogo **Nota:** só é possível selecionar **Padrão** para um Catálogo.
  4. **Opcional**: clique em **Terminais** e preencha os campos a seguir:
        - **URL de gateway customizada**: no campo de texto	URL de Gateway customizada, insira uma URL. Você usará a URL do gateway customizado se desejar
obter a marca customizada de URLs para APIs implementadas no {{site.data.keyword.apiconnect_short}}, em vez de usar a URL padrão
gerada pelo API Manager.
        Por padrão, a URL do gateway do {{site.data.keyword.apiconnect_short}}
possui o formato a
seguir:
        ```
        https://gateway_cluster_hostname/organization_name/Catalog_name
        ```
        No entanto,
é possível substituir o padrão especificando uma URL que seja mais apropriada para sua empresa, por
exemplo, `https://api.mycompany.com`. Todos os terminais de API que forem exibidos no
Portal do Desenvolvedor irão então refletir a URL especificada.
        **Notas:**
		    - Deve-se configurar uma entrada DNS que mapeie seu nome de host e domínio customizados para a URL de gateway
padrão.
		    - Para que os terminais de uma API reflitam sua URL de gateway customizada, deve-se configurar a API para ser
aplicada pelo gateway do API Connect. Para obter mais informações, veja [Especificando um host alternativo para uma API ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){: #new_window}.
		    - Assegure-se de que a mesma URL de gateway customizada não seja aplicada a múltiplos
Catálogos porque o comportamento nesse cenário é indefinido.
	        **DICA**: ao chamar a API, também é possível configurar o cabeçalho de host HTTP na solicitação de API para o valor especificado no campo URL de gateway customizada.

	    - **URL de API customizada**: no campo de texto	URL de API customizada, insira a URL. Você usará a URL da API customizada para especificar a URL
para APIs implementadas em um gateway de terceiro.

	    A URL da API customizada representa o terminal pelo qual a API é conhecida externamente, isto é, o
terminal publicado no Portal do Desenvolvedor e usado por um desenvolvedor de aplicativos para chamar ou
anunciar a API.

	    Se você estiver usando um gateway de terceiros ou um balanceador de carga externo
nesse Catálogo, forneça a URL nesse campo. Todos os terminais de API que forem exibidos no Portal do Desenvolvedor irão então refletir a
URL especificada. Esses terminais existem no gateway ou no balanceador de carga de terceiro e projetam um
endereço virtual, exposto a consumidores de API, que é mapeado para os terminais de proxy de API ou de conjunto de API
no gateway. Os terminais derivados da URL da API customizada são geralmente publicados nos
portais do desenvolvedor de produção para anunciar o endereço da API.

	    **Nota:** se você especificar uma URL de API customizada para um catálogo, ela terá precedência sobre qualquer nome de host que for especificado quando você configurar a API. Para obter mais informações, veja [Especificando um host alternativo para uma API ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){: #new_window}.

	    - **Nome do host para chamadas API do Portal do Desenvolvedor**: na área de janela	Terminal de API da porta, insira um nome de host para chamadas API do Portal do Desenvolvedor. O nome do
host que for inserido pode ser o nome do host de seu serviço de gerenciamento. Para acessar a API do
Portal do Desenvolvedor dentro do contexto de um Portal do Desenvolvedor, deve-se configurar o nome do host de base para as
chamadas API do Portal do Desenvolvedor. Essa ação permite que o API Manager
mapeie seu nome de host para a organização do provedor e o Catálogo das chamadas de API do
Portal do Desenvolvedor, em vez de requerer que você consulte e o inclua em suas chamadas.

7. Clique no ícone **Salvar**.

## Particionando um Catálogo
{: #part_cat_managing_apis}

Para usar o recurso de organização no
{{site.data.keyword.apiconnect_short}},
deve-se ativar Espaços em qualquer Catálogo no qual você requeira recursos de organização.

Para ativar Espaços em um Catálogo, conclua as etapas a seguir:
1. No Painel da UI do API Manager, selecione o Catálogo com o qual deseja trabalhar.

2. Clique em **Configurações** > **Visão geral** e clique no controle da régua de controle **Espaços**.

3. Na janela **Ativar espaços**, clique em **Ativar** e, em seguida, clique no ícone **Salvar** <img src="images/icon_save.png" alt="Ícone Salvar"/>.
Um link **Gerenciar espaços** é exibido abaixo da régua de
controle **Espaços** e um link **Espaços** é
incluído na área de janela de navegação. É possível gerenciar seus Espaços clicando em um
desses links.

Os Espaços são ativados para seu catálogo e um Espaço padrão, chamado Novo Espaço
é criado.

Para obter mais informações sobre o uso de organização, veja os tópicos do Knowledge Center, [Usando a organização no IBM API Connect ![External link icon](../icons/launch-glyph.svg "External link icon")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.apionprem.doc/capic_syndication_using.html){: #new_window}.

## Configurando um Portal do desenvolvedor
{: #config_dev_portal_managing_apis}

Um Portal do desenvolvedor é o local em que seus planos são
publicadas para que
os desenvolvedores de aplicativos acessem e usem.

É possível construir um Portal do desenvolvedor customizado para uso dos
desenvolvedores de aplicativos. Você tem controle administrativo total sobre aparência,
conteúdo, configurações do usuário e definições de configuração.

Além de permitir que os desenvolvedores de aplicativos localizem e usem APIs,
o Portal do desenvolvedor fornece mais recursos, como fóruns, blogs, comentários,
classificações e uma UI do swagger para APIs.

1. Na UI do API Manager, selecione o Catálogo com o qual deseja trabalhar.

2. Selecione a guia **Configurações**.

3. Clique em **Portal**.

4. Na seção **Configuração do portal**, selecione **IBM
Developer Portal**. A URL do portal é exibida.

5. Clique em **Salvar**. É enviado a você um e-mail que contém um link de login único para o usuário
administrador da web do Portal do desenvolvedor.

6. Clique no link que é enviado no e-mail e siga as instruções para reconfigurar sua
senha.

O Portal do desenvolvedor está configurado. É possível localizar a URL para o
Portal do desenvolvedor na linha de assunto do e-mail que você recebeu. Também é possível localizar a URL na UI do API Manager
clicando em **Portal** > **Configurações**.

Para obter mais informações sobre as tarefas que podem ser concluídas no Portal do Desenvolvedor, veja os
tópicos do IBM Knowledge Center sobre o [Portal do Desenvolvedor ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.devportal.doc/capim_devportal_overview.html){: #new_window}.

## Configurando permissões para funções
{: #config_permissions_roles_managing_apis}

Para configurar as Permissões para as funções no API Manager, conclua as
etapas a seguir.

1. No **Painel** do API Manager, clique no Catálogo com o qual você
deseja trabalhar.

2. Clique em **Configurações** > **Permissões**.
As permissões de gerenciamento do produto às quais é possível designar funções são exibidas:
  - **Montar**: permitir montagem de Produtos no Catálogo.
  - **Visualizar**: permitir visualização e listagem de Produtos no catálogo.
  - **Gerenciar**: permitir o gerenciamento do ciclo de vida do Produto (publicação, descontinuação, desativação e arquivamento).
  - **Aprovar**: permitir aprovações para mudanças de estado do ciclo de vida do Produto.
**Nota:** a aprovação para mudanças de estado do ciclo de vida do Produto é desativada para todos os Catálogos de desenvolvimento.

3. Para incluir uma função nas permissões **Montar**, **Visualizar** ou
**Gerenciar**, clique no ícone **+** correspondente.
A lista a seguir mostra as funções disponíveis padrão:
  - Administrador
  - Gerente de produto
  - Desenvolvedor de API
  - Publicador
A função Proprietário tem todas as permissões.

4. Ative as aprovações para as mudanças de estado do ciclo de vida do produto marcando as caixas de seleção necessárias e,
em seguida, clicando no ícone **+** correspondente para designar as funções que possuem
permissão para aprovar uma mudança de estado do ciclo de vida.
As mudanças de estado do ciclo de vida selecionadas são aquelas às quais você deseja aplicar aprovação.
Por exemplo, se você selecionar Publicar, mas deixar as outras limpas, a aprovação será necessária quando alguém
tentar publicar um produto, mas nenhuma aprovação será necessária para nenhuma das outras mudanças de estado do
ciclo de vida.
5. Para designar as funções que têm permissão para gerenciar políticas definidas
pelo usuário, clique no ícone **+** na seção **Gerenciamento
de política**.
As permissões de gerenciamento de política são exibidas, permitindo a designação de funções, conforme
necessário.
6. Clique no ícone **Salvar**.
