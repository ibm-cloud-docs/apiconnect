---

copyright:
  years: 2017
lastupdated: "2017-11-02"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 使用开发者工具箱添加新的 API 规范并调用现有 REST 服务
{: #tut_add_openapi_rest_tk}

**持续时间**：15 分钟  
**技能级别**：初学者  

## 目标
{: #object_tut_add_openapi_rest_tk}

本教程通过说明如何将现有 API 纳入管理控制，帮助您快速上手使用 {{site.data.keyword.apiconnect_full}}。首先将创建新的 OpenAPI 规范，然后为现有 REST 服务创建传递 API 代理。

## 先决条件
{: #prereq_tut_add_openapi_rest_tk}

开始之前，需要[设置 API Connect 实例](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_set_up_apic_instance)和[安装 API Connect 工具箱](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_install_toolkit)。

---


## 浏览样本应用程序并测试目标端点
{: #expl_test_tut_add_openapi_rest_tk}

针对本教程创建了样本 _Weather Provider_ 应用程序。
1. 要浏览该应用程序，请转至 [http://gettingstartedweatherapp.mybluemix.net/ ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://gettingstartedweatherapp.mybluemix.net/){: #new_window}。  
2. 输入有效的 5 位美国邮政编码，以获取_**当前天气**_和_**今日预测**_。  
![](images/explore-weatherapp-1.png)

3. 以上样本天气应用程序是使用提供天气数据的 API 构建的。用于获取**当前**天气数据的端点为 _**https:// myweatherprovider<span></span>.mybluemix.net/current?zipcode={zipcode}**_。通过访问 [https://myweatherprovider.mybluemix.net/current?zipcode=90210](https://myweatherprovider.mybluemix.net/current?zipcode=90210){: #new_window} 对其进行测试。  

  ![](images/explore-weatherapp-2.png)

4. 与此类似，用于获取**今日**预测数据的端点为 `https:// myweatherprovider<span></span>.mybluemix.net/today?zipcode={zipcode}`。通过转至 [https://myweatherprovider.mybluemix.net/today?zipcode=90210](https://myweatherprovider.mybluemix.net/today?zipcode=90210){: #new_window} 对其进行测试。  

  ![](images/explore-weatherapp-3.png)

---

## 添加新的 OpenAPI 规范并调用现有 REST 服务
{: #add_spec_tut_add_openapi_rest_tk}

1. 启动 **API Designer**。在终端中，输入 `apic edit`。
2. 使用您的 IBM 标识登录。![](images/screenshot_apic-edit_login.png)
3.   在 API Designer 中，确保导航面板已打开。如果未打开，请单击 >> 将其打开。在 **API Designer** 导航面板中，选择**草稿 > API**。
4. 在 **API** 面板中，选择**添加 > 新建 API**。
5. 在“新建 API”窗口中，输入“Weather Provider API”作为标题。_这将自动填充“名称”和“基本路径”_。  
  ![](images/toolkit-add-new-api.png)   
6. 单击**创建 API** 以完成向导。  

7. 创建 API 后，已选择**设计**选项卡。

8. 滚动到**主机**面板。如果字段未自动填写，请输入 `$(catalog.host)` 作为值。

9. 滚动到**安全性**选项卡，然后删除已自动生成的“clientIDHeader (API Key)”。  
_（我们将在下一个教程的“API 密钥”中探讨安全性。）_  

10. 在**路径**面板中，通过单击 **+** 来创建新路径。
  a. 将新路径命名为“**/current**”。  
  b. 在相同的**路径**面板中，选择 **GET /current** 部分。  
  c. 在 **GET /current** 部分中，添加新的**参数**。您在浏览该样本应用程序时会注意到，天气服务需要将 zipcode 作为参数。
      - 名称：zipcode  
      - 位于：查询  
      - 必需：是  
      - 类型：string  
    ![](images/path-current-1.png)
  d. 保存 API。

11. 通过上一步中定义的查询参数，现在需要定义在调用天气 API 时返回的响应对象。为此，请向下滚动到**定义**面板。

  1. 添加新定义。 
  2. 将新定义命名为 _Current_。
  3. 将“类型”设置为 _Object_。
  4. 为 **Current** 定义添加新属性。
    - 名称：zip         /  类型：string
    - 名称：temperature /  类型：integer
    - 名称：humidity    /  类型：integer
    - 名称：city        /  类型：string
    - 名称：state       /  类型：string ![](images/definition-current-1.png)
  5. 保存 API。  

12. 在上一步中，已定义响应对象。接下来，需要确保响应对象与 **get /current** 路径相关联。在导航中，向上滚动回**路径**面板。
  a. 打开 **GET /current** 操作，并滚动到**响应**部分。
  b. 将 200 OK 响应的模式从“object”更改为“**Current**”。
  c. 保存 API。

13. 刚才创建的路径和操作用于获取当前天气数据。现在，需要创建类似的路径和操作来获取今日天气数据。通过步骤 11 中创建 **/current** 路径的类似方式，创建新路径：**/today**。 

14. 在 **GET /today** 操作下添加新参数。
    - 参数名称：zipcode  
    - 位于：查询  
    - 必需：是  
    - 类型：string  

15. 创建新定义：**Today**。

16. 为 **Today** 定义添加新属性。
  - 名称：zip / 类型：string
  - 名称：hi / 类型：integer
  - 名称：lo / 类型：integer
  - 名称：nightHumidity / 类型：integer
  - 名称：dayHumidity / 类型：integer
  - 名称：city / 类型：string
  - 名称：state / 类型：string

17. 将 **GET /today** 部分中的响应模式更新为“Today”。

18. 保存 API。

19. 切换到**组合**选项卡。目前，您已创建两个操作：**GET /current** 和 **GET /today**。要确保调用正确的目标端点，需要创建一些逻辑，用于对所调用的操作执行条件。下面使用 **Operation Switch** 逻辑构造来执行此操作。  

    a. 删除可能已添加到_画布_的 **invoke** 策略。  
    b. 将 **Operation Switch** 从_选用板_中拖放到画布上。  
      - 对于**用例 0**，分配 **get /current** 操作。
      - 添加新用例：**用例 1**。
      - 将 **get /today** 操作分配给**用例 1**。![](images/assemble-1.png)**Operation Switch** 将提供决策点。相应的操作必须根据动词/路径对进行调用。  
    c. 将 **invoke** 策略从选用板中拖放到画布上。在 **/get current** 路径和 **/get today** 路径中分别放入一个。
    d. 在 **/get current** 路径中选择 **invoke** 策略，并将其标题更新为“**invoke-current**”。  
    e. 使用 `https://myweatherprovider.mybluemix.net/current?zipcode=$(request.parameters.zipcode)` 更新 URL 字段。
    f. 在 **/get today** 路径中选择 **invoke** 策略，并将其标题更新为“**invoke-today**”。  
    g. 使用 `https://myweatherprovider.mybluemix.net/today?zipcode=$(request.parameters.zipcode)` 更新 URL 字段。  

20. 保存 API。

---

## 测试 API 代理
{: #test_tut_add_openapi_rest_tk}

### 使用 _API Manager 测试工具_进行测试
{: #test_apimgr_tut_add_openapi_rest_tk}

1. 通过单击 Designer 左下方的“启动服务器”图标 (>) 来启动本地测试服务器。网关启动后，将看到状态自动更新为“正在运行”。

    ![](images/screenshot_start-server-1.png)

2. 在**组合**选项卡中，单击“播放”图标 (>) 以测试 API 代理的目标调用。_对于本教程，我们将使用嵌入式 Micro Gateway，因此请确保选中“Micro Gateway 策略”。_

    ![](images/screenshot_test-0.png)

3. 在“测试”面板中，选择 **get /current** 操作。  
  a. Zipcode 是此操作的必需参数，因此请输入有效的美国邮政编码（例如 90210）。  
  b. 单击**调用**，并验证是否看到以下内容：
  ```
  200 OK response
  Current weather data for 90210  
  ```
    ![](images/screenshot_test-2.png)  

_如果遇到 CORS 错误，请按照错误消息中的指示信息进行操作。单击错误中的链接以将例外添加到浏览器，然后重新点击“调用”按钮。_

### 使用_浏览工具_进行测试
{: #test_explore_tut_add_openapi_rest_tk}

1. 要测试 API 代理端点，请选择_浏览_。
2. 从选用板中选择 **GET /current** 操作。
3. 在测试框中输入有效的美国邮政编码（例如 90210）。
4. 单击**调用操作**以查看响应。  
  ![](images/screenshot_explore.png)  
  
---

## 结论
{: #conclusion_tut_add_openapi_rest_tk}

在本教程中，您了解了如何通过 API 传递代理来调用现有 REST 服务。首先，通过 Web 浏览器检查了样本服务的可用性。接着，在 {{site.data.keyword.apiconnect_short}} 中创建了新的 OpenAPI 规范，并将其链接到要调用的样本服务。最后，使用内置测试工具对 API 代理进行了测试。

---

## 下一步
{: #next_tut_add_openapi_rest_tk}

使用[速率限制](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_rate_limit)、[客户机标识和私钥](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_landing)或[使用 OAuth 2.0 进行保护](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_oauth_2)来保护 API。

创建 > **管理** > 安全 > 社交化 > 分析

