---

copyright:
  years: 2017-2019
lastupdated: "2018-05-23"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal

subcollection: apiconnect

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 新機能
{: #apic_029}

{{site.data.keyword.apiconnect_full}} には、以下の機能拡張が含まれています。


- **新しいエラー・ケースはアセンブリー catch 構成でサポートされています**: 次の新しいエラー・ケースは、API アセンブリーの catch 構文でサポートされています: *BadRequestError*、*UnauthorizedError*、および *ForbiddenError*。 [アセンブリー catch でサポートされるエラー・ケース ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/ref_toolkit_catch_errors.html){: #new_window} を参照してください。
- **選択した API に useBytesSent 照会パラメーターが追加されました**: *useBytesSent* パラメーターが追加され、分析フィールド *bytes_sent* を使用して使用量を計算できるようになりました。 詳しくは、[特定のアプリケーションが使用するすべてのリソースのデータ使用情報を返す![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps__appID__data-usageGET.html){: #new_window}、 [特定の組織内のすべてのアプリケーションが使用するすべてのリソースのデータ使用情報を返す![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps_data-usageGET.html){: #new_window}、[特定のアプリケーションが使用するすべてのリソースの結合データ使用率を返す![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps__appID__data-usage_allGET.html){: #new_window}、および[特定の組織が使用するすべてのリソースの結合されたデータ使用率を返す![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_data-usage_allGET.html){: #new_window}を参照してください。
**Invoke ポリシーまたは Proxy ポリシーのターゲット URL の照会パラメーター値内の + 文字をエンコードすることができます**: 新しい *x-ibm-gateway-queryparam-encode-plus-char* API プロパティーが追加されました。値 *true* に設定されている場合、Invoke ポリシーまたは Proxy ポリシーのターゲット URL の照会パラメーター値にあるすべての "+" 文字は "%2F" にエンコードされます。 以前のリリースでは、+ は常に %2F にエンコードされていました。 デフォルトの動作ではエンコードされなくなりました。 [API プロパティー ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){: #new_window} を参照してください。
- **Invoke ポリシーまたは Proxy ポリシーの応答ルールに JSON パーサーを適用することができます**: 新しい *x-ibm-gateway-api-enforce-response-limits* API プロパティーが追加されました。このプロパティーの値を *true* に設定すると、JSON パーサーで応答ルールを適用できるようになります。 応答本文のサイズが、DataPower ドメインに設定されている JSON パーサーの制限よりも大きい場合、ステータスコード 500 が返されます。 [API プロパティー ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){: #new_window} を参照してください。
- **マップ・ポリシーのパフォーマンス向上の可能性**: 非常に複雑なスキーマ定義がポリシー出力定義によって参照された場合に、マップ・ポリシーのパフォーマンスを向上させることができる新しい *x-ibm-gateway-optimize-schema-definition* API プロパティーが追加されました。 [API プロパティー ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){: #new_window} を参照してください。
