---
copyright:
  years: 2017
lastupdated: "2017-10-31"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# API mit-Client-ID und geheimem Clientschlüssel mithilfe von Developer Toolkit schützen


**Dauer:** 10 Minuten  
**Kenntnisstufe:** Anfänger


## Lernziel

Im folgenden Lernprogramm wird beschrieben, wie Sie eine API mit einer Client-ID und einem geheimen Clientschlüssel schützen. Wenn Anwendungen in Developer Portal registriert werden, wird eine Client-ID zum Identifizieren der Anwendung generiert. Optional kann auch ein geheimer Clientschlüssel generiert werden, der dann als Kennwort dient. Von den Anwendungen müssen die generierten Client-IDs und geheimen Clientschlüssel für den Zugriff auf die API angegeben werden.


## Voraussetzungen
Bevor Sie beginnen, müssen Sie eines der folgenden Lernprogramme durchgeführt haben:
- [OpenAPI 2.0-Spezifikation importieren und Proxy für vorhandenen REST-Service erstellen](tut_rest_landing.html)
**oder**  
- [Neue OpenAPI-Spezifikation hinzufügen und vorhandenen REST-Service aufrufen](tut_rest_landing.html)


## Identifikationsmechanismus für API einrichten

1. Starten Sie API Designer (falls noch nicht gestartet):  
   a. Öffnen Sie das Terminal.  
   b. Geben Sie in der Befehlszeile `apic edit` ein. _API Designer wird im Web-Browser gestartet._    
   c. Klicken Sie auf **Mit {{site.data.keyword.Bluemix_notm}}** anmelden.  
   d. Geben Sie Ihre {{site.data.keyword.Bluemix_short}}-Anmeldeinformationen ein.  

2. Navigieren Sie zur Ansicht 'Design' der API:
    a. Klicken Sie im linken Navigationsfenster auf **Entwürfe**. 
    b. Klicken Sie anschließend auf die Registerkarte **APIs**.
    c. Klicken Sie auf die API _Weather Provider API_, die Sie im vorherigen Lernprogramm erstellt haben. Daraufhin wird die Ansicht **Design** der API geöffnet.  
    ![](images/1_goto_drafts_api.png)  

3. Gehen Sie in der Ansicht 'Design' wie folgt vor:  
   a. Blättern Sie abwärts bis zu **Sicherheitsdefinitionen**.  
    ![](images/1b.png) 

   b. Klicken Sie auf das Symbol **Sicherheitsdefinitionen hinzufügen** (+) und klicken Sie anschließend auf **API-Schlüssel**.  
      - Name: Client-ID; Parametername: X-IBM-Client-ID  
      - Name: Geheimer Clientschlüssel; Parametername: X-IBM-Client-Secret  
      - Stellen Sie für beide neuen Schlüssel sicher, dass im Feld **Befindet sich in** der Wert 'Header' eingestellt ist.  
      ![](images/2a.png)    

4. Blättern Sie abwärts bis zur Anzeige **Sicherheit** und fügen Sie eine neue Sicherheitsoption hinzu.  
   a. Wählen Sie die neu erstellte Client-ID und den neuen geheimen Clientschlüssel aus.  
   b. Speichern Sie die API.  
   c. Wechseln Sie zur Registerkarte **Assemblieren**.  
    ![](images/3a.png) 

## An API vorgenommene Änderungen testen

1. Klicken Sie in der Registerkarte 'Assemblieren' auf die Schaltfläche ►, um die Änderungen zu testen.
2. Klicken Sie in der Testanzeige auf die Operation **get /current**.
3. Blättern Sie in der Testanzeige abwärts und beachten Sie, dass die Werte für die Client-ID und den geheimen Clientschlüssel gefüllt wurden. _Hierbei handelt es sich um Testwerte, die für Sandbox generiert wurden; sie stellen die Schlüssel der Anwendung dar, die Ihre API verwendet._  
> Hinweis: Die Werte für die Client-ID und den geheimen Clientschlüssel finden Sie auch unter **Dashboard** > **Katalog** > **Einstellungen** > **Endpunkte**.  

 ![](images/test_api_keys_1.png)

4. Blättern Sie weiter abwärts und geben Sie die Postleitzahl ein (zum Beispiel 90210). 
5. Klicken Sie anschließend auf **Aufrufen**. _Daraufhin müssen die Antwort '200 OK' und der Nachrichtentext mit den Wetterdaten zurückgegeben werden._  
6. Blättern Sie wieder aufwärts zum Feld 'Client-ID' und ersetzen Sie den Wert für die Client-ID durch einen beliebigen Wert (um das Verhalten beim Übergeben einer unzulässigen Client-ID zu überprüfen).  
7. Führen Sie den Test erneut durch Klicken auf **Aufrufen** aus. _Die Antwort '401 Unauthorized' wird zusammen mit der Nachricht 'Client ID not registered' angezeigt._  
  ![](images/test_api_keys_3.png)  
  

## API mit Client-ID und geheimem Clientschlüssel aufrufen

Die Sicherheitseinstellungen können auch mit dem Tool Explore getestet werden, von dem explizit der Proxy-Endpunkt aufgerufen wird und die Client-ID mit den geheimen Clientschlüsseln als Headerwerte übergeben wird.


1. Klicken Sie auf **Erkunden**.
    ![](images/explore_1.png)

2. Klicken Sie in der Liste auf die Operation **GET /current**.  

3. Klicken Sie in der Spalte auf der rechten Seite auf **Operation aufrufen**, um den Test erneut auszuführen.  
    ![](images/4.png)  
    
---

### Fazit
In diesem Lernprogramm haben Sie gelernt, wie der Identifikationsmechanismus für eine API eingerichtet wird, wie die an einer API vorgenommenen Änderungen getestet werden und wie die API mit der Client-ID und dem geheimen Clientschlüssel aufgerufen wird. 

---

## Nächster Schritt

Teilen der API durch [Einrichten und Konfigurieren von Developer Portal](tut_config_dev_portal.html) starten

Erstellen > Verwalten > **Schützen** > Teilen > Analysieren
