---
copyright:
  years: 2019
lastupdated: "2019-3-9"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 使用 {{site.data.keyword.Bluemix_notm}} 添加 API 规范和调用 REST 服务
{: #tut_add_openapi_rest_bm}

**持续时间**：15 分钟  
**技能级别**：初学者  

## 目标
{: #object_tut_add_openapi_rest_bm}

本教程旨在帮助您快速上手使用 {{site.data.keyword.apiconnect_full}}。您将在几分钟内构建一个新的 API，以充当现有 REST 服务的传递 API 代理。您构建的 API 将提供安全性和监视功能。

## 先决条件
{: #prereq_tut_add_openapi_rest_bm}

开始之前，需要[设置 API Connect 实例](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_set_up_apic_instance)。

---

### 浏览样本应用程序并测试目标端点
{: #expl_tut_add_openapi_rest_bm}

针对本教程创建了样本 _Weather Provider_ 应用程序。
1. 要浏览该应用程序，请转至 [http://gettingstartedweatherapp.mybluemix.net/ ![外部链接图标](../../../icons/launch-glyph.svg "外部链接图标")](http://gettingstartedweatherapp.mybluemix.net/){: #new_window}。  
2. 输入有效的 5 位美国邮政编码，以获取_**当前天气**_和_**今日预测**_。  
![](images/explore-weatherapp-1.png)

3. 以上样本天气应用程序是使用提供天气数据的 API 构建的。用于获取**当前**天气数据的端点为 _**https://myweatherprovider.mybluemix.net/current?zipcode={zipcode}**_。通过访问 [https://myweatherprovider.mybluemix.net/current?zipcode=90210 ![外部链接图标](../../../icons/launch-glyph.svg "外部链接图标")](https://myweatherprovider.mybluemix.net/current?zipcode=90210){: #new_window} 对其进行测试。  

  ![](images/explore-weatherapp-2.png)

4. 与此类似，用于获取**今日**预测数据的端点为 _**https:// myweatherprovider<span></span>.mybluemix.net/today?zipcode={zipcode}**_。通过转至 [https://myweatherprovider.mybluemix.net/today?zipcode=90210 ![外部链接图标](../../../icons/launch-glyph.svg "外部链接图标")](https://myweatherprovider.mybluemix.net/today?zipcode=90210){: #new_window} 对其进行测试。  

  ![](images/explore-weatherapp-3.png)


---

### 添加新的 OpenAPI 规范以创建 REST API 代理  
{: #add_spec_tut_add_openapi_rest_bm}

1. 登录到 {{site.data.keyword.Bluemix_short}}：https://cloud.ibm.com。
2. 在 {{site.data.keyword.Bluemix_notm}} **仪表板**中，单击 **Cloud Foundary 服务**。启动 {{site.data.keyword.apiconnect_short}} 服务。 
3. 在 {{site.data.keyword.apiconnect_short}} 中，确保导航面板已打开。如果未打开，请单击 **>>** 将其打开。  

  ![](images/cloud-apic-dashboard.png)

4. 在导航面板中选择**草稿**。
5. 在 **API** 选项卡中，单击**添加**。从下拉菜单中，选择**新建 API**。    
  ![](images/cloud-add-api-new.png)  
6. 在*新建 API* 窗口中，输入 `New Weather Provider API` 作为标题。_这将自动填充“名称”和“基本路径”_。  
  ![](images/bluemix-add-new-api2.png)
7. 单击**创建 API** 以完成向导。  
8. 创建 API 后，已选择**设计**选项卡。 
9. 滚动到**主机**面板。如果字段未自动填写，请输入 `$(catalog.host)` 作为值。
10. 在**基本路径**面板中，记下自动填充的值：`/new-weather-provider-api`。您的 API 的目标 URL 将基于这些值进行创建。  


11. 现在需要定义在调用天气 API 时返回的响应对象。为此，请单击导航栏中的**定义**。   
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

12. 创建新定义：**Today**。

13. 为 **Today** 定义添加新属性。
    - 名称：zip / 类型：string
    - 名称：hi / 类型：integer
    - 名称：lo / 类型：integer
    - 名称：nightHumidity / 类型：integer
    - 名称：dayHumidity / 类型：integer
    - 名称：city        /  类型：string
    - 名称：state       /  类型：string

14. 定义数据格式后，我们可以创建调用路径。在导航栏中，单击**路径**。通过单击 **+** 来创建新路径。     
    a. 将新路径命名为“**/current**”。  
    b. 在相同的*路径*面板中，选择 **GET /current** 部分。    
    c. 在 **GET /current** 部分中，添加新的**参数**。您在浏览该样本应用程序时会注意到，天气服务需要将 zipcode 作为参数。   
      - 名称：zipcode  
      - 位于：查询  
      - 必需：是  
      - 类型：string   
	  
    ![](images/path-current-1.png)   
	
    d. 向下滚动。在**响应**部分中，将**模式**更改为_当前_。  
	
	![](images/path-current-responses.png)
		e. 保存 API。  

15. 重复步骤 11 中执行的操作以创建名为“**/today**”的另一个路径。在本例中，请将**响应**模式设置为_今天_。保存 API。

16. 保存 API。

17. 切换到**组合**选项卡。目前，您已创建两个操作：**GET /current** 和 **GET /today**。要确保调用正确的目标端点，需要创建一些逻辑，用于对所调用的操作执行条件。下面使用 **Operation Switch** 逻辑构造来执行此操作。**Operation Switch** 将提供决策点。相应的操作需要根据动词/路径对进行调用。

    a. 删除可能已添加到_画布_的 **invoke** 策略。  
    b. 将 **Operation Switch** 从选用板中拖放到画布上。  
      - 对于**用例 0**，分配 **get /current** 操作。
      - 添加新用例：**用例 1**。
      - 将 **get /today** 操作分配给**用例 1**。	  
	  
      ![](images/new-assemble-1.png)
	  
    c. 将 **invoke** 策略从选用板中拖放到处理行的 **get /current** 之下。_invoke 操作用于从操作中调用现有服务_。   
    d. 将操作标题更新为“**invoke-current**”。  
    e. 使用 `https://myweatherprovider.mybluemix.net/current?zipcode=$(request.parameters.zipcode)` 更新 URL 字段。  
	
	![](images/new-assemble-invoke1.png)
		f. 将 **invoke** 策略从选用板中拖放到处理行的 **get /today** 之下。 
    g. 将其标题更新为“**invoke-today**”。  
    h. 使用 `https://myweatherprovider.mybluemix.net/today?zipcode=$(request.parameters.zipcode)` 更新 URL 字段。  
	
       ![](images/new-assemble-invoke2.png)
	   

18. 关闭操作配置面板。保存 API。

---

### 测试 API 代理
{: #test_proxy_tut_add_openapi_rest_bm}

1. 在**组合**选项卡中，单击表示更多操作的图标，然后选择**生成缺省产品**。  
   ![](images/generate-default-product-small.png) 

2. 接受**新建产品**对话框中的缺省选项，然后单击**创建产品**。这将创建 Weather Provider API 产品，并将其发布到“沙箱”目录。此时将显示一条消息，指示产品成功生成。  

  ![](images/generate-default-product-new-weather.png) 

  - _在 {{site.data.keyword.apiconnect_short}} 中，**产品**用于对特定用途的 API 进行分组。产品将发布到**目录**。[{{site.data.keyword.apiconnect_short}} 词汇表](../apic_glossary.html)_

3. 在“组合”选项卡中，单击“播放”图标以测试 API 代理的目标调用。

4. 在“测试”面板中，选择 **get /current** 操作。

	a. Zipcode 是此操作的必需参数，因此请输入有效的美国邮政编码（例如 10504）。 
	
	![](images/test-invoke-params.png)  
		
	b. 单击**调用**。   

	_如果遇到 CORS 错误，请按照错误消息中的指示信息进行操作。单击错误中的链接以将例外添加到浏览器，然后重新点击“调用”按钮。_
  
    ![](images/test-invoke-new.png)  


---

### 结论
{: #conclusion_tut_add_openapi_rest_bm}

在本教程中，您已学习如何通过 API 传递代理来调用现有 REST 服务。首先，通过 Web 浏览器检查了样本服务的可用性。接着，在 {{site.data.keyword.apiconnect_short}} 中创建了新的 OpenAPI 规范，并将其链接到要调用的样本服务。随后，将 API 打包成产品，将产品发布到目录，然后测试了代理。

---

## 下一步
{: #next_tut_add_openapi_rest_bm}

利用[使用 OAuth 2.0 进行保护](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_oauth_2)来保护 API。

创建 > **管理** > 安全 > 社交化 > 分析
