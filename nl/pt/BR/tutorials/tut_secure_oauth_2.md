---
copyright:
  years: 2017
lastupdated: "2017-12-13"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Protegendo sua API com o OAuth de duas etapas

Duração: 10 minutos  
Nível de qualificação: iniciante

## Objetivo

Este tutorial orientará você para proteger sua API usando um fluxo OAuth 2.0 de duas etapas. Neste fluxo de aplicativo, o cliente OAuth inicia uma solicitação com o servidor de autorizações e recebe um token de acesso. O cliente OAuth pode então usar o token para acessar os recursos protegidos por meio de sua API.

## Pré-requisito

Antes de iniciar, deve-se ter concluído o tutorial a seguir.  
- [Protegendo uma API com chaves de ID de cliente ou Segredo do cliente com o {{site.data.keyword.Bluemix}}](tut_secure_id_secret_bm.html) ou
- [Protegendo uma API com chaves de ID de cliente ou Segredo do cliente com o kit de ferramentas](tut_secure_id_secret_tk.html)

Nota: este tutorial mostra as etapas e capturas de tela para realizar a tarefa na UI do {{site.data.keyword.Bluemix}}. Também é possível concluir o mesmo procedimento usando a linha de comandos. É possível visualizar esse procedimento no [IBM Knowledge Center](https://www.ibm.com/support/knowledgecenter/SSMNED_5.0.0/com.ibm.apic.toolkit.doc/tutorial_apionprem_security_OAuth_v506.html). 

## Procedimento

1. Crie uma API do Provedor OAuth e selecione seu esquema do OAuth.  
	a. Abra **Rascunhos**, selecione **APIs** e clique em **Incluir** > **API do Provedor OAuth 2.0**.  
    ![](images/oauth_provider_1.png)
	b. Forneça o título "API de terminal OAuth". O nome e o caminho base devem ser preenchidos automaticamente.  
	c. Selecione **Criar API**.  
	d. Na API de terminal do OAuth recém-criada, navegue para o painel **OAuth 2** (ou role para baixo até ele) e selecione "Confidencial" como o Tipo de cliente.  
	e. Em Escopos, renomeie _scope1_ para _view_current_. Exclua _scope2_ e _scope3_.  
	f. Em **Concessões**, cancele a seleção **Implícito**, **Senha** e **Código de acesso**. Deixe **Aplicativo** selecionado.  
	![](images/oauth_provider_2.png)  
	g. Salve sua API.  

2. Atualize a definição de segurança do Weather Provider API para incluir OAuth.  
	a. Alterne para _Weather Provider API_. (Volte para APIs e, em seguida, selecione _Weather Provider API_.)  
	b. Em Definições de segurança, inclua uma nova definição para OAuth. Nomeie-a como "Definição de OAuth".  
	c. No campo Fluxo, selecione **Aplicativo**.  
	d. Insira a URL do token _<your base URL>/oauth-endpoint-api/oauth2/token_.  
	e. Incluir um novo escopo: view_current.  
	![](images/oauth_security_definition_1.png)
	f. Em **Segurança**, selecione **Definição de OAuth** e **view_current** e mantenha o ID de cliente e Segredo do cliente selecionados.  
	![](images/oauth_security_definition_2.png)
	g. Clique em Salvar.  
	h. Navegue de volta para **Rascunhos** e selecione **Produtos**. Inclua a API de terminal OAuth em seu produto Weather Provider.  
	i. Salve o produto e monte-o em seu Ambiente de simulação.  
	![](images/oauth_security_definition_3a.png)

3. Teste sua configuração de segurança OAuth.  
	a. Publique seu produto atualizado no ambiente de simulação. Clique em **Painel > Ambiente de simulação** e, em seguida, publicar seu produto.  
	  ![](images/test_oauth_1.png)
	b. Clique em **Explorar > Ambiente de simulação**.  
      ![](images/test_oauth_2.png)
	c. Em seu **Weather Provider API**, clique em **GET /current** na lista de operações.  
	d. No painel à direita, observe se o ID de cliente e Segredo do cliente já estão preenchidos.  
	e. Na seção **Parâmetros**, insira um CEP.  
      ![](images/test_oauth_3.png)
	f. Na seção **Autorização**, clique em **Autorizar** para obter o token de acesso.  
	g. Depois de ter recebido o seu token de acesso, clique em **Chamar operação** para concluir seu teste.  
      ![](images/test_oauth_4.png)

4. Observe se a solicitação inclui o token de acesso, ID de cliente e Segredo do cliente. Para passar somente o token de acesso na solicitação, você precisará remover o ID e o Segredo do cliente dos requisitos de segurança para o Weather Provider API.  
    ![](images/test_oauth_5.png)

5. Salve seu Weather Provider API. Em seguida, monte e publique-o no Ambiente de simulação. Na ferramenta Explore, execute o mesmo teste que você executou anteriormente.  
    ![](images/test_oauth_6.png)
    
## Conclusão
Neste tutorial, você aprendeu como criar uma API de Provedor OAuth, atualizar a definição de segurança de uma API para incluir OAuth e testar sua configuração de segurança.

---

## Próxima etapa

Comece a socializar sua API [instalando e configurando um portal do desenvolvedor](tut_config_dev_portal.html).

Criar > Gerenciar > **Assegurar** > Socializar > Analisar
