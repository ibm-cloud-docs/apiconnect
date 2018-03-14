---

copyright:
  years: 2017
lastupdated: "2017-07-18"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Informationen zu IBM API Connect

Mit dem Service {{site.data.keyword.apiconnect_full}} können Sie
in kurzer Zeit APIs und Mikroservices erstellen, die auf Node.js und Java-Laufzeitumgebungen basieren. Anschließend können Sie
die erstellten APIs mit geschäftsrelevanten Steuerelementen verwalten, indem Sie verschiedene
Sicherheitsstufen, Sichtbarkeitseinstellungen und Quotenbegrenzungen für die gemeinsame Nutzung der APIs mit Anwendungsentwicklern festlegen. Darüber hinaus stellt der Service {{site.data.keyword.apiconnect_short}}
Tools zum Umgestalten und Erweitern Ihres Geschäfts anhand von Rückschlüssen aus detaillierten Analysen
mit strukturierten gefilterten Suchprozessen bereit.

<object height="315" type="application/x-shockwave-flash" width="560"
data="https://www.youtube.com/v/lmxyiNMER5Y?version=3&amp;hl=en_US">
<desc>Dieses Video bietet einen Überblick über den Service {{site.data.keyword.apiconnect_short}}</desc>
<param name="movie" value="https://www.youtube.com/v/lmxyiNMER5Y?version=3&amp;hl=en_US"/>
<param name="allowFullScreen" value="true"/>
<param name="allowscriptaccess" value="always"/>
<param name="scale" value="noScale"/>
</object>

## API-Erstellung

Mit {{site.data.keyword.apiconnect_short}} können Sie APIs aus Swagger-Definitionen
importieren oder mithilfe einer Proxy-URL bzw. durch Zusammenstellen von Daten aus HTTP-Datenquellen
APIs erstellen. Darüber hinaus unterstützt {{site.data.keyword.apiconnect_short}}
das Erstellen und Testen von APIs im Offline-Modus. Das Entwicklertoolkit verfügt über ein integriertes Micro-Gateway
zum Herstellen einer Verbindung zu Back-End-Datenquellen (z. B. zu einer SQL-Datenbank) und zum Ausführen von
Erstellungs-, Lese-, Aktualisierungs- und Löschoperationen.

APIs werden im Entwicklertoolkit erstellt. Das Entwicklertoolkit beinhaltet eine Befehlszeilenschnittstelle
(Command Line Interface, CLI) sowie die grafische Benutzerschnittstelle API Designer. Um auf das Entwicklertoolkit zuzugreifen,
müssen Sie es zunächst von npm herunterladen und installieren.
Beim Installieren des Toolkits erstellen Sie zunächst ein LoopBack-Projekt. Das folgende Diagramm
zeigt den Inhalt eines LoopBack-Projekts.

- **LoopBack-Projekt**: Das LoopBack-Projekt enthält die LoopBack-Anwendung und das API-Produkt.

- **LoopBack-Anwendung**: Innerhalb der LoopBack-Anwendung befindet sich der API-Endpunkt, der den Zugriff auf
Ihre Datenquelle, Ihre Geschäftsressource oder Ihren Cloud-Service ermöglicht.

- **Produkt**: Das Produkt ist der Container zum Veröffentlichen Ihrer APIs. Ein Produkt enthält einen Plan, der die
API zum Aufrufen des API-Endpunkts enthält.

Das folgende Diagramm zeigt, wo die LoopBack-Anwendung, die API und das Produkt implementiert werden,
nachdem Sie über die Befehlszeilenschnittstelle (CLI) oder die Benutzerschnittstelle des Entwicklertoolkits veröffentlicht wurden.

<img src="images/loopback_project.png" alt="Diagramm des Inhalts eines Loopback-Projekts"/>

- **{{site.data.keyword.Bluemix_short}}-Laufzeit**:
Die LoopBack-App wird in der {{site.data.keyword.Bluemix_short}}-Laufzeit Ihrer Wahl bereitgestellt.

- **Gateway**: Die API wird im Gateway bereitgestellt.

**API Manager**: Das Produkt wird in API Manager bereitgestellt. Sie können in API Manager angeben, wie das Produkt verwendet wird.

<img src="images/Deployed.png" alt="Diagramm, in dem dargestellt wird, an welcher Position die LoopBack-App, die API und das Produkt bereitgestellt werden."/>

Weitere Informationen zu den Tasks, die zum Erstellen von APIs erforderlich sind, finden Sie in [APIs erstellen](creating_apis.html).

## Übersicht über API-Verwaltung

Nachdem ein Produkt bereitgestellt und veröffentlicht wurde, können Sie mit API Manager die Sicherheit, die Quotenbegrenzungen und die Richtlinien verwalten und das Produkt anschließend in einem Developer Portal veröffentlichen.

