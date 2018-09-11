---

copyright:
  years: 2017
lastupdated: "2017-12-15"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# APIs erstellen
{: #creating_apis}

Sie können APIs erstellen, indem Sie das Entwicklertoolkit herunterladen und die Befehlszeilenschnittstelle
(Command Line Interface, CLI) oder API Designer verwenden.

## Befehlszeilenschnittstelle von Developer Toolkit
{: #dev_tk_cli notoc}

Von Developer Toolkit wird eine Befehlszeilenschnittstelle (Command Line Interface, CLI) bereitgestellt,
mit der Sie APIs in {{site.data.keyword.apiconnect_long}} veröffentlichen können.
Sie veröffentlichen APIs, indem Sie sie in ein Produkt einbeziehen und anschließend das Produkt veröffentlichen. Sie definieren
eigene APIs und Produkte, indem Sie YAML-Definitionsdateien in Ihrem lokalen Dateisystem erstellen und validieren. Anschließend
können Sie mithilfe der Toolkitbefehle mit {{site.data.keyword.apiconnect_long}}
interagieren.

## API Designer
{: #designer notoc}

API Designer ist eine grafische Offline-Benutzerschnittstelle im Entwicklertoolkit,
die Funktionen zum Erstellen und Konfigurieren von APIs bereitstellt.
API Designer wird mit dem Befehl 'edit' in der Befehlszeilenschnittstelle gestartet. Bei Verwendung des Befehls 'edit' wird API Designer
in Ihrem Standardbrowser geöffnet oder kann über den Port des lokalen Hosts aufgerufen werden, der beim Ausführen
des Befehls angezeigt wird.

## Entwicklertoolkit installieren
{: #install_dev_tk}

### Voraussetzungen
{: #prereq_install_dev_tk}

Bevor Sie beginnen, müssen Sie [Node.js ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://nodejs.org/en/){:new_window}
auf der Maschine installieren, auf der Sie das Toolkit verwenden möchten, und sicherstellen, dass `node` in `PATH` enthalten ist.

Beim Installieren des Entwicklertoolkits werden die folgenden Elemente installiert.

- {{site.data.keyword.apiconnect_short}}-Befehlszeilentool
- {{site.data.keyword.apiconnect_short}}-Editor mit grafischer Oberfläche
- Lokale Instanz von {{site.data.keyword.apiconnect_short}} Micro-Gateway


1. Um das Toolkit zu installieren, öffnen Sie eine Eingabeaufforderung als Administrator und geben
Sie den folgenden Befehl ein.

    ```
    npm install -g apiconnect
    ```
    {: codeblock}

    **Hinweis:** Bei der Installation werden möglicherweise Fehler aus dem Modul `node-gyp` angezeigt. Diese
    Fehler stammen aus einer optionalen Abhängigkeit; die Installation wird erfolgreich ausgeführt.

2. Um eine Zusammenfassung der Hilfeinformationen für die Verwendung aller Toolkitbefehle anzuzeigen, geben Sie den folgenden Befehl ein:

    ```
    apic
    ```
	{: codeblock}

3. Um Hilfeinformationen für die Verwendung eines beliebigen Befehl anzuzeigen, geben Sie die Option `--help` an.
    Beispiel:

    ```
    apic validate --help
    ```
	{: codeblock}
	
## LoopBack-Connector installieren
{: #install_lb_conn}

Vor der Verwendung einer LoopBack-Datenquelle für den Zugriff auf Daten in einem Back-End-System, z. B. in einer Datenbank,
müssen Sie den Datenquellenconnector installieren. Die speicherinternen Connector und E-Mail-Connector sind in LoopBack integriert, d. h. sie müssen
nicht installiert werden.

### Voraussetzungen
{: #prereq_install_lb_conn}

Für die Oracle-, DB2- und SQLLite-Connector sind C-Compiler-Tools für die Erstellung und Installation von Binärprogrammerweiterungen
erforderlich. Die genauen Anforderungen sind von Ihrem Betriebssystem abhängig; dies wird in der folgenden Tabelle
beschrieben.

<table summary="" id="apic_028__table_pre_reqs" class="defaultstyle style-scope doc-content">
<caption>Tabelle 1. Betriebssystemspezifische Installationsvoraussetzungen</caption>
<thead>
<tr>
<th style="width: 33.3%" id="th_d70e208" class="thleft style-scope doc-content">Windows</th>
<th style="width: 33.3%" id="th_d70e210" class="thleft style-scope doc-content">Linux</th>
<th style="width: 33.3%" id="th_d70e212" class="thleft style-scope doc-content">MAC OS X</th>
</tr>
</thead>
<tbody >
<tr class="style-scope doc-content doc-tr-odd">
<td style="width: 33.3%" > [Microsoft .NET Framework 4 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.microsoft.com/en-us/download/details.aspx?id=17851)</td>
<td style="width: 33.3%">Python v2.7 (v3.x wird nicht unterstützt)</td>
<td style="width: 33.3%" > [Python-Releases für Mac OS X ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.python.org/downloads/mac-osx/)</td>
</tr>
<tr><td style="width: 33.3%" > [Visual Studio ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.visualstudio.com/downloads/download-visual-studio-vs)</td>
<td style="width: 33.3%">
<code>make</code>
</td>
<td style="width: 33.3%" > [Xcode ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.apple.com/xcode/?cm_mc_uid=46449280653414622613810&amp;cm_mc_sid_50200000=1459433716)</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 33.3%" > [Python v2.7.10 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.python.org/downloads/release/python-2710/)</td>
<td style="width: 33.3%">Eine C/C++-Compiler-Toolchain, zum Beispiel GCC Version 4.2 oder höher. </td>
<td style="width: 33.3%" >&nbsp;</td>
</tr>
<tr><td style="width: 33.3%" > [Microsoft Windows SDK for Windows 7 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.microsoft.com/en-gb/download/details.aspx?id=8279)</td>
<td style="width: 33.3%">Verwenden Sie in Debian und in von Debian abgeleiteten Distributionen (Ubuntu, Mint usw.) den folgenden Befehl:
<pre class="codeblock style-scope doc-content"><code>apt-get install build-essential</code></pre>
</td>
<td style="width: 33.3%" >&nbsp;</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 33.3%" >npm Version 3. Siehe folgenden Hinweis.</td>
<td style="width: 33.3%">&nbsp;</td>
<td style="width: 33.3%" >&nbsp;</td>
</tr>
</tbody>
</table>

**Hinweis:** Für Windows-Installationen:

- Verwenden Sie Visual Studio Community, wenn Sie nicht beabsichtigten, Visual Studio Enterprise zu erwerben. Starten Sie das Installationsprogramm, wählen Sie
'Visual C++' unter 'Programming Languages' (Programmiersprachen) aus und akzeptieren Sie die
Standardinstallationsposition.

- Für 64-Bit-Builds von Node.js und nativen Modulen ist außerdem das Windows&trade; 7-64-Bit-SDK erforderlich. Wenn die Installation fehlschlägt, versuchen Sie
es mit der Deinstallation aller C++ 2010 x64&amp;x86 Redistributables, die Sie zuerst installiert haben. Wenn Sie Fehler dazu erhalten, dass die 64-Bit-Compiler
nicht installiert sind, benötigen Sie möglicherweise das Compiler-Update für das Windows&trade; SDK 7.1.
- Geben Sie den folgenden Befehl ein, um NPM Version 3 zu installieren:
  ```
  npm install -g npm
  ```
  {: codeblock}
  Stellen Sie dann sicher, dass für den npm-Befehl die korrekte Version verwendet wird:
  ```
  npm -v
  ```
  {: codeblock}
  Wenn die angezeigte Version nicht 3.x.x ist, bearbeiten Sie Ihren Systempfad so, dass `C:\Users\username\AppData\Roaming\npm` alle anderen Einträge außer Kraft setzt.


1. **Optional**:
Öffnen Sie ein neues Shellfenster, wenn Sie API Designer nutzen.

2. Wenn Sie die Compiler-Tools installiert haben, die für Ihr Betriebssystem erforderlich sind, installieren Sie den Connector, indem Sie im Stammverzeichnis
Ihres Projekts den folgenden Befehl eingeben:

```
npm install --save <connector-package>
```
{: codeblock}
Hierbei gilt: `<connector-package>` ist der Name des npm-Pakets für den LoopBack-Connector (siehe Tabelle).

<table summary="" id="apic_connectors_table_pre_reqs" class="defaultstyle style-scope doc-content">
<caption>Tabelle 3. LoopBack-Connector</caption>
<thead>
<tr class="style-scope doc-content doc-tr-even">
<th style="width: 50%" id="th_new_d70e1489" class="thleft style-scope doc-content">Datenquelle</th>
<th style="width: 50%" id="th_new_d70e1491" class="thleft style-scope doc-content">Connectorpaket</th>
</tr>
</thead>
<tbody>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Cloudant</td>
<td style="width: 50%">loopback-connector-cloudant</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">DashDB</td>
<td style="width: 50%">loopback-connector-dashdb</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">DB2</td>
<td style="width: 50%">loopback-connector-db2</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">DB2 for zOS</td>
<td style="width: 50%">loopback-connector-db2z</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Microsoft SQL Server</td>
<td style="width: 50%">loopback-connector-mssql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">MongoDB</td>
<td style="width: 50%">loopback-connector-mongodb</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">MySQL</td>
<td style="width: 50%">loopback-connector-mysql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">Oracle</td>
<td style="width: 50%">loopback-connector-oracle</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">PostgreSQL</td>
<td style="width: 50%">loopback-connector-postgresql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">SOAP-Web-Services</td>
<td style="width: 50%">loopback-connector-soap</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">REST-Web-Services</td>
<td style="width: 50%">loopback-connector-rest</td>
</tr>
</tbody>
</table>

## LoopBack-API mit Befehlszeilenschnittstelle erstellen
{: #create_lb_api}

Im Folgenden wird die Vorgehensweise zum Erstellen einer LoopBack&reg;-API mit der Befehlszeilenschnittstelle (Command Line Interface, CLI) beschrieben.


### Voraussetzungen
{: #prereq_create_lb_api}

In den nachfolgenden Schritten müssen Sie die Katalog-ID für den Katalog angeben,
den Sie verwenden möchten. Führen Sie die folgenden Schritte aus, um die Katalog-ID
abzurufen:  

1. Rufen Sie das {{site.data.keyword.apiconnect_short}} **-Dashboard** auf.

2. Klicken Sie für den Katalog, den Sie verwenden möchten, auf das Symbol **Katalog-ID anzeigen**
<img alt="Symbol für Kettenverbindung zum Anzeigen der Katalog-ID" src="images/chain_link_icon.png">.

3. Kopieren Sie die Katalog-ID. Beispiel:  
  ```
  apic config:set catalog=apic-catalog://<region>.apiconnect.ibmcloud.com/orgs/<username_string>-dev/catalogs/<catalog>
  ```
  {: codeblock}
    Dabei
gilt Folgendes:

    - `<region>` steht für die {{site.data.keyword.Bluemix_notm}}-Region.

    - `<username_string>` steht für die {{site.data.keyword.Bluemix_notm}}-Organisations-ID ohne Symbole. So sähe beispielsweise
`joe@mycompany.com` wie folgt aus: `joemycompanycom`.

    - `<catalog>` steht für den Namen des Katalogs.  

Führen Sie zum Erstellen einer LoopBack-API mit der CLI die folgenden Schritte aus:

1. Um ein Projekt zu erstellen, öffnen Sie eine Befehlszeile und geben Sie Folgendes ein:
  ```
  apic loopback
  ```
  {: codeblock}

2. In der nächsten Eingabeaufforderung werden Sie aufgefordert, einen Namen für Ihre Anwendung festzulegen. Geben Sie einen Namen ein und drücken Sie dann
die **Eingabetaste**.
  ```
  ? Wie lautet der Name für Ihre Anwendung? (<anwendungsname>)
  ```
    
    Das Tool fordert Sie auf, den Namen des Verzeichnisses einzugeben, in dem das Projekt
    erstellt werden soll.
    ```
    ? Verzeichnisnamen für das Projekt eingeben: (<projektverzeichnisname>)
    ```
    
3. Drücken Sie die **Eingabetaste**, um den Namen beizubehalten, den Sie vorher eingegeben hatten, oder geben Sie einen neuen Namen ein und drücken Sie anschließend die **Eingabetaste**. Das Tool fordert Sie auf, den Typ der zu erstellenden
Anwendung auszuwählen:
```
? Welche Art von Anwendung möchten Sie erstellen? (Pfeiltasten verwenden)
  empty-server (eine leere LoopBack-API ohne konfigurierte Modelle oder Datenquellen)
> hello-world (ein Projekt mit einem funktionsfähigen Basisbeispiel, einschließlich Speicherdatenbank)
```

4. Wählen Sie den gewünschten Anwendungstyp aus und drücken Sie die **Eingabetaste**.
Vom Tool wird eine Anzahl an Nachrichten angezeigt, wenn das Projektverzeichnis erstellt und
eine Anzahl an Verzeichnissen und Dateien hinzugefügt werden. Außerdem wird `npm install` zum
Installieren aller Projektabhängigkeiten ausgeführt (wie in `package.json` angegeben).
Dieser Vorgang kann einige Zeit dauern.

5. Vor dem Erstellen eines Modells müssen Sie sicherstellen, dass das Basisverzeichnis des Projekts
als aktuelles Arbeitsverzeichnis verwendet wird. Geben Sie hierfür den folgenden Befehl ein:
    ```
    cd <projektverzeichnisname>
    ```
    {: codeblock}

6. Geben Sie den folgenden Befehl ein, um ein Modell zu erstellen:
    ```
    apic create --type model
    ```
    {: codeblock}

    Das Tool fordert Sie auf, den Namen des Modells anzugeben.

    ```
    ? Modellnamen eingeben:
    ```

7. Geben Sie einen Namen für das Modell ein.
    Ein Modellname darf beliebige alphanumerische Zeichen sowie Gedankenstriche und Unterstreichungszeichen
    enthalten.
    Alle Datenquellen, die Sie zu dem Projekt hinzugefügt haben, werden aufgelistet,
    und das Tool fordert Sie auf, die zu verwendende Datenquelle
    auszuwählen:
    ```
    ? Datenquelle auswählen, der das Element zugeordnet werden soll: (Pfeiltasten verwenden)
    ```

8. Wählen Sie die Datenquelle aus, die Sie verwenden möchten, und drücken Sie die **Eingabetaste**. Das Tool fordert Sie auf, die Basisklasse für das Modell
auszuwählen:
    ```
    ? Basisklasse für das Modell auswählen (Pfeiltasten verwenden)
       Model
    < PersistedModel
      ACL
      AccessToken
      Application
      Change
      Checkpoint
    (Weitere Auswahlmöglichkeiten können durch Vorwärts- oder Rückwärtsblättern angezeigt werden)
    ```
    Weitere Informationen zu jeder Option finden Sie unter [Using built-in models ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://loopback.io/doc/en/lb3/Using-built-in-models.html){:new_window}.

9. Wählen Sie eine Basisklasse aus und drücken Sie die **Eingabetaste**. Das Tool fragt an, ob Sie die REST-API des Modells bereitstellen
möchten.
```
? Zweig über REST-API bereitstellen? (J/n)
```
Wenn das Modell über REST bereitgestellt wird, sind alle Standardoperationen
zum Erstellen, Lesen, Aktualisieren und Löschen über REST-Endpunkte verfügbar.

10. Treffen Sie die gewünschte Auswahl und drücken Sie die **Eingabetaste**.
Wenn Sie sich dafür entschieden haben, das Modell über REST bereitzustellen, werden Sie vom Tool aufgefordert, den
Modellnamen in der Pluralform anzugeben.
```
? Angepasste Pluralform (zur Verwendung bei der Erstellen der REST-URL):
```

11. Drücken Sie die **Eingabetaste**, wenn die Standardregeln der englischen Sprache für die Pluralbildung verwendet
werden sollen.
Das Tool fordert Sie auf anzugeben, ob ein reines Servermodell erstellt werden soll oder
ein allgemeines Modell, das sowohl in der Server- als auch in der
Client-LoopBack-API verwendet werden kann.
```
? Allgemeines Modell oder nur Servermodell? (Pfeiltasten verwenden)
```

12. Treffen Sie mithilfe der Pfeiltasten die gewünschte Auswahl und drücken Sie die **Eingabetaste**.
Das Tool fordert Sie auf, Eigenschaften zu dem Modell hinzuzufügen:
```
Verzweigungseigenschaften hinzufügen
Geben Sie anschließend einen leeren Eigenschaftsnamen ein.
? Eigenschaftsname:
```

13. Geben Sie einen Eigenschaftsnamen ein.
Das Tool fordert Sie auf, den Datentyp für die Eigenschaft
auszuwählen:
```
? Eigenschaftstyp: (Pfeiltasten verwenden)
> string
  number
  boolean
  object
  array
  date
  buffer
```

14. Wählen Sie den Typ 'string' aus und drücken Sie die **Eingabetaste**.
Das Tool fragt an, ob es sich um eine erforderliche Eigenschaft
handelt:
```
? Erforderlich? (J/n)
```

15. Geben Sie `J` oder `n` ein und
drücken Sie anschließend die **Eingabetaste**.
Das Tool fordert Sie auf, eine weitere Eigenschaft
hinzuzufügen:
```
Weitere Verzweigungseigenschaft hinzufügen
Geben Sie anschließend einen leeren Eigenschaftsnamen ein.
? Eigenschaftsname:
```

16. Fügen Sie bei Bedarf einen weiteren Eigenschaftsnamen hinzu. Falls Sie keine weiteren Eigenschaften benötigen, drücken Sie die
**Eingabetaste**, damit das Modell hinzugefügt wird.

Ein LoopBack-Projekt wird standardmäßig mit einer speicherinternen Datenquelle bereitgestellt, die für Entwicklungs- und Testzwecke geeignet ist. Zu einem späteren Zeitpunkt wird es jedoch erforderlich sein, Ihre Modelle mit einer echten Datenquelle wie einem Datenbankserver zu verbinden. Führen Sie die folgenden Schritte aus, um eine Datenquelle hinzuzufügen:

1. Geben Sie den folgenden Befehl ein:
```
apic create --type datasource
```
{: codeblock}
Das Tool fordert Sie auf, den Namen der Datenquelle anzugeben.
```
? Datenquellennamen eingeben:
```

2. Geben Sie einen Namen für die Datenquelle ein.  Ein Datenquellenname darf beliebige alphanumerische Zeichen sowie Gedankenstriche und
Unterstreichungszeichen enthalten. Das Tool fordert Sie auf, den Connector auszuwählen, der für die Datenquelle verwendet werden soll:
```
? Connector für 'myds' auswählen: (Pfeiltasten verwenden)
> In-memory db (supported by StrongLoop); von StrongLoop unterstützte speicherinterne Datenbank
  Email (supported by StrongLoop); von StrongLoop unterstützte E-Mail-Adresse
  MySQL (supported by StrongLoop); von StrongLoop unterstütztes MySQL
  PostgreSQL (supported by StrongLoop); von StrongLoop unterstütztes PostgreSQL
  Oracle (supported by StrongLoop); von StrongLoop unterstütztes Oracle
  Microsoft SQL (supported by StrongLoop); von StrongLoop unterstütztes Microsoft SQL
  MongoDB (supported by StrongLoop); von StrongLoop unterstützte MongoDB
(Weitere Auswahlmöglichkeiten können durch Vorwärts- oder Rückwärtsblättern angezeigt werden)
```

3. Wählen Sie mithilfe der Pfeiltasten den Connector aus, den Sie verwenden möchten, und drücken Sie
anschließend die **Eingabetaste**.
Das Tool fügt die Datenquelle zu dem Projekt hinzu.

4. Geben Sie Ihren Berechtigungsnachweise für Host, Port, Benutzer, Kennwort und Datenbank ein.
Das Tool fordert Sie auf, den LoopBack-Connector zu installieren.
```
Install loopback-connector-<connector>?
```

5. Geben Sie `Ja` ein .
Das Tool installiert den Connector.

Hinweis: Wenn Sie den Oracle-Connector ausgewählt haben, müssen Sie eine Umgebungsvariable in
{{site.data.keyword.Bluemix_notm}} festlegen, damit die Oracle-App gestartet wird. Führen Sie dazu die folgenden
Schritte aus:

1. Wählen Sie in der Benutzerschnittstelle von {{site.data.keyword.Bluemix_notm}}
die Option **Compute** aus.

2. Wählen Sie bei den CF-Anwendungen die Anwendung aus, mit der Sie arbeiten möchten.

3. Klicken Sie auf **Laufzeit**.

4. Wählen Sie **Umgebungsvariablen** aus.

5. Klicken Sie im Abschnitt für benutzerdefinierte Umgebungsvariablen auf **HINZUFÜGEN**.

6. Geben Sie in das Feld **Name** die Zeichenfolge `LD_LIBRARY_PATH` ein.

7. Geben Sie in das Feld **Wert** die Zeichenfolge
`$LD_LIBRARY_PATH:/home/vcap/app/node_modules/instantclient` ein.

8. Klicken Sie auf **Speichern**.

### LoopBack-Projekt testen
{: #test_lb_proj}

Führen Sie die folgenden Schritte aus, um ein LoopBack-Projekt zu testen.

1. **Optional**: Stellen Sie sicher, dass das Basisverzeichnis des Projekts als aktuelles Arbeitsverzeichnis verwendet wird. Geben Sie den folgenden Befehl ein:
```
cd <loopback-projektverzeichnis>
```
Hierbei gilt: `<loopback-project-dir>` ist der Name des Verzeichnisses, in dem das Projekt enthalten ist.
2. Geben Sie den folgenden Befehl ein:
```
apic start
```
Dieser Befehl führt das LoopBack-Projekt (API) und das Micro Gateway lokal aus. Die folgenden Nachrichten werden angezeigt:
```
Waiting for loopback-project to complete deployment.
Waiting for loopback-project-gw to complete deployment.
Service loopback-project (id 1) started on port 4001
Service loopback-project-gw (id 2) started on port 4002
```
Dabei gilt Folgendes: `<loopback-project>` ist der Name des Verzeichnisses, in
dem das Projekt enthalten ist.

Anschließend können Sie beispielsweise unter Verwendung von `curl` beliebige API-Endpunkte testen.
Wenn Sie die API in einem Web-Browser laden möchten, öffnen Sie die Adresse
`http://localhost:4001` in Ihrem Browser. Für das LoopBack-Standardprojekt (Projekttyp 'empty' oder 'hello-world') wird ungefähr Folgendes angezeigt:
```
{"started":"2016-03-07T22:24:55.322Z","uptime":35.839}
```

### LoopBack-Anwendung über die CLI in {{site.data.keyword.Bluemix_notm}} veröffentlichen
{: #pub_lb_app_cli}

Führen Sie die folgenden Schritte aus, um eine LoopBack-Anwendung über die Befehlszeile in {{site.data.keyword.Bluemix_short}} zu veröffentlichen:

1. Geben Sie den folgenden Befehl ein, um sicherzustellen, dass Sie sich auch tatsächlich im Loopback-Projektverzeichnis befinden.
```
cd <loopback-projektverzeichnis>
```
2. Geben Sie den folgenden Befehl ein, um sich an {{site.data.keyword.apiconnect_short}} und {{site.data.keyword.Bluemix_notm}} anzumelden.
```
apic login --server  <region>.apiconnect.ibmcloud.com -u <username> -p <password>
```
Dabei gilt Folgendes:
  * `<username>` steht für Ihre {{site.data.keyword.apiconnect_short}}-Organisations-ID.
  * `<password>` steht für Ihr {{site.data.keyword.apiconnect_short}}-Kennwort.
3. Drücken Sie die Leertaste, damit die Browserseite **Einmaliger Kenncode** automatisch geöffnet wird.
4. Klicken Sie auf **Neu generieren** und kopieren Sie den einmaligen Kenncode.
5. Wenn Sie sich wieder in der CLI befinden, fügen Sie den Kenncode ein, um die Anmeldung zu vervollständigen. Die folgende Nachricht wird angezeigt:
```
Logged into <region>.apiconnect.ibmcloud.com successfully
```
6. Geben Sie den folgenden Befehl ein:
```
apic organizations -s <region>.apiconnect.ibmcloud.com
```
Dabei gilt Folgendes:
  * `<region>` steht für die {{site.data.keyword.Bluemix_notm}}-Region. Beispiel:
  * Die Angabe für die Region ist `eu`, wenn Sie {{site.data.keyword.Bluemix_notm}} London verwenden.
  * Die Angabe für die Region ist `us`, wenn Sie {{site.data.keyword.Bluemix_notm}} Dallas verwenden.
  * Die Angabe für die Region ist `au`, wenn Sie {{site.data.keyword.Bluemix_notm}} Sydney verwenden.

  Wenn Sie nicht sicher sind, wie die Angabe in Ihrem Fall lauten muss, können Sie Ihre Region ermitteln, indem Sie in der Menüleiste auf das {{site.data.keyword.avatar}}-Symbol <img src="images/i-avatar-icon.svg" alt="Avatar-Symbol"/> klicken, um das Widget 'Konto und Unterstützung' zu öffnen und den Inhalt des Regionsfelds zu prüfen.
7. Geben Sie den folgenden Befehl ein, um Ihre Anwendung in {{site.data.keyword.Bluemix_notm}} zu veröffentlichen.
```
apic apps:publish –a <app> -o <org> -s <region>.apiconnect.ibmcloud.com
```
Dabei gilt Folgendes:
  * `<app>` steht für den Namen der App.
  * `<org>` steht für den Namen der {{site.data.keyword.Bluemix_notm}}-Organisation.
  * `<region>` steht für die {{site.data.keyword.Bluemix_notm}}-Region.
Die folgende Ausgabe wird zurückgegeben:
  ```
  ...preparing project
  ...building package for deploy
  ...uploading package
  Runtime published successfully.
  Management URL: https://new-console.stage1.ng.bluemix.net/apps/3aa7087d-b454-4e13-bbc5-8228ebe00eef
  API target urls: apiconnect-3aa7087d-b454-4e13-bbc5-8228ebe00eef.pszetousibmcom-dev.apic.stage1.mybluemix.net
  API invoke tls-profile: client:Loopback-client
  ```

8. Als Nächstes müssen Sie die Produktdefinitionen unter Verwendung der zum Zeitpunkt der Veröffentlichung zurückgegebenen Werte ändern. Führen Sie dazu die folgenden Schritte aus:

    1. Klicken Sie in der Benutzerschnittstelle von API Designer auf **APIs**.
    2. Wählen Sie Ihre API aus.
    3. Klicken Sie auf **Assemblieren**.
    4. Klicken Sie im Assembly-Editor auf das Symbol **Filterrichtlinien**.
    5. Wählen Sie **DataPower-Gateway-Richtlinien** aus.
    6. Doppelklicken Sie auf **Aufrufen**.
    7. Aktualisieren Sie die folgenden Felder mit den in Schritt 7 abgerufenen Werten.
        - **Aufruf-URL**: Fügen Sie die API-Ziel-URL ein. Sie müssen das sichere Protokoll HTTPS angeben. Beispiel:
        ```
        https://apiconnect-33e7b062-092b-4227-af97-047499dab2e7.<Bluemix org>-<Bluemix space>.apic.<domain name>$(request.path)
        ```
        Wenn Sie diesen Wert nicht notiert haben, können Sie ihn durch Aufrufen der in Schritt 7 zurückgegebenen Management-URL abrufen.
        Sie können den Wert auch ermitteln, indem Sie sich an {{site.data.keyword.Bluemix_notm}} anmelden und die Informationen zu Ihrer App aufrufen.
        - **TLS-Profil**: Fügen Sie den Wert für 'API invoke tls-profile' ein. Beispiel:
        ```
        client:Loopback-client
        ```
    8. Klicken Sie auf **Speichern**, um die API zu speichern.

## LoopBack-API mit API Designer erstellen
{: #create_lb_api_design}

Im Folgenden wird die Vorgehensweise zum Erstellen einer LoopBack-API mit API Designer beschrieben.
{:shortdesc}

### Voraussetzungen
{: #prereq_create_lb_api_design}

**Hinweis:** Bei den folgenden Anweisungen wird vorausgesetzt, dass Sie die neueste Version von
Developer Toolkit verwenden. Informationen zum Überprüfen der neuesten Version finden Sie auf der Seite unter [npm ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.npmjs.com/package/apiconnect){:new_window}-Pakets.

Erstellen Sie zuerst ein LoopBack-Projekt mit der CLI (Befehlszeilenschnittstelle). Führen Sie hierfür die folgenden Schritte aus:

1. Um ein Projekt zu erstellen, öffnen Sie eine Befehlszeile und geben Sie Folgendes ein:
  ```
  apic loopback
  ```
  {: codeblock}

2. In der nächsten Eingabeaufforderung werden Sie aufgefordert, einen Namen für Ihre Anwendung festzulegen. Geben Sie einen Namen ein und drücken Sie dann
die **Eingabetaste**.
  ```
  ? Wie lautet der Name für Ihre Anwendung? (<anwendungsname>)
  ```
    
    Das Tool fordert Sie auf, den Namen des Verzeichnisses einzugeben, in dem das Projekt
    erstellt werden soll.
    ```
    ? Verzeichnisnamen für das Projekt eingeben: (<projektverzeichnisname>)
    ```
    
3. Drücken Sie die **Eingabetaste**, um den Namen beizubehalten, den Sie vorher eingegeben hatten, oder geben Sie einen neuen Namen ein und drücken Sie anschließend die **Eingabetaste**. Das Tool fordert Sie auf, den Typ der zu erstellenden
Anwendung auszuwählen:
```
? Welche Art von Anwendung möchten Sie erstellen? (Pfeiltasten verwenden)
  empty-server (eine leere LoopBack-API ohne konfigurierte Modelle oder Datenquellen)
> hello-world (ein Projekt mit einem funktionsfähigen Basisbeispiel, einschließlich Speicherdatenbank)
```

4. Wählen Sie den gewünschten Anwendungstyp aus und drücken Sie die **Eingabetaste**.
Vom Tool wird eine Anzahl an Nachrichten angezeigt, wenn das Projektverzeichnis erstellt und
eine Anzahl an Verzeichnissen und Dateien hinzugefügt werden. Außerdem wird `npm install` zum
Installieren aller Projektabhängigkeiten ausgeführt (wie in `package.json` angegeben).
Dieser Vorgang kann einige Zeit dauern.

5. Vor dem Erstellen eines Modells müssen Sie sicherstellen, dass das Basisverzeichnis des Projekts
als aktuelles Arbeitsverzeichnis verwendet wird. Geben Sie hierfür den folgenden Befehl ein:
```
cd <projektverzeichnisname>
```

**Hinweis:** Wenn Sie aus Ihrem aktuellen Arbeitsverzeichnis das Projektbasisverzeichnis machen,
wird sichergestellt, dass die Option zum Hinzufügen von Modellen und Datenquellen beim Öffnen von API Designer verfügbar ist. Wenn Sie
API Designer öffnen, ohne das Verzeichnis zu wechseln, können Sie keine Modelle und Datenquellen
hinzufügen.

Führen Sie die folgenden Schritte aus, um API Designer zu öffnen:
1. Öffnen Sie eine Befehlszeile und geben Sie Folgendes ein:
```
apic edit
```
    Nach einer kurzen Wartezeit wird die folgende Nachricht angezeigt.
    ```
    Express server listening on http://127.0.0.1:9000
    ```
    API Designer wird in Ihrem Standard-Web-Browser geöffnet.

2. Geben Sie auf der Anmeldeseite Ihre {{site.data.keyword.Bluemix_notm}}-ID und das
zugehörige Kennwort ein. Klicken Sie auf**Anmelden**.

3. Klicken Sie auf **Modelle**.

4. Klicken Sie auf **Hinzufügen**. Das Fenster **LoopBack-Modell** wird geöffnet.

5. Geben Sie einen Modellnamen ein.
Ein Modellname darf beliebige alphanumerische Zeichen sowie Gedankenstriche und Unterstreichungszeichen
enthalten.

6. Klicken Sie auf **Neu**.

7. Navigieren Sie auf der Seite des Modelleditors zu den Eigenschaften und klicken Sie auf **Hinzufügen**.

8. Geben Sie den Eigenschaftsnamen ein und wählen Sie einen Typ aus.

9. Klicken Sie nach dem Angeben der Eigenschaften für das Modell auf **Speichern**.

In einem leeren LoopBack-Projekt sind standardmäßig keine Datenquellen definiert. Führen Sie die folgenden Schritte aus, um eine Datenquelle zu definieren:
1. Klicken Sie auf **Datenquellen**.

2. Klicken Sie auf das Symbol **Hinzufügen**.
Das Fenster **Neues LoopBack-Modell** wird geöffnet.

3. Geben Sie einen Datenquellennamen ein. Ein Datenquellenname darf beliebige alphanumerische Zeichen sowie Gedankenstriche und
Unterstreichungszeichen enthalten.

4. Klicken Sie auf **Neu**.
Die Datenquelle wird in der Liste der Datenquellen angezeigt und der Editor aktualisiert
die Datei `server/datasources.json` mit den Einstellungen für die neue Datenquelle.

5. Klicken Sie auf Ihre Datenquelle, um die zugehörigen Einstellungen anzuzeigen.

6. Geben Sie in den Connectoreinstellungen den erforderlichen Connector an.

7. Rufen Sie wieder die Konsole auf, über die Sie API Designer gestartet haben, und installieren
Sie den Connector, indem Sie den folgenden Befehl eingeben:
```
npm install --save <connector-package>
```
    Hierbei gilt: `<connector-package>` ist der Name des npm-Pakets für den LoopBack-Connector, den Sie ausgewählt haben. Die folgende Tabelle enthält eine Liste der Connectorpakete.

**Hinweis:** Die speicherinternen Connector und E-Mail-Connector sind in LoopBack integriert, d. h. sie müssen nicht installiert werden.

<table>
<caption>Tabelle 3. LoopBack-Connector</caption>
<thead>
<tr class="style-scope doc-content doc-tr-even">
<th style="width: 50%" id="3rd_d70e1489" class="thleft style-scope doc-content">Datenquelle</th>
<th style="width: 50%" id="3rd_d70e1491" class="thleft style-scope doc-content">Connectorpaket</th>
</tr>
</thead>
<tbody>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Cloudant</td>
<td style="width: 50%">loopback-connector-cloudant</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">DashDB</td>
<td style="width: 50%">loopback-connector-dashdb</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">DB2</td>
<td style="width: 50%">loopback-connector-db2</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">DB2 for zOS</td>
<td style="width: 50%">loopback-connector-db2z</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Microsoft SQL Server</td>
<td style="width: 50%">loopback-connector-mssql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">MongoDB</td>
<td style="width: 50%">loopback-connector-mongodb</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">MySQL</td>
<td style="width: 50%">loopback-connector-mysql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">Oracle</td>
<td style="width: 50%">loopback-connector-oracle</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">PostgreSQL</td>
<td style="width: 50%">loopback-connector-postgresql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">SOAP-Web-Services</td>
<td style="width: 50%">loopback-connector-soap</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">REST-Web-Services</td>
<td style="width: 50%">loopback-connector-rest</td>
</tr>
</tbody>
</table>

Weitere Informationen finden Sie in der [LoopBack-Dokumentation unter Building a Connector ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://loopback.io/doc/en/lb3/Defining-data-sources.html){:new_window}.

**Hinweis:** Wenn Sie den Oracle-Connector ausgewählt haben, müssen Sie eine Umgebungsvariable in
{{site.data.keyword.Bluemix_notm}} festlegen, damit die Oracle-App gestartet wird. Führen Sie dazu die folgenden
Schritte aus:

1. Wählen Sie in der Benutzerschnittstelle von {{site.data.keyword.Bluemix_notm}}
die Option **Compute** aus.

2. Wählen Sie bei den CF-Anwendungen die Anwendung aus, mit der Sie arbeiten möchten.

3. Klicken Sie auf **Laufzeit**.

4. Wählen Sie **Umgebungsvariablen** aus.

5. Klicken Sie im Abschnitt für benutzerdefinierte Umgebungsvariablen auf **HINZUFÜGEN**.

6. Geben Sie in das Feld **Name** die Zeichenfolge `LD_LIBRARY_PATH` ein.

7. Geben Sie in das Feld **Wert** die Zeichenfolge
`$LD_LIBRARY_PATH:/home/vcap/app/node_modules/instantclient` ein.

8. Klicken Sie auf **Speichern**.

Führen Sie die folgenden Schritte aus, um ein LoopBack-Projekt zu testen:
1. Klicken Sie auf das Symbol **Server starten**.
Die folgende Nachricht wird angezeigt:
```
http://localhost:<4001/>Running
```
In Abhängigkeit von Ihrer Projektkonfiguration und den weiteren aktiven Prozessen wird möglicherweise
eine andere Portnummer angezeigt.

2. Klicken Sie auf **localhost:4001**, um den API-Stammendpunkt anzuzeigen. Für das LoopBack-Standardprojekt
(Projekttyp 'empty' oder 'hello-world') wird in etwa
Folgendes angezeigt:
```
{"started":"2017-03-07T22:24:55.322Z","uptime":35.839}
```

Erstellen Sie als Nächstes ein Produkt. Weitere Informationen finden Sie in [Produkt erstellen](managing_products.html#create_product).
**Tipp:** Wann immer Sie eine neue Eingabeaufforderung öffnen, müssen Sie sicherstellen, dass Ihr aktuelles Arbeitsverzeichnis das
Basisverzeichnis des Projekts ist. Geben Sie hierfür den folgenden
Befehl ein:
```
cd <projektverzeichnisname>
```

## Entwicklertoolkit deinstallieren
{: #uninstall_dev_tk}

### Voraussetzungen
{: #prereq_uninstall_dev_tk}

Als Vorbereitung müssen Sie den folgenden Befehl eingeben, um alle lokal ausgeführten Apps zu
stoppen:
```
apic stop --all
```

Führen Sie die folgenden Schritte aus, um Developer Toolkit zu deinstallieren:

1. Geben Sie den folgenden Befehl ein:
```
npm rm -g apiconnect
```
{: codeblock}

2. Löschen Sie Ihren npm-Cache:
```
npm cache clean
```
{:codeblock}
  
Bei Verwendung von Windows:

3. Löschen Sie alle Dateien, deren Namen mit `npm-` beginnen, im Verzeichnis `C:\Users\username\AppData\Local\Temp`.
4. Löschen Sie das Verzeichnis `<home_dir>\.apiconnect`; hierbei steht `<home_dir>` für das Stammverzeichnis des Benutzerkontos, unter dessen Verwendung das Toolkit vorher installiert wurde.
