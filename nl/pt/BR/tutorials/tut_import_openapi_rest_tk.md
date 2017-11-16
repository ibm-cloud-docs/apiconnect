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

# Importar sua especificação de API e usar proxy de um serviço REST existente usando o Developer Toolkit
Duração: 5 min  
Nível de qualificação: iniciante  


## Objetivo
Este tutorial ilustra como é possível colocar sua API existente sob o controle de gerenciamento com o {{site.data.keyword.apiconnect_short}}. Neste tutorial, você importará uma especificação OpenAPI e criará um proxy de API de passagem para um serviço REST existente.

## Pré-requisito
Antes de iniciar, será necessário [configurar sua instância do API Connect](tut_prereq_set_up_apic_instance.html) e [instalar o kit de ferramentas do API Connect](tut_prereq_install_toolkit.html).

---


## Explore o app de amostra e teste os terminais de destino

Um app de _provedor de clima_ de amostra foi criado para este tutorial. A especificação da API correspondente (Swagger 2.0) está no arquivo [weather-provider-api_1.0.0.yaml ![Ícone de link externo](../../../icons/launch-glyph.svg "Ícone de link externo")](https://raw.githubusercontent.com/ibm-apiconnect/getting-started/master/toolkit/1a-import/weather-provider-api_1.0.0.yaml){:new_window}.

1. Para explorar o app, acesse [http://gettingstartedweatherapp.mybluemix.net/ ![Ícone de link externo](../../../icons/launch-glyph.svg "Ícone de link externo")](http://gettingstartedweatherapp.mybluemix.net/){:new_window}.  
2. Insira um CEP válido de 5 dígitos dos EUA para obter o _**clima atual**_ e a _**previsão de hoje**_.  
![](images/explore-weatherapp-1.png)

3. O app de clima de amostra acima foi construído usando APIs que fornecem os dados de clima. O terminal para obter os dados de clima **atuais** é `https:// myweatherprovider<span></span>.mybluemix.net/current?zipcode={zipcode}`. Experimente-o visitando [https://myweatherprovider.mybluemix.net/current?zipcode=90210 ![Ícone de link externo](../../../icons/launch-glyph.svg "Ícone de link externo")](https://myweatherprovider.mybluemix.net/current?zipcode=90210){:new_window}.  

  ![](images/explore-weatherapp-2.png)

4. Da mesma forma, o Terminal para obter os dados de previsão de **hoje** é `https:// myweatherprovider<span></span>.mybluemix.net/today?zipcode={zipcode}`. Experimente-o acessando [https://myweatherprovider.mybluemix.net/today?zipcode=90210 ![Ícone de link externo](../../../icons/launch-glyph.svg "Ícone de link externo")](https://myweatherprovider.mybluemix.net/today?zipcode=90210){:new_window}.  

  ![](images/explore-weatherapp-3.png)



---

## Importe a especificação OpenAPI do app de amostra para criar um proxy de API de REST
1. Ative o **API Designer**. Em sua janela do terminal, insira o comando a seguir: `apic edit`.
2. Efetue login usando seu IBMid. ![](images/screenshot_apic-edit_login.png)
3. No **API Designer**, assegure-se de que o painel de navegação esteja aberto. Caso contrário, clique em >> para abri-la.
4. No painel de navegação, clique em **Rascunhos**.
5. Acesse a guia **APIs**.
6. Na guia APIs, clique em **Incluir**.
7. No menu suspenso, clique em **Importar API de um arquivo ou URL**.
![](images/toolkit-import-1.png)
8. Há uma definição de OpenAPI 2.0 da API de clima que você usará para este tutorial. Na caixa de diálogo "Importar OpenAPI (Swagger)", insira esta URL:
`https://raw.githubusercontent.com/ibm-apiconnect/getting-started/master/toolkit/1a-import/weather-provider-api_1.0.0.yaml`.
9. Deixe a opção _Incluir um produto_ desmarcada e clique em **Importar**.  
    ![](images/screenshot_import-url.png)  

Depois de importar a especificação OpenAPI, você é levado para a visualização Design da API. Aqui é possível visualizar várias seções da definição OpenAPI. Role para explorar e especialmente observe o valor do Host. Também é possível visualizar o OpenAPI na guia Origem.
_Você verá que o valor do host está configurado para _ `$(catalog.host)` _. Esta é a URL base para seu proxy API._
 


## Teste seu proxy de API

1. Inicie o servidor de teste local selecionando o ícone **Iniciar servidores**. Quando o Gateway for iniciado, você verá o status ser atualizado automaticamente para _**Em execução**_.
    ![](images/screenshot_start-server-1.png)

2. Selecione a guia **Montar**.

3. Clique no ícone de reprodução (>) para testar a chamada de destino de seu proxy de API.
   _Para este tutorial, usaremos o Micro Gateway integrado, então assegure-se de que **Políticas de Micro Gateway** esteja selecionado.
![](images/screenshot_test-0.png)

4. No painel de teste:
  - Selecione a operação **get /current**.  
  - Zipcode é um parâmetro necessário para esta operação, portanto, insira um CEP válido dos EUA (por exemplo, 90210).  
  - Selecione **invoke** e verifique a resposta.

    _Se você encontrar um erro CORS, siga as instruções na mensagem de erro. Clique no link no erro para incluir a exceção em seu navegador e, em seguida, clique em **invoke** novamente.
  
  - A resposta esperada é uma resposta **200 OK** e os dados de clima atual para o CEP 90210.
![](images/screenshot_test-1.png)    


## Conclusão

Neste tutorial, você viu como um serviço REST existente pode ser chamado por meio de um proxy de passagem de API. Você iniciou verificando a disponibilidade do serviço de amostra por meio do navegador da web. Em seguida, você criou um proxy de API no API Connect e vinculou-o ao serviço de amostra a ser chamado. Finalmente, você testou esse serviço com as ferramentas de teste interno do {{site.data.keyword.apiconnect_short}}.

---

## Próxima etapa

Proteja sua API usando [limitação de taxa](tut_rate_limit.html), [identificador e segredo do cliente](tut_secure_landing.html) ou [protegendo usando OAuth 2.0](tut_secure_oauth_2.html).

Criar > **Gerenciar** > Assegurar > Socializar > Analisar
