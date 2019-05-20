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

# 保存及刪除 API 產品
{: #tut_manage_remove}

**持續時間**：15 分鐘  
**技能水準**：初學者 

## 目標
{: #object_tut_manage_remove}
在本指導教學中，您將刪除、保存及棄用 API。

---
## 必要條件
{: #prereq_tut_manage_remove}

1. [設定 {{site.data.keyword.apiconnect_full}} 實例](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_set_up_apic_instance)。

2. 完成[接替 API 產品指導教學](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_manage_supercede)。

---

## 刪除 API 產品
{: #delete_tut_manage_remove}

1. 登入 {{site.data.keyword.Bluemix_short}}：`https://cloud.ibm.com`。
2. 在 {{site.data.keyword.Bluemix_notm}} **儀表板**中，按一下 **Cloud Foundry 服務**。啟動 {{site.data.keyword.apiconnect_short}} 服務。 
3. 在 {{site.data.keyword.apiconnect_short}} 中，確定導覽畫面已開啟。否則，請按一下 **>>** 將它開啟。  

  ![](images/cloud-apic-dashboard.png)

4. 按一下**沙盤推演**，以開啟「沙盤推演」型錄。**附註**：您可能需要回到「儀表板」，才能查看可用的型錄。此外，您的儀表板頁面可能會以磚形式來顯示型錄，而非清單形式。
![](images/del-sandbox-list.png)

5. 按一下 **Weather Provider API 1.0.0** 行上的垂直省略符號。  
![](images/del-prod-list1.png)

6. 選取**從型錄中刪除**。  
![](images/del-del-from-cat.png)

7. 按一下**確定**。  
![](images/del-del-dialog.png)
    產品即會從型錄的產品清單中消失。目前無法予以回復。


## 保存 API 產品
{: #archive_tut_manage_remove}

1. 按一下 **Weather Provider API 2.0.0** 行上的垂直省略符號。  
![](images/del-prod-list2.png)

2. 選取**棄用**。  
![](images/del-select-retire.png)

3. 按一下**確定**。  
![](images/del-retire-dialog.png)

4. 按一下 **Weather Provider API 2.0.0** 行上的垂直省略符號。  
![](images/del-prod-list3.png)

5. 選取**保存**。  
![](images/del-select-archive.png)

6. 按一下**確定**。  
![](images/del-archive-dialog.png)
    產品即會從型錄的產品清單中消失。可以予以回復。

7. 按一下清單視圖圖示。  
![](images/del-prod-list4.png)

8. 勾選**已保存**。  
![](images/del-view-archived.png)

9. 按一下 **Weather Provider API 2.0.0** 行上的垂直省略符號。  
![](images/del-prod-list5.png)

10. 選取**取消保存**。  
![](images/del-unarchive.png)
    產品狀態即會變更為「已棄用」。
    ![](images/del-prod-list6.png)

 
 
## 結論
{: #conclusion_tut_manage_remove}

在本指導教學中，您已完成下列活動：

1. 已刪除 API 產品
2. 已棄用 API 產品
3. 已保存 API 產品
4. 已取消保存 API 產品

---












