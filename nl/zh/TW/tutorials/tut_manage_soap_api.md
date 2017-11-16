---
copyright:
  years: 2017
lastupdated: "2017-10-19"
---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# 管理 SOAP 服務
**持續時間**：15 分鐘
**技能水準**：初學者

---
## 目標
在本指導教學中，您將使用 API Manager 來建立 SOAP API，以作為 SOAP 型天氣服務的 Proxy。

## 必要條件
- 開始之前，您需要[設定 {{site.data.keyword.apiconnect_short}} 實例](tut_prereq_set_up_apic_instance.html)。
- 開始之前，請將 [weatherprovider.wsdl 測試 ![外部鏈結圖示](../../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/ibm-apiconnect/getting-started/blob/master/bluemix/manage-soap-api/files/weatherprovider.wsdl){:new_window} 檔案複製到本端檔案系統。附註：您可以按一下**原始**，然後將產生的頁面以 `.wsdl` 檔案形式儲存在本端系統上。顧名思義，此 SOAP 服務會在給定郵遞區號時傳回天氣資料。

---
## 設定 SOAP API 定義
1. 登入 {{site.data.keyword.Bluemix_short}}：[https://new-console.ng.bluemix.net/login](https://new-console.ng.bluemix.net/login){:new_window}。

2. 在 {{site.data.keyword.Bluemix_short}} **儀表板**中，向下捲動至**所有服務**。

3. 選取 **API Connect**，以啟動 API Connect 服務。 
  
4. 導覽至「草稿」頁面（如果您尚未處於該處）：  
    a. 在 API Connect 介面中，按一下 >> 以開啟導覽畫面。
    b. 按一下導覽畫面中的**草稿**。
    c. 移至 **API** 標籤。

5. 在 API 標籤中，按一下`新增 +`。

6. 在下拉功能表中，從 SOAP 服務中選取 **API**。
  ![新建 API](images/newapi-menu2.png)

7. 即會開啟「從 WSDL 新建 API 」對話框。按一下**上傳檔案**。
  ![上傳 .wsdl 檔案](images/4-uploadwsdl.png)

8. 選取您先前儲存的 `weatherprovider.wsdl` 檔案。

9. 即會再次出現「從 WSDL 新建 API 」對話框。勾選 **weatherService** 勾選框。按一下**完成**。
  ![選取天氣服務](images/newapi2.png)

10. 成功匯入時，您會被帶到 API 的「設計」視圖。您也可以在「來源」標籤下檢視 OpenAPI 定義。
   _在「來源」標籤中，您會看到 WSDL 包在 OpenAPI 定義內。_
  ![「API 編輯器」頁面](images/designpage2.png)

11. 向下捲動至**安全**標籤，然後按一下刪除圖示，以移除在建立服務時自動產生的 `clientIDHeader（API 金鑰）`。
   _在下一個指導教學中，您將瞭解使用 API 金鑰的安全。_

12. 按一下 ![儲存](images/save.png) 圖示，以儲存變更。隨即會出現「API 已儲存」確認通知。

13. 在具有儲存圖示的功能表列中，**設計**標籤會指出您的呈現位置。接下來，您會找到**來源**標籤，您可以透過此標籤直接檢視代表 API 的 Swagger (2.0) 檔案。再接著，您會找到**組合**標籤，此標籤會帶領您前往拖放介面以進行 API 處理。按一下**組合**。
  ![「組合」標籤](images/assemble-clean.png)  

## 測試 SOAP API 定義

1. 在**組合**標籤中，按一下**其他動作**（三點）圖示，然後從功能表中選取**產生預設產品**。  
   ![「其他動作」功能表、已開啟](images/gen-default-prod.png)

2. 接受**新建產品**對話框蹦現畫面中的預設選項，然後選取**建立產品**。即會建立 **weatherService 產品 1.0.0**，並將其發佈至「沙盤推演」型錄。  
  ![建立新的產品](images/12a-chooseproduct.png)
 
  _在 {{site.data.keyword.apiconnect_short}} 中，**產品**提供一種用來對特定用途的 API 進行分組的機制。產品會發佈至**型錄**。參照：[{{site.data.keyword.apiconnect_short}} 名詞解釋](../apic_glossary.html)_

3. 儲存變更。  

4. 在「搜尋」方框旁，按一下測試圖示，以測試 API 服務。即會出現「設定」功能表。

5. 從「產品」清單中，選擇 `weatherService 產品 1.0.0`。  
  ![選擇天氣服務](images/12-chooseproduct.png)

6. 捲動至底端，然後按**下一步**。

7. 從「作業」清單中，選取 `post /weatherRequest`。  
  ![張貼要求](images/13-selectoperation.png)

8. 向下捲動。在內文欄位中，輸入下列 XML。您可以選取並複製下列範例 XML，然後按一下**內文**欄位來啟動欄位，並放置範例 XML。  
  ```
  <?xml version="1.0" encoding="UTF-8"?>
  <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
  <wdata:WeatherRequest xmlns:wdata="http://www.ibm.com/wdata">
       <zipcode>10504</zipcode>
  </wdata:WeatherRequest>
   </soap:Body>
  </soap:Envelope>
  ```
  {: codeblock}  
  ![要求](images/14-enterrequest.png)

9. 向下捲動（必要的話），然後按一下**呼叫**。
API 會傳回包含現行天氣的「回應**內文**」。  
  ![](images/15-success.png)

## 您在本指導教學中執行的作業
在本指導教學中，您已完成下列作業：
1. 已設定 SOAP API 定義
2. 已測試 API 定義
3. 從天氣 API 端點接收到「回應**內文**」，指出您的要求結果。

---

## 下一步

[將服務公開為 REST API](tut_expose_soap_api.html)，或使用[速率限制](tut_rate_limit.html)、[用戶端 ID 及密碼](tut_secure_landing.html)或[使用 OAuth 2.0 保護](tut_secure_oauth_2.html)來保護 API。

建立 > **管理** > 安全 > 社交化 > 分析
