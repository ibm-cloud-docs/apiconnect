---

copyright:
  years: 2017
lastupdated: "2017-12-15"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal

subcollection: apiconnect

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 管理产品
{: #managing_products}

有关可用于管理产品的方式的详细信息，请参阅 IBM&reg; Knowledge Center 文档[管理产品 ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.apionprem.doc/task_product_management.html){: #new_window}。

## 产品生命周期
{: #prod_lifecycle_managing_products}

管理产品版本时，可使版本在一系列生命周期状态之间转变，从初始将草稿产品版本编译打包到环境中，一直到发布以使产品版本可供应用程序开发者使用，再到最终引退和归档。下面的表和图描述了产品版本的各种产品生命周期状态。

<table summary="" id="apic_004__table_lym_rxj_gv" class="defaultstyle"><caption class="style-scope doc-content">表 1. API 管理产品生命周期状态</caption>
<thead class="style-scope doc-content">
<tr class="style-scope doc-content doc-tr-even">
<th style="width: 11.25%" id="d3569e1968" class="thleft thbot style-scope doc-content">状态</th>
<th style="width: 88.75%" id="d3569e1970" class="thleft thbot style-scope doc-content">描述</th>
</tr>
</thead>
<tbody class="style-scope doc-content">
<tr class="style-scope doc-content doc-tr-odd">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">草稿</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">产品未部署，并且未与 API Connect 目录相关联。</td>
</tr>
<tr class="style-scope doc-content doc-tr-even">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">已编译打包</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">产品版本的不可变副本已部署到目标环境。“已编译打包”是从草稿产品进行编译打包后的初始状态。产品处于“已编译打包”状态时，任何开发者都还无法查看或预订该产品。</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">已发布</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">目标开发者或社区可查看和预订该产品版本。</td>
</tr>
<tr class="style-scope doc-content doc-tr-even">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">不推荐</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">只有当前已预订其应用程序的开发者才能够看到该产品版本。无法对该产品进行新的预订。</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">已引退</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">无法查看或预订该产品版本，并且所有关联的 API 都已停止。缺省情况下，已引退的产品版本会显示在 API Manager UI 的“产品”页面中。</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">已归档</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">无法查看或预订该产品版本，并且所有关联的 API 都已停止。缺省情况下，该产品版本不会显示在 API Manager UI 的“产品”页面中。</td>
</tr>
</tbody>
</table>

### 产品生命周期流程
{: #prod_lifecycle_flows_managing_products}

下图显示了产品版本的可能生命周期状态，以及将产品版本从一个生命周期状态转变为另一个状态的产品管理操作；例如，“引退”操作将产品版本从“已发布”转变为“已引退”状态。

<img alt="产品版本的生命周期状态图" src="images/apic_plan_lifecycle.png">


## 创建产品
{: #create_product_managing_products}

通过创建产品，可将一组 API 和套餐收集到一个可供开发者使用的产品服务中。套餐包含速率限制设置，这些设置可应用于整个套餐，也可针对某个 API 中的每个操作进行指定。通过产品和套餐，可以更好地控制开发者有权访问哪些 API。创建产品后，必须对产品编译打包。对产品编译打包将使该产品转变为活动状态，使您可以调用并测试其中包含的 API。对产品编译打包后，任何开发者都还无法查看该产品。

**提示**：除了使用本任务中描述的方法之外，您还可以在创建 API 时创建产品。如果使用开发者工具箱命令行界面来创建 API，那么会自动创建产品。随后可以通过在 API Designer 的“**产品**”页面中打开新产品来更改任何产品设置。

要使用 API Designer 创建产品，请完成以下步骤：
1. 要打开 API Designer 用户界面，请打开命令行并输入以下命令：
```
apic edit
```
API Designer 将在缺省浏览器中打开。



2. 在 API Designer 的导航窗格中，单击**产品**。这将打开“产品”选项卡。

3. 单击**添加**，然后单击**新产品**。这将打开“添加新产品”窗口。

4. 填写以下字段：
    - 标题
    - 名称
    - 版本

5. 单击**添加**。这将打开新产品的“设计”选项卡。

6. **可选**：在**信息**部分中，输入产品的描述、联系人、许可证和服务条款信息。

7. 在**可视性**部分中，指定要使其可查看该产品的用户。可以选择**公共**、**已认证的用户**或**定制**。如果选择**定制**，请使用**输入以添加**字段来搜索要使其可查看该产品内套餐的开发者组织或社区。

    **注：**要搜索开发者组织或社区，产品必须处于“已编译打包”、“已发布”或“已弃用”状态。如果在其中编译打包、发布或弃用产品的目录不是沙箱目录，那么当产品处于其中某一状态时，无法对该产品进行其他更改。有关更多信息，请参阅[产品生命周期](#prod_lifecycle_managing_products)。

8. 指定可以预订该产品的用户。可以选择**已认证的用户**或**定制**。如果选择**定制**，请使用**输入以添加**字段来搜索要使其能够预订该产品内套餐的开发者组织或社区。

9. 在 API 部分中，指定要包含在产品中的 API。
    1. 单击**添加 API** 图标。
    2. 选择要包含的 API，然后单击**应用**。这将列出所选 API。

10. 要使 API 可用于应用程序开发者，必须将其包含在套餐中。要向产品添加一个或多个套餐，请单击**添加套餐**图标。
    1. 展开已创建的新套餐。如果已将 API 添加到产品，那么将自动包含这些 API。
    2. 在**标题**和**名称**字段中重命名套餐，并且可以选择添加描述。**注：**将为您自动创建缺省套餐；如果不想创建自己的套餐，那么可以将自己的 API 包含在此套餐中。但是，如果决定不使用缺省套餐，那么必须将其删除，因为如果产品包含任何不包含 API 的套餐，该产品将无法编译打包。

11. 验证您需要的 API 是否包含在该套餐中。
    1. 展开要将 API 添加到的套餐。
    2. 在“包含的 API”下，确保选中所需 API 对应的复选框。如果已选择了 API，并且您不希望将其包含在您所编辑的套餐中，请清除对应的复选框。

12. **可选**：添加套餐的帐单信息。要添加帐单信息，您必须使用信用卡处理服务来建立帐户，以便客户可以使用信用卡支付。每月收费套餐在每个月的同一天收费。

13. **可选**：如果要定制将 API 中的哪些操作包含在套餐中，请将光标悬停在包含相应操作的 API 之上。单击**显示操作**图标，然后选中或清除要包含或排除的操作对应的复选框。

14. **可选**：要向套餐添加速率限制，请清除**无限制**复选框，然后指定要应用的速率限制。如果选中了**强制实施硬性限制**复选框，那么在达到速率限制后，套餐将阻止应用程序调用 API；如果未选中此复选框，将显示警告。

    **注：**在套餐级别应用速率限制会创建应用于该套餐内每个操作的缺省速率限制。如果需要针对特定操作设置特定速率限制，那么必须在这些操作本身内进行设置，并且此设置将覆盖套餐级别的设置。

15. **可选**：指定您的套餐是否需要预订核准。如果希望开发者进行的预订需要通过 API Manager 用户界面进行核准，请选中**需要预订核准**；否则，请确保清除此复选框。

16. **可选**：向操作添加速率限制。
    1. 将光标悬停在包含该操作的 API 之上，并单击**显示操作**图标。
    2. 将光标悬停在要应用速率限制的操作之上。单击**编辑速率限制**图标。
    3. 确保清除**无限制**复选框，然后指定要应用的速率限制。如果选中了**强制实施硬性限制**复选框，那么在达到速率限制后，套餐将阻止应用程序调用 API；如果未选中此复选框，将显示警告。

- 单击**保存**图标以保存更改。

您已创建产品，并且在现在可提供给开发者使用的一个产品服务中指定了一组 API 和套餐。接下来，将您的产品编辑打包到目录中，如下一节所述：[编译打包产品](#stage_product_managing_products})。


## 编译打包产品
{: #stage_product_managing_products}

发布产品之前，对产品编译打包以在目录中创建该产品的特定版本。产品处于“已编译打包”状态时，任何开发者都还无法查看或预订该产品。

**注：**API Manager UI 也包含对产品编译打包的功能，但是执行这些任务的首选方法是使用 API Designer UI，如以下过程中所述。

1. 在 API Designer 的导航窗格中，单击**产品**。这将打开“产品”选项卡。

2. 单击要使用的**产品**。如果您有产品的多个版本，请确保单击要使用的版本。

3. 单击**发布**图标。

4. 如果要将产品编译打包到的目录显示在列表中，请执行以下操作：
    1. 选择需要的目录。 
    2. 选择**仅编译打包（产品不会发布）**，再选择**发布**。您的产品已编译打包。

5. 如果要将产品编译打包到的目录未显示在列表中，请执行以下操作：
    1. 单击**添加和管理目标**。
    2. 单击**添加 {{site.data.keyword.Bluemix_notm}} 目标**。
    3. 选择要发布到的 {{site.data.keyword.Bluemix_short}} **区域**。
    4. 选择要发布到的 {{site.data.keyword.Bluemix_notm}}
**组织**。
    5. 这将显示目录的列表。选择要发布到的目录。
    6. 单击**下一步**。
    7. 如果您有要发布的 LoopBack 应用程序，请选择要发布到的应用程序。否则，请选择**无**。
    8. 单击**保存**。
    9. 再次单击**发布**，然后选择刚才添加的目标。
    10. 选择所需的目录。
    11. 选择**仅编译打包**。
    12. 单击**发布**。

您的产品已编译打包到目录中。要在目录中查看产品的状态，请打开 API Manager UI，在导航窗格中选择“仪表板”部分，然后单击所需目录。产品将显示为“已编译打包”状态。

- 打开 {{site.data.keyword.Bluemix_notm}} **仪表板**。您将在“应用程序”部分中看到应用程序磁贴。

打开 API Manager，将您的产品发布到应用程序开发者可通过开发者门户网站进行访问的社区，如下一节所述：[发布产品](#publish_proj_managing_products})。


## 发布产品
{: #publish_proj_managing_products}

发布套餐后，应用程序开发者即可查看和访问 API。发布产品可使该产品在 {{site.data.keyword.Bluemix_short}} **目录**和内置开发者门户网站中显示，供应用程序开发者使用。

### 先决条件
{: #prereq_publish_proj_managing_products}

必须首先编译打包产品，然后才能将其发布。有关对产品编译打包的更多信息，请参阅[对产品编译打包](#stage_product_managing_products)。

要发布产品，请完成以下步骤：

1. 在 API Manager 的导航窗格中，展开**目录**部分，然后选择要使用的目录。这将打开目录的“产品”选项卡，并显示该目录中可用的所有产品。您可以通过使用屏幕右侧的过滤器复选框来选择要显示的状态。

2. 单击要使用的产品版本旁边的**管理**图标，然后单击**发布**。这将显示“编辑可视性和订户”对话框。

3. 指定以下选项：
    - `可供以下对象查看`：可以选择**公共用户**、**已认证的用户**或**定制**。如果选择`定制`，那么可以使用**输入以添加...** 字段来搜索要允许查看产品的组织或社区。
    - `可供以下对象预订`：可以选择**已认证的用户**或**定制**。如果选择`定制`，那么可以使用**输入以添加...** 字段来搜索要允许查看产品的组织或社区。

4. 单击**发布**。如果需要经过核准才能在此目录中发布产品，那么在发送核准请求后，该产品将转变为“暂挂”状态；当请求通过核准后，便会发布该产品。如果不需要核准，那么该产品版本将立即发布并转变为“已发布”状态。

您的产品已处于“已发布”状态。您的产品已发布到目录中，可供您指定的组织或社区使用。您所选组中的应用程序开发者可以看到并使用该产品中的 API。在包含目录中的“核准”选项卡上，会显示使用您产品的所有应用程序开发者请求，您可以在其中拒绝或接受请求。


## 将产品发布到 Bluemix
{: #pub_to_bm_managing_products}

要在 {{site.data.keyword.apiconnect_short}}“仪表板”的“**浏览 API**”部分中查看产品，请完成以下步骤。

### 先决条件
{: #prereq_pub_bm_managing_products}

开始之前，如果要发布使用 LoopBack 实现的 REST API，请确保已发布应用程序运行时，并且已使用指向新应用程序的调用代理对产品编译打包。有关如何执行此操作的更多信息，请参阅[对 LoopBack 应用程序执行编译打包和发布操作](/docs/services/apiconnect?topic=apiconnect-managing_apis#stage_publish_lb_app_managing_apis)。

1. 在 API Manager UI 中，单击**添加** > **目录**。这将显示“**添加目录**”窗口。

2. 填写以下字段，然后单击**添加**：
    - 显示名称
    - 名称
	
3. 选择已创建的目录。

4. 单击**设置**图标。

5. 单击**门户网站**，然后选择以下某个选项：
    - **IBM 开发者门户网站**。如果选择此选项，那么将显示门户网站 URL。
    - **其他**。如果选择此选项，请输入要使用的门户网站的 URL。

6. 在“用户注册表和邀请”部分中，单击**用户注册表**箭头，并选择 **SAML**。

7. 在导航窗格中，单击**开发者**图标。

8. 单击**添加 IBM Cloud 组织**。

9. 添加 {{site.data.keyword.Bluemix_short}} 用户电子邮件地址，并单击**添加**。

10. 这将向您的电子邮件地址发送邀请。

11. 单击电子邮件中的链接以接受邀请。这将打开 {{site.data.keyword.Bluemix_notm}} UI。

12. 选择您的 {{site.data.keyword.Bluemix_notm}} 组织，然后单击**确认**。

13. 在 API Manager UI 中，单击**产品**图标。

14. 单击要使用的产品版本旁边的**管理**图标，然后单击**发布**。这将显示“编辑可视性和订户”对话框。

15. 指定以下选项：
    - **可供以下对象查看**：选择**定制**，然后使用**输入以添加...** 字段来选择您的开发者组织以及要添加的其他任何对象。
    - **可供以下对象预订**：选择**定制**，然后使用**输入以添加...** 字段来选择您的开发者组织以及要添加的其他任何对象。

16. 单击**发布**。

如果需要经过核准才能在此目录中发布产品，那么在发送核准请求后，该产品将转变为“暂挂”状态；当请求通过核准后，便会发布该产品。如果不需要核准，那么该产品版本将立即发布并转变为“已发布”状态。

现在，您的产品显示在 {{site.data.keyword.apiconnect_short}} **仪表板**的**浏览 API** 选项卡中。如果单击产品链接，将转至开发者门户网站中的该产品。
