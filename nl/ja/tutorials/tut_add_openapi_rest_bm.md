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

# 新しい API 仕様の追加と既存の REST サービスの呼び出し (IBM Bluemix を使用する場合)
**所要時間**: 15 分  
**スキル・レベル**: ビギナー  

## 目標
このチュートリアルは、{{site.data.keyword.apiconnect_full}} での作業を簡単に開始するための方法を取り上げます。まず新しい OpenAPI 仕様を作成してから、既存の REST サービスのパススルー API プロキシーを作成します。

## 前提条件
始める前に、[API Connect インスタンスのセットアップ](tut_prereq_set_up_apic_instance.html)が必要です。

---

### サンプル・アプリケーションの探索とターゲット・エンドポイントのテスト
このチュートリアルで使用する _Weather Provider_ サンプル・アプリケーションは、作成されています。
1. アプリケーションを探索するために、[http://gettingstartedweatherapp.mybluemix.net/ ![外部リンクのアイコン](../../../icons/launch-glyph.svg "外部リンクのアイコン")](http://gettingstartedweatherapp.mybluemix.net/){:new_window} に移動します。  
2. アメリカの有効な 5 桁の郵便番号を入力して、_**現在の天候**_ と_**今日の予報**_ を入手します。  
![](images/explore-weatherapp-1.png)

3. 上の天候サンプル・アプリケーションは、天候データを提供する API を使用して作成されています。**現在の**天候データを取得するエンドポイントは、_**https:// myweatherprovider<span></span>.mybluemix.net/current?zipcode={zipcode}**_ です。[https://myweatherprovider.mybluemix.net/current?zipcode=90210 ![外部リンクのアイコン](../../../icons/launch-glyph.svg "外部リンクのアイコン")](https://myweatherprovider.mybluemix.net/current?zipcode=90210){:new_window} にアクセスして、テストしてください。  

  ![](images/explore-weatherapp-2.png)

4. また、**今日の**予報データを取得するエンドポイントは、_**https:// myweatherprovider<span></span>.mybluemix.net/today?zipcode={zipcode}**_ です。[https://myweatherprovider.mybluemix.net/today?zipcode=90210 ![外部リンクのアイコン](../../../icons/launch-glyph.svg "外部リンクのアイコン")](https://myweatherprovider.mybluemix.net/today?zipcode=90210){:new_window} にアクセスして、テストしてください。  

  ![](images/explore-weatherapp-3.png)


---

### REST API プロキシーを作成するための新規 OpenAPI 仕様の追加  
1. {{site.data.keyword.Bluemix_short}} にログインします (https://new-console.ng.bluemix.net/login)。
2. {{site.data.keyword.Bluemix_short}} のナビゲーション・パネルで**「サービス」**を選択してから、**「ダッシュボード」**を選択します。{{site.data.keyword.apiconnect_short}} サービスを起動します。
3. {{site.data.keyword.apiconnect_short}} でナビゲーション・パネルが開いていることを確認します。表示されていない場合は、**「>>」**をクリックして開きます。  
4. ナビゲーション・パネルで**「ドラフト」** を選択します。
5. **「API」**タブで**「追加」**をクリックします。ドロップダウン・メニューで、**「新規 API」**を選択します。    
  ![](images/create-new-1.png)  
6. *「新規 API」*ウィンドウで、タイトルに `Weather Provider API` と入力します。
_「名前」と「基本パス」は、自動的に入力されます_。  
  ![](images/bluemix-add-new-api.png)
7. **「API の作成」**をクリックしてウィザードを完了します。  
8. API を作成すると、**「設計」**タブが選択されます。 
9. **「ホスト」**パネルまでスクロールします。フィールドに値が自動的に取り込まれていない場合は、`$(catalog.host)` を入力します。
10. **「基本パス」**パネルで、自動的に設定された値である `/weather-provider-api` を確認します。これらの値から API のターゲット URL が作成されます。  

11. **「セキュリティー」**タブまでスクロールして、自動生成された「clientIDHeader (API Key)」を削除します。  
_(API キーによるセキュリティーについては、次のチュートリアルで学びます。)_  

12. ナビゲーションで**「パス」**パネルまでスクロールダウンして、**+** をクリックして新しいパスを作成します。     
    a. 新しいパスに「**/current**」と名前を付けます。  
    b. 同じ*「パス」*パネルで **GET /current** セクションを選択します。    
    c. **GET /current** セクションで、新しい**「パラメーター」**を追加します。サンプル・アプリケーションを探索しているときに気付かれたと思いますが、気象情報サービスではパラメーターとして郵便番号が必要です。   
      - 名前: zipcode  
      - 場所: 照会  
      - 必須：はい  
      - タイプ: ストリング   
    ![](images/path-current-1.png)   
    d. API を保存します。  

13. 前のステップで照会パラメーターを定義したので、今度は気象 API を呼び出す際に返される応答オブジェクトを定義する必要があります。この定義を行うには、**「定義」**パネルまでスクロールダウンします。   
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

14. 前のステップで、応答オブジェクトを定義しました。次に、この応答オブジェクトを **get /current** のパスに関連付ける必要があります。ナビゲーションで、**「パス」**パネルまでスクロールして戻ります。
    a. **GET /current** 操作を開き、**「応答」**セクションまでスクロールします。
    b. 200 OK 応答のスキーマを「オブジェクト」から「**Current**」に変更します。
    c. 「保存」アイコンをクリックして API を保存します。「API が保存されました」という確認通知が短いあいだ表示されます。 

15. 今作成したパスと操作は、現在の気象データを取得するためのものです。今度は、今日の気象予報データを取得するための同様のパスと操作を作成する必要があります。ステップ 12 で **/current** パスを作成した方法と同様に、新しいパス **/today** を作成します。

16. **GET /today** 操作の下に新しいパラメーターを追加します。
    - パラメーター名: zipcode  
    - 場所: 照会  
    - 必須：はい  
    - タイプ: ストリング  

17. 新規定義の **Today** を作成します。

18. 定義 **Today** に新しいプロパティーを追加します。
    - 名前: zip / タイプ: ストリング
    - 名前: hi / タイプ: 整数
    - 名前: lo / タイプ: 整数
    - 名前: nightHumidity / タイプ: 整数
    - 名前: dayHumidity / タイプ: 整数
    - 名前: city / タイプ: ストリング
    - 名前: state / タイプ: ストリング
19. **GET /today** セクションの応答スキーマを「Today」に更新します。
20. API を保存します。

21. **「アセンブル」**タブに切り替えます。ここまでで、**GET /current** と **GET /today** という 2 つの操作を作成しました。正しいターゲット・エンドポイントが呼び出されるように、呼び出し対象の操作に対して条件を実行するためのロジックを作成する必要があります。これを行うために、**「操作切り替え」**ロジック構文を使用しましょう。  
    a. _キャンバス_ に **invoke** ポリシーが既に追加されているなら、それを削除します。  
    b. パレットから**「操作切り替え」**をドラッグして、キャンバスにドロップします。  
      - **case 0** に、**get /current** 操作を割り当てます。
      - 新規ケースの **case 1** を追加します。
      - **get /today** 操作を **case 1** に割り当てます。
      ![](images/assemble-1.png)
**「操作切り替え」**には、決定点としての機能があります。動詞/パスのペアに基づいて、適切な操作を呼び出す必要があります。
    c. パレットから **invoke** ポリシーをドラッグして、キャンバスにドロップします。_invoke アクションは、操作内から既存のサービスを呼び出すために使用されます_。invoke アクションを **/get current** パスと、**/get today** パスにドロップします。   
    d. **/get current** パスにある **invoke** ポリシーを選択して、そのタイトルを「**invoke-current**」に更新します。  
    e. URL フィールドを `https://myweatherprovider.mybluemix.net/current?zipcode=$(request.parameters.zipcode)` に更新します。  
    f. **/get today** パスにある **invoke** ポリシーを選択して、そのタイトルを「**invoke-today**」に更新します。  
    g. URL フィールドを `https://myweatherprovider.mybluemix.net/today?zipcode=$(request.parameters.zipcode)` に更新します。  
       ![](images/assemble-2.png)

22. API を保存します。

---

### API プロキシーのテスト
1. **「アセンブル」**タブで、アクションをさらに表示するためのアイコンをクリックし、**「デフォルト製品の生成」**を選択します。  
   ![](images/generate-default-product-1.png) 

2. **「新規製品」**ダイアログ・ボックスでデフォルト・オプションを受け入れ、**「製品の作成」**をクリックします。Weather Provider API product が作成され、サンドボックス・カタログに公開されます。製品の生成が成功したという趣旨のメッセージが表示されます。  
  ![](images/generate-default-product-2.png)  
  
  ![](images/generate-default-product-3.png) 

  - _{{site.data.keyword.apiconnect_short}} では、**製品**という形で、API を用途ごとにグループ分けできます。製品は**カタログ**に公開されます。[{{site.data.keyword.apiconnect_short}} 用語集](../apic_glossary.html)_

3. 「アセンブル」タブで、再生アイコンをクリックして、API プロキシーのターゲット呼び出しをテストします。

4. テスト・パネルで **get /current** 操作を選択します。
	a. この操作では郵便番号が必須パラメーターになっているので、アメリカの有効な郵便番号 (90210 など) を入力します。 
	b. **「呼び出し」**をクリックして、以下の応答が表示されることを確認します。 
  ```
  200 OK response
  Current weather data for 90210  
  ```
  
    ![](images/test-invoke-1.png)  

    ![](images/test-invoke-2.png)  

    ![](images/test-invoke-3.png)

---

### まとめ
このチュートリアルでは、API パススルー・プロキシーによって既存の REST サービスを呼び出す方法を学習しました。まず、Web ブラウザーでサンプル・サービスを利用できるかどうかを確認しました。次に、API Connect で新しい OpenAPI 仕様を作成し、それを呼び出し対象のサンプル・サービスにリンクしました。その API を製品としてパッケージし、その製品をカタログに公開し、プロキシーをテストしました。

---

## 次のステップ

[レート制限](tut_rate_limit.html)、[クライアント ID と秘密鍵](tut_secure_landing.html)、[OAuth 2.0 を使用した保護](tut_secure_oauth_2.html)のいずれかを使用して API を保護します。

作成 > **管理** > 保護 > ソーシャル化 > 分析
