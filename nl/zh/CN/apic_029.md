---

copyright:
  years: 2017
lastupdated: "2018-02-12"

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 新增内容

{{site.data.keyword.apiconnect_full}} 包括以下增强功能：

- **删除开发者门户网站中的用户帐户和开发者组织**：您可以删除开发者门户网站中您的用户帐户和开发者组织。还可以更改开发者组织的所有权。有关更多信息，请参阅[删除您的开发者帐户 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapic_portal_delete_account.html){:new_window}、[删除开发者组织 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapic_portal_delete_dev_org.html){:new_window} 和[更改开发者组织的所有权 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapic_portal_dev_org_ownership.dita){:new_window}。

- __添加了 *endpoint_url* API 事件字段__：*endpoint_url* 事件记录字段标识请求在其上失败的代理或调用目标
URL。有关更多信息，请参阅[删除您的开发者帐户 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/rapim_analytics_apieventrecordfields.html){:new_window}。</dd>

- **添加了针对分析用开发者门户网站 REST API 的支持和参考**：开发者门户网站 REST API 可帮助您分析目录 API。有关更多信息，请参阅[分析 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/analytics.html){:new_window}。

- **添加了创建 API 时的“分析”部分**：可以定义和指定可用于收集 API 相关分析数据的 API 的现有参数。有关更多信息，请参阅[编写 REST API 定义 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html){:new_window}。

- **鼓励在开发者门户网站中使用双因子认证**：可以通过应用“双因子认证 (TFA) 规则”模块，鼓励开发者门户网站用户在其帐户上设置 TFA。有关更多信息，请参阅[鼓励用户在其开发者门户网站帐户上设置双因子认证 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapim_portal_two_factor_auth_enforce.html){:new_window}。

- **添加到集成帐单和支付管理的功能**：管理员：
	* 创建每月预付帐单预订套餐，API 客户可以使用信用卡来预订这些套餐。有关更多信息，请参阅[产品使用计费 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/capim_product_billing.html){:new_window}。
	* 利用 Stripe 帐户来管理预订支付。
	* 为新订户指定预订套餐中的免费试用天数。在试用天数到期后，会自动开始支付。客户：
	* 在开发者门户网站中预订允许您使用包含一个或多个 API 的产品的付费套餐。有关更多信息，请参阅[教程：预订带有价格的套餐 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tutorial_portal_sub_paid_plan.html){:new_window}。

- **在网关中自动替换调用**：策略中的最后一个调用可能会替换为代理。网关会自动完成此操作以提高性能。有关更多信息，请参阅：[API 属性 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){:new_window}。

- **OAuth 作用域可以由第三方响应进行修改**：可以配置外部服务器来覆盖 API 作用域值。有关更多信息，请参阅：[作用域 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/con_oauth_scope.html){:new_window}。

- **新增 API 事件字段**：添加了以下 API 事件字段：
    * billing.trial_period_days
	* billing.amount
	* billing.currency
	* billing.model
	* billing.provider
	* client_id
	* immediate_client_ip
	* latency_info2.task
	* latency_info2.ended

有关更多信息，请参阅 [API 事件记录字段 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/rapim_analytics_apieventrecordfields.html){:new_window} 和[使用 REST API 调用来获取分析数据 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/tapim_exportanalytics_api_calls.html){:new_window}。

- **新增重定向 URL 的查询参数**：向可供第三方使用的信息中添加了新的查询参数。新参数为 <code>provider</code>、<code>providerid</code> 和 
<code>g-transid</code>。有关更多信息，请参阅[通过重定向 URL 进行认证和授权 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_redirect_form_.html){:new_window}.

- **阻止测试工具中的浏览器 CORS 警报**：API Designer 测试工具会通过浏览器发送请求，这可能触发 CORS 警报。为了阻止 CORS 警报，提供了**启用代理**复选框，用于通过托管 API Designer 的服务器而不是通过浏览器来发送测试消息。有关更多信息，请参阅[使用 API Designer 测试工具测试 API ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_toolkit_testing.html){:new_window}。

- **使用第三方 OAuth（而不是 Mobile First Foundation）保护 API**：使用第三方 OAuth 提供者（而不是 IBM MobileFirst&tm; Platform Foundation 授权服务器）来保护 API。有关更多信息，请参阅[集成第三方 OAuth 提供者 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/con_oauth_introspection.html){:new_window}。

- **使用 OpenID Connect (OIDC) 保护 API**：可以使用根据 OIDC 配置定制的预先提供的样本 OAuth Provider API，通过 OpenID Connect (OIDC) 来保护 API。有关更多信息，请参阅[使用 OpenID Connect 保护 API ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/tapic_sec_api_config_oidc.html){:new_window}。

- **SOAP 更新操作不再覆盖 API**：通过 WSDL 定义更新 SOAP API 时，仅替换 API 中受新 WSDL 影响的那些部分，其他部分保持不变。在前发行版中，更新操作会完全覆盖 SOAP API 定义的配置，包括所有设计属性和组合配置。有关更多信息，请参阅[更新 SOAP API ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/tapic_soap_update.html){:new_window}。

- **在开发者门户网站中使用蜜罐技术阻止垃圾邮件**：蜜罐技术防御提供了多种安全性机制来保护开发者门户网站站点，避免接收垃圾邮件机器人提交的表单。如果检测到垃圾邮件机器人活动，将阻止表单提交。有关更多信息，请参阅[使用蜜罐技术阻止垃圾邮件 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapic_portal_honeypot.html){:new_window}。

- **使用开发者门户网站中的“视图”模块**：在开发者门户网站中，使用“视图”UI 模块来创建新视图，如产品、API 和应用程序的内容列表。有关更多信息，请参阅[使用开发者门户网站中的“视图”模块 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/capic_portal_views.html){:new_window}。
