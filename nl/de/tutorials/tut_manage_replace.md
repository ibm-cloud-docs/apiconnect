---

copyright:
  years: 2019
lastupdated: "2017-3-15"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# API-Produkt ersetzen
{: #tut_manage_replace}

**Dauer**: 15 Minuten  
**Kenntnisstufe**: Anfänger  

## Lernziel
{: #object_tut_manage_replace}
In diesem Lernprogramm aktualisieren Sie ein vorhandenes API-Produkt, indem Sie es durch ein neueres ersetzen. Wenn ein API-Produkt ersetzt wird, werden die Änderungen sofort wirksam und alle Anwendungsabonnements werden automatisch aktualisiert.  

---
## Voraussetzungen
{: #prereq_tut_manage_replace}

1. [Richten Sie die {{site.data.keyword.apiconnect_full}}-Instanz ein](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_set_up_apic_instance).

2. Führen Sie eines der folgenden Lernprogramme aus:
 
    - [OpenAPI 2.0-Spezifikation importieren und Proxy für vorhandenen REST-Service erstellen](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_rest_landing)
       **oder**  
    - [Neue OpenAPI-Spezifikation hinzufügen und vorhandenen REST-Service aufrufen](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_rest_landing).

---

## API-Produkt ersetzen
{: #repl_api_prod_tut_manage_replace}}

1. Melden Sie sich bei {{site.data.keyword.Bluemix_short}} an: https://cloud.ibm.com.
2. Klicken Sie im {{site.data.keyword.Bluemix_notm}}-**Dashboard** auf **Cloud Foundry-Services**.Starten Sie den {{site.data.keyword.apiconnect_short}}-Service. 
3. Stellen Sie in {{site.data.keyword.apiconnect_short}} sicher, dass das Navigationsfenster geöffnet ist. Falls dies nicht der Fall ist, klicken Sie auf **>>**, um es zu öffnen.  

  ![](images/cloud-apic-dashboard.png)

4. Klicken Sie auf **Entwürfe** > **APIs**.

5. Klicken Sie in der Anzeige 'APIs' auf **Wetter-Provider-API**, um die API für den REST-Proxy zu öffnen.  
![](images/rep-api-list.png)

6. Ändern Sie die **Version** in 2.0.0.  

7. Klicken Sie auf das Plattensymbol, um die Änderungen an der API zu speichern.  
![](images/rep-change-version.png)

8. Klicken Sie auf **Alle APIs**.  
![](images/rep-all-apis.png)

9. Klicken Sie auf **Produkte**.  
![](images/rep-api-list-2.png)

10.	Wählen Sie das Produkt **Wetter-Provider-API** aus.  
![](images/rep-draft-prod-list.png)

11.	Ändern Sie die **Version** in 2.0.0. Geben Sie `Updated API` in das Feld **Beschreibung** ein. Klicken Sie auf das Plattensymbol, um die Änderungen zu speichern.  
![](images/rep-update-prod.png)

12.	Klicken Sie auf das Symbol **Staging**, um die neue Version hochzuladen. Wählen Sie den Katalog **Sandbox** aus, sofern noch nicht geschehen.
![](images/rep-stage-prod-2.png)
    **Hinweis:** Es ist möglich, eine neue Version in einem anderen Katalog bereitzustellen, und so zu steuern, welche Zielgruppe an Entwicklern diese Version anzeigen können. Diese Funktion kann sinnvoll sein, wenn API-Produkte aus der Entwicklung zum Testen in die Produktion verschoben werden.

13.	Klicken Sie auf **>>**, um das Navigationsmenü zu öffnen, und wählen Sie **Dashboard** aus.  
![](images/rep-dashboard.png)

14.	Klicken Sie auf **Sandbox**.  

15.	Klicken Sie auf den vertikalen Auslassungspunkt in der Zeile **Wetter-Provider-API Product 2.0.0 Staged**.  
![](images/rep-dash-prod-list-2.png)

16.	Wählen Sie **Vorhandenes Produkt ersetzen** aus.  
![](images/rep-replace-prod.png)

17.	Wählen Sie **Wetter-Provider-API Product 1.0.0** in der Liste der dargestellten Produkte aus. Klicken Sie auf **Weiter**.  
![](images/rep-replace-dialog.png)

18.	Wählen Sie **Standardplan** aus. Klicken Sie auf **Ersetzen**.  
![](images/rep-replace-dialog-2.png)

    Als Ergebnis dieses Ersetzungsvorgangs wird 'Wetter-Provider-API Product 1.0.0' zurückgezogen und 'Wetter-Provider-API Product 2.0.0' veröffentlicht. **Hinweis:** Während des Ersetzungsvorgangs ist es möglich, den Plan zu ändern, der diesem Produkt zugeordnet ist. Dies ist eine einfach Möglichkeit zum Ändern des Plans für ein API-Produkt.
 ![](images/rep-prod-retired.png) 
 

## Fazit
{: #conclusion_tut_manage_replace}

In diesem Lernprogramm haben Sie Folgendes durchgeführt:
1. Ein API-Produkt aktualisiert.
2. Ein vorhandenes API-Produkt durch ein aktualisiertes API-Produkt ersetzt.

---












