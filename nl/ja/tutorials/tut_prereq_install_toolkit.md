---
copyright:
  years: 2017
lastupdated: "2017-10-31"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# API Connect ツールキットのインストール
**所要時間**: 15 分  
**スキル・レベル**: ビギナー  

## 必要なもの
1. Node.js
2. ノード・プロダクト・マネージャー (NPM)
3. {{site.data.keyword.apiconnect_full}} _Lite_

<table>
  <tr><td><b>Node.js</b>: スケーラブルなネットワーク・アプリケーションを作成して実行するために使用する非同期イベント・ドリブン型 JavaScript ランタイム
    <br>
    <b>ノード・プロダクト・マネージャー</b>: JavaScript のパッケージ・マネージャーとソフトウェア・レジストリー<br>
    <b>{{site.data.keyword.apiconnect_short}} _Lite_</b>: ラップトップで使用する無料版の {{site.data.keyword.apiconnect_short}}</td></tr>
  </table>  


## node.js のインストール
1. 以下の 2 つのソースのいずれかから node.js をダウンロードしてインストールします。
   * [https://nodejs.org/en/download/ ![外部リンクのアイコン](../../../icons/launch-glyph.svg "外部リンクのアイコン")](https://nodejs.org/en/download/){:new_window} (注: 最新バージョンではなく、ご使用のプラットフォームに該当する LTS バージョンをダウンロードしてください。そうしないと、エラーになる場合もあります。)
      **または**
   * [https://developer.ibm.com/node/sdk/v6/ ![外部リンクのアイコン](../../../icons/launch-glyph.svg "外部リンクのアイコン")](https://developer.ibm.com/node/sdk/v6/){:new_window}  

    _node.js をインストールすると、**npm** (ノード・パッケージ・マネージャー) もインストールされます_。

2.  Node.js をダウンロードしてインストールしたら、それが _PATH_ に存在することを確認します。
![](images/verify-path.png)  

3. **npm** を更新します。 コマンド・ラインで `npm install -g npm` と入力します。  
   **注:** npm `--engine-strict` や `npm config set engine-strict true` のように設定すると、インストールが完了しません。


4. インストールしたバージョンとパスを確認します。
![](images/screenshot_install_apic-1.png)  



## API Connect ツールキットと Microgateway のインストール
1. npm config を更新して、信頼されていない証明書の使用を許可します。  
   `npm config -g set strict-ssl false`  

2. **npm** から {{site.data.keyword.apiconnect_short}} ツールキットをインストールします。  
    `npm install -g apiconnect`

3. インストールしたバージョンを確認します。  
    `apic -v`

4. コマンド・ラインで `npm install -g microgateway` というコマンドを入力します。

ローカル・テスト・サーバーとして Microgateway を使用します。
