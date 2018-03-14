---
copyright:
  years: 2017
lastupdated: "2017-11-02"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Inclua uma nova especificação de API e chame um serviço REST existente com o {{site.data.keyword.Bluemix_notm}}
**Duração**: 15 min  
**Nível de qualificação**: iniciante  

## Objetivo
Este tutorial ajuda você a começar rapidamente o {{site.data.keyword.apiconnect_full}}. Vamos iniciar criando uma nova especificação OpenAPI e, em seguida, criar um proxy de API de passagem para um serviço REST existente.

## Pré-requisito
Antes de iniciar, você precisa [configurar sua instância do API Connect](tut_prereq_set_up_apic_instance.html).

---

### Explore o app de amostra e teste os terminais de destino
Um app de _provedor de clima_ de amostra foi criado para este tutorial.
1. Para explorar o app, acesse [http://gettingstartedweatherapp.mybluemix.net/ ![Ícone de link externo](../../../icons/launch-glyph.svg "Ícone de link externo")](http://gettingstartedweatherapp.mybluemix.net/){:new_window}.  
2. Insira um CEP válido de 5 dígitos dos EUA para obter o _**clima atual**_ e a _**previsão de hoje**_.  
![](images/explore-weatherapp-1.png)

3. O app de clima de amostra acima foi construído usando APIs que fornecem os dados de clima. O terminal para obter os dados de clima **atuais** é _**https://myweatherprovider.mybluemix.net/current?zipcode={zipcode}**_. Experimente-o visitando [https://myweatherprovider.mybluemix.net/current?zipcode=90210 ![Ícone de link externo](../../../icons/launch-glyph.svg "Ícone de link externo")](https://myweatherprovider.mybluemix.net/current?zipcode=90210){:new_window}.  

  ![](images/explore-weatherapp-2.png)

4. Da mesma forma, o Terminal para obter os dados de previsão de **hoje** é _**https:// myweatherprovider<span></span>.mybluemix.net/today?zipcode={zipcode}**_. Experimente-o acessando [https://myweatherprovider.mybluemix.net/today?zipcode=90210 ![Ícone de link externo](../../../icons/launch-glyph.svg "Ícone de link externo")](https://myweatherprovider.mybluemix.net/today?zipcode=90210){:new_window}.  

  ![](images/explore-weatherapp-3.png)


---

### Incluir uma nova especificação OpenAPI para criar um proxy de API de REST  
1. Efetue login no {{site.data.keyword.Bluemix_notm}}: https://new-console.ng.bluemix.net/login.
2. No painel de navegação do {{site.data.keyword.Bluemix_notm}}, selecione **Serviços**, em seguida, selecione **Painel**. Ative o serviço {{site.data.keyword.apiconnect_short}}.
3. No {{site.data.keyword.apiconnect_short}}, certifique-se de que o painel de navegação esteja aberto. Caso contrário, clique em **>>** para abri-la.  
4. Selecione **Rascunhos** no painel de navegação.
5. Na guia **APIs**, clique em **Incluir**. No menu suspenso, selecione **Nova API**.    
  ![](images/create-new-1.png)  
6. Na janela *Nova API*, insira `Weather Provider API` para o título.
_O nome e o caminho base são preenchidos automaticamente_.  
  ![](images/bluemix-add-new-api.png)
7. Clique em **Criar API** para concluir o assistente.  
8. Depois de criar sua API, a guia **Design** é selecionada. 
9. Role para o painel **Host**. Insira `$(catalog.host)` como o valor se o campo não for preenchido automaticamente.
10. No painel **Caminho base**, observe o valor preenchido automaticamente: `/weather-provider-api`. A URL de destino de sua API será criada por meio desses valores.  

11. Role para a guia **Segurança** e exclua o "clientIDHeader (Chave API)" que foi gerado automaticamente.  
_(Visitaremos a segurança com chaves API no próximo tutorial.)_  

12. Na navegação, role para baixo para o painel **Caminhos** e crie um novo caminho clicando em **+**.     
    a. Dê o nome "**/current**" ao novo caminho.  
    b. No mesmo painel *Caminhos*, selecione a seção **GET /current**.    
    c. Na seção **GET /current**, inclua um novo **Parâmetro**. Conforme observado ao explorar o app de amostra, o serviço de clima requer zipcode como parâmetro.   
      - Nome: CEP  
      - Localizado em: consulta  
      - Necessário: sim  
      - Tipo: sequência   
    ![](images/path-current-1.png)   
    d. Salve sua API.  

13. Com seus parâmetros de consulta definidos na etapa anterior, agora você precisa definir o objeto de resposta que é retornado ao chamar a API de clima. Para isso, role para baixo para o painel **Definições**.   
    a. Incluir uma nova definição.  
    b. Dê o nome _Atual_ à nova definição.  
    c. Configure o Tipo para _Objeto_.  
    d. Incluir novas propriedades para a definição **Atual**.    
       - Nome: CEP/Tipo: sequência   
       - Nome: temperatura/Tipo: número inteiro   
       - Nome: umidade/Tipo: número inteiro   
       - Nome: cidade/Tipo: sequência   
       - Nome: estado/Tipo: sequência   
    ![](images/definition-current-1.png)   
    e. Salve sua API.  

14. Na etapa anterior, você definiu o objeto de resposta. Em seguida, será necessário assegurar-se de que o objeto de resposta esteja associado ao caminho **get /current**. Na navegação, role de volta até o painel **Caminhos**.
    a. Abra a operação **GET /current** e role para a seção **Respostas**.
    b. Mude o esquema da resposta 200OK de "objeto" para "**Atual**".
    c. Salve sua API clicando no ícone de salvamento. Uma notificação de confirmação "API salva" aparece momentaneamente. 

15. O caminho e a operação recém-criados eram para obter os dados de clima atuais. Agora será necessário criar um caminho e uma operação semelhantes para obter os dados de clima de hoje. Semelhante a como você criou o caminho **/current** na etapa 12, crie um novo caminho: **/today**.

16. Incluir um novo parâmetro na operação **GET /today**.
    - Nome do parâmetro: zipcode  
    - Localizado em: consulta  
    - Necessário: sim  
    - Tipo: sequência  

17. Criar uma nova definição: **Hoje**.

18. Incluir novas propriedades para a definição **Hoje**.
    - Nome: CEP/Tipo: sequência
    - Nome: hi/Tipo: número inteiro
    - Nome: lo/Tipo: número inteiro
    - Nome: nightHumidity/Tipo: número inteiro
    - Nome: dayHumidity/Tipo: número inteiro
    - Nome: cidade/Tipo: sequência
    - Nome: estado/Tipo: sequência
19. Atualize o esquema de resposta na seção **GET /today** para "Hoje".
20. Salve sua API.

21. Alterne para a guia **Montar**. Você criou duas operações até agora: **GET /current** e **GET /today**. Para assegurar que o terminal de destino correto seja chamado, será necessário criar alguma lógica que executará a condicional na operação que está sendo chamada. Vamos usar a construção lógica **Comutador de operação** para fazer isso.  
    a. Exclua a política **invoke** que já pode ser incluída na _tela_.  
    b. Na paleta, arraste o **Comutador de operação** e solte-o na tela.  
      - Para o **caso 0**, designe a operação **get /current**.
      - Incluir um novo caso: **caso 1**.
      - Designe a operação **get /today** ao **caso 1**.
      ![](images/assemble-1.png)
O **Comutador de operação** fornece um ponto de decisão. Baseado no par verbo/caminho, a operação apropriada precisa ser chamada.
    c. Arraste a política **invoke** da paleta e solte-a na tela. _A ação de chamada é usada para chamar um serviço existente de dentro de uma operação_.  Solte uma ação de chamada no caminho **/get current** e uma no caminho **/get today**.   
    d. Selecione a política **invoke** no caminho **/get current** e atualize seu título para "**invoke-current**".  
    e. Atualize o campo URL com `https://myweatherprovider.mybluemix.net/current?zipcode=$(request.parameters.zipcode)`.  
    f. Selecione a política **invoke** no caminho **/get today** e atualize seu título para "**invoke-today**".  
    g. Atualize o campo URL com `https://myweatherprovider.mybluemix.net/today?zipcode=$(request.parameters.zipcode)`.  
       ![](images/assemble-2.png)

22. Salve sua API.

---

### Teste seu proxy de API
1. Na guia **Montar**, clique no ícone para obter mais ações e, em seguida, selecione **Gerar um produto padrão**.  
   ![](images/generate-default-product-1.png) 

2. Aceite as opções padrão na caixa de diálogo **Novo produto** e clique em **Criar produto**. O produto Weather Provider API é criado e publicado no catálogo Ambiente de simulação. Uma mensagem indicando geração bem-sucedida do produto é exibida.  
  ![](images/generate-default-product-2.png)  
  
  ![](images/generate-default-product-3.png) 

  - _No {{site.data.keyword.apiconnect_short}}, **Produtos** fornecem uma maneira de agrupar as APIs que são destinadas para um uso específico. Os produtos são publicados em um **Catálogo**. [{{site.data.keyword.apiconnect_short}} glossário](../apic_glossary.html)_

3. Na guia Montar, clique no ícone de reprodução para testar a chamada de destino do proxy de API.

4. No painel de teste, selecione a operação **get /current**.
	a. Zipcode é um parâmetro necessário para esta operação, então insira um CEP dos EUA válido (por exemplo, 90210). 
	b. Clique em **chamar** e verifique se vê: 
  ```
  Resposta 200 OK Dados de clima atuais para 90210  
  ```
  
    ![](images/test-invoke-1.png)  

    ![](images/test-invoke-2.png)  

    ![](images/test-invoke-3.png)

---

### Conclusão
Neste tutorial, você aprendeu como um serviço REST existente pode ser chamado por meio de um proxy de passagem de API. Você iniciou verificando a disponibilidade do serviço de amostra por meio do navegador da web. Depois, você criou uma nova especificação OpenAPI no {{site.data.keyword.apiconnect_short}} e a vinculou ao serviço de amostra a ser chamado. Você empacotou sua API em um produto, publicou o produto no catálogo e testou o proxy.

---

## Próxima etapa

Proteja sua API usando [limitação de taxa](tut_rate_limit.html), [identificador e segredo do cliente](tut_secure_landing.html) ou [protegendo usando OAuth 2.0](tut_secure_oauth_2.html).

Criar > **Gerenciar** > Assegurar > Socializar > Analisar
