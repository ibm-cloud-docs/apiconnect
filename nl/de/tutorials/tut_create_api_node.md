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


# API in Node.js erstellen

**Dauer**: 20 Minuten  
**Kenntnisstufe**: Anfänger  

---
## Lernziel

In diesem Lernprogramm werden Sie durch die Erstellung einer API in Node.js mithilfe eines LoopBack-Frameworks geführt. Im Lernprogramm wird Folgendes beschrieben:
1. Erstellung eines neuen LoopBack-Projekts
2. Hinzufügen einer neuen Datenquelle und eines Modells zu einem LoopBack-Projekt mit API Designer im {{site.data.keyword.apiconnect_short}}-Toolkit
3. Test der API-Endpunkte mit dem Tool API Designer Explore

---
## Voraussetzungen

Bevor Sie beginnen, müssen Sie [das {{site.data.keyword.apiconnect_short}}-Toolkit installieren](tut_prereq_install_toolkit.html).

---
## LoopBack-Projekt erstellen

Ein LoopBack-Projekt können Sie entweder in der Befehlszeilenschnittstelle des {{site.data.keyword.apiconnect_short}}-Entwicklertoolkits oder in der API Designer-Schnittstelle erstellen. 
 
### LoopBack-Projekt mit Befehlszeile des Toolkits erstellen

Führen Sie zum Erstellen eines LoopBack-Projekts in der Befehlszeile des {{site.data.keyword.apiconnect_short}}-Toolkits die folgenden Schritte aus:
1.  Geben Sie in der Befehlszeilenschnittstelle den folgenden Befehl ein. Er wird zum Erstellen und Verwalten von LoopBack-Anwendungen verwendet.
	```bash 
	apic loopback
	```
	>![info]
	>In diesem Lernprogramm erstellen Sie ein Projekt mit der Bezeichnung weather-data.
2.  Geben Sie in der Eingabeaufforderung `weather-data` als Name für das Projekt ein und drücken Sie die **Eingabetaste**.
	```bash
	? Wie lautet der Name für Ihre Anwendung? weather-data
	```
  	>![important]
  	>Im Allgemeinen kann ein Projektname alle Zeichen enthalten bis auf die folgenden: (" "), Schrägstrich ("/"), Et-Zeichen ("&"), kommerzielles A ("@"), Pluszeichen ("+"), Prozentzeichen ("%"), Doppelpunkt (":").
3.  Geben Sie den Namen des Verzeichnisses ein, in dem das Projekt erstellt werden soll. Drücken Sie die **Eingabetaste**, um ein Verzeichnis mit demselben Namen wie das Projekt zu erstellen, oder geben Sie einen neuen Namen ein, und drücken Sie die **Eingabetaste**.
	```bash
	? Geben Sie den Namen des Verzeichnisses ein, das das Projekt enthalten soll: weather-data
	```
4.  Wählen Sie die Version von LoopBack aus, die verwendet werden soll. Wählen Sie die aktuelle Produktionsversion aus: 3.x.
	```bash
	? Welche Version von LoopBack möchten Sie verwenden?
  	2.x (Langfristiger Support)
	? 3.x (Aktuell)
	```
5.  Geben Sie die Art der Anwendung an, die Sie erstellen möchten; wählen Sie hierzu mit den Pfeiltasten **empty-server** aus.
	```bash
	? Welche Art von Anwendung möchten Sie erstellen? (Pfeiltasten verwenden)
	? empty-server (eine leere LoopBack-API ohne konfigurierte Modelle oder Datenquellen)
  	hello-world (ein Projekt mit einem funktionsfähigen Basisbeispiel, einschließlich Speicherdatenbank)
  	notes (ein Projekt mit einem funktionsfähigen Basisbeispiel, einschließlich Speicherdatenbank)
	```
6.  Drücken Sie die **Eingabetaste**, um eine leere LoopBack-API zu erstellen. 

Beim Erstellen des Projektverzeichnisses mit mehreren Unterverzeichnissen und Dateien zeigt das Tool verschiedene Nachrichten an. Außerdem wird der Befehl npm install ausgeführt, um alle Projektabhängigkeiten zu installieren, wie in package.json angegeben. In diesem Prozess wird das Verzeichnis node_modules erstellt; der Vorgang kann etwas Zeit in Anspruch nehmen.

