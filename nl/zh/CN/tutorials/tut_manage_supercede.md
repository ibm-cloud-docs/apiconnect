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

# 取代 API 产品
{: #tut_manage_supercede}

**持续时间**：15 分钟  
**技能级别**：初学者  

## 目标
{: #object_tut_manage_supercede}

在本教程中，您将使用新的 API 取代现有 API。

---
## 先决条件
{: #prereq_tut_manage_supercede}

1. [设置 {{site.data.keyword.apiconnect_full}} 实例](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_set_up_apic_instance)。

2. 完成[替换 API 产品](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_manage_replace)教程。

---

## 取代 API 产品
{: #super_tut_manage_supercede}

1. 登录到 {{site.data.keyword.Bluemix_short}}：https://cloud.ibm.com。
2. 在 {{site.data.keyword.Bluemix_notm}} **仪表板**中，单击 **Cloud Foundary 服务**。启动 {{site.data.keyword.apiconnect_short}} 服务。 
3. 在 {{site.data.keyword.apiconnect_short}} 中，确保导航面板已打开。如果未打开，请单击 **>>** 将其打开。  

  ![](images/cloud-apic-dashboard.png)

4. 单击**草稿** > **API**。

5. 在“API”面板中，单击 **Weather Provider API** 以打开 REST 代理 API。  
![](images/rep-api-list.png)

6. 将**版本**更改为 3.0.0。

7. 单击“磁盘”图标以保存 API 更改。  
![](images/sup-change-version.png)

8. 单击**所有 API**。  
![](images/rep-all-apis.png)

9. 单击**产品**。  
![](images/sup-prods.png)

10.	选择 **Weather Provider API 产品 2.0.0**。  
![](images/sup-draft-prod-list.png)

11.	将**版本**更改为 3.0.0。单击“磁盘”图标以保存更改。单击**编译打包**图标。  
![](images/sup-change-prod-vers-3.png)

12.	单击 **>>** 以打开导航窗格，然后选择**仪表板**。  
![](images/rep-dashboard.png)

13.	单击**沙箱**。

14.	单击**社区**。  
![](images/sup-sand-dash.png)

15.	单击**预订**。  
![](images/sup-comm-orgs.png)

16.	记下对 Weather Provider API 产品 2.0.0 的应用程序预订。单击**产品**。
![](images/sup-scriptions-200.png)  

17.	单击**已编译打包的 Weather Provider API 产品 3.0.0** 行上的垂直省略号。  
![](images/sup-stage-prod-3.png)

18.	选择**取代现有产品**。  
![](images/sup-super-prod.png)

19.	在所提供的产品列表中选择 **Weather Provider API 产品 2.0.0**。单击**下一步**。  
![](images/sup-super-dialog-1.png)

20.	选择**缺省套餐**。单击**取代**。  
![](images/sup-super-dialog-2.png)
    进行此替换后，Weather Provider API 产品 2.0.0 已弃用，并且 Weather Provider API 产品 3.0.0 已发布。  
![](images/sup-dash-prods-3.png) 
 
21.	单击**社区 >> 预订**。  
![](images/sup-scriptions-200.png)
 
22.	单击 **Weather Provider API 产品 2.0.0** 行上的垂直省略号。选择**管理**。  
![](images/sup-dots-manage.png) 

23.	选择“Weather Provider API 产品 3.0.0”下的**缺省套餐**。单击**迁移**。  
![](images/sup-migrate-dialog.png)
    进行此迁移后，Weather Provider API 产品 2.0.0 已迁移到 Weather Provider API 产品 3.0.0。  
![](images/sup-migrated.png) 
 

 
## 结论
{: #conclusion_tut_manage_supercede}

在本教程中，您已完成以下活动：

1. 更新 API 产品。
2. 使用更新的 API 产品取代现有 API 产品。
3. 将对现有 API 产品的预订迁移到更新的 API 产品。

---












