---
copyright:
  years: 2017
lastupdated: "2017-12-15"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Risoluzione dei problemi
{: #troubleshoot}

Qui troverai le risposte alle domande per la risoluzione dei problemi comuni relativi all'utilizzo di {{site.data.keyword.apiconnect_long}} su {{site.data.keyword.Bluemix_notm}}.
{:shortdesc}

## Nome utente e password obbligatori quando aggiungi il servizio API Connect {{site.data.keyword.Bluemix_notm}} 

Dopo aver aggiunto il servizio al tuo dashboard {{site.data.keyword.Bluemix_notm}}, ti viene richiesto di inserire un nome utente e una password quando tenti di aprirlo. 

### Sintomi
{: #ts_sym_usernamepw}

Invece di accedere al servizio {{site.data.keyword.Bluemix_notm}} direttamente quando apri un nuovo
{{site.data.keyword.apiconnect_short}}, ti viene richiesto di accedere a API Manager.

### Causa
{: #ts_cause_usernamepw}

Il tuo browser è impostato per bloccare i cookie o il livello di configurazione è a un livello più limitato rispetto a quello richiesto da {{site.data.keyword.apiconnect_notm}}.

### Soluzione
{: #ts_res_usernamepw}

Abilita o aumenta il livello di cookie nelle tue impostazioni del browser finché non viene aperto il servizio {{site.data.keyword.Bluemix_notm}}.

## Impossibile installare il toolkit sviluppatori

Dopo che hai eseguito il provisioning del servizio  API Connect, provi a installare il toolkit sviluppatori e
l'installazione non riesce.

### Sintomi
{: #ts_sym_noinstalltk}

Durante l'installazione del toolkit sviluppatori
vengono visualizzati i seguenti errori:
```
npm ERR! Error: EACCES, mkdir '/usr/local/lib/node_modules/apiconnect'
...
npm ERR! Please try running this command again as root/Administrator
...
```

### Causa
{: #ts_cause_noinstalltk}

Non disponi delle autorizzazioni adeguate per creare file o directory.

### Soluzione
{: #ts_res_noinstalltk}

Modifica le autorizzazioni per le directory specificate oppure esegui il comando utilizzando
`sudo`. Su un sistema di sviluppo locale, si consiglia di correggere le autorizzazioni delle directory nel seguente
modo:
```
sudo chown -R $USER /usr/local
```
{:codeblock}

Questo comando cambia il tuo account utente
nel proprietario della directory `/usr/local`. Non dovrai, quindi, utilizzare sudo per
installare Node o installare i pacchetti a livello globale con npm. 
    **Nota:** la modifica dell'appartenenza della directory è appropriata solo su un sistema di sviluppo locale. Non effettuare mai questa azione su un sistema di server.

Inoltre, non utilizzare il comando
`chown` precedente sulla directory `/usr/bin`,
altrimenti potresti configurare erroneamente il tuo sistema.

Se devi utilizzare `sudo`, usa
il seguente comando:
```
sudo npm install -g --unsafe-perm install apiconnect
```
{:codeblock}

## Impossibile installare il toolkit sviluppatori su Windows

Dopo che hai eseguito il provisioning del servizio {{site.data.keyword.apiconnect_short}},
provi a installare il toolkit sviluppatori e l'installazione non riesce.

### Sintomi
{: #ts_sym_noinstalltk_path}

Stai provando a installare il toolkit sviluppatori su Windows e ricevi un messaggio di errore che indica che il tuo *percorso deve avere una lunghezza inferiore ai 248 caratteri*.

### Causa
{: #ts_cause_noinstalltk_path}

Sui sistemi Windows, esiste una lunghezza percorso massima che viene superata quando provi a installare tutte le dipendenze in una cartella di livello profondo.

### Soluzione
{: #ts_res_noinstalltk_path}

Puoi risolvere questo problema in uno dei seguenti modi:

- Assicurati di aver installato la versione corretta di Node.js. Per ulteriori informazioni, consulta [Installazione del toolkit sviluppatori](creating_apis.html).

- Se hai dovuto eseguire l'upgrade di un programma, prova nuovamente l'installazione.

Se non funziona, installa {{site.data.keyword.apiconnect_short}} a un livello superiore
alla probabile cartella `C:/program files/nodejs/bin/node_modules...`. Se esegui
l'installazione in una directory di livello superiore, non vedrai questo errore.

## Impossibile installare il toolkit sviluppatori su Mac OS X

Dopo che hai eseguito il provisioning del servizio {{site.data.keyword.apiconnect_short}},
provi a installare il toolkit sviluppatori e l'installazione non riesce.

### Sintomi
{: #ts_sym_noinstalltk_mac}

Durante l'installazione del toolkit sviluppatori
vengono visualizzati i seguenti errori:
```
Agreeing to the Xcode/iOS license requires admin 
privileges, please re-run as root via sudo
```

### Causa
{: #ts_cause_noinstalltk_mac}

Hai recentemente aggiornato o installato Xcode e non hai accettato ancora i
termini della licenza.

### Soluzione
{: #ts_res_noinstalltk_mac}

1. Immetti il seguente comando per convalidare la tua licenza Xcode:
```
sudo xcode-select
```
{:codeblock}

2. Reinstalla il toolkit sviluppatori.


## Impossibile installare il toolkit sviluppatori su Ubuntu

Dopo che hai eseguito il provisioning del servizio {{site.data.keyword.apiconnect_short}},
provi a installare il toolkit sviluppatori e l'installazione non riesce.

### Sintomi
{: #ts_sym_noinstalltk_ubu}

Durante l'installazione del toolkit sviluppatori
vengono visualizzati i seguenti errori:
```
sqlite3@3.1.1 install /usr/local/lib/node_modules/strong-pm/node_modules/minkelite/node_modules/sqlite3 
node-pre-gyp install --fallback-to-build 
/usr/bin/env: node: No such file or directory 
npm WARN This failure might be due to the use of legacy binary "node" 
npm WARN For further explanations, please read /usr/share/doc/nodejs/README.Debian 
npm ERR! weird error 127 
npm ERR! not ok code 0
```

### Soluzione
{: #ts_res_noinstalltk_ubu}

Immetti il seguente comando per risolvere il
problema:
```
$ update-alternatives --install /usr/bin/node node /usr/bin/nodejs 99
```

## Impossibile eseguire il debug dell'errore di installazione npm

Quando segui la procedura per installare il toolkit sviluppatori, l'installazione npm
non riesce.

### Sintomi
{: #ts_sym_npmfail}

L'installazione npm non riesce senza fornire informazioni utili per
il debug.

### Soluzione
{: #ts_res_npmfail}

Quando un'installazione non riesce, npm scrive una riga nel file `npm-debug.log</filepath>`
per indicare dove si verifica l'errore. Utilizza il file `npm-debug.log` per determinare la causa.

## Impossibile aprire l'API Designer

Immetti il comando `apic edit` e l'API Designer non si apre.

### Sintomi
{: #ts_sym_noopenapid}

Non riesci ad aprire un'istanza dell'API Designer dopo
che hai immesso il comando:
```
apic edit
```
e viene visualizzato il seguente messaggio:
```
<data ora>. 329Z ERROR apiConnect: listen EADDRINUSE <indirizzo ip>:9000
```

### Causa
{: #ts_cause_noopenapid}

Già hai avviato un'istanza dell'API Designer da un'altra finestra di comandi.

### Soluzione
{: #ts_res_noopenapid}

Per correggere questo problema, devi chiudere l'altra finestra comandi come descritto nella seguente procedura:

1. Nell'altra finestra comandi, premi **Ctrl + C**.

2. Viene visualizzato il seguente messaggio.
```
Terminate Batch job (Y/N)?
```

3. Immetti `Y` e premi Invio.

## Impossibile configurare le informazioni sulla fatturazione di un prodotto

Alcune delle informazioni di fatturazione non sono disponibili per configurare o eseguire il commit alla produzione. 

### Sintomi
{: #ts_sym_nobill}

  - Quando visualizzi la sezione di gestione del tuo prodotto, non viene visualizzata la scheda di fatturazione.
  - Quando tenti di pubblicare un prodotto con le informazioni di fatturazione specificate, ricevi un errore. 

### Causa
{: #ts_cause_nobill}

Devi disporre dell'account e delle autorizzazioni corrette di {{site.data.keyword.apiconnect_short}} per abilitare le informazioni di fatturazione.

## Impossibile sottoscriversi a un piano d fatturazione di un prodotto.

Stripe limita ogni cliente a un massimo di 25 sottoscrizioni. Assicurati di non aver superato questo
limite. Se è così, puoi aggiungere questa sottoscrizione solo se ne rimuovi un'altra.

### Sintomi
{: #ts_sym_nosubscribe}

Visualizzi un errore quando tenti di sottoscrivere un piano con fatturazione, anche se hai altri piani configurati.

### Causa
{: #ts_cause_nosubscribe}

Il servizio di elaborazione della carta di credito Stripe consente un massimo di 25 sottoscrizioni per account.

### Soluzione
{: #ts_res_nosubscribe}

Assicurati di disporre di un account al livello aziendale per il tuo servizio
{{site.data.keyword.Bluemix_notm}} {{site.data.keyword.apiconnect_short}} e che ci siano meno di 25 istanze. Rimuovi un servizio, se hai raggiunto il numero massimo di servizi.

## Come ottenere aiuto e supporto per API Connect

Se hai dei problemi o delle domande quando utilizzi {{site.data.keyword.apiconnect_short}},
puoi ottenere aiuto ricercando le informazioni o facendo delle domande in un forum. Puoi inoltre aprire un ticket di supporto.

Quando utilizzi i forum per fare una domanda, contrassegna con una tag la tua domanda in modo che sia visualizzabile dai team di sviluppo {{site.data.keyword.Bluemix_notm}}. 

- Se hai domande tecniche sullo sviluppo o la distribuzione di un'applicazione con {{site.data.keyword.apiconnect_short}},
inserisci la tua domanda in Stack Overflow e contrassegnala con le tag "ibm-cloud" e "api connect."

- Per domande sul servizio e sulle istruzioni per l'utilizzo iniziale, utilizza il forum
IBM DeveloperWorks dW Answers. Includi le tag "ibm cloud" e "api connect".
Consulta Come ottenere supporto per ulteriori dettagli sull'utilizzo dei forum. 

Per informazioni su come aprire un ticket di supporto IBM o sui livelli di supporto e sulla gravità dei ticket, consulta
Come contattare il supporto.



