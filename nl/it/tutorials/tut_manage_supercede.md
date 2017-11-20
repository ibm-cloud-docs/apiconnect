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

# Sostituzione dei prodotto API
**Durata**: 15 minuti  
**Livello di competenza**: Principiante  

## Prerequisiti

1. [Configura la tua istanza {{site.data.keyword.apiconnect_full}}](tut_prereq_set_up_apic_instance.html).

2. Completa la [Esercitazione sulla sostituzione di un prodotto API](tut_manage_replace.html). 

---
## Obiettivo
In questa esercitazione, rimpiazzerai un prodotto API esistente con uno nuovo. 

---
## Sostituzione di un prodotto API
1. Accedi a {{site.data.keyword.Bluemix_short}}: [https://console.ng.bluemix.net/login ![Icona link esterno](../../../icons/launch-glyph.svg "Icona link esterno")](https://console.ng.bluemix.net/login){:new_window}.

2. Nel dashboard {{site.data.keyword.Bluemix_short}}, avvia il servizio {{site.data.keyword.apiconnect_short}}.
![](images/Bluemix.png)

3. In API Manager, se non hai precedentemente bloccato il riquadro di navigazione della IU fai clic sull'icona **Navigate to** ![](images/navigate-to.png). Viene aperto il pannello di navigazione della IU API Manager. Per bloccare il pannello di navigazione della IU, fai clic sull'icona **Pin menu** ![](images/pinned.png).

4. Fai clic su **Sandbox** per aprire il catalogo Sandbox. **Nota**: la tua schermata potrebbe visualizzare i tile invece di un elenco di cataloghi.
![](images/del-sandbox-list.png)

4. Fai clic su **Drafts** > **APIs**.

5. Nel pannello delle API, fai clic su **Weather Provider API** per aprire l'API proxy REST.  
![](images/rep-api-list.png)

6. Modifica **Version** con 3.0.0. 

7. Fare clic sull'icona disco per salvare le modifiche all'API.  
![](images/sup-change-version.png)

8. Fai clic su **All APIs**.  
![](images/rep-all-apis.png)

9. Fai clic su **Products**.  
![](images/sup-prods.png)

10.	Seleziona **Weather Provider API Product 2.0.0**.  
![](images/sup-draft-prod-list.png)

11.	Modifica **Version** con 3.0.0. Fai clic sull'icona disco per salvare le modifiche. Fai clic sull'icona **Stage**.  
![](images/sup-change-prod-vers-3.png)

12.	Fai clic su **>>** per aprire il pannello di navigazione e seleziona **Dashboard**.  
![](images/rep-dashboard.png)

13.	Fai clic su **Sandbox**.

14.	Fai clic su **Community**.  
![](images/sup-sand-dash.png)

15.	Fai clic su **Subscriptions**.  
![](images/sup-comm-orgs.png)

16.	Prendi nota delle sottoscrizioni all'applicazione a Weather Provider API Product 2.0.0. Fai clic su **Products**.
![](images/sup-scriptions-200.png)  

17.	Fai clic sulle ellissi verticali nella riga **Weather Provider API Product 3.0.0 Staged**.  
![](images/sup-stage-prod-3.png)

18.	Seleziona **Supersede an existing product**.  
![](images/sup-super-prod.png)

19.	Seleziona **Weather Provider API Product 2.0.0** nell'elenco dei prodotti presentato. Fai clic su **Avanti**.  
![](images/sup-super-dialog-1.png)

20.	Seleziona **Default plan**. Fai clic su **Supercede**.  
![](images/sup-super-dialog-2.png)
    Come risultato di questa sostituzione, il prodotto API Weather Provider 2.0.0 diventa obsoleto e viene pubblicato il prodotto API Weather Provider 3.0.0.  
![](images/sup-dash-prods-3.png) 
 
21.	Fai clic su **Community >> Subscriptions**.  
![](images/sup-scriptions-200.png)
 
22.	Fai clic sulle ellissi verticali nella riga **Weather Provider API Product 2.0.0**. Seleziona **Manage**.  
![](images/sup-dots-manage.png) 

23.	Seleziona **Default plan** nel prodotto API Weather Provider 3.0.0 . Fai clic su **Migrate**.  
![](images/sup-migrate-dialog.png)
    Come risultato di questa migrazione, il prodotto API Weather Provider 2.0.0 viene migrato al prodotto API Weather Provider 3.0.0.  
![](images/sup-migrated.png) 
 

 
## Cosa hai fatto in questa esercitazione
In questa esercitazione, hai completato le seguenti attività:

1. Aggiornato un prodotto API.
2. Sostituito un prodotto API esistente con uno aggiornato.
3. Migrato la sottoscrizione di un prodotto API esistente al prodotto API aggiornato.

---












