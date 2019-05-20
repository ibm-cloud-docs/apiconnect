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

# 设置 API Connect 实例
{: #tut_prereq_set_up_apic_instance}

**持续时间**：15 分钟  
**技能级别**：初学者  


## 先决条件
{: #prereq_tut_prereq_set_up_apic_instance}

1. IBM 标识
2. {{site.data.keyword.Bluemix_short}} 帐户
3. 至少使用 _Lite_ 套餐的 {{site.data.keyword.apiconnect_full}} 实例


<table>
  <tr><td><b>IBM 标识</b>：用于访问 IBM 的所有应用程序、社区、支持等<br>
    <b>{{site.data.keyword.Bluemix_notm}}</b>：托管 {{site.data.keyword.apiconnect_short}} 以及其他应用程序和服务的 IBM 云平台<br>
    <b>{{site.data.keyword.apiconnect_short}} Lite</b>：在 {{site.data.keyword.Bluemix_notm}} 上托管的 {{site.data.keyword.apiconnect_short}} 免费版本</td></tr>
  </table>  


---


1. 在以下 URL 上注册 IBM Cloud 标识：[https://cloud.ibm.com/registration/ ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://cloud.ibm.com/registration/){: #new_window}。

	已有 IBM 标识？那么请跳过注册，只需在以下 URL 上创建免费的 {{site.data.keyword.Bluemix_short}} 帐户：[https://cloud.ibm.com/ ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://cloud.ibm.com/){: #new_window}。  

2. 拥有 IBM 标识和 {{site.data.keyword.Bluemix_notm}} 帐户后，创建 {{site.data.keyword.apiconnect_short}} 实例。  
  a. 登录到 {{site.data.keyword.Bluemix_notm}}：[https://cloud.ibm.com/login ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://cloud.ibm.com/login){: #new_window}。  
  ![](images/cloud_login_page.png)  
  b. 在 {{site.data.keyword.Bluemix_notm}} 中创建_组织_。首次登录时，系统将提示您执行此操作。  
  ![](images/prereqs-2.png)
  c. 创建_空间_。  
  ![](images/prereqs-3.png)
  d. 转至 [https://console.ng.bluemix.net/catalog/services/api-connect ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://console.ng.bluemix.net/catalog/services/api-connect){: #new_window}。  
  ![](images/prereqs-4.png)  
  e. 选择 _Lite_ 价格套餐（免费），然后单击**创建**以开始。  
  ![](images/lite-plan.png)  
