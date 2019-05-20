---

copyright:
  years: 2017
lastupdated: "2017-06-05"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal

subcollection: apiconnect

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Glossar
{: #glossary_apic_glossary}

Dieses Glossar enthält die in {{site.data.keyword.apiconnect_short}} verwendeten Begriffe und ihre Definitionen.

- **Abonnement**: Über ein Abonnement erhält ein Anwendungsentwickler Zugriff auf die Ressourcen, die durch eine API zur Verfügung gestellt werden. Der Anwendungsentwickler abonniert über das Developer Portal den Plan, in dem die API veröffentlicht ist.

- **Anbietererweiterung**: Eine Anbietererweiterung wird zu einer REST-API hinzufügt, um die OpenAPI-Spezifikation (Swagger 2.0) zu erweitern.

- **Anwendung**: Ein Teil des Client-Codes, der auf APIs zugreift, um mit einem Service, System oder Inhalt zu interagieren. Bei Anwendungen handelt es sich normalerweise um Webanwendungen oder mobile Apps.

- **API-Entwickler**: Ein API-Entwickler erstellt und konfiguriert APIs, Produkte und Richtlinien für Provider-Organisationen, in denen er Mitglied ist. Ein API-Entwickler kann Mitglied einer oder mehrerer Provider-Organisationen sein. Der API-Entwickler ist mehr auf die technische Implementierung von APIs als auf die Geschäftsbeziehung mit Anwendungsentwicklern fokussiert.

- **API-Operation**: Eine Einheit einer REST-API, die aufgerufen werden kann. Eine API-Operation  besteht aus einem HTTP-Verb und einem URL-Pfad, der dem Kontextstammelement der API untergeordnet ist. 

- **API Designer**: Die Benutzerschnittstelle zur Erstellung von APIs.

- **API Manager**: Die Benutzerschnittstelle (UI) zum Verwalten von APIs, Plänen und Produkten.

- **Assembly**: Anwendungsprogrammierschnittstelle (API), die umfassende Funktionen zur Interaktion mit einer Anwendung zur Verfügung stellt: Sie führt Seitenaufrufe für externe Services durch und setzt anschließend die Antwort um bzw. kumuliert sie, bevor die Antwort an die aufrufende Anwendung weitergeleitet wird.

- **Benutzerregistry**: Eine Benutzerregistry ist eine Methode zum Sichern des Zugriffs auf Kataloge und APIs. Der Benutzer kann APIs mit einer Benutzerregistry sichern, sodass beim Aufruf einer API Benutzerberechtigungsnachweise angegeben werden müssen.

- **Client-ID**: Eine Einzelinformation, die eine Einzelanwendung kennzeichnet. Eine Anwendung kann eine API nur aufrufen, wenn sie einen Anwendungsschlüssel übergibt, der vom {{site.data.keyword.apiconnect_short}}-System erkannt und dem Zugriff auf die API gewährt wird. Der Anwendungsschlüssel wird mithilfe eines HTTP-Abfrageparameters durch den Client übergeben.

- **Community**: Eine Gruppe von Entwicklerorganisationen. Sie wird als Gruppierungskonstrukt beim Veröffentlichen von APIs verwendet. Mithilfe von Communitys wird die Sichtbarkeit und Zugänglichkeit von APIs beschränkt. Eine API kann für ausgewählte Communitys veröffentlicht werden, was bedeutet, dass nur Anwendungsentwickler innerhalb dieser Organisationen die API sehen können.

- **Geheimer Client-Schlüssel**: Eine Einzelinformation, die zusammen mit dem Anwendungsschlüssel zur Überprüfung der Identität einer Anwendung verwendet wird. Eine API kann so konfiguriert werden, dass für Clientanwendungen die Angabe ihres geheimen Anwendungsschlüssels mit ihrem Anwendungsschlüssel erforderlich ist. Der geheime Anwendungsschlüssel fungiert effektiv als nur der Anwendung bekanntes Kennwort. Der geheime Anwendungsschlüssel wird mithilfe eines HTTP-Abfrageparameters durch den Client übergeben.

- **Katalog**: Ein Katalog ist ein Bereitstellungsziel und verhält sich wie eine logische Partition des Gateway und des Developer Portal. Die URLs für API-Aufrufe und für das Developer Portal sind für einen bestimmten Katalog spezifisch.

- **LoopBack-Modell**: Ein LoopBack-Modell ist ein JavaScript-Objekt, das Anwendungsdaten darstellt und Validierungsregeln, Datenzugriffsfunktionalität und Geschäftslogik enthält. LoopBack-Modelle bieten standardmäßig eine REST-API und stellen für den Zugriff auf Back-End-Daten Verbindungen zu Datenquellen her.

- **LoopBack-Datenquelle**: Eine LoopBack-Datenquelle ist ein JavaScript-Objekt, das einen Back-End-Service darstellt, wie z. B. eine Datenbank, eine REST-API (zum Verarbeiten) oder einen SOAP-Web-Service. Datenquellen werden von Connector gesichert, die ihrerseits direkt mit der Datenbank oder einem anderen Back-End-Service kommunizieren.

- **Organisation**: Die Entität, die Eigner von APIs oder Anwendungen ist, die APIs verwenden. Eine Provider-Organisation ist Eigner von APIs sowie zugeordneter Pläne und kann zusätzlich Eigner von Anwendungen sein. Eine Entwicklerorganisation ist nur Eigner von Anwendungen. Eine Organisation hat mindestens einen Eigner. Bei einer Organisation kann es sich um ein Projektteam, eine Abteilung oder einen Unternehmensbereich handeln.

- **Pfad**: Ein Pfad definiert die Route, über die Benutzer auf REST-APIs zugreifen. Ein Pfad besteht aus einer oder mehreren HTTP-Operationen, wie z. B. GET oder POST. 

- **Plan**: Das Verpackungskonstrukt, anhand dessen APIs Entwicklern zur Verfügung gestellt werden. Ein Plan stellt eine Sammlung von Vorgängen oder Operationen von einer oder mehreren APIs zur Verfügung und wird für Communitys von Anwendungsentwicklern veröffentlicht. Anwendungsentwickler erhalten Zugriff auf APIs, indem Sie Anwendungen für den Zugriff auf Pläne registrieren. Ein Plan geht mit einer Sammlung von Richtlinieneinstellungen einher. In der einfachsten Form definiert ein Plan eine einzelne Quotenrichtlinie, die für alle API-Operationen gilt, auf die durch den Plan zugegriffen wird. In komplexeren Fällen können einem Plan zusätzliche Richtlinien zugeordnet werden.

- **Produkt**: Produkte bieten eine Methode zum Gruppieren von APIs in einem Paket, das für eine bestimmte Verwendung gedacht ist. Zudem enthalten sie Pläne, mit deren Hilfe zwischen verschiedenen Angeboten unterschieden werden kann. Pläne können nur innerhalb von Produkten erstellt werden und diese Produkte werden dann in einem Katalog veröffentlicht.

- **Proxy**: Eine Anwendungsprogrammierschnittstelle (API), die Anforderungen an eine benutzerdefinierte Back-End-Ressource weiterleitet und die Antworten zurück zur aufrufenden Anwendung leitet.

- **Richtlinie**: Eine Richtlinie ist ein Konfigurationselement, das während der Behandlung eines API-Aufrufs zur Laufzeit einen bestimmten Aspekts der Verarbeitung im Gateway-Server steuert. Richtlinien sind die Bausteine von Assembly-Abläufen. Richtlinien stellen das Mittel zur Konfiguration der Funktionalität, wie zum Beispiel Sicherheit, Protokollierung, Routing (Weiterleitung) von Anforderungen zu Zielservices und Umsetzung von Daten aus einem Format in ein anderes. Richtlinien können im Kontext einer API oder im Kontext eines Plans konfiguriert werden.

- **Rolle**: Eine Rolle definiert Berechtigungen, mit denen Benutzern gegenüber Funktionalität aktiviert wird. Jede Rolle verfügt über eine andere Gruppe an Berechtigungen.

- **Sandbox-Katalog**: In einem Sandbox-Katalog werden für Veröffentlichungs- und Lebenszyklusaktionen Genehmigungen übergangen. Wenn ein Nicht-Sandbox-Katalog in einen Sandbox-Katalog umgewandelt wird, werden anstehende Genehmigungen abgebrochen. Ein Sandbox-Katalog wird zum Testen von APIs verwendet, die sich noch in der Entwicklung befinden.

- **Sicherheitsdefinition**: Eine Sicherheitsdefinition gibt alle Einstellungen für einen bestimmten Aspekt der API-Sicherheit an, zum Beispiel die Benutzerregistry, die verwendet wird, um den Zugriff auf die API zu authentifizieren.

- **SSL-Profil**: Ein SSL-Profil wird zum Sichern der Übertragung von Daten über Websites verwendet. SSL-Zertifikate stellen sicher, dass an Websites übergebene Informationen nicht gestohlen oder manipuliert werden.

- **Staging**: Der Vorgang des Umstufens, bei dem eine Anwendung oder ein Produkt den Entwurfsstatus verlässt und zu einem Katalog wird, der vor der Veröffentlichung steht.

- **Veröffentlichen**: Der Vorgang des Umstufens einer Anwendung oder eines Produkts aus der Bereitstellung (dem Staging), damit die darin enthaltenen Pläne und APIs für Anwendungsentwickler verfügbar werden, sodass diese auf sie zugreifen und sie nutzen können.
