---

copyright:
  years: 2017
lastupdated: "2017-10-31"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 使用开发者工具箱导入 API 规范并代理现有 REST 服务
{: #tut_import_openapi_rest_tk}

持续时间：5 分钟  
技能级别：初学者  


## 目标
{: #object_tut_import_openapi_rest_tk}

本教程说明如何使用 {{site.data.keyword.apiconnect_full}} 将现有 API 纳入管理控制。在本教程中，将导入 OpenAPI 规范，然后为现有 REST 服务创建传递 API 代理。

## 先决条件
{: #prereq_tut_import_openapi_rest_tk}

开始之前，需要[设置 API Connect 实例](tut_prereq_set_up_apic_instance.html)和[安装 API Connect 工具箱](tut_prereq_install_toolkit.html)。

---


## 浏览样本应用程序并测试目标端点
{: #explore_tut_import_openapi_rest_tk}

针对本教程已经创建了样本 _Weather Provider_ 应用程序。对应的 API 规范 (Swagger 2.0) 位于 [weather-provider-api_1.yaml ![外部链接图标](../../../icons/launch-glyph.svg "外部链接图标")](https://raw.githubusercontent.com/IBM-Bluemix-Docs/apiconnect/master/tutorials/weather-provider-api_1.yaml){: #new_window} 文件中。

1. 要浏览该应用程序，请转至 [http://gettingstartedweatherapp.mybluemix.net/ ![外部链接图标](../../../icons/launch-glyph.svg "外部链接图标")](http://gettingstartedweatherapp.mybluemix.net/){: #new_window}。  
2. 输入有效的 5 位美国邮政编码，以获取_**当前天气**_和_**今日预测**_。  
![](images/explore-weatherapp-1.png)S

3. 以上样本天气应用程序是使用提供天气数据的 API 构建的。用于获取**当前**天气数据的端点为 `https://myweatherprovider.mybluemix.net/current?zipcode={zipcode}`。通过访问 [https://myweatherprovider.mybluemix.net/current?zipcode=90210 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://myweatherprovider.mybluemix.net/current?zipcode=90210){: #new_window} 对其进行测试。  

  ![](images/explore-weatherapp-2.png)

4. 与此类似，用于获取**今日**预测数据的端点为 `https:// myweatherprovider.mybluemix.net/today?zipcode={zipcode}`。通过转至 [https://myweatherprovider.mybluemix.net/today?zipcode=90210 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://myweatherprovider.mybluemix.net/today?zipcode=90210){: #new_window} 对其进行测试。  

  ![](images/explore-weatherapp-3.png)



---

## 导入样本应用程序的 OpenAPI 规范以创建 REST API 代理
{: #import_tut_import_openapi_rest_tk}

1. 启动 **API Designer**。在终端窗口中，输入以下命令：`apic edit`。
2. 使用您的 IBM 标识登录。![](images/screenshot_apic-edit_login.png)
3. 在 **API Designer** 中，确保导航面板已打开。如果未打开，请单击 >> 将其打开。
4. 在导航面板中，选择**草稿**。
5. 转至 **API** 选项卡。
6. 在“API”选项卡中，单击**添加**。
7. 从下拉菜单中，单击**通过文件或 URL 导入 API**。
![](images/toolkit-import-1.png)
8. 本教程中将使用天气 API 的 OpenAPI 2.0 定义。在“导入 OpenAPI (Swagger)”对话框中，输入以下 URL：`https://raw.githubusercontent.com/IBM-Bluemix-Docs/apiconnect/master/tutorials/weather-provider-api_1.yaml`。
9. 将_添加产品_选项保留未选中状态，然后单击**导入**。  
    ![](images/screenshot_import-url.png)  

导入 OpenAPI 规范后，将转至 API 的“设计”视图。在其中，可以查看 OpenAPI 定义的各个部分。滚动进行浏览，特别是要记下“主机”值。还可以在“源”选项卡下查看 OpenAPI。_您将看到“主机”值设置为 _ `$(catalog.host)`_。这是 API 代理的基本 URL。_
 


## 测试 API 代理
{: #test_tut_import_openapi_rest_tk}

1. 通过选择**启动服务器**图标来启动本地测试服务器。网关启动后，将看到状态自动更新为_**正在运行**_。
![](images/screenshot_start-server-1.png)

2. 选择**组合**选项卡。

3. 单击“播放”图标 (>) 以测试 API 代理的目标调用。_对于本教程，我们将使用嵌入式 Micro Gateway，因此请确保选中 **Micro Gateway 策略**。
![](images/screenshot_test-0.png)

4. 在“测试”面板中：
  - 选择 **get /current** 操作。  
  - Zipcode 是此操作的必需参数，因此请输入有效的美国邮政编码（例如 90210）。  
  - 选择**调用**，然后验证响应。

    _如果遇到 CORS 错误，请按照错误消息中的指示信息进行操作。单击错误中的链接以将例外添加到浏览器，然后重新单击**调用**。
  
  - 预期响应为 **200 OK** 响应，以及邮政编码 90210 所代表地区的当前天气数据。
![](images/screenshot_test-1.png)    


## 结论
{: #conclusion_tut_import_openapi_rest_tk}

在本教程中，您了解了如何通过 API 传递代理来调用现有 REST 服务。首先，通过 Web 浏览器检查了样本服务的可用性。接着，在 {{site.data.keyword.apiconnect_short}} 中创建了 API 代理，并将该代理链接到要调用的样本服务。最后，您使用 {{site.data.keyword.apiconnect_short}} 内部测试工具测试了此服务。

---

## 下一步
{: #next_tut_import_openapi_rest_tk}

使用[速率限制](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_rate_limit)、[客户机标识和私钥](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_landing)或[使用 OAuth 2.0 进行保护](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_oauth_2)来保护 API。

创建 > **管理** > 安全 > 社交化 > 分析
