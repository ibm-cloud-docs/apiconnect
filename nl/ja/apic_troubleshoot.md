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

# トラブルシューティング
{: #troubleshoot}

{{site.data.keyword.Bluemix_notm}} 上での {{site.data.keyword.apiconnect_long}} の使用についての一般的なトラブルシューティングに関する質問の答えを以下に示します。
{:shortdesc}

## API Connect {{site.data.keyword.Bluemix_notm}} サービスを追加する場合はユーザー名とパスワードが必要

{{site.data.keyword.Bluemix_notm}} ダッシュボードにサービスを追加した後、そのサービスを開こうとすると、ユーザー名とパスワードが求められます。 

### 症状
{: #ts_sym_usernamepw}

新しい {{site.data.keyword.apiconnect_short}} を開くときに {{site.data.keyword.Bluemix_notm}} サービスに直接アクセスする代わりに、API Manager へのログインが求められます。

### 原因
{: #ts_cause_usernamepw}

ブラウザーが Cookie をブロックするよう設定されているか、レベルが {{site.data.keyword.apiconnect_notm}} の要求するレベルより厳しく設定されています。

### 解決策
{: #ts_res_usernamepw}

ブラウザー設定で、Cookie を使用可能にするか、{{site.data.keyword.Bluemix_notm}} サービスが開くまで Cookie の許可レベルを上げます。

## デベロッパーズ・ツールキットをインストールできない

API Connect サービスをプロビジョンした後、デベロッパーズ・ツールキットのインストールを試みますが、インストールが失敗します。

### 症状
{: #ts_sym_noinstalltk}

デベロッパーズ・ツールキットのインストール中に、次のエラーが表示されます。
```
npm ERR! Error: EACCES, mkdir '/usr/local/lib/node_modules/apiconnect'
...
npm ERR! Please try running this command again as root/Administrator
...
```

### 原因
{: #ts_cause_noinstalltk}

ファイルまたはディレクトリーの作成に必要な権限を持っていません。

### 解決策
{: #ts_res_noinstalltk}

指定されたディレクトリーの権限を変更するか、`sudo` を使用してコマンドを実行します。 ローカル開発システムで、次のようにディレクトリーの権限を修正することをお勧めします。
```
sudo chown -R $USER /usr/local
```
{:codeblock}

このコマンドは、ユーザー・アカウントを `/usr/local` ディレクトリーの所有者にします。 これで、ノードのインストールや、npm を使用したグローバルでのパッケージのインストールに、sudo を使用する必要がなくなります。 
    **注:** ディレクトリーの所有権の変更は、ローカル開発システムの場合にのみ適切です。 これをサーバー・システムで行わないでください。

また、以前の  `chown` コマンドを `/usr/bin` ディレクトリーで使用しないでください。使用すると、システムに重大な構成ミスが発生する可能性があります。

`sudo` を使用する必要がある場合は、次のコマンドを使用します。
```
sudo npm install -g --unsafe-perm install apiconnect
```
{:codeblock}

## Windows にデベロッパーズ・ツールキットをインストールできない

{{site.data.keyword.apiconnect_short}} サービスをプロビジョンした後、デベロッパーズ・ツールキットのインストールを試みますが、インストールが失敗します。

### 症状
{: #ts_sym_noinstalltk_path}

Windows 上でデベロッパーズ・ツールキットのインストールを試みており、*パスは 248 文字未満にしてください (path should be less than 248 characters)* というエラー・メッセージを受け取ります。

### 原因
{: #ts_cause_noinstalltk_path}

Windows システムには最大パス長さがあり、深いレベルのフォルダー内のすべての依存関係をインストールしようとすると、この最大パス長さを超えます。

### 解決策
{: #ts_res_noinstalltk_path}

この問題は、以下のいずれかの方法で修正できます。

- 正しいバージョンの Node.js がインストールされていることを確認します。 詳しくは、[デベロッパーズ・ツールキットのインストール](creating_apis.html)を参照してください。

- プログラムをアップグレードする必要があった場合は、再度インストールを試みます。

それでもうまくいかない場合は、`C:/program files/nodejs/bin/node_modules...` フォルダーより高いレベルで {{site.data.keyword.apiconnect_short}} をインストールします。 最上位レベルのディレクトリーでインストールすれば、このエラーは表示されません。

## Mac OS X 上でデベロッパーズ・ツールキットをインストールできない

{{site.data.keyword.apiconnect_short}} サービスをプロビジョンした後、デベロッパーズ・ツールキットのインストールを試みますが、インストールが失敗します。

### 症状
{: #ts_sym_noinstalltk_mac}

デベロッパーズ・ツールキットのインストール中に、次のエラーが表示されます。
```
Agreeing to the Xcode/iOS license requires admin
privileges, please re-run as root via sudo
```

### 原因
{: #ts_cause_noinstalltk_mac}

最近 Xcode をアップグレードまたはインストールして、使用許諾にまだ同意していません。

### 解決策
{: #ts_res_noinstalltk_mac}

1. 以下のコマンドを入力して、Xcode のライセンスを検証します。
```
sudo xcode-select
```
{:codeblock}

2. デベロッパーズ・ツールキットを再インストールします。


## Ubuntu にデベロッパーズ・ツールキットをインストールできない

{{site.data.keyword.apiconnect_short}} サービスをプロビジョンした後、デベロッパーズ・ツールキットのインストールを試みますが、インストールが失敗します。

### 症状
{: #ts_sym_noinstalltk_ubu}

デベロッパーズ・ツールキットのインストール中に、次のエラーが表示されます。
```
sqlite3@3.1.1 install /usr/local/lib/node_modules/strong-pm/node_modules/minkelite/node_modules/sqlite3 
node-pre-gyp install --fallback-to-build 
/usr/bin/env: node: No such file or directory 
npm WARN This failure might be due to the use of legacy binary "node" 
npm WARN For further explanations, please read /usr/share/doc/nodejs/README.Debian 
npm ERR! weird error 127 
npm ERR! not ok code 0
```

### 解決策
{: #ts_res_noinstalltk_ubu}

問題を解決するには、以下のコマンドを入力します。
```
$ update-alternatives --install /usr/bin/node node /usr/bin/nodejs 99
```

## npm のインストールの失敗をデバッグできない

デベロッパーズ・ツールキットをインストールする手順に従って、npm のインストールに失敗。

### 症状
{: #ts_sym_npmfail}

npm のインストールが失敗し、デバッグに役立つ情報も提供されません。

### 解決策
{: #ts_res_npmfail}

インストールが失敗すると、npm はエラーが見つかった場所を示すための行を `npm-debug.log</filepath>` ファイルに追加します。 `npm-debug.log` ファイルを使用して原因を判断します。

## API Designer を開けない

コマンド `apic edit` を入力しても、API Designer が開きません。

### 症状
{: #ts_sym_noopenapid}

コマンドを入力しても API Designer のインスタンスが開かず、以下のメッセージが表示されます。
```
apic edit
```
以下のメッセージが表示されます。
```
<time stamp>. 329Z ERROR apiConnect: listen EADDRINUSE <ip address>:9000
```

### 原因
{: #ts_cause_noopenapid}

別のコマンド・ウィンドウから API Designer のインスタンスを既に開始済みです。

### 解決策
{: #ts_res_noopenapid}

この問題を修正するには、以下の手順での説明に従って、他方のコマンド・ウィンドウを閉じる必要があります。

1. 他方のコマンド・ウィンドウで、**Ctrl + C** を押します。

2. 以下のメッセージが表示されます。
```
Terminate Batch job (Y/N)?
```

3. `Y` を入力して、Enter キーを押します。

## 製品の請求情報を構成できない

請求情報の一部が構成に使用できないか、実動にコミットできません。 

### 症状
{: #ts_sym_nobill}

  - 製品の「管理」セクションを確認すると、「請求」タブが表示されていません。
  - 請求情報を指定して製品を公開しようとすると、エラーが表示されます。 

### 原因
{: #ts_cause_nobill}

請求情報を使用可能にするには、正しい {{site.data.keyword.apiconnect_short}} アカウントと権限を持っている必要があります。

## 製品で請求プランをサブスクライブできない

Stripe では、各利用者が指定できるサブスクリプションが最大 25 個に制限されています。 この制限を超えていないことを確認してください。 超えている場合は、別のサブスクリプションを解除した場合にのみ、このサブスクリプションを追加できます。

### 症状
{: #ts_sym_nosubscribe}

他のプランは構成できるのに、請求のあるプランにサブスクライブしようとするとエラーが表示されます。

### 原因
{: #ts_cause_nosubscribe}

Stripe のクレジット・カード処理サービスでは、1 つのアカウントにつき最大で 25 のサブスクリプションが可能です。

### 解決策
{: #ts_res_nosubscribe}

{{site.data.keyword.Bluemix_notm}} {{site.data.keyword.apiconnect_short}} サービスのエンタープライズ・レベルのアカウントを持ち、インスタンスが 25 より少ないことを確認します。 サービスの最大数になっている場合は、サービスを解除します。

## API Connect に関するヘルプとサポートの入手

{{site.data.keyword.apiconnect_short}} を使用しているときに問題や疑問が生じた場合は、フォーラムで情報を検索したり、質問したりすると役に立ちます。 また、サポート・チケットを開くことができます。

フォーラムを使用して質問する場合は、{{site.data.keyword.Bluemix_notm}} の開発チームの目に触れるように、質問にタグを付けます。 

- {{site.data.keyword.apiconnect_short}} によるアプリケーションの開発またはデプロイに関して技術的な質問がある場合は、Stack Overflow に質問を投稿し、質問に「ibm-cloud」と「api connect」のタグを付けてください。

- サービスおよび概説の指示に関する質問については、IBM DeveloperWorks dW Answers フォーラムを使用してください。 「ibm cloud」と「api connect」のタグを付けてください。
フォーラムの使用法の詳細については、ヘルプの入手を参照してください。 

IBM サポート・チケットをオープンする方法、サポート・レベルとチケットの重大度については、サポートへのお問い合わせを参照してください。



