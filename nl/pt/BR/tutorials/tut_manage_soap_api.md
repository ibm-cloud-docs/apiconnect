---
copyright:
  years: 2017
lastupdated: "2017-12-15"
---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# Gerenciando um serviço SOAP
**Duração**: 15 minutos
**Nível de qualificação**: iniciante

---
## Objetivo
Neste tutorial, você usará o API Manager para criar uma API SOAP que é um proxy para um serviço de clima baseado em SOAP.

## Pré-requisito
- Antes de iniciar, será necessário [configurar sua instância do {{site.data.keyword.apiconnect_short}}](tut_prereq_set_up_apic_instance.html).
- Antes de iniciar, copie o arquivo de [teste weatherprovider.wsdl ![Ícone de link externo](../../../icons/launch-glyph.svg "Ícone de link externo")](https://raw.githubusercontent.com/IBM-Bluemix-Docs/apiconnect/master/tutorials/weatherprovider.wsdl){:new_window} para seu sistema de arquivos local.
Nota: é possível clicar em **Bruto** e, em seguida, salvar a página resultante em seu sistema local como um arquivo `.wsdl`. Como o nome sugere, esse serviço SOAP retorna os dados de clima quando um CEP é fornecido.

---
## Configurando uma definição de API SOAP
1. Efetue login no {{site.data.keyword.Bluemix_short}}: [https://new-console.ng.bluemix.net/login](https://new-console.ng.bluemix.net/login){:new_window}.

2. No **Painel** do {{site.data.keyword.Bluemix_notm}}, role para baixo para **Todos os serviços**.

3. Selecione **API Connect** para ativar o serviço do {{site.data.keyword.apiconnect_short}}. 
  
4. Navegue para a página Rascunhos, se você ainda não estiver lá:  
    a. Na interface do {{site.data.keyword.apiconnect_short}}, clique em >> para abrir o painel de navegação.
    b. Clique em **Rascunhos** no painel de navegação.
    c. Acesse a guia **APIs**.

5. Na guia APIs, clique em `Incluir +`.

6. No menu suspenso, selecione **API de um serviço SOAP**.
  ![Nova API](images/newapi-menu2.png)

7. A caixa de diálogo Nova API do WSDL é aberta. Clique em **Fazer upload de arquivo**.
![fazer upload do arquivo .wsdl](images/4-uploadwsdl.png)

8. Selecione o arquivo `weatherprovider.wsdl` que você salvou anteriormente.

9. A caixa de diálogo Nova API do WSDL reaparece. Marque a caixa de seleção **weatherService**. Clique em **Pronto**.
  ![selecionar serviço de clima](images/newapi2.png)

10. Na importação bem-sucedida, você é levado para a visualização Design da API. Além disso, é possível visualizar a definição de OpenAPI na guia Origem.
   _Na guia Origem, você verá que o WSDL é agrupado dentro da definição de OpenAPI._
![página Editor da API](images/designpage2.png)

11. Role para baixo para a **guia Segurança** e clique no ícone de exclusão para remover o `clientIDHeader (API Key)` que foi gerado automaticamente quando você criou o serviço.
   _Você aprenderá sobre segurança com Chaves API no próximo tutorial._

12. Clique no ícone ![salvar](images/save.png) para salvar suas mudanças. Uma notificação de confirmação de "API salva" aparece momentaneamente.

13. Na barra de menus com o ícone de salvamento, a guia **Design** indica sua localização atual. Junto a isso, você localiza a guia **Origem** na qual é possível visualizar diretamente o arquivo Swagger (2.0) que representa sua API e, próximo a isso, localiza a guia **Montar** que o leva para uma interface arrastar e soltar para processamento da API. Clique em **Montar**.
![guia Montar](images/assemble-clean.png)  

## Testando a definição da API SOAP

1. Na guia **Montar**, clique no ícone **Mais ações** (três pontos) e selecione **Gerar um produto padrão** no menu.  
   ![menu Mais ações, abrir](images/gen-default-prod.png)

2. Aceite as opções padrão no diálogo pop-up **Novo produto** e selecione **Criar produto**. O **Produto weatherService 1.0.0** é criado e publicado no catálogo Ambiente de simulação.  
  ![criar um novo produto](images/12a-chooseproduct.png)
 
  _No {{site.data.keyword.apiconnect_short}}, os **Produtos** fornecem um mecanismo para agrupar as APIs que são destinadas para um uso específico. Os produtos são publicados em um **Catálogo**. Referência: [Glossário do {{site.data.keyword.apiconnect_short}}](../apic_glossary.html)_

3. Salve as suas mudanças.  

4. Próximo à caixa Procurar, clique no ícone de teste para testar o serviço de API. O menu Configuração aparece.

5. Na lista de produtos, escolha `weatherService product 1.0.0`.  
  ![escolher serviço de clima](images/12-chooseproduct.png)

6. Role para baixo e clique em **Avançar**.

7. Na lista de Operações, selecione `post /weatherRequest`.  
  ![postar uma solicitação](images/13-selectoperation.png)

8. Role para baixo. Insira o XML a seguir no campo de corpo. É possível selecionar e copiar o XML de exemplo a seguir, em seguida, clicar no campo **corpo** para ativar o campo e colocar o XML de exemplo.  
  ```
  <?xml version="1.0" encoding="UTF-8"?>
  <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
  <wdata:WeatherRequest xmlns:wdata="http://www.ibm.com/wdata">
       <zipcode>10504</zipcode>
  </wdata:WeatherRequest>
   </soap:Body>
  </soap:Envelope>
  ```
  {: codeblock}  
  ![the request](images/14-enterrequest.png)

9. Role para baixo, se necessário, e clique em **Chamar**.
A API retorna um **corpo** de Resposta consistindo no clima atual.  
  ![](images/15-success.png)

## O que você fez neste tutorial
Neste tutorial, você concluiu o seguinte:
1. Configurou uma definição de API SOAP
2. Testou sua definição de API
3. Recebeu um **corpo** de Resposta do terminal de API de clima indicando o resultado de sua solicitação.

---

## Próxima etapa

[Exponha seu serviço como uma API de REST](tut_expose_soap_service.html) ou proteja sua API usando [limitando de taxa](tut_rate_limit.html), [ID de cliente e segredo](tut_secure_landing.html) ou [protegendo usando OAuth 2.0](tut_secure_oauth_2.html).

Criar > **Gerenciar** > Assegurar > Socializar > Analisar
