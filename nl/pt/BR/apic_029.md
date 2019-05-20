---

copyright:
  years: 2017-2019
lastupdated: "2018-05-23"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal

subcollection: apiconnect

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# O que há de novo
{: #apic_029}

O {{site.data.keyword.apiconnect_full}} inclui os aprimoramentos a seguir:


- **Novos casos de erro são suportados pela construção de captura de conjunto**: os novos casos de erro a seguir são suportados pela construção de captura em um conjunto de APIs: *BadRequestError*, *UnauthorizedError* e *ForbiddenError*. Consulte [Casos de erro suportados por capturas de conjuntos ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/ref_toolkit_catch_errors.html){: #new_window}.
- **Incluído o parâmetro de consulta useBytesSent para as APIs selecionadas**: o parâmetro *useBytesSent* foi incluído, o que permite que o campo de análise de dados *bytes_sent* seja usado para calcular o uso. Consulte [Retornar informações de uso de dados para todos os recursos usados por um determinado aplicativo ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps__appID__data-usageGET.html){: #new_window}, [Retornar as informações de uso de dados para todos os recursos usados por todos os aplicativos na organização determinada ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps_data-usageGET.html){: #new_window}, [Retornar o uso de dados combinados para todos os recursos usados por um determinado aplicativo ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps__appID__data-usage_allGET.html){: #new_window} e [Retornar o uso de dados combinados para todos os recursos usados por uma determinada organização ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_data-usage_allGET.html){: #new_window} para obter mais informações.
**É possível codificar caracteres + nos valores de parâmetros de consulta da URL de destino de uma política de chamada ou de proxy**: há uma nova propriedade de API *x-ibm-gateway-queryparam-encode-plus-char*; se configurada como um valor de *true*, todos os caracteres "+" nos valores de parâmetro de consulta da URL de destino de políticas de chamada e de proxy serão codificados para "%2F". Em liberações anteriores, + sempre eram codificados para %2F. Agora, o comportamento padrão é não fazer a codificação. Consulte [Propriedades da API ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){: #new_window}.
- **É possível impor o analisador JSON na regra de resposta para uma política de chamada ou proxy**: há uma nova propriedade da API *x-ibm-gateway-api-enforce-response-limits*; configurar essa propriedade para um valor de *true* permite que o analisador JSON seja aplicado na regra de resposta. Se o tamanho do corpo de resposta for maior que o limite do analisador JSON configurado no domínio DataPower, um código de status de 500 será retornado. Consulte [Propriedades da API ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){: #new_window}.
- **Potencial para melhoria de desempenho para a política de mapa**: há uma nova propriedade de API *x-ibm-gateway-optimize-schema-definition* que pode fornecer uma melhoria de desempenho para a política de mapa quando uma definição de esquema muito complexa é referenciada por uma definição de saída de política. Consulte [Propriedades da API ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){: #new_window}.
