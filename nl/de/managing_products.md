---

copyright:
  years: 2017
lastupdated: "2017-12-15"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal

subcollection: apiconnect

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Produkte verwalten
{: #managing_products}

Detaillierte Informationen zur Vorgehensweise beim Verwalten Ihrer Produkte finden Sie in der IBM&reg; Knowledge Center-Dokumentation unter [Managing your Products ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.apionprem.doc/task_product_management.html){: #new_window}.

## Produktlebenszyklus
{: #prod_lifecycle_managing_products}

Während des Verwaltungsprozesses durchlaufen Ihre Produktversionen verschiedene Lebenszyklusstatus -
angefangen mit dem Bereitstellen einer ersten Entwurfsversion des Produkts in einer Umgebung über das Veröffentlichen,
um die Produktversion Ihren Anwendungsentwicklern zur Verfügung zu stellen, bis zum Zurückziehen und Archivieren der
Produktversion. Die folgende Tabelle und das zugehörige Diagramm beschreiben die verschiedenen Status im
Produktlebenszyklus für eine Produktversion.

<table summary="" id="apic_004__table_lym_rxj_gv" class="defaultstyle"><caption class="style-scope doc-content">Tabelle 1. Produktlebenszyklusstatus beim API-Management</caption>
<thead class="style-scope doc-content">
<tr class="style-scope doc-content doc-tr-even">
<th style="width: 11.25%" id="d3569e1968" class="thleft thbot style-scope doc-content">Status</th>
<th style="width: 88.75%" id="d3569e1970" class="thleft thbot style-scope doc-content">Beschreibung</th>
</tr>
</thead>
<tbody class="style-scope doc-content">
<tr class="style-scope doc-content doc-tr-odd">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">Entwurf</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">Das Produkt ist weder bereitgestellt noch einem API Connect-Katalog zugeordnet.</td>
</tr>
<tr class="style-scope doc-content doc-tr-even">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">Bereitgestellt</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">Eine nicht veränderbare Kopie der Produktversion ist in der Zielumgebung
bereitgestellt. 'Bereitgestellt' ist der Anfangsstatus beim Bereitstellen eines Produktentwurfs. Ein Produkt mit dem Status 'Bereitgestellt' ist noch nicht
für Entwickler sichtbar und kann noch nicht von Entwicklern abonniert werden.</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">Veröffentlicht</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">Die Produktversion wird zielgruppenspezifisch für Entwickler oder Communitys
angezeigt und kann abonniert werden.</td>
</tr>
<tr class="style-scope doc-content doc-tr-even">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">Veraltet</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">Die Produktversion ist nur für Entwickler sichtbar, deren Anwendungen derzeit
abonniert sind. Neue Abonnements für das Produkt sind nicht möglich.</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">Zurückgezogen</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">Die Produktversion kann weder angezeigt noch abonniert werden und alle zugehörigen
APIs sind gestoppt. Eine zurückgezogene Produktversion wird standardmäßig auf der Seite
Produkte in der Benutzerschnittstelle von API Manager angezeigt.</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">Archiviert</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">Die Produktversion kann weder angezeigt noch abonniert werden und alle zugehörigen
APIs sind gestoppt. Die Produktversion wird nicht standardmäßig auf der Seite Produkte in der Benutzerschnittstelle von API Manager angezeigt.</td>
</tr>
</tbody>
</table>

### Produktlebenszyklusabläufe
{: #prod_lifecycle_flows_managing_products}

Das folgende Diagramm zeigt die möglichen Lebenszyklusstatus für eine Produktversion sowie die Produktverwaltungsoperationen beim Übergang einer
Produktversion von einem Lebenszyklusstatus in einen anderen. Beispielsweise versetzt die Operation 'Zurückziehen' eine Produktversion aus dem Status
'Veröffentlicht' in den Status 'Zurückgezogen'.

<img alt="Lebenszyklusstatusdiagramm für Produktversion" src="images/apic_plan_lifecycle.png">


## Produkt erstellen
{: #create_product_managing_products}

Erstellen Sie ein Produkt, um mehrere APIs und Pläne zu einem Angebot zusammenzufassen, das
Sie Ihren Entwicklern zur Verfügung stellen möchten. Ein Plan enthält Einstellungen für Quotenbegrenzungen,
die auf den gesamten Plan oder auf einzelne Operationen in einer API angewendet werden können. Durch Produkte
und Pläne können Sie präziser steuern, auf welche APIs Ihre Entwickler zugreifen können. Nachdem Sie ein Produkt
erstellt haben, muss das Produkt bereitgestellt werden. Beim Bereitstellen wird das Produkt in einen aktiven Status
versetzt und Sie können die im Produkt enthaltenen APIs aufrufen und testen. Ein bereitgestelltes Produkt ist noch nicht für Entwickler sichtbar.

**Tipp**: Alternativ zu der hier beschriebenen Methode können Sie ein Produkt auch während
der Erstellung einer API erstellen. Wenn Sie eine API über die Developer Toolkit-Befehlszeilenschnittstelle
erstellen, wird automatisch ein Produkt erstellt. Anschließend können Sie die Einstellungen für das Produkt
ändern, indem Sie das neue Produkt auf der Seite **Produkte** von API Designer öffnen.

Führen Sie die folgenden Schritte aus, um mit API Designer ein Produkt zu
erstellen:
1. Um die Benutzerschnittstelle von API Designer zu öffnen, öffnen Sie eine Befehlszeile und geben Sie den folgenden Befehl ein:
```
apic edit
```
API Designer wird in Ihrem Standardbrowser geöffnet.

2. Klicken Sie im Navigationsbereich von API Designer auf **Produkte**.
Die Registerkarte 'Produkte' wird geöffnet.

3. Klicken Sie auf **Hinzufügen** und anschließend auf **Neues Produkt**.
Das Fenster zum Hinzufügen eines neuen Produkts wird geöffnet.

4. Füllen Sie die folgenden Felder aus:
    - Titel
    - Name
    - Version

5. Klicken Sie auf **Hinzufügen**.
Die Registerkarte 'Design' für das neue Produkt wird geöffnet.

6. **Optional**:
Geben Sie die Beschreibung, den Ansprechpartner, die Lizenz und die Servicebedingungen für
das Produkt im Abschnitt **Info** ein.

7. Geben Sie im Abschnitt **Sichtbarkeit** an, für welche Benutzer
das Produkt sichtbar sein soll. Auswahlmöglichkeiten sind **Öffentlich**, **Authentifizierte
Benutzer** oder **Angepasst**. Wenn Sie die Option **Angepasst** auswählen,
können Sie im Feld **Typ zum Hinzufügen** nach den Developer-Organisationen oder
-Communitys suchen, für die die Pläne im Produkt sichtbar sein sollen.

    **Hinweis:**
    Um nach Developer-Organisationen oder -Communitys zu suchen, muss das Produkt den Status
    'Bereitgestellt', 'Veröffentlicht' oder 'Veraltet' aufweisen. Wenn es sich bei dem Katalog, in dem das bereitgestellte,
    veröffentlichte oder veraltete Produkt enthalten ist, nicht um einen Sandbox-Katalog handelt, können Sie keine weiteren Änderungen
    an dem Produkt vornehmen, solange es eine dieser Statusangaben aufweist. Weitere Informationen finden Sie unter [Produktlebenszyklus](#prod_lifecycle_managing_products).

8. Geben Sie an, welche Benutzer das Produkt abonnieren können. Auswahlmöglichkeiten sind **Authentifizierte
Benutzer** oder **Angepasst**. Wenn Sie **Angepasst** auswählen,
können Sie im Feld **Typ zum Hinzufügen** nach den Developer-Organisationen oder
-Communitys suchen, die in der Lage sein sollen, die Pläne in dem Produkt zu abonnieren.

9. Geben Sie im Abschnitt für APIs an, welche APIs Sie in das Produkt einbeziehen möchten.
    1. Klicken Sie auf das Symbol **API hinzufügen**.
    2. Wählen Sie die APIs aus, die Sie einbeziehen möchten, und klicken Sie anschließend auf **Anwenden**. Die
    ausgewählten APIs werden aufgelistet.

10. Um eine API für Anwendungsentwickler verfügbar zu machen, müssen Sie die API in einen Plan einfügen. Um einen
oder mehrere Pläne zu dem Produkt hinzuzufügen, klicken Sie auf das Symbol zum Hinzufügen von Plänen****.
    1. Erweitern Sie den neu erstellten Plan. Wenn Sie bereits APIs zu Ihrem Produkt hinzugefügt haben,
werden diese APIs automatisch einbezogen.
    2. Ändern Sie den Namen des Plans in den Feldern **Titel** und **Name**
und fügen Sie eine optionale Beschreibung hinzu.
    **Hinweis:** Es wird automatisch ein Standardplan erstellt, in den Sie Ihre API einbeziehen können,
    falls Sie keinen eigenen Plan erstellen möchten. Wenn Sie den Standardplan nicht verwenden möchten, müssen Sie ihn löschen,
    da ein Produkt nicht bereitgestellt werden kann, wenn es Pläne ohne einbezogene APIs enthält.

11. Stellen Sie sicher, dass die erforderlichen APIs in den Plan einbezogen sind.
    1. Erweitern Sie den Plan, zu dem Sie eine API hinzufügen möchten.
    2. Stellen Sie im Bereich für einbezogene APIs sicher, dass die Kontrollkästchen für die erforderlichen APIs ausgewählt sind. Wenn APIs ausgewählt sind,
die Sie nicht in den Plan einbeziehen möchten, den Sie momentan bearbeiten, wählen Sie die betreffenden Kontrollkästchen
ab.

12. **Optional**:
Fügen Sie die Abrechnungsinformationen für den Plan hinzu. Zum Hinzufügen der Abrechnungsinformationen müssen Sie ein Konto mit einem Service zur Verarbeitung von Kreditkarten hinzufügen, damit Kunden mit einer Kreditkarte zahlen können. Monatliche Abrechnungspläne werden in jedem Monat an demselben Tag abgerechnet.

13. **Optional**:
Wenn Sie festlegen möchten, welche Operationen einer API in den Plan einbezogen werden,
bewegen Sie den Cursor über die API, in der die Operation enthalten ist. Klicken Sie auf das Symbol **Operationen anzeigen** und wählen Sie
anschließend die Kontrollkästchen für die Operationen aus bzw. ab, die Sie ein- bzw. ausschließen möchten.

14. **Optional**:
Um zu Ihrem Plan eine Quotenbegrenzung hinzuzufügen, wählen Sie das Kontrollkästchen **Unbegrenzt** ab und geben Sie anschließend das
Quotenlimit an, das Sie anwenden möchten. Wenn das Kontrollkästchen **Festen Grenzwert durchsetzen**
ausgewählt ist, verhindert der Plan, dass Anwendungen die API aufrufen, sobald die Quotenbegrenzung
erreicht ist. Andernfalls wird eine Warnung ausgegeben.

    **Hinweis:** Durch das Anwenden einer Quotenbegrenzung auf Planebene wird eine Standardquotenbegrenzung erstellt, die für jede
    Operation in dem betreffenden Plan gilt. Wenn Sie bestimmte Quotenbegrenzungen für bestimmte Operationen
    festlegen möchten, müssen Sie diese Begrenzungen innerhalb der Operationen angeben, damit diese Einstellungen
    die Begrenzung auf Planebene außer Kraft setzen.

15. **Optional**:
Geben Sie an, ob für Ihren Plan eine Abonnementgenehmigung erforderlich ist. Wenn für Abonnements der Entwickler eine Genehmigung über
die Benutzerschnittstelle von API Manager erforderlich sein soll, wählen Sie **Abonnementgenehmigung erforderlich** aus.
Wenn keine Genehmigung erforderlich sein soll, wählen Sie das Kontrollkästchen ab.

16. **Optional**:
Fügen Sie eine Quotenbegrenzung zu einer Operation hinzu.
    1. Bewegen Sie den Cursor über die API, in der die Operation enthalten ist,
und klicken Sie auf das Symbol **Operationen anzeigen**.
    2. Bewegen Sie den Cursor über die Operation, auf die Sie eine Quotenbegrenzung anwenden möchten. Klicken Sie auf
das Symbol **Quotenbegrenzung bearbeiten**.
    3. Stellen Sie sicher, dass das Kontrollkästchen **Unbegrenzt** abgewählt ist,
und geben Sie anschließend die Quotenbegrenzung an, die Sie anwenden möchten. Wenn das Kontrollkästchen **Festen Grenzwert durchsetzen**
ausgewählt ist, verhindert der Plan, dass Anwendungen die API aufrufen, sobald die Quotenbegrenzung
erreicht ist. Andernfalls wird eine Warnung ausgegeben.

- Klicken Sie auf das Symbol **Speichern**, um Ihre Änderungen zu speichern.

Sie haben ein Produkt erstellt und eine Gruppe von APIs und Plänen zu einem Angebot zusammengefasst,
das Sie nun für Ihre Entwickler verfügbar machen können.
Stellen Sie als Nächstes Ihr Produkt in einem Katalog bereit; dieser Vorgang wird im nächsten Abschnitt [Produkt bereitstellen](#stage_product_managing_products}) erläutert.


## Produkt bereitstellen
{: #stage_product_managing_products}

Stellen Sie ein Produkt bereit, um vor dem Veröffentlichen eine bestimmte Version des Produkts
in einem Katalog zu erstellen. Ein Produkt mit dem Status 'Bereitgestellt' ist noch nicht für Entwickler sichtbar
und kann noch nicht von Entwicklern abonniert werden.

**Hinweis:** Die Benutzerschnittstelle von API Manager bietet ebenfalls die Möglichkeit zum Bereitstellen von Produkten;
die bevorzugte Methode für diese Tasks ist jedoch die Benutzerschnittstelle von API Designer, wie in der folgenden Prozedur beschrieben.

1. Klicken Sie im Navigationsbereich von API Designer auf **Produkte**.
Die Registerkarte 'Produkte' wird geöffnet.

2. Klicken Sie auf das **Produkt**, mit dem Sie arbeiten möchten. Wenn mehrere Versionen des Produkts vorhanden sind,
stellen Sie sicher, dass Sie auf die Version klicken, mit der Sie arbeiten möchten.

3. Klicken Sie auf das Symbol **Veröffentlichen**.

4. Gehen Sie wie folgt vor, wenn der Katalog, in dem Sie das Produkt bereitstellen möchten, in der Liste enthalten ist:
    1. Wählen Sie den Katalog aus, den Sie benötigen. 
    2. Wählen Sie **Nur bereitstellen (Produkte werden
nicht veröffentlicht)** und danach **Veröffentlichen** aus. Ihr Produkt wird
bereitgestellt.

5. Gehen Sie wie folgt vor, wenn der Katalog, in dem Sie das Produkt bereitstellen möchten, nicht in der Liste enthalten ist:
    1. Klicken Sie auf **Ziele hinzufügen und verwalten**.
    2. Klicken Sie auf **{{site.data.keyword.Bluemix_notm}}-Ziel hinzufügen**.
    3. Wählen Sie die {{site.data.keyword.Bluemix_short}}-**Region**
für die Veröffentlichung aus.
    4. Wählen Sie die {{site.data.keyword.Bluemix_notm}}-**Organisation**
für die Veröffentlichung aus.
    5. Eine Liste mit Katalogen wird angezeigt. Wählen Sie den Katalog aus, in dem Sie die Anwendung veröffentlichen möchten.
    6. Klicken Sie auf **Weiter**.
    7. Wenn Sie über eine LoopBack-Anwendung verfügen, die Sie veröffentlichen möchten, wählen Sie die App aus, in der die Veröffentlichung erfolgen soll.
Wählen Sie andernfalls **Keine** aus.
    8. Klicken Sie auf **Speichern**.
    9. Klicken Sie erneut auf **Veröffentlichen** und wählen Sie das Ziel aus, das Sie gerade hinzugefügt haben.
    10. Wählen Sie den erforderlichen Katalog aus.
    11. Wählen Sie **Nur bereitstellen** aus.
    12. Klicken Sie auf **Veröffentlichen**.

Ihr Produkt wird in einem Katalog bereitgestellt. Um den Status des Produkts im Katalog anzuzeigen,
öffnen Sie die Benutzerschnittstelle von API Manager, wählen Sie im Navigationsbereich den Abschnitt
für das Dashboard aus und klicken Sie auf den betreffenden Katalog. Für das Produkt wird der Status 'Bereitgestellt' angezeigt.

- Öffnen Sie das {{site.data.keyword.Bluemix_notm}} **-Dashboard**. Die Kachel für die Anwendung wird im Bereich 'Anwendungen' angezeigt.

Öffnen Sie API Manager, um Ihr Produkt in einer Community zu veröffentlichen, von wo aus Anwendungsentwickler im Developer Portal darauf zugreifen können; dieser Vorgang wird im nächsten Abschnitt [Produkt veröffentlichen](#publish_proj_managing_products}) erläutert.


## Produkt veröffentlichen
{: #publish_proj_managing_products}

Beim Veröffentlichen eines Plans werden APIs für Anwendungsentwickler sichtbar und zugänglich gemacht.
Beim Veröffentlichen eines Produkts wird das betreffende Produkt im {{site.data.keyword.Bluemix_short}}-**Katalog**
und im integrierten Developer Portal für Anwendungsentwickler sichtbar und
verwendbar.

### Voraussetzungen
{: #prereq_publish_proj_managing_products}

Sie müssen ein Produkt zunächst bereitstellen, damit es veröffentlicht werden kann. Weitere Informationen zum Bereitstellen von Produkten
finden Sie unter [Produkt bereitstellen](#stage_product_managing_products).

Führen Sie die folgenden Schritte aus, um ein Produkt zu veröffentlichen:

1. Erweitern Sie im Navigationsbereich von API Manager den Bereich **Kataloge**
und wählen Sie den Katalog aus, mit dem Sie arbeiten möchten. Die Registerkarte 'Produkte' für den Katalog
wird geöffnet und alle in dem Katalog verfügbaren Produkte werden angezeigt. Sie können festlegen, welche
Status angezeigt werden sollen, indem Sie die entsprechenden Filteroptionen rechts in der Anzeige auswählen.

2. Klicken Sie neben der Produktversion, mit der Sie arbeiten möchten, auf das Symbol
**Verwalten** und anschließend auf **Veröffentlichen**. Das Dialogfeld
zum Bearbeiten der Sichtbarkeit und der Abonnenten wird angezeigt.

3. Geben Sie die folgenden Optionen an:
    - `Sichtbar für:` Sie können **Öffentliche Benutzer**, **Authentifizierte Benutzer**
    oder **Angepasst** auswählen. Wenn Sie `Angepasst` auswählen, können Sie im Feld **Typ zum Hinzufügen**
nach den Organisationen oder Communitys suchen, für die das Produkt sichtbar sein soll.
    - `Abonnierbar für:` Sie können **Authentifizierte Benutzer** oder **Angepasst** auswählen. Wenn Sie `Angepasst` auswählen, können Sie im Feld **Typ zum Hinzufügen**
nach den Organisationen oder Communitys suchen, für die das Produkt sichtbar sein soll.

4. Klicken Sie auf **Veröffentlichen**.
    Wenn zum Veröffentlichen von Produkten in diesem Katalog eine Genehmigung erforderlich ist, wird eine Genehmigungsanforderung gesendet und das Produkt wird in
    den Status 'Anstehend' versetzt. Das Produkt wird veröffentlicht, sobald die Anforderung genehmigt wurde. Falls keine Genehmigung
    erforderlich ist, wird die Produktversion sofort veröffentlicht und in den Status 'Veröffentlicht'
    versetzt.

Ihr Produkt befindet sich im Status 'Veröffentlicht'. Das Produkt ist in Ihrem Katalog
veröffentlicht und für die von Ihnen angegebenen Organisationen oder Communitys verfügbar. Anwendungsentwickler,
die den von Ihnen ausgewählten Gruppen angehören, können die im Produkt enthaltenen APIs anzeigen und
verwenden. Alle Anforderungen der Anwendungsentwickler, die Ihr Produkt verwenden möchten,
werden in der Registerkarte 'Genehmigungen' des betreffenden Katalogs angezeigt und können dort
von Ihnen akzeptiert oder abgelehnt werden.


## Produkt in Bluemix veröffentlichen
{: #pub_to_bm_managing_products}

Führen Sie die folgenden Schritte aus, um die Produkte im Abschnitt **APIs durchsuchen** des {{site.data.keyword.apiconnect_short}}-Dashboards anzuzeigen.

### Voraussetzungen
{: #prereq_pub_bm_managing_products}

Vor dem Veröffentlichen einer REST-API, die mit LoopBack implementiert wurde, müssen Sie sicherstellen, dass
die Laufzeit Ihrer App veröffentlicht ist und Ihr Produkt so bereitgestellt wurde, dass der Aufruf-Proxy auf die
neue App verweist. Weitere Informationen hierzu finden Sie in [Loopback-Anwendung bereitstellen und veröffentlichen](/docs/services/apiconnect?topic=apiconnect-managing_apis#stage_publish_lb_app_managing_apis).

1. Klicken Sie in der Benutzerschnittstelle von API Manager auf **Hinzufügen** > **Katalog**. Das Fenster **Katalog hinzufügen** wird angezeigt.

2. Füllen Sie die folgenden Felder aus und klicken Sie anschließend auf **Hinzufügen**:
    - Anzeigename
    - Name
	
3. Wählen Sie den Katalog aus, den Sie erstellt haben.

4. Klicken Sie auf das Symbol **Einstellungen**.

5. Klicken Sie auf **Portal** und wählen Sie eine der folgenden Optionen aus:
    - **IBM Developer Portal**. Wenn Sie diese Option auswählen. wird die Portal-URL
angezeigt.
    - **Anderes**. Wenn Sie diese Option auswählen, geben Sie die URL
für das Portal ein, das Sie verwenden möchten.

6. Klicken Sie im Abschnitt für Benutzerregistry und Einladung auf den Pfeil **Benutzerregistry**
und wählen Sie **SAML** aus.

7. Klicken Sie im Navigationsbereich auf das Symbol **Entwickler**.

8. Klicken Sie auf **IBM Cloud-Organisation hinzufügen**.

9. Fügen Sie Ihre {{site.data.keyword.Bluemix_short}}-Benutzer-E-Mail-Adresse
hinzu und klicken Sie auf **Hinzufügen**.

10. Eine Einladung wird an Ihre E-Mail-Adresse gesendet.

11. Klicken Sie auf den Link in der E-Mail, um die Einladung anzunehmen.
Die {{site.data.keyword.Bluemix_notm}}-Benutzerschnittstelle
wird geöffnet.

12. Wählen Sie Ihre {{site.data.keyword.Bluemix_notm}}-Organisation aus
und klicken Sie auf **Bestätigen**.

13. Klicken Sie in der Benutzerschnittstelle von API Manager auf das Symbol **Produkte**.

14. Klicken Sie neben der Produktversion, mit der Sie arbeiten möchten, auf das Symbol
**Verwalten** und anschließend auf **Veröffentlichen**. Das Dialogfeld
zum Bearbeiten der Sichtbarkeit und der Abonnenten wird angezeigt.

15. Geben Sie die folgenden Optionen an:
    - **Sichtbar für:** Wählen Sie **Angepasst** aus und verwenden Sie das Feld **Typ zum Hinzufügen** zum
Auswählen der Developer-Organisation und aller anderen, die Sie hinzufügen möchten.
    - **Abonnierbar für:** Wählen Sie **Angepasst** aus und verwenden Sie das Feld **Typ zum Hinzufügen** zum
Auswählen der Developer-Organisation und aller anderen, die Sie hinzufügen möchten.

16. Klicken Sie auf **Veröffentlichen**.

Wenn zum Veröffentlichen von Produkten in diesem Katalog eine Genehmigung erforderlich ist, wird eine Genehmigungsanforderung gesendet und das Produkt wird in
    den Status 'Anstehend' versetzt. Das Produkt wird veröffentlicht, sobald die Anforderung genehmigt wurde. Falls keine Genehmigung erforderlich ist,
wird die Produktversion sofort veröffentlicht und in den Status 'Veröffentlicht'
versetzt.

Das Produkt wird in der Registerkarte **APIs durchsuchen** des {{site.data.keyword.apiconnect_short}}-**Dashboards**
angezeigt. Wenn Sie auf den Link für das Produkt klicken, wird das Produkt im Developer Portal
aufgerufen.
