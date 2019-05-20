---
copyright:
  years: 2019
lastupdated: "2019-3-9"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# API-Spezifikation hinzufügen und REST-Service mit {{site.data.keyword.Bluemix_notm}} aufrufen
{: #tut_add_openapi_rest_bm}

**Dauer**: 15 Minuten  
**Kenntnisstufe**: Anfänger  

## Lernziel
{: #object_tut_add_openapi_rest_bm}

Dieses Lernprogramm unterstützt Sie beim Einstieg in {{site.data.keyword.apiconnect_full}}. Sie erstellen in wenigen Minuten eine neue API, die als API-Durchgriffsproxy für einen vorhandenen REST-Service fungiert. Die erstellte API dient zur Sicherheit und Überwachung. 

## Voraussetzung
{: #prereq_tut_add_openapi_rest_bm}

Bevor Sie beginnen, müssen Sie [eine Instanz von API Connect einrichten](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_set_up_apic_instance).

---

### Beispielapp untersuchen und Zielendpunkt testen
{: #expl_tut_add_openapi_rest_bm}

Für dieses Lernprogramm wurde die Beispielapp _weather provider_ erstellt.
1. Rufen Sie [http://gettingstartedweatherapp.mybluemix.net/ ![Symbol für externen Link](../../../icons/launch-glyph.svg "Symbol für externen Link")](http://gettingstartedweatherapp.mybluemix.net/){: #new_window} auf, um die App kennenzulernen.  
2. Geben Sie eine gültige fünfstellige US-Postleitzahl ein, um Angaben zum _**aktuellen Wetter**_ und zur _**Vorhersage für heute**_ zu erhalten.  
![](images/explore-weatherapp-1.png)

3. Die obige Beispielwetterapp wurde mithilfe von APIs erstellt, von denen die Wetterdaten bereitgestellt werden. Der Endpunkt zum Abrufen der **aktuellen** Wetterdaten ist _**https://myweatherprovider.mybluemix.net/current?zipcode={zipcode}**_. Testen Sie ihn durch Aufrufen von [https://myweatherprovider.mybluemix.net/current?zipcode=90210 ![Symbol für externen Link](../../../icons/launch-glyph.svg "Symbol für externen Link")](https://myweatherprovider.mybluemix.net/current?zipcode=90210){: #new_window}.  

  ![](images/explore-weatherapp-2.png)

4. Analog ist der Endpunkt zum Abrufen der Vorhersagedaten von **heute** der Link _**https:// myweatherprovider<span></span>.mybluemix.net/today?zipcode={zipcode}**_. Testen Sie ihn durch Aufrufen von [https://myweatherprovider.mybluemix.net/today?zipcode=90210 ![Symbol für externen Link](../../../icons/launch-glyph.svg "Symbol für externen Link")](https://myweatherprovider.mybluemix.net/today?zipcode=90210){: #new_window}.  

  ![](images/explore-weatherapp-3.png)


---

### Neue OpenAPI-Spezifikation zum Erstellen eines REST-API-Proxy hinzufügen  
{: #add_spec_tut_add_openapi_rest_bm}

1. Melden Sie sich bei {{site.data.keyword.Bluemix_short}} an: https://cloud.ibm.com.
2. Klicken Sie im {{site.data.keyword.Bluemix_notm}}-**Dashboard** auf **Cloud Foundry-Services**.Starten Sie den {{site.data.keyword.apiconnect_short}}-Service. 
3. Stellen Sie in {{site.data.keyword.apiconnect_short}} sicher, dass das Navigationsfenster geöffnet ist. Falls dies nicht der Fall ist, klicken Sie auf **>>**, um es zu öffnen.  

  ![](images/cloud-apic-dashboard.png)

4. Wählen Sie im Navigationsfenster **Entwürfe** aus.
5. Klicken Sie in der Registerkarte **APIs** auf **Hinzufügen**. Wählen Sie im Dropdown-Menü **Neue API** aus.    
  ![](images/cloud-add-api-new.png)  
6. Geben Sie im Fenster *Neue API* den Titel `Neue Wetter-Provider-API` ein.
_Name und Basispfad werden automatisch generiert_.  
  ![](images/bluemix-add-new-api2.png)
7. Klicken Sie auf **API erstellen**, um den Assistenten zu beenden.  
8. Nach der Erstellung der API ist die Registerkarte **Entwurf** ausgewählt. 
9. Blättern Sie zur Anzeige **Host**. Geben Sie `$(catalog.host)` als Wert ein, wenn das Feld nicht automatisch gefüllt wurde.
10. Notieren Sie sich in der Anzeige **Basispfad** den automatisch ausgefüllten Wert `/new-weather-provider-api`. Die Ziel-URL der API wird anhand dieser Werte erstellt.  


11. Nun müssen Sie das Antwortobjekt definieren, das beim Aufrufen der Wetter-API zurückgegeben wird. Klicken Sie hierzu in der Navigationsleiste auf **Definitionen**.    
    a. Fügen Sie eine neue Definition hinzu.  
    b. Legen Sie als Name für die neue Definition _Aktuell_ fest.  
    c. Definieren Sie für sie den Typ _Objekt_.  
    d. Fügen Sie für die Definition **Aktuell** neue Eigenschaften hinzu.    
       - Name: Postleitzahl /  Typ: Zeichenfolge   
       - Name: Temperatur   /  Typ: Ganzzahl   
       - Name: Feuchtigkeit /  Typ: Ganzzahl   
       - Name: Ort          /  Typ: Zeichenfolge   
       - Name: Status       /  Typ: Zeichenfolge   
	   
    ![](images/definition-current-1.png)   
	
    e. Speichern Sie die API.  

12. Erstellen Sie eine neue Definition: **Heute**.

13. Fügen Sie für die Definition **Heute** neue Eigenschaften hinzu.
    - Name: Postleitzahl /  Typ: Zeichenfolge
    - Name: Hoch         /  Typ: Ganzzahl
    - Name: Niedrig      /  Typ: Ganzzahl
    - Name: FeuchtNacht  /  Typ: Ganzzahl
    - Name: FeuchtTag    /  Typ: Ganzzahl
    - Name: Ort          /  Typ: Zeichenfolge
    - Name: Status       /  Typ: Zeichenfolge

14. Nachdem nun die Datenformate definiert sind, können Aufrufpfade erstellt werden. Klicken Sie in der Navigationsleiste auf **Pfade**. Erstellen Sie einen neuen Pfad, indem Sie auf **+** klicken.      
    a. Legen Sie für den neuen Pfad den Namen "**/current**" fest.  
    b. Wählen Sie in derselben Anzeige *Pfade* den Abschnitt **GET /current** aus.    
    c. Fügen Sie im Abschnitt **GET /current** einen neuen **Parameter** hinzu. Wie schon beim Beschreiben der Beispielapp erläutert, ist für den Wetterdienst eine Postleitzahl als Parameter erforderlich.   
      - Name: Postleitzahl  
      - Befindet sich in: Abfrage  
      - Erforderlich: Ja  
      - Typ: Zeichenfolge   
	  
    ![](images/path-current-1.png)   
	
    d. Blättern Sie abwärts.  Ändern Sie im Abschnitt **Antworten** das **Schema** in _Aktuell_.   
	
	![](images/path-current-responses.png)
	
	e. Speichern Sie die API.  

15. Wiederholen Sie die Aktionen, die Sie in Schritt 11 ausgeführt haben, um einen weiteren Pfad mit der Bezeichnung "**/today**" zu erstellen.  In diesem Fall legen Sie für das Schema **Antworten** den Wert _Heute_ fest. Speichern Sie die API.

16. Speichern Sie die API.

17. Wechseln Sie zur Registerkarte **Assemblieren**. Sie haben bisher zwei Operationen erstellt: **GET /current** und **GET /today**. Um sicherzustellen, dass der korrekte Endpunkt aufgerufen wird, müssen Sie eine Logik erstellen, die abhängig von der jeweils aufgerufenen Operation ausgeführt wird. Hierfür wird die Logikanweisung **Operation Switch** verwendet.  Von **Operation Switch** wird ein Entscheidungspunkt bereitgestellt. Abhängig vom Verb/Pfad-Paar muss die entsprechende Operation aufgerufen werden.

    a. Löschen Sie die Richtlinie für den **Aufruf**, die unter Umständen bereits zum _Erstellungsbereich_ hinzugefügt wurde.  
    b. Ziehen Sie **Operation Switch** aus der Palette und legen Sie die Anweisung im Erstellungsbereich ab.  
      - Ordnen Sie dem Fall **case 0** die Operation **get /current** zu.
      - Fügen Sie den neuen Fall **case 1** hinzu.
      - Ordnen Sie die Operation **get /today** dem Fall **case 1** zu.
      
	  
	  
      ![](images/new-assemble-1.png)
	  
    c. Ziehen Sie die Richtlinie für den **Aufruf** aus der Palette und legen Sie sie in der Verarbeitungszeile unter **get /current** ab. _Eine Aufrufaktion (invoke) wird zum Aufrufen eines vorhandenen Service in einer Operation verwendet._.   
    d. Aktualisieren Sie den Aktionstitel in "**Aufruf-aktuell**".  
    e. Aktualisieren Sie das Feld 'URL' anhand von `https://myweatherprovider.mybluemix.net/current?zipcode=$(request.parameters.zipcode)`.  
	
	![](images/new-assemble-invoke1.png)
	
	
	f. Ziehen Sie die Richtlinie für den **Aufruf** aus der Palette und legen Sie sie in der Verarbeitungszeile unter **get /today** ab.  
    g. Aktualisieren Sie den Titel in "**Aufruf-heute**".  
    h. Aktualisieren Sie das Feld 'URL' anhand von `https://myweatherprovider.mybluemix.net/today?zipcode=$(request.parameters.zipcode)`.  
	
       ![](images/new-assemble-invoke2.png)
	   

18. Schließen Sie die Aktionskonfigurationsanzeige. Speichern Sie die API.

---

### API-Proxy testen
{: #test_proxy_tut_add_openapi_rest_bm}

1. Klicken Sie in der Registerkarte **Assemblieren** auf das Symbol für mehr Aktionen und wählen Sie anschließend **Standardprodukt auswählen** aus.  
   ![](images/generate-default-product-small.png) 

2. Bestätigen Sie die Standardoptionen im Dialogfeld **Neues Produkt** und klicken Sie auf **Produkt erstellen**. Das Produkt 'Wetter-Provider-API' wird erstellt und im Sandbox-Katalog veröffentlicht. Eine Nachricht über die erfolgreiche Generierung des Produkts wird angezeigt.  

  ![](images/generate-default-product-new-weather.png) 

  - _In {{site.data.keyword.apiconnect_short}} wird mithilfe von **Produkte** eine Möglichkeit zum Gruppieren von APIs bereitgestellt, die für eine bestimmte Verwendung vorgesehen sind. Die Produkte werden in einem **Katalog** veröffentlicht. [{{site.data.keyword.apiconnect_short}}-Glossar](../apic_glossary.html)_

3. Klicken Sie in der Registerkarte 'Assemblieren' auf das Wiedergabesymbol, um den Zielaufruf des API-Proxys zu testen.

4. Wählen Sie in der Testanzeige die Operation **get /current** aus.

	a. Da die Postleitzahl für diese Operation ein erforderlicher Parameter ist, geben Sie eine gültige US-Postleitzahl ein (z. B. 10504). 
	
	![](images/test-invoke-params.png)  
		
	b. Klicken Sie auf **Aufrufen**.   

	_Falls ein CORS-Fehler auftritt, gehen Sie gemäß den Anweisungen in der Fehlernachricht vor. Klicken Sie auf den Link im Fehler, um die Ausnahmebedingung zum Browser hinzuzufügen und klicken Sie anschließend erneut auf die Schaltfläche zum Aufrufen._
  
    ![](images/test-invoke-new.png)  


---

### Fazit
{: #conclusion_tut_add_openapi_rest_bm}

In diesem Lernprogramm haben Sie gelernt, wie ein vorhandener REST-Service über einen Durchgriffs-API-Proxy aufgerufen werden kann. Als ersten Schritt haben Sie die Verfügbarkeit des Beispielservice über den Web-Browser getestet. Anschließend haben Sie eine neue OpenAPI-Spezifikation in {{site.data.keyword.apiconnect_short}} erstellt und mit dem Beispielservice verknüpft, der aufgerufen werden soll. Sie haben die API in ein Produkt gepackt, das Produkt im Katalog veröffentlicht und den Proxy getestet.

---

## Nächster Schritt
{: #next_tut_add_openapi_rest_bm}

API schützen wie in [Schutz durch OAuth 2.0](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_oauth_2) beschrieben.

Erstellen > **Verwalten** > Schützen > Teilen > Analysieren
