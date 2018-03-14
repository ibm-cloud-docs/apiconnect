---
copyright:
  years: 2017
lastupdated: "2017-11-02"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 使用 {{site.data.keyword.Bluemix_notm}} 导入 API 规范并代理现有 REST 服务
持续时间：5 分钟  
技能级别：初学者  

## 目标
本教程通过说明如何将现有 API 纳入管理控制，帮助您快速上手使用 {{site.data.keyword.apiconnect_full}}。首先将导入 OpenAPI 规范，然后为现有 REST 服务创建传递 API 代理。

## 先决条件
开始之前，需要[设置 {{site.data.keyword.apiconnect_short}} 实例](tut_prereq_set_up_apic_instance.html)。

---


## 浏览样本应用程序并测试目标端点

针对本教程已经创建了样本 _Weather Provider_ 应用程序。对应的 API 规范 (Swagger 2.0) 位于 [weather-provider-api_1.yaml ![外部链接图标](../../../icons/launch-glyph.svg "外部链接图标")](https://raw.githubusercontent.com/IBM-Bluemix-Docs/apiconnect/master/tutorials/weather-provider-api_1.yaml){:new_window} 文件中。

1. 要浏览该应用程序，请转至 [http://gettingstartedweatherapp.mybluemix.net/ ![外部链接图标](../../../icons/launch-glyph.svg "外部链接图标")](http://gettingstartedweatherapp.mybluemix.net/){:new_window}。  
2. 输入有效的 5 位美国邮政编码，以获取_**当前天气**_和_**今日预测**_。  
![](images/explore-weatherapp-1.png)

3. 以上样本天气应用程序是使用提供天气数据的 API 构建的。用于获取**当前**天气数据的端点为 `https:// myweatherprovider<span></span>.mybluemix.net/current?zipcode={zipcode}`。通过访问 [https://myweatherprovider.mybluemix.net/current?zipcode=90210 ![外部链接图标](../../../icons/launch-glyph.svg "外部链接图标")](https://myweatherprovider.mybluemix.net/current?zipcode=90210){:new_window} 对其进行测试。  

  ![](images/explore-weatherapp-2.png)

4. 与此类似，用于获取**今日**预测数据的端点为 `https:// myweatherprovider<span></span>.mybluemix.net/today?zipcode={zipcode}`。通过转至 [https://myweatherprovider.mybluemix.net/today?zipcode=90210 ![外部链接图标](../../../icons/launch-glyph.svg "外部链接图标")](https://myweatherprovider.mybluemix.net/today?zipcode=90210){:new_window} 对其进行测试。  

  ![](images/explore-weatherapp-3.png)


---

## 导入样本应用程序的 OpenAPI 规范以创建 REST API 代理
1. 登录到 {{site.data.keyword.Bluemix_short}}：https://new-console.ng.bluemix.net/login。
2. 在 {{site.data.keyword.Bluemix_notm}} 导航面板中，选择**服务**，然后选择**仪表板**。启动 {{site.data.keyword.apiconnect_short}} 服务。 
3. 在 {{site.data.keyword.apiconnect_short}} 中，确保左侧的导航面板已打开。如果未打开，请单击 **>>** 将其打开。  
4. 在导航面板中选择**草稿**。   
5. 在 **API** 选项卡中，单击**添加**。从下拉菜单中，选择**通过文件或 URL 导入 API**。  
     ![](images/import-1.png)

6. 现在，我们将导入 OpenAPI 天气定义。在打开的“导入 OpenAPI (Swagger)”对话框中，输入以下 URL：`https://raw.githubusercontent.com/IBM-Bluemix-Docs/apiconnect/master/tutorials/weather-provider-api_1.yaml`。将其他选项保留其缺省值，然后单击**导入**。  
    ![](images/import-2.png)  

7. 导入 OpenAPI 规范后，将转至 API 的**设计**视图。在其中，可以查看 OpenAPI 定义的各个部分。滚动进行浏览，并记下**主机**值。还可以在**源**选项卡下查看 OpenAPI。_注：您将注意到“主机”值设置为 _`$(catalog.host)`_。这是 API 代理的基本 URL。_
8. API 已保存。 


## 测试 API 代理

### 使用 _API Manager 测试工具_进行测试。
1. 在**组合**选项卡中，单击表示更多操作的图标，然后选择**生成缺省产品**。  
  ![](images/generate-default-product-1.png)   

2. 接受**新建产品**对话框中的缺省选项，然后单击**创建产品**。这将创建 **Weather Provider API 产品**，并将其发布到“沙箱”目录。此时将显示一条消息，指示产品成功生成。  
  ![](images/generate-default-product-2.png)  

  ![](images/generate-default-product-3.png)

  _在 {{site.data.keyword.apiconnect_short}} 中，**产品**用于对特定用途的 API 进行分组。产品将发布到**目录**。[{{site.data.keyword.apiconnect_short}} 词汇表](../apic_glossary.html)_

3. 在“组合”选项卡中，单击“播放”图标以测试 API 代理的目标调用。

4. 在“测试”面板中，选择 **get /current** 操作。  
    a. Zipcode 是此操作的必需参数，因此请输入有效的美国邮政编码（例如 90210）。  
    b. 单击**调用**，并验证是否看到以下内容：  
    ```
    - 200 OK response
    - Current weather data for 90210
    ```
_如果遇到 CORS 错误，请按照错误消息中的指示信息进行操作。单击错误中的链接以将例外添加到浏览器，然后重新点击“调用”按钮。_
    ![](images/test-invoke-1.png)


### 使用_浏览工具_进行测试。
_浏览工具允许用户通过强制实施在 OpenAPI 定义中设置的任何参数需求来测试 API 是否正确操作。此强制实施不会在“组合”选项卡中的“API 测试工具”中执行，因此它允许用户在缺少参数的情况下验证 API 行为。_

1. 要测试 API 代理端点，请选择**浏览**，然后选择**沙箱**。![](images/test-explore-1.png)
2. 从选用板中选择 **GET /current** 操作。
3. 选择“试用”。  
4. 在测试框中输入有效的美国邮政编码（例如 90210）。
5. 单击**调用操作**以查看响应。
![](images/test-explore-2.png)

    ![](images/test-explore-3.png)


### 结论
在本教程中，您了解了如何通过 API 传递代理来调用现有 REST 服务。首先，通过 Web 浏览器检查了样本服务的可用性。接着，在 {{site.data.keyword.apiconnect_short}} 中创建了 API 代理，并将该代理链接到要调用的样本服务。随后，将 API 打包成产品，将产品发布到目录，然后测试了代理。

---

## 下一步

使用[速率限制](tut_rate_limit.html)、[客户机标识和私钥](tut_secure_landing.html)或[使用 OAuth 2.0 进行保护](tut_secure_oauth_2.html)来保护 API。

创建 > **管理** > 安全 > 社交化 > 分析

