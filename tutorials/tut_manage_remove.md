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

# Archiving and deleting API Products
**Duration**: 15 mins  
**Skill level**: Beginner 

## Prerequisites

1. [Set up your {{site.data.keyword.apiconnect_full}} instance](tut_prereq_set_up_apic_instance.html).

2. Complete the [Supercede an API product tutorial](tut_manage_supercede.html).

---
## Objective
In this tutorial, you will delete, archive, and retire an API.

---
## Deleting an API Product
1. Log in to {{site.data.keyword.Bluemix_short}}: [https://console.ng.bluemix.net/login ![External link icon](../../../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/login){:new_window}.

2. In the {{site.data.keyword.Bluemix_short}} Dashboard, launch the {{site.data.keyword.apiconnect_short}} service.
![](images/Bluemix.png)

3. In API Manager, if you have not previously pinned the UI navigation pane, click the **Navigate to** icon ![](images/navigate-to.png). The API Manager UI navigation pane opens. To pin the UI Navigation pane, click the **Pin menu** icon ![](images/pinned.png).

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

 
 
## What you accomplished in this tutorial
In this tutorial, you completed the following activities:

1. Deleted an API product
2. Retired an APIpProduct
3. Archived an API product
4. Unarchived an API product

---








