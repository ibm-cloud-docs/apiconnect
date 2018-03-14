---
copyright:
  years: 2017
lastupdated: "2017-12-15"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# API のインポート

Swagger 定義ファイルを使用して、REST API を追加できます。
{:shortdesc}

## 前提条件
{: #prereq_import_swagger}

始めに、ご使用のファイルがバージョン 2.0 の Swagger 仕様に適合していることを確認します。 有効なファイル・フォーマットは、JSON と YAML です。

Swagger ファイルをロードして REST API を追加するには、以下のステップを実行します。

1. API Manager UI のナビゲーション・ペインで、**「ドラフト」**をクリックし、次に**「API」**をクリックします。
「API」タブが開きます。

2. **「+ 追加 (+ Add)」**をクリックし、**「インポート」**セクションから**「Swagger 2.0」**を選択します。
**「Swagger のインポート API (Import Swagger API)」**ウィンドウが開きます。

3. **オプション**: ローカル・ファイル・システムからファイルをアップロードするには、**「ファイルの選択」**をクリックし、ファイル・システムで、使用するファイルを選択します。 `.json` ファイル、`.yml` ファイル、および `.yaml` ファイルに有効な Swagger 定義が含まれている場合、これらのファイルがサポートされます。

4. **オプション**: URL からファイルをアップロードするには、**「または URL からインポート (Or import from URL)」**をクリックして、表示されている**「URL」**フィールドに正しい URL を指定します。 URL にアクセスするのに認証が必要な場合は、ユーザー名とパスワードを指定します。 `.json` ファイル、`.yml` ファイル、および `.yaml` ファイルに有効な Swagger 定義が含まれている場合、これらのファイルがサポートされます。

5. **「インポート」**をクリックします。
新しい REST API 定義が、パスおよび HTTP 操作を含めて作成されます。

API 定義がインポートされると、**「ドラフト」**ページの**「API」**タブ内の API 定義のリストに表示されます。
次に、他の REST API 定義と同様に、API 定義を編集できます。

## IBM Integration Bus からの API のインポート
{: #tut_import_iib_apic}

このチュートリアルを使用すると、IBM Integration Bus で作成する REST API を {{site.data.keyword.apiconnect_full}} にインポートすることができ、それらの API をより簡単に管理し、公開できるようになります。 
{: shortdesc}

始めに、ご使用の REST API ファイルがバージョン 2.0 の Swagger 仕様に適合していることを確認します。 有効なファイル・フォーマットは、JSON と YAML です。

IBM Integration Bus を使用すると、REST API を作成できます。これらの API は、統合を RESTful Web サービスとして公開する場合に使用できる特殊なアプリケーションで、HTTP クライアントが呼び出すことができます。 API を作成したら、それらを {{site.data.keyword.apiconnect_short}} にインポートして管理し、公開することができます。

以下に、{{site.data.keyword.apiconnect_short}} で API を管理することの利点をいくつかリストします。
* API に対する呼び出しの数をモニターできる。
* API に対する呼び出しの数を制御できる。
* API の複数のバージョンを保守できる。

その他の利点については、[API の管理](managing_apis.html)を参照してください。

IBM Integration Bus で REST API を作成し、それを {{site.data.keyword.apiconnect_short}} にインポートするには、以下のステップを実行します。
1. IBM Integration Bus を使用して REST API を作成します。 制限: REST API は、IBM Integration Toolkit でのみ作成できます。
これは、IBM Integration Bus のインストール済みバージョンに用意されています。
	1. IBM Integration Toolkit を使用して REST API を作成します。 IBM Integration Bus を使用して REST API を作成する作業を行う方法について詳しくは、IBM Knowledge Center の [REST API を使用した統合ソリューションの開発![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSMKHH_10.0.0/com.ibm.etools.mft.doc/bi12016_.htm){: new_window} を参照してください。
		
	2. **「ファイル」** >**「新規」** >**「REST API」**を選択して、「REST API の作成」ウィザードを開きます。
		
	3. REST API の名前を入力します。 指定した名前は、IBM Integration Toolkit 内でプロジェクトの名前として使用されます。
		
	4. 以下の REST API 作成方法のいずれかを選択し、手順を完了します。
		
	**IBM Integration Toolkit に用意されている REST API エディターを使用して最初から作成**:
		1. **「REST API を作成し、リソースと操作を自分で定義する」**を選択します。
		2. **「完了」**をクリックします。 新規 REST API 用の REST API エディターが自動的に開くので、このエディターを使用して、リソース、モデル、操作を定義する必要があります。
		
	**既存の Swagger 2.0 文書から作成**:
		1. **「Swagger 文書に定義されているリソースおよび操作のインポート」**を選択し、**「次へ」**をクリックします。
		2. REST API に含めるリソースと操作が記述されている Swagger 文書のパスを選択します。 Swagger 文書は、ファイル・システムからインポートすることも、ワークスペース内の既存のプロジェクトからインポートすることもできます。 REST API での使用に関してファイルの妥当性が検査されます。 選択した Swagger 文書の妥当性で何らかのエラーが検出されると、ウィザードの先頭に該当する妥当性検査エラーが表示されます。 選択した Swagger 文書の妥当性検査エラーが検出された場合、次の操作に進むことはできません。
		3. **「完了」**をクリックすると、API が作成されます。
	5. REST API 用のサブフローを実装します。これらは、含める必要がある REST 操作です。
2. IBM Integration Bus の新規または既存のブローカー・アーカイブ (BAR) ファイルに REST API プロジェクトを追加します。
3. BAR ファイルを IBM Integration Bus on Cloud にデプロイします。
	1. まだログインしていない場合は、ご使用の IBMid を使用して IBM Integration Bus on Cloud にログインします。 アカウントがない場合は、アカウントの登録を行います。
	2. **「統合の追加」**>**「BAR ファイルのアップロード (Upload BAR file)」**をクリックします。
	3. REST API プロジェクト用に作成した BAR ファイルを選択します。 ヒント: IBM Integration Toolkit で BAR ファイルを右クリックしてプロパティーを表示すると、そのファイルの場所が分かります。
	4. **「保存」**を選択します。
	5. 画面を更新するには、**「リストの最新表示 (Refresh listing)」**を選択してください。
	6. IBM Integration Bus on Cloud の「*統合*」ウィンドウで API の API 統合フローを表示して、BAR ファイルが正常にアップロードされたことを確認します。
4. 「開始」アイコン ![「開始」アイコンが表示されている画面キャプチャー](images/a_play_button.jpg " ") を選択して、統合フローを開始します。 API が開始され、`実行中` の状況が表示されます。
5. 統合のリストから統合を選択し、それに関する情報を表示します。 「コンテンツ」メニュー内のツリーに、REST API とそれに関連するサブフローが表示されます。 他のセクションの情報を表示することもできます。 「パブリック・エンドポイント (Public Endpoints)」セクションでは、IBM Integration Bus on Cloud によって統合フローに割り当てられたパブリック URL を表示できます。 **「完全な URL の表示 (Show full URL)」**を選択して、その操作の完全な URL を表示します。
6. 操作の完全な URL をクリップボードにコピーします。 これは、{{site.data.keyword.apiconnect_short}} で作業を行うために API を構成するときに必要です。 基本認証を有効にした場合は、割り当てられたユーザー名とパスワードもメモしてください。

### IBM Integration Bus と API Connect の統合
{: #integrateiibapic}

1. IBM Integration Toolkit で、REST API プロジェクトに関連付けられている Swagger ファイルを {{site.data.keyword.apiconnect_short}} サービスにインポートします。 
	1. {{site.data.keyword.apiconnect_short}} {{site.data.keyword.Bluemix_notm}} サービスにログインします。
	2. API Manager UI のナビゲーション・ペインで、**「ドラフト」** >**「API」**をクリックします。 「API」タブが開きます。
	3. **「+ 追加 (+ Add)」** >**「ファイルまたは URL から API をインポート (Import API from a file or URL)」**を選択します。 *「OpenAPI (Swagger) のインポート」*ウィンドウが開きます。
	4. ローカル・ファイル・システムから作成したファイルをアップロードするには、**「ファイルの選択」**をクリックし、IBM Integration Bus で作成したファイルを選択します。 拡張子が `.json`、`.yml`、`.yaml` のファイルに有効な Swagger 定義が含まれている場合、これらのファイルがサポートされます。 **「製品の追加」**のオプションが選択されていることを確認してください。 **「この製品をカタログに公開する (Publish this product to a catalog)」**を選択すると、オプションで製品を公開できます。
	5. **「インポート」**をクリックします。 新しい REST API 定義が、パスおよび HTTP 操作を含めて作成されます。 ヒント: インポートの所要時間が 1 分を超える場合は、インポートをキャンセルし、ブラウザーを最新表示して、インポートを再試行してください。 セッションの有効期限が切れている可能性があります。
2. インポートした {{site.data.keyword.apiconnect_short}} 内の API を IBM Integration Bus on Cloud 内の API に関連付けます。
	1. {{site.data.keyword.apiconnect_short}} のダッシュボードに進みます。
	2. **「ドラフト」** > **「API」**を選択します。
	3. インポートした REST API をクリックします。
	4. 「アセンブル」タブを選択し、**「アセンブリーの作成」**を選択してプロキシー・ポリシーを追加します。
	5. **「プロキシー」**ポリシーを新しい空のポリシーにドラッグして、有効化します。
	6. IBM Integration Bus on Cloud の「パブリック・エンドポイント (Public Endpoints)」セクションからコピーした API の URL を貼り付けます。
	7. REST API の基本認証を有効にした場合は、IBM Integration Bus on Cloud で生成されたユーザー名とパスワードを入力します。
	8. API の設定を保存します。
3. API をテストします。
	1. API の「アセンブル」タブで、「テスト」ボタン ![「テスト」ボタン](images/a_play_button.jpg "「テスト」ボタン・アイコンを表示する画面キャプチャー") を選択します。
	2. **「製品の再公開」**を選択します。
	3. 「操作」を選択します。
	4. 必須パラメーターを入力します。
	5. **「呼び出し」**を選択します。
	6. API から予期される応答があることを確認します。 
	
API 定義がインポートされて統合されると、他の REST API 定義の場合と同様に API を管理し、制御できるようになります。 API について詳しくは、[API の管理](managing_apis.html)を参照してください。

## IBM API Connect の IBM App Connect Professional で作成した API の公開

このチュートリアルでは、{{site.data.keyword.apiconnect_full}} の IBM App Connect Professional で作成した REST API を公開して管理することができます。

### 前提条件
{: #prereq_pub_api_appconn}

このチュートリアルを完了するには、IBM App Connect Professional on Cloud と {{site.data.keyword.apiconnect_short}} の有効なアカウントが必要です。 使用する REST API ファイルがバージョン 2.0 の Swagger 仕様に準拠していることを確認します。 有効なファイル・フォーマットは、JSON と YAML です。

IBM App Connect Professional を使用すると、REST API を作成できます。それらの REST API は、統合を RESTful Web サービスとして公開するために使用できる特殊なアプリケーションであり、HTTP クライアントから呼び出すことができます。 API を作成したら、{{site.data.keyword.apiconnect_short}} を使用して公開および管理できます。
以下に、{{site.data.keyword.apiconnect_short}} で API を管理することの利点をいくつかリストします。

- API に対する呼び出しの数をモニターできる。
- API に対する呼び出しの数を制御できる。
- API の複数のバージョンを保守できる。

その他の利点については、[API の管理](managing_apis.html)を参照してください。
IBM App Connect Professional で REST API を作成し、それを {{site.data.keyword.apiconnect_short}} に公開するには、以下の手順を実行します。

1. IBM App Connect Professional を使用して REST API を作成します。
  - IBMid を使用して [App Connect Professional Web 管理コンソール ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://appconnect.ibmcloud.com/professional/){:new_window} にログインします。 IBM App Connect Professional Web 管理コンソールを使用して REST API を作成する作業を行う方法について詳しくは、IBM Knowledge Center の [About management console settings ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SS3LC4_7.5.2.0/com.ibm.wci.appliance.doc/About_the_WMC/consoleSettings.html){:new_window} を参照してください。
  - 「実動」タブが選択されていない場合は選択します。
  - ナビゲーション・パネルで**「リポジトリー」** >**「構成」**を選択します。
  - 「プロジェクト構成 (Project Configurations)」画面で、{{site.data.keyword.apiconnect_short}} に公開するプロジェクトを選択します。  公開しているプロジェクトの構成詳細が表示されます。
  - **「API Management にプッシュ (Push to API Management)」**を選択します。 
      **ヒント**: **「API Management にプッシュ (Push to API Management)」**ボタンは、インポートするプロジェクトのステータスが実行中またはデプロイ済みである場合にのみアクティブになります。 リンクが表示されない場合は、再生ボタンを選択してプロジェクトを開始します。
  - 「API Management にプッシュ (Push to API Management)」画面で、API 管理システムへの接続を作成するために、以下の情報を入力します。

  <table><caption>表 1. {{site.data.keyword.apiconnect_short}} に API を公開するための接続情報</caption>
  <thead>
  <tr>
  <th>フィールド名</th>
  <th>説明</th>
  </tr>
  </thead>
  <tbody>
  <tr><td>ホスト</td>
  <td>管理クラスター、サーバー、またはクラウドのアドレスのホスト名を指定します。 ほとんどの場合、{{site.data.keyword.Bluemix_notm}} ではこの項目は us.apiconnect.ibmcloud.com です。</td>
  </tr>
  <tr>
  <td>ポート</td>
  <td>管理クラスター、サーバー、またはクラウドのアドレスへの接続に必要なポート番号を指定します。</td>
  </tr>
  <tr><td>ユーザー ID</td>
  <td>管理クラスター、サーバー、またはクラウドのアドレスへのアクセスに使用する認証ユーザーの名前を指定します。 ほとんどの場合、これは {{site.data.keyword.Bluemix_notm}} へのログインに使用する IBMid です。</td>
  </tr>
  <tr><td>パスワード</td>
  <td>管理クラスター、サーバー、またはクラウドのアドレスへのアクセスに使用される認証パスワードを指定します。 ほとんどの場合、これは {{site.data.keyword.Bluemix_notm}} へのログインに使用する IBMid のパスワードです。</td>
  </tr>
  </tbody>
  </table>

2. **「組織のロード (Load Organizations)」**を選択して、ID とパスワードに関連付けられている組織のリストを取り込みます。

3. **「組織」**を選択して、使用可能な組織を 1 つプロジェクトに関連付けます。

4. **「APIM にプッシュ(Push to APIM)」**を選択して、**「OK」**を選択します。

5. **「閉じる」**を選択してウィンドウを閉じます。
デフォルト・ブラウザーで新しいブラウザー・タブが開き、API が表示されます。

IBM App Connect API を {{site.data.keyword.apiconnect_short}} に関連付けます。

#### Swagger API 定義のインポート

IBM App Connect で REST API プロジェクトに関連付けられている Swagger ファイルを {{site.data.keyword.apiconnect_short}} サービスにインポートするには、以下の手順を実行します。

1. {{site.data.keyword.apiconnect_short}} {{site.data.keyword.Bluemix_notm}} サービスにログインします。

1.  API Manager UI のタイトル・バーで、**「ナビゲート先」**>**「ドラフト」**を選択します。

2. メニュー・バーで、**「API」**を選択します。
「API」タブが開きます。

3. インポートされた API を選択して API Designer を開きます。

4. ナビゲーション・ウィンドウで**「アセンブル」**を選択します。
ポリシーのリストがナビゲーション・ウィンドウに表示されます。

5. 必要に応じて**「アセンブリーの作成」**を選択します。

6. **「呼び出し」**ポリシーをメインウィンドウのアセンブリーにドラッグして追加します。

7. メインウィンドウで**「呼び出し」**ポリシーを選択して、構成設定を変更します。

8. 次の情報を使用して、host/basePath を「URL」フィールドに構成します。

- **hostname**: 使用するクラウド・インスタンスに応じた設定。 この設定について詳しくは、[IBM App Connect Professional ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://provide.castiron.ibmcloud.com){:new_window} を参照してください。

- **basepath**: App Connect Professional オーケストレーションの httpReceive 要求ノートで指定するパス。

9. IBMid のユーザー名とパスワードを、App Connect Professional で使用する HTTP 基本認証の詳細に追加して保存します。

#### API のテスト

API をテストするには、以下の手順を実行します。

1. API の「アセンブル」タブで、「テスト」ボタン <img alt="「テスト」ボタン・アイコンを表示する画面キャプチャー" src="images/a_play_button.jpg" /> を選択します。
2. **「製品の再公開」**を選択します。
3. 「操作」を選択します。
4.  必須パラメーターを入力します。
5. **「呼び出し」**を選択します。
6. API から予期される応答があることを確認します。

API 定義がインポートされて統合されると、他の REST API 定義の場合と同様に API を管理し、制御できるようになります。API について詳しくは、[API の管理](managing_apis.html)を参照してください。


