---

copyright:
  years: 2017
lastupdated: "2017-10-19"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# 使用 Node.js 创建 API

**持续时间**：20 分钟  
**技能级别**：初学者  

---
## 目标

本教程将指导您逐步使用 LoopBack 框架以 Node.js 创建 API。本教程将描述如何执行以下操作：
1. 创建新的 LoopBack 项目。
2. 使用 {{site.data.keyword.apiconnect_short}} 工具箱中的 API Designer 向 LoopBack 项目添加新的数据源和模型。
3. 使用 API Designer 浏览工具测试 API 端点。

---
## 先决条件

开始之前，请[安装 {{site.data.keyword.apiconnect_short}} 工具箱](tut_prereq_install_toolkit.html)。

---
## 创建 LoopBack 项目

可以使用 {{site.data.keyword.apiconnect_short}} 开发者工具箱命令行界面或 API Designer 界面来创建 LoopBack 项目。 
 
### 使用工具箱命令行创建 LoopBack 项目

要使用 {{site.data.keyword.apiconnect_short}} 工具箱命令行创建 LoopBack 项目，请完成以下步骤：
1.  在命令行界面中，输入以下命令。此命令用于创建和管理 LoopBack 应用程序。
	```bash 
	apic loopback
	```
	>![参考信息]
	>对于本教程，将创建名为 weather-data 的项目。
2.  在提示符处，输入 `weather-data` 作为项目名称，然后按 **Enter** 键。
	```bash
	? What's the name of your application? weather-data
	```
  	>![重要信息]
  	>通常，项目名称可以包含除空格（“ ”）、正斜杠（“/”）、“&”符号、“@”符号、加号（“+”）、百分号（“%”）和冒号（“:”）以外的其他任何字符。
3.  输入要在其中创建项目的目录的名称。按 **Enter** 键可使用与项目同名的目录，或者输入新名称，然后按 **Enter** 键。
	```bash
	? Enter name of the directory to contain the project: weather-data
	```
4.  选择要使用的 LoopBack 版本。请选择当前生产版本：3.x。
	```bash
	? Which version of LoopBack would you like to use? 
  	2.x (long term support) 
	? 3.x (current) 
	```
5.  通过使用方向键选择 **empty-server**，指定要创建的应用程序的类型。
	```bash
	? What kind of application do you have in mind? (Use arrow keys)
	? empty-server (An empty LoopBack API, without any configured models or datasources) 
  	hello-world (A project containing a basic working example, including a memory database) 
  	notes (A project containing a basic working example, including a memory database)
	```
6.  按 **Enter** 键以创建空的 LoopBack API。 

工具在创建项目目录并向其添加多个目录和文件时，将显示多条消息。
工具还将运行 npm install 以安装 package.json 中指定的所有项目依赖项。此过程将创建 node_modules 目录，并且可能需要一些时间。

空的 LoopBack 项目包含以下目录：
- server：包含服务器模型和数据源定义以及其他服务器代码
- definitions：包含 YAML 定义文件
- node_modules：由 node.js 创建


### 使用 API Designer 界面创建 LoopBack 项目

要使用 API Designer 创建 LoopBack 项目，请完成以下步骤：
1.  在命令行界面中，输入以下命令以启动 API Designer：
	```bash
	apic edit
	```
	![](images/api-designer-1.png)
	>![参考信息]
	>以上命令会初始化 APIC 工具箱，并在完成后在缺省浏览器中启动 API Designer。
	>![参考信息]
	>在本教程中，将创建名为 weather-data 的项目。
2.  如果先前未锁定 UI 导航窗格，请单击“导航至”图标 ![](images/navigate-to.png)。这将打开 API Manager UI 导航窗格。要锁定 UI 导航窗格，请单击“锁定菜单”图标 ![](images/pinned.png)。
3.  在侧边栏中，单击“添加项目”图标 ![](images/add-icon.png)。
4.  单击**创建 LoopBack 项目**。您将看到**添加新的 LoopBack 项目**对话框。
5.  选择 **empty-server** 作为项目模板。
6.  对于 **LoopBack 版本**，选择 V3.x（当前版本）。
7.  对于“显示名称”和“名称”字段，输入 `weather-data`。
8.  对于**项目目录**，通过单击**浏览**按钮，选择在步骤 1 中创建的 `weather-data` 文件夹。![](images/api-designer-2.png)
9. 单击**添加**以添加项目。
	>![参考信息]
	>工具在创建项目目录并向其添加多个目录和文件时，将在**添加新的 LoopBack 项目**窗口中显示多条消息。工具还将运行 npm install 以安装 package.json 中指定的所有项目依赖项。此过程将创建 node_modules 目录，并且可能需要一些时间。
	
	>空的 LoopBack 项目包含以下目录：
	- server：包含服务器模型和数据源定义以及其他服务器代码
	- definitions：包含 YAML 定义文件
	- node_modules：由 node.js 创建
