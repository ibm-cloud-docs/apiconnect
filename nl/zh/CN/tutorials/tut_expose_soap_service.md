---

copyright:
years: 2017
lastupdated: "2017-11-14"

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
 

# 将 SOAP 服务公开为 REST API
**持续时间**：20 分钟  
**技能级别**：初学者  

---
## 目标
在 API Manager 中，您将创建一个 REST API，用于访问现有 SOAP 服务并将其公开为 REST API。

## 先决条件
1. 开始之前，需要[设置 {{site.data.keyword.apiconnect_full}} 实例](tut_prereq_set_up_apic_instance.html)。
2. 开始之前，请将 [weatherprovider.wsdl 测试 ![外部链接图标](../../../icons/launch-glyph.svg "外部链接图标")](https://raw.githubusercontent.com/IBM-Bluemix-Docs/apiconnect/master/tutorials/weatherprovider.wsdl){:new_window} 文件复制到本地文件系统。
	>![images/info.png]
	>可以单击**原始**，然后将生成的页面在本地系统上另存为 `.wsdl` 文件。

---
## 设置 REST API 定义
1. 登录到 {{site.data.keyword.Bluemix_short}}：[https://new-console.ng.bluemix.net/login ![外部链接图标](../../../icons/launch-glyph.svg "外部链接图标")](https://new-console.ng.bluemix.net/login){:new_window}。
2. 在 {{site.data.keyword.Bluemix_notm}} **仪表板**中，向下滚动并选择 {{site.data.keyword.apiconnect_short}}。或者，从菜单图标中，选择**服务**，接着选择 **API** 以访问**使用 API** 窗口，然后选择 **API Connect**。在 **API Connect** 页面中，可以直接按`创建`，也可以调整缺省设置。对于本练习，请将此实例保留未绑定状态，并调整“服务名称”以方便以后更容易识别。例如，`API Connect-weather-exercise`。按`创建`按钮以启动 {{site.data.keyword.apiconnect_short}} 服务。  
您可能会看到一条描述新增内容的警报，或者看到**草稿 API** 信息启动页面。阅读相应信息后，单击“**知道了**”图标以查看 API Manager。
3. 在 {{site.data.keyword.apiconnect_short}} 中，如果先前未锁定 UI 导航窗格，请单击**导航至**图标 ![](images/navigate-to.png)。这将打开 API Manager UI 导航窗格。要锁定 UI 导航窗格，请单击**锁定菜单**图标 ![](images/pinned.png)。
4. 在 UI 导航窗格中选择**草稿**，然后单击 **API** 选项卡。这将打开 **API** 选项卡。
![](images/drafts-api-1.png)
5. 选择**添加 +** > **新建 API**。
6. 指定有关 API 的基本信息。
	- 在**标题**字段中，输入 `Weather Data`。
	- 输入标题时，**名称**字段会填充 `weather-data`，请保留此值不变。	
	- 将**基本路径**字段保留为 `/weather-data`。
	- 将**版本**字段保留为 `1.0.0`。
7. 展开**其他属性**以指定 API 的其他属性。
	- 从 **API 模板**字段中，选择**缺省值**以指示您想要使用缺省模板来创建 API 定义。
	- 将其余字段保留不变。
![](images/new-api-1.png)
8. 将 API 添加到新产品，然后创建 API 定义。
	- 选择**添加产品**。
	- 在**标题**字段中，使用 `Weather Data product` 作为缺省值。
	- 将**名称**和**版本**字段保留不变。
	- 确保选中**将此产品发布到目录**复选框，然后选择**沙箱**作为目标目录。
![](images/new-api-2.png)
	- 单击**创建 API**。这将打开 API 定义草稿的**设计**选项卡。
9. 现在，API 已创建。将显示“设计”页面。单击导航栏中的**安全性**。
![](images/api-security-1.png)
10. 取消选中 **ClientID** 选项。
![](images/api-security-2.png)
	>![](images/info.png)
	
>您可能会注意到，在“保存”磁盘图标旁显示有一个黄色三角形图标。这是警告，指示存在已定义但尚未使用的定义。（此警告不会影响 API 定义。）
11. 在**定义**部分中，单击**添加定义**图标 ![](images/add-icon.png)，然后通过单击该图标来展开新定义。
12. 将定义命名为 `Weather Data Output`。
13. 该定义将有五个属性。请单击**添加属性**四次以添加其他属性。参考下图来对`属性名称`重命名，并对`描述`、`类型`和`示例`使用缺省值：![](images/definition-new-1.png)
14. 在**路径**部分中，单击**添加路径**图标 ![](images/add-icon.png)。
15. 在新创建的路径的**路径**字段中，将内容替换为 `/getweatherdata`。
16. 通过单击 **GET /getweatherdata** 操作以将其展开。![](images/path-new-1.png)
17. 对于 **GET /getweatherdata** 操作，请单击**添加参数**，然后单击**添加新参数**。
18. 将新参数命名为 `zip_code`，并将其余参数保留缺省值。
19. 在**响应**部分中 **200 OK** 响应的**模式**列中，选择 **Weather Data Output** 定义。对于 API 调用的响应，**Weather Data Output** 定义的对象将为响应对象。
![](images/path-new-2.png)
20. 单击“保存”图标 ![](images/save-icon.png) 以保存更改。

---
## 添加和配置 Web Service 调用
要添加并配置用于将 Web Service 集成到 API 定义中的 invoke 和 map 策略，请完成以下步骤。
1. 在**服务**部分中，单击**添加服务**图标 ![](images/add-icon.png)。这将打开`通过 WSDL 导入 Web Service` 窗口。
![](images/upload-file-1.png)
2. 选择**上传文件**。
3. 在**文件上传**窗口中，指定在**先决条件**部分的`步骤 2` 中下载的 `weatherprovider.wsdl` 文件的位置，然后单击**打开**以继续。
4. 选择 **weatherService** SOAP 服务，然后单击**完成**。在**服务**部分中，**WeatherService** Web Service 与单个 **weatherRequest** 操作一起列出。
![](images/upload-file-2.png)

	![](images/services-add-1.png)	
5. 导航至**组合**选项卡，然后确保选中 **DataPower Gateway 策略**。
6. 通过将光标悬停在画布上的现有 **invoke** 策略上并单击**删除策略**图标 ![](images/delete-icon.png)，从而删除该策略。
![](images/delete-invoke-1.png)	
7. 将 **weatherRequest** Web Service 从选用板中拖至画布上显示的虚线框中。这会将一个 invoke 策略和两个 map 策略放入组合件中。第一个 map 策略用于将变量分配给 Web Service 调用的输入，第二个 map 策略用于将 Web Service 调用的输出分配给变量。第一个 map 的输出和第二个 map 的输入通过步骤 4 中提供的 WSDL 生成。
![](images/services-add-2.png)	
8. 单击 **weatherRequest: input** map 策略，然后单击属性表的“输入”列中的**编辑输入**图标 ![](images/edit-icon.png)。
![](images/services-add-3.png)	
9. 单击 **+ 操作参数**，然后选择 `get /getweatherdata`。
10. 单击**完成**以添加 `zip_code` 参数。
![](images/webservice-input-1.png)
11. 单击输入侧与 **zip_code string** 对应的圆圈，然后单击输出侧与 **zipcode string** 对应的圆圈。  
	![](images/webservice-input-2.png)
12. 关闭属性表。
13. 单击选用板中的 **weatherRequest: output** map 策略，然后单击属性工作表的“输出”列中的**编辑输出**图标 ![](images/edit-icon.png)。
14. 选择 **+ 操作输出**，然后选择 `get /getweatherdata`。
15. 选择**完成**以添加 `Weather Data Output` 输出定义。
![](images/webservice-output-1.png)
16. 单击输入侧与 **zip string** 对应的圆圈，然后单击输出侧与 **zip string** 对应的圆圈。参考下图来映射其余参数。
![](images/webservice-output-2.png)
17. 单击**保存**图标 ![](images/save-icon.png) 以保存更改。

您已在组合件中包含 Web Service 调用，并已将输入参数映射到 SOAP 请求的相应部分，将 SOAP 响应的相应部分映射到 JSON 输出。

---
## 测试 API 定义
要使用 API Manager 测试工具来测试 API 定义，请完成以下步骤。
1. 单击**组合件**选项卡下的**测试**图标 ![](images/test-icon.png) 以显示测试窗格。
![](images/test-pane-1.png)
2. 如果原先曾使用过测试工具，请单击**更改设置**。
3. 从产品列表中选择 `Weather Data product 1.0.0`。
![](images/choose-product-1.png)
4. 单击**重新发布产品**。
5. 单击**下一步**。
6. 从操作列表中选择 `get /getweatherdata`。  
	![](images/select-operation-1.png)
7. 向下滚动到 **zip_code** 字段，然后输入 `90210`。  
	![](images/test-api-1.png)
8. 单击**调用**。API 将返回当前天气。  
	![](images/test-api-2.png)

---
## 在本教程中执行的操作
在本教程中，您已完成以下活动：
1. 设置 REST API 定义
2. 配置 API 以调用现有 Web Service 并返回其输出
3. 测试 API 定义

---

## 下一步

使用[速率限制](tut_rate_limit.html)、[客户机标识和私钥](tut_secure_landing.html)或[使用 OAuth 2.0 进行保护](tut_secure_oauth_2.html)来保护 API。

创建 > **管理** > 安全 > 社交化 > 分析

[important]: ./images/important.png "重要信息！"
[info]: ./images/info.png "参考信息"
[troubleshooting]: ./images/troubleshooting.png "故障诊断" 
