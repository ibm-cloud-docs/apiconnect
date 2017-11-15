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

# API-Produkt ersetzen
**Dauer**: 15 Minuten  
**Kenntnisstufe**: Anfänger  


## Voraussetzungen

1. [Richten Sie die {{site.data.keyword.apiconnect_full}}-Instanz ein](tut_prereq_set_up_apic_instance.html).

2. Führen Sie eines der folgenden Lernprogramme aus:
 
    - [OpenAPI 2.0-Spezifikation importieren und Proxy für vorhandenen REST-Service erstellen](tut_rest_landing.html)
       **oder**  
    - [Neue OpenAPI-Spezifikation hinzufügen und vorhandenen REST-Service aufrufen](tut_rest_landing.html).

---
## Lernziel
In diesem Lernprogramm aktualisieren Sie ein vorhandenes API-Produkt, indem Sie es durch ein neueres ersetzen. Wenn ein API-Produkt ersetzt wird, werden die Änderungen sofort wirksam und alle Anwendungsabonnements werden automatisch aktualisiert.  


---
## API-Produkt ersetzen
{: #repl_api_prod}

1. Melden Sie sich an {{site.data.keyword.Bluemix_short}} an: [https://console.ng.bluemix.net/login ![Symbol für externen Link](../../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.ng.bluemix.net/login){:new_window}.

2. Starten Sie im {{site.data.keyword.Bluemix_short}}-Dashboard den {{site.data.keyword.apiconnect_short}}-Service.
![](images/Bluemix.png)

3. Wenn Sie in API Manager bisher nicht den Navigationsbereich der Benutzerschnittstelle fixiert haben, klicken Sie auf das Symbol **Navigieren zu** ![](images/navigate-to.png). Der Navigationsbereich der Benutzerschnittstelle von API Manager wird geöffnet. Klicken Sie zum Fixieren des Navigationsbereichs der Benutzerschnittstelle auf das Symbol für das **Fixiermenü** ![](images/pinned.png).

4. Klicken Sie auf **Entwürfe** > **APIs**.

5. Klicken Sie in der Anzeige 'APIs' auf **Weather Provider API**, um die API für den REST-Proxy zu öffnen.  
![](images/rep-api-list.png)

6. Ändern Sie die **Version** in 2.0.0.  

7. Klicken Sie auf das Plattensymbol, um die Änderungen an der API zu speichern.  
![](images/rep-change-version.png)

8. Klicken Sie auf **Alle APIs**.  
![](images/rep-all-apis.png)

9. Klicken Sie auf **Produkte**.  
![](images/rep-api-list-2.png)

10.	Wählen Sie das Produkt **Weather Provider API** aus.  
![](images/rep-draft-prod-list.png)

11.	Ändern Sie die **Version** in 2.0.0. Geben Sie `Updated API` in das Feld **Beschreibung** ein. Klicken Sie auf das Plattensymbol, um die Änderungen zu speichern.  
![](images/rep-update-prod.png)

12.	Klicken Sie auf das Symbol **Staging**, um die neue Version hochzuladen. Wählen Sie den Katalog **Sandbox** aus, sofern noch nicht geschehen.![](images/rep-stage-prod-2.png)
    **Hinweis:** Es ist möglich, eine neue Version in einem anderen Katalog bereitzustellen, und so zu steuern, welche Zielgruppe an Entwicklern diese Version anzeigen können. Diese Funktion kann sinnvoll sein, wenn API-Produkte aus der Entwicklung zum Testen in die Produktion verschoben werden.

13.	Klicken Sie auf **>>**, um das Navigationsmenü zu öffnen, und wählen Sie **Dashboard** aus.  
![](images/rep-dashboard.png)

14.	Klicken Sie auf **Sandbox**.  

15.	Klicken Sie auf den vertikalen Auslassungspunkt in der Zeile **Weather Provider API Product 2.0.0 Staged**.  
![](images/rep-dash-prod-list-2.png)

16.	Wählen Sie **Vorhandenes Produkt ersetzen** aus.  
![](images/rep-replace-prod.png)

17.	Wählen Sie **Weather Provider API Product 1.0.0** in der Liste der dargestellten Produkte aus. Klicken Sie auf **Weiter**.  
![](images/rep-replace-dialog.png)

18.	Wählen Sie **Standardplan** aus. Klicken Sie auf **Ersetzen**.  
![](images/rep-replace-dialog-2.png)

    Als Ergebnis dieses Ersetzungsvorgangs wird 'Weather Provider API Product 1.0.0' zurückgezogen und 'Weather Provider API Product 2.0.0' veröffentlicht. **Hinweis:** Während des Ersetzungsvorgangs ist es möglich, den Plan zu ändern, der diesem Produkt zugeordnet ist. Dies ist eine einfach Möglichkeit zum Ändern des Plans für ein API-Produkt.
 ![](images/rep-prod-retired.png)


## Was Sie in diesem Lernprogramm erreicht haben

In diesem Lernprogramm haben Sie Folgendes durchgeführt:
1. Ein API-Produkt aktualisiert.
2. Ein vorhandenes API-Produkt durch ein aktualisiertes API-Produkt ersetzt.

---












