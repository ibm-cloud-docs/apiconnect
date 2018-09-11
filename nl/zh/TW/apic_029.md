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

# 新增功能

{{site.data.keyword.apiconnect_full}} 包括下列加強功能：


- **組件 catch 結構支援新的錯誤案例**：API 組件中的 catch 結構支援下列新的錯誤案例：*BadRequestError*、*UnauthorizedError* 及 *ForbiddenError*。請參閱 [Error cases supported by assembly catches ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/ref_toolkit_catch_errors.html){:new_window}。
- **已新增 useBytesSent 查詢參數至選取的 API**：已新增 *useBytesSent* 參數，它允許使用分析欄位 *bytes_sent* 來計算用量。如需相關資訊，請參閱 [Return data usage information for all the resources used by a given application ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps__appID__data-usageGET.html){:new_window}、[Return data usage information for all the resources used by all applications in the given organization ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps_data-usageGET.html){:new_window}、[Return combined data usage for all resources used by a given application ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps__appID__data-usage_allGET.html){:new_window} 及 [Return combined data usage for all the resources used by a given organization ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_data-usage_allGET.html){:new_window}。
- **您可以將呼叫或 Proxy 原則之目標 URL 查詢參數值裡的 + 字元編碼**：有一個新的 *x-ibm-gateway-queryparam-encode-plus-char* API 內容；如果設為 *true* 值，呼叫及 Proxy 原則之 target-url 查詢參數值裡的所有 "+" 字元都會編碼為 "%2F"。在舊版中，+ 一律編碼為 %2F。現在，預設行為是不執行編碼。請參閱 [API properties ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){:new_window}。
- **您可以對呼叫或 Proxy 原則的回應規則施行 JSON 剖析器**：有一個新的 *x-ibm-gateway-api-enforce-response-limits* API 內容；將此內容設為 *true* 值，會允許對回應規則施行 JSON 剖析器。如果回應內文大小高於 DataPower 領域中設定的 JSON 剖析器限制，會傳回狀態碼 500。請參閱 [API properties ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){:new_window}。
- **可能改善對映原則的效能**：有一個新的 *x-ibm-gateway-optimize-schema-definition* API 內容，當原則輸出定義參照了非常複雜的綱目定義時，可以提供對映原則的效能改善。請參閱 [API properties ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){:new_window}。
