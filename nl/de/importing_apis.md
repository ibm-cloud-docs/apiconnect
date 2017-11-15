---
copyright:
  years: 2017
lastupdated: "2017-10-19"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# APIs importieren

Sie können die Swagger-Definitionsdatei verwenden, um eine REST-API hinzuzufügen.
{:shortdesc}

## Voraussetzungen
{: #prereq_import_swagger}

Stellen Sie vor Beginn sicher, dass Ihre Datei der Version 2.0 der Swagger-Spezifikation
entspricht. Die Datei kann im JSON-Format oder im YAML-Format vorliegen.

Führen Sie die folgenden Schritte aus, um eine Swagger-Datei zu laden
und eine REST-API hinzuzufügen:

1. Klicken Sie im Navigationsbereich der Benutzerschnittstelle von API Manager auf **Entwürfe** und
anschließend auf **APIs**. Die Registerkarte 'APIs' wird geöffnet.

2. Klicken Sie auf **Hinzufügen** und wählen Sie **Swagger 2.0** im
Bereich **Importieren** aus. Das Fenster **Swagger-API importieren** wird geöffnet.

3. **Optional**:
Um eine Datei aus Ihrem lokalen Dateisystem hochzuladen, klicken Sie auf **Datei auswählen**,
und wählen Sie in Ihrem Dateisystem die Datei aus, die Sie verwenden möchten. Dateien mit den
Erweiterungen `.json`, `.yml` und `.yaml` werden unterstützt,
sofern sie eine gültige Swagger-Definition enthalten.

4. **Optional**:
Um eine Datei von einer bestimmten URL hochzuladen, klicken Sie auf **Oder aus URL importieren**,
und geben Sie die korrekte URL in das angezeigte Feld **URL** ein. Falls für den Zugriff auf
die URL eine Authentifizierung erforderlich ist, geben Sie einen Benutzernamen und ein Kennwort an. Dateien mit den
Erweiterungen `.json`, `.yml` und `.yaml` werden unterstützt,
sofern sie eine gültige Swagger-Definition enthalten.

5. Klicken Sie auf **Importieren**. Eine REST-API-Definition mit Pfaden und HTTP-Operationen wird erstellt.

Nach dem Importieren wird die API-Definition in der Liste der API-Definitionen in der Registerkarte
**APIs** auf der Seite **Entwürfe** angezeigt. Als Nächstes können Sie Ihre API-Definition bearbeiten wie jede andere REST-API-Definition.

## APIs aus IBM Integration Bus importieren
{: #tut_import_iib_apic}

Mithilfe dieses Lernprogramms können Sie REST-APIs, die Sie mit IBM Integration Bus erstellen, in {{site.data.keyword.apiconnect_full}} importieren, wodurch sich deren Verwaltung und Veröffentlichung vereinfachen lässt.
{: shortdesc}

Stellen Sie vor Beginn sicher, dass Ihre REST-API-Datei der Version 2.0 der Swagger-Spezifikation entspricht. Die Datei kann im JSON-Format oder im YAML-Format vorliegen.

Mithilfe von IBM Integration Bus können Sie REST-APIs erstellen; dabei handelt es sich
um Fachanwendungen, die für das Zugänglichmachen von Integrationen als REST-konformer Web-Service verwendet und von HTTP-Clients
aufgerufen werden können. Nach der Erstellung der APIs können Sie sie in {{site.data.keyword.apiconnect_short}} zur Verwaltung und Veröffentlichung importieren.

In der folgenden Liste sind einige Vorteile der Verwaltung Ihrer APIs in {{site.data.keyword.apiconnect_short}} aufgeführt:
* Sie können die Anzahl der Aufrufe Ihrer API überwachen.
* Sie können die Anzahl der Aufrufe Ihrer API steuern.
* Sie können mehrere Versionen einer API pflegen.

Weitere Vorteile finden Sie unter [APIs verwalten](managing_apis.html).

Führen Sie die folgenden Schritte aus, um eine REST-API in IBM Integration Bus zu erstellen
und sie in {{site.data.keyword.apiconnect_short}} zu
importieren:
1. Erstellen Sie die REST-API mithilfe von IBM Integration Bus. Einschränkung: Sie können eine REST-API nur mit dem IBM Integration Toolkit erstellen; dieses Toolkit wird mit der installierten Version von IBM Integration Bus bereitgestellt.
	1. Erstellen Sie eine REST-API mithilfe von IBM Integration
Toolkit. Weitere Informationen zur Durchführung der Tasks zur Erstellung einer REST-API mit IBM Integration Bus finden Sie im IBM Knowledge Center unter [Integrationslösungen mithilfe von REST-APIs entwickeln ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSMKHH_10.0.0/com.ibm.etools.mft.doc/bi12016_.htm){: new_window}.
		
	2. Öffnen Sie den Assistenten zum Erstellen einer REST-API; wählen Sie hierfür **Datei** > **Neu** > **REST-API** aus.
		
	3. Geben Sie einen Namen für die REST-API ein. Der von Ihnen angegebene Name wird als Name für das Projekt in
IBM Integration Toolkit verwendet.
		
	4. Wählen Sie für die Erstellung der REST-API eine der folgenden Methoden aus und führen Sie die Prozedur aus:
		
	**Neuerstellung mithilfe des im Lieferumfang von IBM Integration Toolkit enthaltenen REST-API-Editors:**
		1. Wählen Sie die Option **REST-API erstellen und Ressourcen und Operationen selbst definieren** aus.
		2. Klicken Sie auf **Fertigstellen**. Der REST-API-Editor für die neue REST-API wird automatisch geöffnet; die Verwendung für die Definition von Ressourcen, Modellen und Operationen hiermit ist obligatorisch.
		
	**Erstellung auf Basis eines vorhandenen Swagger 2.0-Dokuments**:
		1. Wählen Sie die Option **In Swagger-Dokument definierte Ressourcen und Operationen importieren** aus und klicken Sie auf **Weiter**.
		2. Wählen Sie den Pfad zu dem Swagger-Dokument aus, in dem die Ressourcen und Operationen beschrieben werden, die Sie in der REST-API wünschen. Sie können das Swagger-Dokument aus dem Dateisystem oder aus einem im Arbeitsbereich bereits vorhandenen Projekt importieren. Die Datei wird für die Verwendung in einer REST-API validiert. Falls bei der Validierung des ausgewählten Swagger-Dokuments Fehler festgestellt werden, werden diese Fehler am Anfang des Assistenten angezeigt. Falls in dem ausgewählten Swagger-Dokument Validierungsfehler gefunden werden, ist ein Fortfahren nicht möglich. 
		3. Wählen Sie **Fertigstellen** aus, um die API zu erstellen.
	5. Implementieren Sie die Unterabläufe für Ihre REST-API; dies sind die REST-Operationen, die Sie einbeziehen möchten.
2. Fügen Sie das REST-API-Projekt zu einer neuen oder einer bereits vorhandenen BAR-Datei (Brokerarchivdatei) von IBM Integration Bus hinzu.
3. Stellen Sie die BAR-Datei in IBM Integration Bus on Cloud bereit.
	1. Melden Sie sich unter Verwendung Ihrer IBMid bei IBM Integration Bus on Cloud an, falls Sie nicht bereits angemeldet sind. Melden Sie sich für ein Konto an, falls Sie nicht bereits über ein Konto verfügen.
	2. Klicken Sie auf **Integration hinzufügen** > **BAR-Datei hochladen**.
	3. Wählen Sie die BAR-Datei aus, die Sie für Ihr REST-API-Projekt erstellt haben. Tipp: Sie können die Position Ihrer BAR-Datei herausfinden, indem Sie in IBM Integration Toolkit mit der rechten Maustaste darauf klicken und die Eigenschaften anzeigen.
	4. Wählen Sie **Speichern** aus.
	5. Wählen Sie **Liste aktualisieren** aus, um die Anzeige zu aktualisieren.
	6. Stellen Sie sicher, dass die BAR-Datei erfolgreich hochgeladen wurde; zeigen Sie hierfür im Fenster *Integrationen* von IBM Integration Bus on Cloud den API-Integrationsablauf für die API an.
4. Starten Sie den Integrationsablauf, indem Sie das Startsymbol ![Screenshot mit Startsymbol](images/a_play_button.jpg " ") auswählen. Die API wird gestartet und es wird der Status `Aktiv` angezeigt.
5. Wenn Sie Informationen zu einer Integration anzeigen möchten, wählen Sie die Integration in der Liste der Integrationen aus. In der Baumstruktur des Inhaltsmenüs werden die REST-API und die ihr zugeordneten Unterabläufe angezeigt. Sie können auch Informationen in den anderen Abschnitten anzeigen. Im Abschnitt mit den öffentlichen Endpunkten können Sie die öffentliche
URL anzeigen, die IBM Integration Bus on Cloud
Ihrem Integrationsablauf zugewiesen hat. Wählen Sie **Vollständige URL anzeigen** aus, um die vollständige URL für diese Operation anzuzeigen.
6. Kopieren Sie die vollständige URL für diese Operation in die Zwischenablage. Diese URL ist für die Konfiguration der API zur Verwendung in {{site.data.keyword.apiconnect_short}} erforderlich. Wenn Sie die Basisauthentifizierung aktiviert haben, müssen Sie außerdem den zugewiesenen Benutzernamen und das Kennwort notieren.

### IBM Integration Bus in API Connect integrieren
{: #integrateiibapic}

1. Importieren Sie die Swagger-Datei, die dem REST-API-Projekt in IBM Integration Toolkit zugeordnet ist, in den {{site.data.keyword.apiconnect_short}}-Service. 
	1. Melden Sie sich am {{site.data.keyword.apiconnect_short}} {{site.data.keyword.Bluemix_notm}}-Service an.
	2. Wählen Sie im Navigationsbereich der Benutzerschnittstelle von API Manager **Entwürfe** > **APIs** aus. Die Registerkarte 'APIs' wird geöffnet.
	3. Wählen Sie **+ Hinzufügen** > **API aus Datei oder URL importieren** aus. Das Fenster *OpenAPI importieren (Swagger)* wird geöffnet. 
	4. Wählen Sie zum Hochladen der von Ihnen erstellten Datei aus Ihrem lokalen Dateisystem **Datei auswählen** aus und wählen Sie anschließend die mit IBM Integration Bus erstellte Datei aus. Dateien mit den Erweiterungen `.json`, `.yml` und `.yaml` werden unterstützt, sofern sie eine gültige Swagger-Definition enthalten. Stellen Sie sicher, dass die Option **Produkt hinzufügen** ausgewählt ist. Sie können das Produkt optional veröffentlichen, indem Sie die Option **Dieses Produkt in einem Katalog veröffentlichen** auswählen.
	5. Klicken Sie auf **Importieren**. Eine REST-API-Definition mit Pfaden und HTTP-Operationen wird erstellt. Tipp: Wenn der Import länger als 1 Minute dauert, brechen Sie den Vorgang ab, aktualisieren Sie Ihren Browser und wiederholen Sie den Import. Möglicherweise ist Ihre Sitzung abgelaufen.
2. Stellen Sie eine Zuordnung zwischen der importierten API in {{site.data.keyword.apiconnect_short}} und der API in IBM Integration Bus on Cloud her.
	1. Rufen Sie das Dashboard von {{site.data.keyword.apiconnect_short}} auf.
	2. Wählen Sie **Entwürfe** > **APIs** aus.
	3. Klicken Sie auf die von Ihnen importierte REST-API.
	4. Wählen Sie die Registerkarte für die Assemblierung und die Option **Assemblierung erstellen** aus, um die Proxy-Richtlinie hinzuzufügen.
	5. Ziehen Sie die Richtlinie **Proxy** in die neue leere Richtlinie, um sie zu aktivieren.
	6. Fügen Sie die URL für Ihre API ein, die Sie aus dem Abschnitt mit den öffentlichen Endpunkten von IBM Integration Bus on Cloud kopiert haben.
	7. Wenn Sie die Basisauthentifizierung für Ihre REST-API aktiviert haben, geben Sie den Benutzernamen und das Kennwort ein, die in IBM Integration Bus on Cloud generiert wurden.
	8. Speichern Sie die API-Einstellungen.
3. Testen Sie die API.
	1. Wählen Sie in der Registerkarte 'Assemblierung' der API die Schaltfläche für Tests ![Schaltfläche für Tests](images/a_play_button.jpg "Screenshot mit dem Schaltflächensymbol für Tests") aus.
	2. Wählen Sie **Produkt erneut veröffentlichen** aus.
	3. Wählen Sie die Operation aus.
	4. Geben Sie die erforderlichen Parameter ein.
	5. Wählen Sie **Aufrufen** aus.
	6. Stellen Sie sicher, dass Sie von der API die erwartete Antwort erhalten. 
	
Wurde die API-Definition importiert und integriert, können Sie die APIs so verwalten und regeln wie Sie es mit anderen REST-API-Definitionen tun. Weitere Informationen zu den APIs finden Sie in [APIs verwalten](managing_apis.html).

## Mit IBM App Connect Professional erstellte APIs in IBM API Connect veröffentlichen

Mithilfe dieses Lernprogramms können Sie REST-APIs, die Sie mit IBM&reg; App Connect Professional erstellen, in {{site.data.keyword.apiconnect_full}} veröffentlichen und verwalten.

### Voraussetzungen
{: #prereq_pub_api_appconn}

Sie benötigen gültige Konten für IBM&reg; App Connect Professional on Cloud und
für IBM API Connect&trade; in Bluemix&reg;,
um dieses Lernprogramm auszuführen. Stellen Sie sicher,
dass die REST-API-Datei Version 2.0 der Swagger-Spezifikation entspricht. Die Datei kann
im JSON-Format oder im YAML-Format vorliegen.

Mithilfe von IBM&reg; App Connect Professional können Sie REST-APIs erstellen; dabei handelt es sich
um Fachanwendungen, die dazu verwendet werden können, Integrationen als REST-konforme Web-Services zugänglich zu machen,
und die von HTTP-Clients aufgerufen werden können. Nach der Erstellung der APIs können Sie sie mit
{{site.data.keyword.apiconnect_short}} veröffentlichen und verwalten.
In der folgenden Liste sind einige Vorteile der Verwaltung Ihrer APIs in {{site.data.keyword.apiconnect_short}} aufgeführt:

- Sie können die Anzahl der Aufrufe Ihrer API überwachen.
- Sie können die Anzahl der Aufrufe Ihrer API steuern.
- Sie können mehrere Versionen einer API pflegen.

Weitere Vorteile finden Sie unter [APIs verwalten](managing_apis.html).
Führen Sie die folgenden Schritte aus, um eine REST-API in IBM&reg; App Connect Professional
zu erstellen und diese in {{site.data.keyword.apiconnect_short}}
zu veröffentlichen:

1. Erstellen Sie die REST-API mit IBM&reg; App Connect
Professional.
  - Melden Sie sich mit Ihrer IBMid an der [Web-Management-Konsole für App Connect Professional ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://appconnect.ibmcloud.com/professional/){:new_window} an. Weitere Informationen zur Durchführung der Tasks zur Erstellung einer REST-API mit der Web-Management-Konsole für IBM&reg; App Connect Professional finden Sie in [Informationen zu den Einstellungen für die Managementkonsole![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SS3LC4_7.5.2.0/com.ibm.wci.appliance.doc/About_the_WMC/consoleSettings.html){:new_window} im IBM&reg; Knowledge Center.
  - Wählen Sie die Registerkarte für die Produktion aus, falls diese nicht bereits ausgewählt ist.
  - Wählen Sie im Navigationsfenster **Repository** > **Konfigurationen** aus.
  - Wählen Sie in der Projektkonfigurationsanzeige das Projekt aus, das Sie in {{site.data.keyword.apiconnect_short}} veröffentlichen möchten. Die Konfigurationsdetails des zu veröffentlichenden Projekts werden angezeigt.
  - Wählen Sie **Push-Operation an das API Management** aus.
      **Tipp:** Die Schaltfläche **Push-Operation an das API-Management** ist nur aktiv, wenn das importierte Projekt den Status 'Aktiv' oder 'Bereitgestellt' aufweist. Wählen Sie die Wiedergabeschaltfläche aus, um das Projekt zu starten, falls der Link nicht angezeigt wird.
  - Geben Sie in der Anzeige für eine Push-Operation an das API-Management die folgenden Informationen ein, um eine Verbindung zum API-Managementsystem herzustellen.

  <table><caption>Tabelle 1. Verbindungsinformationen für die Veröffentlichung einer API in API Connect</caption>
  <thead>
  <tr>
  <th>Feldname</th>
  <th>Beschreibung</th>
  </tr>
  </thead>
  <tbody>
  <tr><td>Host</td>
  <td>Gibt den Hostnamen der Management-Cluster-, -Server- oder -Cloudadresse an. Für {{site.data.keyword.Bluemix_short}} lautet dieser Eintrag in der Regel us.apiconnect.ibmcloud.com.</td>
  </tr>
  <tr>
  <td>Port</td>
  <td>Gibt die Portnummer an, die für eine Verbindung zur Management-Cluster-, -Server- oder -Cloudadresse erforderlich ist.</td>
  </tr>
  <tr><td>Benutzer-ID</td>
  <td>Gibt den Authentifizierungsbenutzernamen an, der für den Zugriff auf die Management-Cluster-, -Server- oder -Cloudadresse verwendet wird. Dies ist in der Regel Ihre IBMid, mit der Sie sich an {{site.data.keyword.Bluemix_short}} anmelden.</td>
  </tr>
  <tr><td>Kennwort</td>
  <td>Gibt das Authentifizierungskennwort an, das für den Zugriff auf die Management-Cluster-, -Server- oder -Cloudadresse
verwendet wird. Dies ist in der Regel das Kennwort für Ihre IBMid, mit der Sie sich an
  {{site.data.keyword.Bluemix_short}} anmelden.</td>
  </tr>
  </tbody>
  </table>

2. Wählen Sie **Organisationen laden** aus, um die Liste der Organisationen zu füllen,
die Ihrer ID und Ihrem Kennwort zugeordnet sind.

3. Wählen Sie **Organisationen** aus, um das Projekt einer der verfügbaren
Organisationen zuzuordnen.

4. Wählen Sie **Push-Operation an API-Management** aus und wählen Sie anschließend **OK** aus.

5. Wählen Sie **Schließen** aus, um das Fenster zu schließen.
Im Standardbrowser wird eine neue Browserregisterkarte geöffnet, auf der die API angezeigt wird.

Ordnen Sie die IBM&reg; App Connect-API {{site.data.keyword.apiconnect_short}} zu.

#### Swagger-API-Definition importieren

Führen Sie die folgenden Schritte aus, um die Swagger-Datei, die dem REST-API-Projekt in IBM&reg; App Connect zugeordnet ist, in den {{site.data.keyword.apiconnect_short}}-Service zu importieren:

1. Melden Sie sich am {{site.data.keyword.apiconnect_short}}
Bluemix&reg;-Service an.

1.  Wählen Sie in der Titelleiste der API Manager-Benutzerschnittstelle **Navigieren zu** > **Entwürfe** aus.

2. Wählen Sie **APIs** in der Menüleiste aus.
Die Registerkarte 'APIs' wird geöffnet.

3. Wählen Sie die importierte API aus, um API Designer zu öffnen.

4. Wählen Sie **Assemblieren** im Navigationsfenster aus.
Im Navigationsfenster wird eine Liste mit Richtlinien angezeigt.

5. Wählen Sie **Assemblierung erstellen** aus, falls erforderlich.

6. Fügen Sie die Richtlinie **Invoke** hinzu, indem Sie sie zur Assemblierung
im Hauptfenster ziehen.

7. Wählen Sie die Richtlinie **Invoke** im Hauptfenster aus, um die zugehörigen
Konfigurationseinstellungen zu modifizieren.

8. Konfigurieren Sie die Einstellung 'host/basePath' für das URL-Feld mit den folgenden Informationen:

- **Hostname**: Einstellung, die von der jeweiligen Cloudinstanz abhängig ist. Weitere Informationen zu dieser Einstellung finden Sie in
[IBM App Connect Professional ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://provide.castiron.ibmcloud.com){:new_window}.

- **Basispfad**: Pfad, den Sie im Anforderungshinweis 'httpReceive' in der App Connect Professional-Orchestrierung angeben.

9. Fügen Sie den Benutzernamen und das Kennwort für Ihre IBMid zu den HTTP-Basisauthentifizierungsdetails,
die Sie für App Connect Professional verwenden, hinzu und speichern Sie sie.

#### API testen

Führen Sie die folgenden Schritte aus, um die API zu testen:

1. Wählen Sie auf der Registerkarte 'Assemblierung' der API die Schaltfläche für Tests aus <img alt="Screenshot mit dem Schaltflächensymbol für Tests" src="images/a_play_button.jpg" />.
2. Wählen Sie **Produkt erneut veröffentlichen** aus.
3. Wählen Sie die Operation aus.
4.  Geben Sie die erforderlichen Parameter ein.
5. Wählen Sie **Aufrufen** aus.
6. Stellen Sie sicher, dass Sie von der API die erwartete Antwort erhalten.

Wurde die API-Definition importiert und integriert, können Sie die APIs
so verwalten und regeln wie Sie es mit anderen REST-API-Definitionen tun. Weitere Informationen zu den APIs finden Sie in [APIs verwalten](managing_apis.html).


