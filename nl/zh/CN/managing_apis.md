---

copyright:
  years: 2018
lastupdated: "2019-01-17"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal

subcollection: apiconnect

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 管理 API
{: #managing_apis}

不管 API 是位于 {{site.data.keyword.Bluemix_notm}} 中，还是在 {{site.data.keyword.Bluemix_notm}} 外部进行维护，都可以使用 API Connect 在 {{site.data.keyword.Bluemix}} 中管理这些 API。通过管理 API，可以控制使用情况，提高采用率以及跟踪统计信息。

如果您是客户，那么开发者创建 API 并将产品推送到 {{site.data.keyword.Bluemix_notm}} 后，您可以在 API Manager UI 内管理其使用方式。以下主题描述了如何在 {{site.data.keyword.apiconnect_short}} 中创建和管理产品。

## 通过安全网关公开内部部署 API
{: #expose_apis_sec_gate_managing_apis}

您可以创建安全网关，以安全方式将内部部署 API 公开到 {{site.data.keyword.apiconnect_full}}。

创建安全网关并提供其客户机或云的地址 `<host>:<port>` 时，需要将 {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.SecureGateway}} 服务的功能与 {{site.data.keyword.apiconnect_short}} 相集成。这意味着您可通过安全通道，以安全方式从 {{site.data.keyword.apiconnect_short}} 访问内部部署 API。您可在公共环境上有效地创建 {{site.data.keyword.apiconnect_short}} 的隧道，而不公开内部部署数据。您只需在 IBM Cloud 上创建和配置安全网关服务，然后在 API 中提供其地址即可。

有关 {{site.data.keyword.SecureGateway}} 服务以及如何设置该服务的更多信息，请参阅[关于 {{site.data.keyword.SecureGateway}} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://cloud.ibm.com/docs/services/SecureGateway?topic=index#getting-started-with-sg){: #new_window}。

### 使用安全网关与 API
{: #using_sec_gate_apis_managing_apis notoc}

当您已经配置网关之后，可以将其与 API 一起使用。
{:shortdesc}

要将安全网关与 API 一起使用，请完成以下步骤。
1. 创建 API 和产品，如以下步骤中所述。
  - 单击**导航至** <img src="images/navigate_to_icon.png" alt="“导航至”图标" /> > **草稿** > **API** > **添加**。
  - 选择要创建的 API 的类型。
  - 选择或单击**添加产品**。**重要信息**：目前请勿发布产品。
  - 单击**创建 API**。这将在`设计`视图中显示 API。
  
2. 单击**组合**。

3. 单击**调用**策略以打开“**调用**”选用板。**限制**：逻辑开关（例如，`Switch`、`Operation Switch` 和 `If`）不能与使用安全网关的 API 一起使用。

4. **不要**选中**通过安全网关访问 URL** 复选框。
**重要信息**：此复选框所适用的功能现已弃用，在生产环境中不受支持，随时都可能会被除去。您将转而直接提供安全网关 URL 的地址，而无需选中此复选框。

5. 在 URL 字段中，将 `target-url` 更新为云主机名和端口号，例如：
```
target-url: cap-sg-prd-5.securegateway.appdomain.cloud:18579
```

6. 单击**保存** <img src="images/icon_save.png" alt="“保存”图标" />。

7. 单击**所有 API** > **产品**，然后选择先前创建的产品。

8. 单击**发布**，以将产品编译打包到所选目录中。

9. 选择要使用的目录。

10. 选择已编译打包的产品。

11. 单击**发布**。

您已安全地将内部部署 API 公开到 {{site.data.keyword.apiconnect_short}}。接下来，测试 {{site.data.keyword.SecureGateway}} API。

### 测试安全网关 API
{: test_sec_gate_managing_apis notoc}

在 API 中提供 {{site.data.keyword.SecureGateway}} 的地址之后，您可以测试 API，以确保网关运作正常，并可生成正确的响应。

要使用安全网关来测试 API，请完成以下步骤：

1. 单击 <img alt="“导航至”图标" src="images/navigate_to_icon.png" /> > **草稿** > **API** **<您的 API>** > **组合**。

2. 单击**测试**图标 <img src="images/test_icon.png" alt="“测试”图标"/>。

3. 从提供的列表选择要在其中进行测试的目录。

4. 确保 URL 会提供正确的安全网关的地址 `<cloud_host>:<port>`，并且已正确配置安全网关服务目标，如 [{{site.data.keyword.SecureGateway}} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://cloud.ibm.com/docs/services/SecureGateway?topic=index#getting-started-with-sg){: #new_window} 文档中所述。

5. 从提供的列表选择现有产品，然后单击**重新发布产品**。**重要信息**：如果此产品已经发布到目录，那么将使用新网关重新发布该产品。

6. **可选**：提供名称以创建新产品，然后单击**创建并发布**。

7. 单击**下一步**。

8. 从提供的列表选择要调用的操作。

9. 单击**调用**。

此时将显示测试结果。

## 编译打包和发布 LoopBack 应用程序
{: #stage_publish_lb_app_managing_apis}

1. 在 API Designer 的导航窗格中，单击**产品**。这将打开“产品”选项卡。

2. 选择产品的版本，确保单击要使用的版本。

3. 要将运行时发布到 {{site.data.keyword.Bluemix_notm}}，请单击**发布**。

4. 单击**添加和管理目标** > **添加 IBM Cloud 目标**。

5. 选择要发布到的 {{site.data.keyword.Bluemix_notm}} **区域**并登录。

6. 选择要发布到的 {{site.data.keyword.Bluemix_notm}} **组织**。

7.  这将显示目录的列表。选择要发布到的目录。

8.  单击**下一步**。

9. 选择要发布的 LoopBack 应用程序。如果这是第一次将运行时部署到 {{site.data.keyword.Bluemix_notm}}，请添加名称，然后单击**添加**图标。

10.  单击**保存**。

11.  再次单击**发布**，然后选择**发布应用程序**。

12.  单击**发布**。

13. 在命令行中，为 API 指定了“API 目标 URL”和“API 调用 tls-profile”。请记下这些信息。“API 调用 tls-profile”始终为 `client:Loopback-client`，但可以检索“API 目标 URL”，如以下步骤中所述。
    ```
    Deploying to Bluemix
    ...preparing project
    ...building package for deploy
    ...uploading package
    Runtime published successfully.
    Management URL: https://<domain name>/apps/33e7b062-092b-4227-af97-047499dab2e7
    API target urls: apiconnect-33e7b062-092b-4227-af97-047499dab2e7.<Bluemix org>-<Bluemix space>.apic.<domain name>
    API invoke tls-profile: client:Loopback-client
    Updated newapi_1.0.0.yaml with tls-profile and target-url.
    Updated notes.yaml with tls-profile and target-url.
    ```

14. 在 API Designer UI 中，完成以下步骤：
    1. 单击 **API**。
    2. 选择您的 API。
    3. 单击**组合**。
    4. 在组合件编辑器中，单击**过滤策略**图标。
    5. 选择 **DataPower Gateway 策略**。
    6. 单击**保存**以保存 API。

15.  接下来，需要发布到 API Manager。单击**发布**。
    1. 选择**发布应用程序**，然后选择以下某个选项：
	    - **替换现有应用程序**：如果您有已发布的应用程序，那么选择此选项可覆盖现有应用程序。
        - **作为全新应用程序（使用现有路径）**：选择此选项可创建新应用程序，并在**新建应用程序**字段中为其提供名称。服务不会中断。

    2. 选择以下选项：
	    - 编译打包或发布产品
        - 选择特定产品
        - _your product_
 
    3. 单击**发布**。

要测试发布是否已生效，请完成以下步骤：

1. 确保 {{site.data.keyword.Bluemix_notm}} 应用程序正在运行。

2. 打开浏览器窗口，并导航至 API URL。应用程序通过客户机验证进行保护。如果未提供正确的客户机证书，那么将输出错误（这是预期行为）。

3. 浏览至公开的 {{site.data.keyword.apiconnect_short}} URL。例如：
```
https://<domain>/<Bluemix org>-<Bluemix space>/<Catalog identifier>/api/notes
```
这将显示 200 响应。



## 配置目录
{: #config_cat_managing_apis}

您可以创建和配置 API Manager 目录。使用目录，可在将产品和 API 提供给开发者组织之前，将它们分隔开来以用于测试。
配置目录时，还可以配置定制标记，以便您无需使用 API Manager 提供的缺省 API URL。

要创建目录，请完成以下步骤：

1. 单击**导航至** <img alt="“导航至”图标" src="images/navigate_to_icon.png"> > **仪表板**。

2. 单击 **+ 添加** > **目录**。这将显示“**添加目录**”窗口。

3.  在**显示名称**字段中输入新目录的名称。

4. 在**名称**字段中，输入您要形成 URL 目录段的文本。
**注：****名称**字段仅可以包含小写字母数字字符（a-z 和 0-9）或连字符 (-)。连字符不能用作名称的第一个或最后一个字符。

5. 单击**添加**。这将创建目录，且会显示在仪表板上。

6. 要配置目录，请单击目录的名称，然后单击**设置** > **信息**，并继续以下步骤：
  1. 如果新目录是开发目录，请选择**开发方式**。如果选择开发方式，那么会强制执行编译打包和发布操作，这表示如果您重新发布之前已发布的产品，那么会直接覆盖而不会发出警告。
如果发现冲突，系统会自动解决这些冲突。这样会自动执行取消发布操作。**注：**对于开发目录，不会显示核准框。您不能对生命周期启用批准流程。
  2. 如果您想要启用目录的自动预订，请选择**自动预订**。如果启用自动预订，API 的测试将变得更加轻松，因为通过预先提供的客户机标识和客户机私钥，使用了测试应用程序，该应用程序会自动预订目录中的所有套餐，因此在测试时您无需指定套餐或应用程序。**注：**自动预订仅可用于开发目录。
  3. 如果目录是缺省的编译打包目录，请选择**缺省值**。然后，对发布到目录的 API 的调用可以使用不包含目录名称的简短 URL。
    **注：**只能对一个目录选择**缺省值**。
  4. **可选**：单击**端点**，然后填充以下字段：
        - **定制网关 URL**：在“定制网关 URL”文本字段中，输入 URL。如果您想要针对部署至 {{site.data.keyword.apiconnect_short}} 的 API 获取 URL 的定制标记，而不是使用 API Manager 生成的缺省 URL，那么您可以使用“定制网管 URL”。缺省情况下，{{site.data.keyword.apiconnect_short}} 网关 URL 的格式如下：
        ```
        https://gateway_cluster_hostname/organization_name/Catalog_name
        ```
        但是，您可以通过指定更适合企业的 URL 来覆盖缺省值；例如，`https://api.mycompany.com`。之后，开发者门户网站中显示的任何 API 端点都将反映该指定的 URL。**注：**
		    - 您必须配置 DNS 条目，以将定制主机名和域映射到缺省网关 URL。
		    - 对于要反映定制网关 URL 的 API 的端点，您必须对该 API 进行配置，以由 API Connect 网管强制执行。有关更多信息，请参阅[为 API 指定替代主机 ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){: #new_window}。
		    - 确保未向多个目录应用相同的定制网关 URL，因为并未在该场景中定义此类行为。
        **提示：**调用 API 时，还可以将 API 请求上的 HTTP 主机头设置为在“定制网关 URL”字段中指定的值。

	    - **定制 API URL**：在“定制 API URL”文本字段中，输入 URL。您可以使用“定制 API URL”来为部署到第三方网关的 API 指定 URL。

	    定制 API URL 代表 API 外部已知的端点；也就是说，该端点是对开发者门户网站发布的，并且应用程序开发者将其用于调用或传递 API。

	    如果您正在该目录中使用第三方网关或外部负载均衡器，请在该字段中提供 URL。之后，开发者门户网站中显示的任何 API 端点都将反映该指定的 URL。这些端点存在于第三方网关或负载均衡器上，呈现一个虚拟地址并显示给 API 使用者，该虚拟地址会映射到网关上的 API 代理或 API 组合端点。从定制 API URL 衍生的端点通常发布在生产开发者门户网站中，以推广该 API 的地址。

	    **注：**如果您为目录指定定制 API URL，那么它会优先于您在配置 API 时指定的任何主机名。有关更多信息，请参阅[为 API 指定替代主机 ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){: #new_window}。

	    - **开发者门户网站 API 调用的主机名**：在“端口 API 端点”窗口区域中，输入开发者门户网站 API 调用的主机名。输入的主机名可以是管理服务的主机名。
     要访问开发者门户网站上下文中的开发者门户网站 API，您必须配置开发者门户网站 API 调用的基本主机名。
     此操作允许 API Manager 将主机名映射到开发者门户网站 API 调用的提供者组织和目录，而不需要您对其进行查找并将它们包含在调用中。

7. 单击**保存**图标。

## 对目录分区
{: #part_cat_managing_apis}

要使用 {{site.data.keyword.apiconnect_short}} 中的联合功能，您必须在需要联合功能的任何目录中，启用空间。

要在目录中启用空间，请完成以下步骤：
1. 在 API Manager UI 的仪表板中，选择要使用的目录。

2. 单击**设置** > **概述**，然后单击**空间**滑块控件。

3. 在**启用空间**窗口中，单击**启用**，然后单击**保存**图标 <img src="images/icon_save.png" alt="保存图标"/>。此时，**管理空间**链接将显示在**空间**滑块控件的下方，而**空间**链接将添加到导航窗格。
您可以通过单击以下任何链接来管理您的空间。

此时将会针对您的目录启用空间，且会创建名为“新空间”的缺省空间。


有关使用联合的更多信息，请参阅 Knowledge Center 主题[使用 IBM API Connect 中的联合 ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.apionprem.doc/capic_syndication_using.html){: #new_window}。

## 配置开发者门户网站
{: #config_dev_portal_managing_apis}

开发者门户网站是用于发布套餐以供应用程序开发者访问和使用的位置。

您可以构建定制开发者门户网站以供应用程序开发者使用。您对其外观、内容、用户设置和配置设置具有完全管理控制权。

除了允许应用程序开发者查找并使用 API 外，开发者门户网站还提供了更多功能，例如论坛、博客、评论、评级以及用于 API 的 Swagger UI。

1. 在 API Manager UI 中，选择要使用的目录。

2. 选择**设置**选项卡。

3. 单击**门户网站**。

4. 在“**门户网站配置**”部分中，选择 **IBM 开发者门户网站**。这将显示门户网站 URL。

5. 单击**保存**。这将向您发送一封电子邮件，其中包含供开发者门户网站 Web 管理用户使用的一次性登录链接。

6. 单击在电子邮件中发送的链接，并遵循指示信息来重置密码。

您的开发者门户网站已配置。您可以在收到的电子邮件的主题行中找到开发者门户网站 URL。还可以在 API Manager UI 中通过单击**门户网站** > **设置**来找到该 URL。

有关可以在开发者门户网站中完成的任务的更多信息，请参阅 IBM Knowledge Center 中有关
[开发者门户网站 ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.devportal.doc/capim_devportal_overview.html){: #new_window} 的主题。

## 配置角色的许可权
{: #config_permissions_roles_managing_apis}

要在 API Manager 中配置角色的许可权，请完成以下步骤。

1. 在 API Manager“**仪表板**”中，单击要使用的目录。

2. 单击**设置** > **许可权**。这将显示您可以为其分配角色的产品管理许可权：
  - **编译打包**：允许将产品编译打包到目录。
  - **查看**：允许查看和列出目录中的产品。
  - **管理**：允许管理产品生命周期（发布、弃用、引退和归档）。
  - **核准**：启用对产品生命周期状态更改的核准。**注：**针对所有开发目录，会禁用对产品生命周期状态更改的核准。

3. 要将角色添加到**编译打包**、**查看**或**管理**许可权，请单击相应的 **+** 图标。以下列表显示了可用的缺省角色：
  - 管理员
  - 产品经理
  - API 开发者 (API Developer)
  - 发布者
“所有者”角色具有全部许可权。

4. 通过选择所需的复选框，然后单击相应的 **+** 图标，分配具有批准生命周期状态更改许可权的角色，启用对产品生命周期状态更改的批准。
所选的生命周期状态更改是您希望实施批注的那些更改。例如，如果清除所有其他项而只选择“发布”，那么在任何人尝试发布某个产品时都需要进行批准，但任何其他生命周期状态更改都不需要进行批准。
5. 要分配具有管理用户定义策略许可权的角色，请单击“**策略管理**”部分的 **+** 图标。这将显示策略管理许可权，使您能够根据需要分配角色。
6. 单击**保存**图标。
