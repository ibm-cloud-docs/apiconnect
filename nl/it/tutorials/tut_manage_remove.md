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

# Archiviazione ed eliminazione dei prodotti API
**Durata**: 15 minuti  
**Livello di competenza**: Principiante 

## Prerequisiti

1. [Configura la tua istanza {{site.data.keyword.apiconnect_full}}](tut_prereq_set_up_apic_instance.html).

2. Completa la [Esercitazione sulla sostituzione di un prodotto API](tut_manage_supercede.html).

---
## Obiettivo
In questa esercitazione, eliminerai, archivierai e ritirerai un'API.

---
## Eliminazione di un prodotto API
1. Accedi a {{site.data.keyword.Bluemix_short}}: [https://console.ng.bluemix.net/login ![Icona link esterno](../../../icons/launch-glyph.svg "Icona link esterno")](https://console.ng.bluemix.net/login){:new_window}.

2. Nel dashboard {{site.data.keyword.Bluemix_short}}, avvia il servizio {{site.data.keyword.apiconnect_short}}.
![](images/Bluemix.png)

3. In API Manager, se non hai precedentemente bloccato il riquadro di navigazione della IU fai clic sull'icona **Navigate to** ![](images/navigate-to.png). Viene aperto il pannello di navigazione della IU API Manager. Per bloccare il pannello di navigazione della IU, fai clic sull'icona **Pin menu** ![](images/pinned.png).

4. Fai clic su **Sandbox** per aprire il catalogo Sandbox. **Nota**: potresti dover ritornare al dashboard per visualizzare i cataloghi disponibili. Inoltre, la tua pagina del dashboard potrebbe mostrare i cataloghi come tile invece che come un elenco.
![](images/del-sandbox-list.png)

5. Fai clic sulle ellissi verticali nella riga **Weather Provider API 1.0.0**.  
![](images/del-prod-list1.png)

6. Seleziona **Delete from catalog**.  
![](images/del-del-from-cat.png)

7. Fai clic su **OK**.  
![](images/del-del-dialog.png)
    Il prodotto scompare dall'elenco dei prodotti nel catalogo. A questo punto non è possibile ripristinarlo.


## Archiviazione di un prodotto API
1. Fai clic sulle ellissi verticali nella riga **Weather Provider API 2.0.0**.  
![](images/del-prod-list2.png)

2. Seleziona **Retire**.  
![](images/del-select-retire.png)

3. Fai clic su **OK**.  
![](images/del-retire-dialog.png)

4. Fai clic sulle ellissi verticali nella riga **Weather Provider API 2.0.0**.  
![](images/del-prod-list3.png)

5. Seleziona **Archive**.  
![](images/del-select-archive.png)

6. Fai clic su **OK**.  
![](images/del-archive-dialog.png)
    Il prodotto scompare dall'elenco dei prodotti nel catalogo. Non può essere ripristinato.

7. Fai clic sull'icona di visualizzazione dell'elenco.  
![](images/del-prod-list4.png)

8. Controlla **Archived**.  
![](images/del-view-archived.png)

9. Fai clic sulle ellissi verticali nella riga **Weather Provider API 2.0.0**.  
![](images/del-prod-list5.png)

10. Seleziona **Unarchive**.  
![](images/del-unarchive.png)
    Lo stato del prodotto viene modificato con Retired.
    ![](images/del-prod-list6.png)

 
 
## Cosa hai fatto in questa esercitazione
In questa esercitazione, hai completato le seguenti attività:

1. Eliminato un prodotto API
2. Ritirato un prodotto API
3. Archiviato un prodotto API
4. Annullata l'archiviazione di un prodotto API

---












