---

copyright:
  years: 2017
lastupdated: "2017-10-31"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorials

subcollection: apiconnect

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Protegendo sua API com ID de cliente e Segredo do cliente usando {{site.data.keyword.Bluemix_notm}}
{: #tut_secure_id_secret_bm}

**Duração:** 10 min  
**Nível de qualificação:** iniciante


## Objetivo
{: #object_tut_secure_id_secret_bm}
Este tutorial fornecerá orientação durante a proteção de sua API com o Identificador de cliente e o Segredo do cliente. Quando os aplicativos são registrados no Portal do Desenvolvedor, um Identificador de cliente é gerado para identificar o aplicativo. Opcionalmente, um Segredo do cliente, que serve como uma senha, também pode ser gerado. Os aplicativos precisariam fornecer as chaves Identificador de cliente e Segredo do cliente para acessar a API.


## Pré-requisito
{: #prereq_tut_secure_id_secret_bm}

Antes de iniciar, deve-se ter concluído um dos tutoriais a seguir: 
- [Importar uma especificação do OpenAPI2.0 e configurar o proxy de um serviço REST existente](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_rest_landing)  
**ou 
**  
- [Incluir uma nova especificação de API e chamar um serviço REST existente](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_rest_landing)


## Configure o mecanismo de identificação de sua API
{: #set_id_tut_secure_id_secret_bm}

1. Navegue para a visualização Design de sua API:  
   a. Clique em **Rascunhos** no painel de navegação esquerdo  
   b. Em seguida, clique na guia **APIs**  
   c. Clique na _API do Provedor de clima_ criada no tutorial anterior. Isso abre a visualização **Design** da API.  
   ![](images/1_goto_drafts_api.png)  

2. Na visualização Design:
    a. Role para baixo para **Definições de segurança**.  
    b. Clique no ícone **Incluir definições de segurança** (+) e, em seguida, clique em **Chave API**.  
    c. Inclua as duas novas chaves API mostradas abaixo. Para ambas as novas chaves, assegure-se de que o campo "Localizado em" esteja configurado para "Cabeçalho".  
      - Nome: ID do cliente, Nome do parâmetro: X-IBM-Client-Id  
      - Nome: Segredo do cliente; Nome do parâmetro: X-IBM-Client-Secret    
        ![](images/2_security_definitions.png)  

3. Role para baixo para o painel **Segurança** e inclua uma nova opção de segurança.  
    a. Selecione as chaves Identificador de cliente e Segredo do cliente recém-criadas.  
    b. Salve sua API.  
    c. Alterne para a guia **Montar**.  
    ![](images/3_security_option.png)  


## Teste as mudanças feitas em sua API
{: #test_tut_secure_id_secret_bm}

1. Na guia Montar, clique no botão ► para testar suas mudanças.

2. No painel de Teste/Configuração, clique em **Publicar novamente o produto** para obter as mudanças mais recentes. 
> Essa opção atualiza seu produto de API e também o publica no catálogo Ambiente de simulação.

3. Depois que o produto tiver sido publicado, clique na operação **get /current** no painel de teste.
4. Role para baixo no painel de Teste e observe se os valores de ID de cliente e Segredo do cliente já foram preenchidos. 
> Estes são valores de teste gerados para seu ambiente de simulação e representam as chaves do aplicativo que usará sua API.
> **Nota:** as chaves de ID de cliente e Segredo do cliente também podem ser localizadas em Painel > Catálogo > Configurações > Terminais]_   
  
  ![](images/test_api_keys_1.png)

5. Role ainda mais para baixo e insira um CEP (por exemplo, 90210). 
6. Clique em **Chamar**. _Você deverá obter uma resposta 200 OK junto ao corpo da mensagem retornando as informações de clima._
7. Agora role novamente para cima para o campo ID de cliente. 
8. Substitua o valor de ID de Cliente por um aleatório.
9. Execute o teste novamente clicando em **Chamar**. _Você verá uma resposta 401 Desautorizado junto à mensagem "Identificador de cliente não registrado"._  

    ![](images/test_api_keys_3.png)  


## Chame sua API usando o Identificador de cliente e o Segredo do cliente
{: #call_tut_secure_id_secret_bm}

As configurações de segurança também podem ser testadas usando a ferramenta Explorar que chama explicitamente o terminal de proxy e passa as chaves Identificador de cliente e Segredo do cliente como valores de cabeçalho.

1. Clique em **Explorar** e, em seguida, clique em **Ambiente de simulação**.
    ![](images/explore_1.png)

2. Clique na operação **GET /current** na lista.

3. Na coluna direita, clique em **Chamar operação** para executar novamente o teste.
    ![](images/explore_3.png)

---

## Conclusão
{: #conclusion_tut_secure_id_secret_bm}

Neste tutorial, você aprendeu como configurar o mecanismo de identificação de sua API, testar mudanças feitas na API e chamar sua API usando o ID de cliente e Segredo do cliente. 

---

## Próxima etapa
{: #next_tut_secure_id_secret_bm}

Comece a socializar sua API [instalando e configurando um portal do desenvolvedor](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_config_dev_portal).

Criar > Gerenciar > **Assegurar** > Socializar > Analisar
