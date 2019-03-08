---

copyright:
  years: 2017
lastupdated: "2017-10-31"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Replacing an API Product
{: #tut_manage_replace}

**Duration**: 15 mins  
**Skill level**: Beginner  

## Objective
{: #object_tut_manage_replace}
In this tutorial, you will update an existing API product by replacing it with a newer one. When an API product is replaced, the changes take effect immediately and all application subscriptions are updated automatically.  

---
## Prerequisites
{: #prereq_tut_manage_replace}

1. [Set up your {{site.data.keyword.apiconnect_full}} instance](/docs/services/apiconnect/tutorials?topic=tut_prereq_set_up_apic_instance).

2. Complete one of the following tutorials:
 
    - [Import an OpenAPI2.0 spec and proxy an existing REST service](/docs/services/apiconnect/tutorials?topic=tut_rest_landing)
       **or**  
    - [Add a New API Spec and Invoke an Existing REST Service](/docs/services/apiconnect/tutorials?topic=tut_rest_landing).

---

## Replacing an API Product
{: #repl_api_prod_tut_manage_replace}}

1. Log in to {{site.data.keyword.Bluemix_short}}: [https://console.ng.bluemix.net/login ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/login){: #new_window}.

2. In the {{site.data.keyword.Bluemix_notm}} Dashboard, launch the {{site.data.keyword.apiconnect_short}} service.
![](images/Bluemix.png)

3. In API Manager, if you have not previously pinned the UI navigation pane, click the **Navigate to** icon ![](images/navigate-to.png). The API Manager UI navigation pane opens. To pin the UI Navigation pane, click the **Pin menu** icon ![](images/pinned.png).

4. Click **Drafts** > **APIs**.

5. In the APIs panel, click **Weather Provider API** to open the REST proxy API.  
![](images/rep-api-list.png)

6. Change the **Version** to 2.0.0.  

7. Click the disk icon to save the API changes.  
![](images/rep-change-version.png)

8. Click **All APIs**.  
![](images/rep-all-apis.png)

9. Click **Products**.  
![](images/rep-api-list-2.png)

10.	Select **Weather Provider API Product**.  
![](images/rep-draft-prod-list.png)

11.	Change the **Version** to 2.0.0. Enter `Updated API` in the **Description** field. Click the disk icon to save the changes.  
![](images/rep-update-prod.png)

12.	Click the **Stage** icon to upload the new version. Select the **Sandbox** catalog if it is not already selected.
![](images/rep-stage-prod-2.png)
    **Note**: It is possible to stage a new version to a different catalog, allowing control of what audience of developers can see this version. This capability can be helpful when moving API products from development to test to production.

13.	Click **>>** to open the navigation menu, and select **Dashboard**.  
![](images/rep-dashboard.png)

14.	Click **Sandbox**.  

15.	Click the vertical ellipsis on the **Weather Provider API Product 2.0.0 Staged** line.  
![](images/rep-dash-prod-list-2.png)

16.	Select **Replace an existing product**.  
![](images/rep-replace-prod.png)

17.	Select **Weather Provider API Product 1.0.0** in the list of products presented. Click **Next**.  
![](images/rep-replace-dialog.png)

18.	Select **Default plan**. Click **Replace**.  
![](images/rep-replace-dialog-2.png)

    As a result of this replacement, the Weather Provider API Product 1.0.0 is retired, and the Weather Provider API Product 2.0.0  is published. **Note**: It is possible to change the plan associated with this product during the replacement process. This is an easy way to alter the plan for an API product.
 ![](images/rep-prod-retired.png) 
 

## Conclusion
{: #conclusion_tut_manage_replace}

In this tutorial, you completed the following activities:
1. Updated an API product.
2. Replaced an existing API product with an updated API product.

---