Ein leeres LoopBack-Projekt enthält die folgenden Verzeichnisse:
- server: Enthält das Servermodell, die Quellendefinitionen und weiteren Server-Code
- definitions: Enthält YAML-Definitionsdateien
- node_modules: Wird von node.js erstellt


### LoopBack-Projekt mit API Designer-Schnittstelle erstellen

Führen Sie die folgenden Schritte aus, um mit API Designer ein LoopBack-Projekt zu erstellen:
1.  Geben Sie in der Befehlszeilenschnittstelle den folgenden Befehl ein, um API Designer zu starten:
	```bash
	apic edit
	```
	![](images/api-designer-1.png)
	>![info]
	>Mit dem obigen Befehl wird das APIC-Toolkit initialisiert und API Designer im Standardbrowser gestartet.
	>![info]
	>In diesem Lernprogramm erstellen Sie ein Projekt mit der Bezeichnung weather-data.
2.  Falls Sie den Navigationsbereich der Benutzerschnittstelle vorher nicht fixiert haben, klicken Sie auf das Navigationssymbol ![](images/navigate-to.png). Der Navigationsbereich der Benutzerschnittstelle von API Manager wird geöffnet. Klicken Sie zum Fixieren des Navigationsbereichs der Benutzerschnittstelle auf das Symbol für das Fixiermenü ![](images/pinned.png).
3.  Klicken Sie in der Seitenleiste auf das Pluszeichen für Projekte ![](images/add-icon.png).
4.  Klicken Sie auf **LoopBack-Projekt erstellen**. Der Dialog **Neues LoopBack-Projekt hinzufügen** wird angezeigt.
5.  Wählen Sie **empty-server** als Projektvorlage aus.
6.  Wählen Sie für **LoopBack-Version** die Version 3.x (die aktuelle Version) aus.
7.  Geben Sie `weather-data` für den Anzeigenamen und die Namensfelder ein.
8.  Wählen Sie unter **Projektverzeichnis** den Ordner `weather-data` aus, den Sie in Schritt 1 erstellt haben; klicken Sie hierzu auf die Schaltfläche **Durchsuchen**.
	![](images/api-designer-2.png)
9. Klicken Sie auf **Hinzufügen**, um das Projekt hinzuzufügen.
	>![info]
	>Im Fenster **Neues LoopBack-Projekt hinzufügen** werden mehrere Nachrichten angezeigt, da in ihm das Projektverzeichnis erstellt und eine Reihe von Verzeichnissen und Dateien zu diesem Verzeichnis hinzugefügt werden. Außerdem wird der Befehl npm install ausgeführt, um alle Projektabhängigkeiten zu installieren, wie in package.json angegeben. In diesem Prozess wird das Verzeichnis node_modules erstellt; der Vorgang kann etwas Zeit in Anspruch nehmen.
	
	>Ein leeres LoopBack-Projekt enthält die folgenden Verzeichnisse:
	- server: Enthält das Servermodell, die Quellendefinitionen und weiteren Server-Code
	- definitions: Enthält YAML-Definitionsdateien
	- node_modules: Wird von node.js erstellt
10. Klicken Sie auf **Fertig**, um das Dialogfeld **Neues LoopBack-Projekt hinzufügen** zu schließen.
11. Beenden Sie **API Designer**, indem Sie zur Befehlszeile in Schritt 1 zurückkehren, und geben Sie `Strg + C` ein. Geben Sie `J` ein, um das Beenden zu bestätigen.
12. Schließen Sie die Browsersitzung.

---
## Neue Datenquelle und neues Modell hinzufügen

Führen Sie die folgenden Schritte aus, um ein neues Modell und eine neue Datenquelle mit API Designer zu einem LoopBack-Projekt hinzuzufügen:

### Datenquelle hinzufügen
Führen Sie die folgenden Schritte aus, um eine neue Datenquelle mit API Designer zu einem LoopBack-Projekt hinzuzufügen.
1. Sie müssen auch ein LoopBack-Projekt (das Projekt "weather-data") wie in `LoopBack-Projekt in Befehlszeile erstellen` erstellen und sicherstellen, dass das aktuelle funktionsfähige Verzeichnis das Projektstammverzeichnis ist:
	```bash
	cd weather-data
	```
