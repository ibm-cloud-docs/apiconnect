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

# 使用 {{site.data.keyword.Bluemix_notm}} 新增 API 規格及呼叫 REST 服務
{: #tut_add_openapi_rest_bm}

**持續時間**：15 分鐘  
**技能水準**：初學者  

## 目標
{: #object_tut_add_openapi_rest_bm}

本指導教學協助您快速開始使用 {{site.data.keyword.apiconnect_full}}。您將在幾分鐘內建置新的 API，充當現有 REST 服務的透通 API Proxy。您建置的 API 會提供安全及監視。

## 必要條件
{: #prereq_tut_add_openapi_rest_bm}

開始之前，您需要[設定 API Connect 實例](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_set_up_apic_instance)。

---

### 探索範例應用程式並測試目標端點
{: #expl_tut_add_openapi_rest_bm}

已針對本指導教學建立範例_氣象局_ 應用程式。
1. 若要探索應用程式，請移至 [http://gettingstartedweatherapp.mybluemix.net/ ![外部鏈結圖示](../../../icons/launch-glyph.svg "外部鏈結圖示")](http://gettingstartedweatherapp.mybluemix.net/){: #new_window}。  
2. 輸入有效的 5 位數美國郵遞區號，以取得_**現行天氣**_ 及_**今天的預測**_。  
![](images/explore-weatherapp-1.png)

3. 上述範例天氣應用程式是使用可提供天氣資料的 API 所建置。用來取得**現行**天氣資料的端點是 _**https://myweatherprovider.mybluemix.net/current?zipcode={zipcode}**_。請造訪 [https://myweatherprovider.mybluemix.net/current?zipcode=90210 ![外部鏈結圖示](../../../icons/launch-glyph.svg "外部鏈結圖示")](https://myweatherprovider.mybluemix.net/current?zipcode=90210){: #new_window}，以進行測試。  

  ![](images/explore-weatherapp-2.png)

4. 同樣地，用來取得**今天的**預測資料的端點是 _**https:// myweatherprovider<span></span>.mybluemix.net/today?zipcode={zipcode}**_。請造訪 [https://myweatherprovider.mybluemix.net/today?zipcode=90210 ![外部鏈結圖示](../../../icons/launch-glyph.svg "外部鏈結圖示")](https://myweatherprovider.mybluemix.net/today?zipcode=90210){: #new_window}，以進行測試。  

  ![](images/explore-weatherapp-3.png)


---

### 新增 OpenAPI 規格以建立 REST API Proxy  
{: #add_spec_tut_add_openapi_rest_bm}

1. 登入 {{site.data.keyword.Bluemix_short}}：`https://cloud.ibm.com`。
2. 在 {{site.data.keyword.Bluemix_notm}} **儀表板**中，按一下 **Cloud Foundry 服務**。啟動 {{site.data.keyword.apiconnect_short}} 服務。 
3. 在 {{site.data.keyword.apiconnect_short}} 中，確定導覽畫面已開啟。否則，請按一下 **>>** 將它開啟。  

  ![](images/cloud-apic-dashboard.png)

4. 在導覽畫面中，選取**草稿**。
5. 在 **API** 標籤中，按一下**新增**。從下拉功能表中，選取**新建 API**。    
  ![](images/cloud-add-api-new.png)  
6. 在*新建 API* 視窗中，輸入 `New Weather Provider API` 作為標題。_即會自動移入「名稱」及「基礎路徑」欄位資料_。  
  ![](images/bluemix-add-new-api2.png)
7. 按一下**建立 API**，完成精靈。  
8. 建立 API 之後，會選取**設計**標籤。 
9. 捲動至**主機**畫面。如果此欄位未自動填寫，請輸入 `$(catalog.host)` 作為值。
10. 在**基礎路徑**畫面中，記下自動移入的值：`/new-weather-provider-api`。您的 API 目標 URL 將會從這些值建立。  


11. 您現在需要定義在呼叫天氣 API 時傳回的回應物件。要這麼做，請按一下導覽列中的**定義**。   
    a. 新增定義。  
    b. 將新定義命名為 _Current_。  
    c. 將「類型」設為 _Object_。  
    d. 新增 **Current** 定義的新內容。    
       - 名稱：zip         /  類型：string   
       - 名稱：temperature /  類型：integer   
       - 名稱：humidity    /  類型：integer   
       - 名稱：city        /  類型：string   
       - 名稱：state       /  類型：string   
	   
    ![](images/definition-current-1.png)   
	
    e. 儲存 API。  

12. 建立新的定義：**Today**。

13. 新增 **Today** 定義的新內容。
    - 名稱：zip / 類型：string
    - 名稱：hi / 類型：integer
    - 名稱：lo / 類型：integer
    - 名稱：nightHumidity / 類型：integer
    - 名稱：dayHumidity / 類型：integer
    - 名稱：city        /  類型：string
    - 名稱：state       /  類型：string

14. 定義好我們的資料格式之後，我們可以建立呼叫路徑。在導覽列中，按一下**路徑**。按一下 **+** 來建立新路徑。     
    a. 將新路徑命名為 "**/current**"。  
    b. 在相同*路徑* 畫面中，選取 **GET /current** 區段。    
    c. 在 **GET /current** 區段中，新增**參數**。正如您在探索範例應用程式時所注意到的，天氣服務需要使用 zipcode 作為參數。   
      - 名稱：zipcode  
      - 位於：查詢  
      - 必要：是  
      - 類型：string   
	  
    ![](images/path-current-1.png)   
	
    d. 向下捲動。在**回應**區段中，將 **SCHEMA** 變更為 _Current_。  
	
	![](images/path-current-responses.png)
	
	e. 儲存 API。  

15. 重複您在步驟 11 中進行的動作，建立另一個名為 "**/today**" 的路徑。在此情況下，將 **Responses** 綱目設為 _Today_。儲存 API。

16. 儲存 API。

17. 切換至**組合**標籤。您目前已建立兩個作業：**GET /current** 及 **GET /today**。若要確保已呼叫正確的目標端點，您需要建立某些會在所呼叫的作業上執行條件式的邏輯。請使用 **Operation Switch** 邏輯建構來執行這項作業。**Operation Switch** 會提供決策點。根據動詞/路徑配對，需要呼叫適當的作業。

    a. 刪除可能已新增至_畫布_ 的 **invoke** 原則。  
    b. 從選用區中，將 **Operation Switch** 拖曳至畫布上。  
      - 對於**案例 0**，指派 **get /current** 作業。
      - 新增「案例」：**案例 1**。
      - 將 **get /today** 作業指派給**案例 1**。
      
	  
	  
      ![](images/new-assemble-1.png)
	
  
    c. 從選用區中，將 **invoke** 原則拖曳至 **get /current** 底下的處理線。_invoke 動作用來從作業內呼叫現有服務_。   
    d. 將動作標題更新為 "**invoke-current**"。  
    e. 將 URL 欄位更新為 `https://myweatherprovider.mybluemix.net/current?zipcode=$(request.parameters.zipcode)`。  
	
	![](images/new-assemble-invoke1.png)
	
	f. 從選用區中，將 **invoke** 原則拖曳至 **get /today** 底下的處理線。 
    g. 將其標題更新為 "**invoke-today**"。  
    h. 將 URL 欄位更新為 `https://myweatherprovider.mybluemix.net/today?zipcode=$(request.parameters.zipcode)`。  
	
       ![](images/new-assemble-invoke2.png)
	
   

18. 關閉動作配置畫面。儲存 API。

---

### 測試 API Proxy
{: #test_proxy_tut_add_openapi_rest_bm}

1. 在**組合**標籤中，按一下其他動作的圖示，然後選取**產生預設產品**。  
   ![](images/generate-default-product-small.png) 

2. 接受**新建產品**對話框中的預設選項，然後按一下**建立產品**。即會建立 Weather Provider API 產品，並將其發佈至「沙盤推演」型錄。會顯示一則訊息，指出產品產生成功。  

  ![](images/generate-default-product-new-weather.png) 

  - _在 {{site.data.keyword.apiconnect_short}} 中，**產品**提供一種用來對特定用途的 API 進行分組的方式。產品會發佈至**型錄**。[{{site.data.keyword.apiconnect_short}} 名詞解釋](../apic_glossary.html)_

3. 在「組合」標籤中，按一下播放圖示來測試 API Proxy 的目標呼叫。

4. 在測試畫面中，選取 **get /current** 作業。

	a. Zipcode 是這項作業的必要參數，因此請輸入有效的美國郵遞區號（例如：10504）。 
	
	![](images/test-invoke-params.png)  
		
	b. 按一下 **Invoke**。   

	_如果您遇到 CORS 錯誤，請遵循錯誤訊息中的指示。按一下錯誤中的鏈結以將異常狀況新增至瀏覽器，然後再按 invoke 按鈕。_
  
    ![](images/test-invoke-new.png)  


---

### 結論
{: #conclusion_tut_add_openapi_rest_bm}

在本指導教學中，您學習到如何透過 API 透通 Proxy 來呼叫現有 REST 服務。您是從透過 Web 瀏覽器檢查範例服務可用性開始。然後，您會在 {{site.data.keyword.apiconnect_short}} 中建立新的 OpenAPI 規格，並將它鏈結至要呼叫的範例服務。您已將 API 包裝成產品、已將產品發佈至型錄，並且已測試 Proxy。

---

## 下一步
{: #next_tut_add_openapi_rest_bm}

利用[使用 OAuth 2.0 進行保護](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_oauth_2)來保護您的 API。

建立 > **管理** > 安全 > 社交化 > 分析
