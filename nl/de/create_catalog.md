---

copyright:
  years: 2017
lastupdated: "2017-10-24"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal

subcollection: apiconnect

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Katalog konfigurieren
{: #create_catalog}

Sie können API Manager-Kataloge erstellen und konfigurieren. Kataloge sind nützlich, um Produkte und APIs zum Testen voneinander zu trennen,
bevor Sie sie Developer-Organisationen verfügbar machen.
Wenn Sie einen Katalog konfigurieren, können Sie außerdem das angepasste Branding konfigurieren, sodass
Sie nicht auf die Verwendung der standardmäßigen API-URL angewiesen sind, die API Manager bereitstellt.

Führen Sie die folgenden Schritte aus, um einen Katalog zu erstellen:

1. Klicken Sie auf **Navigieren zu** <img alt="Symbol 'Navigieren zu'" src="images/navigate_to_icon.png"> > **Dashboard**.

2. Klicken Sie auf **Hinzufügen** > **Katalog**.
Das Fenster **Katalog hinzufügen** wird angezeigt.

3.  Geben Sie den Namen für Ihren neuen Katalog im Feld **Anzeigename** ein.

4. Geben Sie den Text, der das Katalogsegment der URL bilden soll, im Feld
**Name** ein.
	**Hinweis:** Das Feld **Name** darf nur alphanumerische Zeichen in Kleinschreibung
(a-z und 0-9) oder Trennstriche (-) enthalten. Der Trennstrich darf nicht als erstes oder
letztes Zeichen im Namen verwendet werden.

5. Klicken Sie auf **Hinzufügen**. Ihr Katalog wird erstellt und im Dashboard angezeigt.

6. Klicken Sie zum Konfigurieren des Katalogs zuerst auf den Namen des Katalogs und dann auf **Einstellungen** > **Info** und fahren Sie mit den folgenden Schritten fort:
  1. Wenn es sich bei dem neuen Katalog um einen Entwicklungskatalog handelt, wählen Sie den Modus **Entwicklung** aus.
Wenn Sie den Entwicklungsmodus auswählen, werden die Bereitstellungs- (Staging-) und Veröffentlichungsaktionen erzwungen.
Das bedeutet, dass ein bereits veröffentlichtes Produkt bei seiner erneuten Veröffentlichung ohne Warnung überschrieben wird. Werden Konflikte festgestellt, werden
diese automatisch vom System aufgelöst. Aktionen zum Rückgängigmachen der Veröffentlichung erfolgen automatisch.
	**Hinweis:** Für Entwicklungskataloge werden keine Genehmigungsfelder angezeigt. Der Genehmigungsprozess
für Lebenszyklen kann nicht aktiviert werden.
  2. Wenn Sie das automatische Abonnement für den Katalog aktivieren möchten, wählen Sie
**Automatisches Abonnement** aus.
Die Aktivierung des automatischen Abonnements vereinfacht das Testen Ihrer APIs, denn es wird eine Testanwendung mit einer vorab bereitgestellten Client-ID und einem ebensolchen geheimen Clientschlüssel verwendet. Diese Testanwendung ist automatisch bei allen Plänen im Katalog abonniert, sodass Sie beim Testen keinen bestimmten Plan bzw. keine bestimmte Anwendung angeben müssen. 
    **Hinweis:** Das automatische Abonnement ist nur für Entwicklungskataloge verfügbar.
  3. Wenn es sich bei dem Katalog um den Standardbereitstellungskatalog handelt, wählen Sie **Standard** aus. Dann können Aufrufe
an die APIs, die im Katalog veröffentlicht sind, eine kürzere URL verwenden, die nicht den
Katalognamen enthält.
    **Hinweis:** Die Option **Standard** kann nur für einen einzelnen Katalog ausgewählt werden.
  4. **Optional:** Klicken Sie auf **Endpunkte** und füllen Sie die folgenden Felder aus:
        - **Angepasste Gateway-URL**: Geben Sie eine URL im Feld 'Angepasste Gateway-URL' ein. Die Verwendung einer angepassten Gateway-URL
        bietet sich an, wenn Sie ein angepasstes Branding von URLs für APIs erzielen möchten, die in {{site.data.keyword.apiconnect_short}} bereitgestellt werden,
        anstatt die Standard-URL zu verwenden, die API Manager generiert.
        Standardmäßig hat die {{site.data.keyword.apiconnect_short}}-Gateway-URL
        das folgende Format:
        ```
        https://gateway_cluster_hostname/organization_name/Catalog_name
        ```
        Diesen Standard können Sie jedoch außer Kraft setzen, indem Sie eine URL angeben, die sich für Ihr Unternehmen besser eignet, wie zum Beispiel
        `https://api.mycompany.com`. Alle API-Endpunkte, die im Developer Portal angezeigt werden,
        werden dann die angegebene URL widerspiegeln.
			**Hinweise:**
		    - Sie müssen einen DNS-Eintrag konfigurieren, über den die Zuordnung Ihres angepassten Hostnamens mitsamt Domäne zur Standard-Gateway-URL
      erfolgt.
		    - Damit die Endpunkte einer API Ihre Standard-Gateway-URL widerspiegeln, müssen Sie die API so konfigurieren, dass sie durch das
      API Connect-Gateway umgesetzt wird. Weitere Informationen finden Sie unter [Specifying an alternative host for an API ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){: #new_window}.
		    - Stellen Sie sicher, dass eine einzige angepasste Gateway-URL nicht etwa auf mehrere Kataloge angepasst wird,
denn das Verhalten für ein derartiges Szenario ist nicht definiert.
				**Tipp:** Wenn Sie die API aufrufen, können Sie auch den HTTP-Host-Header für die API-Anforderung auf den Wert festlegen, den Sie
im Feld 'Angepasste Gateway-URL' angegeben haben.

	    - **Angepasste API-URL**
	    Geben Sie die URL im Feld 'Angepasste API-URL' ein. Die angepasste API-URL wird verwendet, um die URL für APIs anzugeben,
     die im Gateway eines Drittanbieters bereitgestellt werden.

	    Die angepasste API-URL stellt den Endpunkt dar, über den die API extern bekannt ist, d. h. den Endpunkt, der im Developer Portal veröffentlicht ist und
     vom Anwendungsentwickler verwendet wird, um die API aufzurufen oder
     zugänglich zu machen.

	    Wenn Sie ein Gateway eines Drittanbieters oder eine externe Lastausgleichsfunktion in diesem Katalog verwenden, geben Sie in diesem Feld
     die entsprechende URL an. Alle API-Endpunkte, die im Developer Portal angezeigt werden, werden dann die angegebene
     URL widerspiegeln. Diese Endpunkte sind auf dem Gateway des Drittanbieters oder in der Lastausgleichsfunktion vorhanden und
     projizieren eine virtuelle Adresse. Diese Adresse ist gegenüber API-Konsumenten zugänglich und ist den Endpunkten des API-Proxy
     oder der API-Assembly auf dem Gateway zugeordnet. Die von der angepassten API-URL abgeleiteten Endpunkte werden normalerweise in Entwicklerportalen für
     die Produktion veröffentlicht, um die Adresse der API zugänglich zu machen.

	    **Hinweis:** Wenn Sie eine angepasste API-URL für einen Katalog angeben, so hat diese Vorrang vor jeglichem Hostnamen, den Sie
     beim Konfigurieren der API angeben. Weitere Informationen finden Sie unter [Specifying an alternative host for an API ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){: #new_window}.

	    - **Hostname für Aufrufe der Developer Portal-API:**
     Geben Sie im Fensterbereich für den Port-API-Endpunkt einen Hostnamen für Aufrufe der Developer Portal-API ein. Bei dem Hostnamen,
     den Sie eingeben, kann es sich um den Hostnamen Ihres Management-Service handeln. Um im Kontext von Developer Portal auf die
     Developer Portal-API zugreifen zu können, müssen Sie den Basishostnamen für Aufrufe der Developer Portal-API
     konfigurieren. Diese Aktion ermöglicht API Manager die Zuordnung Ihres Hostnamens zur
     Provider-Organisation und zum Katalog der Developer Portal-API-Aufrufe; es ist nun nicht mehr
     erforderlich, diese Angaben nachzuschlagen und in die Aufrufe einzubinden.

7. Klicken Sie auf das Symbol **Speichern**.

## Katalog in Bereiche aufteilen
{: #apic_spaces_create_catalog}

Um die Syndikationsfunktion in {{site.data.keyword.apiconnect_short}} verwenden zu können, müssen Sie Bereiche in allen Katalogen
aktivieren, in denen die Syndikationsfunktionalität benötigt wird.

Führen Sie die folgenden Schritte aus, um Bereiche in einem Katalog zu aktivieren:
1. Wählen Sie im Dashboard der Benutzerschnittstelle von API Manager den Katalog aus, mit dem Sie arbeiten möchten.

2. Klicken Sie auf **Einstellungen** > **Übersicht** und dann auf den Schieberegler **Bereiche**.

3. Klicken Sie im Fenster **Bereiche aktivieren** auf **Aktivieren** und klicken Sie anschließend auf das Symbol **Speichern** <img src="images/icon_save.png" alt="Symbol 'Speichern'"/>.
Unter dem Schieberegler für **Bereiche** wird der Link **Bereiche verwalten** angezeigt und der
Link **Bereiche** wird zum Navigationsbereich hinzugefügt. Sie können Ihre Bereiche verwalten, indem Sie auf einen dieser Links klicken.

Für den Katalog werden Bereiche aktiviert und ein Standardbereich namens 'Neuer Bereich' wird
erstellt.

Weitere Informationen zur Verwendung der Syndikation finden Sie in den Abschnitten im Knowledge Center unter [Verwendung der Syndikation in IBM API Connect ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.apionprem.doc/capic_syndication_using.html){: #new_window}.
