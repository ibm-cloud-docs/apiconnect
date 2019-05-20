---

copyright:
  years: 2017
lastupdated: "2017-11-02"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 新しい API 仕様の追加と既存の REST サービスの呼び出し (デベロッパーズ・ツールキットを使用する場合)
{: #tut_add_openapi_rest_tk}

**所要時間**: 15 分  
**スキル・レベル**: ビギナー  

## 目標
{: #object_tut_add_openapi_rest_tk}

このチュートリアルでは、{{site.data.keyword.apiconnect_full}} での作業を簡単に開始するための基礎として、既存の API を管理制御下に置くため方法を取り上げます。 まず新しい OpenAPI 仕様を作成してから、既存の REST サービスのパススルー API プロキシーを作成します。

## 前提条件
{: #prereq_tut_add_openapi_rest_tk}

始める前に、[API Connect インスタンスのセットアップ](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_set_up_apic_instance)と [API Connect ツールキットのインストール](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_install_toolkit)が必要です。

---


## サンプル・アプリケーションの探索とターゲット・エンドポイントのテスト
{: #expl_test_tut_add_openapi_rest_tk}

このチュートリアルで使用する _Weather Provider_ サンプル・アプリケーションは、作成されています。
1. アプリケーションを探索するために、[http://gettingstartedweatherapp.mybluemix.net/ ![外部リンクのアイコン](../../icons/launch-glyph.svg "外部リンクのアイコン")](http://gettingstartedweatherapp.mybluemix.net/){: #new_window} に移動します。  
2. アメリカの有効な 5 桁の郵便番号を入力して、_**現在の天候**_ と_**今日の予報**_ を入手します。  
![](images/explore-weatherapp-1.png)

3. 上の天候サンプル・アプリケーションは、天候データを提供する API を使用して作成されています。 **現在の**天候データを取得するエンドポイントは、_**https:// myweatherprovider<span></span>.mybluemix.net/current?zipcode={zipcode}**_ です。 [https://myweatherprovider.mybluemix.net/current?zipcode=90210](https://myweatherprovider.mybluemix.net/current?zipcode=90210){: #new_window}にアクセスして、テストしてください。  

  ![](images/explore-weatherapp-2.png)

4. また、**今日の**予報データを取得するエンドポイントは、`https:// myweatherprovider<span></span>.mybluemix.net/today?zipcode={zipcode}` です。 [https://myweatherprovider.mybluemix.net/today?zipcode=90210](https://myweatherprovider.mybluemix.net/today?zipcode=90210){: #new_window} にアクセスして、テストしてください。  

  ![](images/explore-weatherapp-3.png)

---

## 新しい OpenAPI 仕様の追加と既存の REST サービスの呼び出し
{: #add_spec_tut_add_openapi_rest_tk}

1. **API Designer** を起動します。 端末で `apic edit` と入力します。
2. IBMid を使用してログインします。
    ![](images/screenshot_apic-edit_login.png)
3.   API Designer でナビゲーション・パネルが開いていることを確認します。 表示されていない場合は、「>>」をクリックして開きます。 **API Designer** のナビゲーション・パネルで**「ドラフト」>「API」**を選択します。
4. **「API」**パネルで**「追加」>「新規 API」**を選択します。
5. 「新規 API」ウィンドウで、タイトルに「Weather Provider API」と入力します。 _「名前」と「基本パス」は、自動的に入力されます_。  
  ![](images/toolkit-add-new-api.png)   
6. **「API の作成」**をクリックしてウィザードを完了します。  

7. API が作成されると、**「設計」**タブが選択されます。

8. **「ホスト」**パネルまでスクロールします。 フィールドに値が自動的に取り込まれていない場合は、`$(catalog.host)` を入力します。

9. **「セキュリティー」**タブまでスクロールして、自動生成された「clientIDHeader (API Key)」を削除します。  
_(API キーによるセキュリティーについては、次のチュートリアルで学びます。)_  

10. **「パス」**パネルで、**+** をクリックして新しいパスを作成します。
  a. 新しいパスに「**/current**」と名前を付けます。  
  b. 同じ**「パス」**パネルで **GET /current** セクションを選択します。  
  c. **GET /current** セクションで、新しい**「パラメーター」**を追加します。 サンプル・アプリケーションを探索しているときに気付かれたと思いますが、気象情報サービスではパラメーターとして郵便番号が必要です。
      - 名前: zipcode  
      - 場所: 照会  
      - 必須：はい  
      - タイプ: ストリング  
    ![](images/path-current-1.png)
  d. API を保存します。

11. 前のステップで照会パラメーターを定義したので、今度は気象 API を呼び出す際に返される応答オブジェクトを定義する必要があります。 この定義を行うには、**「定義」**パネルまでスクロールダウンします。

  1. 新規定義を追加します。 
  2. 新規定義に _Current_ と名前を付けます。
  3. 「タイプ」を_「オブジェクト」_に設定します。
  4. 定義 **Current** に新しいプロパティーを追加します。
    - 名前: zip         /  タイプ: ストリング
    - 名前: temperature /  タイプ: 整数
    - 名前: humidity    /  タイプ: 整数
    - 名前: city        /  タイプ: ストリング
    - 名前: state       /  タイプ: ストリング
    ![](images/definition-current-1.png)
  5. API を保存します。  

12. 前のステップで、応答オブジェクトを定義しました。 次に、この応答オブジェクトを **get /current** のパスに関連付ける必要があります。 ナビゲーションで、**「パス」**パネルまでスクロールして戻ります。
  a. **GET /current** 操作を開き、**「応答」**セクションまでスクロールします。
  b. 200 OK 応答のスキーマを「オブジェクト」から「**Current**」に変更します。
  c. API を保存します。

13. 今作成したパスと操作は、現在の気象データを取得するためのものです。 今度は、今日の気象予報データを取得するための同様のパスと操作を作成する必要があります。 ステップ 11 で **/current** パスを作成した方法と同様に、新しいパス **/today** を作成します。 

14. **GET /today** 操作の下に新しいパラメーターを追加します。
    - パラメーター名: zipcode  
    - 場所: 照会  
    - 必須：はい  
    - タイプ: ストリング  

15. 新規定義の **Today** を作成します。

16. 定義 **Today** に新しいプロパティーを追加します。
  - 名前: zip / タイプ: ストリング
  - 名前: hi / タイプ: 整数
  - 名前: lo / タイプ: 整数
  - 名前: nightHumidity / タイプ: 整数
  - 名前: dayHumidity / タイプ: 整数
  - 名前: city / タイプ: ストリング
  - 名前: state / タイプ: ストリング

17. **GET /today** セクションの応答スキーマを「Today」に更新します。

18. API を保存します。

19. **「アセンブル」**タブに切り替えます。 ここまでで、**GET /current** と **GET /today** という 2 つの操作を作成しました。 適切なターゲット・エンドポイントが呼び出されるように、呼び出し対象の操作に対して条件を実行するためのロジックを作成する必要があります。 これを行うために、**「操作切り替え」**ロジック構文を使用しましょう。  

    a. _キャンバス_ に **invoke** ポリシーが既に追加されているなら、それを削除します。  
    b. _パレット_ から**「操作切り替え」**をドラッグして、キャンバスにドロップします。  
      - **case 0** に、**get /current** 操作を割り当てます。
      - 新規ケースの **case 1** を追加します。
      - **get /today** 操作を **case 1** に割り当てます。
    ![](images/assemble-1.png)
    **「操作切り替え」**には、決定点としての機能があります。 動詞/パスのペアに基づいて、適切な操作を呼び出す必要があります。  
    c. パレットから **invoke** ポリシーをドラッグして、キャンバスにドロップします。 このポリシーを **/get current** パスと、**/get today** パスにドロップします。
    d. **/get current** パスにある **invoke** ポリシーを選択して、そのタイトルを「**invoke-current**」に更新します。  
    e. URL フィールドを `https://myweatherprovider.mybluemix.net/current?zipcode=$(request.parameters.zipcode)` に更新します。
    f. **/get today** パスにある **invoke** ポリシーを選択して、そのタイトルを「**invoke-today**」に更新します。  
    g. URL フィールドを `https://myweatherprovider.mybluemix.net/today?zipcode=$(request.parameters.zipcode)` に更新します。  

20. API を保存します。

---

## API プロキシーのテスト
{: #test_tut_add_openapi_rest_tk}

### _API Manager テスト・ツール_ によるテスト
{: #test_apimgr_tut_add_openapi_rest_tk}

1. Designer の左下にある「サーバーの開始」アイコン (>) をクリックして、ローカル・テスト・サーバーを開始します。 ゲートウェイが開始すると、状況が自動的に「実行中」に更新されます。

    ![](images/screenshot_start-server-1.png)

2. **「アセンブル」**タブで、再生アイコン (>) をクリックして、API プロキシーのターゲット呼び出しをテストします。 _このチュートリアルでは組み込みの Micro Gateway を使用するので、「Micro Gateway ポリシー」が選択されていることを確認してください。_

    ![](images/screenshot_test-0.png)

3. テスト・パネルで **get /current** 操作を選択します。  
  a. この操作では郵便番号が必須パラメーターになっているので、アメリカの有効な郵便番号 (90210 など) を入力します。  
  b. **「呼び出し」**をクリックして、以下の応答が表示されることを確認します。
  ```
  200 OK response
  Current weather data for 90210  
  ```
    ![](images/screenshot_test-2.png)  

_CORS エラーになった場合は、エラー・メッセージに記されている手順を実行してください。 エラーに含まれているリンクをクリックして例外をブラウザーに追加し、「呼び出し」ボタンを再び押します。_

### _「探索」ツール_ によるテスト
{: #test_explore_tut_add_openapi_rest_tk}

1. API プロキシー・エンドポイントをテストするために、_「探索」_を選択します。
2. パレットから **GET /current** 操作を選択します。
3. テスト・ボックスにアメリカの有効な郵便番号 (90210 など) を入力します。
4. **「操作の呼び出し」**をクリックして、応答を表示します。  
  ![](images/screenshot_explore.png)  
  
---

## まとめ
{: #conclusion_tut_add_openapi_rest_tk}

このチュートリアルでは、API パススルー・プロキシーによって既存の REST サービスを呼び出す方法を確認しました。 まず、Web ブラウザーでサンプル・サービスを利用できるかどうかを確認しました。 次に、{{site.data.keyword.apiconnect_short}} で新しい OpenAPI 仕様を作成し、それを呼び出し対象のサンプル・サービスにリンクしました。 最後に、組み込みのテスト・ツールを使用して API プロキシーをテストしました。

---

## 次のステップ
{: #next_tut_add_openapi_rest_tk}

[レート制限](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_rate_limit)、[クライアント ID と秘密鍵](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_landing)、[OAuth 2.0 を使用した保護](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_oauth_2)のいずれかを使用して API を保護します。

作成 > **管理** > 保護 > ソーシャル化 > 分析