2. Geben Sie in der Befehlszeile den folgenden Befehl ein:
	```bash
	apic edit
	```
	Nach einer kurzen Pause wird in der Konsole die folgende Nachricht angezeigt:
	```bash
	Express server listening on http://127.0.0.1:9000
	```
	API Designer wird im Standard-Web-Browser geöffnet, anfangs wird die Anmeldeseite angezeigt, falls Sie sich noch nicht angemeldet haben.  
	>![info]
	>Sie können sich unter Verwendung Ihres Bluemix-Kontos anmelden oder ein neues erstellen.
3. Klicken Sie auf das Symbol **Datenquellen** ![](images/datasource-icon.png).
4. Klicken Sie auf **Hinzufügen**. Das Fenster 'Neue LoopBack-Datenquelle' wird geöffnet.
5. Geben Sie `weatherDS` in das Textfeld **Name** ein.
	>![info]
	>Ein Datenquellenname darf beliebige alphanumerische Zeichen sowie Gedankenstriche und Unterstreichungszeichen enthalten.
6. Klicken Sie auf **Neu**.
7. Für die Einstellung **Connector** wird standardmäßig der Wert **In-memory db** (speicherinterne Datenbank) angezeigt, die anderen Einstellungen sind leer. Behalten Sie vorerst die Standardeinstellungen bei, die neue Datenquelle wird von API Designer automatisch gespeichert.
	>![info]
	>Die speicherinterne Datenquelle ist in LoopBack integriert und eignet sich ausschließlich für die Entwicklung sowie für erste Testprozesse. Wenn Sie soweit sind, die Modelle mit einer realen Datenquelle wie einem Datenbankserver zu verbinden, ändern Sie die Einstellung **Connector** entsprechend und installieren Sie den Datenquellenconnector gemäß den Anweisungen in [LoopBack-Connector installieren ![Symbol für externen Link](../../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSMNED_5.0.0/com.ibm.apic.toolkit.doc/tapim-connector-install.html#task_i2p_dnw_vv){:new_window}. Geben Sie die Connectoreinstellungen (Hostname, Port, Datenbankname, Benutzername, Kennwort) für den jeweiligen Connectortyp ein und klicken Sie auf das Symbol **Speichern** ![](images/save-icon.png). Die Verbindung zur Datenquelle wird von API Designer automatisch getestet. Wenn der Test erfolgreich verläuft, wird die Nachricht **Erfolg - Test der Datenquellenverbindung war erfolgreich** angezeigt.
8. Klicken Sie auf das Symbol 'Verbindung testen' ![](images/db-test-icon.png), um die Verbindung zur Datenquelle zu testen. Die Nachricht "Datenquellenverbindung erfolgreich" wird angezeigt.
9. Klicken Sie auf **Alle Datenquellen**. Die Datenquelle wird in der Liste der Datenquellen angezeigt und der Editor aktualisiert die Datei 'server/datasources.json' mit den Einstellungen für die neue Datenquelle.

### Modell hinzufügen

Führen Sie die folgenden Schritte aus, um ein neues Modell mit API Designer zu einem LoopBack-Projekt hinzuzufügen:
1. Klicken Sie auf das Symbol **Modelle** ![](images/models-icon.png).
2. Klicken Sie auf **Hinzufügen**. Das Fenster 'Neues LoopBack-Modell' wird geöffnet.
3. Geben Sie `weather` in das Textfeld **Name** ein und klicken Sie anschließend auf **Neu**.
4. Wählen Sie im Feld **Datenquelle** die Auswahlmöglichkeit **weatherDS** aus.
	![](images/new-model-1.png)
5. Klicken Sie in **Eigenschaften** auf das Symbol **Eigenschaft hinzufügen** ![](images/add-icon.png).
6. Geben Sie in das Textfeld **Eigenschaftsname** die Zeichenfolge `zip_code` ein.
7. Wählen Sie als **Typ** die Option **Nummer** aus.
8. Wählen Sie **Erforderlich** aus, damit die Eigenschaft erforderlich ist. Dies bedeutet, dass ein Wert vorhanden sein muss, wenn Sie eine Modellinstanz hinzufügen oder aktualisieren. Behalten Sie vorerst die Standardwerte für die restlichen Einstellungen bei:
	- **Ist Array:** Gibt an, ob die Eigenschaft ein JavaScript-Array mit Elementen des angegebenen Typs ist.
	- **ID:** Gibt an, ob die Eigenschaft eine eindeutige Kennung ist.
	- **Index:** Gibt an, ob die Eigenschaft für eine Spalte (ein Feld) steht, das ein Datenbankindex ist.
	- **Beschreibung:** Die Textbeschreibung der Eigenschaft.
9. Klicken Sie erneut auf das Symbol **Eigenschaft hinzufügen** ![](images/add-icon.png), um eine weitere Eigenschaft hinzuzufügen. Informationen zum Vervollständigen der übrigen Eigenschaften finden Sie in der nachfolgenden Tabelle:
	![](images/new-model-property-1.png)
10. Klicken Sie auf das Symbol **Speichern** ![](images/save-icon.png), um Ihre Änderungen zu speichern.
11. Klicken Sie auf **Alle Modelle**, um die Bearbeitung des Modells zu beenden.

Damit ist das Hinzufügen einer neuen Datenquelle und eines neuen Modells zum LoopBack-Projekt 'weather-data' abgeschlossen.

---

## LoopBack-Projekt testen

>![info]
	>Sie können direkt mit Schritt 2 unten fortfahren, wenn Sie {{site.data.keyword.apiconnect_short}} Designer nach Abschluss des Abschnitts 'Neue Datenquelle und neues Modell hinzufügen' nicht beendet haben.
	
Führen Sie die folgenden Schritte aus, um mit API Designer Explore die API-Endpunkte zu testen:
1. Geben Sie in der Befehlszeile den folgenden Befehl ein:
	```bash
	apic edit
	```
	Nach einer kurzen Pause wird in der Konsole die folgende Nachricht angezeigt:
	```bash
	Express server listening on http://127.0.0.1:9000
	```
	API Designer wird im Standard-Web-Browser geöffnet, anfangs wird die Anmeldeseite angezeigt, falls Sie sich noch nicht angemeldet haben.
	
2. Starten Sie die lokalen Testserver.
	a. Klicken Sie in der Testkonsole ganz unten auf dem Bildschirm auf das Symbol **Server starten** ![](images/test-icon.png):
	![](images/start-server-1.png)
	b. Warten Sie, bis die Nachricht 'Aktiv' angezeigt wird:
	![](images/running-server-1.png)

	>![info]
	>In Abhängigkeit von Ihrer Projektkonfiguration und den weiteren aktiven Prozessen werden möglicherweise andere Portnummern angezeigt.
3. Klicken Sie auf **http://127.0.0.1:port_number**, um den API-Rootendpunkt anzuzeigen. Für das LoopBack-Standardprojekt (Projekttyp 'empty' oder 'hello-world') wird ungefähr Folgendes angezeigt:
	```bash
	{"started":"2017-05-24T19:21:47.807Z","uptime":80.876}
	```
	>![info]
	>Klicken Sie zum Stoppen des Projekts auf das Symbol **Server stoppen** ![](images/stop-icon.png):
	>![](images/stop-server-1.png)
	
	>Klicken Sie zum erneuten Starten auf das Symbol **Server erneut starten** ![](images/restart-icon.png):
	>![](images/restart-server-1.png)
	
4. Klicken Sie auf das Symbol **Durchsuchen** ![](images/explore-icon.png), um API Designer Explore anzuzeigen. In der Seitenleiste werden all REST-Operationen für die LoopBack-Modelle in der API angezeigt. Modelle, die auf 'PersistedModel' basieren, verfügen über eine [Standardgruppe mit Erstellungs-, Lese-, Aktualisierungs- und Löschoperationen ![Symbol für externen Link](../../../icons/launch-glyph.svg "Symbol für externen Link")](http://loopback.io/doc/en/lb2/PersistedModel-REST-API){:new_window}.

5. Klicken Sie auf die Operation **weather.create** im linken Teilfenster, um den Endpunkt anzuzeigen.
![](images/explore-test-1.png)
Im mittleren Teilfenster werden Übersichtsinformationen zum Endpunkt angezeigt, unter anderem zu Parametern, Sicherheit, Modellinstanzdaten und Antwortcodes. Im rechten Teilfenster werden ein Vorlagencode zum Aufrufen des Endpunkts mithilfe des curl-Befehls sowie Sprachen wie Ruby, Python, Java und Node bereitgestellt.

6. Klicken Sie zum Testen der REST-Endpunkte in API Designer Explore im rechten Teilfenster auf **Versuchen**. Blättern Sie abwärts zu **Parameter** und klicken Sie auf **Generieren**, um Testdaten zu generieren. Die generierten Daten umfassen standardmäßig die Eigenschaften Postleitzahl (`zip_code`), aktuelle Temperatur (`current_temperature`), aktuelle Feuchtigkeit (`current_humidity`), nächtliche Tiefsttemperatur (`tonight_temperature_low`), nächtliche Höchsttemperatur (`tonight_temperature_high`), niedrigste nächtliche Feuchtigkeit (`tonight_humidity_low`), höchste nächtliche Feuchtigkeit (`tonight_humidity_high`) und die ID (`id`). Die Eigenschaft `id` wird von LoopBack für ein bestimmtes Modell erstellt und der Wert wird automatisch generiert. Entfernen Sie die Eigenschaft `id` aus den Beispieldaten, aktualisieren Sie die generierten Daten bei Bedarf und klicken Sie auf **Operation aufrufen**.
![](images/explore-test-2.png)
>![troubleshooting]
>Falls aufgrund eines nicht vertrauenswürdigen Zertifikats für einen lokalen Host eine Fehlernachricht angezeigt wird, klicken Sie auf den in der Fehlernachricht API Designer Explore bereitgestellten Link, um das Zertifikat zu bestätigen; fahren Sie anschließend mit dem Aufrufen der Operationen im Web-Browser fort. Die genaue Vorgehensweise hängt vom jeweils verwendeten Browser ab. Falls Sie die REST-Endpunkte direkt in den Browser laden, wird die folgende Nachricht angezeigt: {"name":"PreFlowError","message":"unable to process the request"}. Sie müssen API Designer Explore zum Testen der REST-Endpunkte in Ihrem Browser verwenden, weil es die erforderlichen Header und Anforderungsparameter umfasst.
>
>![troubleshooting]
>Falls der Antwortcode **422 - Nicht verarbeitbare Entität** mit den folgenden Angaben zurückgegeben wird:
>![](images/explore-test-3.png)
>
>Das Datenelement `id` wurde nicht aus den generierten Daten entfernt. Entfernen Sie das Datenelement `id` und führen Sie den Test erneut durch.
>![troubleshooting]
>Falls der Fehler **Auswertung des Anforderungshauptteils fehlgeschlagen** angezeigt wird, müssen Sie das Komma nach der letzten Nummer für `humidity_high` entfernen.
7. Bearbeiten Sie die Werte in den JSON-Daten wie im Abschnitt **Daten** angegeben. Versuchen Sie, die generierten Testdaten zu ändern, und klicken Sie erneut auf **Operation aufrufen**. Jetzt sollten die Anforderungs- und Antwortparameter sowie die von Ihnen eingegebenen JSON-Instanzdaten angezeigt werden.
![](images/explore-test-4.png)

8. Klicken Sie auf **weather.find**, um zu bestätigen, dass durch die Operation ein Modell hinzugefügt wurde. Klicken Sie auf **Operation aufrufen**, um alle Instanzen von 'weather' anzuzeigen. Beispiel (mit zwei Modellinstanzen):

	![](images/explore-test-5.png)
---

### Was Sie in diesem Lernprogramm erreicht haben
In diesem Lernprogramm haben Sie Folgendes durchgeführt: 
1. Ein neues LoopBack-Projekt in der Befehlszeile des {{site.data.keyword.apiconnect_short}}-Toolkits erstellt.
2. Ein neues Modell und eine neue Datenquelle mit API Designer im {{site.data.keyword.apiconnect_short}} Toolkit zu einem LoopBack-Projekt hinzugefügt.
3. Die API-Endpunkte mit API Designer Explore getestet.


---

## Nächster Schritt

[REST-Service verwalten](tut_rest_landing.html) oder [SOAP-Service verwalten](tut_manage_soap_api.html).

Erstellen > **Verwalten** > Schützen > Teilen > Analysieren

 
[important]: ./images/important.png "Wichtig!"
[info]: ./images/info.png "Information"
[troubleshooting]: ./images/troubleshooting.png "Fehlerbehebung" 

