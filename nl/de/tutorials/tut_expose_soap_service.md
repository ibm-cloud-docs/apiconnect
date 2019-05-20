---

copyright:
years: 2019
lastupdated: "2019-3-12"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
 

# SOAP-Service als REST-API verfügbar machen
{: #tut_expose_soap_service}

**Dauer**: 20 Minuten  
**Kenntnisstufe**: Anfänger  

---
## Lernziel
{: #object_tut_expose_soap_service}

Sie erstellen in API Manager eine REST-API, die auf einen vorhandenen SOAP-Service zugreift und diesen als REST-API verfügbar macht.

## Voraussetzungen
{: #prereq_tut_expose_soap_service}

1. Bevor Sie beginnen, müssen Sie [eine Instanz von {{site.data.keyword.apiconnect_full}} einrichten](/docs/services/apiconnect?topic=apiconnect-tut_prereq_set_up_apic_instance).
2. Bevor Sie beginnen, müssen Sie die Testdatei [weatherprovider.wsdl ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://raw.githubusercontent.com/IBM-Bluemix-Docs/apiconnect/master/tutorials/weatherprovider.wsdl){: #new_window} in Ihr lokales Dateisystem kopieren.
	>![images/info.png]
	>Sie können auf **Unbearbeitet** klicken und anschließend die resultierende Seite im lokalen System als `.wsdl`-Datei speichern.

---
## REST-API-Definition festlegen
{: #setup_tut_expose_soap_service}

1. Melden Sie sich bei {{site.data.keyword.Bluemix_short}} an: https://cloud.ibm.com.
2. Klicken Sie im {{site.data.keyword.Bluemix_notm}}-**Dashboard** auf **Cloud Foundry-Services**.Starten Sie den {{site.data.keyword.apiconnect_short}}-Service. 
3. Stellen Sie in {{site.data.keyword.apiconnect_short}} sicher, dass das Navigationsfenster geöffnet ist. Falls dies nicht der Fall ist, klicken Sie auf **>>**, um es zu öffnen.  

  ![](images/cloud-apic-dashboard.png)

4. Wählen Sie im Navigationsfenster **Entwürfe** aus.
5. Wählen Sie **Hinzufügen +** > **Neue API** aus.

    ![](images/cloud-add-api-new.png)  

	
6. Geben Sie die Basisinformationen zur API an.
	- Geben Sie in das Feld **Titel** die Zeichenfolge `Weather Data` ein.
	- Belassen Sie im Feld **Name** die Angabe `weather-data`, wenn es gefüllt wird, während Sie den Titel eingeben.	
	- Übernehmen Sie im Feld **Basispfad** den Wert `/weather-data`.
	- Lassen Sie im Feld **Version** die Angabe `1.0.0` unverändert.
7. Erweitern Sie **Zusätzliche Eigenschaften**, um weitere Eigenschaften für die API anzugeben.
	- Wählen Sie im Feld **API-Vorlage** die Angabe **Standard** aus, um festzulegen, dass Sie die Standardvorlage zum Erstellen einer API-Definition verwenden möchten.
	- Lassen Sie die übrigen Felder unverändert.
	![](images/new-api-1.png)
8. Fügen Sie die API zum neuen Produkt hinzu und erstellen Sie anschließend die API-Definition.
	- Wählen Sie **Produkt hinzufügen** aus.
	- Verwenden Sie im Feld **Titel** die Zeichenfolge `Weather Data product` als Standardeinstellung.
	- Belassen Sie die Felder **Name** und **Version** unverändert.
	- Stellen Sie sicher, dass das Kontrollkästchen **Dieses Produkt in einem Katalog veröffentlichen** ausgewählt ist und wählen Sie anschließend **Sandbox** als Zielkatalog aus.
	![](images/new-api-2.png)
	- Klicken Sie auf **API erstellen**. Die Registerkarte **Design** zum Entwerfen der API-Definition wird geöffnet.
9. Die API wird jetzt erstellt. Die Seite 'Design' wird angezeigt.

   ![](images/design-new-1.png)

10. Klicken Sie in der Navigationsleiste auf **Definitionen**. Klicken Sie auf das Symbol **Definition hinzufügen** ![](images/add-icon.png).

11. Erweitern Sie die neue Definition, indem Sie darauf klicken. 
12. Legen Sie für die Definition den Namen `Wetterdatenausgabe` fest.
13. Die Definition besteht aus fünf Eigenschaften. Klicken Sie vier Mal auf **Eigenschaft hinzufügen**, um die zusätzlichen Eigenschaften hinzuzufügen. Benennen Sie den `Eigenschaftsnamen` um, indem Sie sich nach der folgenden Anleitung richten, und verwenden Sie die Standardeinstellungen für `Beschreibung`, `Typ` und `Beispiel`:
    a. Fügen Sie neue Eigenschaften für die Definition der **Wetterdatenausgabe** hinzu.     
       - Name: Postleitzahl /  Typ: Zeichenfolge   
       - Name: Temperatur   /  Typ: Ganzzahl   
       - Name: Feuchtigkeit /  Typ: Ganzzahl   
       - Name: Ort          /  Typ: Zeichenfolge   
       - Name: Status       /  Typ: Zeichenfolge   

	![](images/definition-new-1.png)
14. Klicken Sie in der Navigationsleiste auf **Pfade**. Klicken Sie auf das Symbol **Pfad hinzufügen** ![](images/add-icon.png).
15. Legen Sie für den **Titel** des neu erstellten Pfads `/getweatherdata` fest.
16. Erweitern Sie die Operation **GET /getweatherdata** durch Klicken auf dieselbe.
	![](images/path-new-1.png)
17. Klicken Sie für die Operation **GET /getweatherdata** auf **Parameter hinzufügen** und klicken Sie anschließend auf **Neuen Parameter hinzufügen**.
18. Legen Sie für den neuen Parameter den Namen `zip_code` fest und belassen Sie für den Rest die Standardeinstellung.
19. Wählen Sie in der Spalte **Schema** der Antwort **200 OK** im Abschnitt **Antworten** die Definition **Wetterdatenausgabe** aus. Die Antwort auf den API-Aufruf ist das Antwortobjekt, das unter **Wetterdatenausgabe** definiert ist.
	![](images/path-new-2.png)
20. Klicken Sie auf das Speichersymbol ![](images/save-icon.png), um die Änderungen zu speichern.

---
## Web-Service-Aufruf hinzufügen und konfigurieren
{: #add_web_tut_expose_soap_service}

Führen Sie die nachfolgenden Schritte aus, um den Aufruf hinzuzufügen und zu konfigurieren und um die Richtlinien zuzuordnen, mit deren Hilfe der Web-Service in die API-Definition integriert wird.
1. Klicken Sie im Abschnitt **Services** auf das Symbol **Service hinzufügen** ![](images/add-icon.png). Das Fenster `Web-Service aus WSDL-Datei importieren` wird geöffnet.
	![](images/upload-file-1.png)
2. Wählen Sie **Datei hochladen** aus.
3. Geben Sie im Fenster **Dateiupload** die Position für die Datei `weatherprovider.wsdl` an, die Sie in `Schritt 2` im Abschnitt **Voraussetzungen** heruntergeladen haben, und klicken Sie auf **Öffnen**, um fortzufahren.
4. Wählen Sie den SOAP-Service **weatherService** aus und klicken Sie auf **Fertig**. Im Abschnitt **Services** wird der Web-Service **WeatherService** mit der einzigen Operation **weatherRequest** aufgelistet.
	![](images/upload-file-2.png)

	![](images/services-add-1.png)	
5. Navigieren Sie zur Registerkarte **Assemblieren** und stellen Sie sicher, dass **DataPower-Gateway-Richtlinien** ausgewählt ist.
6. Löschen Sie die vorhandene Richtlinie **invoke** im Erstellungsbereich; bewegen Sie hierzu den Cursor über die Richtlinie und klicken Sie anschließend auf das Symbol **Richtlinie löschen** ![](images/delete-icon.png).
	![](images/delete-invoke-1.png)	
7. Ziehen Sie den Web-Service **weatherRequest** aus der Palette in das gestrichelte Feld, das im Erstellungsbereich angezeigt wird. In der Assembly befinden sich eine Aufrufrichtlinie (invoke) und zwei Zuordnungsrichtlinien. Von der ersten Zuordnungsrichtlinie werden Variablen der Eingabe des Web-Service-Aufrufs zugeordnet, von der zweiten Richtlinie werden die Ausgaben des Web-Service-Aufrufs den Variablen zu zugewiesen. Die Ausgaben der ersten Zuordnung und die Eingaben der zweiten Zuordnung werden aus der WSDL-Datei generiert, die in Schritt 4 bereitgestellt wurde.
	![](images/services-add-2.png)	
8. Klicken Sie auf die Zuordnungsrichtlinie **weatherRequest: input** und klicken Sie anschließend auf das Symbol **Eingaben bearbeiten** ![](images/edit-icon.png) in der Eingabespalte der Eigenschaftsseite.
	![](images/services-add-3.png)	
9. Klicken Sie auf **+ Parameter für Operation** und wählen Sie `get /getweatherdata` aus.
10. Klicken Sie auf **Fertig**, um den Parameter `zip_code` hinzuzufügen.
	![](images/webservice-input-1.png)
11. Klicken Sie auf den Kreis, der **zip_code string** auf der Eingabeseite zugeordnet ist, und klicken Sie anschließend auf den Kreis, der **zipcode string** auf der Ausgabeseite zugeordnet ist.  
	![](images/webservice-input-2.png)
12. Schließen Sie die Eigenschaftsseite.
13. Klicken Sie auf die Zuordnungsrichtlinie **weatherRequest: output** in der Palette und klicken Sie anschließend auf das Symbol **Ausgaben bearbeiten** ![](images/edit-icon.png) in der Ausgabespalte des Eigenschaftenblatts.
14. Wählen Sie **+ Ausgaben für Operation** und anschließend `get /getweatherdata` aus.
15. Wählen Sie **Fertig** aus, um die Ausgabedefinition `Wetterdatenausgabe` hinzuzufügen.
	![](images/webservice-output-1.png)
16. Klicken Sie auf den Kreis, der **zip string** auf der Eingabeseite zugeordnet ist, und klicken Sie anschließend auf den Kreis, der **zip string** auf der Ausgabeseite zugeordnet ist. Ordnen Sie die übrigen Parameter gemäß der folgenden Vorgehensweise zu.
	![](images/webservice-output-2.png)
17. Klicken Sie auf das Symbol **Speichern** ![](images/save-icon.png), um Ihre Änderungen zu speichern.

Sie haben den Web-Service-Aufruf in die Assembly eingeschlossen und einen Eingabeparameter zum entsprechenden Teil der SOAP-Anforderung zugeordnet und den entsprechenden Teil der SOAP-Antwort einer JSON-Ausgabe zugeordnet.

---
## API-Definition testen
{: #test_tut_expose_soap_service}

Führen Sie die nachfolgenden Schritte aus, um die API-Definition mithilfe des Testtools von API Manager zu testen.
1. Klicken Sie auf das Symbol **Testen** ![](images/test-icon.png) unter der Registerkarte **Assembly**, um das Testfenster anzuzeigen.
	![](images/test-pane-1.png)
2. Falls Sie das Testtool bereits vorher verwendet haben, klicken Sie auf **Konfiguration ändern**.
3. Wählen Sie in der Liste der Produkte `Weather Data product 1.0.0` aus.
	![](images/choose-product-1.png)
4. Klicken Sie auf **Produkt erneut veröffentlichen**.
5. Klicken Sie auf **Weiter**.
6. Wählen Sie in der Liste der Operationen `get /getweatherdata` aus.  
	![](images/select-operation-1.png)
7. Blättern Sie abwärts bis zum Feld **zip_code** und geben Sie `10504` ein.  
	![](images/test-api-1.png)
8. Klicken Sie auf **Aufrufen**. Von der API wird das aktuelle Wetter zurückgegeben.  
	![](images/test-wdata-result.png)

---
## Fazit
{: #conclusion_tut_expose_soap_service}

In diesem Lernprogramm haben Sie Folgendes durchgeführt:
1. REST-API-Definition festgelegt
2. API zum Aufrufen eines vorhandenen Web-Service und Zurückgeben seiner Ausgabe konfiguriert
3. API-Definition getestet

---

## Nächster Schritt
{: #next_tut_expose_soap_service}

API schützen wie in [Schutz durch OAuth 2.0](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_oauth_2) beschrieben.

Erstellen > **Verwalten** > Schützen > Teilen > Analysieren

[important]: ./images/important.png "Wichtig!"
[info]: ./images/info.png "Information"
[troubleshooting]: ./images/troubleshooting.png "Fehlerbehebung" 
