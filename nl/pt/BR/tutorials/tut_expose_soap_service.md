---

copyright:
years: 2017
lastupdated: "2017-11-14"

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
 

# Expor um serviço SOAP como uma API REST
**Duração**: 20 min  
**Nível de qualificação**: iniciante  

---
## Objetivo
No API Manager, você criará uma API de REST que acessará um serviço SOAP existente e o exporá como uma API de REST.

## Pré-requisito
1. Antes de iniciar, você precisará [configurar sua instância do {{site.data.keyword.apiconnect_full}}](tut_prereq_set_up_apic_instance.html).
2. Antes de iniciar, copie o arquivo de [teste weatherprovider.wsdl ![Ícone de link externo](../../../icons/launch-glyph.svg "Ícone de link externo")](https://raw.githubusercontent.com/IBM-Bluemix-Docs/apiconnect/master/tutorials/weatherprovider.wsdl){:new_window} para seu sistema de arquivos local.
	>![images/info.png]
	>É possível clicar em **Bruto** e, em seguida, salvar a página resultante em seu sistema local como um arquivo `.wsdl`.

---
## Configurando uma definição de API de REST
1. Efetue login no {{site.data.keyword.Bluemix_short}}: [https://new-console.ng.bluemix.net/login ![Ícone de link externo](../../../icons/launch-glyph.svg "Ícone de link externo")](https://new-console.ng.bluemix.net/login){:new_window}.
2. No {{site.data.keyword.Bluemix_notm}} **Painel** role para baixo e selecione {{site.data.keyword.apiconnect_short}}. Como alternativa, no ícone de menu, escolha **Serviços** e, em seguida, **APIs** para atingir a janela **Trabalhar com APIs** e selecione **API Connect**. Na página **API Connect**, é possível simplesmente pressionar `Criar` ou ajustar as configurações padrão. Para os propósitos deste exercício, deixe a instância desvinculada ajuste o nome do Serviço para facilitar o reconhecimento mais tarde. Um exemplo seria `API Connect-weather-exercise`.
Pressione o botão `Criar` para ativar o serviço {{site.data.keyword.apiconnect_short}}.  
Você pode ver um alerta que descreve o que há de novo ou a página de abertura informativa **APIs de rascunhos**. Depois de ler as informações, clique no ícone **"Pronto"** para visualizar o API Manager.
3. No {{site.data.keyword.apiconnect_short}}, se você não tiver fixado anteriormente a área de janela de navegação da UI, clique em **Navegar para** ![](images/navigate-to.png). A área de janela de navegação da UI do API Manager é aberta. Para fixar a área de janela de navegação da UI, clique no ícone do **menu Fixar** ![](images/pinned.png).
4. Selecione **Rascunhos** na área de janela de navegação da UI e, em seguida, clique na guia **APIs**. A guia **APIs** é aberta.
![](images/drafts-api-1.png)
5. Selecione **Incluir +** > **Nova API**.
6. Especifique as informações básicas sobre a API.
	- No campo **Título**, insira `Weather Data`.
	- Deixe o campo **Nome** como `weather-data` quando ele é preenchido enquanto você insere seu título.	
	- Deixe o campo de Caminho **Base** como `/weather-data`.
	- Deixe o campo **Versão** como `1.0.0`.
7. Expanda **Propriedades adicionais** para especificar propriedades adicionais para a API.
	- No campo **Modelo de API**, selecione **Padrão** para indicar que você deseja usar o modelo padrão para criar a definição da API.
	- Deixe os campos restantes inalterados.
![](images/new-api-1.png)
8. Inclua sua API para um novo Produto e, em seguida, criar a definição de API.
	- Selecione **Incluir um produto**.
	- No campo **Título**, use `Weather Data product` como o padrão.
	- Deixe os campos **Nome** e **Versão** inalterados.
	- Assegure-se de que a caixa de seleção **Publicar este produto em um catálogo** esteja selecionada e, em seguida, selecione **Ambiente de simulação** como o Catálogo de destino.
![](images/new-api-2.png)
	- Clique em **Criar API**. A guia **Design** para o rascunho de sua definição de API é aberta.
9. Sua API está agora criada. A página Design é exibida. Clique em **Segurança** na barra de navegação.
![](images/api-security-1.png)
10. Desmarque a opção  ** ClientID ** .
![](images/api-security-2.png)
	>![](images/info.png)
	>Você pode observar que há um ícone triangular amarelo que aparece próximo ao ícone de salvamento do disco.  Este é um aviso de que há definição que pode ter sido definida, mas ainda não usada. (Isso não afetará a definição de API.)
11. Na seção **Definições**, clique no ícone **Incluir definição** ![](images/add-icon.png) e, em seguida, expanda a nova definição clicando nela.
12. Nomeie a definição `Weather Data Output`.
13. A definição terá cinco propriedades. Clique em **Incluir propriedade** quatro vezes para incluir as propriedades adicionais. Renomeie o `Property Name` usando o seguinte como guia e use o padrão para `Description`, `Type` e `Example`:
	![](images/definition-new-1.png)
14. Na seção **Caminhos**, clique no ícone **Incluir caminho** ![](images/add-icon.png).
15. No campo **Caminho** de seu Caminho recém-criado, substitua o conteúdo por `/getweatherdata`.
16. Expanda a operação **GET /getweatherdata** clicando nela.
	![](images/path-new-1.png)
17. Para sua operação **GET /getweatherdata**, clique em **Incluir parâmetro** e, em seguida, em **Incluir novo parâmetro**.
18. Nomeie seu novo parâmetro `zip_code` e deixe o resto como padrão.
19. Na coluna **Esquema** da resposta **200 OK** na seção **Respostas**, selecione sua definição **Saída de dados de clima**. Para a resposta à chamada API, o objeto definido pela **Saída de dados de clima** será o objeto de resposta.
![](images/path-new-2.png)
20. Clique no ícone Salvar ![](images/save-icon.png) para salvar suas mudanças.

---
## Incluindo e configurando sua chamada de serviço da web
Para incluir e configurar as políticas de chamada e mapa que integram o serviço da web em sua definição de API, conclua as etapas abaixo.
1. Na seção **Serviços**, clique no ícone **Incluir serviço** ![](images/add-icon.png). A janela `Importar serviço da web do WSDL` é aberta.
![](images/upload-file-1.png)
2. Selecione **Fazer upload de arquivo**.
3. Na janela **Upload de arquivo**, especifique o local para o arquivo `weatherprovider.wsdl` que você transferiu por download em `step 2` da seção **Pré-requisitos** e clique em **Abrir** para continuar.
4. Selecione o serviço SOAP **weatherService** e, em seguida, clique em **Pronto**. Na seção **Serviços**, o serviço da web **WeatherService** é listado com uma única operação **weatherRequest**.
![](images/upload-file-2.png)

	![](images/services-add-1.png)	
5. Navegue para a guia **Montar** e, em seguida, assegure-se de que **Políticas do DataPower Gateway** seja selecionado.
6. Exclua a política **invoke** existente na tela passando o cursor sobre a política e, em seguida, clicando no ícone **Excluir política** ![](images/delete-icon.png).
![](images/delete-invoke-1.png)	
7. Na paleta, arraste o serviço da web **weatherRequest** para a caixa tracejada que é exibida na tela. Uma política de chamada e duas políticas de mapa são colocadas no conjunto. A primeira política do mapa designa variáveis à entrada de sua chamada de serviço da web, enquanto a segunda política designa saídas de sua chamada de serviço da web a variáveis. As saídas do primeiro mapa e as entradas do segundo mapa são gerados por meio do WSDL fornecido na etapa 4.
![](images/services-add-2.png)	
8. Clique na política do mapa **weatherRequest: input** e, em seguida, clique no ícone **Editar entradas** ![](images/edit-icon.png) na coluna Entrada da folha de propriedade.
	![](images/services-add-3.png)	
9. Clique em **+ parâmetros para operação** e selecione `get /getweatherdata`.
10. Clique em **Pronto** para incluir o parâmetro `zip_code`.
![](images/webservice-input-1.png)
11. Clique no círculo correspondente a **zip_code string** no lado de entrada e, em seguida, clique no círculo correspondente a **zipcode string** no lado de saída.  
	![](images/webservice-input-2.png)
12. Feche a folha de propriedade.
13. Clique na política do mapa **weatherRequest: output** na paleta e, em seguida, clique no ícone **Editar saídas** ![](images/edit-icon.png) na coluna Saída da folha de propriedade.
14. Selecione **+ saídas para operação** e selecione `get /getweatherdata`.
15. Selecione **Pronto** para incluir a definição de saída `Weather Data Output`.
	![](images/webservice-output-1.png)
16. Clique no círculo correspondente a **zip string** no lado de entrada e, em seguida, clique no círculo correspondente a **zip string** no lado de saída. Mapeie os parâmetros restantes usando o seguinte como um guia.
![](images/webservice-output-2.png)
17. Clique no ícone **Salvar** ![](images/save-icon.png) para salvar suas mudanças.

Você incluiu a chamada de serviço da web em seu conjunto e mapeou um parâmetro de entrada para a parte apropriada da solicitação SOAP e mapeou a parte apropriada do resposta SOAP para uma saída JSON.

---
## Testando sua definição de API
Para testar sua definição de API usando a ferramenta de teste do API Manager, conclua as etapas a seguir.
1. Clique no ícone **Teste** ![](images/test-icon.png) sob a guia **Conjunto** para revelar a área de janela de teste.
![](images/test-pane-1.png)
2. Se você tiver usado a ferramenta de teste anteriormente, clique em **Mudar configuração**.
3. Escolha `Weather Data product 1.0.0` na lista de produtos.
	![](images/choose-product-1.png)
4. Clique em **Publicar novamente o produto**.
5. Clique em **Avançar**.
6. Selecione `get /getweatherdata` na lista de operações.  
	![](images/select-operation-1.png)
7. Role para baixo para o campo **zip_code**, insira `90210`.  
	![](images/test-api-1.png)
8. Clique em **Chamar**. A API retorna o clima atual.  
	![](images/test-api-2.png)

---
## O que você fez neste tutorial
Neste tutorial, você concluiu as atividades a seguir:
1. Configurou uma definição de API de REST
2. Configurou uma API para chamar um serviço da web existente e retornar sua saída
3. Testou sua definição de API

---

## Próxima etapa

Proteja sua API usando [limitação de taxa](tut_rate_limit.html), [identificador e segredo do cliente](tut_secure_landing.html) ou [protegendo usando OAuth 2.0](tut_secure_oauth_2.html).

Criar > **Gerenciar** > Assegurar > Socializar > Analisar

[important]: ./images/important.png "Importante!"
[info]: ./images/info.png "Informações"
[troubleshooting]: ./images/troubleshooting.png "Resolução de problemas" 