Ein Produkt enthält einen Plan, der wiederum eine API beinhaltet, wie im folgenden Diagramm dargestellt.

<img src="images/Product.png" alt="Diagramm des Inhalts eines Produkt"/>

### Pläne

Eine API, die für einen Kunden bereitgestellt werden soll, muss in einem Plan enthalten sein. Pläne ermöglichen das Bereitstellen unterschiedlicher Produktangebote. Dabei können Pläne APIs gemeinsam nutzen; ob eine Genehmigung für das Abonnement erforderlich ist, hängt jedoch von dem Plan selbst ab. Darüber hinaus können Sie mithilfe von Plänen Quotenbegrenzungen durchsetzen oder mithilfe von Operationen in den APIs eines Plans die Quotenbegrenzung für diesen Plan außer Kraft setzen.

### Produkte

Pläne und APIs werden in Produkten zusammengefasst. Produkte ermöglichen das Verwalten der Verfügbarkeit und Sichtbarkeit von APIs und Plänen. Mit API Designer können Sie Ihr Produkt erstellen, bearbeiten und bereitstellen. Verwenden Sie API Manager, um den Lebenszyklus Ihres Produkts zu verwalten.

Das folgende Diagramm veranschaulicht die Beziehungen zwischen Produkten, Plänen und APIs. Dabei wird deutlich, dass Pläne nur einem Produkt zugeordnet sind, sie können jedoch verschiedene APIs für andere Pläne beinhalten und APIs mit Plänen aus jedem beliebigen Produkt gemeinsam nutzen. In der Abbildung wird die Hierarchie der Produkte, Pläne und APIs dargestellt. <img src="images/plan_product_hierarchy.png" alt="Abbildung der Hierarchie der Produkte, Pläne und APIs."/>

Pläne können nur innerhalb von Produkten erstellt werden und diese Produkte werden dann in einem Katalog veröffentlicht. In einem Lebenszyklusmanager kann die Verfügbarkeit und Sichtbarkeit von APIs  und Plänen mit API Manager gesteuert werden. Anschließend kann der Kunde im Developer Portal einen der für ihn verfügbaren Pläne abonnieren. Die Verfügbarkeit wird in API Manager festgelegt. Der Benutzer kann lediglich einen Plan aus
einem bestimmten Produkt abonnieren. Mehrere Pläne innerhalb eines Produkts können nützlich sein, um ähnliche Zielsetzungen mit verschiedenen Leistungsanforderungen zu realisieren. Beispielsweise können Sie einen "Demoplan" verwenden, der eine bestimmte API zur Verfügung stellt, und einen "Vollständigen Plan", der mehrere APIs zur Verfügung stellt.

Pläne können jedoch nicht nur steuern, welche APIs ein Kunde nutzen kann, sondern auch Quotenbegrenzungen umsetzen. Eine Quotenbegrenzung kann als Standardrate für einen ganzen Plan implementiert werden, oder um bestimmte Operationen einer API innerhalb des Plans von der Quotenbegrenzung auszuschließen. Verschiedene Pläne können über verschiedene Quotenbegrenzungen verfügen, sowohl zwischen Operationen als auch für die Gesamtbegrenzung. Auf diese Weise können verschiedene Servicestufen für Kunden bereitgestellt werden. Beispiel: Für einen "Demoplan" kann eine Quotenbegrenzung von 10 Aufrufen pro Minute gelten, während ein "Vollständiger Plan" bis zu 1.000 Aufrufe pro Minute zulässt.

**Hinweis:** Durch das Anwenden einer Quotenbegrenzung auf Planebene wird eine Standardquotenbegrenzung erstellt, die für jede Operation in dem betreffenden Plan gilt. Wenn Sie bestimmte Quotenbegrenzungen für bestimmte Operationen festlegen möchten, müssen Sie diese Begrenzungen innerhalb der Operationen angeben, damit diese Einstellungen die Begrenzung auf Planebene außer Kraft setzen.

IBM API Connect unterstützt auch die Implementierung von mehreren Produktversionen. Sie können Versionsnummern festlegen, um die Entwicklung Ihrer Produkte und Pläne zu unterstützen.

**Hinweis:** Die Version eines Produkts unterscheidet sich von den Versionen der APIs, die in den zugehörigen Plänen enthalten sind. Für Pläne können keine spezifischen Versionen erstellt werden; sie verwenden die Version des übergeordneten Produkts.

Weitere Informationen zu den Tasks, die zum Verwalten von APIs erforderlich sind, finden Sie in [APIs verwalten](managing_apis.html).

### Kataloge

Produkte müssen in einem Katalog bereitgestellt und anschließend in Developer-Organisationen veröffentlicht werden, damit sie für Anwendungsentwickler zur Verfügung gestellt werden können. In {{site.data.keyword.apiconnect_short}} können Sie mehrere Kataloge erstellen. Kataloge sind nützlich, um Produkte und APIs zum Testen voneinander zu trennen, bevor Sie sie Developer-Organisationen verfügbar machen.

