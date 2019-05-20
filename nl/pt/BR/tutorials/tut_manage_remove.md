---

copyright:
  years: 2019
lastupdated: "2019-3-15"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial


---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Arquivando e excluindo produtos de API
{: #tut_manage_remove}

**Duração**: 15 min  
**Nível de qualificação**: iniciante 

## Objetivo
{: #object_tut_manage_remove}
Neste tutorial, você irá excluir, arquivar e desativar uma API.

---
## Pré-requisito
{: #prereq_tut_manage_remove}

1. [Configure sua instância do {{site.data.keyword.apiconnect_full}}](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_set_up_apic_instance).

2. Conclua o [tutorial Suplantar um produto de API](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_manage_supercede).

---

## Excluindo um Produto de API
{: #delete_tut_manage_remove}

1. Efetue login no {{site.data.keyword.Bluemix_short}}: https://cloud.ibm.com.
2. No **Painel** do {{site.data.keyword.Bluemix_notm}}, clique em **Serviços do Cloud Foundry**. Ative o serviço {{site.data.keyword.apiconnect_short}}. 
3. No {{site.data.keyword.apiconnect_short}}, certifique-se de que o painel de navegação esteja aberto. Caso contrário, clique em **>>** para abri-la.  

  ![](images/cloud-apic-dashboard.png)

4. Clique em **Ambiente de simulação** para abrir o catálogo Ambiente de simulação. **Nota**: você pode precisar retornar para o Painel para ver os catálogos disponíveis. Além disso, sua página de painel pode mostrar catálogos como tiles em vez de uma lista.
![](images/del-sandbox-list.png)

5. Clique no botão de reticências verticais na linha **Weather Provider API 1.0.0**.  
![](images/del-prod-list1.png)

6. Selecione **Excluir do catálogo**.  
![](images/del-del-from-cat.png)

7. Clique em **OK**.  
![](images/del-del-dialog.png)
    O produto desaparece da lista de produtos no catálogo. Ele não pode ser recuperado neste momento.


## Arquivando um Produto de API
{: #archive_tut_manage_remove}

1. Clique nas reticências verticais na linha **API do Provedor de clima 2.0.0**.  
![](images/del-prod-list2.png)

2. Selecione **Desativar**.  
![](images/del-select-retire.png)

3. Clique em **OK**.  
![](images/del-retire-dialog.png)

4. Clique nas reticências verticais na linha **API do Provedor de clima 2.0.0**.  
![](images/del-prod-list3.png)

5. Selecione **Arquivar**.  
![](images/del-select-archive.png)

6. Clique em **OK**.  
![](images/del-archive-dialog.png)
    O produto desaparece da lista de produtos no catálogo. Ele pode ser recuperado.

7. Clique no ícone de visualização de lista.  
![](images/del-prod-list4.png)

8. Marque **Arquivado**.  
![](images/del-view-archived.png)

9. Clique nas reticências verticais na linha **API do Provedor de clima 2.0.0**.  
![](images/del-prod-list5.png)

10. Selecione **Desarquivar**.  
![](images/del-unarchive.png)
    O estado do produto muda para Obsoleto.
    ![](images/del-prod-list6.png)

 
 
## Conclusão
{: #conclusion_tut_manage_remove}

Neste tutorial, você concluiu as atividades a seguir:

1. Excluiu um Produto de API
2. Desativou um Produto de API
3. Arquivou um Produto de API
4. Desarquivou um Produto de API

---












