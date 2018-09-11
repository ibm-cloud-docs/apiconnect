---

copyright:
  years: 2017-2018
lastupdated: "2018-05-23"

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Neuerungen

{{site.data.keyword.apiconnect_full}} enthält die folgenden Erweiterungen:


- **Unterstützung für neue Fehler durch das Catch-Assemblykonstrukt**: Die folgenden neuen Fehler werden durch das Catch-Konstrukt in einer API-Assembly unterstützt: *BadRequestError*, *UnauthorizedError* und *ForbiddenError*. Weitere Informationen finden Sie in [Von Assembly-Catches unterstützte Fehler ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/ref_toolkit_catch_errors.html){:new_window}.
- **Abfrageparameter 'useBytesSent' zu ausgewählten APIs hinzugefügt**: Der Parameter *useBytesSent* wurde hinzugefügt, der es ermöglicht, dass das Analysefeld *bytes_sent* zur Berechnung der Nutzung verwendet wird. Weitere Informationen finden Sie in [Datennutzungsinformationen für alle von einer bestimmten Anwendung verwendeten Ressourcen zurückgeben ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps__appID__data-usageGET.html){:new_window}, [Datennutzungsinformationen für alle Ressourcen zurückgeben, die von allen Anwendungen in der angegebenen Organisation verwendet werden ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps_data-usageGET.html){:new_window}, [Kombinierte Datennutzungsinformationen für alle von einer bestimmten Anwendung verwendeten Ressourcen zurückgeben ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps__appID__data-usage_allGET.html){:new_window} und [Kombinierte Datennutzungsinformationen für alle von einer bestimmten Organisation verwendeten Ressourcen zurückgeben ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_data-usage_allGET.html){:new_window}.
- **Codieren von Pluszeichen in den Abfrageparameterwerten der Ziel-URL einer Aufruf- oder Proxy-Richtlinie**: Die neue API-Eigenschaft *x-ibm-gateway-queryparam-encode-plus-char* steht zur Verfügung; wird für diese der Wert *true* festgelegt, werden alle Pluszeichen ("+") in den Abfrageparameterwerten der Ziel-URL von Aufruf- oder Proxy-Richtlinien mit "%2F" codiert. In früheren Releases wurden Pluszeichen stets mit %2F codiert. Nun besteht das Standardverhalten darin, keine Codierung vorzunehmen. Weitere Informationen finden Sie in [API-Eigenschaften ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){:new_window}.
- **Durchsetzen der Verwendung des JSON-Parsers für die Antwortregel einer Aufruf- oder Proxy-Richtlinie möglich**: Die neue API-Eigenschaft *x-ibm-gateway-api-enforce-response-limits* steht zur Verfügung; wird für diese Eigenschaft der Wert *true* festgelegt, kann die Vewendung des JSON-Parsers für die Antwortregel durchgesetzt werden. Überschreitet die Größe des Antworthauptteils den in der DataPower-Domäne festgelegten Grenzwert des JSON-Parsers wird der Statuscode 500 zurückgegeben. Weitere Informationen finden Sie in [API-Eigenschaften ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){:new_window}.
- **Potenzielle Leistungsverbesserung für die Zuordnungsrichtlinie**: Die neue API-Eigenschaft *x-ibm-gateway-optimize-schema-definition* steht zur Verfügung; mit dieser Eigenschaft kann eine Leistungsverbesserung für die Zuordnungsrichtlinie erreicht werden, wenn eine sehr komplexe Schemadefinition durch eine Richtlinienausgabendefinition referenziert wird. Weitere Informationen finden Sie in [API-Eigenschaften ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){:new_window}.
