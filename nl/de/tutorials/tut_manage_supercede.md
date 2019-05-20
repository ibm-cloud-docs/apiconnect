---

copyright:
  years: 2019
lastupdated: "2017-3-18"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial


---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# API-Produkte außer Kraft setzen
{: #tut_manage_supercede}

**Dauer**: 15 Minuten  
**Kenntnisstufe**: Anfänger  

## Lernziel
{: #object_tut_manage_supercede}

In diesem Lernprogramm setzen Sie eine vorhandene API zugunsten einer neuen außer Kraft.

---
## Voraussetzungen
{: #prereq_tut_manage_supercede}

1. [Richten Sie die {{site.data.keyword.apiconnect_full}}-Instanz ein](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_set_up_apic_instance).

2. Schließen Sie das [Lernprogramm zum Ersetzen von API-Produkten](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_manage_replace) ab.

---

## API-Produkt außer Kraft setzen
{: #super_tut_manage_supercede}

1. Melden Sie sich bei {{site.data.keyword.Bluemix_short}} an: https://cloud.ibm.com.
2. Klicken Sie im {{site.data.keyword.Bluemix_notm}}-**Dashboard** auf **Cloud Foundry-Services**.Starten Sie den {{site.data.keyword.apiconnect_short}}-Service. 
3. Stellen Sie in {{site.data.keyword.apiconnect_short}} sicher, dass das Navigationsfenster geöffnet ist. Falls dies nicht der Fall ist, klicken Sie auf **>>**, um es zu öffnen.  

  ![](images/cloud-apic-dashboard.png)

4. Klicken Sie auf **Entwürfe** > **APIs**.

5. Klicken Sie in der Anzeige 'APIs' auf **Wetter-Provider-API**, um die API für den REST-Proxy zu öffnen.  
![](images/rep-api-list.png)

6. Ändern Sie die **Version** in 3.0.0.

7. Klicken Sie auf das Plattensymbol, um die Änderungen an der API zu speichern.  
![](images/sup-change-version.png)

8. Klicken Sie auf **Alle APIs**.  
![](images/rep-all-apis.png)

9. Klicken Sie auf **Produkte**.  
![](images/sup-prods.png)

10.	Wählen Sie das Produkt **Wetter-Provider-API 2.0.0** aus.  
![](images/sup-draft-prod-list.png)

11.	Ändern Sie die **Version** in 3.0.0. Klicken Sie auf das Plattensymbol, um die Änderungen zu speichern. Klicken Sie auf das Symbol **Staging**.  
![](images/sup-change-prod-vers-3.png)

12.	Klicken Sie auf **>>**, um das Navigationsfenster zu öffnen, und wählen Sie anschließend **Dashboard** aus.  
![](images/rep-dashboard.png)

13.	Klicken Sie auf **Sandbox**.

14.	Klicken Sie auf **Community**.  
![](images/sup-sand-dash.png)

15.	Klicken Sie auf **Abonnements**.  
![](images/sup-comm-orgs.png)

16.	Notieren Sie die Anwendungsabonnements für Wetter-Provider-API Product 2.0.0. Klicken Sie auf **Produkte**.
![](images/sup-scriptions-200.png)  

17.	Klicken Sie auf den vertikalen Auslassungspunkt in der Zeile **Wetter-Provider-API Product 3.0.0 Staged**.  
![](images/sup-stage-prod-3.png)

18.	Wählen Sie **Vorhandenes Produkt außer Kraft setzen** aus.  
![](images/sup-super-prod.png)

19.	Wählen Sie **Wetter-Provider-API Product 2.0.0** in der Liste der dargestellten Produkte aus. Klicken Sie auf **Weiter**.  
![](images/sup-super-dialog-1.png)

20.	Wählen Sie **Standardplan** aus. Klicken Sie auf **Außer Kraft setzen**.  
![](images/sup-super-dialog-2.png)
    Als Ergebnis dieses Ersetzungsvorgangs wird 'Wetter-Provider-API Product 2.0.0' nicht weiter unterstützt und 'Wetter-Provider-API Product 3.0.0' wird veröffentlicht.  
![](images/sup-dash-prods-3.png) 
 
21.	Klicken Sie auf **Community >> Abonnements**.  
![](images/sup-scriptions-200.png)
 
22.	Klicken Sie auf den vertikalen Auslassungspunkt in der Zeile **Wetter-Provider-API Product 2.0.0**. Wählen Sie **Verwalten** aus.  
![](images/sup-dots-manage.png) 

23.	Wählen Sie **Standardplan** unter 'Wetter-Provider-API Product 3.0.0' aus. Klicken Sie auf **Migrieren**.  
![](images/sup-migrate-dialog.png)
    Als Ergebnis dieser Migration wird 'Wetter-Provider-API Product 2.0.0' auf 'Wetter-Provider-API Product 3.0.0' migriert.  
![](images/sup-migrated.png) 
 

 
## Fazit
{: #conclusion_tut_manage_supercede}

In diesem Lernprogramm haben Sie Folgendes durchgeführt:

1. Ein API-Produkt aktualisiert
2. Ein vorhandenes API-Produkt zugunsten eines aktualisierten API-Produkts außer Kraft gesetzt
3. Das Abonnement für das vorhandene API-Produkt auf das aktualisierte API-Produkt migriert

---












