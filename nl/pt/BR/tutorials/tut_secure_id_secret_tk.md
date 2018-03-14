---
copyright:
  years: 2017
lastupdated: "2017-10-31"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Protegendo sua API com ID de cliente e Segredo do cliente usando o Developer Toolkit


**Duração:** 10 min  
**Nível de qualificação:** iniciante


## Objetivo

Este tutorial fornecerá orientação durante a proteção de sua API com o Identificador de cliente e o Segredo do cliente. Quando os aplicativos são registrados no Portal do Desenvolvedor, um Identificador de cliente é gerado para identificar o aplicativo. Opcionalmente, um Segredo do cliente, que serve como uma senha, também pode ser gerado. Os aplicativos precisariam fornecer as chaves Identificador de cliente e Segredo do cliente para acessar a API.


## Pré-requisito
Antes de iniciar, deve-se ter concluído um dos tutoriais a seguir:
- [Importar uma especificação OpenAPI2.0 e transmitir por proxy um serviço REST existente](tut_rest_landing.html) **ou**  
- [Incluir uma nova especificação de API e chamar um serviço REST existente](tut_rest_landing.html)


## Configure o mecanismo de identificação de sua API

1. Ative o API Designer (se ainda não estiver aberto):  
   a. Abra seu terminal.  
   b. Insira `apic edit` na linha de comandos. _O API Designer é ativado em seu navegador da web_    
   c. Clique em **Conectar-se ao {{site.data.keyword.Bluemix_notm}}**.  
   d. Insira suas informações de login do {{site.data.keyword.Bluemix_short}}.  

2. Navegue para a visualização Design de sua API:
    a. Clique em **Rascunhos** no painel de navegação esquerdo 
    b. Em seguida, clique na guia **APIs**
    c. Clique na _API do Provedor de clima_ criada no tutorial anterior. Isso abre a visualização **Design** da API.  
    ![](images/1_goto_drafts_api.png)  

3. Na visualização Design:  
   a. Role para baixo para **Definições de segurança**.  
    ![](images/1b.png) 

   b. Clique no ícone **Incluir definições de segurança** (+) e, em seguida, clique em **Chave API**.  
      - Nome: ID de cliente, Nome do parâmetro: X-IBM-Client-ID  
      - Nome: Segredo do cliente; Nome do parâmetro: X-IBM-Client-Secret  
      - Para ambas as novas chaves, assegure-se de que o campo **Localizado em** esteja configurado para "Cabeçalho".  
      ![](images/2a.png)    

4. Role para baixo para o painel **Segurança** e inclua uma nova opção de segurança.  
   a. Selecione as chaves Identificador de cliente e Segredo do cliente recém-criadas.  
   b. Salve sua API.  
   c. Alterne para a guia **Montar**.  
    ![](images/3a.png) 

## Teste as mudanças feitas em sua API

1. Na guia Montar, clique em ► para testar suas mudanças.
2. No painel de teste, clique na operação **get /current**.
3. Role para baixo no painel de teste e observe se os valores de ID de cliente e Segredo do cliente já foram preenchidos. _Esses são valores de teste gerados para seu ambiente de simulação e representam as chaves do aplicativo que usarão sua API._  
> Nota: estas chaves de ID de Cliente e Segredo do cliente também podem ser localizadas em **Painel** > **Catálogo** > **Configurações** > **Terminais**  

 ![](images/test_api_keys_1.png)

4. Role ainda mais para baixo e insira um CEP (por exemplo, 90210). 
5. Em seguida, clique em **Chamar**. _Você deverá obter uma resposta 200 OK junto ao corpo da mensagem retornando as informações de clima._  
6. Role novamente para cima até o campo ID de cliente e substitua o valor de ID de cliente por um aleatório (para ver o comportamento quando um ID de cliente incorreto é passado)  
7. Execute o teste novamente clicando em **Chamar**. _Você verá uma resposta 401 Desautorizado junto à mensagem "Identificador de cliente não registrado"._  
  ![](images/test_api_keys_3.png)  
  

## Chame sua API usando o Identificador de cliente e o Segredo do cliente

As configurações de segurança também podem ser testadas usando a ferramenta Explorar que chama explicitamente o terminal de proxy e passa as chaves Identificador de cliente e Segredo do cliente como valores de cabeçalho.


1. Clique em **Explorar**.
    ![](images/explore_1.png)

2. Clique na operação **GET /current** na lista.  

3. Na coluna à direita, clique em **Chamar operação** para executar o teste.  
    ![](images/4.png)  
    
---

### Conclusão
Neste tutorial, você aprendeu como configurar o mecanismo de identificação de sua API, testar mudanças feitas na API e chamar sua API usando o ID de cliente e Segredo do cliente. 

---

## Próxima etapa

Comece a socializar sua API [instalando e configurando um portal do desenvolvedor](tut_config_dev_portal.html).

Criar > Gerenciar > **Assegurar** > Socializar > Analisar
