---

copyright:
  years: 2017
lastupdated: "2017-10-10"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# API-Produkte archivieren und löschen
**Dauer**: 15 Minuten  
**Kenntnisstufe**: Anfänger 

## Voraussetzungen

1. [Richten Sie die {{site.data.keyword.apiconnect_full}}-Instanz ein](tut_prereq_set_up_apic_instance.html).

2. Schließen Sie das [Lernprogramm zum Außerkraftsetzen von API-Produkten](tut_manage_supercede.html) ab.

---
## Lernziel
In diesem Lernprogramm löschen und archivieren Sie eine API und ziehen eine API zurück.

---
## API-Produkt löschen
1. Melden Sie sich an {{site.data.keyword.Bluemix_short}} an: [https://console.ng.bluemix.net/login ![Symbol für externen Link](../../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.ng.bluemix.net/login){:new_window}.

2. Starten Sie im {{site.data.keyword.Bluemix_short}}-Dashboard den {{site.data.keyword.apiconnect_short}}-Service.
![](images/Bluemix.png)

3. Wenn Sie in API Manager bisher nicht den Navigationsbereich der Benutzerschnittstelle fixiert haben, klicken Sie auf das Symbol **Navigieren zu** ![](images/navigate-to.png). Der Navigationsbereich der Benutzerschnittstelle von API Manager wird geöffnet. Klicken Sie zum Fixieren des Navigationsbereichs der Benutzerschnittstelle auf das Symbol für das **Fixiermenü** ![](images/pinned.png).

4. Klicken Sie auf **Sandbox**, um den Sandbox-Katalog zu öffnen. **Hinweis:** Es kann sein, dass Sie zum Dashboard zurückkehren müssen, um die verfügbaren Kataloge anzuzeigen. Es kann auch vorkommen, dass die Kataloge auf der Dashboardseite als Kacheln und nicht in einer Liste angezeigt werden.
![](images/del-sandbox-list.png)

5. Klicken Sie auf den vertikalen Auslassungspunkt in der Zeile **Weather Provider API 1.0.0**.  
![](images/del-prod-list1.png)

6. Wählen Sie **Aus Katalog löschen** aus.  
![](images/del-del-from-cat.png)

7. Klicken Sie auf **OK**.  
![](images/del-del-dialog.png)
    Das Produkt wird in der Liste der Produkte im Katalog nicht mehr angezeigt. Es kann zu diesem Zeitpunkt nicht mehr wiederhergestellt werden.


## API-Produkt archivieren
1. Klicken Sie auf den vertikalen Auslassungspunkt in der Zeile **Weather Provider API 2.0.0**.  
![](images/del-prod-list2.png)

2. Wählen Sie **Zurückziehen** aus.  
![](images/del-select-retire.png)

3. Klicken Sie auf **OK**.  
![](images/del-retire-dialog.png)

4. Klicken Sie auf den vertikalen Auslassungspunkt in der Zeile **Weather Provider API 2.0.0**.  
![](images/del-prod-list3.png)

5. Wählen Sie **Archivieren** aus.  
![](images/del-select-archive.png)

6. Klicken Sie auf **OK**.  
![](images/del-archive-dialog.png)
    Das Produkt wird in der Liste der Produkte im Katalog nicht mehr angezeigt. Es kann wiederhergestellt werden.

7. Klicken Sie auf das Symbol für die Listenansicht.  
![](images/del-prod-list4.png)

8. Wählen Sie **Archiviert** aus.  
![](images/del-view-archived.png)

9. Klicken Sie auf den vertikalen Auslassungspunkt in der Zeile **Weather Provider API 2.0.0**.  
![](images/del-prod-list5.png)

10. Wählen Sie **Archivierung aufheben** aus.  
![](images/del-unarchive.png)
    Der Status des Produkts wechselt zu 'Zurückgezogen'
    ![](images/del-prod-list6.png)

 
 
## Was Sie in diesem Lernprogramm erreicht haben
In diesem Lernprogramm haben Sie Folgendes durchgeführt:

1. Ein API-Produkt gelöscht
2. Ein API-Produkt zurückgezogen
3. Ein API-Produkt archiviert
4. Die Archivierung eines API-Produkts aufgehoben

---












