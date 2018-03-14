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

# 导入 API

您可以使用 Swagger 定义文件来添加 REST API。
{:shortdesc}

## 先决条件
{: #prereq_import_swagger}

开始之前，请确保您的文件符合 Swagger 规范 V2.0。该文件的格式可以是 JSON 或 YAML。

要通过装入 Swagger 文件来添加 REST API，请完成以下步骤：

1. 在 API Manager UI 导航窗格中，单击**草稿**，然后单击 **API**。这将打开 API 选项卡。

2. 单击 **+ 添加**，然后从**导入**部分中选择 **Swagger 2.0**。这将打开“**导入 Swagger API**”窗口。

3. **可选**：要从本地文件系统上传文件，请单击**选择文件**，然后在文件系统中选择要使用的文件。`.json`、`.yml` 和 `.yaml` 文件在包含有效 Swagger 定义的情况下受支持。

4. **可选**：要通过 URL 上传文件，请单击**或者通过 URL 导入**，然后在显示的 **URL** 字段中提供正确的 URL。如果需要认证才可访问 URL，请提供用户名和密码。`.json`、`.yml` 和 `.yaml` 文件在包含有效 Swagger 定义的情况下受支持。

5. 单击**导入**。这将创建新的 REST API 定义，包括路径和 HTTP 操作。

API 定义导入后，会显示在“**草稿**”页面中 **API** 选项卡的 API 定义列表中。接下来，可以编辑 API 定义，编辑方法与编辑其他任何 REST API 定义一样。

## 通过 IBM Integration Bus 导入 API
{: #tut_import_iib_apic}

在本教程中，可以将使用 IBM Integration Bus 创建的 REST API 导入到 {{site.data.keyword.apiconnect_full}}，从而可更轻松地管理和发布这些 API。
{: shortdesc}

开始之前，请确保您的 REST API 文件符合 Swagger 规范 V2.0。该文件的格式可以是 JSON 或 YAML。

您可以使用 IBM Integration Bus 创建 REST API，这些 API 是专用应用程序，可用于将集成作为 RESTful Web Service 公开且可由 HTTP 客户机调用。创建 API 后，可以将其导入 {{site.data.keyword.apiconnect_short}} 以管理和发布这些 API。

以下列表中包含了在 {{site.data.keyword.apiconnect_short}} 中管理 API 的一些优势：
* 您可以监视对 API 执行的调用数。
* 您可以控制对 API 执行的调用数。
* 您可以维护多个 API 版本。

有关更多优点，请参阅[管理 API](managing_apis.html)。

要在 IBM Integration Bus 中创建 REST API 并将其导入到 {{site.data.keyword.apiconnect_short}}，请完成以下步骤：
1. 使用 IBM Integration Bus 创建 REST API。限制：仅可使用安装的 IBM Integration Bus 版本随附的 IBM Integration Toolkit 来创建 REST API。
	1. 使用 IBM Integration Toolkit 创建 REST API。有关如何完成使用 IBM Integration Bus 创建 REST API 的任务的更多信息，请参阅 IBM Knowledge Center 中的[使用 REST API 开发集成解决方案 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSMKHH_10.0.0/com.ibm.etools.mft.doc/bi12016_.htm){: new_window}。
		
	2. 通过选择**文件** > **新建** > **REST API**，打开“创建 REST API”向导。
		
	3. 输入 REST API 的名称。在 IBM Integration Toolkit 中，将使用您指定的名称作为项目的名称。
		
	4. 选择下列某种方法创建 REST API 并完成以下过程：
		
	**使用 IBM Integration Toolkit 随附的 REST API 编辑器从头开始操作**
		1. 选择**创建 REST API 并自行定义资源和操作**。
		2. 单击**完成**。此时将为新 REST API 自动打开 REST API 编辑器，定义资源、模型和操作时必须使用此编辑器。
		
	**从现有 Swagger 2.0 文档操作**：
		1. 选择**导入 Swagger 文档中定义的资源和操作**并单击**下一步**。
		2. 选择描述 REST API 中所需资源和操作的 Swagger 文档的路径。您可以从文件系统或工作空间中的现有项目导入 Swagger 文档。此时将验证文件是否可在 REST API 中使用。如果验证所选 Swagger 文档时发现任何错误，那么会在向导开头显示这些验证错误。如果在所选 Swagger 文档中发现验证错误，那么无法继续。
		3. 选择**完成**以创建 API。
	5. 实现 REST API 的子流，即要包含的 REST 操作。
2. 将 REST API 项目添加到 IBM Integration Bus 的新增或现有代理程序归档 (BAR) 文件。
3. 将 BAR 文件部署到 IBM Integration Bus on Cloud。
	1. 如果尚未登录到 IBM Integration Bus on Cloud，请使用 IBM 标识登录。如果没有帐户，请注册一个帐户。
	2. 单击**添加集成** > **上传 BAR 文件**。
	3. 选择为 REST API 项目创建的 BAR 文件。提示：您可以通过在 IBM Integration Toolkit 中右键单击 BAR 文件并查看其属性来找到该文件的位置。
	4. 选择**保存**。
	5. 选择**刷新列表**以更新屏幕。
	6. 通过在 IBM Integration Bus on Cloud 的*集成*窗口中查看 API 的 API 集成流，验证是否已成功上传 BAR 文件。
4. 通过选择“启动”图标 ![此截屏显示启动图标。](images/a_play_button.jpg " ")，启动集成流。API 已启动，并显示 `Running` 状态。
5. 从集成列表选择集成以查看相关信息。“内容”菜单中的树显示 REST API 和与其关联的子流。还可查看其他部分中的信息。在“公共端点”部分中，可查看 IBM Integration Bus on Cloud 为集成流分配的公共 URL。选择**显示完整 URL** 可查看该操作的完整 URL。
6. 将操作的完整 URL 复制到剪贴板。在将该 API 配置为与 {{site.data.keyword.apiconnect_short}} 配合使用时，需要此 URL。如果启用了“基本认证”，那么还需要记录分配的用户名和密码。

### 将 IBM Integration Bus API 与 API Connect 集成。
{: #integrateiibapic}

1. 将与 IBM Integration Toolkit 中的 REST API 项目关联的 Swagger 文件导入到 {{site.data.keyword.apiconnect_short}} 服务。 
	1. 登录到 {{site.data.keyword.apiconnect_short}} {{site.data.keyword.Bluemix_notm}} 服务。
	2. 在 API Manager UI 导航窗格中，选择**草稿** > **API**。这将打开 API 选项卡。
	3. 选择 **+ 添加** > **通过文件或 URL 导入 API**。这将打开“*导入 OpenAPI (Swagger)*”窗口。
	4. 要从本地文件系统上传您创建的文件，请单击**选择文件**，然后选择已使用 IBM Integration Bus 创建的文件。扩展名为 `.json`、`.yml` 和 `.yaml` 的文件在包含有效 Swagger 定义的情况下受支持。确保选择了**添加产品**选项。（可选）您可以通过选择**将此产品发布到目录**发布产品。
	5. 单击**导入**。这将创建新的 REST API 定义，包括路径和 HTTP 操作。提示：如果导入时间超过了 1 分钟，请取消导入，刷新浏览器，然后重试导入。您的会话可能已到期。
2. 将 {{site.data.keyword.apiconnect_short}} 中的已导入 API 与 IBM Integration Bus on Cloud 中的 API 相关联。
	1. 转至 {{site.data.keyword.apiconnect_short}} 的仪表板。
	2. 选择**草稿** > **API**。
	3. 单击导入的 REST API。
	4. 选择“组合”选项卡，选择**创建组合件**以添加代理策略。
	5. 将**代理**策略拖动到新的空策略以启用该策略。
	6. 粘贴从 IBM Integration Bus on Cloud 的“公共端点”部分复制的 API 的 URL。
	7. 如果为 REST API 启用了基本认证，请输入在 IBM Integration Bus on Cloud 中生成的用户名和密码。
	8. 保存 API 设置。
3. 测试 API。
	1. 在 API 的“组合”选项卡中，选择“测试”按钮 ![“测试”按钮](images/a_play_button.jpg "此截屏显示“测试”按钮图标。")。
	2. 选择**重新发布产品**。
	3. 选择“操作”。
	4. 输入必需参数。
	5. 选择**调用**。
	6. 验证是否从 API 收到预期响应。 
	
导入并集成 API 定义后，可管理 API，如管理任何其他 REST API 定义一样。有关 API 的更多信息，请参阅[管理 API](managing_apis.html)。

## 在 IBM API Connect 中发布使用 IBM App Connect Professional 创建的 API

在本教程中，可以通过 {{site.data.keyword.apiconnect_full}} 发布并管理使用 IBM App Connect Professional 创建的 REST API。

### 先决条件
{: #prereq_pub_api_appconn}

您需要 IBM App Connect Professional on Cloud 和 {{site.data.keyword.apiconnect_short}} 的有效帐户才能完成此教程的学习。请确保您的 REST API 文件符合 Swagger 规范 V2.0。该文件的格式可以是 JSON 或 YAML。

您可以使用 IBM App Connect Professional 创建 REST API，这些 API 是专用应用程序，可用于将集成作为 RESTful Web Service 公开且可由 HTTP 客户机调用。创建 API 后，您可以通过使用 {{site.data.keyword.apiconnect_short}} 来发布并管理这些 API。以下列表中包含了在 {{site.data.keyword.apiconnect_short}} 中管理 API 的一些优势：

- 您可以监视对 API 执行的调用数。
- 您可以控制对 API 执行的调用数。
- 您可以维护多个 API 版本。

有关更多优点，请参阅[管理 API](managing_apis.html)。要在 IBM App Connect Professional 中创建 REST API 并将其发布到 {{site.data.keyword.apiconnect_short}}，请完成以下步骤：

1. 通过使用 IBM App Connect Professional 创建 REST API。
  - 使用 IBM 标识登录到 [App Connect Professional Web 管理控制台 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://appconnect.ibmcloud.com/professional/){:new_window}。有关如何完成使用 IBM App Connect Professional Web 管理控制台创建 REST API 的任务的更多信息，请参阅 IBM Knowledge Center 中的[关于管理控制台设置 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SS3LC4_7.5.2.0/com.ibm.wci.appliance.doc/About_the_WMC/consoleSettings.html){:new_window}。
  - 选择“生产”选项卡（如果尚未选择）。
  - 在导航面板中选择**存储库** > **配置**。
  - 在“项目配置”屏幕中，选择要发布到 {{site.data.keyword.apiconnect_short}} 的项目。将显示要发布的项目的“配置详细信息”。
  - 选择**推送到 API 管理**。**提示**：仅当您要导入的项目的状态为正在运行或已部署时，**推送到 API 管理**按钮才处于活动状态。如果未显示此链接，请选择播放按钮以启动此项目。
  - 在“推送到 API 管理”屏幕上，输入以下信息以创建与 API 管理系统的连接。

  <table><caption>表 1. 用于向 {{site.data.keyword.apiconnect_short}} 发布 API 的连接信息</caption>
  <thead>
  <tr>
  <th>字段名称</th>
  <th>描述</th>
  </tr>
  </thead>
  <tbody>
  <tr><td>主机</td>
  <td>指定管理集群、服务器或云地址的主机名。对于 {{site.data.keyword.Bluemix_notm}}，此条目最有可能是 us.apiconnect.ibmcloud.com。</td>
  </tr>
  <tr>
  <td>端口</td>
  <td>指定连接到管理集群、服务器或云地址所需的端口号。</td>
  </tr>
  <tr><td>用户标识</td>
  <td>指定用于访问管理集群、服务器或云地址的认证用户名。此条目最有可能是您用于登录到 {{site.data.keyword.Bluemix_notm}} 的 IBM 标识。</td>
  </tr>
  <tr><td>密码</td>
  <td>指定用于访问管理集群、服务器或云地址的认证密码。此条目最有可能是您用于登录到 {{site.data.keyword.Bluemix_notm}} 的 IBM 标识密码。</td>
  </tr>
  </tbody>
  </table>

2. 选择**装入组织**以填充与您的标识和密码相关联的组织列表。

3. 选择**组织**以将该项目与其中一个可用组织相关联。

4. 选择**推送到 APIM**，然后选择**确定**。

5. 选择**关闭**以关闭窗口。一个新的浏览器选项卡将在缺省浏览器中打开，并显示您的 API。

将 IBM App Connect API 与 {{site.data.keyword.apiconnect_short}} 相关联。

#### 导入 Swagger API 定义

要将与 IBM App Connect 中的 REST API 项目关联的 Swagger 文件导入到 {{site.data.keyword.apiconnect_short}} 服务，请执行以下步骤：

1. 登录到 {{site.data.keyword.apiconnect_short}} {{site.data.keyword.Bluemix_notm}} 服务。

1.  在 API Manager UI 标题栏中，选择**导航至** > **草稿**。

2. 在菜单栏中选择 **API**。这将打开 API 选项卡。

3. 选择已导入的 API 以打开 API Designer。

4. 在导航窗口中选择**组合**。策略的列表将显示在导航窗口中。

5. 如果需要，请选择**创建组合件**。

6. 通过将**调用**策略拖至主窗口中的组合件来添加此策略。

7. 在主窗口中选择**调用**策略可修改其配置设置。

8. 使用以下信息配置 URL 字段的 host/basePath：

- **hostname**：这是取决于云实例的设置。有关此设置的更多信息，请参阅 [IBM App Connect Professional ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://provide.castiron.ibmcloud.com){:new_window}。

- **basepath**：您在 App Connect Professional 编排中的 httpReceive 请求注释上指定的路径。

9. 添加 IBM 标识用户名和密码并将其保存到用于 App Connect Professional 的 HTTP 基本认证详细信息中。

#### 测试 API

要测试 API，请执行以下步骤：

1. 在 API 的“组合”选项卡中，选择“测试”按钮 <img alt="此截屏显示“测试”按钮图标" src="images/a_play_button.jpg" />。
2. 选择**重新发布产品**。
3. 选择“操作”。
4.  输入必需参数。
5. 选择**调用**。
6. 验证是否从 API 收到预期响应。

导入并集成 API 定义后，可管理 API，如管理任何其他 REST API 定义一样。有关 API 的更多信息，请参阅[管理 API](managing_apis.html)。


