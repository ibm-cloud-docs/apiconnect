---

copyright:
  years: 2017
lastupdated: "2018-02-12"

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# O que há de novo

O {{site.data.keyword.apiconnect_full}} inclui os aprimoramentos a seguir:

- **Excluir contas de usuários e organizações do desenvolvedor no Portal do Desenvolvedor**: é possível excluir sua conta de usuário e organizações do desenvolvedor no Portal do Desenvolvedor. Também é possível mudar a propriedade de suas organizações do desenvolvedor. Para obter mais informações, consulte [Excluindo sua conta de desenvolvedor ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapic_portal_delete_account.html){:new_window}, [Excluindo uma organização do desenvolvedor ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapic_portal_delete_dev_org.html){:new_window} e [Mudando a propriedade de uma organização do desenvolvedor ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapic_portal_dev_org_ownership.dita){:new_window}.

- __Incluído o campo de evento de API *endpoint_url*__: o campo de registro de eventos *endpoint_url* identifica o proxy ou chama a URL de destino na qual a solicitação falhou. Consulte [Excluindo sua conta do desenvolvedor ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/rapim_analytics_apieventrecordfields.html){:new_window} para obter informações adicionais.</dd>

- **Incluído suporte e uma referência para APIs de REST do Portal do Desenvolvedor para analítica**: as APIs de REST do Portal do Desenvolvedor ajudam a analisar suas APIs do catálogo. Para obter mais informações, veja [Analítica ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/analytics.html){:new_window}.

- **Incluída a seção Analítica ao criar uma API**: é possível definir e especificar parâmetros existentes para sua API que podem ser usados para reunir dados de analítica
sobre a API. Veja [Editando uma definição de API de REST ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html){:new_window} para obter mais informações.

- **Incentive o uso de autenticação de dois fatores no Portal do Desenvolvedor**: é possível incentivar os
usuários do Portal do Desenvolvedor a configurar uma autentificação de dois fatores (TFA) em
sua conta aplicando um módulo de Regras de TFA. Para obter mais informações, veja [Incentivando os usuários a configurar a autenticação de dois fatores em sua conta do Portal do Desenvolvedor ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapim_portal_two_factor_auth_enforce.html){:new_window}.

- **Recursos incluídos no gerenciamento de faturamento e pagamento integrado**:
administrador:
	* Crie Planos de assinatura de faturamento mensal pré-pago que seus clientes de API podem assinar com um cartão de crédito. Veja [Faturamento para o uso de seus Produtos ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/capim_product_billing.html){:new_window} para obter mais informações.
	* Alavanque uma conta de Faixa para gerenciar os pagamentos para suas assinaturas.
	* Especifique um número de dias de avaliação grátis em seu Plano de assinatura para novos assinantes. O pagamento inicia automaticamente após a expiração dos dias de avaliação.
	Cliente:
	* Assine Planos baseados em taxa no Portal do Desenvolvedor que permitem que você use produtos que contêm uma ou mais APIs. Veja [Tutorial: assinando um Plano com precificação ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tutorial_portal_sub_paid_plan.html){:new_window} para obter mais informações.

- **Chamada substituída automaticamente no gateway**: a última chamada em sua política pode ser substituída por um proxy. Isso é feito automaticamente pelo
gateway para melhorar o desempenho. Para obter mais informações, veja: [Propriedades da API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){:new_window}.

- **O escopo de OAuth pode ser modificado por respostas de terceiros**: é possível configurar um servidor externo para substituir o valor do escopo da API. Para obter mais informações, veja: [Escopo ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/con_oauth_scope.html){:new_window}.

- **Novos campos de eventos da API**: incluídos os campos de eventos da API a seguir:
    * billing.trial_period_days
	* billing.amount
	* billing.currency
	* billing.model
	* billing.provider
	* client_id
	* immediate_client_ip
	* latency_info2.task
	* latency_info2.ended

Veja [Campos de registro de eventos da API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/rapim_analytics_apieventrecordfields.html){:new_window} e [Obtendo dados de analítica usando chamadas API de REST ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/tapim_exportanalytics_api_calls.html){:new_window} para obter mais
informações.

- **Novos parâmetros de consulta para a URL de redirecionamento**: novos parâmetros de consulta foram incluídos nas informações disponíveis para um terceiro. Os novos parâmetros são <code>provider</code>, <code>providerid</code> e
<code>g-transid</code>. Para obter mais informações, veja [Autenticando
e autorizando por meio de uma URL de redirecionamento ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_redirect_form_.html){:new_window}.

- **Evitando alertas CORS do navegador na ferramenta de Teste**: a ferramenta de Teste do API Designer envia solicitações do navegador que podem acionar alertas CORS. Para
evitar alertas CORS, a caixa de seleção **Ativar proxy** é fornecida para enviar mensagens de teste do servidor que hospeda o API Designer em vez do navegador. Para obter mais informações,
veja [Testando uma API com a ferramenta de Teste do API Designer ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_toolkit_testing.html){:new_window}.

- **Proteger APIs com OAuth de terceiro em vez do Mobile First Foundation**: proteja sua API com um provedor OAuth de terceiro em vez do servidor de autorizações do IBM MobileFirst&tm; Platform Foundation. Para obter
mais informações, veja [Integrando o provedor OAuth de terceiro ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/con_oauth_introspection.html){:new_window}.

- **Proteger suas APIs com o OpenID Connect (OIDC)**: é possível proteger suas APIs com o OpenID Connect (OIDC) usando
uma API do Provedor OAuth de amostra pré-fornecida que você customiza de acordo com sua configuração do OIDC. Para
obter mais informações, veja [Protegendo suas APIs com o OpenID Connect ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/tapic_sec_api_config_oidc.html){:new_window}.

- **A ação de atualização do SOAP não sobrescreve a API**: quando você atualiza uma API SOAP de uma definição WSDL, somente as seções da API que são
afetadas pelo novo WSDL são substituídas, as outras seções ficam inalteradas. Em liberações anteriores, a
ação de atualização sobrescrevia completamente a configuração da definição da API SOAP, incluindo todas
as propriedades de design e configuração de conjunto. Para obter mais informações, veja [Atualizando uma API
SOAP ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/tapic_soap_update.html){:new_window}.

- **Use o Honeypot para proteção de spam no Portal do Desenvolvedor**: a proteção Honeypot fornece mecanismos de segurança para proteger seu site do Portal do Desenvolvedor contra o envio de formulário por robôs de spam. Se a atividade do robô de spam é detectada, o envio de formulário é bloqueado. Para obter mais
informações, veja [Usando o Honeypot para proteção de spam ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapic_portal_honeypot.html){:new_window}.

- **Usando o módulo Visualizações no Portal do Desenvolvedor**: crie novas visualizações no Portal do Desenvolvedor, como listas de conteúdos de Produtos, APIs e aplicativos, usando o módulo de UI de Visualizações. Para obter mais informações, veja [Usando o módulo Visualizações no Portal do Desenvolvedor ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/capic_portal_views.html){:new_window}.
