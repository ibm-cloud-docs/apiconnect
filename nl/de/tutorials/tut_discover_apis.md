---

copyright:
  years: 2017
lastupdated: "2017-10-10"



{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# APIs kennenlernen
**Dauer**: 25 Minuten  
**Kenntnisstufe**: Anfänger  


## Voraussetzung
Für dieses Lernprogramm gibt es keine Voraussetzungen. Als Portaladministrator können Sie dieses Lernprogramm auch durcharbeiten, während Sie in Developer Portal navigieren, um zu untersuchen, wie die Portalbenutzer in Developer Portal navigieren. Beachten Sie, dass alle Instanzen von Developer Portal unterschiedliche Oberflächen aufweisen.

Wenn Sie nicht über eine vorhandene Developer Portal-Instanz verfügen, können Sie eine solche in {{site.data.keyword.Bluemix_short}} einrichten und konfigurieren, bevor Sie mit diesem Lernprogramm fortfahren.

## Lernziel
In diesem Lernprogramm erfahren Sie, wie ein Portalbenutzer die APIs in {{site.data.keyword.apiconnect_short}} Developer Portal nutzen kann. Sie machen sich damit vertraut, wie ein Portalbenutzer Produkte und APIs durchsucht, APIs anzeigt und testet, und wie er die APIs abonniert.

## Produkte und APIs nutzen
In diesem Abschnitt wird erläutert, wie ein Portalbenutzer die Produkte und APIs in Developer Portal nutzen würde.

1. Navigieren Sie in einem Browser zu **API Connect Developer Portal**.
![API Connect Developer Portal](images/11-developer-portal.png)

2. Wählen Sie in {{site.data.keyword.apiconnect_short}} Developer Portal die Registerkarte 'API-Produkte' aus.
![API-Produkte](images/12-API-products.png)

3. Wählen Sie eines der verfügbaren Produkte aus, damit die verfügbaren APIs und Pläne für das Produkt angezeigt werden.  
  ![Produkt auswählen](images/13-product.png)

4. Wählen Sie eine API zum Kennenlernen der Details der verfügbaren APIs aus.  
  ![APIs der Produkte](images/14-api.png)

5. Auf der Detailseite einer API können Sie die verfügbaren Operationen mit ihren Parametern und zurückgegebenen Antworten anzeigen. Am Ende der Seite können Sie die Definitionen anzeigen, die von der API verwendet werden.  
  ![API-Details](images/15-details.png)

6. In der Anzeige für die Codebeispiele können Sie die Beispiele in den unterschiedlichen Codesprachen anzeigen, um zu erfahren, wie die Anforderungen und ihre Antworten aufgerufen werden. Wählen Sie eines der Beispiele aus, zum Beispiel **Knoten**, um ein Beispiel in dieser Codesprache anzuzeigen.  
  ![API-Details](images/16-examples.png)

---

## APIs anzeigen und testen
In diesem Abschnitt wird erläutert, wie ein Portalbenutzer die für ein Produkt verfügbaren APIs anzeigt und testet. 

1. Navigieren Sie wie im vorherigen Abschnitt beschrieben zu den API-Details in {{site.data.keyword.apiconnect_short}} Developer Portal.  
  ![API-Details](images/21-details.png) 

2. Sie können die YAML-Informationen zu Swagger-APIs durch Auswählen von **Open-API** herunterladen und anzeigen.  
  ![Swagger-YAML-Informationen herunterladen](images/22-swagger.png) 

3. Blättern Sie abwärts bis zu einer Operation, um ihre Details anzuzeigen. Sie können auch auf den Link für die Operationen klicken, um zu diesen auf der Seite zu springen.
![Operation](images/23-operation.png)

4. Blättern Sie im rechten Teilfenster unterhalb der Beispiele zum Abschnitt **Diese Operation testen**. Geben Sie die Parameter ein und wählen Sie **Operation aufrufen** aus.  
  ![Diese Operation testen](images/24-try-this-operation.png)

5. Blättern Sie abwärts, um Anforderung und Antwort des Operationsaufrufs anzuzeigen. Anhand der Rückgabe der Antwort **200 OK** und der Anzeige des Nachrichtentexts wird angegeben, dass der Aufruf der Operation erfolgreich war.  
  ![Antwort auf Operation](images/25-operation-response.png)

---

## APIs subskribieren
In diesem Abschnitt wird beschrieben, wie ein Portalbenutzer APIs in Developer Portal subskribiert. 

1. Wählen Sie **Konto erstellen** aus.
![API-Produkte](images/31-create-account.png)

2. Füllen Sie die erforderlichen Felder aus und wählen Sie **Neues Konto erstellen** ganz unten auf der Seite aus.
**Hinweis:** Verwenden Sie eine andere E-Mail-Adresse als die, die Sie zum Erstellen der Developer Portal-Instanz im vorherigen Lernprogramm verwendet haben.
![API-Produkte](images/32-create-new-account.png)

3. Melden Sie sich nach dem Erstellen des Developer Portal-Kontos an und zeigen Sie die Startseite an. Sie müssen über eine App verfügen, um die APIs subskribieren zu können. Wählen Sie **Apps** aus, um die Seite mit den registrierten Apps aufzurufen.  
  ![API-Produkte](images/33-login.png)

4. Wählen Sie zum Registrieren einer neuen Anwendung **Neue App erstellen** aus.  
  ![Neue App registrieren](images/34-create-new-app.png)

5. Geben Sie einen *Titel* und eine *Beschreibung* für die App ein und wählen Sie **Übergeben** aus.  
  ![Neue App übergeben](images/35-submit-new-app.png) 

6. Da jetzt eine App vorhanden ist, können Sie API-Produktpläne abonnieren. Wählen Sie **Verfügbare APIs** oder **API-Produkte** aus, um die API-Produktpläne zu durchsuchen.  
  ![API-Details](images/36-api-products.png) 

7. Wählen Sie das API-Produkt aus, das Sie abonnieren möchten.  
  ![API-Produkt](images/37-select-product.png) 

8. Wählen Sie **Abonnieren** aus, um den API-Produktplan zu abonnieren.  
  ![API-Produktplan](images/38-subscribe-plan.png) 

9. Wählen Sie die App aus, die Sie für den Produktplan abonnieren möchten und wählen Sie anschließend **Abonnieren** aus.
  ![Abonnementplan für App](images/39-subscribe-app-plan.png) 

10. Die Anwendung wurde erfolgreich für den Produktplan abonniert.
  ![Abonnierung der App erfolgreich](images/310-subscribe-success.png) 

## Fazit

In diesem Lernprogramm haben Sie erfahren, wie Portalbenutzer Produkte und APIs durchsuchen, APIs anzeigen und testen, und wie sie die APIs abonnieren. 

---

## Nächster Schritt

Lernen, [wie Erkenntnisse aus grundlegenden Analysedaten gewonnen werden können](tut_insights_analytics.html).

Erstellen > Verwalten > Schützen > **Teilen** > Analysieren  



