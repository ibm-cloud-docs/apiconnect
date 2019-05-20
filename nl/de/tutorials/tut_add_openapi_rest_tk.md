---

copyright:
  years: 2017
lastupdated: "2017-11-02"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Neue API-Spezifikation hinzufügen und vorhandenen REST-Service mit Entwicklertoolkit aufrufen
{: #tut_add_openapi_rest_tk}

**Dauer**: 15 Minuten  
**Kenntnisstufe**: Anfänger  

## Lernziel
{: #object_tut_add_openapi_rest_tk}

Dieses Lernprogramm unterstützt Sie beim Einstieg in {{site.data.keyword.apiconnect_full}}, da es verdeutlicht, wie Sie vorgehen müssen, damit Sie eine vorhandene API verwalten können. In einem ersten Schritt wird eine neue OpenAPI-Spezifikation erstellt, anschließend ein Durchgriffs-API-Proxy für einen vorhandenen REST-Service.

## Voraussetzung
{: #prereq_tut_add_openapi_rest_tk}

Bevor Sie beginnen, müssen Sie [eine Instanz von API Connect einrichten](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_set_up_apic_instance) und [das API Connect-Toolkit installieren](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_install_toolkit).

---


## Beispielapp untersuchen und Zielendpunkt testen
{: #expl_test_tut_add_openapi_rest_tk}

Für dieses Lernprogramm wurde die Beispielapp _weather provider_ erstellt.
1. Rufen Sie [http://gettingstartedweatherapp.mybluemix.net/ ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://gettingstartedweatherapp.mybluemix.net/){: #new_window} auf, um die App kennenzulernen.  
2. Geben Sie eine gültige fünfstellige US-Postleitzahl ein, um Angaben zum _**aktuellen Wetter**_ und zur _**Vorhersage für heute**_ zu erhalten.  
![](images/explore-weatherapp-1.png)

3. Die obige Beispielwetterapp wurde mithilfe von APIs erstellt, von denen die Wetterdaten bereitgestellt werden. Der Endpunkt zum Abrufen der **aktuellen** Wetterdaten ist _**https:// myweatherprovider<span></span>.mybluemix.net/current?zipcode={zipcode}**_. Testen Sie ihn durch Aufrufen von [https://myweatherprovider.mybluemix.net/current?zipcode=90210](https://myweatherprovider.mybluemix.net/current?zipcode=90210){: #new_window}.  

  ![](images/explore-weatherapp-2.png)

4. Analog ist der Endpunkt zum Abrufen der Vorhersagedaten von **heute** der Link `https:// myweatherprovider<span></span>.mybluemix.net/today?zipcode={zipcode}`. Testen Sie ihn durch Aufrufen von [https://myweatherprovider.mybluemix.net/today?zipcode=90210](https://myweatherprovider.mybluemix.net/today?zipcode=90210){: #new_window}.  

  ![](images/explore-weatherapp-3.png)

---

## Neue OpenAPI-Spezifikation hinzufügen und vorhandenen REST-Service aufrufen
{: #add_spec_tut_add_openapi_rest_tk}

1. Starten Sie **API Designer**. Geben Sie im Terminal `apic edit` ein.
2. Melden Sie sich mit Ihrer IBMid an.
    ![](images/screenshot_apic-edit_login.png)
3.   Stellen Sie in API Designer sicher, dass das Navigationsfenster geöffnet ist. Falls dies nicht der Fall ist, klicken Sie auf >>, um es zu öffnen. Wählen Sie im **API Designer**-Navigationsfenster **Entwürfe > APIs** aus.
4. Wählen Sie in der Anzeige **APIs** die Optionen **Hinzufügen > Neue API** aus.
5. Geben Sie im Fenster 'Neue API' die Zeichenfolge 'Wetter-Provider-API' als Titel ein. _Name und Basispfad werden automatisch generiert_.  
  ![](images/toolkit-add-new-api.png)   
6. Klicken Sie auf **API erstellen**, um den Assistenten zu beenden.  

7. Nach der Erstellung der API ist die Registerkarte **Entwurf** ausgewählt.

8. Blättern Sie zur Anzeige **Host**. Geben Sie `$(catalog.host)` als Wert ein, wenn das Feld nicht automatisch gefüllt wurde.

9. Blättern Sie zur Registerkarte **Sicherheit** und löschen Sie die automatisch generierte Angabe 'clientIDHeader (API Key)'.  
_(Die Sicherheit durch API-Schlüssel wird im nächsten Lernprogramm besprochen.)_  

10. Erstellen Sie in der Anzeige **Pfade** durch Klicken auf **+** einen neuen Pfad.
  a. Legen Sie für den neuen Pfad den Namen "**/current**" fest.  
  b. Wählen Sie in derselben Anzeige **Pfade** den Abschnitt **GET /current** aus.  
  c. Fügen Sie im Abschnitt **GET /current** einen neuen **Parameter** hinzu. Wie schon beim Beschreiben der Beispielapp erläutert, ist für den Wetterdienst eine Postleitzahl als Parameter erforderlich.
      - Name: Postleitzahl  
      - Befindet sich in: Abfrage  
      - Erforderlich: Ja  
      - Typ: Zeichenfolge  
    ![](images/path-current-1.png)
  d. Speichern Sie die API.

11. Nachdem im vorherigen Schritt die Abfrageparameter definiert wurden, muss jetzt das Antwortobjekt definiert werden, das zurückgegeben wird, wenn die Wetter-API aufgerufen wird. Blättern Sie hierzu abwärts zur Anzeige **Definitionen**.

  1. Fügen Sie eine neue Definition hinzu. 
  2. Legen Sie als Name für die neue Definition _Aktuell_ fest.
  3. Definieren Sie für sie den Typ _Objekt_.
  4. Fügen Sie für die Definition **Aktuell** neue Eigenschaften hinzu.
    - Name: Postleitzahl /  Typ: Zeichenfolge
    - Name: Temperatur   /  Typ: Ganzzahl
    - Name: Feuchtigkeit /  Typ: Ganzzahl
    - Name: Ort          /  Typ: Zeichenfolge
    - Name: Status       /  Typ: Zeichenfolge
    ![](images/definition-current-1.png)
  5. Speichern Sie die API.  

12. Im vorherigen Schritt haben Sie das Antwortobjekt definiert. Als Nächstes müssen Sie sicherstellen, dass das Antwortobjekt dem Pfad **get /current** zugeordnet ist. Blättern Sie in der Navigation zurück zur Anzeige **Pfade**.
  a. Öffnen Sie die Operation **GET /current** und blättern Sie zum Abschnitt **Antworten**.
  b. Ändern Sie das Schema der Antwort '200 OK' von 'Objekt' in '**Aktuell**'.
  c. Speichern Sie die API.

13. Der Pfad und die Operation zum Abrufen der aktuellen Wetterdaten wurden somit erstellt. Jetzt müssen Sie noch einen ähnlichen Pfad und die zugehörige Operation zum Abrufen der Wetterdaten von heute erstellen. Erstellen Sie analog zur Erstellung des Pfads **/current** in Schritt 11 den neuen Pfad **/today**. 

14. Fügen Sie einen neuen Parameter unter der Operation **GET /today** hinzu.
    - Parametername: Postleitzahl  
    - Befindet sich in: Abfrage  
    - Erforderlich: Ja  
    - Typ: Zeichenfolge  

15. Erstellen Sie eine neue Definition: **Heute**.

16. Fügen Sie für die Definition **Heute** neue Eigenschaften hinzu.
  - Name: Postleitzahl /  Typ: Zeichenfolge
  - Name: Hoch         /  Typ: Ganzzahl
  - Name: Niedrig      /  Typ: Ganzzahl
  - Name: FeuchtNacht  /  Typ: Ganzzahl
  - Name: FeuchtTag    /  Typ: Ganzzahl
  - Name: Ort          /  Typ: Zeichenfolge
  - Name: Status       /  Typ: Zeichenfolge

17. Aktualisieren Sie das Antwortschema im Abschnitt **GET /today** in 'Heute' (Today).

18. Speichern Sie die API.

19. Wechseln Sie zur Registerkarte **Assemblieren**. Sie haben bisher zwei Operationen erstellt: **GET /current** und **GET /today**. Um sicherzustellen, dass der korrekte Endpunkt aufgerufen wird, müssen Sie eine Logik erstellen, die abhängig von der jeweils aufgerufenen Operation ausgeführt wird. Hierfür wird die Logikanweisung **Operation Switch** verwendet.  

    a. Löschen Sie die Richtlinie **invoke**, die unter Umständen bereits zum _Erstellungsbereich_ hinzugefügt wurde.  
    b. Ziehen Sie **Operation Switch** aus der _Palette_ und legen Sie die Anweisung im Erstellungsbereich ab.  
      - Ordnen Sie dem Fall **case 0** die Operation **get /current** zu.
      - Fügen Sie den neuen Fall **case 1** hinzu.
      - Ordnen Sie die Operation **get /today** dem Fall **case 1** zu.
    ![](images/assemble-1.png)
    Von **Operation Switch** wird ein Entscheidungspunkt bereitgestellt. Abhängig vom Verb/Pfad-Paar muss die entsprechende Operation aufgerufen werden.  
    c. Ziehen Sie die Richtlinie **invoke** aus aus der Palette und legen Sie sie im Erstellungsbereich ab. Legen Sie eine im Pfad **/get current** und eine im Pfad **/get today** ab.
    d. Wählen Sie die Richtlinie **invoke** im Pfad **/get current** aus und ändern Sie ihren Titel in '**invoke-current**'.  
    e. Aktualisieren Sie das Feld 'URL' anhand von `https://myweatherprovider.mybluemix.net/current?zipcode=$(request.parameters.zipcode)`.
    f. Wählen Sie die Richtlinie **invoke** im Pfad **/get today** aus und ändern Sie ihren Titel in '**invoke-today**'.  
    g. Aktualisieren Sie das Feld 'URL' anhand von `https://myweatherprovider.mybluemix.net/today?zipcode=$(request.parameters.zipcode)`.  

20. Speichern Sie die API.

---

## API-Proxy testen
{: #test_tut_add_openapi_rest_tk}

### Mit _API Manager-Testtool_ testen
{: #test_apimgr_tut_add_openapi_rest_tk}

1. Starten Sie den lokalen Testserver durch Klicken auf das Symbol zum Starten der Server (>) unten links in Designer. Sobald das Gateway gestartet ist, wird der Status automatisch auf 'Aktiv' aktualisiert.

    ![](images/screenshot_start-server-1.png)

2. Klicken Sie in der Registerkarte **Assemblieren** auf das Symbol für die Wiedergabe (>), um den Zielaufruf des API-Proxy zu testen. _Da in diesem Lernprogramm das integrierte Micro Gateway verwendet wird, sollten Sie sicherstellen, dass die Micro Gateway-Richtlinien ausgewählt sind._

    ![](images/screenshot_test-0.png)

3. Wählen Sie in der Testanzeige die Operation **get /current** aus.  
  a. Da die Postleitzahl für diese Operation ein erforderlicher Parameter ist, geben Sie eine gültige US-Postleitzahl ein (z. B. 90210).  
  b. Klicken Sie auf **Aufrufen** und stellen Sie sicher, dass Folgendes angezeigt wird:
  ```
  200 OK response
  Current weather data for 90210  
  ```
    ![](images/screenshot_test-2.png)  

_Falls ein CORS-Fehler auftritt, gehen Sie gemäß den Anweisungen in der Fehlernachricht vor. Klicken Sie auf den Link im Fehler, um die Ausnahmebedingung zum Browser hinzuzufügen und klicken Sie anschließend erneut auf die Schaltfläche zum Aufrufen._

### Mit _Explorertool_ testen
{: #test_explore_tut_add_openapi_rest_tk}

1. Wählen Sie zum Testen der API-Proxy-Endpunkte _Erkunden_ aus.
2. Wählen Sie die Operation **GET /current** in der Palette aus.
3. Geben Sie eine gültige US-Postleitzahl (zum Beispiel 90210) in das Testfeld ein.
4. Klicken Sie auf **Operation aufrufen**, um die Antwort anzuzeigen.  
  ![](images/screenshot_explore.png)  
  
---

## Fazit
{: #conclusion_tut_add_openapi_rest_tk}

In diesem Lernprogramm haben Sie erfahren, wie ein vorhandener REST-Service über einen Durchgriffs-API-Proxy aufgerufen werden kann. Als ersten Schritt haben Sie die Verfügbarkeit des Beispielservice über den Web-Browser getestet. Anschließend haben Sie eine neue OpenAPI-Spezifikation in {{site.data.keyword.apiconnect_short}} erstellt und mit dem Beispielservice verknüpft, der aufgerufen werden soll. Zum Schluss haben Sie den API-Proxy mit dem integrierten Testtool getestet.

---

## Nächster Schritt
{: #next_tut_add_openapi_rest_tk}

API mit [Quotenbegrenzung](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_rate_limit), [Client-ID und geheimen Schlüssel](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_landing) oder [OAuth 2.0](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_oauth_2) schützen.

Erstellen > **Verwalten** > Schützen > Teilen > Analysieren

