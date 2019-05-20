---

copyright:
  years: 2019
lastupdated: "2019-3-14"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# API mit doppeltem OAuth-Datenfluss (Two-legged OAuth) schützen
{: #tut_secure_oauth_2}

Dauer: 10 Minuten  
Kenntnisstufe: Anfänger

## Lernziel
{: #object_tut_secure_oauth_2}

Im folgenden Lernprogramm wird beschrieben, wie Sie eine API mit einem doppelten OAuth 2.0-Datenfluss (Two-legged OAuth) schützen. In diesem Anwendungsfluss startet der OAuth-Client eine Anforderung an den Berechtigungsserver und empfängt ein Zugriffstoken. Der OAuth-Client kann dieses Token anschließend für den Zugriff auf geschützte Ressourcen über die API verwenden.

## Voraussetzungen
{: #prereq_tut_secure_oauth_2}

Bevor Sie beginnen, müssen Sie eines der folgenden Lernprogramme durchgeführt haben.  
- [API mit Client-ID und geheimen Clientschlüsseln mithilfe von {{site.data.keyword.Bluemix}}](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_id_secret_bm) schützen
oder
- [API mit Client-ID und geheimen Clientschlüsseln mithilfe des Toolkits schützen](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_id_secret_tk)

Hinweis: In diesem Lernprogramm sind die Schritte und Screenshots zur Ausführung der Task in der {{site.data.keyword.Bluemix}}-Benutzerschnittstelle dargestellt. Dieselbe Prozedur kann auch über die Befehlszeile ausgeführt werden. Eine Beschreibung dieser Prozedur finden Sie im [IBM Knowledge Center ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSMNED_5.0.0/com.ibm.apic.toolkit.doc/tutorial_apionprem_security_OAuth_v506.html){: #new_window}. 

## Vorgehensweise
{: #steps_tut_secure_oauth_2}

1. Erstellen Sie eine OAuth-Provider-API und wählen Sie ein OAuth-Schema aus.  
	a. Öffnen Sie **Entwürfe**, wählen Sie **APIs** aus und klicken Sie auf **Hinzufügen** > **OAuth 2.0 Provider-API**.  
    ![](images/oauth_provider_1.png)
	b. Legen Sie den Titel 'OAuth-Endpunkt-API' fest. Name und Basispfad werden automatisch gefüllt.  
	c. Wählen Sie **API erstellen** aus.  
	d. Navigieren Sie in der neu erstellten OAuth-Endpunkt-API zur Anzeige **OAuth 2** (oder blättern Sie abwärts zu ihr) und wählen Sie 'Vertraulich' als Clienttyp aus.  
	e. Benennen Sie unter 'Bereich' den Bereich _scope1_ in _view_current_ um. Löschen Sie _scope2_ und _scope3_.  
	![](images/oauth_provider_type_scope.png) 
	
	f. Nehmen Sie unter **Erteilt** die Auswahl von **Implizit**, **Kennwort** und **Zugriffscode** zurück. Lassen Sie **Anwendung** ausgewählt.  
	![](images/oauth_provider_grants.png)  
	
	g. Speichern Sie die API.  

2. Aktualisieren Sie die Sicherheitsdefinition von 'Wetter-Provider-API' so, dass OAuth eingeschlossen ist.  
	a. Wechseln Sie zu _Wetter-Provider-API_. (Wechseln Sie zu 'APIs' und wählen Sie anschließend _Wetter-Provider-API_ aus.)  
	![](images/oauth_weatherapi_info.png)
	
	b. Klicken Sie unter 'Sicherheitsdefinitionen' auf das Symbol **+** und fügen Sie eine neue Definition für OAuth hinzu.
	![](images/oauth_add_security.png)
	c. Legen Sie für den Namen "OAuth-Definition" fest.  
	d. Wählen Sie im Feld 'Datenfluss' **Anwendung** aus.  
	e. Geben Sie die Token-URL _**Basis-URL**/oauth-endpoint-api/oauth2/token_ ein.  
	![](images/oauth_secdef_top.png)
	
	f. Fügen Sie den neuen Bereich 'view_current' hinzu.  
	![](images/oauth_secdef_scopes.png)
	g. Wählen Sie unter **Sicherheit** die Auswahlmöglichkeiten **OAuth-Definition** und **view_current** aus und belassen Sie Client-ID und geheimen Clientschlüssel ausgewählt.  
	![](images/oauth_security_oauth.png)
	
	h. Klicken Sie auf 'Speichern'.  
	
	i. Navigieren Sie zurück zu **Entwürfe** und wählen Sie **Produkte** aus.  Öffnen Sie das **Wetter-Provider-API-Produkt**.
	![](images/weatherapi_prod_info.png)
	
	j. Klicken Sie in der Navigationsleiste auf **APIs**. Klicken Sie auf das Symbol **+** zum Hinzufügen einer neuen API. Fügen Sie die OAuth-Endpunkt-API zum Wetterdienstprodukt (Weather Provider product) hinzu.  
	![](images/weatherapi_prod_apis.png)
	k. Speichern Sie das Produkt und stellen Sie es im Sandbox-Katalog bereit.  
	![](images/oauth_security_definition_3a.png)

3. Testen Sie die OAuth-Sicherheitskonfiguration.  
	a. Veröffentlichen Sie das aktualisierte Produkt im Sandbox-Katalog. Klicken Sie auf **Dashboard > Sandbox** und veröffentlichen Sie anschließend das Produkt.  
	  ![](images/test_oauth_1.png)
	b. Akzeptieren Sie die Standardwerte im Dialog mit den Anzeigeoptionen. Klicken Sie auf **Veröffentlichen**.
	  ![](images/pub_visibility.png)
	  
	c. Klicken Sie auf **Erkunden > Sandbox**.  
      ![](images/test_oauth_2.png)
	d. Klicken Sie in **Wetter-Provider-API** in der Liste der Operationen auf **GET /current**. 
	
	e. Klicken Sie auf **Testen**. 
	
	f. Beachten Sie, dass in der Anzeige auf der rechten Seite die Felder für die Client-ID und den geheimen Clientschlüssel bereits gefüllt sind.  
	
	g. Geben Sie im Abschnitt **Parameter** _10504_ in das Feld **Postleitzahl** ein.   
	  ![](images/weather_oauth_explorer_param.png)
	
	h. Klicken Sie im Abschnitt **Berechtigung** auf **Berechtigen**, um ein Zugriffstoken abzurufen.
	  ![](images/weather_oauth_explorer_auth.png)
	
	i. Klicken Sie nach dem Empfang des Zugriffstokens auf **Operation aufrufen**, um den Test durchzuführen.  
      ![](images/test_oauth_4.png)

4. Beachten Sie, dass in der Anforderung das Zugriffstoken, die Client-ID und der geheime Clientschlüssel enthalten sind. Wenn Sie nur das Zugriffstoken übergeben möchten, müssen Sie die Client-ID und den geheimen Clientschlüssel aus den Sicherheitsanforderungen für 'Wetter-Provider-API' entfernen.  
    ![](images/test_oauth_5.png)

5. Speichern Sie 'Wetter-Provider-API'. Stellen Sie die API anschließend bereit und veröffentlichen Sie sie im Sandbox-Katalog. Führen Sie im Explorertool denselben Test aus, den Sie davor bereits ausgeführt haben.  
    ![](images/test_oauth_6.png)
    
## Fazit
{: #conclusion_tut_secure_oauth_2}

In diesem Lernprogramm haben Sie gelernt, wie Sie eine API für OAuth-Provider (OAuth Provider API) erstellen, die Sicherheitsdefinition einer API so aktualisieren, dass OAuth darin enthalten ist und wie Sie die Sicherheitskonfiguration testen.

---

## Nächster Schritt
{: #next_tut_secure_oauth_2}

Teilen der API durch [Einrichten und Konfigurieren von Developer Portal](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_config_dev_portal) starten

Erstellen > Verwalten > **Schützen** > Teilen > Analysieren
