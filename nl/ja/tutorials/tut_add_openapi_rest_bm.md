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

# API 仕様を追加して {{site.data.keyword.Bluemix_notm}} で REST サービスを呼び出します。
{: #tut_add_openapi_rest_bm}

**所要時間**: 15 分  
**スキル・レベル**: ビギナー  

## 目標
{: #object_tut_add_openapi_rest_bm}

このチュートリアルは、{{site.data.keyword.apiconnect_full}} での作業を簡単に開始するための方法を取り上げます。 既存の REST サービスのパススルー API プロキシーとして動作する新しい API を数分で構築します。構築する API にはセキュリティーとモニタリングの機能を含めます。

## 前提条件
{: #prereq_tut_add_openapi_rest_bm}

始める前に、[API Connect インスタンスのセットアップ](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_set_up_apic_instance)が必要です。

---

### サンプル・アプリケーションの探索とターゲット・エンドポイントのテスト
{: #expl_tut_add_openapi_rest_bm}

このチュートリアルで使用する _Weather Provider_ サンプル・アプリケーションは、作成されています。
1. アプリケーションを探索するために、[http://gettingstartedweatherapp.mybluemix.net/ ![外部リンクのアイコン](../../../icons/launch-glyph.svg "外部リンクのアイコン")](http://gettingstartedweatherapp.mybluemix.net/){: #new_window} に移動します。  
2. アメリカの有効な 5 桁の郵便番号を入力して、_**現在の天候**_ と_**今日の予報**_ を入手します。  
![](images/explore-weatherapp-1.png)

3. 上の天候サンプル・アプリケーションは、天候データを提供する API を使用して作成されています。 **現在の**天候データを取得するエンドポイントは、_**https://myweatherprovider.mybluemix.net/current?zipcode={zipcode}**_ です。 [https://myweatherprovider.mybluemix.net/current?zipcode=90210 ![外部リンクのアイコン](../../../icons/launch-glyph.svg "外部リンクのアイコン")](https://myweatherprovider.mybluemix.net/current?zipcode=90210){: #new_window} にアクセスして、テストしてください。  

  ![](images/explore-weatherapp-2.png)

4. また、**今日の**予報データを取得するエンドポイントは、_**https:// myweatherprovider<span></span>.mybluemix.net/today?zipcode={zipcode}**_ です。 [https://myweatherprovider.mybluemix.net/today?zipcode=90210 ![外部リンクのアイコン](../../../icons/launch-glyph.svg "外部リンクのアイコン")](https://myweatherprovider.mybluemix.net/today?zipcode=90210){: #new_window} にアクセスして、テストしてください。  

  ![](images/explore-weatherapp-3.png)


---

### REST API プロキシーを作成するための新規 OpenAPI 仕様の追加  
{: #add_spec_tut_add_openapi_rest_bm}

1. {{site.data.keyword.Bluemix_short}} (https://cloud.ibm.com) にログインします。
2. {{site.data.keyword.Bluemix_notm}} の**ダッシュボード**で、**「Cloud Foundary サービス (Cloud Foundary Services)」**をクリックします。{{site.data.keyword.apiconnect_short}} サービスを起動します。 
3. {{site.data.keyword.apiconnect_short}} でナビゲーション・パネルが開いていることを確認します。 表示されていない場合は、**「>>」**をクリックして開きます。  

  ![](images/cloud-apic-dashboard.png)

4. ナビゲーション・パネルで**「ドラフト」** を選択します。
5. **「API」**タブで**「追加」**をクリックします。 ドロップダウン・メニューで、**「新規 API」**を選択します。    
  ![](images/cloud-add-api-new.png)  
6. *「新規 API」*ウィンドウで、タイトルに `New Weather Provider API` と入力します。
_「名前」と「基本パス」は、自動的に入力されます_。  
  ![](images/bluemix-add-new-api2.png)
7. **「API の作成」**をクリックしてウィザードを完了します。  
8. API を作成すると、**「設計」**タブが選択されます。 
9. **「ホスト」**パネルまでスクロールします。 フィールドに値が自動的に取り込まれていない場合は、`$(catalog.host)` を入力します。
10. **「基本パス」**パネルで、自動的に設定された値である `/new-weather-provider-api` を確認します。これらの値から API のターゲット URL が作成されます。  


11. 気象 API を呼び出す際に返される応答オブジェクトを定義する必要があります。そのためには、ナビゲーション・バーの**「定義」**をクリックします。   
    a. 新規定義を追加します。  
    b. 新規定義に _Current_ と名前を付けます。  
    c. 「タイプ」を_「オブジェクト」_に設定します。  
    d. 定義 **Current** に新しいプロパティーを追加します。    
       - 名前: zip         /  タイプ: ストリング   
       - 名前: temperature /  タイプ: 整数   
       - 名前: humidity    /  タイプ: 整数   
       - 名前: city        /  タイプ: ストリング   
       - 名前: state       /  タイプ: ストリング   
	   
    ![](images/definition-current-1.png)   
	
    e. API を保存します。  

12. 新規定義の **Today** を作成します。

13. 定義 **Today** に新しいプロパティーを追加します。
    - 名前: zip / タイプ: ストリング
    - 名前: hi / タイプ: 整数
    - 名前: lo / タイプ: 整数
    - 名前: nightHumidity / タイプ: 整数
    - 名前: dayHumidity / タイプ: 整数
    - 名前: city        /  タイプ: ストリング
    - 名前: state       /  タイプ: ストリング

14. 定義したデータ・フォーマットを使用して、呼び出しパスを作成できます。ナビゲーション・バーで**「パス」**をクリックします。**+** をクリックして、新しいパスを作成します。     
    a. 新しいパスに「**/current**」と名前を付けます。  
    b. 同じ*「パス」*パネルで **GET /current** セクションを選択します。    
    c. **GET /current** セクションで、新しい**「パラメーター」**を追加します。 サンプル・アプリケーションを探索しているときに気付かれたと思いますが、気象情報サービスではパラメーターとして郵便番号が必要です。   
      - 名前: zipcode  
      - 場所: 照会  
      - 必須：はい  
      - タイプ: ストリング   
	  
    ![](images/path-current-1.png)   
	
    d. スクロールダウンします。  **「応答」**セクションで、**「スキーマ」**を_「Current」_に変更します。  
	
	![](images/path-current-responses.png)
	
	e. API を保存します。  

15. ステップ 11 で実行したアクションを繰り返して「**/today**」という名前の別のパスを作成します。この場合、**「応答」**スキーマを「_Today_」に設定します。API を保存します。

16. API を保存します。

17. **「アセンブル」**タブに切り替えます。 ここまでで、**GET /current** と **GET /today** という 2 つの操作を作成しました。 正しいターゲット・エンドポイントが呼び出されるように、呼び出し対象の操作に対して条件を実行するためのロジックを作成する必要があります。 これを行うために、**「操作切り替え」**ロジック構文を使用しましょう。**「操作切り替え」**には、決定点としての機能があります。 動詞/パスのペアに基づいて、適切な操作を呼び出す必要があります。

    a. _キャンバス_ に **invoke** ポリシーが既に追加されているなら、それを削除します。  
    b. パレットから**「操作切り替え」**をドラッグして、キャンバスにドロップします。  
      - **case 0** に、**get /current** 操作を割り当てます。
      - 新規ケースの **case 1** を追加します。
      - **get /today** 操作を **case 1** に割り当てます。
	  
	  
      ![](images/new-assemble-1.png)
	  
    c. パレットから **invoke** ポリシーをドラッグして、**get /current** の下の処理行にドロップします。_invoke アクションは、操作内から既存のサービスを呼び出すために使用されます_。   
    d. アクション・タイトルを「**invoke-current**」に更新します。  
    e. URL フィールドを `https://myweatherprovider.mybluemix.net/current?zipcode=$(request.parameters.zipcode)` に更新します。  
	
	![](images/new-assemble-invoke1.png)
	
	
	f. パレットから **invoke** ポリシーをドラッグして、**get /today** の下の処理行にドロップします。 
    g. タイトルを「**invoke-today**」に更新します。  
    h. URL フィールドを `https://myweatherprovider.mybluemix.net/today?zipcode=$(request.parameters.zipcode)` に更新します。  
	
       ![](images/new-assemble-invoke2.png)
	   

18. アクション構成パネルを閉じます。API を保存します。

---

### API プロキシーのテスト
{: #test_proxy_tut_add_openapi_rest_bm}

1. **「アセンブル」**タブで、アクションをさらに表示するためのアイコンをクリックし、**「デフォルト製品の生成」**を選択します。  
   ![](images/generate-default-product-small.png) 

2. **「新規製品」**ダイアログ・ボックスでデフォルト・オプションを受け入れ、**「製品の作成」**をクリックします。 Weather Provider API product が作成され、サンドボックス・カタログに公開されます。 製品の生成が成功したという趣旨のメッセージが表示されます。  

  ![](images/generate-default-product-new-weather.png) 

  - _{{site.data.keyword.apiconnect_short}} では、**製品**という形で、API を用途ごとにグループ分けできます。 製品は**カタログ**に公開されます。 [{{site.data.keyword.apiconnect_short}} 用語集](../apic_glossary.html)_

3. 「アセンブル」タブで、再生アイコンをクリックして、API プロキシーのターゲット呼び出しをテストします。

4. テスト・パネルで **get /current** 操作を選択します。

	a. この操作では郵便番号が必須パラメーターになっているので、アメリカの有効な郵便番号 (10504 など) を入力します。 
	
	![](images/test-invoke-params.png)  
		
	b. **「呼び出し」**をクリックします。   

	_CORS エラーになった場合は、エラー・メッセージに記されている手順を実行してください。 エラーに含まれているリンクをクリックして例外をブラウザーに追加し、「呼び出し」ボタンを再び押します。_
  
    ![](images/test-invoke-new.png)  


---

### まとめ
{: #conclusion_tut_add_openapi_rest_bm}

このチュートリアルでは、API パススルー・プロキシーによって既存の REST サービスを呼び出す方法を学習しました。 まず、Web ブラウザーでサンプル・サービスを利用できるかどうかを確認しました。 次に、{{site.data.keyword.apiconnect_short}} で新しい OpenAPI 仕様を作成し、それを呼び出し対象のサンプル・サービスにリンクしました。 その API を製品としてパッケージし、その製品をカタログに公開し、プロキシーをテストしました。

---

## 次のステップ
{: #next_tut_add_openapi_rest_bm}

[OAuth 2.0 を使用した保護](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_oauth_2)によって API を保護します。

作成 > **管理** > 保護 > ソーシャル化 > 分析
