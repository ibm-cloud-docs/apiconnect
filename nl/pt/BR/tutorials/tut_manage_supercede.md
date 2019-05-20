---

copyright:
  years: 2019
lastupdated: "2017-3-18"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial


---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Suplantando produtos de API
{: #tut_manage_supercede}

**Duração**: 15 min  
**Nível de qualificação**: iniciante  

## Objetivo
{: #object_tut_manage_supercede}

Neste tutorial, você irá suplantar uma API existente por uma nova.

---
## Pré-requisito
{: #prereq_tut_manage_supercede}

1. [Configure sua instância do {{site.data.keyword.apiconnect_full}}](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_set_up_apic_instance).

2. Conclua o [tutorial Substituir um produto de API](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_manage_replace).

---

## Suplantando uma API de Produto
{: #super_tut_manage_supercede}

1. Efetue login no {{site.data.keyword.Bluemix_short}}: https://cloud.ibm.com.
2. No **Painel** do {{site.data.keyword.Bluemix_notm}}, clique em **Serviços do Cloud Foundry**. Ative o serviço {{site.data.keyword.apiconnect_short}}. 
3. No {{site.data.keyword.apiconnect_short}}, certifique-se de que o painel de navegação esteja aberto. Caso contrário, clique em **>>** para abri-la.  

  ![](images/cloud-apic-dashboard.png)

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
 

 
## Conclusão
{: #conclusion_tut_manage_supercede}

Neste tutorial, você concluiu as atividades a seguir:

1. Atualizou um produto de API.
2. Substituiu um produto de API existente por um produto de API atualizado.
3. Migrou a assinatura do Produto de API existente para o Produto de API atualizado.

---












