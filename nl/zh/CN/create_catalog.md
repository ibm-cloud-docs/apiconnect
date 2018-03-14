---
copyright:
  years: 2017
lastupdated: "2017-10-24"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 配置目录

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
  2. 如果您想要启用目录的自动预订，请选择**自动预订**。如果启用自动预订，测试 API 将变得更加轻松，因为通过预先提供的客户机标识和客户机私钥，使用了测试应用程序。测试应用程序会自动预订目录中的所有方案，因此在测试时，您无需指定方案或应用程序。
    **注：**自动预订仅可供开发目录使用。
  3. 如果目录是缺省的编译打包目录，请选择**缺省值**。然后，对发布到目录的 API 的调用可以使用不包括目录名称的简短 URL。
    **注：**您仅可以针对一个目录选择**缺省值**。
  4. **可选**：单击**端点**，然后填充以下字段：
        - **定制网关 URL**：在“定制网关 URL”文本字段中，输入 URL。如果您想要针对部署至 {{site.data.keyword.apiconnect_short}} 的 API 获取 URL 的定制标记，而不是使用 API Manager 生成的缺省 URL，那么您可以使用“定制网管 URL”。缺省情况下，{{site.data.keyword.apiconnect_short}} 网关 URL 的格式如下：
        ```
        https://gateway_cluster_hostname/organization_name/Catalog_name
        ```
但是，您可以通过指定更适合企业的 URL 来覆盖缺省值；例如，`https://api.mycompany.com`。之后，开发者门户网站中显示的任何 API 端点都将反映该指定的 URL。**注：**
		    - 您必须配置 DNS 条目，以将定制主机名和域映射到缺省网关 URL。
		    - 对于要反映定制网关 URL 的 API 的端点，您必须对该 API 进行配置，以由 API Connect 网管强制执行。有关更多信息，请参阅[为 API 指定替代主机 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){:new_window}。
		    - 确保未向多个目录应用相同的定制网关 URL，因为并未在该场景中定义此类行为。
**提示：**调用 API 时，还可以将 API 请求上的 HTTP 主机头设置为在“定制网关 URL”字段中指定的值。

	    - **定制 API URL**：在“定制 API URL”文本字段中，输入 URL。您可以使用“定制 API URL”来为部署到第三方网关的 API 指定 URL。

	    定制 API URL 代表 API 外部已知的端点；也就是说，该端点是对开发者门户网站发布的，并且应用程序开发者将其用于调用或传递 API。

	    如果您正在该目录中使用第三方网关或外部负载均衡器，请在该字段中提供 URL。之后，开发者门户网站中显示的任何 API 端点都将反映该指定的 URL。这些端点存在于第三方网关或负载均衡器上，呈现一个虚拟地址并显示给 API 使用者，该虚拟地址会映射到网关上的 API 代理或 API 组合端点。从定制 API URL 衍生的端点通常发布在生产开发者门户网站中，以推广该 API 的地址。

	    **注：**如果您为目录指定定制 API URL，那么它会优先于您在配置 API 时指定的任何主机名。有关更多信息，请参阅[为 API 指定替代主机 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){:new_window}。

	    - **开发者门户网站 API 调用的主机名**：在“端口 API 端点”窗口区域中，输入开发者门户网站 API 调用的主机名。输入的主机名可以是管理服务的主机名。
要访问开发者门户网站上下文中的开发者门户网站 API，您必须配置开发者门户网站 API 调用的基本主机名。
此操作允许 API Manager 将主机名映射到开发者门户网站 API 调用的提供者组织和目录，而不需要您对其进行查找并将它们包含在调用中。

7. 单击**保存**图标。

## 分区目录
{: #apic_spaces}

要使用 {{site.data.keyword.apiconnect_short}} 中的联合功能，您必须在需要联合功能的任何目录中，启用空间。

要在目录中启用空间，请完成以下步骤：
1. 在 API Manager UI 的仪表板中，选择要使用的目录。

2. 单击**设置** > **概述**，然后单击**空间**滑块控件。

3. 在**启用空间**窗口中，单击**启用**，然后单击**保存**图标 <img src="images/icon_save.png" alt="保存图标"/>。此时，**管理空间**链接将显示在**空间**滑块控件的下方，而**空间**链接将添加到导航窗格。
您可以通过单击以下任何链接来管理您的空间。

此时将会针对您的目录启用空间，且会创建名为“新空间”的缺省空间。


有关使用联合的更多信息，请参阅 Knowledge Center 主题[使用 IBM API Connect 中的联合 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.apionprem.doc/capic_syndication_using.html){:new_window}。
