---

copyright:
  years: 2017
lastupdated: "2017-12-15"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# API の作成
{: #creating_apis}

デベロッパーズ・ツールキットをダウンロードし、コマンド・ライン・インターフェース (CLI) または API Designer を使用して、API を作成できます。

## デベロッパーズ・ツールキット CLI
{: #dev_tk_cli notoc}

デベロッパーズ・ツールキットで提供されるコマンド・ライン・インターフェースを使用して、API を {{site.data.keyword.apiconnect_long}} に公開することができます。
API を製品に含めた後にその製品を公開することで、API を公開します。 ローカル・ファイル・システムに YAML 定義ファイルを作成して検証することで、API と製品を定義します。 その後、ツールキットのコマンドを使用して、{{site.data.keyword.apiconnect_long}} と対話式に操作を実行できます。

## API Designer
{: #designer notoc}

API Designer は、デベロッパーズ・ツールキット内のオフラインのグラフィカル・ユーザー・インターフェースです。これは、API の作成および構成のための機能を提供します。
API Designer は、コマンド・ライン・インターフェースから edit コマンドを使用することで実行されます。 edit コマンドが使用されると、API Designer は、デフォルト・ブラウザーで開くか、そのコマンドを実行すると表示されるローカル・ホスト・ポートからアクセスできます。

## デベロッパーズ・ツールキットのインストール
{: #install_dev_tk}

### 前提条件
{: #prereq_install_dev_tk}

始めに、ツールキットを使用するマシンに [Node.js ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://nodejs.org/en/){:new_window} をインストールし、
`node` が `PATH` にあることを確認する必要があります。

デベロッパーズ・ツールキットをインストールすると、以下の項目がインストールされます。

- {{site.data.keyword.apiconnect_short}} コマンド・ライン・ツール
- {{site.data.keyword.apiconnect_short}} グラフィカル・エディター
- ローカル {{site.data.keyword.apiconnect_short}} Micro-gateway


1. ツールキットをインストールするには、管理者としてコマンド・プロンプトを開き、以下のコマンドを入力します。

    ```
    npm install -g apiconnect
    ```
    {: codeblock}

    **注:** インストール中に、`node-gyp` モジュールからエラーが表示されることがあります。 これらのエラーは、オプションの依存関係に由来するものであり、インストールは正常に完了します。

2. すべてのツールキット・コマンドの使用法に関するヘルプの要約を表示するには、以下のコマンドを入力します。

    ```
    apic
    ```
	{: codeblock}

3. いずれかのコマンドの使用法に関するヘルプを表示するには、`--help` オプションを使用します。
    以下に例を示します。

    ```
    apic validate --help
    ```
	{: codeblock}
	
## LoopBack コネクターのインストール
{: #install_lb_conn}

LoopBack データ・ソースを使用して、データベースなどのバックエンド・システム内のデータにアクセスするには、その前に、データ・ソース・コネクターをインストールする必要があります。 メモリー内のコネクターと E メール・コネクターは LoopBack に組み込まれているため、インストールする必要はありません。

### 前提条件
{: #prereq_install_lb_conn}

Oracle、DB2、および SQLLite の各コネクターでは、バイナリー拡張子をビルドしてインストールするために、C コンパイラー・ツールが必要です。 次の表に記述されているように、正確な要件はオペレーティング・システムによって異なります。

<table summary="" id="apic_028__table_pre_reqs" class="defaultstyle style-scope doc-content">
<caption>表 1. オペレーティング・システム固有のインストール要件</caption>
<thead>
<tr>
<th style="width: 33.3%" id="th_d70e208" class="thleft style-scope doc-content">Windows</th>
<th style="width: 33.3%" id="th_d70e210" class="thleft style-scope doc-content">Linux</th>
<th style="width: 33.3%" id="th_d70e212" class="thleft style-scope doc-content">MAC OS X</th>
</tr>
</thead>
<tbody >
<tr class="style-scope doc-content doc-tr-odd">
<td style="width: 33.3%" > [Microsoft .NET Framework 4 ![外部リンク・アイコン](../../icons/launch-glyph.svg "External link icon")](https://www.microsoft.com/en-us/download/details.aspx?id=17851)</td>
<td style="width: 33.3%">Python v2.7 (v3.x はサポートされません)</td>
<td style="width: 33.3%" > [Python Releases for Mac OS X ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.python.org/downloads/mac-osx/)</td>
</tr>
<tr><td style="width: 33.3%" > [Visual Studio ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.visualstudio.com/downloads/download-visual-studio-vs)</td>
<td style="width: 33.3%">
<code>make</code>
</td>
<td style="width: 33.3%" > [Xcode ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.apple.com/xcode/?cm_mc_uid=46449280653414622613810&amp;cm_mc_sid_50200000=1459433716)</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 33.3%" > [Python v2.7.10 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.python.org/downloads/release/python-2710/)</td>
<td style="width: 33.3%">C/C++ コンパイラー・ツールチェーン (例えば、GCC バージョン 4.2 以降)。 </td>
<td style="width: 33.3%" >&nbsp;</td>
</tr>
<tr><td style="width: 33.3%" > [Microsoft Windows SDK for Windows 7 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.microsoft.com/en-gb/download/details.aspx?id=8279)</td>
<td style="width: 33.3%">Debian または Debian 派生ディストリビューション (Ubuntu、Mint など) では、以下のコマンドを使用します。
<pre class="codeblock style-scope doc-content"><code>apt-get install build-essential</code></pre>
</td>
<td style="width: 33.3%" >&nbsp;</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 33.3%" >npm バージョン 3。次の注を参照してください。</td>
<td style="width: 33.3%">&nbsp;</td>
<td style="width: 33.3%" >&nbsp;</td>
</tr>
</tbody>
</table>

**注:** Windows インストール済み環境の場合:

- Visual Studio Enterprise を購入しない場合は、Visual Studio Community を使用してください。 インストーラーを実行し、「プログラミング言語」の下の「Visual C++」にチェック・マークを付けて、デフォルトのインストール場所を受け入れます。

- Node.js およびネイティブ・モジュールの 64 ビット・ビルドの場合は、Windows&trade; 7 の 64 ビット SDK も必要です。 インストールが失敗した場合は、最初にインストールした C++ 2010 x64&amp;x86 再配布可能パッケージをアンインストールしてみてください。 64 ビット・コンパイラーがインストールされていないというエラーが表示された場合は、Windows&trade; SDK 7.1 用のコンパイラー更新も必要である可能性があります。
- 以下のコマンドを入力して、npm バージョン 3 をインストールします。
  ```
  npm install -g npm
  ```
  {: codeblock}
  次に、以下のコマンドを入力して、npm コマンドが正しいバージョンを使用していることを確認します。
  ```
  npm -v
  ```
  {: codeblock}
  表示されたバージョンが 3.x.x ではない場合は、システム PATH を編集して、`C:\Users\username\AppData\Roaming\npm` が、それ以外のすべてのエントリーを置き換えるようにします


1. **オプション**:
API Designer を使用している場合は、新しいシェル・ウィンドウを開きます。

2. オペレーティング・システムに必要なコンパイラー・ツールのインストールが完了したら、プロジェクトのルート・ディレクトリーで以下のコマンドを入力して、コネクターをインストールします。

```
npm install --save <connector-package>
```
{: codeblock}
ここで、`<connector-package>` は、LoopBack コネクターの npm パッケージの名前 (次の表を参照) です。

<table summary="" id="apic_connectors_table_pre_reqs" class="defaultstyle style-scope doc-content">
<caption>表 3. LoopBack コネクター</caption>
<thead>
<tr class="style-scope doc-content doc-tr-even">
<th style="width: 50%" id="th_new_d70e1489" class="thleft style-scope doc-content">データ・ソース</th>
<th style="width: 50%" id="th_new_d70e1491" class="thleft style-scope doc-content">コネクター・パッケージ</th>
</tr>
</thead>
<tbody>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Cloudant</td>
<td style="width: 50%">loopback-connector-cloudant</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">dashDB</td>
<td style="width: 50%">loopback-connector-dashdb</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">DB2</td>
<td style="width: 50%">loopback-connector-db2</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">DB2 for zOS</td>
<td style="width: 50%">loopback-connector-db2z</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Microsoft SQL Server</td>
<td style="width: 50%">loopback-connector-mssql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">MongoDB</td>
<td style="width: 50%">loopback-connector-mongodb</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">MySQL</td>
<td style="width: 50%">loopback-connector-mysql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">Oracle</td>
<td style="width: 50%">loopback-connector-oracle</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">PostgreSQL</td>
<td style="width: 50%">loopback-connector-postgresql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">SOAP Web サービス</td>
<td style="width: 50%">loopback-connector-soap</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">REST Web サービス</td>
<td style="width: 50%">loopback-connector-rest</td>
</tr>
</tbody>
</table>

## CLI を使用した LoopBack API の作成
{: #create_lb_api}

以下の手順では、コマンド・ライン・インターフェースを使用して LoopBack&reg; API を作成する方法を説明します。


### 前提条件
{: #prereq_create_lb_api}

始めに、使用するカタログのカタログ ID を手許に用意します。 カタログ ID を取得するには、以下の手順を実行します。  

1. {{site.data.keyword.apiconnect_short}} の**「ダッシュボード」**を開きます。

2. 使用するカタログについて、**「カタログ ID の表示」**アイコン <img alt="カタログ ID を表示するためのチェーン・リンク・アイコン" src="images/chain_link_icon.png"> をクリックします。

3. カタログ ID をコピーします。 以下に例を示します。  
  ```
  apic config:set catalog=apic-catalog://<region>.apiconnect.ibmcloud.com/orgs/<username_string>-dev/catalogs/<catalog>
  ```
  {: codeblock}
    ここで、

    - `<region>` は、{{site.data.keyword.Bluemix_notm}} 地域です。

    - `<username_string>` は、記号を含まない {{site.data.keyword.Bluemix_notm}} 組織 ID です。 例えば、`joe@mycompany.com` は、`joemycompanycom` のようになります。

    - `<catalog>` は、カタログの名前です  

CLI で LoopBack API を作成する場合は、以下の手順を実行します。

1. プロジェクトを作成するには、コマンド・ラインを開き、以下を入力します。
  ```
  apic loopback
  ```
  {: codeblock}

2. 後続のプロンプトで、アプリケーションの名前を尋ねられます。 名前を入力して、**「Enter」**キーを押します。
  ```
  ? What's the name of your application? (<application name>)
  ```
    
    ツールで、プロジェクトを作成するディレクトリーの名前を入力するように求めるプロンプトが出されます。
    ```
    ? Enter name of the directory to contain the project: (<project directory name>)
    ```
    
3. **Enter** を押して前に入力した名前を使用するか、新しい名前を入力してから **Enter** を押します。 以下のように、ツールで、作成するアプリケーションの種類を選択するように求めるプロンプトが出されます。
```
? What kind of application do you have in mind? (Use arrow keys)
  empty-server (An empty LoopBack API, without any configured models or datasources)
> hello-world (A project containing a basic working example, including a memory database)
```

4. 使用するアプリケーションを選択して、**Enter** を押します。
ツールで、プロジェクト・ディレクトリーが作成され、そこにいくつかのディレクトリーとファイルが追加される間、いくつかのメッセージが表示されます。
また、`npm install` が実行され、`package.json` での指定に従ってすべてのプロジェクト依存関係がインストールされます。
この処理にはある程度時間がかかることがあります。

5. モデルを作成するには、その前に、現行作業ディレクトリーがプロジェクトの最上位ディレクトリーになっていることを確認する必要があります。 これを行うには、以下のコマンドを入力します。
    ```
    cd <project directory name>
    ```
    {: codeblock}

6. モデルを作成するには、以下のコマンドを入力します。
    ```
    apic create --type model
    ```
    {: codeblock}

    ツールで、モデルの名前を入力するように求めるプロンプトが出されます。

    ```
    ? Enter the model name:
    ```

7. モデルの名前を入力します。
    一般的に、モデル名では任意の英数字、ダッシュ、および下線を使用できます。
    プロジェクトに追加したすべてのデータ・ソースがリストされており、ツールにより、使用するデータ・ソースを選択するように求める以下のようなプロンプトが出されます。
    ```
    ? Select the data-source to attach item to: (Use arrow keys)
    ```

8. 使用するデータ・ソースを選択して、**「Enter」**キーを押します。 以下のように、ツールで、モデルの基本クラスを選択するように求めるプロンプトが出されます。
    ```
    ? Select model's base class (Use arrow keys)
       Model
    < PersistedModel
      ACL
      AccessToken
      Application
      Change
      Checkpoint
    (Move up and down to reveal more choices)
    ```
    各オプションについて詳しくは、[Using built-in models ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://loopback.io/doc/en/lb3/Using-built-in-models.html){:new_window} を参照してください。

9. 基本クラスを選択して、**「Enter」**キーを押します。 ツールで、モデルの REST API を公開するかどうかを選択するように求められます。
```
? Expose branch via the REST API? (Y/n)
```
REST を介してモデルを公開した場合、REST エンドポイントを介してすべての標準的な作成、読み取り、更新、および削除の操作が使用可能になります。

10. 選択項目を入力して、**「Enter」**キーを押します。
REST を介してモデルを公開するように選択すると、ツールから、モデル名の複数形を入力するように求められます。
```
? Custom plural form (used to build REST URL):
```

11. **「Enter」**キーを押して、デフォルトの標準的な英文法による複数形化を使用します。
ツールでは、サーバー専用モデルを作成するのか、サーバーとクライアントの LoopBack API の両方で使用できる共通モデルを作成するのかを選択するように求めるプロンプトが出されます。
```
? Common model or server only? (Use arrow keys)
```

12. 矢印キーを使用して選択を行い、**「Enter」**キーを押します。
以下のように、ツールで、プロパティーをモデルに追加するように求めるプロンプトが出されます。
```
Let's add some branch properties now.
Enter an empty property name when done.
? Property name:
```

13. プロパティー名を入力します。
以下のように、ツールで、プロパティーのデータ型を選択するように求めるプロンプトが出されます。
```
? Property type: (Use arrow keys)
> string
  number
  boolean
  object
  array
  date
  buffer
```

14. ストリング・タイプを選択して、**「Enter」**キーを押します。
ツールで、プロパティーが必須かどうかを選択するように求められます。
```
? 必須 (y/N)
```

15. `y` または `n` を入力して、**「Enter」**キーを押します。
以下のように、ツールで、別のプロパティーを追加するように求めるプロンプトが出されます。
```
Let's add another branch property.
Enter an empty property name when done.
? Property name:
```

16. 必要に応じて、別のプロパティー名を追加します。 それ以上のプロパティーは必要ない場合は、**「Enter」**キーを押して、モデルの追加を終了します。

デフォルトでは、LoopBack プロジェクトは、開発やテストに適した、メモリー内のデータ・ソースを構成済みで出荷されます。 しかし、ある時点で、データベース・サーバーなどの実際のデータ・ソースにモデルを接続することが必要になります。 データ・ソースを追加するには、以下の手順を実行します。

1. 以下のコマンドを入力します。
```
apic create --type datasource
```
{: codeblock}
ツールで、データ・ソースの名前を入力するように求めるプロンプトが出されます。
```
? Enter the data-source name:
```

2. データ・ソースの名前を入力します。  データ・ソース名では任意の英数字、ダッシュ、および下線を使用できます。 以下のように、ツールで、データ・ソースで使用するコネクターを選択するように求めるプロンプトが出されます。
```
? Select the connector for myds: (Use arrow keys)
> In-memory db (supported by StrongLoop)
  Email (supported by StrongLoop)
  MySQL (supported by StrongLoop)
  PostgreSQL (supported by StrongLoop)
  Oracle (supported by StrongLoop)
  Microsoft SQL (supported by StrongLoop)
  MongoDB (supported by StrongLoop)
(Move up and down to reveal more choices)
```

3. 矢印キーを使用して、使用するコネクターを選択し、**「Enter」**キーを押します。
ツールにより、データ・ソースがプロジェクトに追加されます。

4. ホスト、ポート、ユーザー、パスワード、およびデータベースの資格情報を入力します。
LoopBack コネクターのインストールを求めるプロンプトがツールによって出されます。
```
Install loopback-connector-<connector>?
```

5. `Yes` を入力します。
ツールにより、コネクターがインストールされます。

注: Oracle コネクターを選択した場合、Oracle アプリを開始するには、{{site.data.keyword.Bluemix_notm}} で環境変数を設定する必要があります。 これを行うには、以下の手順を実行します。

1. {{site.data.keyword.Bluemix_notm}} UI で、**「コンピュート」**を選択します。

2. 「CF アプリケーション」で、使用するアプリケーションを選択します。

3. **「ランタイム」**をクリックします。

4. **「環境変数」**を選択します。

5. 「ユーザー定義」セクションで、**「追加」**をクリックします。

6. **「名前」**フィールドに、`LD_LIBRARY_PATH` と入力します。

7. **「値」**フィールドに、`$LD_LIBRARY_PATH:/home/vcap/app/node_modules/instantclient` と入力します。

8. **「保存」**をクリックします。

### LoopBack プロジェクトのテスト
{: #test_lb_proj}

LoopBack プロジェクトをテストするには、以下の手順を実行します。

1. **オプション**: 現行作業ディレクトリーがプロジェクトの最上位ディレクトリーになっていることを確認します。 以下のコマンドを入力します。
```
cd <loopback-project-dir>
```
ここで、`<loopback-project-dir>` は、プロジェクトが入っているディレクトリーの名前です。
2. 以下のコマンドを入力します。
```
apic start
```
これにより、LoopBack プロジェクト (API) および Micro Gateway がローカルで実行されます。 以下のメッセージが表示されます。
```
Waiting for loopback-project to complete deployment.
Waiting for loopback-project-gw to complete deployment.
Service loopback-project (id 1) started on port 4001
Service loopback-project-gw (id 2) started on port 4002
```
ここで、`<loopback-project>` は、プロジェクトが入っているディレクトリーの名前です。


その後、例えば `curl` を使用して、任意の API エンドポイントをテストできます。
Web ブラウザーを使用して API をロードする場合、ブラウザーで `http://localhost:4001` を開きます。 デフォルトの LoopBack (空または hello-world) プロジェクトの場合、以下のように表示されます。
```
{"started":"2016-03-07T22:24:55.322Z","uptime":35.839}
```

### CLI から {{site.data.keyword.Bluemix_notm}} への LoopBack アプリケーションの公開
{: #pub_lb_app_cli}

コマンド・ラインから {{site.data.keyword.Bluemix_short}} に LoopBack アプリケーションを公開するには、以下の手順を実行します。

1. 以下のコマンドを入力して、Loopback プロジェクト・ディレクトリー内にいることを確認します。
```
cd <loopback-project-dir>
```
2. 以下のコマンドを入力して、{{site.data.keyword.apiconnect_short}} と {{site.data.keyword.Bluemix_notm}} にログインします。
```
apic login --server  <region>.apiconnect.ibmcloud.com -u <username> -p <password>
```
ここで、
  * `<username>` は、{{site.data.keyword.apiconnect_short}} 組織 ID です。
  * `<password>` は、{{site.data.keyword.apiconnect_short}} のパスワードです。
3. スペース・バーを押すと、**「ワンタイム・パスコード」**ブラウザー・ページが自動的に開きます。
4. **「再生成」**をクリックして、ワンタイム・パスコードをコピーします。
5. CLI に戻り、パスコードを貼り付けてログインを完了します。 以下のメッセージが表示されます。
```
Logged into <region>.apiconnect.ibmcloud.com successfully
```
6. 以下のコマンドを入力します。
```
apic organizations -s <region>.apiconnect.ibmcloud.com
```
ここで、
  * `<region>` は、{{site.data.keyword.Bluemix_notm}} 地域です。 以下に例を示します。
  * {{site.data.keyword.Bluemix_notm}} ロンドンを使用している場合は `eu`。
  * {{site.data.keyword.Bluemix_notm}} ダラスを使用している場合は `us`。
  * {{site.data.keyword.Bluemix_notm}} シドニーを使用している場合は `au`。

  ご使用の地域が分からない場合は、メニュー・バーの「{{site.data.keyword.avatar}}」アイコン <img src="images/i-avatar-icon.svg" alt="アバター・アイコン"/> をクリックして「アカウントとサポート」ウィジェットを開くと、地域フィールドで確認できます。
7. 以下のコマンドを入力して、アプリケーションを {{site.data.keyword.Bluemix_notm}} に公開します。
```
apic apps:publish –a <app> -o <org> -s <region>.apiconnect.ibmcloud.com
```
ここで、
  * `<app>` は、アプリの名前です。
  * `<org>` は、{{site.data.keyword.Bluemix_notm}} 組織の名前です。
  * `<region>`は、{{site.data.keyword.Bluemix_notm}} 地域です。
次の出力が返されます。
  ```
  ...preparing project
  ...building package for deploy
  ...uploading package
  Runtime published successfully.
  Management URL: https://new-console.stage1.ng.bluemix.net/apps/3aa7087d-b454-4e13-bbc5-8228ebe00eef
  API target urls: apiconnect-3aa7087d-b454-4e13-bbc5-8228ebe00eef.pszetousibmcom-dev.apic.stage1.mybluemix.net
  API invoke tls-profile: client:Loopback-client
  ```

8. 次に、公開時に返された値を使用して、製品定義を変更する必要があります。 これを行うには、次の手順を実行します。

    1. API Designer UI で、**「API」**をクリックします。
    2. 「API」を選択します。
    3. **「アセンブル」**をクリックします。
    4. アセンブリー・エディターで、**「ポリシーのフィルター」**アイコンをクリックします。
    5. **「DataPower Gateway ポリシー」**を選択します。
    6. **「呼び出し」**をダブルクリックします。
    7. ステップ 7 で取得した値を使用して、以下のフィールドを更新します。
        - **呼び出し URL**: API ターゲット URL を挿入します。 セキュア・プロトコル HTTPS を指定する必要があります。 以下に例を示します。
        ```
        https://apiconnect-33e7b062-092b-4227-af97-047499dab2e7.<Bluemix org>-<Bluemix space>.apic.<domain name>$(request.path)
        ```
        この値をメモしていなかった場合は、ステップ 7 で返された管理 URL にアクセスして取得できます。また、{{site.data.keyword.Bluemix_notm}} にログインし、アプリ情報を確認して取得することもできます。
        - **TLS プロファイル**: 「API 呼び出し TLS プロファイル」を挿入します。 以下に例を示します。
        ```
        client:Loopback-client
        ```
    8. **「保存」**をクリックして API を保存します。

## API Designer を使用した LoopBack API の作成
{: #create_lb_api_design}

以下の手順では、API Designer を使用して LoopBack API を作成する方法を説明します。
{:shortdesc}

### 前提条件
{: #prereq_create_lb_api_design}

**注**: 以下の手順は、最新バージョンのデベロッパーズ・ツールキットを使用することを想定しています。 最新バージョンを確認するには、[npm ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.npmjs.com/package/apiconnect){:new_window} パッケージのページを参照してください。

最初に、CLI を使用して LoopBack プロジェクトを作成する必要があります。 これを行うには、以下の手順を実行します。

1. プロジェクトを作成するには、コマンド・ラインを開き、以下を入力します。
  ```
  apic loopback
  ```
  {: codeblock}

2. 後続のプロンプトで、アプリケーションの名前を尋ねられます。 名前を入力して、**「Enter」**キーを押します。
  ```
  ? What's the name of your application? (<application name>)
  ```
    
    ツールで、プロジェクトを作成するディレクトリーの名前を入力するように求めるプロンプトが出されます。
    ```
    ? Enter name of the directory to contain the project: (<project directory name>)
    ```
    
3. **Enter** を押して前に入力した名前を使用するか、新しい名前を入力してから **Enter** を押します。 以下のように、ツールで、作成するアプリケーションの種類を選択するように求めるプロンプトが出されます。
```
? What kind of application do you have in mind? (Use arrow keys)
  empty-server (An empty LoopBack API, without any configured models or datasources)
> hello-world (A project containing a basic working example, including a memory database)
```

4. 使用するアプリケーションを選択して、**Enter** を押します。
ツールで、プロジェクト・ディレクトリーが作成され、そこにいくつかのディレクトリーとファイルが追加される間、いくつかのメッセージが表示されます。
また、`npm install` が実行され、`package.json` での指定に従ってすべてのプロジェクト依存関係がインストールされます。
この処理にはある程度時間がかかることがあります。

5. モデルを作成するには、その前に、現行作業ディレクトリーがプロジェクトの最上位ディレクトリーになっていることを確認する必要があります。 これを行うには、以下のコマンドを入力します。
```
cd <project directory name>
```

**注**: 現行作業ディレクトリーをプロジェクトの最上位のディレクトリーにすると、API Designer を開いたときに、モデルやデータ・ソースを追加するためのオプションが選択可能になります。 ディレクトリーを変更せずに API Designer を開いた場合は、モデルやデータ・ソースを追加できません。

API Designer を開くには、以下のステップを実行します。
1. コマンド・ラインを開き、以下を入力します。
```
apic edit
```
    しばらくしてから、以下のメッセージが表示されます。
    ```
    Express server listening on http://127.0.0.1:9000
    ```
    API Designer がデフォルトの Web ブラウザーで開きます。

2. ログイン・ページで、{{site.data.keyword.Bluemix_notm}} ID とパスワードを入力します。 **「サインイン」**をクリックします。

3. **「モデル」**をクリックします。

4. **「追加」**をクリックします。 LoopBack の**「モデル」**ウィンドウが開きます。

5. モデル名を入力します。
一般的に、モデル名では任意の英数字、ダッシュ、および下線を使用できます。

6. **「新規」**をクリックします。

7. モデル・エディター・ページで、「プロパティー」に移動して、**「追加」**をクリックします。

8. プロパティー名を入力し、タイプを選択します。

9. モデルに関するプロパティーの入力が終了したら、**「保存」**をクリックします。

デフォルトでは、空の LoopBack プロジェクトには、データ・ソースは定義されていません。 データ・ソースを定義するには、以下のステップを実行します。
1. **「データ・ソース」**をクリックします。

2. **「追加」**アイコンをクリックします。
新しい LoopBack の**「モデル」**ウィンドウが開きます。

3. データ・ソース名を入力します。 データ・ソース名では任意の英数字、ダッシュ、および下線を使用できます。

4. **「新規」**をクリックします。
当該データ・ソースがデータ・ソースのリストに表示されます。また、エディターにより、`server/datasources.json` ファイルが新しいデータ・ソースの設定で更新されます。

5. データ・ソースをクリックして、その設定を確認します。

6. コネクターの設定を、必要なコネクターに変更します。

7. API Designer を開始したコンソールに戻り、以下のコマンドを入力して、コネクターをインストールします。
```
npm install --save <connector-package>
```
    ここで、`<connector-package>` は、選択した LoopBack コネクターの npm パッケージの名前です。 コネクター・パッケージのリストについては、以下の表を参照してください。

**注:** メモリー内コネクターと E メール・コネクターは LoopBack に組み込まれているため、インストールする必要はありません。

<table>
<caption>表 3. LoopBack コネクター</caption>
<thead>
<tr class="style-scope doc-content doc-tr-even">
<th style="width: 50%" id="3rd_d70e1489" class="thleft style-scope doc-content">データ・ソース</th>
<th style="width: 50%" id="3rd_d70e1491" class="thleft style-scope doc-content">コネクター・パッケージ</th>
</tr>
</thead>
<tbody>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Cloudant</td>
<td style="width: 50%">loopback-connector-cloudant</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">dashDB</td>
<td style="width: 50%">loopback-connector-dashdb</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">DB2</td>
<td style="width: 50%">loopback-connector-db2</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">DB2 for zOS</td>
<td style="width: 50%">loopback-connector-db2z</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Microsoft SQL Server</td>
<td style="width: 50%">loopback-connector-mssql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">MongoDB</td>
<td style="width: 50%">loopback-connector-mongodb</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">MySQL</td>
<td style="width: 50%">loopback-connector-mysql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">Oracle</td>
<td style="width: 50%">loopback-connector-oracle</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">PostgreSQL</td>
<td style="width: 50%">loopback-connector-postgresql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">SOAP Web サービス</td>
<td style="width: 50%">loopback-connector-soap</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">REST Web サービス</td>
<td style="width: 50%">loopback-connector-rest</td>
</tr>
</tbody>
</table>

詳しくは、[LoopBack Documentation - Building a connector ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://loopback.io/doc/en/lb3/Defining-data-sources.html){:new_window} を参照してください。

**注:** Oracle コネクターを選択した場合、Oracle アプリを開始するには、{{site.data.keyword.Bluemix_notm}} で環境変数を設定する必要があります。 これを行うには、以下の手順を実行します。

1. {{site.data.keyword.Bluemix_notm}} UI で、**「コンピュート」**を選択します。

2. 「CF アプリケーション」で、使用するアプリケーションを選択します。

3. **「ランタイム」**をクリックします。

4. **「環境変数」**を選択します。

5. 「ユーザー定義」セクションで、**「追加」**をクリックします。

6. **「名前」**フィールドに、`LD_LIBRARY_PATH` と入力します。

7. **「値」**フィールドに、`$LD_LIBRARY_PATH:/home/vcap/app/node_modules/instantclient` と入力します。

8. **「保存」**をクリックします。

LoopBack プロジェクトをテストするには、以下の手順を実行します。
1. **「サーバーの開始 (Start the servers)」**アイコンをクリックします。
以下のメッセージが表示されます。
```
http://localhost:<4001/>Running
```
プロジェクトの構成や他のプロセスが実行中かどうかによって、表示されるポート番号が異なる場合があります。

2. **「localhost:4001」**をクリックして、API ルート・エンドポイントを表示します。 デフォルトの LoopBack (空または hello-world) プロジェクトの場合、以下のように表示されます。
```
{"started":"2017-03-07T22:24:55.322Z","uptime":35.839}
```

次に、製品を作成する必要があります。 詳しくは、[製品の作成](managing_products.html#create_product)を参照してください。**ヒント**: 新しいコマンド・プロンプトを開始する際には、必ず、現行作業ディレクトリーがプロジェクトの最上位ディレクトリーになっていることを確認する必要があります。 これを行うには、以下のコマンドを入力します。
```
cd <project directory name>
```

## デベロッパーズ・ツールキットのアンインストール
{: #uninstall_dev_tk}

### 前提条件
{: #prereq_uninstall_dev_tk}

始めに、以下のコマンドを入力して、ローカルで実行されているアプリをすべて停止する必要があります。
```
apic stop --all
```

デベロッパーズ・ツールキットをアンインストールするには、以下の手順を実行します。

1. 以下のコマンドを入力します。
```
npm rm -g apiconnect
```
{: codeblock}

2. npm キャッシュをクリアします。
```
npm cache clean
```
{:codeblock}
  
Windows を使用している場合:

3. `C:\Users\username\AppData\Local\Temp` 内で、名前が `npm-` で始まるすべてのファイルを削除します
4. ディレクトリー `<home_dir>\.apiconnect` を削除します。`<home_dir>` は、以前にツールキットをインストールしたときに使用したユーザー・アカウントのホーム・ディレクトリーです。
