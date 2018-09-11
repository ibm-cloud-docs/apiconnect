---
copyright:
  years: 2017
lastupdated: "2017-10-24"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Configurando um Catálogo

É possível criar e configurar seus Catálogos do API Manager. Os catálogos são úteis para
separar Produtos e APIs para teste antes de torná-los disponíveis para Organizações do desenvolvedor.
Ao configurar um Catálogo, também é possível configurar a marca customizada para que você
não tenha que usar a URL da API padrão fornecida pelo API Manager.

Conclua as etapas a seguir para criar seu Catálogo:

1. Clique em **Navegar para** <img alt="Ícone Navegar para" src="images/navigate_to_icon.png"> > **Painel**.

2. Clique em **+ Incluir** > **Catálogo**.
A janela **Incluir catálogo** é exibida.

3.  Insira o nome de seu novo Catálogo no campo **Nome de exibição**.

4. Insira o texto desejado para formar o segmento do Catálogo da URL no campo
**Nome**.
	**NOTA:** o campo **Nome** pode conter somente caracteres alfanuméricos minúsculos (a-z
e 0-9) ou caracteres de hífen (-). Um hífen
não pode ser usado como o primeiro ou último caractere no nome.

5. Clique em **Incluir (Add)**. Seu Catálogo é criado e exibido no painel.

6. Para configurar o Catálogo, clique no nome do Catálogo e, em seguida, clique em **Configurações** > **Informações** e continue com as etapas a seguir:
  1. Se o novo Catálogo for um de desenvolvimento, selecione **Modo de desenvolvimento**.
Se você selecionar o modo de desenvolvimento, as ações de preparação e publicação serão forçadas, ou seja,
se você publicar novamente um Produto publicado anteriormente, ele será sobrescrito sem aviso. Se forem localizados
conflitos, eles serão resolvidos automaticamente pelo sistema. Ações de cancelamento de publicação acontecem automaticamente.
	**Nota:** as caixas de aprovação não são exibidas para catálogos de desenvolvimento. Não é possível ativar o processo de
aprovação para ciclos de vida.
  2. Se você desejar ativar a assinatura automática para o Catálogo, selecione
**Assinatura automática**.
A ativação da assinatura automática facilita o teste de suas APIs porque um aplicativo de teste é usado com um ID de cliente e um segredo do cliente fornecidos previamente. O aplicativo de teste é automaticamente inscrito em todos os Planos no Catálogo, portanto, não é necessário especificar um plano ou um aplicativo durante o teste. 
    **Nota:** a assinatura automática está disponível somente para um catálogo de desenvolvimento.
  3. Se o Catálogo for o de preparação padrão, selecione **Padrão**. Em seguida,
as chamadas para APIs que foram publicadas no Catálogo poderão usar uma URL mais curta que não inclua
o nome do Catálogo.
    **Nota:** é possível selecionar apenas **Padrão** para um Catálogo.
  4. **Opcional**: clique em **Terminais** e preencha os campos a seguir:
        - **URL de gateway customizada**: no campo de texto	URL de Gateway customizada, insira uma URL. Você usará a URL do gateway customizado se desejar
obter a marca customizada de URLs para APIs implementadas no {{site.data.keyword.apiconnect_short}}, em vez de usar a URL padrão
gerada pelo API Manager.
        Por padrão, a URL do gateway do {{site.data.keyword.apiconnect_short}}
possui o formato a
seguir:
        ```
        https://gateway_cluster_hostname/organization_name/Catalog_name
        ```
        No entanto,
é possível substituir o padrão especificando uma URL que seja mais apropriada para sua empresa, por
exemplo, `https://api.mycompany.com`. Todos os terminais de API que forem exibidos no
Portal do Desenvolvedor irão então refletir a URL especificada.
			**Notas:**
		    - Deve-se configurar uma entrada DNS que mapeie seu nome de host e domínio customizados para a URL de gateway
padrão.
		    - Para que os terminais de uma API reflitam sua URL de gateway customizada, deve-se configurar a API para ser
aplicada pelo gateway do API Connect. Para obter mais informações, veja [Especificando um host alternativo para uma API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){:new_window}.
		    - Assegure-se de que a mesma URL de gateway customizada não seja aplicada a múltiplos
Catálogos porque o comportamento nesse cenário é indefinido.
				**DICA**: ao chamar a API, também é possível configurar o cabeçalho de host HTTP na solicitação de API para o valor especificado no campo URL de gateway customizada.

	    - **URL de API customizada**: no campo de texto	URL de API customizada, insira a URL. Você usará a URL da API customizada para especificar a URL
para APIs implementadas em um gateway de terceiro.

	    A URL da API customizada representa o terminal pelo qual a API é conhecida externamente, isto é, o
terminal publicado no Portal do Desenvolvedor e usado por um desenvolvedor de aplicativos para chamar ou
anunciar a API.

	    Se você estiver usando um gateway de terceiros ou um balanceador de carga externo
nesse Catálogo, forneça a URL nesse campo. Todos os terminais de API que forem exibidos no Portal do Desenvolvedor irão então refletir a
URL especificada. Esses terminais existem no gateway ou no balanceador de carga de terceiro e projetam um
endereço virtual, exposto a consumidores de API, que é mapeado para os terminais de proxy de API ou de conjunto de API
no gateway. Os terminais derivados da URL da API customizada são geralmente publicados nos
portais do desenvolvedor de produção para anunciar o endereço da API.

	    **Nota:** se você especificar uma URL de API customizada para um catálogo, ela terá precedência sobre qualquer nome de host que for especificado quando você configurar a API. Para obter mais informações, veja [Especificando um host alternativo para uma API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){:new_window}.

	    - **Nome do host para chamadas API do Portal do Desenvolvedor**: na área de janela	Terminal de API da porta, insira um nome de host para chamadas API do Portal do Desenvolvedor. O nome do
host que for inserido pode ser o nome do host de seu serviço de gerenciamento. Para acessar a API do
Portal do Desenvolvedor dentro do contexto de um Portal do Desenvolvedor, deve-se configurar o nome do host de base para as
chamadas API do Portal do Desenvolvedor. Essa ação permite que o API Manager
mapeie seu nome de host para a organização do provedor e o Catálogo das chamadas de API do
Portal do Desenvolvedor, em vez de requerer que você consulte e o inclua em suas chamadas.

7. Clique no ícone **Salvar**.

## Particionando um Catálogo
{: #apic_spaces}

Para usar o recurso de organização no
{{site.data.keyword.apiconnect_short}},
deve-se ativar Espaços em qualquer Catálogo no qual você requeira recursos de organização.

Para ativar Espaços em um Catálogo, conclua as etapas a seguir:
1. No Painel da UI do API Manager, selecione o Catálogo com o qual deseja trabalhar.

2. Clique em **Configurações** > **Visão geral** e clique no controle da régua de controle **Espaços**.

3. Na janela **Ativar espaços**, clique em **Ativar** e, em seguida, clique no ícone **Salvar** <img src="images/icon_save.png" alt="Ícone Salvar"/>.
Um link **Gerenciar espaços** é exibido abaixo da régua de
controle **Espaços** e um link **Espaços** é
incluído na área de janela de navegação. É possível gerenciar seus Espaços clicando em um
desses links.

Os Espaços são ativados para seu catálogo e um Espaço padrão, chamado Novo Espaço
é criado.

Para obter mais informações sobre o uso de organização, veja os tópicos do Knowledge Center, [Usando a organização no IBM API Connect ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.apionprem.doc/capic_syndication_using.html){:new_window}.
