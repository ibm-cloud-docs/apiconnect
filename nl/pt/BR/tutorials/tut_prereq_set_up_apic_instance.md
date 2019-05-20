---

copyright:
  years: 2019
lastupdated: "2019-3-14"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorials

subcollection: apiconnect

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Configurando uma instância do API Connect
{: #tut_prereq_set_up_apic_instance}

**Duração**: 15 min  
**Nível de qualificação**: iniciante  


## Pré-requisito
{: #prereq_tut_prereq_set_up_apic_instance}

1. Um IBMid
2. Um {{site.data.keyword.Bluemix_short}} conta
3. Uma instância do {{site.data.keyword.apiconnect_full}} com pelo menos um plano _Lite_


<table>
  <tr><td><b>IBMid</b>: usado para acessar todos os apps da IBM, comunidades, suporte e mais
    <br>
    <b>{{site.data.keyword.Bluemix_notm}}</b>: a plataforma de nuvem da IBM que hospeda o {{site.data.keyword.apiconnect_short}} junto com outros apps e serviços<br>
    <b>{{site.data.keyword.apiconnect_short}} Lite</b>: uma versão grátis do {{site.data.keyword.apiconnect_short}} hospedada no {{site.data.keyword.Bluemix_notm}}</td></tr>
  </table>  


---


1. Inscreva-se para obter o seu ID do IBM Cloud na URL a seguir: [https://cloud.ibm.com/registration/ ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.ibm.com/registration/){: #new_window}.

	Já tem um IBMid? Em seguida, ignore o registro e simplesmente crie sua conta grátis do {{site.data.keyword.Bluemix_short}} na URL a seguir: [https://cloud.ibm.com/ ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.ibm.com/){: #new_window}.  

2. Quando você tiver seu IBMid e conta do {{site.data.keyword.Bluemix_notm}}, crie sua instância do {{site.data.keyword.apiconnect_short}}.  
  a. Efetue login no {{site.data.keyword.Bluemix_notm}}: [https://cloud.ibm.com/login ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.ibm.com/login){: #new_window}.  
  ![](images/cloud_login_page.png)  
  b. Crie sua _organização_ no {{site.data.keyword.Bluemix_notm}}. Você será solicitado a fazer isso na primeira vez que efetuar login.  
  ![](images/prereqs-2.png)
  c. Crie seu _espaço_.  
  ![](images/prereqs-3.png)
  d. Acesse [https://console.ng.bluemix.net/catalog/services/api-connect ![External link icon](../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/catalog/services/api-connect){: #new_window}.  
  ![](images/prereqs-4.png)  
  e. Selecione o plano de precificação _Lite_ (grátis) e clique em **Criar** para iniciar.  
  ![](images/lite-plan.png)  
