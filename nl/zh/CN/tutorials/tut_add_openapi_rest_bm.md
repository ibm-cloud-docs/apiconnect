---
copyright:
  years: 2017
lastupdated: "2017-10-19"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 使用 IBM Bluemix 添加新的 API 规范并调用现有 REST 服务
**持续时间**：15 分钟  
**技能级别**：初学者  

## 目标
本教程旨在帮助您快速上手使用 {{site.data.keyword.apiconnect_full}}。首先将创建新的 OpenAPI 规范，然后为现有 REST 服务创建传递 API 代理。

## 先决条件
开始之前，需要[设置 API Connect 实例](tut_prereq_set_up_apic_instance.html)。

---

### 浏览样本应用程序并测试目标端点
针对本教程创建了样本 _Weather Provider_ 应用程序。
1. 要浏览该应用程序，请转至 [http://gettingstartedweatherapp.mybluemix.net/ ![外部链接图标](../../../icons/launch-glyph.svg "外部链接图标")](http://gettingstartedweatherapp.mybluemix.net/){:new_window}。  
2. 输入有效的 5 位美国邮政编码，以获取_**当前天气**_和_**今日预测**_。  
![](images/explore-weatherapp-1.png)

3. 以上样本天气应用程序是使用提供天气数据的 API 构建的。用于获取**当前**天气数据的端点为 _**https:// myweatherprovider<span></span>.mybluemix.net/current?zipcode={zipcode}**_。通过访问 [https://myweatherprovider.mybluemix.net/current?zipcode=90210 ![外部链接图标](../../../icons/launch-glyph.svg "外部链接图标")](https://myweatherprovider.mybluemix.net/current?zipcode=90210){:new_window} 对其进行测试。  

  ![](images/explore-weatherapp-2.png)

4. 与此类似，用于获取**今日**预测数据的端点为 _**https:// myweatherprovider<span></span>.mybluemix.net/today?zipcode={zipcode}**_。通过转至 [https://myweatherprovider.mybluemix.net/today?zipcode=90210 ![外部链接图标](../../../icons/launch-glyph.svg "外部链接图标")](https://myweatherprovider.mybluemix.net/today?zipcode=90210){:new_window} 对其进行测试。  

  ![](images/explore-weatherapp-3.png)


---

### 添加新的 OpenAPI 规范以创建 REST API 代理  
1. 登录到 {{site.data.keyword.Bluemix_short}}：https://new-console.ng.bluemix.net/login。
2. 在 {{site.data.keyword.Bluemix_short}} 导航面板中，选择**服务**，然后选择**仪表板**。启动 {{site.data.keyword.apiconnect_short}} 服务。
3. 在 {{site.data.keyword.apiconnect_short}} 中，确保导航面板已打开。如果未打开，请单击 **>>** 将其打开。  
4. 在导航面板中选择**草稿**。
5. 在 **API** 选项卡中，单击**添加**。从下拉菜单中，选择**新建 API**。    
  ![](images/create-new-1.png)  
6. 在*新建 API* 窗口中，输入 `Weather Provider API` 作为标题。_这将自动填充“名称”和“基本路径”_。  
  ![](images/bluemix-add-new-api.png)
7. 单击**创建 API** 以完成向导。  
8. 创建 API 后，已选择**设计**选项卡。 
9. 滚动到**主机**面板。如果字段未自动填写，请输入 `$(catalog.host)` 作为值。
10. 在**基本路径**面板中，记下自动填充的值：`/weather-provider-api`。您的 API 的目标 URL 将基于这些值进行创建。  

11. 滚动到**安全性**选项卡，然后删除已自动生成的“clientIDHeader (API Key)”。  
_（我们将在下一个教程的“API 密钥”中探讨安全性。）_  

12. 在导航中，向下滚动到**路径**面板，然后通过单击 **+** 来创建新路径。     
    a. 将新路径命名为“**/current**”。  
    b. 在相同的*路径*面板中，选择 **GET /current** 部分。    
    c. 在 **GET /current** 部分中，添加新的**参数**。您在浏览该样本应用程序时会注意到，天气服务需要将 zipcode 作为参数。   
      - 名称：zipcode  
      - 位于：查询  
      - 必需：是  
      - 类型：string   
    ![](images/path-current-1.png)   
    d. 保存 API。  

13. 通过上一步中定义的查询参数，现在需要定义在调用天气 API 时返回的响应对象。为此，请向下滚动到**定义**面板。   
    a. 添加新定义。  
    b. 将新定义命名为 _Current_。  
    c. 将“类型”设置为 _Object_。  
    d. 为 **Current** 定义添加新属性。    
       - 名称：zip         /  类型：string   
       - 名称：temperature /  类型：integer   
       - 名称：humidity    /  类型：integer   
       - 名称：city        /  类型：string   
       - 名称：state       /  类型：string   
    ![](images/definition-current-1.png)   
    e. 保存 API。  

14. 在上一步中，已定义响应对象。接下来，需要确保响应对象与 **get /current** 路径相关联。在导航中，向上滚动回**路径**面板。
    a. 打开 **GET /current** 操作，并滚动到**响应**部分。
    b. 将 200 OK 响应的模式从“object”更改为“**Current**”。
    c. 通过单击“保存”图标以保存 API。很快将显示“API 已保存”确认通知。 

15. 刚才创建的路径和操作用于获取当前天气数据。现在，需要创建类似的路径和操作来获取今日天气数据。通过步骤 12 中创建 **/current** 路径的类似方式，创建新路径：**/today**。

16. 在 **GET /today** 操作下添加新参数。
    - 参数名称：zipcode  
    - 位于：查询  
    - 必需：是  
    - 类型：string  

17. 创建新定义：**Today**。

18. 为 **Today** 定义添加新属性。
    - 名称：zip / 类型：string
    - 名称：hi / 类型：integer
    - 名称：lo / 类型：integer
    - 名称：nightHumidity / 类型：integer
    - 名称：dayHumidity / 类型：integer
    - 名称：city / 类型：string
    - 名称：state / 类型：string
19. 将 **GET /today** 部分中的响应模式更新为“Today”。
20. 保存 API。

21. 切换到**组合**选项卡。目前，您已创建两个操作：**GET /current** 和 **GET /today**。要确保调用正确的目标端点，需要创建一些逻辑，用于对所调用的操作执行条件。下面使用 **Operation Switch** 逻辑构造来执行此操作。  
    a. 删除可能已添加到_画布_的 **invoke** 策略。  
    b. 将 **Operation Switch** 从选用板中拖放到画布上。  
      - 对于**用例 0**，分配 **get /current** 操作。
      - 添加新用例：**用例 1**。
      - 将 **get /today** 操作分配给**用例 1**。![](images/assemble-1.png)**Operation Switch** 将提供决策点。相应的操作需要根据动词/路径对进行调用。
    c. 将 **invoke** 策略从选用板中拖放到画布上。_invoke 操作用于从操作中调用现有服务_。在 **/get current** 路径和 **/get today** 路径中分别放入一个 invoke 操作。   
    d. 在 **/get current** 路径中选择 **invoke** 策略，并将其标题更新为“**invoke-current**”。  
    e. 使用 `https://myweatherprovider.mybluemix.net/current?zipcode=$(request.parameters.zipcode)` 更新 URL 字段。  
    f. 在 **/get today** 路径中选择 **invoke** 策略，并将其标题更新为“**invoke-today**”。  
    g. 使用 `https://myweatherprovider.mybluemix.net/today?zipcode=$(request.parameters.zipcode)` 更新 URL 字段。  
       ![](images/assemble-2.png)

22. 保存 API。

---

### 测试 API 代理
1. 在**组合**选项卡中，单击表示更多操作的图标，然后选择**生成缺省产品**。  
   ![](images/generate-default-product-1.png) 

2. 接受**新建产品**对话框中的缺省选项，然后单击**创建产品**。这将创建 Weather Provider API 产品，并将其发布到“沙箱”目录。此时将显示一条消息，指示产品成功生成。  
  ![](images/generate-default-product-2.png)  
  
  ![](images/generate-default-product-3.png) 

  - _在 {{site.data.keyword.apiconnect_short}} 中，**产品**用于对特定用途的 API 进行分组。产品将发布到**目录**。[{{site.data.keyword.apiconnect_short}} 词汇表](../apic_glossary.html)_

3. 在“组合”选项卡中，单击“播放”图标以测试 API 代理的目标调用。

4. 在“测试”面板中，选择 **get /current** 操作。
	a. Zipcode 是此操作的必需参数，因此请输入有效的美国邮政编码（例如 90210）。 
	b. 单击**调用**，并验证是否看到以下内容： 
  ```
  200 OK response
  Current weather data for 90210  
  ```
  
    ![](images/test-invoke-1.png)  

    ![](images/test-invoke-2.png)  

    ![](images/test-invoke-3.png)

---

### 结论
在本教程中，您已学习如何通过 API 传递代理来调用现有 REST 服务。首先，通过 Web 浏览器检查了样本服务的可用性。接着，在 API Connect 中创建了新的 OpenAPI 规范，并将其链接到要调用的样本服务。随后，将 API 打包成产品，将产品发布到目录，然后测试了代理。

---

## 下一步

使用[速率限制](tut_rate_limit.html)、[客户机标识和私钥](tut_secure_landing.html)或[使用 OAuth 2.0 进行保护](tut_secure_oauth_2.html)来保护 API。

创建 > **管理** > 安全 > 社交化 > 分析
