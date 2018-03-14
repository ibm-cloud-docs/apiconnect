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

# 新增功能

{{site.data.keyword.apiconnect_full}} 包括下列加強功能：

- **刪除「開發人員入口網站」中的刪除使用者帳戶及「開發者」組織**：您可以刪除「開發人員入口網站」中您的使用者帳戶及「開發者」組織。您也可以變更您的「開發者」組織的所有權。如需相關資訊，請參閱[刪除您的開發人員帳戶 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapic_portal_delete_account.html){:new_window}、[刪除開發人員組織 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapic_portal_delete_dev_org.html){:new_window}，以及[變更開發人員組織的所有權 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapic_portal_dev_org_ownership.dita){:new_window}。

- __新增 *endpoint_url* API 事件欄位__：*endpoint_url* 事件記錄欄位識別 Proxy 或者對要求失敗的項目呼叫目標 URL。如需相關資訊，請參閱[刪除您的開發人員帳戶 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/rapim_analytics_apieventrecordfields.html){:new_window}。</dd>

- **新增了「開發人員入口網站 REST API」支援及參照來進行分析**：「開發人員入口網站 REST API」可協助您分析型錄 API。如需相關資訊，請參閱[分析 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/analytics.html){:new_window}。

- **在建立 API 時新增了「分析」區段**：您可以定義及指定 API 的現有「參數」，這些參數可用來收集 API 的分析資料。如需相關資訊，請參閱[組合 REST API 定義 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html){:new_window}。

- **支持在「開發人員入口網站」中使用雙因子鑑別**：您可以套用「TFA 規則」模組，支持「開發人員入口網站」使用者對其帳戶設定雙因子鑑別 (TFA)。如需相關資訊，請參閱[支持使用者對其開發人員入口網站帳戶設定雙因子鑑別 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapim_portal_two_factor_auth_enforce.html){:new_window}。

- **已新增至整合式計費及付款管理的特性**：管理者：
	* 建立 API 客戶可使用信用卡訂閱的每月預付計費訂閱方案。如需相關資訊，請參閱[產品使用計費 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/capim_product_billing.html){:new_window}。
	* 運用「分段」帳戶來管理訂閱的付款。
	* 指定新訂閱者的訂閱方案的免費試用天數。在試用日到期之後，會自動開始付款。
	客戶：
	* 在「開發人員入口網站」中訂閱付費型方案，容許您使用包含一個以上 API 的產品。如需相關資訊，請參閱[指導教學：訂閱含定價的方案 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tutorial_portal_sub_paid_plan.html){:new_window}。

- **閘道中自動取代的呼叫**：Proxy 可能會取代原則中的最後一次呼叫。這由閘道自動完成，可改善效能。如需相關資訊，請參閱：[API 內容 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){:new_window}。

- **協力廠商回應可以修改 OAuth 範圍**：您可以配置外部伺服器來置換 API 範圍值。如需相關資訊，請參閱：[範圍 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/con_oauth_scope.html){:new_window}。

- **新的 API 事件欄位**：已新增下列 API 事件欄位：
    * billing.trial_period_days
	* billing.amount
	* billing.currency
	* billing.model
	* billing.provider
	* client_id
	* immediate_client_ip
	* latency_info2.task
	* latency_info2.ended

如需相關資訊，請參閱 [API 事件記錄欄位 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/rapim_analytics_apieventrecordfields.html){:new_window} 及[使用 REST API 呼叫取得分析資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/tapim_exportanalytics_api_calls.html){:new_window}。

- **重新導向 URL 的新查詢參數**：新的查詢參數已新增至可供協力廠商使用的資訊。新參數是 <code>provider</code>、<code>providerid</code> 及
<code>g-transid</code>。如需相關資訊，請參閱[透過重新導向 URL 進行鑑別及授權 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_redirect_form_.html){:new_window}。

- **避免測試工具中的瀏覽器 CORS 警示**：API Designer 測試工具會從瀏覽器傳送可觸發 CORS 警示的要求。為了避免 CORS 警示，提供**啟用 Proxy** 勾選框，以從管理 API Designer 的伺服器（而非瀏覽器）傳送測試訊息。如需相關資訊，請參閱[使用 API Designer 測試工具測試 API ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_toolkit_testing.html){:new_window}。

- **使用協力廠商 OAuth 保護 API，而非 Mobile First Foundation**：使用協力廠商 OAuth 提供者保護 API，而非 IBM MobileFirst&tm; Platform Foundation 授權伺服器。如需相關資訊，請參閱[整合協力廠商 OAuth 提供者 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/con_oauth_introspection.html){:new_window}。

- **利用 OpenID Connect (OIDC) 保護 API**：您可以使用依據 OIDC 配置自訂的預先提供範例「OAuth 提供者 API」，利用 OpenID Connect(OIDC) 來保護 API。如需相關資訊，請參閱[利用 OpenID Connect 保護 API ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/tapic_sec_api_config_oidc.html){:new_window}。

- **SOAP 更新動作不再改寫 API**：從 WSDL 定義更新 SOAP API 時，只會取代那些受新 WSDL 影響的 API 區段，其他區段不會變更。在舊版中，更新動作會完全改寫 SOAP API 定義的配置，包括所有設計內容及組合配置。如需相關資訊，請參閱[更新 SOAP API ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/tapic_soap_update.html){:new_window}。

- **在「開發人員入口網站」中使用 Honeypot 進行垃圾郵件保護**：Honeypot 保護提供安全機制，防止「開發人員入口網站」收到 spambot 程式的表單提交。如果偵測到 spambot 程式活動，則會封鎖表單提交。如需相關資訊，請參閱[使用 Honeypot 進行垃圾郵件保護 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapic_portal_honeypot.html){:new_window}。

- **在「開發人員入口網站」中使用「視圖」模組**：使用「視圖使用者介面」模組，在「開發人員入口網站」中建立新視圖（例如產品、API 及應用程式的內容清單）。如需相關資訊，請參閱[在「開發人員入口網站」中使用「視圖」模組 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/capic_portal_views.html){:new_window}。
