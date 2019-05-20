---

copyright:
  years: 2017
lastupdated: "2017-11-20"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Descobrindo APIs
{: #tut_discover_apis}

**Duração**: 25 min  
**Nível de qualificação**: iniciante  

## Objetivo
{: #object_tut_discover_apis}

Neste tutorial, você aprenderá como um usuário do portal pode consumir as APIs no {{site.data.keyword.apiconnect_full}} Developer Portal. Você entenderá como um usuário do portal exploraria produtos e APIs, visualizar e testar APIs e assinar as APIs. 

## Pré-requisito
{: #prereq_tut_discover_apis}

Não há nenhum pré-requisito para este tutorial. Como um administrador do portal, também é possível concluir este tutorial enquanto navega pelo portal do desenvolvedor para vivenciar como seus usuários do portal navegam por seu portal do desenvolvedor. Tenha em mente que todos os portais do desenvolvedor têm aparências diferentes. 

Se você não tiver um portal do desenvolvedor existente, será possível configurar um portal do desenvolvedor no {{site.data.keyword.Bluemix_short}} antes de continuar com este tutorial.

## Explorar produtos & e APIs
{: #explore_tut_discover_apis}

Essa seção mostra como um usuário do portal exploraria os produtos e as APIs no Portal do Desenvolvedor.

1. Em um navegador, navegue para o **API Connect Developer Portal**.
![API Connect Developer Portal](images/11-developer-portal.png)

2. No {{site.data.keyword.apiconnect_short}} Developer Portal, selecione a guia Produtos de API.
![Produtos de API](images/12-API-products.png)

3. Selecione um dos produtos de API disponíveis para exibir as APIs e os Planos disponíveis para o produto.  
  ![Selecionar produto](images/13-product.png)

4. Selecione uma API para explorar os detalhes das APIs disponíveis.  
  ![APIs de produtos](images/14-api.png)

5. Na página de detalhes de uma API, é possível visualizar as operações disponíveis juntamente com seus parâmetros e as respostas retornadas. No final da página, é possível visualizar as definições que são usadas pela API.  
  ![Detalhes da API](images/15-details.png) 

6. No painel de exemplos de Código, é possível visualizar exemplos de como chamar as solicitações em diferentes linguagens de codificação e suas respostas. Selecione um dos exemplos, como **Nó**, para ver um exemplo dessa linguagem de codificação.  
  ![Detalhes da API](images/16-examples.png) 

---

## Visualizar e testar as APIs
{: #view_tut_discover_apis}

Esta seção mostra como um usuário do portal que visualizar e testar as APIs disponíveis para um produto. 

1. Navegue para os detalhes da API no Portal do Desenvolvedor do {{site.data.keyword.apiconnect_short}}, conforme descrito na seção anterior.  
  ![Detalhes da API](images/21-details.png) 

2. É possível fazer download e visualizar as informações de Swagger yaml de APIs selecionando **Abrir API**.  
  ![Download Swagger yaml](images/22-swagger.png) 

3. Role para baixo para uma das operações para visualizar seus detalhes. Também é possível clicar no link de operações para ir para ele na página.
![Operação](images/23-operation.png)

4. No painel direito sob os exemplos, role para a seção **Tentar esta operação**. Insira os parâmetros e selecione **Chamar operação**.  
  ![Tentar essa operação](images/24-try-this-operation.png)

5. Role para baixo para visualizar a solicitação e resposta da chamada de operação. Uma resposta retornada de **200 OK** e o corpo da mensagem são exibidos, indicando que a chamada de operação foi bem-sucedida.  
  ![Resposta da operação](images/25-operation-response.png)

---

## Assinar APIs
{: #subscr_tut_discover_apis}

Esta seção mostra como um usuário do portal assinaria as APIs no portal do desenvolvedor. 

1. Selecione **Criar uma conta**.
![Produtos de API](images/31-create-account.png)

2. Conclua os campos necessários e selecione **Criar nova conta** na parte inferior da página. 
**Nota:** use um endereço de e-mail diferente do que você usou para criar seu portal do desenvolvedor no tutorial anterior.
![Produtos de API](images/32-create-new-account.png)

3. Após a conta do desenvolvedor ser criada, efetue login para visualizar a página inicial. Deve-se ter um app para assinar as APIs. Selecione **Apps** para acessar a página de apps registrados.  
  ![Produtos de API](images/33-login.png)

4. Para registrar um novo aplicativo, selecione **Criar novo app**.  
  ![Registrar novo app](images/34-create-new-app.png)

5. Insira um *Título* e uma *Descrição* para seu app e selecione **Enviar**.  
  ![Enviar novo app](images/35-submit-new-app.png) 

6. Agora que você tem um App, é possível assinar os planos do Produto de API. Selecione **APIs disponíveis** ou **Produtos de API** para procurar os planos do Produto de API.  
  ![Detalhes da API](images/36-api-products.png) 

7. Selecione o Produto de API que você deseja assinar.  
  ![Produto de API](images/37-select-product.png) 

8. Selecione **Assinar** para assinar o Plano de Produto de API.  
  ![Plano de Produto da API](images/38-subscribe-plan.png) 

9. Selecione o app que você deseja assinar no Plano de produto, em seguida, selecione **Assinar**.
![Assinar plano do app](images/39-subscribe-app-plan.png) 

10. Seu aplicativo foi inscrito com êxito no Plano de produto.
![Sucesso da assinatura do app](images/310-subscribe-success.png) 

## Conclusão
{: #conclusion_tut_discover_apis}

Neste tutorial, você aprendeu como os usuários do portal poderiam explorar os produtos e APIs, visualizar e testar as APIs e assinar as APIs. 

---

## Próxima etapa
{: #next_tut_discover_apis}

Saiba [como obter insights de analítica básica](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_insights_analytics).

Criar > Gerenciar> Assegurar > **Socializar** > Analisar  



