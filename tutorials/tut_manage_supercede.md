---

copyright:
  years: 2017
lastupdated: "2017-09-20"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Superceding API Products
**Duration**: 15 mins  
**Skill level**: Intermediate  

## Prerequisites

1. [Set up your {{site.data.keyword.apiconnect_full}} instance](tut_prereq_set_up_apic_instance.html).

2. Complete the [Replace an API product tutorial](tut_manage_replace.html).

---
## Objective
In this tutorial, you will supercede an existing API with a new one.

---
## Superceding an API Product
1. Log in to {{site.data.keyword.Bluemix_short}}: [https://console.ng.bluemix.net/login ![External link icon](../../../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/login){:new_window}.

2. In the {{site.data.keyword.Bluemix_short}} Dashboard, launch the {{site.data.keyword.apiconnect_short}} service.
![](images/Bluemix.png)

3. In API Manager, if you have not previously pinned the UI navigation pane, click the **Navigate to** icon ![](images/navigate-to.png). The API Manager UI navigation pane opens. To pin the UI Navigation pane, click the **Pin menu** icon ![](images/pinned.png).

4. Click **Sandbox** to open the Sandbox catalog. **Note**: Your screen may show tiles rather than a list of catalogs.
![](images/del-sandbox-list.png)

4. Click **Drafts** > **APIs**.

5. In the APIs panel, click **Weather Provider API** to open the REST proxy API.  
![](images/rep-api-list.png)

6. Change the **Version** to 3.0.0.

7. Click the disk icon to save the API changes.  
![](images/sup-change-version.png)

8. Click **All APIs**.  
![](images/rep-all-apis.png)

9. Click **Products**.  
![](images/sup-prods.png)

10.	Select **Weather Provider API Product 2.0.0**.  
![](images/sup-draft-prod-list.png)

11.	Change the **Version** to 3.0.0. Click the disk icon to save the changes. Click the **Stage** icon.  
![](images/sup-change-prod-vers-3.png)

12.	Click **>>** to open the navigation pane, then select **Dashboard**.  
![](images/rep-dashboard.png)

13.	Click **Sandbox**.

14.	Click **Community**.  
![](images/sup-sand-dash.png)

15.	Click **Subscriptions**.  
![](images/sup-comm-orgs.png)

16.	Note the application subscriptions to Weather Provider API Product 2.0.0. Click **Products**.
![](images/sup-scriptions-200.png)  

17.	Click the vertical ellipsis on the **Weather Provider API Product 3.0.0 Staged** line.  
![](images/sup-stage-prod-3.png)

18.	Select **Supercede an existing product**.  
![](images/sup-super-prod.png)

19.	Select **Weather Provider API Product 2.0.0** in the list of products presented. Click **Next**.  
![](images/sup-super-dialog-1.png)

20.	Select **Default plan**. Click **Supercede**.  
![](images/sup-super-dialog-2.png)
    As a result of this replacement, the Weather Provider API Product 2.0.0 is deprecated, and the Weather Provider API Product 3.0.0 is published.  
![](images/sup-dash-prods-3.png) 
 
21.	Click **Community >> Subscriptions**.  
![](images/sup-scriptions-200.png)
 
22.	Click the vertical ellipsis on the **Weather Provider API Product 2.0.0** line. Select **Manage**.  
![](images/sup-dots-manage.png) 

23.	Select **Default plan** under Weather Provider API Product 3.0.0 . Click **Migrate**.  
![](images/sup-migrate-dialog.png)
    As a result of this migration, the Weather Provider API Product 2.0.0 is migrated to Weather Provider API Product 3.0.0.  
![](images/sup-migrated.png) 
 

 
## What you accomplished in this tutorial
In this tutorial, you completed the following activities:

1. Updated an API product.
2. Superceded an existing API product with an updated API product.
3. Migrated the subscription to the existing API product to the updated API product.

---








