---

copyright:
  years: 2017
lastupdated: "2017-10-19"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Substituindo um Produto de API
**Duração**: 15 min  
**Nível de qualificação**: iniciante  


## Pré-requisito

1. [Configure sua instância do {{site.data.keyword.apiconnect_full}}](tut_prereq_set_up_apic_instance.html).

2. Conclua um dos tutoriais a seguir:
 
    - [Importar uma especificação OpenAPI2.0 e transmitir por proxy um serviço REST existente](tut_rest_landing.html) **ou**  
    - [Incluir uma nova especificação de API e chamar um serviço REST existente](tut_rest_landing.html).

---
## Objetivo
Neste tutorial, você irá atualizar um produto de API existente substituindo-o por um mais novo. Quando um produto de API é substituído, as mudanças entram em vigor imediatamente e todas as assinaturas do aplicativo são atualizadas automaticamente.  


---
## Substituindo um Produto de API
{: #repl_api_prod}

1. Efetue login no {{site.data.keyword.Bluemix_short}}: [https://console.ng.bluemix.net/login ![Ícone de link externo](../../../icons/launch-glyph.svg "Ícone de link externo")](https://console.ng.bluemix.net/login){:new_window}.

2. No Painel do {{site.data.keyword.Bluemix_short}}, ative o serviço {{site.data.keyword.apiconnect_short}}. ![](images/Bluemix.png)

3. No API Manager, se você não tiver fixado anteriormente a área de janela de navegação da UI, clique no ícone **Navegar para** ![](images/navigate-to.png). A área de janela de navegação da UI do API Manager é aberta. Para fixar a área de janela de navegação da UI, clique no ícone do **menu Fixar** ![](images/pinned.png).

4. Clique em **Rascunhos** > **APIs**.

5. No painel APIs, clique em **API do Provedor de clima** para abrir a API do proxy de REST.  
![](images/rep-api-list.png)

6. Mude a **Versão** para 2.0.0.  

7. Clique no ícone de disco para salvar as mudanças da API.  
![](images/rep-change-version.png)

8. Clique em **Todas as APIs**.  
![](images/rep-all-apis.png)

9. Clique em **Produtos**.  
![](images/rep-api-list-2.png)

10.	Selecione **Weather Provider API Product**.  
![](images/rep-draft-prod-list.png)

11.	Mude a **Versão** para 2.0.0. Insira `Updated API` no campo **Descrição**. Clique no ícone de disco para salvar as mudanças.  
![](images/rep-update-prod.png)

12.	Clique no ícone **Montar** para fazer upload da nova versão. Selecione o catálogo **Ambiente de simulação** se ele ainda não estiver selecionado.
![](images/rep-stage-prod-2.png)
**Nota**: é possível montar uma nova versão em um catálogo diferente, permitindo controle de qual público de desenvolvedores pode ver essa versão. Esse recurso pode ser útil ao mover os produtos de API de desenvolvimento para teste para produção.

13.	Clique em **>>** para abrir o menu de navegação e selecione **Painel**.  
![](images/rep-dashboard.png)

14.	Clique em **Ambiente de simulação**.  

15.	Clique nas reticências verticais na linha **Weather Provider API Product 2.0.0 montado**.  
![](images/rep-dash-prod-list-2.png)

16.	Selecione **Substituir um produto existente**.  
![](images/rep-replace-prod.png)

17.	Selecione **Weather Provider API Product 1.0.0** na lista de produtos apresentados. Clique em **Avançar**.  
![](images/rep-replace-dialog.png)

18.	Selecione **Plano padrão**. Clique em **Substituir**.  
![](images/rep-replace-dialog-2.png)

    Como resultado dessa substituição, o Weather Provider API Product 1.0.0 é desativado e o Weather Provider API Product 2.0.0 é publicado. **Nota**: é possível mudar o plano associado a esse produto durante o processo de substituição. Esta é uma maneira fácil de alterar o plano para um produto de API.
![](images/rep-prod-retired.png)


## O que você realizou neste tutorial

Neste tutorial, você concluiu as atividades a seguir:
1. Atualizou um produto de API.
2. Substituiu um produto de API existente por um produto de API atualizado.

---












