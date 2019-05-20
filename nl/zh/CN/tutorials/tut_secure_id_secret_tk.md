---

copyright:
  years: 2017
lastupdated: "2017-10-31"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorials

subcollection: apiconnect

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 通过开发者工具箱使用客户机标识和客户机私钥保护 API
{: #tut_secure_id_secret_tk}

**持续时间**：10 分钟  
**技能级别**：初学者


## 目标
{: #object_tut_secure_id_secret_tk}

本教程将指导您逐步完成使用客户机标识和客户机私钥来保护 API 的过程。在开发者门户网站中注册应用程序时，会生成客户机标识以标识应用程序。（可选）还可以生成用作密码的客户机私钥。应用程序需要提供生成的客户机标识和客户机私钥才能访问 API。


## 先决条件
{: #prereq_tut_secure_id_secret_tk}

开始之前，必须已完成以下其中一个教程：
- [导入 OpenAPI2.0 规范并代理现有 REST 服务](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_rest_landing)**或**  
- [添加新的 API 规范并调用现有 REST 服务](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_rest_landing)


## 设置 API 的标识机制
{: #set_id_tut_secure_id_secret_tk}

1. 启动 API Designer（如果尚未打开）：  
   a. 打开终端。  
   b. 在命令行中输入 `apic edit`。_这将在 Web 浏览器中启动 API Designer_。    
   c. 单击**使用 {{site.data.keyword.Bluemix_notm}} 登录**。  
   d. 输入您的 {{site.data.keyword.Bluemix_short}} 登录信息。  

2. 导航至 API 的“设计”视图：
    a. 单击左侧导航面板中的**草稿** 
    b. 然后单击 **API** 选项卡
    c. 单击在先前教程中创建的 _Weather Provider API_。这将打开 API 的**设计**视图。  
    ![](images/1_goto_drafts_api.png)  

3. 在“设计”视图中：  
   a. 向下滚动到**安全性定义**。  
    ![](images/1b.png) 

   b. 单击**添加安全性定义**图标 (+)，然后单击 **API 密钥**。  
      - 名称：客户机标识；参数名称：X-IBM-Client-ID  
      - 名称：客户机私钥；参数名称：X-IBM-Client-Secret  
      - 对于这两个新密钥，请确保**位于**字段设置为“头”。  
      ![](images/2a.png)    

4. 向下滚动到**安全性**面板，然后添加新的安全性选项。  
   a. 选择新创建的“客户机标识”和“客户机私钥”。  
   b. 保存 API。  
   c. 切换到**组合**选项卡。  
    ![](images/3a.png) 

## 测试对 API 所做的更改
{: #test_tut_secure_id_secret_tk}

1. 在“组合”选项卡中，单击 ► 以测试更改。
2. 在“测试”面板中，单击 **get /current** 操作。
3. 在“测试”面板中向下滚动，并注意“客户机标识”和“客户机私钥”值是否已填充。_这些是针对沙箱生成的测试值，表示将使用 API 的应用程序的密钥。_  
> 注：还可以在**仪表板** > **目录** > **设置** > **端点**下找到这些“客户机标识”和“客户机私钥”。  

 ![](images/test_api_keys_1.png)

4. 进一步向下滚动并输入邮政编码（例如 90210）。 
5. 然后，单击**调用**。_您应该会获得 200 OK 响应，以及返回天气信息的消息体。_  
6. 向上滚动回“客户机标识”字段，将“客户机标识”值替换为随机值（以查看传递不正确的“客户机标识”时的行为）。  
7. 通过单击**调用**来重新运行测试。_您将看到 401 Unauthorized 响应以及“客户机标识未注册”消息。_  
  ![](images/test_api_keys_3.png)  
  

## 使用客户机标识和客户机私钥调用 API
{: #call_tut_secure_id_secret_tk}

还可以使用显式调用代理端点的浏览工具来测试安全设置，并将“客户机标识”和“客户机私钥”作为头值传递。


1. 单击**浏览**。
    ![](images/explore_1.png)

2. 单击列表中的 **GET /current** 操作。  

3. 在右侧列中，单击**调用操作**以重新运行测试。  
    ![](images/4.png)  
    
---

### 结论
{: #conclusion_tut_secure_id_secret_tk}

在本教程中，您已学习如何设置 API 的标识机制，测试对 API 所做的更改，并使用客户机标识和客户机私钥调用了 API。 

---

## 下一步
{: #next_tut_secure_id_secret_tk}

通过[设置和配置开发者门户网站](tut_config_dev_portal.html)，开始对 API 社交化。

创建 > 管理 > **安全** > 社交化 > 分析
