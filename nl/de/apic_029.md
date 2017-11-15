---

copyright:
  years: 2017
lastupdated: "2017-09-28"

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Neuerungen

{{site.data.keyword.apiconnect_full}} enthält die folgenden Erweiterungen:

- **Unterstützung und ein Verweis auf Developer Portal-REST-APIs für Analyse hinzugefügt**: Mit den Developer Portal-REST-APIs können Sie Ihre Katalog-APIs analysieren. Weitere Informationen finden Sie unter [Analyse ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/analytics.html){:new_window}.

- **Abschnitt 'Analyse' beim Erstellen einer API hinzugefügt**: Sie können vorhandene Parameter für die API definieren und angeben, die zum Zusammenstellen
von Analysedaten verwendet werden können. Weitere Informationen hierzu finden Sie unter [REST-API-Definition erstellen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html){:new_window}.

- **Förderung der Verwendung der Zwei-Faktor-Authentifizierung in Developer Portal**: Sie können Benutzer von Developer Portal ermutigen, eine
Zwei-Faktor-Authentifizierung (Two-Factor Authentication, TFA) durch Anwenden von TFA-Regeln für ihr Konto einzurichten. Weitere Informationen finden Sie unter [Benutzer zum Einrichten der Zwei-Faktor-Authentifizierung für ihr Developer Portal-Konto ermutigen![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapim_portal_two_factor_auth_enforce.html){:new_window}.

- **Zur integrierten Rechnungs- und Zahlungsabwicklung hinzugefügte Funktionen**:
Administrator:
	* Erstellung von Abonnementplänen für monatliche Prepaid-Abrechnungen, die die Kunden mit einer Kreditkarte abonnieren können. Weitere Informationen finden Sie unter [Verwendung von Produkten abrechnen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/capim_product_billing.html){:new_window}.
	* Nutzung eines Stripe-Kontos zur Verwaltung der Zahlungen für die Abonnements.
	* Angeben der Anzahl an Tagen für einen kostenlosen Test im Abonnementplan für neue Abonnenten. Die Zahlung beginnt automatisch nach Ablauf der Testtage.
	Kunde:
	* Abonnieren gebührenpflichtiger Pläne in Developer Portal, die die Nutzung von Produkten ermöglichen, in denen mindestens eine API enthalten ist. Weitere Informationen finden Sie unter [Lernprogramm: Plan mit Preisstruktur abonnieren ![Weitere Informationen zu](../../icons/launch-glyph.svg "Weitere Informationen zu")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tutorial_portal_sub_paid_plan.html){:new_window}.

- **Automatisches Ersetzen von Aufrufen im Gateway**: Der letzte Aufruf in einer Richtlinie kann durch einen Proxy ersetzt werden. Dies wird
vom Gateway automatisch ausgeführt, um die Leistung zu verbessern. Weitere Informationen finden Sie unter [API-Eigenschaften ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){:new_window}.

- **OAuth-Bereich kann durch Antworten von Drittanbietern geändert werden**: Sie können einen externen Server so konfigurieren, dass von ihm die API-Bereichswerte überschrieben werden. Weitere Informationen finden Sie unter [Bereich ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/con_oauth_scope.html){:new_window}.

- **Neue API-Ereignisfelder**: Folgende API-Ereignisfelder wurden hinzugefügt:
    * billing.trial_period_days
	* billing.amount
	* billing.currency
	* billing.model
	* billing.provider
	* client_id
	* immediate_client_ip
	* latency_info2.task
	* latency_info2.ended

Weitere Informationen finden Sie unter [API-Ereignisdatensatzfelder ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/rapim_analytics_apieventrecordfields.html){:new_window} und [Analysedaten durch REST-API-Aufrufe abrufen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbolfür externen Link")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/tapim_exportanalytics_api_calls.html){:new_window}.


- **Neue Abfrageparameter für Weiterleitungs-URL:** Zu den für einen Drittanbieter verfügbaren Informationen wurden neue Abfrageparameter hinzugefügt. Die neuen Parameter lauten <code>provider</code>, <code>providerid</code> und
<code>g-transid</code>. Weitere Informationen finden Sie unter [Authentifizieren und Autorisieren über eine Weiterleitungs-URL
![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_redirect_form_.html){:new_window}.

- **CORS-Alerts im Browser im Testtool vermeiden:** Vom API Designer-Testtool werden Anforderungen vom Browser gesendet, durch die CORS-Alerts ausgelöst werden können. Zum
Vermeiden von CORS-Alerts wird das Kontrollkästchen **Proxy aktivieren** zum Senden von Testnachrichten von dem Server bereitgestellt, auf dem API Designer gehostet wird und nicht vom Browser. Weitere
Informationen finden Sie unter [API mit API Designer-Testtool testen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_toolkit_testing.html){:new_window}.

- **APIs mit Drittanbieter-OAuth anstatt Mobile First Foundation schützen:** Sichern Sie die API mithilfe eines OAuth-Drittanbieters anstatt eines IBM MobileFirst&tm; Platform Foundation-Autorisierungsservers. Weitere
Informationen finden Sie unter [Drittanbieter-OAuth integrieren ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/con_oauth_introspection.html){:new_window}.

- **APIs mit OpenID Connect (OIDC) schützen:** Sie können ihre APIs mit OpenID Connect(OIDC) anhand
einer vorab bereitgestellten Beispiels-API des OAuth-Anbieters sichern, die Sie in Übereinstimmung mit der OIDC-Konfiguration anpassen. Weitere Informationen finden Sie unter
[APIs mit OpenID Connect schützen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/tapic_sec_api_config_oidc.html){:new_window}.

- **API wird nicht mehr durch SOAP-Aktualisierungsaktion überschrieben:** Wenn Sie eine SOAP-API von einer WSDL-Definition aktualisieren, werden nur die Abschnitte der API ersetzt,
die von der neuen WSDL betroffen sind, die anderen Abschnitte werden nicht geändert. In früheren Releases wurde die
Konfiguration der SOAP-API durch eine solche Aktualisierungsaktion vollständig überschrieben, inklusive aller Designeigenschaften
und der Assemblierungkonfiguration. Weitere Informationen finden Sie unter [SOAP-API
aktualisieren ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/tapic_soap_update.html){:new_window}.

- **Verwendung von Honeypot als Spamschutz in Developer Portal:** Die Honeypot-Schutzmöglickeiten bieten Sicherheitsmechanismen zum Schutz der Developer Portal-Site vor der Einreichung von Formularen durch Spam-Bots. Sobald eine Spam-Bot-Aktivität erkannt wird, wird die Formulareinreichung blockiert. Weitere
Informationen finden Sie unter [Honeypot für den Spamschutz verwenden ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapic_portal_honeypot.html){:new_window}.

- **Verwendung des Ansichtmoduls in Developer Portal:** Sie können in Developer Portal mithilfe des Moduls für die Benutzerschnittstelle für Module neue Ansichten erstellen, zum Beispiel Inhaltslisten von Produkten, APIs und Anwendungen. Weitere Informationen finden Sie unter [Modul für Ansichten in Developer Portal verwenden ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/capic_portal_views.html){:new_window}.