10. 单击**完成**以关闭**添加新的 LoopBack 项目**对话框。
11. 通过返回到步骤 1 中的命令行并输入 `Ctrl + C` 来退出 **API Designer**。输入 `Y` 以确认退出。
12. 关闭浏览器会话。

---
## 添加新的数据源和模型

要使用 API Designer 向 LoopBack 项目添加新的模型和数据源，请完成以下步骤：

### 添加数据源
要使用 API Designer 向 LoopBack 项目添加新的数据源，请完成以下步骤。
1. 还必须如`通过命令行创建 LoopBack 项目`中所述，创建 LoopBack 项目（“weather-data”项目），并确保当前工作目录是项目根目录：
	```bash
	cd weather-data
	```
2. 在命令行中，输入以下命令：
	```bash
	apic edit
	```
	在短暂停顿后，控制台将显示以下消息：
```bash
	Express server listening on http://127.0.0.1:9000
	```
	API Designer 将在缺省 Web 浏览器中打开，如果您最近未登录过，那么初始会显示登录页面。  
	>![参考信息]
	>可以使用自己的 Bluemix 帐户进行登录，也可以创建一个帐户。
3. 单击**数据源**图标 ![](images/datasource-icon.png)。
4. 单击**添加**。这将打开“新建 LoopBack 数据源”窗口。
5. 在**名称**文本字段中输入 `weatherDS`。
	>![参考信息]
	>可以在数据源名称中使用任何字母数字字符、连字符和下划线。
