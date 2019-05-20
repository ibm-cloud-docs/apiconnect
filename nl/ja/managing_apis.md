---

copyright:
  years: 2018
lastupdated: "2019-01-17"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal

subcollection: apiconnect

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# API の管理
{: #managing_apis}

API Connect を使用すれば、{{site.data.keyword.Bluemix}} 内の API が {{site.data.keyword.Bluemix_notm}} 内に存在するか、{{site.data.keyword.Bluemix_notm}} の外部で維持管理されているかに関係なく、それらを管理することができます。 API を管理することで、使用量を制御したり、採用を増やしたり、統計を追跡したりすることができます。

開発者が API を作成し、その製品を {{site.data.keyword.Bluemix_notm}} にプッシュすると、利用者は、API Manager UI 内で API の使用方法を管理できます。 以下の各トピックでは、{{site.data.keyword.apiconnect_short}} 内での製品の作成および管理の方法について説明します。

## セキュア・ゲートウェイによるオンプレミス API の公開
{: #expose_apis_sec_gate_managing_apis}

セキュア・ゲートウェイを作成すると、オンプレミスの API を {{site.data.keyword.apiconnect_full}} に安全に公開できます。

セキュア・ゲートウェイを作成し、クライアントまたはクラウドの `<host>:<port>` のアドレスを指定すると、{{site.data.keyword.Bluemix_notm}} {{site.data.keyword.SecureGateway}} サービスの機能が {{site.data.keyword.apiconnect_short}} に統合されます。これは、セキュアな経路で {{site.data.keyword.apiconnect_short}} からオンプレミスの API に安全にアクセスできることを意味します。 オンプレミスのデータを公開することなく、パブリック環境の {{site.data.keyword.apiconnect_short}} へのトンネルを効果的に作成できます。 実行する必要があるのは、IBM Cloud でセキュア・ゲートウェイ・サービスを作成および構成して、API でそのためのアドレスを指定することだけです。

{{site.data.keyword.SecureGateway}}・サービスの詳細と設定方法については、[{{site.data.keyword.SecureGateway}}の概要![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com/docs/services/SecureGateway?topic=index#getting-started-with-sg){: #new_window}を参照してください。

### API でのセキュア・ゲートウェイの使用
{: #using_sec_gate_apis_managing_apis notoc}

ゲートウェイを構成したら、API でそれを使用できるようになります。
{:shortdesc}

API でセキュア・ゲートウェイを使用するには、以下のステップを実行します。
1. 以下の手順に従って、API と製品を作成します。
  - **「ナビゲート先」**<img src="images/navigate_to_icon.png" alt="「ナビゲート先」アイコン" /> >**「ドラフト」**>**「API」**>**「追加」**をクリックします。
  - 作成する API のタイプを選択します。
  - **「製品の追加 (Add a Product)」**を選択またはクリックします。 **重要**: まだ製品を公開しないでください。
  - **「API の作成」**をクリックします。
  API が`「設計」`ビューに表示されます。
  
2. **「アセンブル」**をクリックします。

3. **「呼び出し」**ポリシーをクリックして**「呼び出し」**パレットを開きます。
**制約事項**: セキュア・ゲートウェイを使用する API では、`Switch`、`Operation Switch`、`If` などの論理スイッチは使用できません。

4. **「セキュア・ゲートウェイを介して URL にアクセスする (Access URL through Secure Gateway)」**チェック・ボックスを選択**しない**でください。
**重要**: これは製品ではサポートされない、いずれ削除される非推奨機能のチェック・ボックスです。 このチェック・ボックスを選択する代わりに、セキュア・ゲートウェイの URL アドレスを直接指定してください。

5. 「URL」フィールドで、クラウドのホスト名およびポート番号を指定して `target-url` を更新します。次のようになります。
```
target-url: cap-sg-prd-5.securegateway.appdomain.cloud:18579
```

6. **「保存」**<img src="images/icon_save.png" alt="「保存」アイコン" />をクリックします。

7. **「すべての API」** >**「製品」**をクリックし、先ほど作成した製品を選択します。

8. **「公開」**アイコンをクリックして、選択したカタログに製品を掲載します。

9. 使用するカタログを選択します。

10. 掲載する製品を選択します。

11. **「公開」**をクリックします。

オンプレミスの API が {{site.data.keyword.apiconnect_short}} に安全に公開されました。 次に、{{site.data.keyword.SecureGateway}} API をテストします。

### セキュア・ゲートウェイ API のテスト
{: test_sec_gate_managing_apis notoc}

API で {{site.data.keyword.SecureGateway}} のアドレスを指定した後で、API をテストして、ゲートウェイが動作していて正しい応答が生成されていることを確認できます。

セキュア・ゲートウェイを使用して API をテストするには、以下の手順を実行します。

1. <img alt="「ナビゲート先」アイコン" src="images/navigate_to_icon.png" /> >**「ドラフト」**>**「API」**
**<該当の API>** >**「アセンブル」**をクリックします。

2. **「テスト」**アイコン <img src="images/test_icon.png" alt="「テスト」アイコン"/> をクリックします。

3. 表示されたリストの中から、テストするカタログを選択します。

4. URL が正しいセキュア・ゲートウェイ `<cloud_host>:<port>` のアドレスを指定しており、セキュア・ゲートウェイ・サービスの宛先が [{{site.data.keyword.SecureGateway}}![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com/docs/services/SecureGateway?topic=index#getting-started-with-sg){: #new_window}資料の説明に従って正しく構成されていることを確認します。

5. 表示されたリストから、既存の製品を選択し、**「製品の再公開」**をクリックします。
   **重要**: この製品が既にカタログに公開されている場合、新しいゲートウェイにより製品が再公開されます。

6. **オプション**:
新規製品を作成するために名前を指定し、**「作成および公開」**をクリックします。

7. **「次へ」**をクリックします。

8. 表示されたリストから、呼び出す操作を選択します。

9. **「呼び出し」**をクリックします。

テスト結果が表示されます。

## LoopBack アプリケーションのステージングおよび公開
{: #stage_publish_lb_app_managing_apis}

1. API Designer のナビゲーション・ペインで、**「製品」**をクリックします。
「製品」タブが開きます。

2. 製品のバージョンを選択します。作業対象のバージョンを必ずクリックしてください。

3. ランタイムを {{site.data.keyword.Bluemix_notm}} に公開するには、**「公開」**をクリックします。

4. **「ターゲットの追加および管理」** >**「IBM Cloud ターゲットの追加」**をクリックします。

5. 公開先の {{site.data.keyword.Bluemix_notm}} の**「地域」**を選択してから、サインインします。

6. 公開先の {{site.data.keyword.Bluemix_notm}} の**「組織」**を選択します。

7.  カタログのリストが表示されます。 公開先のカタログを選択します。

8.  **「次へ」**をクリックします。

9. 公開する LoopBack application を選択します。
そのランタイムを {{site.data.keyword.Bluemix_notm}} にデプロイするのはこれが初めてである場合は、名前を追加して、**「追加」**アイコンをクリックします。

10.  **「保存」**をクリックします。

11.  再び**「公開」**をクリックして、**「アプリケーションの公開」**を選択します。

12.  **「公開」**をクリックします。

13. コマンド・ラインに、その API の「API ターゲット URL (API Target URL)」と「API 呼び出し TLS プロファイル (API invoke tls-profile)」が指定されます。
この情報をメモしてください。 「API 呼び出し TLS プロファイル」は常に `client:Loopback-client` ですが、「API ターゲット URL」は、以下のステップで説明する方法で取得できます。
    ```
    Deploying to Bluemix
    ...preparing project
    ...building package for deploy
    ...uploading package
    Runtime published successfully.
    Management URL: https://<domain name>/apps/33e7b062-092b-4227-af97-047499dab2e7
    API target urls: apiconnect-33e7b062-092b-4227-af97-047499dab2e7.<Bluemix org>-<Bluemix space>.apic.<domain name>
    API invoke tls-profile: client:Loopback-client
    Updated newapi_1.0.0.yaml with tls-profile and target-url.
    Updated notes.yaml with tls-profile and target-url.
    ```

14. API Designer UI で、以下のステップを実行します。
    1. **「API」**をクリックします。
    2. 「API」を選択します。
    3. **「アセンブル」**をクリックします。
    4. アセンブリー・エディターで、**「ポリシーのフィルター」**アイコンをクリックします。
    5. **「DataPower Gateway ポリシー」**を選択します。
    6. **「保存」**をクリックして API を保存します。

15.  次に、API Manager に公開する必要があります。 **「公開」**をクリックします。
    1. **「アプリケーションの公開」**を選択してから、以下のいずれかのオプションを選択します。
	    - **既存アプリケーションの置換 (Replace existing app)**: 既に公開したアプリケーションがあり、その既存のアプリを上書きする場合は、このオプションを選択します。
        - **新規アプリケーション (既存の経路を使用) (As a brand new app (using the existing route))**: 新しいアプリを作成する場合は、このオプションを選択し、**「新規アプリ (New app)」**フィールドに名前を入力します。 サービスは中断されません。

    2. 以下のオプションを選択します。
	    - 「製品のステージングまたは公開 (Stage or Publish products)」
        - 特定の製品を選択
        - _your product_
 
    3. **「公開」**をクリックします。

公開が機能していることを検査するには、以下の手順を実行します。

1. {{site.data.keyword.Bluemix_notm}} アプリが稼働していることを確認します。

2. ブラウザー・ウィンドウを開いて、API URL に移動します。
アプリケーションはクライアント検証により保護されます。 正しいクライアント証明書を提供しないと、エラーが発生します (この想定になっています)。

3. 公開された {{site.data.keyword.apiconnect_short}} URL に移動します。
以下に例を示します。
```
https://<domain>/<Bluemix org>-<Bluemix space>/<Catalog identifier>/api/notes
```
「200」応答が表示されます。

## カタログの構成
{: #config_cat_managing_apis}

API Manager カタログを作成して構成できます。 カタログは、製品と API を開発者組織に提供する前にテストのために分離する場合に役に立ちます。
API Manager に用意されているデフォルトの API URL を使用せずに済むように、カタログを構成する際にカスタム・ブランドを構成することもできます。

カタログを作成するには、以下の手順を実行します。

1. **「ナビゲート先」**<img alt="「ナビゲート先」アイコン" src="images/navigate_to_icon.png">>**「ダッシュボード」**をクリックします。

2. **「+ 追加」**>**「カタログ」**をクリックします。
**「カタログの追加」**ウィンドウが表示されます。

3.  **「表示名 (Display Name)」**フィールドに、新しいカタログの名前を入力します。

4. **「名前」**フィールドに、URL のカタログ・セグメントを形成するテキストを入力します。
**注:** **「名前」**フィールドには、小文字の英数字 (a-z と 0-9)、またはハイフン文字 (-) のみを含めることができます。 名前の開始文字や終了文字としてハイフンを使用することはできません。

5. **「追加」**をクリックします。 カタログが作成され、ダッシュボードに表示されます。

6. カタログを構成するには、カタログの名前をクリックしてから、**「設定」** >**「情報」**をクリックし、以下の手順を実行します。
  1. 新しいカタログが開発カタログである場合は、**「開発モード (Development mode)」**を選択します。
開発モードを選択すると、ステージングと公開のアクションが適用されます。つまり、既に公開されている製品をもう一度公開すると、警告なしで上書きされます。 競合が見つかった場合は、システムによって自動的に解決されます。 非公開にするアクションは自動的に実行されます。
**注:** 開発カタログの場合、承認ボックスは表示されません。 ライフサイクルの承認プロセスを有効にすることはできません。
  2. カタログの自動サブスクリプションを有効にする場合は、**「自動サブスクリプション (Automatic subscription)」**を選択します。
自動サブスクリプションを有効にすると、API のテストが容易になります。
これは、カタログ内のすべてのプランを自動的にサブスクライブするアプリケーション・テストが、事前に指定したクライアント ID とクライアント秘密鍵を使用して行われるため、テスト時にプランやアプリケーションを指定する必要がなくなります。
**注:** 自動サブスクリプションは、開発カタログの場合のみ使用可能です。
  3. このカタログがデフォルトのステージング・カタログである場合は、**「デフォルト」**を選択します。 その後、
カタログに公開される API に対する呼び出しで、カタログ名が含まれない短縮形の URL を使用できます。
    **注:****「デフォルト」**を選択できるカタログは 1 つのみです。
  4. **オプション**: **「エンドポイント」**をクリックして、以下のフィールドにデータを追加します。
        - **カスタム・ゲートウェイ URL**: 「カスタム・ゲートウェイ URL (Custom Gateway URL)」テキスト・フィールドに URL を入力します。 API Manager が生成したデフォルトの URL を使用せずに、{{site.data.keyword.apiconnect_short}} にデプロイされている API の URL のカスタム・ブランドを行う場合は、カスタム・ゲートウェイ URL を使用します。
        デフォルトでは、{{site.data.keyword.apiconnect_short}} ゲートウェイ URL は以下の形式です。
        ```
        https://gateway_cluster_hostname/organization_name/Catalog_name
        ```
        しかし、自社に適した URL (例えば `https://api.mycompany.com`) を指定してデフォルトをオーバーライドできます。 そうすると、開発者ポータルに表示されるすべての API エンドポイントに、指定した URL が反映されます。
        **注:**
		    - カスタムのホスト名およびドメインをデフォルトのゲートウェイ URL にマップする DNS 項目を構成する必要があります。
		    - API のエンドポイントにカスタム・ゲートウェイ URL を反映させるには、API Connect ゲートウェイによって適用されるように API を構成しなければなりません。 詳細については、[Specifying an alternative host for an API ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){: #new_window} を参照してください。
		    - 同じカスタム・ゲートウェイ URL を複数のカタログに適用しないでください。このようなシナリオでの動作は不明確です。
	        **ヒント**: API を呼び出すときに、API 要求の HTTP ホスト・ヘッダーに「カスタム・ゲートウェイ URL」フィールドで指定した値を設定することもできます。

	    - **カスタム API URL**
	    「カスタム API URL (Custom API URL)」テキスト・フィールドに URL を入力します。 カスタム API URL を使用して、サード・パーティーのゲートウェイにデプロイされている API の URL を指定します。

	    カスタム API URL は、外部的に知られている API 名でエンドポイントを表します。つまり、開発者ポータルに公開されているエンドポイントであり、アプリケーション開発者はこの名前を使用して API の呼び出しや公表を行います。

	    このカタログでサード・パーティーのゲートウェイまたは外部ロード・バランサーを使用している場合は、このフィールドに URL を指定します。 そうすると、開発者ポータルに表示されるすべての API エンドポイントに、指定した URL が反映されます。 これらのエンドポイントは、サード・パーティーのゲートウェイまたはロード・バランサー上に存在し、API コンシューマーに公開される仮想アドレスを提示します。このアドレスは、ゲートウェイ上の API プロキシーまたは API アセンブリー・エンドポイントにマップされます。 カスタム API URL から派生したエンドポイントは、通常、実動開発者ポータルで公開されて、API のアドレスを公表します。

	    **注:** カタログにカスタム API URL を指定すると、API の構成時に指定したホスト名より優先されます。 詳細については、[Specifying an alternative host for an API ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){: #new_window} を参照してください。

	    - **開発者ポータル API 呼び出しのホスト名**:
	    「ポート API エンドポイント (Port API Endpoint)」ウィンドウ領域で、開発者ポータル API 呼び出しのホスト名を入力します。 入力するホスト名は、管理サービスのホスト名にすることができます。 開発者ポータルのコンテキスト内で開発者ポータル API にアクセスするには、開発者ポータル API 呼び出し用に基本ホスト名を構成しなければなりません。 このアクションにより、API Manager でホスト名をプロバイダー組織と開発者ポータル API 呼び出しのカタログにマッピングできるようになるため、ユーザーがそれらを取得して呼び出しに含める必要がなくなります。

7. **「保存」**アイコンをクリックします。

## カタログのパーティション化
{: #part_cat_managing_apis}

{{site.data.keyword.apiconnect_short}} のシンジケーション・フィーチャーを使用するには、シンジケーション機能を必要とするカタログ内でスペースを有効にする必要があります。

カタログ内でスペースを有効にするには、以下の手順を実行します。
1. API Manager UI のダッシュボードで、作業対象のカタログを選択します。

2. **「設定」** >**「概要」**をクリックした後、**「スペース」**スライダー・コントロールをクリックします。

3. **「スペースを有効にする (Enable Spaces)」**ウィンドウで、**「有効にする (Enable)」**をクリックした後、**「保存」**アイコン <img src="images/icon_save.png" alt="「保存」アイコン"/> をクリックします。
**「スペースの管理」**リンクが**「スペース」**スライダー・コントロールの下に表示され、**「スペース」**リンクがナビゲーション・ペインに追加されます。 それらのリンクのいずれかをクリックすることにより、スペースを管理できます。

カタログでスペースが有効になり、「New Space」というデフォルトのスペースが作成されます。

シンジケーションの使用について詳しくは、Knowledge Center のトピック、[Using syndication in IBM API Connect ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.apionprem.doc/capic_syndication_using.html){: #new_window} を参照してください。

## 開発者ポータルの構成
{: #config_dev_portal_managing_apis}

開発者ポータルとは、アプリケーション開発者がアクセスして使用できるようにするために、プランが公開される場所です。

アプリケーション開発者が使用するためのカスタマイズされた開発者ポータルを構築できます。 外観、コンテンツ、ユーザー設定、および構成設定を完全に管理できます。

開発者ポータルでは、アプリケーション開発者が API を検索して使用できるだけでなく、フォーラム、ブログ、コメント、レーティング、および API 用の Swagger UI など、さまざまな機能が提供されます。

1. API Manager UI で、作業するカタログを選択します。

2. **「設定」**タブを選択します。

3. **「ポータル」**をクリックします。

4. 「**ポータル構成**」セクションで、**「IBM 開発者ポータル」**を選択します。 ポータル URL が表示されます。

5. **「保存」**をクリックします。 開発者ポータルの Web 管理者ユーザーのワンタイム・ログイン・リンクが記載された E メールが送信されます。

6. E メールで送信されるリンクをクリックし、指示に従ってパスワードを再設定します。

開発者ポータルが構成されました。 受信した E メールの件名の行に、開発者ポータルの URL があります。 また、URL の検索は、API Manager UI で**「ポータル」** >**「設定」**をクリックすることでも行えます。

開発者ポータルで実行できるタスクについて詳しくは、IBM Knowledge Center の [開発者ポータル![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.devportal.doc/capim_devportal_overview.html){: #new_window}を参照してください。

## ロールの許可の構成
{: #config_permissions_roles_managing_apis}

API Manager でロールのアクセス権を構成するには、以下の手順を実行します。

1. API Manager の**「ダッシュボード」**で、作業対象のカタログをクリックします。

2. **「設定」**>**「許可」**をクリックします。
ロールを割り当てることができる製品の管理許可が表示されます。
  - **ステージ**: カタログへの製品のステージングを許可します。
  - **表示**: カタログ内の製品の表示とリスト出力を許可します。
  - **管理**: 製品のライフサイクル (公開、非推奨、廃棄、アーカイブ) の管理を許可します。
  - **承認**: 製品のライフサイクルの状態変更の承認を有効にします。
**注:** すべての開発カタログについて、製品ライフサイクルの状態変更の承認は無効になっています。

3. **「ステージ」**、**「表示 (View)」**、または**「管理」**の各許可にロールを追加するには、対応する**「+」**アイコンをクリックします。
以下のリストに、デフォルトで使用可能なロールを示します。
  - 管理者 (Administrator)
  - プロダクト・マネージャー (Product Manager)
  - API 開発者 (API Developer)
  - パブリッシャー
「所有者」ロールはすべての許可を持ちます。

4. 製品のライフサイクル状態変更に対する承認を有効にします。そのためには、必要なチェック・ボックスを選択し、対応する**「+」**アイコンをクリックして、ライフサイクル状態変更を承認する許可を持つロールを割り当てます。
選択するライフサイクル状態変更は、承認を適用したいものです。
例えば、「公開 (Publish)」のみを選択し、他のチェック・ボックスはクリアした状態のままにした場合、製品を公開するときには承認が必要になりますが、他のライフサイクル状態変更についてはいずれも承認が不要になります。
5. ユーザー定義のポリシーを管理するための許可を付与されたロールを割り当てるために、**「ポリシー管理 (Policy Management)」**セクションの**「+」**アイコンをクリックします。
ポリシー管理の許可が表示され、必要に応じて、ロールを割り当てることができます。
6. **「保存」**アイコンをクリックします。
