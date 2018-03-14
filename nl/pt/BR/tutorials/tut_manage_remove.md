---

copyright:
  years: 2017
lastupdated: "2017-10-10"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Arquivando e excluindo produtos de API
**Duração**: 15 min  
**Nível de qualificação**: iniciante 

## Pré-requisito

1. [Configure sua instância do {{site.data.keyword.apiconnect_full}}](tut_prereq_set_up_apic_instance.html).

2. Conclua o [tutorial Substituir um produto de API](tut_manage_supercede.html).

---
## Objetivo
Neste tutorial, você irá excluir, arquivar e desativar uma API.

---
## Excluindo um Produto de API
1. Efetue login no {{site.data.keyword.Bluemix_short}}: [https://console.ng.bluemix.net/login ![Ícone de link externo](../../../icons/launch-glyph.svg "Ícone de link externo")](https://console.ng.bluemix.net/login){:new_window}.

2. No Painel do {{site.data.keyword.Bluemix_short}}, ative o serviço {{site.data.keyword.apiconnect_short}}. ![](images/Bluemix.png)

3. No API Manager, se você não tiver fixado anteriormente a área de janela de navegação da UI, clique no ícone **Navegar para** ![](images/navigate-to.png). A área de janela de navegação da UI do API Manager é aberta. Para fixar a área de janela de navegação da UI, clique no ícone do **menu Fixar** ![](images/pinned.png).

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

 
 
## O que você realizou neste tutorial
Neste tutorial, você concluiu as atividades a seguir:

1. Excluiu um Produto de API
2. Desativou um Produto de API
3. Arquivou um Produto de API
4. Desarquivou um Produto de API

---












