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


# SOAP-Service verwalten
**Dauer:** 15 Minuten
**Kenntnisstufe:** Anfänger

---
## Lernziel
In diesem Lernprogramm verwenden Sie API Manager, um eine SOAP-API zu erstellen, die als Proxy für einen SOAP-basierten Wetterdienst fungiert.

## Voraussetzungen
- Bevor Sie beginnen, müssen Sie [eine Instanz von {{site.data.keyword.apiconnect_short}} einrichten](tut_prereq_set_up_apic_instance.html).
- Bevor Sie beginnen, müssen Sie die Testdatei [weatherprovider.wsdl ![Symbol für externen Link](../../../icons/launch-glyph.svg "Symbol für externen Link")](https://raw.githubusercontent.com/IBM-Bluemix-Docs/apiconnect/master/tutorials/weatherprovider.wsdl){:new_window} in Ihr lokales Dateisystem kopieren.
Hinweis: Sie können auf **Unbearbeitet** klicken und anschließend die resultierende Seite im lokalen System als `.wsdl`-Datei speichern. Wie der Name nahelegt, werden von diesem SOAP-Service Wetterdaten zurückgegeben, wenn eine Postleitzahl eingegeben wird.

---
## SOAP-API-Definition festlegen
1. Melden Sie sich an {{site.data.keyword.Bluemix_short}} an: [https://new-console.ng.bluemix.net/login](https://new-console.ng.bluemix.net/login){:new_window}.

2. Blättern Sie im {{site.data.keyword.Bluemix_notm}}-**Dashboard** abwärts bis zu **Alle Services**.

3. Wählen Sie **API Connect** aus, um den {{site.data.keyword.apiconnect_short}}-Service zu starten. 
  
4. Navigieren Sie zur Seite 'Entwürfe', falls diese noch nicht angezeigt wird:  
    a. Klicken Sie in der {{site.data.keyword.apiconnect_short}}-Schnittstelle auf >>, um das Navigationsfenster zu öffnen.
    b. Klicken Sie im Navigationsfenster auf **Entwürfe**.
    c. Wechseln Sie zur Registerkarte **APIs**.

5. Klicken Sie in der Registerkarte 'APIs' auf `Hinzufügen +`.

6. Wählen Sie im Dropdown-Menü **API von SOAP-Service** aus.
  ![Neue API](images/newapi-menu2.png)

7. Das Dialogfenster 'Neue API aus WSDL' wird geöffnet. Klicken Sie auf **Datei hochladen**.
  ![Hochladen der .wsdl-Datei](images/4-uploadwsdl.png)

8. Wählen Sie die Datei `weatherprovider.wsdl` aus, die Sie vorher gespeichert haben.

9. Das Dialogfenster 'Neue API aus WSDL' wird erneut angezeigt. Wählen Sie das Kontrollkästchen **weatherService** aus. Klicken Sie auf **Fertig**.
  ![Auswahl des Wetterdienstes](images/newapi2.png)

10. Bei einem erfolgreichen Import wird die Ansicht 'Design' der API angezeigt. Sie können auch die OpenAPI-Definition in der Registerkarte 'Quelle' anzeigen.
   _In der Registerkarte 'Quelle' wird angezeigt, dass die WSDL-Datei in der OpenAPI-Definition eingeschlossen ist._
  ![API-Editorseite](images/designpage2.png)

11. Blättern Sie abwärts bis zur Registerkarte **Sicherheit** und klicken Sie auf das Löschsymbol, um `clientIDHeader (API Key)` zu entfernen (wurde beim Erstellen des Service automatisch generiert).
   _Im nächsten Lernprogramm erfahren Sie mehr über Sicherheit durch API-Schlüssel._

12. Klicken Sie auf das Symbol ![Speichern](images/save.png), um Ihre Änderungen zu speichern. Kurzzeitig wird die Bestätigungsnachricht 'API gespeichert' angezeigt.

13. In der Menüleiste mit dem Speichersymbol gibt die Registerkarte **Design** die derzeitige Position an. Daneben befindet sich die Registerkarte **Quelle**, in der Sie direkt die Swagger-Datei (Version 2.0) anzeigen können, in der die API dargestellt wird; in der Nähe befindet sich auch die Registerkarte **Assemblieren**, mit der Sie die Drag-and-Drop-Schnittstelle für die API-Verarbeitung öffnen können. Klicken Sie auf **Assemblieren**.
  ![Registerkarte 'Assemblieren'](images/assemble-clean.png)  

## SOAP-API-Definition testen

1. Klicken Sie in der Registerkarte **Assemblieren** auf das Symbol **Weitere Aktionen** (drei Punkte) und wählen Sie **Standardprodukt generieren** im Menü aus.  
   ![Menü für weitere Aktionen, öffnen](images/gen-default-prod.png)

2. Bestätigen Sie die Standardoptionen im Dialogfenster **Neues Produkt** und wählen Sie **Produkt erstellen** aus. **weatherService product 1.0.0** wird erstellt und im Sandbox-Katalog veröffentlicht.  
  ![Erstellen eines neuen Produkts](images/12a-chooseproduct.png)
 
  _In {{site.data.keyword.apiconnect_short}} wird mithilfe von **Produkte** eine Möglichkeit zum Gruppieren von APIs bereitgestellt, die für eine bestimmte Verwendung vorgesehen sind. Die Produkte werden in einem **Katalog** veröffentlicht. Referenz: [{{site.data.keyword.apiconnect_short}}-Glossar](../apic_glossary.html)_

3. Speichern Sie Ihre Änderungen.  

4. Klicken Sie neben dem Suchfeld auf das Testsymbol, um den API-Service zu testen. Das Konfigurationsmenü wird angezeigt.

5. Wählen Sie in der Liste der Produkte `weatherService product 1.0.0` aus.  
  ![Auswahl des Wetterdienstes](images/12-chooseproduct.png)

6. Blättern Sie nach unten und klicken Sie auf **Weiter**.

7. Wählen Sie in der Liste der Operationen `post /weatherRequest` aus.  
  ![Posten einer Anforderung](images/13-selectoperation.png)

8. Blättern Sie abwärts. Geben Sie den folgenden XML-Code in das Textfeld ein. Sie können die folgende Beispiel-XML auswählen, kopieren und anschließend auf das Feld **Hauptteil** klicken, um das Feld zu aktivieren und die Beispiel-XML einzufügen.  
  ```
  <?xml version="1.0" encoding="UTF-8"?>
  <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
  <wdata:WeatherRequest xmlns:wdata="http://www.ibm.com/wdata">
       <zipcode>10504</zipcode>
  </wdata:WeatherRequest>
   </soap:Body>
  </soap:Envelope>
  ```
  {: codeblock}  
  ![Die Anforderung](images/14-enterrequest.png)

9. Blättern Sie bei Bedarf nach unten und klicken Sie auf **Aufrufen**.
Von der API wird der **Hauptteil** der Antwort mit dem aktuellen Wetter zurückgegeben.  
  ![](images/15-success.png)

## Was Sie in diesem Lernprogramm erreicht haben
In diesem Lernprogramm haben Sie Folgendes durchgeführt:
1. SOAP-API-Definition festgelegt
2. API-Definition getestet
3. **Hauptteil** der Antwort mit dem Ergebnis der Anfrage vom Endpunkt der Wetter-API empfangen

---

## Nächster Schritt

[Service als REST-API verfügbar machen](tut_expose_soap_service.html) oder API mit [Quotenbegrenzung](tut_rate_limit.html), [Client-ID und geheimen Schlüssel](tut_secure_landing.html) oder [Schutz durch OAuth 2.0](tut_secure_oauth_2.html) schützen.

Erstellen > **Verwalten** > Schützen > Teilen > Analysieren