6. 单击**新建**。
7. 缺省情况下，**连接器**设置显示**内存中数据库**，并且其他设置为空白。目前请保留缺省设置，API Designer 会自动保存新数据源。
	>![参考信息]
	>内存中数据源内置于 LoopBack 中，但仅适用于开发和初始测试。准备好将模型连接到实际数据源（如数据库服务器）时，请相应地更改**连接器**设置，并按照[安装 LoopBack 连接器 ![外部链接图标](../../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSMNED_5.0.0/com.ibm.apic.toolkit.doc/tapim-connector-install.html#task_i2p_dnw_vv){:new_window} 中的指示信息安装数据源连接器。根据连接器类型，相应地输入连接器设置（主机名、数据库名称、用户名和密码），然后单击**保存**图标 ![](images/save-icon.png)。API Designer 会自动测试与数据源的连接。如果测试成功，将显示**成功 - 数据源连接测试成功**消息。
8. 单击“测试连接”图标 ![](images/db-test-icon.png) 以测试数据源连接。这将显示消息“数据源连接测试成功”。
9. 单击**所有数据源**。数据源会显示在数据源列表中，并且编辑器会使用新数据源的设置来更新 server/datasources.json 文件。

### 添加模型

要使用 API Designer 向 LoopBack 项目添加新模型，请完成以下步骤：
1. 单击**模型**图标 ![](images/models-icon.png)。
2. 单击**添加**。这将打开“新建 LoopBack 模型”窗口。
3. 在**名称**文本字段中输入 `weather`，然后单击**新建**。
4. 在**数据源**字段中，选择 **weatherDS**。![](images/new-model-1.png)
5. 在**属性**中，单击**添加属性**图标 ![](images/add-icon.png)。
6. 在**属性名称**文本字段中，输入 `zip_code`。
7. 对于**类型**，选择 **number**。
8. 选中**必需**以使此属性成为必需属性。这表示在添加或更新模型实例时，此属性必须具有值。目前，请保留其他设置的缺省值：
	- **是数组**：属性是否为包含指定类型的元素的 JavaScript 数组。
	- **标识**：属性是否为唯一标识。
	- **索引**：属性是否表示作为数据库索引的列（字段）。
	- **描述**：属性的文本描述。
9. 再次单击**添加属性**图标 ![](images/add-icon.png) 以添加其他属性。请参阅下表以完成其余属性：
	![](images/new-model-property-1.png)
10. 单击**保存**图标 ![](images/save-icon.png) 以保存更改。
11. 单击**所有模型**以完成对模型的编辑。

这将完成向 weather-data LoopBack 项目添加新数据源和模型的操作。

---

## 测试 LoopBack 项目

>![参考信息]
	>如果完成“添加新的模型和数据源”部分后未退出 {{site.data.keyword.apiconnect_short}} Designer，那么可以直接转至下面的步骤 2。
	
要使用 API Designer 浏览工具测试 API 端点，请完成以下步骤：
1. 在命令行中，输入以下命令：
	```bash
	apic edit
	```
	在短暂停顿后，控制台将显示以下消息：
```bash
	Express server listening on http://127.0.0.1:9000
	```
	API Designer 将在缺省 Web 浏览器中打开，如果您最近未登录过，那么初始会显示登录页面。
2. 启动本地测试服务器。
	a. 在屏幕底部的测试控制台中，单击**启动服务器**图标 ![](images/test-icon.png)：
	![](images/start-server-1.png)
	b. 等待显示“正在运行”消息：
	![](images/running-server-1.png)

	>![参考信息]
	>根据项目配置以及是否有其他进程在运行，可能会显示不同的端口号。
3. 单击 **http://127.0.0.1:port_number** 以显示 API 根端点。对于缺省 LoopBack（为空或为 hello-world）项目，将看到类似于以下内容的内容：
	```bash
	{"started":"2017-05-24T19:21:47.807Z","uptime":80.876}
	```
	>![参考信息]
	>要停止项目，请单击**停止服务器**图标 ![](images/stop-icon.png)：
	>![](images/stop-server-1.png)
	
	>要将其重新启动，请单击**重新启动服务器** icon ![](images/restart-icon.png)：
	>![](images/restart-server-1.png)
	
4. 单击**浏览**图标 ![](images/explore-icon.png) 以查看 API Designer 浏览工具。侧边栏将显示 API 中 LoopBack 模型的所有 REST 操作。缺省情况下，基于 PersistedModel 的模型有[一组标准的创建、读取、更新和删除操作 ![外部链接图标](../../../icons/launch-glyph.svg "外部链接图标")](http://loopback.io/doc/en/lb2/PersistedModel-REST-API){:new_window}。

5. 单击左侧窗格中的 **weather.create** 操作以显示端点。
![](images/explore-test-1.png)
中间窗格显示有关端点的摘要信息，包括其参数、安全性、模型实例数据和响应代码。右侧窗格提供使用 curl 命令以及 Ruby、Python、Java 和 Node 等语言调用端点的模板代码。

6. 要在 API Designer 浏览工具中测试 REST 端点，请在右侧窗格上单击**试用**。向下滚动到**参数**，然后单击**生成**以生成一些哑元数据。缺省情况下，生成的数据包括 `zip_code`、`current_temperature`、`current_humidity`、`tonight_temperature_low`、`tonight_temperature_high`、`tonight_humidity_low`、`tonight_humidity_high` 和 `id` 属性。`id` 属性由 LoopBack 针对给定模型创建，其值将自动生成。从样本数据中除去 `id` 属性，根据需要更新生成的数据，然后单击**调用操作**。
![](images/explore-test-2.png)
>![故障诊断]
>如果看到由于本地主机的证书不可信而生成的错误消息，请单击 API Designer 浏览工具中的错误消息内提供的链接以接受证书，然后继续在 Web 浏览器中调用操作。具体过程取决于您使用的 Web 浏览器。如果在浏览器中直接装入 REST 端点，那么将看到以下消息：{"name":"PreFlowError","message":"unable to process the request"}。必须使用 API Designer 浏览工具在浏览器中测试 REST 端点，因为该端点包含必需的头和其他请求参数。
>
>![故障诊断]
>如果获得响应代码 **422 - 无法处理的实体**，其中包含以下有效内容：
>![](images/explore-test-3.png)
>
>说明 `id` 数据元素尚未从生成的数据中除去。请除去 `id` 数据元素，然后重新运行测试。
>![故障诊断]
>如果收到错误称**未能解析请求主体**，那么必须除去最后一个 `humidity_high` 数字后的逗号。
7. 编辑 **data** 部分中显示的 JSON 格式的值。尝试更改生成的哑元数据，然后再次单击**调用操作**。您应该会看到请求和响应参数以及您输入的 JSON 实例数据。
![](images/explore-test-4.png)

8. 要确认操作是否添加了模型实例，请单击 **weather.find**。单击**调用操作**以显示所有天气实例。例如（有两个模型实例）：

	![](images/explore-test-5.png)
---

### 在本教程中完成的操作
在本教程中，您已完成以下操作：
1. 使用 {{site.data.keyword.apiconnect_short}} 工具箱命令行创建了新的 LoopBack 项目。
2. 使用 {{site.data.keyword.apiconnect_short}} 工具箱中的 API Designer 向 LoopBack 项目添加了新的模型和数据源。
3. 使用 API Designer 浏览工具测试了 API 端点。


---

## 下一步

[管理 REST 服务](tut_rest_landing.html)或[管理 SOAP 服务](tut_manage_soap_api.html)。

创建 > **管理** > 安全 > 社交化 > 分析

 
[important]: ./images/important.png "重要信息！"
[info]: ./images/info.png "参考信息"
[troubleshooting]: ./images/troubleshooting.png "故障诊断" 

