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

# 归档和删除 API 产品
**持续时间**：15 分钟  
**技能级别**：初学者 

## 先决条件

1. [设置 {{site.data.keyword.apiconnect_full}} 实例](tut_prereq_set_up_apic_instance.html)。

2. 完成[取代 API 产品](tut_manage_supercede.html)教程。

---
## 目标
在本教程中，您将删除、归档和引退 API。

---
## 删除 API 产品
1. 登录到 {{site.data.keyword.Bluemix_short}}：[https://console.ng.bluemix.net/login ![外部链接图标](../../../icons/launch-glyph.svg "外部链接图标")](https://console.ng.bluemix.net/login){:new_window}。

2. 在 {{site.data.keyword.Bluemix_short}}“仪表板”中，启动 {{site.data.keyword.apiconnect_short}} 服务。
![](images/Bluemix.png)

3. 在 API Manager 中，如果先前未锁定 UI 导航窗格，请单击**导航至**图标 ![](images/navigate-to.png)。这将打开 API Manager UI 导航窗格。要锁定 UI 导航窗格，请单击**锁定菜单**图标 ![](images/pinned.png)。

4. 单击**沙箱**以打开“沙箱”目录。**注**：您可能需要返回到“仪表板”来查看可用的目录。此外，“仪表板”页面可能会将目录显示为磁贴而不是列表。
![](images/del-sandbox-list.png)

5. 单击 **Weather Provider API 1.0.0** 行上的垂直省略号。  
![](images/del-prod-list1.png)

6. 选择**从目录中删除**。  
![](images/del-del-from-cat.png)

7. 单击**确定**。  
![](images/del-del-dialog.png)
    该产品将从目录中的产品列表中消失。此时无法对其进行恢复。


## 归档 API 产品
1. 单击 **Weather Provider API 2.0.0** 行上的垂直省略号。  
![](images/del-prod-list2.png)

2. 选择**引退**。  
![](images/del-select-retire.png)

3. 单击**确定**。  
![](images/del-retire-dialog.png)

4. 单击 **Weather Provider API 2.0.0** 行上的垂直省略号。  
![](images/del-prod-list3.png)

5. 选择**归档**。  
![](images/del-select-archive.png)

6. 单击**确定**。  
![](images/del-archive-dialog.png)
    该产品将从目录中的产品列表中消失。可以对其进行恢复。

7. 单击“列表视图”图标。  
![](images/del-prod-list4.png)

8. 选中**已归档**。  
![](images/del-view-archived.png)

9. 单击 **Weather Provider API 2.0.0** 行上的垂直省略号。  
![](images/del-prod-list5.png)

10. 选择**取消归档**。  
![](images/del-unarchive.png)
    产品的状态将更改为“已引退”。
![](images/del-prod-list6.png)

 
 
## 在本教程中完成的操作
在本教程中，您已完成以下活动：

1. 删除 API 产品
2. 引退 API 产品
3. 归档 API 产品
4. 取消归档 API 产品

---












