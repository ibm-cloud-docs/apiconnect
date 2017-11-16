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

# 匯入 API 規格並使用 Developer Toolkit 對現有 REST 服務進行 Proxy 處理
持續時間：5 分鐘  
技能水準：初學者  


## 目標
本指導教學說明如何使用 {{site.data.keyword.apiconnect_short}} 對現有 API 進行管理控制。在本指導教學中，您將匯入 OpenAPI 規格，然後為現有 REST 服務建立透通 API Proxy。

## 必要條件
開始之前，您需要[設定 API Connect 實例](tut_prereq_set_up_apic_instance.html)及[安裝 API Connect Toolkit](tut_prereq_install_toolkit.html)。

---


## 探索範例應用程式並測試目標端點

已針對本指導教學建立範例_氣象局_ 應用程式。對應的 API 規格 (Swagger 2.0) 位於 [weather-provider-api_1.0.0.yaml ![外部鏈結圖示](../../../icons/launch-glyph.svg "外部鏈結圖示")](https://raw.githubusercontent.com/ibm-apiconnect/getting-started/master/toolkit/1a-import/weather-provider-api_1.0.0.yaml){:new_window} 檔案中。

1. 若要探索應用程式，請移至 [http://gettingstartedweatherapp.mybluemix.net/ ![外部鏈結圖示](../../../icons/launch-glyph.svg "外部鏈結圖示")](http://gettingstartedweatherapp.mybluemix.net/){:new_window}。  
2. 輸入有效的 5 位數美國郵遞區號，以取得_**現行天氣**_ 及_**今天的預測**_。  
![](images/explore-weatherapp-1.png)

3. 上述範例天氣應用程式是使用可提供天氣資料的 API 所建置。用來取得**現行**天氣資料的端點是 `https:// myweatherprovider<span></span>.mybluemix.net/current?zipcode={zipcode}`。請造訪 [https://myweatherprovider.mybluemix.net/current?zipcode=90210 ![外部鏈結圖示](../../../icons/launch-glyph.svg "外部鏈結圖示")](https://myweatherprovider.mybluemix.net/current?zipcode=90210){:new_window}，以進行測試。  

  ![](images/explore-weatherapp-2.png)

4. 同樣地，用來取得**今天的**預測資料的端點是 `https:// myweatherprovider<span></span>.mybluemix.net/today?zipcode={zipcode}`。請造訪 [https://myweatherprovider.mybluemix.net/today?zipcode=90210 ![外部鏈結圖示](../../../icons/launch-glyph.svg "外部鏈結圖示")](https://myweatherprovider.mybluemix.net/today?zipcode=90210){:new_window}，以進行測試。  

  ![](images/explore-weatherapp-3.png)



---

## 匯入範例應用程式的 OpenAPI 規格以建立 REST API Proxy
1. 啟動 **API Designer**。在終端機視窗中，輸入下列指令：`apic edit`。
2. 使用 IBM ID 登入。
    ![](images/screenshot_apic-edit_login.png)
3. 在 **API Designer** 中，確定已開啟導覽畫面。否則，請按一下 >> 將它開啟。
4. 在導覽畫面中，按一下**草稿**。
5. 移至 **API** 標籤。
6. 在 API 標籤中，按一下**新增**。
7. 從下拉功能表中，按一下**從檔案或 URL 匯入 API**。
   ![](images/toolkit-import-1.png)
8. 具有您要用於本指導教學之天氣 API 的 OpenAPI 2.0 定義。在「匯入 OpenAPI (Swagger)」對話框中，輸入以下 URL：`https://raw.githubusercontent.com/ibm-apiconnect/getting-started/master/toolkit/1a-import/weather-provider-api_1.0.0.yaml`。
9. 保持不勾選_新增產品_ 選項，然後按一下**匯入**。  
    ![](images/screenshot_import-url.png)  

匯入 OpenAPI 規格之後，您會被帶到 API 的「設計」視圖。您可以在這裡檢視 OpenAPI 定義的各個區段。捲動以進行探索，並特別記下「主機」值。您也可以在「來源」標籤下檢視 OpenAPI。
_您會看到「主機」值設為 _ `$(catalog.host)`_。這是 API Proxy 的基本 URL。_
 


## 測試 API Proxy

1. 選取**啟動伺服器**圖示，以啟動本端測試伺服器。啟動「閘道」之後，您會看到狀態自動更新為_**執行中**_。
    ![](images/screenshot_start-server-1.png)

2. 選取**組合**標籤。

3. 按一下播放圖示 (>) 來測試 API Proxy 的目標呼叫。
   _在本指導教學中，我們將使用內嵌的 Micro Gateway，所以請確定已選取 **Micro Gateway 原則**。
    ![](images/screenshot_test-0.png)

4. 在測試畫面中：
  - 選取 **get /current** 作業。  
  - Zipcode 是這項作業的必要參數，因此請輸入有效的美國郵遞區號（例如，90210）。  
  - 選取**呼叫**，並驗證回應。

    _如果您遇到 CORS 錯誤，請遵循錯誤訊息中的指示。按一下錯誤中的鏈結以將異常狀況新增至瀏覽器，然後再按一下**呼叫**。
  
  - 預期的回應是 **200 OK** 回應，以及郵遞區號 90210 的現行天氣資料。
    ![](images/screenshot_test-1.png)    


## 結論

在本指導教學中，您看到如何透過 API 透通 Proxy 來呼叫現有 REST 服務。您是從透過 Web 瀏覽器檢查範例服務可用性開始。然後，您會在 API Connect 中建立 API Proxy，並將此 Proxy 鏈結至要呼叫的範例服務。最後，您已使用 {{site.data.keyword.apiconnect_short}} 內部測試工具測試過此服務。

---

## 下一步

使用[速率限制](tut_rate_limit.html)、[用戶端 ID 及密碼](tut_secure_landing.html)或[使用 OAuth 2.0 保護](tut_secure_oauth_2.html)來保護 API。

建立 > **管理** > 安全 > 社交化 > 分析
