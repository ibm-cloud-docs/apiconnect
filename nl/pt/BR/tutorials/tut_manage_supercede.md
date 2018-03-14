---

copyright:
  years: 2017
lastupdated: "2017-10-31"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Suplantando produtos de API
**Duração**: 15 min  
**Nível de qualificação**: iniciante  

## Pré-requisito

1. [Configure sua instância do {{site.data.keyword.apiconnect_full}}](tut_prereq_set_up_apic_instance.html).

2. Conclua o [tutorial Substituir um produto de API](tut_manage_replace.html).

---
## Objetivo
Neste tutorial, você irá suplantar uma API existente por uma nova.

---
## Suplantando uma API de Produto
1. Efetue login no {{site.data.keyword.Bluemix_short}}: [https://console.ng.bluemix.net/login ![Ícone de link externo](../../../icons/launch-glyph.svg "Ícone de link externo")](https://console.ng.bluemix.net/login){:new_window}.

2. No Painel do {{site.data.keyword.Bluemix_notm}}, ative o serviço {{site.data.keyword.apiconnect_short}}. ![](images/Bluemix.png)

3. No API Manager, se você não tiver fixado anteriormente a área de janela de navegação da UI, clique no ícone **Navegar para** ![](images/navigate-to.png). A área de janela de navegação da UI do API Manager é aberta. Para fixar a área de janela de navegação da UI, clique no ícone do **menu Fixar** ![](images/pinned.png).

4. Clique em **Ambiente de simulação** para abrir o catálogo Ambiente de simulação. **Nota**: sua tela pode mostrar tiles em vez de uma lista de catálogos.
![](images/del-sandbox-list.png)

4. Clique em **Rascunhos** > **APIs**.

5. No painel APIs, clique em **API do Provedor de clima** para abrir a API do proxy de REST.  
![](images/rep-api-list.png)

6. Mude a **Versão** para 3.0.0.

7. Clique no ícone de disco para salvar as mudanças da API.  
![](images/sup-change-version.png)

8. Clique em **Todas as APIs**.  
![](images/rep-all-apis.png)

9. Clique em **Produtos**.  
![](images/sup-prods.png)

10.	Selecione **Weather Provider API Product 2.0.0**.  
![](images/sup-draft-prod-list.png)

11.	Mude a **Versão** para 3.0.0. Clique no ícone de disco para salvar as mudanças. Clique no ícone **Montar**.  
![](images/sup-change-prod-vers-3.png)

12.	Clique em **>>** para abrir a área de janela de navegação, em seguida, selecione **Painel**.  
![](images/rep-dashboard.png)

13.	Clique em **Ambiente de simulação**.

14.	Clique em **Comunidade**.  
![](images/sup-sand-dash.png)

15.	Clique em **Assinaturas**.  
![](images/sup-comm-orgs.png)

16.	Observe as assinaturas do aplicativo para o Weather Provider API Product 2.0.0. Clique em **Produtos**.
![](images/sup-scriptions-200.png)  

17.	Clique nas reticências verticais na linha **Weather Provider API Product 3.0.0 montado**.  
![](images/sup-stage-prod-3.png)

18.	Selecione **Suplantar um produto existente**.  
![](images/sup-super-prod.png)

19.	Selecione **Weather Provider API Product 2.0.0** na lista de produtos apresentados. Clique em **Avançar**.  
![](images/sup-super-dialog-1.png)

20.	Selecione **Plano padrão**. Clique em **Suplantar**.  
![](images/sup-super-dialog-2.png)
    Como resultado dessa substituição, o Weather Provider API Product 2.0.0 é descontinuado e o Weather Provider API Product 3.0.0 é publicado.  
![](images/sup-dash-prods-3.png) 
 
21.	Clique em **Comunidade >> Assinaturas**.  
![](images/sup-scriptions-200.png)
 
22.	Clique nas reticências verticais na linha **Weather Provider API Product 2.0.0**. Selecione **Gerenciar**.  
![](images/sup-dots-manage.png) 

23.	Selecione **Plano padrão** sob Weather Provider API Product 3.0.0. Clique em **Migrar**.  
![](images/sup-migrate-dialog.png)
    Como resultado desta migração, o Weather Provider API Product 2.0.0 é migrado para o Weather Provider API Product 3.0.0.  
![](images/sup-migrated.png) 
 

 
## O que você realizou neste tutorial
Neste tutorial, você concluiu as atividades a seguir:

1. Atualizou um produto de API.
2. Substituiu um produto de API existente por um produto de API atualizado.
3. Migrou a assinatura do Produto de API existente para o Produto de API atualizado.

---












