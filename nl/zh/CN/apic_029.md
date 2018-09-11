---

copyright:
  years: 2017-2018
lastupdated: "2018-05-23"

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 新增内容

{{site.data.keyword.apiconnect_full}} 包括以下增强功能：


- **组合件 catch 构造支持新的错误案例**：API 组合件中的 catch 构造支持以下新的错误案例：*BadRequestError*、*UnauthorizedError* 和 *ForbiddenError*。请参阅[组合件 catch 支持的错误案例 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/ref_toolkit_catch_errors.html){:new_window}。
- **向选中的 API 添加了 useBytesSent 查询参数**：添加了 *useBytesSent* 参数，允许使用分析字段 *bytes_sent* 来计算使用情况。请参阅 [Return data usage information for all the resources used by a given application ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps__appID__data-usageGET.html){:new_window}、[Return data usage information for all the resources used by all applications in the given organization ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps_data-usageGET.html){:new_window}、[Return combined data usage for all resources used by a given application ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps__appID__data-usage_allGET.html){:new_window} 和 [Return combined data usage for all the resources used by a given organization ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_data-usage_allGET.html){:new_window} 以获取更多信息。
**您可以编码 Invoke 或 Proxy 策略的目标 URL 的查询参数值中的 + 字符**：提供新的 *x-ibm-gateway-queryparam-encode-plus-char* API 属性；如果将值设置为 *true*，那么 Invoke 和 Proxy 策略的 target-url 的查询参数值中的所有“+”字符将编码为“%2F”。在先前发行版中，+ 总是编码为 %2F。现在，缺省行为是不执行编码。请参阅 [API 属性 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){:new_window}。
- **您可以在 Invoke 或 Proxy 策略的响应规则上实施 JSON 解析器**：提供新的 *x-ibm-gateway-api-enforce-response-limits* API 属性；将此属性设置为值 *true* 可允许在响应规则上实施 JSON 解析器。如果响应主体大小大于 DataPower 域中设置的 JSON 解析器限制，那么将返回状态码 500。请参阅 [API 属性 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){:new_window}。
- **可提高映射策略的性能**：提供新的 *x-ibm-gateway-optimize-schema-definition* API 属性，在策略输出定义引用非常复杂的模式定义时，此属性可针对映射策略提供性能改进。请参阅 [API 属性 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){:new_window}。
