---

copyright:
  years: 2017
lastupdated: "2017-06-05"

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Glossário

O glossário de termos e definições do {{site.data.keyword.apiconnect_short}}.

- **Desenvolvedor de API**: um Desenvolvedor de API cria e configura APIs, Produtos e políticas para organizações de provedores dos quais é membro. Um Desenvolvedor de API pode ser um membro de uma ou mais organizações de provedores. O Desenvolvedor de API concentra-se na implementação técnica de APIs mais do que fazem no relacionamento de
negócio com desenvolvedores de aplicativos.

- **operação de API**: uma unidade de uma API de REST que pode ser chamada. Uma operação de API é composta por um verbo HTTP e um caminho de URL
subordinados à raiz de contexto da API.

- **API Designer**: a UI para criação de APIs.

- **API Manager**: a UI para gerenciar APIs, planos e produtos.

- **aplicativo**: uma parte de código do cliente que acessa APIs para interagir com um serviço, sistema ou conteúdo. Aplicativos são geralmente aplicativos da web ou aplicativos móveis.

- **conjunto**: interface de programação de aplicativos que fornece funcionalidade avançada para interagir com um aplicativo: faz chamadas laterais para serviços externos e, em seguida, transforma e agrega a resposta antes de uma resposta ser retransmitida para o aplicativo de chamada.

- **Catálogo**: um Catálogo é um destino de preparação e se comporta como uma partição lógica do gateway e do Portal do Desenvolvedor. As URLs para chamadas API e para o Portal do
Desenvolvedor são específicas de um determinado Catálogo.

- **ID de cliente**: uma parte das informações que identifica um aplicativo individual. Um aplicativo poderá chamar uma
API somente se ela passar uma chave de aplicativo que seja reconhecida pelo sistema {{site.data.keyword.apiconnect_short}} e receba acesso à
API. A chave do aplicativo é passada pelo cliente ao usar
um parâmetro de consulta de HTTP.

- **segredo do cliente**: uma parte das informações que é usada junto com a chave do aplicativo para verificar a identidade de um aplicativo. Uma API pode ser configurada
para requerer que os aplicativos do cliente forneçam seu segredo do aplicativo com
sua chave do aplicativo. O segredo do aplicativo funciona efetivamente
como uma senha conhecida somente para o aplicativo. O segredo do aplicativo é passado pelo cliente ao usar
um parâmetro de consulta de HTTP.

- **comunidade**: uma coleção de organizações do desenvolvedor. É usada como uma construção de
agrupamento ao publicar APIs. As comunidades são usadas para restringir a visibilidade e a acessibilidade das APIs. Uma API pode ser publicada em comunidades selecionadas, o que significa que somente desenvolvedores de aplicativos dentro dessas organizações podem ver a API.

- **modelo de LoopBack**: um modelo de LoopBack é um objeto JavaScript que representa dados do aplicativo e inclui regras de validação, recursos de acesso a dados e lógica de negócios. Modelos de LoopBack fornecem uma API REST por padrão
e conectam-se a origens de dados para obter acesso a dados de backend.

- **origem de dados de LoopBack**: uma origem de dados de LoopBack é um objeto JavaScript que representa um serviço de backend, como um banco de dados, API de REST (a ser consumida) ou serviço da web SOAP. As origens de dados são suportadas por conectores
que, em seguida, se comunicam diretamente com o banco de dados ou com outros serviços de backend.

- **organização**: a entidade que possui APIs ou aplicativos que usam APIs. Uma organização do provedor possui APIs e
Planos associados e pode, além disso, possuir aplicativos. Uma organização do desenvolvedor possui somente
aplicativos. Uma organização possui no mínimo um proprietário. Uma organização pode ser uma equipe do projeto,
um departamento ou uma divisão.

- **Caminho**: um caminho define a rota por meio da qual os usuários acessam as APIs de REST. Um caminho consiste em uma ou mais
operações de HTTP, como GET ou POST.

- **Plano**: A construção de pacote pela qual as APIs são disponibilizadas aos desenvolvedores. Um Plano disponibiliza uma
coleção de operações de uma ou mais APIs e é publicado para comunidades de desenvolvedores de
aplicativos. Os desenvolvedores de aplicativos obtêm acesso a APIs registrando aplicativos para acessar Planos. Um Plano transporta com ele uma coleção de configurações de política. Na forma mais simples, um Plano define uma
política de cota única que se aplica a todas as operações de API que são acessadas por meio do Plano. Em
casos mais avançados, políticas adicionais podem ser associadas a um Plano.

- **política**: uma política é uma parte da configuração que controla um aspecto específico do processamento no servidor Gateway durante a manipulação de uma chamada da API no tempo de execução. Políticas são os blocos de
construção de fluxos de conjuntos. As políticas fornecem o meio para configurar recursos, como segurança,
criação de log, roteamento de solicitações para serviços de destino e transformação de dados de um formato para
outro. As políticas podem ser configuradas no contexto de uma API ou no contexto de um Plano.

- **Produto**: os produtos fornecem um método pelo qual é possível agrupar as APIs em um pacote que é planejado para um uso específico. Além disso, eles contêm Planos, que podem ser usados para diferenciar entre diferentes ofertas. É possível criar Planos somente dentro de Produtos, e esses Produtos depois são publicados em um catálogo.

- **proxy**: interface de programação de aplicativos que encaminha solicitações para um recurso de backend definido pelo usuário e retransmite respostas de volta para o aplicativo de chamada.

- **publicar**: o processo de movimentação de um aplicativo ou Produto da preparação para que os Planos e APIs incluídos nele fiquem disponíveis para os desenvolvedores de aplicativos para acessar e usar.

- **função**: uma função define permissões que podem ativar a funcionalidade para usuários. Cada função possui um conjunto
diferente de permissões.

- **catálogo de Ambiente de simulação**: em um catálogo de Ambiente de simulação, as aprovações são submetidas a bypass para ações de publicação e de ciclo de vida. As aprovações
pendentes são canceladas quando um catálogo que não é de Ambiente de simulação é convertido em um Ambiente de simulação. Um catálogo de Ambiente de simulação é
usado para testar APIs que estão em desenvolvimento.

- **definição de segurança**: uma definição de segurança especifica todas as configurações para um aspecto específico de segurança da API; por exemplo, o registro do usuário que você usa para autenticar o acesso à API.

- **Perfil SSL**: um perfil SSL é usado para assegurar a transmissão de dados por meio de websites. Os certificados SSL
garantem que as informações enviadas a websites não sejam roubadas
ou corrompidas.

- **estágio**: o processo de mover um aplicativo ou produto do status de rascunho para um catálogo na preparação para publicação.

- **assinatura**: uma assinatura é o meio pelo qual um desenvolvedor de aplicativos obtém acesso aos recursos fornecidos por uma API. Um desenvolvedor de aplicativos usa o Portal do Desenvolvedor para assinar o plano no
qual a API é publicada.

- **registro do usuário**: um registro do usuário é uma maneira de assegurar acesso aos catálogos e APIs. O usuário pode proteger as APIs com
um registro do usuário para que as credenciais do usuário devam ser fornecidas quando uma API é chamada.

- **extensão do fornecedor**: uma extensão do fornecedor é incluída em uma API de REST para estender a especificação OpenAPI (Swagger 2.0).
