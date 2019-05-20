---

copyright:
  years: 2019
lastupdated: "2019-3-8"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Importar sua especificação de API e efetuar proxy de um serviço REST existente com o {{site.data.keyword.Bluemix_notm}}
{: #tut_import_openapi_rest_bm}

Duração: 5 min  
Nível de qualificação: iniciante  

## Objetivo
{: #object_tut_import_openapi_rest_bm}

Este tutorial ajuda você a começar rapidamente com o {{site.data.keyword.apiconnect_full}} ilustrando como é possível colocar sua API existente sob o controle de gerenciamento. Vamos iniciar importando uma especificação OpenAPI e, em seguida, criar um proxy de API de passagem para um serviço REST existente.

## Pré-requisito
{: #prereq_tut_import_openapi_rest_bm}

Antes de começar, será necessário [configurar sua instância do {{site.data.keyword.apiconnect_short}}](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_set_up_apic_instance).

---


## Explore o app de amostra e teste os terminais de destino
{: #explore_tut_import_openapi_rest_bm}

Um app de _provedor de clima_ de amostra foi criado para este tutorial. A especificação da API correspondente (Swagger 2.0) está no arquivo [clima-provider-api_1.yaml ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://raw.githubusercontent.com/IBM-Bluemix-Docs/apiconnect/master/tutorials/weather-provider-api_1.yaml){: #new_window}.

1. Para explorar o app, acesse [http://gettingstartedweatherapp.mybluemix.net/ ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](http://gettingstartedweatherapp.mybluemix.net/){: #new_window}.  
2. Insira um CEP válido de 5 dígitos dos EUA para obter o _**clima atual**_ e a _**previsão de hoje**_.  
![](images/explore-weatherapp-1.png)

3. O app de clima de amostra acima foi construído usando APIs que fornecem os dados de clima. O terminal para obter os dados de clima **atuais** é `https:// myweatherprovider<span></span>.mybluemix.net/current?zipcode={zipcode}`. Experimente-o visitando [https://myweatherprovider.mybluemix.net/current?zipcode=90210 ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://myweatherprovider.mybluemix.net/current?zipcode=90210){: #new_window}.  

  ![](images/explore-weatherapp-2.png)

4. Da mesma forma, o Terminal para obter os dados de previsão de **hoje** é `https:// myweatherprovider<span></span>.mybluemix.net/today?zipcode={zipcode}`. Experimente-o acessando [https://myweatherprovider.mybluemix.net/today?zipcode=90210 ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://myweatherprovider.mybluemix.net/today?zipcode=90210){: #new_window}.  

  ![](images/explore-weatherapp-3.png)


---

## Importe a especificação OpenAPI do app de amostra para criar um proxy de API de REST
{: #import_tut_import_openapi_rest_bm}

1. Efetue login no {{site.data.keyword.Bluemix_short}}: https://cloud.ibm.com.
2. No **Painel** do {{site.data.keyword.Bluemix_notm}}, clique em **Serviços do Cloud Foundry**. Ative o serviço {{site.data.keyword.apiconnect_short}}. 
3. No {{site.data.keyword.apiconnect_short}}, certifique-se de que o painel de navegação no lado esquerdo esteja aberto. Caso contrário, clique em **>>** para abri-la.  
4. Selecione **Rascunhos** no painel de navegação.   
5. Na guia **APIs**, clique em **Incluir**. No menu suspenso, selecione **Importar API de um arquivo ou URL**.  
     ![](images/import-1.png)

6. Vamos agora importar a definição de clima OpenAPI. Na caixa de diálogo "Importar OpenAPI (Swagger)" que é aberta, insira a URL a seguir: `https://raw.githubusercontent.com/IBM-Bluemix-Docs/apiconnect/master/tutorials/weather-provider-api_1.yaml`. Deixe as outras opções com seus valores padrão e clique em **Importar**.  
    ![](images/import-2.png)  

7. Depois de importar a especificação OpenAPI, você é levado para a visualização **Design** da API. Aqui é possível visualizar várias seções da definição OpenAPI. Também é possível visualizar o OpenAPI sob a guia **Origem**.

8. Sua API é salva. 


## Teste seu proxy de API
{: #test_tut_import_openapi_rest_bm}

### Teste com a _ferramenta de teste do API Manager_
{: #test_apimgr_tut_import_openapi_rest_bm}

1. Na guia **Montar**, clique no ícone para obter mais ações e, em seguida, selecione **Gerar um produto padrão**.  
  ![](images/generate-default-product-3.png)   

2. Aceite as opções padrão na caixa de diálogo **Novo produto** e clique em **Criar produto**. O **Produto de API Weather Provider** é criado e publicado no catálogo Ambiente de simulação. Uma mensagem indicando geração bem-sucedida do produto é exibida.  
  ![](images/generate-default-product-2.png)  


  _No {{site.data.keyword.apiconnect_short}}, **Produtos** fornecem uma maneira de agrupar as APIs que são destinadas para um uso específico. Os produtos são publicados em um **Catálogo**.  [{{site.data.keyword.apiconnect_short}} glossário](../apic_glossary.html)_

3. Na guia Montar, clique no ícone de reprodução para testar a chamada de destino do proxy de API.

4. No painel de teste, selecione a operação **get /current**.  
    a. Zipcode é um parâmetro necessário para essa operação, portanto, insira um CEP válido dos EUA (por exemplo, 10504).  
    b. Clique em **chamar**.  

_Se você obtiver um erro CORS, siga as instruções na mensagem de erro. Clique no link com erro para incluir a exceção em seu navegador e, em seguida, pressione o botão "chamar" novamente._
    ![](images/test-invoke-all.png)


### Teste com a _ferramenta Explore_
{: #test_explore_tut_import_openapi_rest_bm}

_A ferramenta Explore permite que os usuários testem a operação correta da API cumprindo quaisquer requisitos de parâmetros configurados na definição OpenAPI. Esse cumprimento não é feito na Ferramenta de Teste da API localizada na guia Montar, portanto isso permite que o usuário verifique o comportamento da API quando o parâmetro está ausente._

1. Para testar seus terminais de proxy de API, selecione **Explore**, em seguida, selecione **Ambiente de simulação**.
![](images/test-explore-1.png)
2. Selecione **Weather Provider API** na lista de APIs disponíveis.
3. Selecione a operação **GET /current** na paleta.
4. Selecione "Experimente".  
5. Insira um CEP válido dos EUA (por exemplo, 10504) na caixa de teste.
  ![](images/test-explore-2.png)
6. Clique em **Chamar operação** para ver a resposta.

    ![](images/test-explore-3h.png)


### Conclusão
{: #conclusion_tut_import_openapi_rest_bm}

Neste tutorial, você viu como um serviço REST existente pode ser chamado por meio de um proxy de passagem de API. Você iniciou verificando a disponibilidade do serviço de amostra por meio do navegador da web. Então você criou um proxy de API no {{site.data.keyword.apiconnect_short}} e vinculou o proxy ao serviço de amostra a ser chamado. Você empacotou sua API em um produto, publicou o produto no catálogo e testou o proxy.

---

## Próxima etapa
{: #next_tut_import_openapi_rest_bm}

Proteger sua API usando o OAuth 2.0](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_oauth_2).

Criar > **Gerenciar** > Assegurar > Socializar > Analisar