Ein Katalog ist ein Bereitstellungsziel und verhält sich wie eine logische Partition des Gateway und des Developer Portal. Die URL für API-Aufrufe und für das Developer Portal ist für einen bestimmten Katalog spezifisch. In einer Standardkonfiguration verwendet eine API-Provider-Organisation einen Entwicklungskatalog zum Testen von APIs, die sich in der Entwicklung befinden, und einen Produktionskatalog für das Hosten von APIs, die für eine umfassende Verwendung bereit sind. Ein allgemeiner Ansatz ist das Vorhandensein einer Entwicklungscloud mit einem Entwicklungskatalog, einige Testkataloge und eine Produktionscloud mit einem eigenen Testkatalog.

#### Katalogeinstellungen

Sie können die folgenden Einstellungen auf einen Katalog anwenden:

- **Entwicklung**: Ein Entwicklungskatalog wird standardmäßig bereitgestellt. Ein solcher Katalog darf nur für Testzwecke verwendet werden. In einem Entwicklungskatalog werden die Bereitstellungs- (Staging-) und Veröffentlichungsaktionen erzwungen. Das bedeutet, dass ein bereits veröffentlichtes Produkt bei seiner erneuten Veröffentlichung ohne Warnung überschrieben wird. Werden Konflikte festgestellt, werden diese automatisch vom System aufgelöst. Aktionen zum Rückgängigmachen der Veröffentlichung erfolgen automatisch. Wenn Sie das Testtool in einem Entwicklungskatalog verwenden, werden alle getesteten Produkte durchgesetzt und überschreiben bereitgestellte und veröffentlichte Produkte selbst dann, wenn die Operationen im Developer Portal verwendet werden. Ein aus einem Entwicklungskatalog erstelltes Developer Portal muss in gleicher Weise (d. h. nur für Testzwecke) verwendet werden wie der Katalog.

- **Automatisches Abonnement**: Die Aktivierung des automatischen Abonnements vereinfacht das Testen Ihrer APIs in der API Manager-Benutzerschnittstelle, denn es wird eine Testanwendung mit einer vorab bereitgestellten Client-ID und einem ebensolchen geheimen Clientschlüssel verwendet. Diese Testanwendung ist automatisch bei allen Plänen im Katalog abonniert, sodass Sie beim Testen keinen bestimmten Plan bzw. keine bestimmte Anwendung angeben müssen. Die Testanwendung unterliegt keinerlei Quotenbegrenzungen. Das automatische Abonnement ist nur für Entwicklungskataloge verfügbar.

- **Standard**: Sie können einen Ihrer Kataloge als Standardkatalog festlegen. Dann können Aufrufe an die APIs, die in diesem Katalog veröffentlicht sind, eine kürzere URL verwenden, die nicht den Katalognamen enthält.

Weitere Informationen zur Verwendung des Developer Portal finden Sie in [Developer Portal: Erkennen und Verwenden von APIs](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/capim_devportal_overview.dita).

### Syndikation

Mit der Syndikationsfunktion von {{site.data.keyword.apiconnect_full}}
können Sie Ihre Kataloge in Bereiche aufteilen. Jeder Bereich wird von einem anderen
API-Provider-Entwicklungsteam verwendet und verfügt über seine eigenen Managementfunktionen,
die sich speziell auf die APIs beziehen, die das entsprechende Team in diesem Bereich veröffentlicht.
So kann jedes Team unabhängig seine eigenen APIs verwalten.

Wenn Sie eine API in einem Katalog bereitstellen oder veröffentlichen, für den Bereiche aktiviert sind,
geben Sie den Bereich innerhalb des Katalogs an, in dem die API bereitgestellt oder veröffentlicht werden soll. Jedoch sind sich Anwendungsentwickler,
die für den Katalog auf das Developer Portal zugreifen, der Bereichsaufteilung des Katalogs nicht bewusst und sehen die APIs
als ein koordiniertes Angebot an.
Jeder Bereich verfügt über sein eigenes Produkt-Lifecycle-Management, eigene Abonnementgenehmigungen und Analysedaten.
Mithilfe einer bereichsspezifischen Zugriffssteuerung können Sie den Benutzerzugriff auf die einzelnen Bereiche eingrenzen.
Beispielsweise kann ein Entwickler im Team 'Flights' nur APIs im Bereich 'Flights' bereitstellen.

**Hinweis:** Bereiche sind in einem Katalog standardmäßig inaktiviert. Sie können Bereiche durch das Ändern
der Katalogeinstellungen aktivieren.

Informationen zum Aufteilen eines Katalogs finden Sie in [Katalog in Bereiche aufteilen](create_catalog.html#apic_spaces).
