---
copyright:
  years: 2017
lastupdated: "2017-09-30"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# API mit doppeltem OAuth-Datenfluss (Two-legged OAuth) schützen

Dauer: 10 Minuten  
Kenntnisstufe: Anfänger

## Lernziel

Im folgenden Lernprogramm wird beschrieben, wie Sie eine API mit einem doppelten OAuth 2.0-Datenfluss (Two-legged OAuth) schützen. In diesem Anwendungsfluss startet der OAuth-Client eine Anforderung an den Autorisierungsserver und empfängt ein Zugriffstoken. Der OAuth-Client kann dieses Token anschließend für den Zugriff auf geschützte Ressourcen über die API verwenden.

## Voraussetzungen

Bevor Sie beginnen, müssen Sie eines der folgenden Lernprogramme durchgeführt haben.  
- [API mit Client-ID und geheimen Clientschlüssel mithilfe von IBM Bluemix schützen](tut_secure_id_secret_bm.html)
oder
- [API mit Client-ID und geheimen Clientschlüssel mithilfe des Toolkits schützen](tut_secure_id_secret_tk.html)

## Vorgehensweise

1. Erstellen Sie eine OAuth-Provider-API und wählen Sie ein OAuth-Schema aus.  
	a. Öffnen Sie **Entwürfe**, wählen Sie **APIs** aus und klicken Sie auf **Hinzufügen** > **OAuth 2.0 Provider-API**.  
    ![](images/oauth_provider_1.png)
	b. Legen Sie den Titel 'OAuth-Endpunkt-API' fest. (Name und Basispfad werden automatisch gefüllt.)  
	c. Wählen Sie **API erstellen** aus.  
	d. Navigieren Sie in der neu erstellten OAuth-Endpunkt-API zur Anzeige **OAuth 2** (oder blättern Sie abwärts zu ihr) und wählen Sie 'Vertraulich' als Clienttyp aus.  
	e. Benennen Sie unter 'Bereich' den Bereich _scope1_ in _view_current_ um. Löschen Sie _scope2_ und _scope3_.  
	f. Nehmen Sie unter **Erteilt** die Auswahl von **Implizit**, **Kennwort** und **Zugriffscode** zurück. Lassen Sie **Anwendung** ausgewählt.  
	![](images/oauth_provider_2.png)  
	g. Speichern Sie die API.  

2. Aktualisieren Sie die Sicherheitsdefinition von 'Weather Provider API' so, dass OAuth eingeschlossen ist.  
	a. Wechseln Sie zu _Weather Provider API_. (Wechseln Sie zu 'APIs' und wählen Sie anschließend _Weather Provider API_ aus.)  
	b. Fügen Sie unter 'Sicherheitsdefinitionen' eine neue Definition für OAuth hinzu. Legen Sie als Name für sie 'OAuth-Definition' fest.  
	c. Wählen Sie im Feld 'Datenfluss' **Anwendung** aus.  
	d. Geben Sie die Token-URL _<Basis-URL>/oauth-endpoint-api/oauth2/token_ ein.  
	e. Fügen Sie den neuen Bereich 'view_current' hinzu.  
	![](images/oauth_security_definition_1.png)
	f. Wählen Sie unter **Sicherheit** die Auswahlmöglichkeiten **OAuth-Definition** und **view_current** aus und belassen Sie Client-ID und geheimen Clientschlüssel ausgewählt.  
	![](images/oauth_security_definition_2.png)
	g. Klicken Sie auf 'Speichern'.  
	h. Navigieren Sie zurück zu **Entwürfe** und wählen Sie **Produkte** aus. Fügen Sie die OAuth-Endpunkt-API zum Wetterdienstprodukt (Weather Provider product) hinzu.  
	i. Speichern Sie das Produkt und stellen Sie es im Sandbox-Katalog bereit.  
	![](images/oauth_security_definition_3a.png)

3. Testen Sie die OAuth-Sicherheitskonfiguration.  
	a. Veröffentlichen Sie das aktualisierte Produkt im Sandbox-Katalog. Klicken Sie auf **Dashboard > Sandbox** und veröffentlichen Sie anschließend das Produkt.  
	  ![](images/test_oauth_1.png)
	b. Klicken Sie auf **Explore > Sandbox**.  
      ![](images/test_oauth_2.png)
	c. Klicken Sie in **Weather Provider API** in der Liste der Operationen auf **GET /current**.  
	d. Beachten Sie, dass in der Anzeige auf der rechten Seite die Felder für die Client-ID und den geheimen Clientschlüssel bereits gefüllt sind.  
	e. Geben Sie im Abschnitt **Parameter** eine Postleitzahl ein.  
      ![](images/test_oauth_3.png)
	f. Klicken Sie im Abschnitt **Autorisierung** auf **Autorisieren**, um ein Zugriffstoken abzurufen.  
	g. Klicken Sie nach dem Empfang des Zugriffstokens auf **Operation aufrufen**, um den Test durchzuführen.  
      ![](images/test_oauth_4.png)

4. Beachten Sie, dass in der Anforderung das Zugriffstoken, die Client-ID und der geheime Clientschlüssel enthalten sind. Wenn Sie nur das Zugriffstoken übergeben möchten, müssen Sie die Client-ID und den geheimen Clientschlüssel aus den Sicherheitsanforderungen für 'Weather Provider API' entfernen.  
    ![](images/test_oauth_5.png)

5. Speichern Sie 'Weather Provider API'. Stellen Sie die API anschließend bereit und veröffentlichen Sie sie im Sandbox-Katalog. Führen Sie im Tool Explore denselben Test aus, den Sie davor bereits ausgeführt haben.  
    ![](images/test_oauth_6.png)
    
## Fazit
In diesem Lernprogramm haben Sie gelernt, wie Sie eine API für OAuth-Provider (OAuth Provider API) erstellen, die Sicherheitsdefinition einer API so aktualisieren, dass OAuth darin enthalten ist und wie Sie die Sicherheitskonfiguration testen.

---

## Nächster Schritt

Teilen der API durch [Einrichten und Konfigurieren von Developer Portal](tut_config_dev_portal.html) starten

Erstellen > Verwalten > **Schützen** > Teilen > Analysieren
