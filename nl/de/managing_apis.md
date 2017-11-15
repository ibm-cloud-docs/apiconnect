---

copyright:
  years: 2017
lastupdated: "2017-10-19"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# APIs verwalten
{: #managing_apis}

Sie können API Connect zum Verwalten der APIs in {{site.data.keyword.Bluemix}} verwenden; hierbei ist es unerheblich, ob sie sich innerhalb von {{site.data.keyword.Bluemix_notm}} oder außerhalb von {{site.data.keyword.Bluemix_notm}} befinden. Durch das Verwalten der APIs können Sie die Nutzung steuern, die Akzeptanz erhöhen und Statistiken verfolgen.

Wenn Sie ein Kunde sind, können Sie die Verwendung in der API Manager-Benutzerschnittstelle verwalten, nachdem ein Entwickler eine API erstellt und das Produkt anhand einer Push-Operation an {{site.data.keyword.Bluemix_short}} übertragen hat. In den folgenden Abschnitten werden die Vorgehensweisen zum Erstellen und Verwalten von Produkten in {{site.data.keyword.apiconnect_short}} beschrieben. Designer.

## Lokale APIs über einen sicheren Gateway verfügbar machen
{: #expose_apis_sec_gate}

Sie können ein sicheres Gateway erstellen, um lokale APIs sicher in {{site.data.keyword.apiconnect_full}} bereitzustellen.

Wenn Sie ein sicheres Gateway erstellen, integrieren Sie die Funktionen des {{site.data.keyword.Bluemix_short}}
{{site.data.keyword.SecureGateway}}-Service in {{site.data.keyword.apiconnect_short}}. Das bedeutet, dass Sie eine sichere Möglichkeit haben,
von {{site.data.keyword.apiconnect_short}} über eine sichere Passage auf Ihre lokalen APIs zuzugreifen, ohne eine separate Instanz des
{{site.data.keyword.SecureGateway}}-Service bereitstellen zu müssen. Effektiv erstellen Sie einen Tunnel
zu {{site.data.keyword.apiconnect_short}} in einer öffentlichen Umgebung, ohne Ihre lokalen Daten
zugänglich zu machen. Dazu müssen Sie nur das Gateway erstellen und es einer API
zuordnen. Die Erstellung eines Ziels, eines SSL-Profils und der Zertifikate wird ausgeführt.
Weitere Informationen zum {{site.data.keyword.SecureGateway}}-Service finden Sie unter [Informationen zu {{site.data.keyword.SecureGateway}}](../../services/SecureGateway/sg_overview.html#sg_overview).
Führen Sie zum Erstellen einer Secure Gateway-Instanz die Schritte in den folgenden Abschnitten durch.

### Sicheres Gateway erstellen
{: #create_sec_gate notoc}

Wenn Sie ein sicheres Gateway erstellen, werden eine Gateway-ID und ein Sicherheitstoken für Sie generiert.
Sie können auch in Ihrer lokalen Unternehmensumgebung einen Secure Gateway-Client für die Verbindung mit {{site.data.keyword.apiconnect_short}} einrichten. Nach dem Einrichten des Clients stellen Sie anhand der Gateway-ID und des Sicherheitstokens eine Verbindung mit dem Client her, damit Sie auf Ihre
lokalen APIs zugreifen können.

Führen Sie die folgenden Schritte aus, um ein Gateway zu erstellen:

1. Klicken Sie auf **Navigieren zu** <img alt="Symbol 'Navigieren zu'" src="images/navigate_to_icon.png"> > **Admin** > **Secure Gateways**.
Die Seite `Secure Gateways` wird geöffnet und in einer Ecke der Benutzerschnittstelle wird eine geführte Tour
für den Secure Gateway-Service angezeigt.

2. **Optional**:
Klicken Sie auf jeden Schritt der geführten Tour, um Ihre Gateway-Einrichtung durchzuführen.

3. Klicken Sie auf **Hinzufügen**.
Das Dialogfeld `Secure Gateway erstellen` wird angezeigt.

4. Geben Sie einen Namen für Ihr Gateway an.

**Hinweis:** Nur alphanumerische Zeichen und Unterstriche sind zulässig.

5. Klicken Sie auf **Speichern**.
Das Gateway wird gemeinsam mit der Gateway-ID und dem Sicherheitstoken angezeigt.

6. Klicken Sie auf **Einrichten**.
Durch Klicken auf **Einrichten** haben Sie die Möglichkeit, einen Secure Gateway-Client auf Ihren lokalen Arbeitsplatz herunterzuladen und dort zu
installieren, um eine Verbindung zwischen einem fernen Netz und einem sicheren Gateway im Bluemix&reg;-Netz herzustellen.

    Das Fenster `Secure Gateway-Clients einrichten` wird angezeigt.

7. Klicken Sie in den folgenden Optionen auf den Client, den Sie verwenden wollen:

    - IBM&reg; Installationsprogramme
    - Docker
    - IBM DataPower&reg;

8. Befolgen Sie die Anweisungen am Bildschirm, um den ausgewählten Client zu installieren und auszuführen.

Weitere Informationen zum Einrichten eines Secure Gateway-Clients finden Sie unter [Client einrichten](../../services/SecureGateway/sg_021.html#sg_021).

9. Wenn Sie die Installation des Clients beendet haben, schließen Sie das Fenster **Secure Gateway-Clients einrichten**.

10. Aktualisieren Sie die Seite.

Die Verbindung zum Client wird hergestellt und die ID und der Status des Gateways werden angezeigt. Sie haben die Gateway-Konfiguration abgeschlossen und ein sicheres Gateway erstellt. Verwenden Sie als Nächstes das sichere Gateway für den Zugriff auf Ihre lokalen APIs.

### Sicheres Gateway mit den APIs verwenden
{: #using_sec_gate_apis notoc}

Nachdem Sie das Gateway konfiguriert haben, können Sie es mit den APIs verwenden.
{:shortdesc}

Führen Sie die folgenden Schritte aus, um das sichere Gateway mit APIs zu verwenden:
1. Erstellen Sie Ihre API und Ihr Produkt, wie in den folgenden Schritten beschrieben.
  - Klicken Sie auf **Navigieren zu** <img src="images/navigate_to_icon.png" alt="Symbol 'Navigieren zu'" /> > **Entwürfe** > **APIs** > **Hinzufügen**.
  - Wählen Sie den Typ der API aus, die Sie erstellen möchten.
  - Wählen Sie **Produkt hinzufügen** aus bzw. klicken Sie darauf. **Wichtig:** Veröffentlichen Sie das Produkt noch nicht.
  - Klicken Sie auf **API erstellen**.
  Die API wird in der Ansicht `Design` angezeigt.
  
2. Klicken Sie auf **Assemblieren**.

3. Klicken Sie auf die Richtlinie **invoke**, um die Palette **invoke** zu öffnen.
**Einschränkung:** Logische Schalter, z. B. `Switch`, `Operation Switch` oder `If`
können nicht mit APIs verwendet werden, die ein sicheres Gateway nutzen.

4. Wählen Sie **Zugriff auf URL über Secure Gateway** aus.

5. Aktualisieren Sie im URL-Feld die Ziel-URL (`target-url`) mit dem lokalen Hostnamen und der
lokalen Portnummer. Beispiel:
```
target-url: http://onpremdb2.rtp.raleigh.ibm.com:3055$(request.path)$(request.search)
```

6. Klicken Sie auf **Speichern** <img src="images/icon_save.png" alt="Symbol 'Speichern'" />.

7. Klicken Sie auf die Registerkarte **Quelle**. Versehen Sie das Feld `secure-gateway` mit dem Wert `true`.

8. Klicken Sie auf **Alle APIs** > **Produkte** und wählen Sie das zuvor erstellte Produkt aus.

9. Klicken Sie auf das Symbol **Veröffentlichen**, um das Produkt in einem ausgewählten Katalog bereitzustellen.

10. Wählen Sie den Katalog aus, den Sie verwenden möchten.

11. Wählen Sie das bereitgestellte Produkt aus.

12. Klicken Sie auf **Veröffentlichen** und wählen Sie **Secure Gateway-Zuweisungen** aus.

Sie haben Ihre lokale API sicher auf {{site.data.keyword.apiconnect_short}} bereitgestellt. Alle TLS-Profile, die einem Ziel zugeordnet sind, werden
hinzugefügt. Klicken Sie zum Überprüfen der TLS-Profile auf **Navigieren zu**
<img src="images/navigate_to_icon.png" alt="Symbol 'Navigieren zu'" /> > **Admin** > **Sicherheit** > **TLS-Profile**.
Für jede API können mehrere Gateways eingerichtet werden. Welches Gateway verwendet werden soll, entscheiden Sie beim Veröffentlichen der API. Wenn Sie den
{{site.data.keyword.SecureGateway}}-Service bereits bereitgestellt haben, haben Sie die Möglichkeit, Ihre Ziele im
{{site.data.keyword.SecureGateway}}-Dashboard zu überwachen. Sie können jedoch keine {{site.data.keyword.apiconnect_short}}-Ziele bearbeiten, die vom
{{site.data.keyword.apiconnect_short}}-Service erstellt wurden.
Testen Sie als Nächstes die {{site.data.keyword.SecureGateway}}-API.

### Secure Gateway-API testen
{: test_sec_gate notoc}

Nachdem Sie das Gateway mit einer API verbunden haben, können Sie die API testen, um sicherzustellen, dass das Gateway ordnungsgemäß funktioniert
und die richtige Antwort zurückgibt. 

Um eine API mit dem sicheren Gateway zu testen, führen Sie die folgenden Schritte aus:

1. Klicken Sie auf <img alt="Symbol 'Navigieren zu'" src="images/navigate_to_icon.png" /> > **Entwürfe** > **APIs**
**<Eigene API>** > **Assemblieren**.

2. Klicken Sie auf das Symbol **Testen** <img src="images/test_icon.png" alt="Symbol 'Testen'"/>.

3. Wählen Sie aus der bereitgestellten Liste einen zu testenden Katalog aus.

4. Wählen Sie aus der bereitgestellten Liste ein sicheres Gateway aus, das getestet werden soll.

5. Wählen Sie ein vorhandenes Produkt aus der bereitgestellten Liste aus und klicken Sie anschließend auf
**Produkt erneut veröffentlichen** aus.
   **Wichtig:** Wenn dieses Produkt bereits in einem Katalog veröffentlicht ist, wird das Produkt mit dem
   neuen Gateway erneut veröffentlicht.

6. **Optional**:
Geben Sie einen Namen an, um ein neues Produkt zu erstellen, und klicken Sie auf **Erstellen
und veröffentlichen**.

7. Klicken Sie auf **Weiter**.

8. Wählen Sie aus der bereitgestellten Liste eine aufzurufende Operation aus.

9. Klicken Sie auf **Aufrufen**.

Die Testergebnisse werden angezeigt.

## Loopback-Anwendung bereitstellen und veröffentlichen
{: #stage_publish_lb_app}

1. Klicken Sie im Navigationsbereich von API Designer auf **Produkte**.
Die Registerkarte 'Produkte' wird geöffnet.

2. Wählen Sie die Version des Produkts aus und stellen Sie sicher, dass Sie auf die Version klicken, mit der Sie arbeiten möchten.

3. Um die Laufzeit in {{site.data.keyword.Bluemix_short}} zu veröffentlichen, klicken Sie auf **Veröffentlichen**.

4. Klicken Sie auf **Ziele hinzufügen und verwalten** > **IBM Bluemix-Ziel hinzufügen**.

5. Wählen Sie die {{site.data.keyword.Bluemix_short}}-**Region** für die Veröffentlichung aus und melden Sie sich an.

6. Wählen Sie die {{site.data.keyword.Bluemix_short}}-**Organisation** aus, die Sie veröffentliche möchten.

7.  Eine Liste mit Katalogen wird angezeigt. Wählen Sie den Katalog aus, in dem Sie die Anwendung veröffentlichen möchten.

8.  Klicken Sie auf **Weiter**.

9. Wählen Sie die LoopBack-Anwendung aus, die Sie veröffentlichen möchten.
Wenn Sie die Laufzeit zum ersten Mal in {{site.data.keyword.Bluemix_short}} bereitstellen,
fügen Sie einen Namen hinzu und klicken Sie auf das Symbol **Hinzufügen**.

10.  Klicken Sie auf **Speichern**.

11.  Klicken Sie erneut auf **Veröffentlichen** und wählen Sie **Anwendung veröffentlichen** aus.

12.  Klicken Sie auf **Veröffentlichen**.

13. In der Befehlszeile ist die URL des API-Ziels (API Target URL) und 'API invoke tls-profile' für die API angegeben.
Notieren Sie diese Informationen. Für 'API invoke tls-profile' wird stets
`client:Loopback-client` verwendet, aber Sie können die URL des API-Ziels wie im nachfolgenden Schritt
beschrieben abrufen.
    ```
    Deploying to Bluemix
    ...preparing project
    ...building package for deploy
    ...uploading package
    Runtime published successfully.
    Management URL: https://<domain name>/apps/33e7b062-092b-4227-af97-047499dab2e7
    API target urls: apiconnect-33e7b062-092b-4227-af97-047499dab2e7.<Bluemix org>-<Bluemix space>.apic.<domain name>
    API invoke tls-profile: client:Loopback-client
    Updated newapi_1.0.0.yaml with tls-profile and target-url.
    Updated notes.yaml with tls-profile and target-url.
    ```

14. Führen Sie in der Benutzerschnittstelle von API Designer die folgenden Schritte aus:
    1. Klicken Sie auf **APIs**.
    2. Wählen Sie Ihre API aus.
    3. Klicken Sie auf **Assemblieren**.
    4. Klicken Sie im Assemblierungseditor auf das Symbol **Filterrichtlinien**.
    5. Wählen Sie **DataPower-Gateway-Richtlinien** aus.
    6. Klicken Sie auf **Speichern**, um die API zu speichern.

15.  Als Nächstes müssen Sie die API in API Manager veröffentlichen. Klicken Sie auf **Veröffentlichen**.
    1. Wählen Sie **Anwendung veröffentlichen** aus und wählen Sie dann eine der folgenden Optionen aus:
	    - **Vorhandene App ersetzen:** Wenn Sie über eine veröffentlichte Anwendung verfügen, wählen Sie diese Option aus, damit die vorhandene App überschrieben wird.
        - **Als völlig neue App (unter Verwendung der vorhandenen Route)**: Wählen Sie diese Option aus, damit eine neue App erstellt wird, für die Sie im Feld **Neue App** einen Namen eingeben müssen. Hierdurch ergibt sich keine Unterbrechung des Service.

    2. Wählen Sie die folgenden Optionen aus:
	    - Produkte bereitstellen oder veröffentlichen
        - Bestimmte Produkte auswählen
        - _ihr produkt_
 
    3. Klicken Sie auf **Veröffentlichen**.

Führen Sie die folgenden Schritte aus, um zu testen, ob das Veröffentlichen erfolgreich durchgeführt wurde:

1. Stellen Sie sicher, dass die {{site.data.keyword.Bluemix_short}}-App
aktiv ist.

2. Öffnen Sie ein Browserfenster und navigieren Sie zur API-Ziel-URL.
Die Anwendung wird durch Client-Validierung geschützt. Wenn Sie nicht das korrekte Clientzertifikat
angeben, wird der Prozess wegen Fehlern beendet (dies ist die erwartete Funktionsweise).

3. Navigieren Sie zur verfügbar gemachten
{{site.data.keyword.apiconnect_short}}-URL.
Beispiel:
```
https://<domäne>/<Bluemix-organisation>-<Bluemix-bereich>/<katalogkennung>/api/notes
```
Eine Antwort aus der Serie 200 wird angezeigt.

## Katalog konfigurieren

Sie können API Manager-Kataloge erstellen und konfigurieren. Kataloge sind nützlich, um Produkte und APIs zum Testen voneinander zu trennen,
bevor Sie sie Entwicklerorganisationen verfügbar machen. Wenn Sie einen Katalog konfigurieren, können Sie außerdem das angepasste Branding konfigurieren, sodass
Sie nicht auf die Verwendung der standardmäßigen API-URL angewiesen sind, die API Manager bereitstellt.

Führen Sie die folgenden Schritte aus, um einen Katalog zu erstellen:

1. Klicken Sie auf **Navigieren zu** <img alt="Symbol 'Navigieren zu'" src="images/navigate_to_icon.png"> > **Dashboard**.

2. Klicken Sie auf **Hinzufügen** > **Katalog**.
Das Fenster **Katalog hinzufügen** wird angezeigt.

3.  Geben Sie den Namen für Ihren neuen Katalog im Feld **Anzeigename** ein.

4. Geben Sie den Text, der das Katalogsegment der URL bilden soll, im
Feld **Name** ein. **Hinweis:** Das Feld **Name** darf nur alphanumerische Zeichen in Kleinschreibung
(a-z und 0-9) oder Trennstriche (-) enthalten. Der Trennstrich darf nicht als erstes oder letztes Zeichen im Namen verwendet
werden.

5. Klicken Sie auf **Hinzufügen**. Ihr Katalog wird erstellt und im Dashboard angezeigt.

6. Klicken Sie zum Konfigurieren des Katalogs zuerst auf den Namen des Katalogs und dann auf **Einstellungen** > **Info** und fahren Sie mit den folgenden Schritten fort:
  1. Wenn es sich bei dem neuen Katalog um einen Entwicklungskatalog handelt, wählen Sie den Modus **Entwicklung** aus.
Wenn Sie den Entwicklungsmodus auswählen, werden die Bereitstellungs- (Staging-) und Veröffentlichungsaktionen erzwungen.
Das bedeutet, dass ein bereits veröffentlichtes Produkt bei seiner erneuten Veröffentlichung ohne Warnung überschrieben wird. Werden Konflikte festgestellt, werden
diese automatisch vom System aufgelöst. Aktionen zum Rückgängigmachen der Veröffentlichung erfolgen automatisch.
**Hinweis:** Für Entwicklungskataloge werden keine Genehmigungsfelder angezeigt. Der Genehmigungsprozess für Lebenszyklen
kann nicht aktiviert werden.
  2. Wenn Sie die automatische Subskription für den Katalog aktivieren möchten, wählen Sie
**Automatisches Abonnement** aus. Die Aktivierung der
automatischen Subskription vereinfacht das Testen Ihrer APIs, denn es wird eine Testanwendung mit einer vorab bereitgestellten Client-ID und einem ebensolchen geheimen
Clientschlüssel verwendet. Diese Testanwendung ist automatisch bei allen Plänen im Katalog subskribiert, sodass Sie beim Testen keinen bestimmten Plan bzw. keine bestimmte
Anwendung angeben müssen. **Hinweis:** Die automatische Subskription ist nur für Entwicklungskataloge verfügbar.
  3. Wenn es sich bei dem Katalog um den Standardbereitstellungskatalog handelt, wählen Sie **Standard** aus. Dann können Aufrufe an die APIs,
die im Katalog veröffentlicht sind, eine kürzere URL verwenden, die nicht den
Katalognamen enthält.
    **Hinweis:** Sie können nur **Standard** für einen Katalog auswählen.
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
      API Connect-Gateway umgesetzt wird. Weitere Informationen finden Sie unter [Specifying an alternative host for an API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){:new_window}.
		    - Stellen Sie sicher, dass eine einzige angepasste Gateway-URL nicht etwa auf mehrere Kataloge angepasst wird, denn das Verhalten für ein derartiges
		    Szenario ist nicht definiert.
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
     beim Konfigurieren der API angeben. Weitere Informationen finden Sie unter [Specifying an alternative host for an API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){:new_window}.

	    - **Hostname für Aufrufe der Developer Portal-API:**
     Geben Sie im Fensterbereich für den Port-API-Endpunkt einen Hostnamen für Aufrufe der Developer Portal-API ein. Bei dem Hostnamen,
     den Sie eingeben, kann es sich um den Hostnamen Ihres Management-Service handeln. Um im Kontext von Developer Portal auf die
     Developer Portal-API zugreifen zu können, müssen Sie den Basishostnamen für Aufrufe der Developer Portal-API
     konfigurieren. Diese Aktion ermöglicht API Manager die Zuordnung Ihres Hostnamens zur
     Provider-Organisation und zum Katalog der Developer Portal-API-Aufrufe; es ist nun nicht mehr
     erforderlich, diese Angaben nachzuschlagen und in die Aufrufe einzubinden. 

7. Klicken Sie auf das Symbol **Speichern**.

## Katalog in Bereiche aufteilen

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

Weitere Informationen zur Verwendung der Syndikation finden Sie in den Abschnitten im Knowledge Center unter [Verwendung der Syndikation in IBM API Connect ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.apionprem.doc/capic_syndication_using.html){:new_window}.

## Developer Portal konfigurieren
{: #config_dev_portal}

In einem Developer Portal werden Ihre Pläne veröffentlicht, um sie für Anwendungsentwickler
zugänglich und nutzbar zu machen.

Sie können ein angepasstes Developer Portal erstellen, das von Anwendungsentwicklern verwendet werden kann. Sie können die Darstellung, den Inhalt,
die Benutzereinstellungen und die Konfigurationseinstellungen genau festlegen.

Das Developer Portal ermöglicht Anwendungsentwicklern nicht nur den Zugriff auf und die Nutzung von APIs, sondern stellt darüber hinaus weitere
Ressourcen wie Foren, Blogs, Kommentare, Bewertungen sowie eine Swagger-Benutzerschnittstelle für APIs bereit.

1. Wählen Sie in der Benutzerschnittstelle von API Manager den Katalog aus, mit dem Sie arbeiten möchten.

2. Wählen Sie die Registerkarte **Einstellungen** aus.

3. Klicken Sie auf **Portal**.

4. Wählen Sie im Abschnitt **Portalkonfiguration** die Auswahlmöglichkeit **IBM Developer
Portal** aus. Die Portal-URL wird angezeigt.

5. Klicken Sie auf **Speichern**. Sie erhalten in einer E-Mail-Nachricht einen nur einmal verwendbaren Anmeldelink für den
Developer Portal-Benutzer mit Administratorberechtigung.

6. Klicken Sie auf den Link in der E-Mail-Nachricht und befolgen Sie die Anweisungen
zum Zurücksetzen Ihres Kennworts.

Ihr Developer Portal ist konfiguriert. Die URL für das Developer Portal ist in der
Betreffzeile der E-Mail-Nachricht enthalten, die Sie empfangen haben. Sie finden die URL auch in der Benutzerschnittstelle
von API Manager, indem Sie auf **Portal** > **Einstellungen** klicken.

Weitere Informationen zu den Tasks, die Sie in Developer Portal ausführen, finden Sie in den Abschnitten des
Knowledge Center zu [Developer Portal ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.devportal.doc/capim_devportal_overview.html){:new_window}.

## Berechtigungen für Rollen konfigurieren
{: #config_permissions_roles}

Um die Berechtigungen für die Rollen in API Manager zu konfigurieren, führen Sie die
folgenden Schritte aus.

1. Klicken Sie im **Dashboard** von API Manager auf den Katalog, mit dem Sie
arbeiten möchten.

2. Klicken Sie auf **Einstellungen** > **Berechtigungen**.
Es werden die Berechtigungen für das Produktmanagement angezeigt, denen Sie Rollen zuweisen können:
  - **Staging**: Ermöglicht das Bereitstellen (Staging) von Produkten im Katalog.
  - **Anzeigen**: Ermöglicht das Anzeigen und Auflisten von Produkten im Katalog.
  - **Verwalten**: Ermöglicht die Verwaltung des Produktlebenszyklus (Veröffentlichen, Einstellen der Unterstützung, Zurückziehen und Archivieren).
  - **Genehmigen**: Aktiviert Genehmigungen für Änderungen am Produktlebenszyklusstatus.
**Hinweis:** Die Funktion zur Genehmigung für Änderungen am Produktlebenszyklusstatus ist für alle Entwicklungskataloge inaktiviert.

3. Wenn Sie eine Rolle zu den Berechtigungen **Bereitstellen**, **Anzeigen** oder **Verwalten** hinzufügen möchten, klicken Sie auf das zugehörige Plussymbol **+**.
Die folgende Liste zeigt die standardmäßig verfügbaren Rollen an:
  - Administrator
  - Produktmanager
  - API-Entwickler
  - Publisher
Die Rolle 'Publisher' verfügt über alle Berechtigungen.

4. Aktivieren Sie Genehmigungen für Änderungen des Produktlebenszyklusstatus, indem Sie die erforderlichen
Kontrollkästchen auswählen und dann auf das entsprechende Plussymbol **+** klicken, um die Rollen zuzuweisen,
die über die Berechtigung zur Genehmigung eines Lebenszyklusstatus verfügen.
Bei den von Ihnen ausgewählten Änderungen des Lebenszyklusstatus handelt es sich um jene, für die die Genehmigung erzwungen werden soll.
Wenn Sie zum Beispiel 'Veröffentlichen' auswählen, die anderen Optionen jedoch weiterhin inaktiviert lassen, so ist
eine Genehmigung erforderlich, wenn jemand versucht, ein Produkt zu veröffentlichen. Für alle anderen Änderungen des
Lebenszyklusstatus ist jedoch keine Genehmigung erforderlich.
5. Wenn Sie die Rollen zuweisen möchten, die über die Berechtigung zur Verwaltung benutzerdefinierter Richtlinien verfügen,
klicken Sie im Abschnitt für die **Richtlinienverwaltung** auf das Plussymbol **+**.
Es werden die Berechtigungen zur Richtlinienverwaltung angezeigt, wodurch Sie nach Bedarf Rollen zuweisen
können.
6. Klicken Sie auf das Symbol **Speichern**.
