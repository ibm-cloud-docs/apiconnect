---

copyright:
  years: 2017
lastupdated: "2017-09-14"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal

subcollection: apiconnect

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Sobre o IBM API Connect
{: #about_apic_overview}

Use o serviço do
{{site.data.keyword.apiconnect_full}} para
criar rapidamente APIs e microsserviços com base nos tempos de Node.js e Java. Depois que eles são criados, é possível
gerenciar suas APIs com controles de nível de negócios configurando diferentes níveis de segurança, visibilidade,
planos de faturamento e limites de taxa enquanto as APIs são compartilhadas com os desenvolvedores de aplicativos. O serviço do
{{site.data.keyword.apiconnect_short}} também
fornece a você as ferramentas para transformar e ampliar seus negócios com insights por
meio de análises detalhadas com procuras filtradas estruturadas.

<object height="315" type="application/x-shockwave-flash" width="560"
data="https://www.youtube.com/v/lmxyiNMER5Y?version=3&amp;hl=en_US">
<desc>Este vídeo fornece uma visão geral do serviço {{site.data.keyword.apiconnect_short}}</desc>
<param name="movie" value="https://www.youtube.com/v/lmxyiNMER5Y?version=3&amp;hl=en_US"/>
<param name="allowFullScreen" value="true"/>
<param name="allowscriptaccess" value="always"/>
<param name="scale" value="noScale"/>
</object>

## Criação da API
{: #creation_apic_overview}

Com o
{{site.data.keyword.apiconnect_short}}, é
possível importar APIs das definições do swagger ou criar APIs usando uma URL de proxy ou
montando dados a partir de origens de dados HTTP. Além disso, o
{{site.data.keyword.apiconnect_short}} suporta
criação e teste de APIs off-line. Integrado com o kit de ferramentas do desenvolvedor
está um microgateway que permite conectar-se a origens de dados backend, como um
banco de dados SQL e executar operações baseadas em criação, leitura, atualização e exclusão.

As APIs são criadas dentro do kit de ferramentas do desenvolvedor. O kit de
ferramentas do desenvolvedor inclui uma CLI e a interface gráfica com o usuário do API
Designer. Para acessar o kit de ferramentas do desenvolvedor, você precisa fazer download e
instalá-lo a partir de npm.
Ao instalar o kit de ferramentas, você começa criando um projeto LoopBack. O
diagrama a seguir ilustra o que está contido em um projeto LoopBack.

- **Projeto LoopBack**: o projeto LoopBack contém o aplicativo LoopBack e o Produto de API.

- **Aplicativo LoopBack**: no aplicativo Loopback está o terminal de API que fornece acesso à sua origem de dados,
recurso de negócios ou serviço de nuvem.

- **Produto**: o Produto é a unidade que permite publicar as APIs. Um Produto contém um Plano e um
Plano contém a API que chama o terminal de API quando é chamado.

O diagrama a seguir demonstra onde o aplicativo LoopBack, a API e o Produto são
implementados para depois serem publicados a partir da CLI ou da UI do kit de ferramentas do
desenvolvedor.

<img src="images/loopback_project.png" alt="Diagram to show what is contained within a LoopBack project"/>

- **Tempo de execução do {{site.data.keyword.Bluemix_short}}**:
o app LoopBack é implementado no tempo de execução do {{site.data.keyword.Bluemix_short}} de sua escolha.

- **Gateway**: a API é implementada no gateway.

**API Manager**: o produto é implementado no API Manager no qual é possível especificar como ele é usado.

<img src="images/Deployed.png" alt="Diagram to show where the LoopBack app, API, and product are deployed to."/>

Para obter mais informações sobre as tarefas necessárias para criar APIs, veja [Criando APIs](/docs/services/apiconnect?topic=apiconnect-creating_apis).

## Visão geral do gerenciamento de API

Após a montagem e a publicação de um produto, é possível abrir o API Manager para gerenciar a segurança, os limites
de taxa, as políticas e as informações de faturamento e, em seguida, publicar o produto em um Portal do Desenvolvedor.

Conforme exibido no diagrama a seguir, um produto contém um plano com uma ou mais APIs.

<img src="images/Product.png" alt="diagram to show what is contained within a Product"/>

### Plans
{: #plans_apic_overview}

Para tornar uma API disponível para um cliente, ela deverá ser incluída em um Plano. Os
planos são usados para diferenciar entre diferentes ofertas. Os planos podem compartilhar APIs mas, se a aprovação de assinatura é requerida, depende do Plano em si. Além
disso, é possível impor limites de taxa por meio de Planos ou de operações nas APIs de um
Plano que substituam o limite de taxa do Plano.

Os planos também podem especificar os custos de faturamento para os clientes que usam os seus produtos. Por exemplo, é possível
definir três planos diferentes para um único produto. Cada plano pode ter um custo de assinatura diferente e um limite
de taxa diferente que se destinam a diferentes clientes.  

### Produtos
{: #products_apic_overview}

Planos e APIs são agrupados em Produtos. Por meio de Produtos, é possível gerenciar a disponibilidade e visibilidade de APIs e Planos. Use
o API Designer para criar, editar e preparar seu Produto. Use o
API Manager para gerenciar o ciclo de vida de seu Produto.

O diagrama a seguir demonstra como Produtos, Planos e APIs estão relacionados uns aos outros. Observe
que, como os Planos pertencem a um Produto somente, eles podem possuir APIs diferentes
para outros Planos dentro do mesmo Produto e podem compartilhar APIs com Planos de
qualquer Produto. Figura para mostrar a hierarquia de Produtos, Planos e APIs. <img src="images/plan_product_hierarchy.png" alt="Figure to show the hierarchy of Products, Plans, and APIs."/>

É possível criar Planos somente dentro de Produtos, e esses Produtos depois
são publicados em um Catálogo. Um
gerenciador de ciclo de vida então pode controlar a disponibilidade e visibilidade de
APIs e Planos por meio do API Manager. Com o Portal do desenvolvedor, o cliente é então
capaz de assinar um dos Planos que está disponível para ele, conforme determinado no API
Manager. Se for um plano com faturamento, o cliente deverá fornecer informações de cartão de crédito ao assiná-lo. O usuário pode assinar somente um Plano de um Produto específico. Múltiplos
planos dentro de um único produto são úteis, pois eles podem cumprir propósitos semelhantes, mas com diferentes níveis
de desempenho e custo. Por
exemplo, você poderá ter um "Plano de demo", que torna uma única API disponível e um
"Plano completo", que torna várias disponíveis.

Assim como controlar quais APIs um cliente pode usar, Planos diferentes podem ser usados para implementar limites de taxa. Um limite de taxa pode ser implementado como uma taxa padrão em um Plano inteiro, ou para operações específicas de uma API nesse Plano, isentando-as do limite da taxa do Plano. Planos diferentes podem ter limites de taxa diferentes, entre as operações e para o limite geral. Isso é útil para fornecer diferentes níveis de serviço aos clientes. Por
exemplo, um "Plano demo" pode impor um limite de taxa de 10 chamadas por minuto,
enquanto um "Plano completo" pode permitir até 1000 chamadas por minuto.

Finalmente, planos diferentes podem ser usados para designar um custo de faturamento. Um plano pode ser configurado como
um plano grátis ou como um plano com faturamento. Planos com faturamento podem ser usados com limites de taxa para
configurar diferentes níveis de serviço para os clientes. Por exemplo, um "plano demo" pode impor um limite de taxa
de 10 chamadas por minuto por um custo de US$ 5 por mês, enquanto um "plano completo" pode permitir até 1.000 chamadas
por minuto por um custo de US$ 20 por mês.

**Nota:** a aplicação de um limite de taxa no nível de Plano cria um limite de taxa padrão que se aplica a cada operação no Plano. Se
você precisar configurar limites de taxa específicos para operações específicas, deverá
configurar estes dentro das próprias operações e essa configuração substitui a
configuração no nível do Plano.

O IBM API Connect também suporta a implementação de diversas versões de Produtos. É possível escolher números de versão e utilizá-los para ajudar no desenvolvimento de seus Produtos e Planos.

**Nota:** a versão para um Produto é distinta da versão de quaisquer APIs que estejam contidas nos Planos associados. Planos em si não podem ter sua própria versão, eles usam a versão de seu Produto pai.

Para obter mais informações sobre as tarefas necessárias para gerenciar APIs, veja [Gerenciando APIs](/docs/services/apiconnect?topic=apiconnect-managing_apis).

### Catalogs
{: #catalogs_apic_overview}

Os produtos devem ser montados em um Catálogo e, em seguida, publicados nas
organizações do desenvolvedor para se tornarem disponíveis aos desenvolvedores de
aplicativos. No {{site.data.keyword.apiconnect_short}}, é
possível criar diversos Catálogos. Os catálogos são úteis para
separar Produtos e APIs para teste antes de torná-los disponíveis para Organizações do desenvolvedor.

Um Catálogo é um destino de preparação e se comporta como uma partição lógica
do gateway e do Portal do Desenvolvedor. A URL para chamadas de API e o Portal do
Desenvolvedor são específicos de um determinado Catálogo. Em uma configuração típica, uma
organização do provedor da API usa um Catálogo de desenvolvimento para testar APIs em
desenvolvimento e um Catálogo de produção para hospedar APIs que estão prontos para uso
total. Uma abordagem comum é ter uma nuvem de desenvolvimento com um Catálogo de
desenvolvimento, alguns Catálogos de teste e uma nuvem de produção que possa ter seu
próprio Catálogo de teste.

#### Configurações do catálogo
{: #cat_set_apic_overview}

É possível aplicar as seguintes configurações a um catálogo:

- **Desenvolvimento**: por padrão, um Catálogo de desenvolvimento é fornecido para você. Um Catálogo de
desenvolvimento deve ser usado apenas para propósitos de teste. Em um Catálogo de desenvolvimento, as ações de preparação e publicação
serão forçadas, ou seja, se você publicar novamente um Produto publicado anteriormente,
ele será sobrescrito sem aviso. Se forem localizados
conflitos, eles serão resolvidos automaticamente pelo sistema. Ações de cancelamento de publicação acontecem automaticamente. Ao usar a
ferramenta de teste em um Catálogo de desenvolvimento, qualquer Produto que você testar
será forçado e sobrescreverá os Produtos montados e publicados mesmo se as operações
estiverem sendo usadas no Portal do Desenvolvedor. Um Portal do Desenvolvedor criado a
partir de um Catálogo de desenvolvimento deve ser usado da mesma maneira, ou seja, para
propósitos de teste apenas e não para casos reais.

- **Assinatura automática**: se você deseja ativar a assinatura automática para um Catálogo, o teste das APIs na interface com o usuário do API Manager é mais fácil porque um aplicativo de teste é usado, com um ID de cliente e um segredo do cliente previamente fornecidos, que é inscrito automaticamente em todos os Planos no Catálogo, então você não precisa especificar um plano ou um aplicativo durante o teste. O aplicativo de teste não está sujeito a limites de taxa. A assinatura
automática está disponível somente para um Catálogo de desenvolvimento.

- **Padrão**: é possível configurar um de seus Catálogos para ser o Catálogo padrão. Então, as
chamadas das APIs que forem publicadas nesse Catálogo poderão usar uma URL mais curta que
não inclua o nome do Catálogo

Para obter mais informações sobre o uso do Portal do Desenvolvedor, consulte
[Descobrindo
e usando APIs ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/capim_devportal_overview.dita){: #new_window}.

### Sindicação
{: #syn_apic_overview}

Com o recurso de organização do
{{site.data.keyword.apiconnect_full}}, é
possível particionar seus Catálogos em Espaços. Cada Espaço é usado por uma equipe de
desenvolvimento do provedor de API diferente e tem seu próprio conjunto de recursos de
gerenciamento relacionados especificamente às APIs que a equipe associada publica nesse
Espaço, permitindo que cada equipe gerencie suas APIs independentemente.

Quando você monta ou publica uma API em um Catálogo que tem Espaços ativados, você
especifica o Espaço dentro desse Catálogo no qual deseja montar ou publicar. Entretanto,
os desenvolvedores de aplicativos que acessam o Portal do Desenvolvedor para o Catálogo
não estão cientes do particionamento de Espaço do Catálogo e veem as APIs como uma oferta
coordenada.
Cada Espaço tem seu próprio gerenciamento de ciclo de vida do Produto, aprovações de
assinatura e dados de analítica.
Você usa controle de acesso específico do Espaço para
restringir o acesso do usuário a cada Espaço; por exemplo, um desenvolvedor na equipe
Flights pode montar APIs somente no Espaço Flights.

**Nota:** por padrão, os Espaços são desativados em um Catálogo. Você ativa Espaços
modificando as configurações do Catálogo.

Para particionar um catálogo, consulte [Particionando um catálogo](/docs/services/apiconnect?topic=apiconnect-create_catalog#apic_spaces).
