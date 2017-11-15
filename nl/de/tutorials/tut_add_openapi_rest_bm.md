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

# Neue API-Spezifikation hinzufügen und vorhandenen REST-Service mit IBM Bluemix aufrufen
**Dauer**: 15 Minuten  
**Kenntnisstufe**: Anfänger  

## Lernziel
Dieses Lernprogramm unterstützt Sie beim Einstieg in {{site.data.keyword.apiconnect_full}}. In einem ersten Schritt wird eine neue OpenAPI-Spezifikation erstellt, anschließend ein Durchgriffs-API-Proxy für einen vorhandenen REST-Service.

## Voraussetzung
Bevor Sie beginnen, müssen Sie [eine Instanz von API Connect einrichten](tut_prereq_set_up_apic_instance.html).

---

### Beispielapp untersuchen und Zielendpunkt testen
Für dieses Lernprogramm wurde die Beispielapp _weather provider_ erstellt. 
1. Rufen Sie [http://gettingstartedweatherapp.mybluemix.net/ ![Symbol für externen Link](../../../icons/launch-glyph.svg "Symbol für externen Link")](http://gettingstartedweatherapp.mybluemix.net/){:new_window} auf, um die App kennenzulernen.  
2. Geben Sie eine gültige fünfstellige US-Postleitzahl ein, um Angaben zum _**aktuellen Wetter**_ und zur _**Vorhersage für heute**_ zu erhalten.  
![](images/explore-weatherapp-1.png)

3. Die obigen Beispielwetterapp wurde mithilfe von APIs erstellt, von denen die Wetterdaten bereitgestellt werden. Der Endpunkt zum Abrufen der **aktuellen** Wetterdaten ist _**https:// myweatherprovider<span></span>.mybluemix.net/current?zipcode={zipcode}**_. Testen Sie ihn durch Aufrufen von [https://myweatherprovider.mybluemix.net/current?zipcode=90210 ![Symbol für externen Link](../../../icons/launch-glyph.svg "Symbol für externen Link")](https://myweatherprovider.mybluemix.net/current?zipcode=90210){:new_window}.  

  ![](images/explore-weatherapp-2.png)

4. Analog ist der Endpunkt zum Abrufen der Vorhersagedaten von **heute** der Link _**https:// myweatherprovider<span></span>.mybluemix.net/today?zipcode={zipcode}**_. Testen Sie ihn durch Aufrufen von [https://myweatherprovider.mybluemix.net/today?zipcode=90210 ![Symbol für externen Link](../../../icons/launch-glyph.svg "Symbol für externen Link")](https://myweatherprovider.mybluemix.net/today?zipcode=90210){:new_window}.  

  ![](images/explore-weatherapp-3.png)


---

### Neue OpenAPI-Spezifikation zum Erstellen eines REST-API-Proxy hinzufügen  
1. Melden Sie sich an {{site.data.keyword.Bluemix_short}} an: https://new-console.ng.bluemix.net/login.
2. Wählen Sie im {{site.data.keyword.Bluemix_short}}-Navigationsfenster **Services** und anschließend **Dashboard** aus. Starten Sie den {{site.data.keyword.apiconnect_short}}-Service.
3. Stellen Sie in {{site.data.keyword.apiconnect_short}} sicher, dass das Navigationsfenster geöffnet ist. Falls dies nicht der Fall ist, klicken Sie auf **>>**, um es zu öffnen.  
4. Wählen Sie im Navigationsfenster **Entwürfe** aus.
5. Klicken Sie in der Registerkarte **APIs** auf **Hinzufügen**. Wählen Sie im Dropdown-Menü **Neue API** aus.    
  ![](images/create-new-1.png)  
6. Geben Sie im Fenster *Neue API* die Bezeichnung `Weather Provider API` als Titel ein.
_Name und Basispfad werden automatisch generiert_.  
  ![](images/bluemix-add-new-api.png)
7. Klicken Sie auf **API erstellen**, um den Assistenten zu beenden.  
8. Nach der Erstellung der API ist die Registerkarte **Entwurf** ausgewählt. 
9. Blättern Sie zur Anzeige **Host**. Geben Sie `$(catalog.host)` als Wert ein, wenn das Feld nicht automatisch gefüllt wurde.
10. Notieren Sie in der Anzeige **Basispfad** den automatisch generierten Wert `/weather-provider-api`. Die Ziel-URL der API wird anhand dieser Werte erstellt.  

11. Blättern Sie zur Registerkarte **Sicherheit** und löschen Sie die automatisch generierte Angabe 'clientIDHeader (API Key)'.  
_(Die Sicherheit durch API-Schlüssel wird im nächsten Lernprogramm besprochen.)_  

12. Blättern Sie in der Navigation abwärts zur Anzeige **Pfade** und erstellen Sie durch Klicken auf **+** einen neuen Pfad.     
    a. Legen Sie für den neuen Pfad den Namen "**/current**" fest.  
    b. Wählen Sie in derselben Anzeige *Pfade* den Abschnitt **GET /current** aus.    
    c. Fügen Sie im Abschnitt **GET /current** einen neuen **Parameter** hinzu. Wie schon beim Beschreiben der Beispielapp erläutert, ist für den Wetterdienst eine Postleitzahl als Parameter erforderlich.   
      - Name: Postleitzahl  
      - Befindet sich in: Abfrage  
      - Erforderlich: Ja  
      - Typ: Zeichenfolge   
    ![](images/path-current-1.png)   
    d. Speichern Sie die API.  

13. Nachdem im vorherigen Schritt die Abfrageparameter definiert wurden, muss jetzt das Antwortobjekt definiert werden, das zurückgegeben wird, wenn die Wetter-API aufgerufen wird. Blättern Sie hierzu abwärts zur Anzeige **Definitionen**.   
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

14. Im vorherigen Schritt haben Sie das Antwortobjekt definiert. Als Nächstes müssen Sie sicherstellen, dass das Antwortobjekt dem Pfad **get /current** zugeordnet ist. Blättern Sie in der Navigation zurück zur Anzeige **Pfade**.
    a. Öffnen Sie die Operation **GET /current** und blättern Sie zum Abschnitt **Antworten**.
    b. Ändern Sie das Schema der Antwort '200 OK' von 'Objekt' in '**Aktuell**'.
    c. Speichern Sie die API durch Klicken auf das Symbol zum Speichern. Kurzzeitig wird die Bestätigungsnachricht 'API gespeichert' angezeigt. 

15. Der Pfad und die Operation zum Abrufen der aktuellen Wetterdaten wurden somit erstellt. Jetzt müssen Sie noch einen ähnlichen Pfad und die zugehörige Operation zum Abrufen der Wetterdaten von heute erstellen. Erstellen Sie analog zur Erstellung des Pfads **/current** in Schritt 12 den neuen Pfad **/today**.

16. Fügen Sie einen neuen Parameter unter der Operation **GET /today** hinzu.
    - Parametername: Postleitzahl  
    - Befindet sich in: Abfrage  
    - Erforderlich: Ja  
    - Typ: Zeichenfolge  

17. Erstellen Sie eine neue Definition: **Heute**.

18. Fügen Sie für die Definition **Heute** neue Eigenschaften hinzu.
    - Name: Postleitzahl /  Typ: Zeichenfolge
    - Name: Hoch         /  Typ: Ganzzahl
    - Name: Niedrig      /  Typ: Ganzzahl
    - Name: FeuchtNacht  /  Typ: Ganzzahl
    - Name: FeuchtTag    /  Typ: Ganzzahl
    - Name: Ort          /  Typ: Zeichenfolge
    - Name: Status       /  Typ: Zeichenfolge
19. Aktualisieren Sie das Antwortschema im Abschnitt **GET /today** in 'Heute' (Today). 
20. Speichern Sie die API.

21. Wechseln Sie zur Registerkarte **Assemblieren**. Sie haben bisher zwei Operationen erstellt: **GET /current** und **GET /today**. Um sicherzustellen, dass der korrekte Endpunkt aufgerufen wird, müssen Sie eine Logik erstellen, die abhängig von der jeweils aufgerufenen Operation ausgeführt wird. Hierfür wird die Logikanweisung **Operation Switch** verwendet.  
    a. Löschen Sie die Richtlinie **invoke**, die unter Umständen bereits zum _Erstellungsbereich_ hinzugefügt wurde.  
    b. Ziehen Sie **Operation Switch** aus der Palette und legen Sie die Anweisung im Erstellungsbereich ab.  
      - Ordnen Sie dem Fall **case 0** die Operation **get /current** zu.
      - Fügen Sie den neuen Fall **case 1** hinzu.
      - Ordnen Sie die Operation **get /today** dem Fall **case 1** zu.
      ![](images/assemble-1.png)
Von **Operation Switch** wird ein Entscheidungspunkt bereitgestellt. Abhängig vom Verb/Pfad-Paar muss die entsprechende Operation aufgerufen werden.
    c. Ziehen Sie die Richtlinie **invoke** aus aus der Palette und legen Sie sie im Erstellungsbereich ab. _Eine Aufrufaktion (invoke) wird zum Aufrufen eines vorhandenen Service in einer Operation verwendet._. Legen Sie eine Aufrufaktion im Pfad **/get current** und eine im Pfad **/get today** ab.   
    d. Wählen Sie die Richtlinie **invoke** im Pfad **/get current** aus und ändern Sie ihren Titel in '**invoke-current**'.  
    e. Aktualisieren Sie das Feld 'URL' anhand von `https://myweatherprovider.mybluemix.net/current?zipcode=$(request.parameters.zipcode)`.  
    f. Wählen Sie die Richtlinie **invoke** im Pfad **/get today** aus und ändern Sie ihren Titel in '**invoke-today**'.  
    g. Aktualisieren Sie das Feld 'URL' anhand von `https://myweatherprovider.mybluemix.net/today?zipcode=$(request.parameters.zipcode)`.  
       ![](images/assemble-2.png)

22. Speichern Sie die API.

---

### API-Proxy testen
1. Klicken Sie in der Registerkarte **Assemblieren** auf das Symbol für mehr Aktionen und wählen Sie anschließend **Standardprodukt auswählen** aus.  
   ![](images/generate-default-product-1.png) 

2. Bestätigen Sie die Standardoptionen im Dialogfeld **Neues Produkt** und klicken Sie auf **Produkt erstellen**. Das Produkt 'Weather Provider API' wird erstellt und im Sandbox-Katalog veröffentlicht. Eine Nachricht über die erfolgreiche Generierung des Produkts wird angezeigt.  
  ![](images/generate-default-product-2.png)  
  
  ![](images/generate-default-product-3.png) 

  - _In {{site.data.keyword.apiconnect_short}} wird mithilfe von **Produkte** eine Möglichkeit zum Gruppieren von APIs bereitgestellt, die für eine bestimmte Verwendung vorgesehen sind. Die Produkte werden in einem **Katalog** veröffentlicht. [{{site.data.keyword.apiconnect_short}}-Glossar](../apic_glossary.html)_

3. Klicken Sie in der Registerkarte 'Assemblieren' auf das Wiedergabesymbol, um den Zielaufruf des API-Proxys zu testen.

4. Wählen Sie in der Testanzeige die Operation **get /current** aus.
	a. Da die Postleitzahl für diese Operation ein erforderlicher Parameter ist, geben Sie eine gültige US-Postleitzahl ein (z. B. 90210). 
	b. Klicken Sie auf **Aufrufen** und stellen Sie sicher, dass Folgendes angezeigt wird: 
  ```
  200 OK response
  Current weather data for 90210
  ```
  
    ![](images/test-invoke-1.png)  

    ![](images/test-invoke-2.png)  

    ![](images/test-invoke-3.png)

---

### Fazit
In diesem Lernprogramm haben Sie gelernt, wie ein vorhandener REST-Service über einen Durchgriffs-API-Proxy aufgerufen werden kann. Als ersten Schritt haben Sie die Verfügbarkeit des Beispielservice über den Web-Browser getestet. Anschließend haben Sie eine neue OpenAPI-Spezifikation in API Connect erstellt und mit dem Beispielservice verknüpft, der aufgerufen werden soll. Sie haben die API in ein Produkt gepackt, das Produkt im Katalog veröffentlicht und den Proxy getestet.

---

## Nächster Schritt

API mit [Quotenbegrenzung](tut_rate_limit.html), [Client-ID und geheimen Schlüssel](tut_secure_landing.html) oder [OAuth 2.0](tut_secure_oauth_2.html) schützen.

Erstellen > **Verwalten** > Schützen > Teilen > Analysieren
