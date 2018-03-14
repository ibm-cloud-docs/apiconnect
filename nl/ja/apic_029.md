---

copyright:
  years: 2017
lastupdated: "2018-02-12"

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 新機能

{{site.data.keyword.apiconnect_full}} には、以下の機能拡張が含まれています。

- **開発者ポータルのユーザー・アカウントと開発者組織の削除**: 開発者ポータルのユーザー・アカウントと開発者組織を削除できます。また、開発者組織の所有権を変更することもできます。詳しくは、[Deleting your Developer account ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapic_portal_delete_account.html){:new_window}、[Deleting a Developer organization ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapic_portal_delete_dev_org.html){:new_window}、および [Changing the ownership of a Developer organization ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapic_portal_dev_org_ownership.dita){:new_window} を参照してください。

- __*endpoint_url* API イベント・フィールドを追加__: *endpoint_url* イベント・レコード・フィールドで、要求が失敗したプロキシーまたは呼び出しターゲット URL を識別できます。詳しくは、[Deleting your Developer account ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/rapim_analytics_apieventrecordfields.html){:new_window} を参照してください。</dd>

- **分析のための開発者ポータル REST API のサポートと参照情報を追加**: 開発者ポータル REST API は、カタログ API の分析に役立ちます。 詳しくは、[分析 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/analytics.html){:new_window} を参照してください。

- **API の作成時に「分析」セクションを追加**: 使用する API に既存のパラメーターを定義して指定し、その API に関する分析データを収集するために使用できます。 詳しくは、[REST API 定義の作成 ![外部リンク・アイコン icon](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html){:new_window} を参照してください。

- **開発者ポータルで 2 要素認証を使用するよう促す**: TFA ルール・モジュールを適用することにより、開発者ポータルのユーザーに対して、アカウントで 2 要素認証 (TFA) セットアップするよう促すことができます。 詳しくは、[Encouraging users to set up two-factor authentication on their Developer Portal account ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapim_portal_two_factor_auth_enforce.html){:new_window} を参照してください。

- **統合された請求支払管理に追加された機能**:
    管理者:
	* API の利用者がクレジット・カードを使用してサブスクライブできる、月次前払請求サブスクリプション・プランを作成します。 詳しくは、[Billing for the use of your Products ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/capim_product_billing.html){:new_window} を参照してください。
	* Stripe アカウントを活用してサブスクリプションの支払いを管理できます。
	* 新しいサブスクライバーのサブスクリプション・プランの無料の試用日数を指定します。 試用日数が経過すると、支払いが自動的に開始します。
	利用者:
	* 開発者ポータルで 1 つ以上の API が入った製品を使用できる、料金ベースのプランをサブスクライブできます。 詳しくは、[Tutorial: Subscribing to a Plan with pricing ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tutorial_portal_sub_paid_plan.html){:new_window} を参照してください。

- **ゲートウェイで起動が自動的に置換される**: 使用しているポリシーの最後の起動が、プロキシーによって自動的に置換されることがあります。 これはパフォーマンス向上のために、ゲートウェイによって自動的に実行されます。 詳しくは、[API プロパティー ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){:new_window} を参照してください。

- **OAuth のスコープをサード・パーティーの応答によって変更できる**: API のスコープの値をオーバーライドするように、外部サーバーを構成できます。 詳しくは、[Scope ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/con_oauth_scope.html){:new_window} を参照してください。

- **新しい API イベント・フィールド**: 次の API イベント・フィールドを追加しました。
    * billing.trial_period_days
	* billing.amount
	* billing.currency
	* billing.model
	* billing.provider
	* client_id
	* immediate_client_ip
	* latency_info2.task
	* latency_info2.ended

詳しくは、[API イベント・レコードのフィールド ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/rapim_analytics_apieventrecordfields.html){:new_window} と [REST API 呼び出しを使用して分析データを取得する ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/tapim_exportanalytics_api_calls.html){:new_window} を参照してください。

- **リダイレクト URL の新しい照会パラメーター**: サード・パーティーが利用できる情報に新しい照会パラメーターが追加されました。 新しいパラメーターは <code>provider</code>、<code>providerid</code>、
<code>g-transid</code> です。 詳しくは、[ダイレクト URL を介した認証および許可![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_redirect_form_.html){:new_window} を参照してください。

- **テスト・ツールでブラウザーの CORS アラートが表示されないようにする**: API Designer テスト・ツールは、CORS アラートをトリガーする可能性のあるブラウザーから要求を送信します。 CORS アラートを回避するために、ブラウザーからではなく API Designer をホストするサーバーからテスト・メッセージを送信するための、**「プロキシーを有効にする」**チェック・ボックスが用意されています。 詳しくは、[API Designer テスト・ツールを使用した API のテスト ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_toolkit_testing.html){:new_window} を参照してください。

- **Mobile First Foundation の代わりにサード・パーティーの OAuth を使用して API を保護する**: IBM MobileFirst&tm; Platform Foundation の許可サーバーの代わりにサード・パーティーの OAuth プロバイダーを使用して API を保護します。 詳しくは、[Integrating third party OAuth provider ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/con_oauth_introspection.html){:new_window} を参照してください。

- **OpenID Connect (OIDC) で API を保護する**: 事前提供されたサンプル OAuth プロバイダー API を、OpenID Connect (OIDC) の構成に従ってカスタマイズしてから使用することによって、OIDC で API を保護できます。 詳しくは、[Securing your APIs with OpenID Connect ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/tapic_sec_api_config_oidc.html){:new_window} を参照してください。

- **SOAP の更新アクションで API が上書きされなくなった**: SOAP API を WSDL 定義から更新する場合、新しい WSDL の影響を受ける API のセクションのみが置き換えられます。他のセクションは変更されません。 以前のリリースでは、更新アクションによって、すべての設計プロパティーやアセンブリーの構成を含め、SOAP API 定義の構成がすべて上書きされていました。 詳しくは、[Updating a SOAP API ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/tapic_soap_update.html){:new_window} を参照してください。

- **開発者ポータルでのスパム保護に Honeypot を使用する**: Honeypot による保護によって、スパム・ボットによるフォーム送信から開発者ポータル・サイトを保護するセキュリティー・メカニズムが提供されます。 スパム・ボットのアクティビティーが検出されると、フォーム送信がブロックされます。 詳しくは、[Using Honeypot for spam protection ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapic_portal_honeypot.html){:new_window} を参照してください。

- **開発者ポータルでビュー・モジュールを使用する**: ビュー UI モジュールを使用して、製品、API、アプリケーションのコンテンツ・リストなどの新しいビューを、開発者ポータルで作成します。 詳しくは、[Using the Views module in the Developer Portal ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/capic_portal_views.html){:new_window} を参照してください。
