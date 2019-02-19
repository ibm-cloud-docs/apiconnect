---
copyright:
  years: 2017
lastupdated: "2017-12-15"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Managing Products
{: #managing_products}

For details of the ways in which you can manage your Products, see the IBM&reg; Knowledge Center documentation [Managing your Products ![External link icon](../icons/launch-glyph.svg "External link icon")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.apionprem.doc/task_product_management.html){: #new_window}.

## Product lifecycle
{: #prod_lifecycle_managing_products}

When you manage your Product versions, you move them through a series of lifecycle
states, from initially staging a draft Product version to an environment, through to publishing to
make the Product version available to your application developers, and to eventual retiring and
archiving. The following table and diagram describe the various Product lifecycle states for a
Product version.

<table summary="" id="apic_004__table_lym_rxj_gv" class="defaultstyle"><caption class="style-scope doc-content">Table 1. API Management Product lifecycle states</caption>
<thead class="style-scope doc-content">
<tr class="style-scope doc-content doc-tr-even">
<th style="width: 11.25%" id="d3569e1968" class="thleft thbot style-scope doc-content">State</th>
<th style="width: 88.75%" id="d3569e1970" class="thleft thbot style-scope doc-content">Description</th>
</tr>
</thead>
<tbody class="style-scope doc-content">
<tr class="style-scope doc-content doc-tr-odd">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">Draft</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">Product is not deployed and is not associated with an API Connect Catalog.</td>
</tr>
<tr class="style-scope doc-content doc-tr-even">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">Staged</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">An immutable copy of the Product version is deployed to the target
environment. Staged is the initial state when you stage from a draft Product. When a Product is in
the staged state, it is not yet visible to, or subscribable by, any developers.</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">Published</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">The Product version is visible to, and subscribable by, the targeted
developers or communities.</td>
</tr>
<tr class="style-scope doc-content doc-tr-even">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">Deprecated</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">The Product version is visible only to developers whose applications are
currently subscribed. No new subscriptions to the Product are possible.</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">Retired</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">The Product version cannot be viewed or subscribed to, and all of the
associated APIs are stopped. A retired Product version is displayed by default in the
Products page in the API Manager UI.</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">Archived</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">The Product version cannot be viewed or subscribed to, and all of the
associated APIs are stopped. The Product version is not displayed by default in the Products page in the API Manager UI.</td>
</tr>
</tbody>
</table>

### Product lifecycle flows
{: #prod_lifecycle_flows_managing_products}

The following diagram shows the possible lifecycle states for a Product version, and the Product management operations that move a Product version from
one lifecycle state to another; for example, the Retire operation moves a Product version from the
Published to the Retired state.

<img alt="Lifecycle state diagram for Product version" src="images/apic_plan_lifecycle.png">


## Creating a Product
{: #create_product_managing_products}

Create a Product to collect a set of APIs and Plans into one offering that you make
available to your developers. A Plan includes rate limit settings that can be applied to the Plan as
a whole, or specified for each operation in an API. Through Products and Plans, you have greater
control over what APIs your developers have access to. After you create a product, it must be
staged. Staging a product moves it to an active state that enables you to call and test the APIs
included within it. When a product is staged, it is not yet visible to any developers.

**Tip**: As well as using the method described in this task, you can also create a Product
when you create an API. If you create an API by using the Developer Toolkit command line interface,
a Product is automatically created for you. You can then change any of the Product settings by
opening your new Product in the **Products** page of the API Designer.

To create a Product by using the API Designer, complete the following
steps:
1. To open the API Designer user interface, open a command line and enter the following command:
```
apic edit
```
The API Designer opens in your default browser.

2. In the navigation pane of the API Designer, click **Products**.
The Products tab opens.

3. Click **Add** and then click **New Product**.
The Add a new product window opens.

4. Complete the following fields:
    - Title
    - Name
    - Version

5. Click **Add**.
The Design tab for the new Product opens.

6. **Optional**:
Enter description, contact, license, and terms of service information for the Product in the
**Info** section.

7. In the **Visibility** section, specify the users that you want the Product
to be visible to. You can choose **Public**, **Authenticated
users**, or **Custom**. If you select **Custom**,
use the **Type to add** field to search for the developer organizations or
communities that you want the Plans in the Product to be visible to.

    **Note:**
    To search for developer organizations or communities, the Product must be in the staged,
    published, or deprecated state. If the Catalog in which it is staged, published, or deprecated is
    not a sandbox Catalog, you cannot make other changes to the Product while it is in one of these
    states. For more information, see [Product lifecycle](#prod_lifecycle_managing_products).

8. Specify the users that can subscribe to the Product. You can choose **Authenticated
users** or **Custom**. If you select **Custom**, use
the **Type to add** field to search for the developer organizations or
communities that you want to be able to subscribe to the Plans in the Product.

9. In the APIs section, specify the APIs that you want to include in the Product.
    1. Click the **Add API** icon.
    2. Select the APIs that you want to include, then click **Apply**. The selected
    APIs are listed.

10. To make an API available to application developers, you must include it in a Plan. To add one
or more Plans to the Product, click the **Add Plan** icon.
    1. Expand the new Plan that has been created. If you have already added APIs to your Product,
these are automatically included.
    2. Rename your Plan in the **Title** and **Name** fields,
and optionally add a description.
    **Note:** A Default Plan is automatically created for you, and you can include your API in this Plan if
    you do not want to create your own. However, if you decide not to use the Default Plan you must
    delete it, as a Product cannot be staged if it includes any Plans that do not include APIs.

11. Verify that the APIs you require are included in the Plan.
    1. Expand the Plan to which you want to add an API.
    2. Under APIs included, ensure that the check boxes of the APIs you require are selected. If there
are APIs already selected, and you do not want them included in the Plan you are editing, clear
their check boxes.

12. **Optional**:
Add the billing information for your Plan. To add billing information, you must establish an account with a credit card processing service so your customers can pay with a credit card. Monthly billing Plans are billed on the same date of each month.

13. **Optional**:
If you want to tailor which operations from an API are included in the Plan, hover the cursor
over the API that contains the operation. Click the **Show operations** icon, and
then select or clear the check boxes for the operations you want to include or exclude.

14. **Optional**:
To add a rate limit to your Plan, clear the **Unlimited** check box and then
specify the rate limit that you want to apply. If the **Enforce hard limit**
check box is selected the Plan will stop applications from calling the API after reaching the rate
limit, otherwise a warning will be presented.

    **Note:** Applying a rate limit at the Plan level, creates a default rate limit that applies to each
    operation within the Plan. If you need to set specific rate limits for specific operations, you must
    set these within the operations themselves and this setting overrides the setting at the Plan
    level.

15. **Optional**:
Specify whether your Plan requires subscription approval. If you want subscriptions by
developers to require approval through the API Manager user interface, select **Require
subscription approval**; otherwise, ensure that the check box is cleared.

16. **Optional**:
Add a rate limit to an operation.
    1. Hover the cursor over the API that contains the operation, click the **Show
operations** icon.
    2. Hover the cursor over the operation that you want to apply a rate limit to. Click the
**Edit rate limit** icon.
    3. Ensure the **Unlimited** check box is cleared, and then specify the rate
limit that you want to apply. If the **Enforce hard limit** check box is selected
the Plan will stop applications from calling the API after reaching the rate limit, otherwise a
warning will be presented.

- Click the **Save** icon  to save your changes.

You have created a Product, and specified a set of APIs and Plans into one offering that you
can now make available to your developers.
Next, stage your poduct to a catalog as explained in the next section, [Staging a Product](#stage_product_managing_products}).


## Staging a Product
{: #stage_product_managing_products}

Stage a Product to create a specific version of that Product in a Catalog, before
publishing. When a Product is in the staged state, it is not yet visible to, or subscribable by, any
developers.

**Note:** The API Manager UI also includes the ability to stage Products, however the preferred method
for these tasks is by using the API Designer UI, as described in the following procedure.

1. In the navigation pane of the API Designer, click **Products**.
The Products tab opens.

2. Click the **Product** that you want to work with. If you have more than one
version of the Product, ensure that you click the version that you want to work with.

3. Click the **Publish** icon.

4. If the Catalog to which you want to stage the Product is shown in the list:
    1. Select the Catalog that you require. 
    2. Select **Stage only (products will not
be published)**, followed by **Publish**. Your Product has been
staged.

5. If the Catalog to which you want to stage the Product is not shown in the list:
    1. Click **Add and Manage Targets**.
    2. Click **Add {{site.data.keyword.Bluemix_notm}} target**.
    3. Select the {{site.data.keyword.Bluemix_short}}
**Region** that you want to publish to.
    4. Select the {{site.data.keyword.Bluemix_notm}}
**Organization** that you want to publish to.
    5. A list of Catalogs is displayed. Select the Catalog that you want to publish to.
    6. Click **Next**.
    7. If you have a LoopBack application that you want to publish, select the App to publish to.
Otherwise, select **None**.
    8. Click **Save**.
    9. Click **Publish** again and select the target that you just added.
    10. Select the required Catalog
    11. Select **Stage only**.
    12. Click **Publish**.

Your Product has been staged to a Catalog. To view the state of the Product in the Catalog, open
the API Manager UI, select the Dashboard section in the navigation pane, and click on the required
Catalog. The Product is shown with a state of Staged.

- Open the {{site.data.keyword.Bluemix_notm}} **Dashboard**. You will see the application tile in the Applications section.

Open the API Manager to publish your product to a community where application developers can access it through the Developer Portal as explained in the next section, [Publishing a Product](#publish_proj_managing_products}).


## Publishing a Product
{: #publish_proj_managing_products}

APIs are made visible and accessible to application developers when a plan is published.
Publishing a Product makes it visible in the {{site.data.keyword.Bluemix_short}}
**Catalog** and built-in Developer Portal for application developers to
use.

### Prerequisites
{: #prereq_publish_proj_managing_products}

You must stage a Product before it can be published. For more information about staging Products, see [Staging a Product](#stage_product_managing_products).

To publish a Product, complete the following steps:

1. In the navigation pane of the API Manager, expand the **Catalogs** section
and select the Catalog that you want to work with. The Products tab of the Catalog opens, and all of
the Products available in that Catalog are displayed. You can select which states are shown by using
the filter check boxes on the right of the screen.

2. Alongside the Product version that you want to work with, click the
**Manage** icon  and then click **Publish**. The Edit
visibility and subscribers dialog box is displayed.

3. Specify the following options:
    - `Visible to`: You can choose **Public users**, **Authenticated users**,
    or **Custom**. If you select `Custom`, you can use the **Type to add...** field to
search for organizations or communities that you want your Product to be visible to.
    - `Subscribable by`: You can choose **Authenticated users**, or **Custom**. If you select `Custom`, you can use the **Type to add...** field to
search for organizations or communities that you want your Product to be visible to.

4. Click **Publish**.
    If approval is required to publish Products in this Catalog, an approval request is sent, and the
    Product moves to the Pending state; the Product is published when the request is approved. If
    approval is not required, the Product version is published immediately, and moves to the Published
    state.

Your Product is in the Published state. Your Product is published to your Catalog and
available to your specified organizations or communities. Application developers within the groups
you selected can see and use the APIs within the Product. Any application developer requests
to use your Product are displayed on the Approvals tab in the containing Catalog, where you can
decline or accept the request.


## Publishing a Product to Bluemix
{: #pub_to_bm_managing_products}

To see your Products in the **Explore APIs** section of the {{site.data.keyword.apiconnect_short}} Dashboard, complete the following steps.

### Prerequisites
{: #prereq_pub_bm_managing_products}

Before you begin, if you want to publish a REST API implemented with LoopBack, ensure that
you have published your app run time, and staged your product with the invoke proxy pointing to the
new app. For more information about how to do this, see [Staging and publishing a LoopBack Application](/docs/services/apiconnect/managing_apis.html#stage_publish_lb_app_managing_apis).

1. In the API Manager UI, click **Add** > **Catalog**. The **Add Catalog** window is displayed.

2. Complete the following fields and then click **Add**:
    - Display Name
    - Name
	
3. Select the Catalog that you created.

4. Click the **Settings** icon.

5. Click **Portal** and select one of the following options:
    - **IBM Developer Portal**. If you select this option, the Portal URL is
displayed.
    - **Other**. If you select this option, enter the URL for the Portal that
you want to use.

6. In the User Registry and Invitation section, click the **User Registry**
arrow and select **SAML**.

7. In the navigation pane, click the **Developers** icon.

8. Click **Add IBM Cloud Organization**.

9. Add your {{site.data.keyword.Bluemix_short}} user email
address and click **Add**.

10. An invitation is sent to your email address.

11. Click the link in the email to accept the invitation.
The {{site.data.keyword.Bluemix_notm}} UI
opens.

12. Select your {{site.data.keyword.Bluemix_notm}} org and click
**Confirm**.

13. In the API Manager UI, click the **Products** icon.

14. Alongside the Product version that you want to work with, click the
**Manage** icon and then click **Publish**. The Edit
visibility and subscribers dialog box is displayed.

15. Specify the following options:
    - **Visible to:** Choose **Custom** and use the **Type to add...** field to select
your developer org and any others that you want to add.
    - **Subscribable by:** Choose **Custom** and use the **Type to add...** field to select
your developer org and any others that you want to add.

16. Click **Publish**.

If approval is required to publish Products in this Catalog, an approval request is sent, and the
Product moves to the Pending state; the Product is published when the request is approved. If
approval is not required, the Product version is published immediately, and moves to the Published
state.

Your product is displayed in the **Explore APIs** tab of the {{site.data.keyword.apiconnect_short}}
**Dashboard**. If you click the Product  link, it will take you to the Product in
the Developer Portal.
