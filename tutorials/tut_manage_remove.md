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

# Archiving and deleting API Products
{: #tut_manage_remove}

**Duration**: 15 mins  
**Skill level**: Beginner 

## Objective
{: #object_tut_manage_remove}
In this tutorial, you will delete, archive, and retire an API.

---
## Prerequisites
{: #prereq_tut_manage_remove}

1. [Set up your {{site.data.keyword.apiconnect_full}} instance](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_set_up_apic_instance).

2. Complete the [Supercede an API product tutorial](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_manage_supercede).

---

## Deleting an API Product
{: #delete_tut_manage_remove}

1. Log in to {{site.data.keyword.Bluemix_short}}: https://cloud.ibm.com.
2. In the {{site.data.keyword.Bluemix_notm}} **Dashboard**, click **Cloud Foundary Services**. Launch the {{site.data.keyword.apiconnect_short}} service. 
3. In {{site.data.keyword.apiconnect_short}}, make sure the navigation panel is open. If not, click **>>** to open it.  

  ![](images/cloud-apic-dashboard.png)

4. Click **Sandbox** to open the Sandbox catalog. **Note**: You may need to return to the Dashboard to see the available catalogs. Also, your dashboard page may show catalogs as tiles rather than a list.
![](images/del-sandbox-list.png)

5. Click the vertical ellipsis on the **Weather Provider API 1.0.0** line.  
![](images/del-prod-list1.png)

6. Select **Delete from catalog**.  
![](images/del-del-from-cat.png)

7. Click **OK**.  
![](images/del-del-dialog.png)
    The product disappears from the list of products in the catalog. It cannot be recovered at this point.


## Archiving an API Product
{: #archive_tut_manage_remove}

1. Click the vertical ellipsis on the **Weather Provider API 2.0.0** line.  
![](images/del-prod-list2.png)

2. Select **Retire**.  
![](images/del-select-retire.png)

3. Click **OK**.  
![](images/del-retire-dialog.png)

4. Click the vertical ellipsis on the **Weather Provider API 2.0.0** line.  
![](images/del-prod-list3.png)

5. Select **Archive**.  
![](images/del-select-archive.png)

6. Click **OK**.  
![](images/del-archive-dialog.png)
    The product disappears from the list of products in the catalog. It can be recovered.

7. Click the list view icon.  
![](images/del-prod-list4.png)

8. Check **Archived**.  
![](images/del-view-archived.png)

9. Click the vertical ellipsis on the **Weather Provider API 2.0.0** line.  
![](images/del-prod-list5.png)

10. Select **Unarchive**.  
![](images/del-unarchive.png)
    The product state changes to Retired.
    ![](images/del-prod-list6.png)

 
 
## Conclusion
{: #conclusion_tut_manage_remove}

In this tutorial, you completed the following activities:

1. Deleted an API Product
2. Retired an API Product
3. Archived an API Product
4. Unarchived an API Product

---








