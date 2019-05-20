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

# Fehlerbehebung
{: #apic_troubleshoot}

Dieser Abschnitt enthält Antworten auf häufig gestellte Fragen bei der Fehlerbehebung für {{site.data.keyword.apiconnect_long}} unter {{site.data.keyword.Bluemix_notm}}.
{:shortdesc}

## Benutzername und Kennwort, die zum Hinzufügen des {{site.data.keyword.Bluemix_notm}}-Service 'API Connect' erforderlich sind
{: #user_pw_apic_troubleshoot}

Nachdem Sie den Service zum {{site.data.keyword.Bluemix_notm}}-Dashboard hinzugefügt haben, werden Sie aufgefordert, Benutzernamen und Kennwort einzugeben, wenn Sie versuchen, ihn zu öffnen. 

### Symptome
{: #ts_sym_usernamepw_apic_troubleshoot}

Sie können nicht direkt auf den {{site.data.keyword.Bluemix_notm}}-Service zugreifen, wenn Sie eine neue {{site.data.keyword.apiconnect_short}}-Instanz öffnen, sondern müssen sich dazu an API Manager anmelden.

### Ursache
{: #ts_cause_usernamepw_apic_troubleshoot}

Im Browser ist das Blockieren von Cookies eingestellt oder es ist eine eingeschränktere Ebene eingerichtet, als für {{site.data.keyword.apiconnect_notm}} erforderlich ist.

### Lösung
{: #ts_res_usernamepw_apic_troubleshoot}

Aktivieren oder erhöhen Sie die Berechtigungsebene der Cookies in den Browsereinstellungen, bis der {{site.data.keyword.Bluemix_notm}}-Service geöffnet werden kann.

## Developer Toolkit kann nicht installiert werden
{: #unable_tk_apic_troubleshoot}

Nach der Bereitstellung des API Connect-Service schlägt der Installationsversuch für Developer Toolkit
fehl.

### Symptome
{: #ts_sym_noinstalltk_apic_troubleshoot}

Bei der Installation von Developer Toolkit werden die folgenden
Fehler angezeigt:
```
npm ERR! Error: EACCES, mkdir '/usr/local/lib/node_modules/apiconnect'
...
npm ERR! Please try running this command again as root/Administrator
...
```

### Ursache
{: #ts_cause_noinstalltk_apic_troubleshoot}

Sie verfügen nicht über die Berechtigungen, die erforderlich sind, um Dateien oder Verzeichnisse zu erstellen.

### Lösung
{: #ts_res_noinstalltk_apic_troubleshoot}

Ändern Sie die Berechtigungen für die angegebenen Verzeichnisse oder führen Sie den Befehl mit
`sudo` aus. Auf einem lokalen Entwicklungssystem ist es besser, die Korrektur der Verzeichnisberechtigungen wie folgt
vorzunehmen:
```
sudo chown -R $USER /usr/local
```
{:codeblock}

Durch diesen Befehl wird Ihr Benutzerkonto zum Eigner des Verzeichnisses `/usr/local`. Dadurch ist es nicht mehr nötig, 'sudo' zum Installieren
von Node zu verwenden oder die Installation von Paketen global mit npm vorzunehmen. 
    **Hinweis:** Eine Änderung der Eigentumsrechte für ein Verzeichnis ist nur auf einem lokalen Entwicklungssystem angemessen. Führen Sie diesen Schritt niemals auf einem Serversystem aus.

Verzichten Sie außerdem unbedingt auf die Anwendung
des zuvor genannten Befehls `chown` auf das Verzeichnis
`/usr/bin`; andernfalls kann es zu einer ernsthaften Fehlkonfiguration Ihres Systems kommen.

Wenn die Verwendung von `sudo` erforderlich ist,
benutzen Sie den folgenden Befehl:
```
sudo npm install -g --unsafe-perm install apiconnect
```
{:codeblock}

## Developer Toolkit kann unter Windows nicht installiert werden
{: #unable_tk_win_apic_troubleshoot}

Nach der Bereitstellung des {{site.data.keyword.apiconnect_short}}-Service schlägt der
Installationsversuch für Developer Toolkit fehl.

### Symptome
{: #ts_sym_noinstalltk_path_apic_troubleshoot}

Bei dem Versuch, Developer Toolkit unter Windows zu installieren, wird in einer Fehlernachricht darauf hingewiesen, dass der Pfad kürzer als 248 Zeichen sein muss (*path should be less than 248 characters*).

### Ursache
{: #ts_cause_noinstalltk_path_apic_troubleshoot}

Auf Windows gilt eine maximale Pfadlänge, die überschritten wird, wenn versucht wird, alle Abhängigkeiten in einem tief verschachtelten
Ordnerpfad zu installieren.

### Lösung
{: #ts_res_noinstalltk_path_apic_troubleshoot}

Dieses Problem kann mit einer der folgenden Maßnahmen behoben werden:

- Stellen Sie sicher, dass die richtige Version von 'Node.js' installiert wurde. Weitere Informationen finden Sie in [Developer Toolkit installieren](/docs/services/apiconnect?topic=apiconnect-creating_apis).

- Falls ein Programm aktualisiert werden musste, führen Sie die Installation erneut durch.

Falls dies nicht funktioniert, installieren Sie {{site.data.keyword.apiconnect_short}} auf einer höheren Verzeichnisebene als der wahrscheinlich verwendeten Verzeichnisebene
`C:/Programme/nodejs/bin/node_modules...`. Wenn die Installation in einem Basisverzeichnis (Verzeichnis der höchsten Ebene) erfolgt,
tritt dieser Fehler nicht auf.

## Developer Toolkit kann unter Mac OS X nicht installiert werden
{: #unable_tk_mac_apic_troubleshoot}

Nach der Bereitstellung des {{site.data.keyword.apiconnect_short}}-Service schlägt der
Installationsversuch für Developer Toolkit fehl.

### Symptome
{: #ts_sym_noinstalltk_mac_apic_troubleshoot}

Bei der Installation von Developer Toolkit werden die folgenden
Fehler angezeigt:
```
Agreeing to the Xcode/iOS license requires admin
privileges, please re-run as root via sudo
```

### Ursache
{: #ts_cause_noinstalltk_mac_apic_troubleshoot}

Sie haben Xcode vor kurzem installiert oder ein Upgrade für Xcode ausgeführt und der Lizenz noch nicht
zugestimmt.

### Lösung
{: #ts_res_noinstalltk_mac_apic_troubleshoot}

1. Geben Sie den folgenden Befehl ein, um Ihre Lizenz für Xcode zu überprüfen:
```
sudo xcode-select
```
{:codeblock}

2. Installieren Sie Developer Toolkit erneut.


## Developer Toolkit kann unter Ubuntu nicht installiert werden
{: #unable_tk_ubu_apic_troubleshoot}

Nach der Bereitstellung des {{site.data.keyword.apiconnect_short}}-Service schlägt der
Installationsversuch für Developer Toolkit fehl.

### Symptome
{: #ts_sym_noinstalltk_ubu_apic_troubleshoot}

Bei der Installation von Developer Toolkit werden die folgenden
Fehler angezeigt:
```
sqlite3@3.1.1 install /usr/local/lib/node_modules/strong-pm/node_modules/minkelite/node_modules/sqlite3
node-pre-gyp install --fallback-to-build
/usr/bin/env: node: No such file or directory
npm WARN This failure might be due to the use of legacy binary "node"
npm WARN For further explanations, please read /usr/share/doc/nodejs/README.Debian
npm ERR! weird error 127
npm ERR! not ok code 0
```

### Lösung
{: #ts_res_noinstalltk_ubu_apic_troubleshoot}

Geben Sie den folgenden Befehl ein, um das Problem zu
beheben:
```
$ update-alternatives --install /usr/bin/node node /usr/bin/nodejs 99
```

## Kein Debuggen der fehlgeschlagenen npm-Installation möglich
{: #unable_nmp_apic_troubleshoot}

Wenn Sie entsprechend den Schritten zum Installieren von Developer Toolkit vorgehen, schlägt die npm-Installation
fehl.

### Symptome
{: #ts_sym_npmfail_apic_troubleshoot}

Die npm-Installation schlägt ohne jegliche Angabe nützlicher Informationen für das Debuggen
fehl.

### Lösung
{: #ts_res_npmfail_apic_troubleshoot}

Wenn eine Installation fehlschlägt, schreibt npm eine Zeile in die Datei `npm-debug.log</filepath>`,
die angibt, wo sich der Fehler befindet. Verwenden Sie die Datei `debug.log`, um die Ursache
zu ermitteln.

## API Designer kann nicht geöffnet werden
{: #unable_apid_apic_troubleshoot}

Sie haben den Befehl `apic edit` eingegeben, aber API Designer wird nicht
geöffnet.

### Symptome
{: #ts_sym_noopenapid_apic_troubleshoot}

Es wird keine Instanz von API Designer geöffnet, nachdem der Befehl eingegeben wurde:
```
apic edit
```
und die folgende Nachricht angezeigt wird:
```
<time stamp>. 329Z ERROR apiConnect: listen EADDRINUSE <ip address> :9000
```

### Ursache
{: #ts_cause_noopenapid_apic_troubleshoot}

Sie haben bereits eine andere Instanz von API Designer über ein
anderes Befehlsfenster gestartet.

### Lösung
{: #ts_res_noopenapid_apic_troubleshoot}

Beheben Sie dieses Problem, indem Sie das andere Befehlsfenster schließen, wie in den
folgenden Schritten beschrieben:

1. Drücken Sie im anderen Befehlsfenster die Tastenkombination **Strg + C**.

2. Die folgende Nachricht wird angezeigt.
```
Terminate Batch job (Y/N)? (Batch-Job beenden (Y/N)?)
```

3. Geben Sie `Y` ein und drücken Sie die Eingabetaste.

## Die Abrechnungsinformationen für ein Produkt können nicht konfiguriert werden.
{: #cannot_bill_apic_troubleshoot}

Ein Teil der Abrechnungsinformationen ist nicht zum Konfigurieren oder Festschreiben für die Produktion verfügbar. 

### Symptome
{: #ts_sym_nobill_apic_troubleshoot}

  - Wenn Sie den Abschnitt für die Verwaltung Ihres Produkts anzeigen, wird die Registerkarte für die Abrechnung nicht angezeigt.
  - Wenn Sie versuchen, ein Produkt mit den angegebenen Abrechnungsinformationen zu veröffentlichen, tritt ein Fehler auf. 

### Ursache
{: #ts_cause_nobill_apic_troubleshoot}

Sie müssen über das richtige {{site.data.keyword.apiconnect_short}}-Konto und die korrekten Berechtigungen verfügen, um die Abrechnungsinformationen aktivieren zu können.

## Ein Abrechnungsplan für ein Produkt kann nicht abonniert werden.
{: #cannot_bill_plan_apic_troubleshoot}

Aufgrund der Verwendung von Stripe ist die Anzahl der Abonnements auf ein Maximum von 25 beschränkt. Stellen Sie sicher, dass diese Obergrenze nicht
überschritten wird. Wenn dies der Fall ist, können Sie dieses Abonnement nur hinzufügen, wenn Sie ein anderes entfernen.

### Symptome
{: #ts_sym_nosubscribe_apic_troubleshoot}

Es wird ein Fehler angezeigt, wenn Sie versuchen, einen Plan zum Abrechnung zu abonnieren, obwohl weitere Pläne konfiguriert sind.

### Ursache
{: #ts_cause_nosubscribe_apic_troubleshoot}

Für den Stripe-Service zur Kreditkartenverarbeitung ist ein Maximum von 25 Abonnements pro Konto zulässig.

### Lösung
{: #ts_res_nosubscribe_apic_troubleshoot}

Stellen Sie sicher, dass Sie über ein Konto auf Unternehmensebene für den {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.apiconnect_short}}-Service verfügen und dass weniger als 25 Instanzen vorhanden sind. Entfernen Sie einen Service, wenn die maximale Anzahl an Services vorhanden ist.

## Hilfe und Unterstützung für API Connect abrufen
{: #get_help_apic_troubleshoot}

Falls Probleme oder Fragen bei der Verwendung von {{site.data.keyword.apiconnect_short}} auftreten, können Sie Hilfe erhalten, indem Sie im Forum nach entsprechenden Informationen suchen oder Fragen stellen. Sie können auch ein Support-Ticket öffnen.

Wenn Sie in den Foren eine Frage stellen, versehen Sie Ihre Frage mit einem Tag, sodass sie von den {{site.data.keyword.Bluemix_notm}}-Entwicklungsteams gesehen wird. 

- Bei technischen Fragen zur Entwicklung oder Bereitstellung einer App mit {{site.data.keyword.apiconnect_short}} veröffentlichen Sie Ihre Frage auf Stack Overflow und verwenden Sie die Tags "ibm-cloud" und "api connect".

- Bei Fragen zum Service und zu den Einführungsanweisungen nutzen Sie das Forum IBM developerWorks dW Answers. Verwenden Sie die Tags "ibm cloud" und "api connect".
Weitere Einzelheiten zur Verwendung der Foren finden Sie im Abschnitt zum Anfordern von Unterstützung. 

Information dazu, wie Sie ein IBM Support-Ticket öffnen, sowie zu Supportebenen und Ticket-Prioritäten, finden Sie im Abschnitt 'Support kontaktieren'.



