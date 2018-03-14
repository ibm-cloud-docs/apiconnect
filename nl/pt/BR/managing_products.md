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

# Gerenciando Produtos

Para obter detalhes das maneiras nas quais é possível gerenciar seus Produtos, veja a documentação do IBM&reg; Knowledge Center [Gerenciando seus produtos ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.apionprem.doc/task_product_management.html){:new_window}.

## Ciclo de vida do produto
{: #prod_lifecycle}

Ao gerenciar suas versões do Produto, você as move por uma série de
estados do ciclo de vida, inicialmente preparando uma versão rascunho do Produto para um
ambiente, até a publicação para tornar a versão do Produto disponível aos seus
desenvolvedores de aplicativos e a eventual desativação e arquivamento. A tabela e o
diagrama a seguir descrevem os diversos estados do ciclo de vida do Produto para uma
versão do Produto.

<table summary="" id="apic_004__table_lym_rxj_gv" class="defaultstyle"><caption class="style-scope doc-content">Tabela 1. Estados do ciclo de vida do produto API Management</caption>
<thead class="style-scope doc-content">
<tr class="style-scope doc-content doc-tr-even">
<th style="width: 11.25%" id="d3569e1968" class="thleft thbot style-scope doc-content">Estado</th>
<th style="width: 88.75%" id="d3569e1970" class="thleft thbot style-scope doc-content">Descrição</th>
</tr>
</thead>
<tbody class="style-scope doc-content">
<tr class="style-scope doc-content doc-tr-odd">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">Rascunho</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">O produto não está implementado e não está associado a um Catálogo do API Connect.</td>
</tr>
<tr class="style-scope doc-content doc-tr-even">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">Com Estágio Definido</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">Uma cópia imutável da versão do Produto foi implementada no
ambiente de destino. Com estágio definido é o estado inicial quando você define o estágio
a partir de um Produto rascunho. Quando um produto está no estado em estágios, ele ainda não está visível, ou pode ser assinado, por quaisquer desenvolvedores.</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">Publicado</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">A versão do Produto pode ser visualizada e assinada pelos
desenvolvedores ou pelas comunidades de destino.</td>
</tr>
<tr class="style-scope doc-content doc-tr-even">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">Reprovada</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">A versão do Produto pode ser visualizada somente pelos
desenvolvedores cujos aplicativos estão inscritos atualmente. Nenhuma nova assinatura do
Produto é possível.</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">Aposentado(a)</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">A versão do Produto não pode ser visualizada ou assinada e todas as
APIs associadas foram interrompidas. Uma versão de Produto obsoleta é exibida por padrão na
página Produtos na UI do API Manager.</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">Arquivado</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">A versão do Produto não pode ser visualizada ou assinada e todas as
APIs associadas foram interrompidas. A versão do Produto não é exibida por padrão na página Produtos na UI do API Manager.</td>
</tr>
</tbody>
</table>

### Fluxos do ciclo de vida do produto

O diagrama a seguir mostra os
estados possíveis do ciclo de vida para uma versão do Produto e as operações de
gerenciamento do Produto que movem uma versão do Produto de um estado do ciclo de vida
para outro; por exemplo, a operação Desativar move uma versão do Produto do
estado Publicado para o estado Obsoleto.

<img alt="Diagrama de estado do ciclo de vida para versão do Produto" src="images/apic_plan_lifecycle.png">


## Criando um produto
{: #create_product}

Crie um Produto para coletar um conjunto de APIs e Planos em uma oferta que você torna disponível aos seus desenvolvedores. Um Plano inclui configurações de limite de taxa que podem ser aplicadas no Plano como um todo, ou especificadas para cada operação em uma API. Por meio de Produtos e Planos, você tem maior controle sobre a quais APIs seus desenvolvedores têm acesso. Depois
de criar um produto, ele deve ser preparado. A preparação de um produto o move para um
estado ativo que permite chamar e testar as APIs incluídas nele. Quando um produto é
preparado, ele ainda não é visível a nenhum desenvolvedor.

**Dica**: assim como o uso do método descrito nesta tarefa, também é possível criar um Produto
ao criar uma API. Se
você criar uma API usando a interface da linha de comandos do Kit de ferramentas
do desenvolvedor, um Produto será criado automaticamente para você. Será possível então
mudar qualquer uma das configurações do Produto abrindo o novo Produto
na página
**Produtos** do API Designer.

Para criar um Produto usando o API Designer, conclua as etapas a
seguir:
1. Para abrir a interface com o usuário do API Designer, abra uma linha de comandos e
insira o comando a seguir:
```
apic edit
```
O API Designer é aberto no navegador padrão.

2. Na área de janela de navegação do API Designer, clique em
**Produtos**.
A guia Produtos é aberta.

3. Clique em **Incluir** e, em seguida, clique em **Novo Produto**.
A janela Incluir um novo produto é aberta.

4. Conclua os campos a seguir:
    - Título
    - Nome
    - Versão

5. Clique em **Incluir**.
A guia Design para o novo Produto é aberta.

6. **Opcional**:
insira uma descrição, contato, licença e termos de informações de serviço para o Produto na
seção **Informações**.

7. Na seção **Visibilidade**, especifique os usuários para os quais você deseja que o Produto esteja visível. É possível escolher **Público**, **Usuários
autenticados** ou **Customizado**. Se você selecionar **Customizado**, use o campo **Tipo a ser incluído** para procurar as organizações ou comunidades do desenvolvedor para as quais você deseja que os Planos no Produto estejam visíveis.

    **Nota:**
Para procurar organizações ou comunidades do desenvolvedor, o Produto deve estar no estado montado,
publicado ou descontinuado. Se
o Catálogo no qual ele é montado, publicado ou descontinuado não for um Catálogo de
ambiente de simulação, não será possível fazer outras mudanças no Produto enquanto ele
estiver em um desses estados. Para obter mais informações, veja [Ciclo de vida do produto](#prod_lifecycle).

8. Especifique os usuários que podem assinar o Produto. É possível escolher **Usuários Autenticados** ou **Customizado**. Se
você selecionar **Customizado**, use o campo **Tipo a ser
incluído** para procurar as organizações ou comunidades do desenvolvedor cujos
Planos você deseja assinar no Produto.

9. Na seção APIs, especifique as APIs que você deseja incluir no Produto.
    1. Clique no ícone **Incluir API**.
    2. Selecione as APIs que você deseja incluir, em seguida, clique em **Aplicar**. As APIs selecionadas são listadas.

10. Para tornar uma API disponível para desenvolvedores de aplicativos, você deverá incluí-la em um Plano. Para
incluir um ou mais Planos no Produto, clique no ícone **Incluir plano**.
    1. Expanda o novo Plano que foi criado. Se você já tiver incluído APIs em seu Produto, elas serão incluídas automaticamente.
    2. Renomeie seu Plano nos campos **Título** e **Nome** e, opcionalmente, inclua uma descrição.
    **Nota:** um Plano padrão é criado automaticamente e é possível incluir sua API nesse Plano se
você não deseja criar o seu próprio. No entanto, se decidir não usar o Plano Padrão, você deverá excluí-lo, pois um Produto não pode ser colocado em estágios se ele inclui quaisquer Planos que não incluem APIs.

11. Verifique se as APIs requeridas estão incluídas no Plano.
    1. Expanda o Plano para o qual você deseja incluir uma API.
    2. Nas APIs incluídas, assegure-se de que as caixas de seleção das APIs que você
precisa sejam marcadas. Se houver APIs já selecionadas e você não desejar que elas sejam incluídas no Plano que está sendo editado, limpe suas caixas de seleção.

12. **Opcional**:
inclua as informações de faturamento para o Plano. Para incluir informações de faturamento, deve-se estabelecer uma conta com um serviço de processamento de cartão de crédito para que seus clientes possam pagar com um cartão de crédito. Planos de faturamento mensais são faturadas na mesma data de cada mês.

13. **Opcional**:
se você deseja customizar quais operações de uma API são incluídas no Plano, passe o cursor
sobre a API que contém a operação. Clique
no ícone **Mostrar operações** e, em seguida, marque ou desmarque as
caixa de seleção para as operações que você deseja incluir ou excluir.

14. **Opcional**:
para incluir um limite de taxa no Plano, limpe a caixa de seleção **Ilimitado** e, em seguida,
especifique o limite de taxa que você deseja aplicar. Se a caixa de seleção **Impingir limite máximo** estiver selecionada, o Plano parará a chamada da API pelos aplicativos após atingir o limite de taxa, caso contrário, um aviso será apresentado.

    **Nota:** a aplicação de um limite de taxa no nível de Plano cria um limite de taxa padrão que se aplica a cada operação no Plano. Se
você precisar configurar limites de taxa específicos para operações específicas, deverá
configurar estes dentro das próprias operações e essa configuração substitui a
configuração no nível do Plano.

15. **Opcional**:
especifique se o seu Plano requer aprovação de assinatura. Se você deseja assinaturas
por desenvolvedores para requerer aprovação por meio da interface com o usuário do API
Manager, selecione **Requerer aprovação de assinatura**; caso
contrário, assegure-se de que a caixa de seleção esteja desmarcada.

16. **Opcional**:
inclua um limite de taxa em uma operação.
    1. Passe o cursor sobre a API que contém a operação, clique no ícone **Mostrar
operações**.
    2. Passe o cursor sobre a operação na qual deseja aplicar um limite de taxa. Clique no
ícone **Editar limite de taxa**.
    3. Assegure-se de que a caixa de seleção **Ilimitado** esteja
desmarcada e, em seguida, especifique o limite de taxa que você deseja aplicar. Se a caixa de seleção **Impingir limite máximo** estiver selecionada, o Plano parará a chamada da API pelos aplicativos após atingir o limite de taxa, caso contrário, um aviso será apresentado.

- Clique no ícone **Salvar** para salvar suas mudanças.

Você criou um Produto e especificou um conjunto de APIs e Planos em uma oferta que agora pode tornar disponível aos seus desenvolvedores.
Em seguida, monte seu Produto em um Catálogo. Para obter mais informações, veja [Montando um produto](#stage_product}).


## Colocando um produto em estágios
{: #stage_product}

Antes da publicação, prepare um Produto para criar uma versão específica desse Produto em um Catálogo. Quando um produto está no estado em estágios, ele ainda não está visível, ou pode ser assinado, por quaisquer desenvolvedores.

**Nota:** a UI do API Manager também inclui a capacidade de montar Produtos, no entanto, o método preferencial
para essas tarefas é usar a UI do API Designer, conforme descrito no procedimento a seguir.

1. Na área de janela de navegação do API Designer, clique em
**Produtos**.
A guia Produtos é aberta.

2. Clique no **Produto** com o qual você deseja trabalhar. Se você
tiver mais de uma versão do Produto, assegure-se de clicar na versão com a qual você
deseja trabalhar.

3. Clique no ícone **Publicar**.

4. Se o Catálogo no qual você deseja montar o Produto for mostrado na lista:
    1. Selecione o Catálogo que você requer. 
    2. Selecione **Somente montar (os produtos não
serão publicados)**, seguido por **Publicar**. Seu Produto foi colocado em estágios.

5. Se o Catálogo no qual você deseja montar o Produto não for mostrado na lista:
    1. Clique em **Incluir e gerenciar destinos**.
    2. Clique em **Incluir destino do {{site.data.keyword.Bluemix_notm}}**.
    3. Selecione a **Região** do {{site.data.keyword.Bluemix_short}}
na qual você deseja publicar.
    4. Selecione a **Organização** do
{{site.data.keyword.Bluemix_notm}} na qual você deseja publicar.
    5. Uma lista de Catálogos é exibida. Selecione o Catálogo no qual deseja publicar.
    6. Clique em **Avançar**.
    7. Se você tiver um aplicativo LoopBack que deseja publicar, selecione o App no qual
publicar.
Caso contrário, selecione **Nenhum**.
    8. Clique em **Salvar**.
    9. Clique em **Publicar** novamente e selecione o destino que você acabou de incluir.
    10. Selecione o Catálogo requerido
    11. Selecione **Somente estágio**.
    12. Clique em **Publicar**.

Seu Produto foi montado em um Catálogo. Para visualizar o estado do Produto no
Catálogo, abra a UI do API Manager, selecione a seção Painel na área de janela de
navegação e clique no Catálogo requerido. O Produto é mostrado com o estado
de Em estágio.

- Abra o **Painel** do {{site.data.keyword.Bluemix_notm}}. Você verá
o tile do aplicativo na seção Aplicativos.

Abra o API Manager para publicar seu produto em uma comunidade para
desenvolvedores de aplicativos para acessá-lo no Portal do desenvolvedor. Para obter mais informações, veja [Publicando um produto](#publish_proj}).


## Publicando um Produto
{: #publish_proj}

As APIs ficam visíveis e acessíveis aos desenvolvedores de aplicativo quando um plano é publicado.
Publicar um Produto o torna visível no **Catálogo** do {{site.data.keyword.Bluemix_short}}
e no Portal do Desenvolvedor integrado para os desenvolvedores de aplicativos
usarem.

### Pré-requisito
{: #prereq_publish_proj}

Deve-se preparar um Produto para que ele possa ser publicado. Para obter mais informações sobre a montagem de Produtos,
veja [Montando um produto](#stage_product).

Para publicar um Produto, conclua as etapas a seguir:

1. Na área de janela de navegação do API Manager, expanda a seção
**Catálogos** e selecione o Catálogo com o qual deseja trabalhar. A
guia Produtos do Catálogo é aberta e todos os Produtos disponíveis nesse catálogo são
exibidos. É possível selecionar quais estados são mostrados usando as caixas de seleção de filtro à direita da tela.

2. Ao lado da versão do Produto com a qual você deseja trabalhar, clique no
ícone **Gerenciar** e, em seguida, clique em
**Publicar**. A caixa de diálogo Editar visibilidade e assinantes é exibida.

3. Especifique as seguintes opções:
    - `Visível para`: é possível escolher **Usuários públicos**, **Usuários
autenticados** ou **Customizado**. Se você selecionar `Custom`, será possível usar o campo **Digite para incluir...** para procurar organizações ou comunidades para as quais você deseja que seu Produto esteja visível.
    - `Assinável por`: é possível escolher **Usuários autenticados** ou **Customizado**. Se você selecionar `Custom`, será possível usar o campo **Digite para incluir...** para procurar organizações ou comunidades para as quais você deseja que seu Produto esteja visível.

4. Clique em **Publicar**.
    Se a aprovação for necessária para publicar Produtos nesse Catálogo, uma solicitação
de aprovação será enviada e o Produto será movido para o estado Pendente; o Produto será
publicado quando a solicitação for aprovada. Se a aprovação não for necessária, a versão
do Produto será publicada imediatamente e movida para o estado Publicado.

Seu produto está no estado Publicado. Seu Produto foi publicado no Catálogo e
está disponível para as organizações ou comunidades especificadas. Os desenvolvedores
de aplicativos dentro dos grupos selecionados podem ver e usar as APIs no
Produto. Qualquer solicitação do desenvolvedor de aplicativos para usar seu Produto
é exibida na guia Aprovações no Catálogo de contenção, no qual é possível recusar ou
aceitar a solicitação.


## Publicando um Produto para Bluemix

Para ver seus Produtos na seção **Explorar APIs** do
Painel do
{{site.data.keyword.apiconnect_short}}, conclua
as etapas a seguir.

### Pré-requisito

Antes de começar, se você deseja publicar uma API REST implementada com
LoopBack, assegure-se de que tenha publicado o tempo de execução de seu app e de ter
preparado seu produto com o proxy de chamada apontando para o novo app. Para obter mais informações sobre como fazer isso, veja [Montando e publicando um aplicativo LoopBack](managing_apis.html#stage_publish_lb_app).

1. Na UI do API Manager, clique em **Incluir** > **Catálogo**. A janela **Incluir catálogo** é exibida.

2. Conclua os campos a seguir e, em seguida, clique em **Incluir**:
    - Nome da Exibição
    - Nome
	
3. Selecione o Catálogo criado.

4. Clique no ícone **Configurações**.

5. Clique em **Portal** e selecione uma das opções a seguir:
    - **IBM Developer Portal**. Se você selecionar essa opção, a URL
do portal será exibida.
    - **Outro**. Se você selecionar essa opção, digite a URL para o
portal que deseja usar.

6. Na seção Registro e convite do usuário, clique na seta **Registro
do usuário** e selecione **SAML**.

7. Na área de janela de navegação, clique no ícone **Desenvolvedores**.

8. Clique em **Incluir organização do IBM Cloud**.

9. Inclua seu endereço de e-mail do usuário do
{{site.data.keyword.Bluemix_short}} e clique em
**Incluir**.

10. Um convite é enviado para seu endereço de e-mail.

11. Clique no link do e-mail para aceitar o convite.
A UI do
{{site.data.keyword.Bluemix_notm}} é aberta.

12. Selecione sua organização do
{{site.data.keyword.Bluemix_notm}} e clique em
**Confirmar**.

13. Na UI do API Manager, clique no ícone **Produtos**.

14. Ao lado da versão do Produto com a qual você deseja trabalhar, clique no
ícone **Gerenciar** e, em seguida, clique em
**Publicar**. A caixa de diálogo Editar visibilidade e assinantes é exibida.

15. Especifique as seguintes opções:
    - **Visível para:** escolha **Customizado** e use o campo **Tipo para incluir...** para selecionar
sua organização do desenvolvedor e quaisquer outras que você deseja incluir.
    - **Assinável por:** escolha **Customizado** e use o campo **Tipo para incluir...** para selecionar
sua organização do desenvolvedor e quaisquer outras que você deseja incluir.

16. Clique em **Publicar**.

Se a aprovação for necessária para publicar Produtos nesse Catálogo, uma solicitação
de aprovação será enviada e o Produto será movido para o estado Pendente; o Produto será
publicado quando a solicitação for aprovada. Se a aprovação não for necessária, a versão
do Produto será publicada imediatamente e movida para o estado Publicado.

Seu produto é exibido na guia **Explorar APIs** do **Painel**
do {{site.data.keyword.apiconnect_short}}. Se você
clicar no link Produto, ele levará você para o Produto no Portal do desenvolvedor.
