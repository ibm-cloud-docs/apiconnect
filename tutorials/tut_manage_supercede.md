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

# Superseding API Products
{: #tut_manage_supercede}

**Duration**: 15 mins  
**Skill level**: Beginner  

## Objective
{: #object_tut_manage_supercede}

In this tutorial, you will supersede an existing API with a new one.

---
## Prerequisites
{: #prereq_tut_manage_supercede}

1. [Set up your {{site.data.keyword.apiconnect_full}} instance](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_set_up_apic_instance).

2. Complete the [Replace an API product tutorial](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_manage_replace).

---

## Superceding an API Product
{: #super_tut_manage_supercede}

1. Log in to {{site.data.keyword.Bluemix_short}}: https://cloud.ibm.com.
2. In the {{site.data.keyword.Bluemix_notm}} **Dashboard**, click **Cloud Foundary Services**. Launch the {{site.data.keyword.apiconnect_short}} service. 
3. In {{site.data.keyword.apiconnect_short}}, make sure the navigation panel is open. If not, click **>>** to open it.  

  ![](images/cloud-apic-dashboard.png)

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

18.	Select **Supersede an existing product**.  
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
 

 
## Conclusion
{: #conclusion_tut_manage_supercede}

In this tutorial, you completed the following activities:

1. Updated an API product.
2. Superceded an existing API product with an updated API Product.
3. Migrated the subscription to the existing API Product to the updated API Product.

---








