---
copyright:
  years: 2017
lastupdated: "2017-09-12"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Personalizzazione del portale sviluppatori e selezione di un tema 
**Durata**: 30 minuti  
**Livello di competenza**: Principiante  


## Obiettivo
Questa esercitazione ti aiuterà a personalizzare velocemente il tuo portale sviluppatori {{site.data.keyword.apiconnect_short}} e a selezionare un tema che soddisfi i tuoi bisogni.

---

## Prerequisiti

Prima di iniziare con questa esercitazione, devi aver completato l'esercitazione [Impostazione e configurazione del portale sviluppatori](tut_config_dev_portal.html) e aver eseguito l'accesso come amministratore del portale.

---

## Personalizza il tuo portale sviluppatori
Dopo aver creato il tuo portale sviluppatori, puoi personalizzarne l'aspetto.

1. Iniziamo modificando il banner di benvenuto. Nel menu in alto seleziona **Content** e **Blocks**.  
  ![Menu contenuti](images/31-content.png)

2. Seleziona **Edit** nel blocco **Welcome Banner**.  
  ![Modifica banner di benvenuto](images/32-edit.png)

3. Nell'intestazione del contenuto, puoi modificare l'immagine e il testo del contenuto del banner di benvenuto immettendo del testo nell'editor del contenuto o selezionando l'icona Edit HTML Source per modificare o incollare direttamente del testo HTML che definisce le specifiche di testo e immagine.  
  ![Editor contenuto](images/33-content.png) 

4. Aggiungiamo inoltre un'immagine alla nostra schermata home. Scorri fino all'intestazione dell'immagine. Trova un'immagine per il tuo background e salvala nel formato file appropriato (png, gif, jpg, jpeg). Se non hai un'immagine, puoi utilizzare [questa](images/Cloudy_Day.png). Fai clic su **Choose File** e scegli l'immagine di background. Dopo aver selezionato l'immagine, fai clic su **Upload**.  
  ![Carica immagine](images/34-image.png)

5. L'immagine sarà visualizzata dopo essere stata caricata. Se desideri rimuoverla, fai clic su **Remove**.  
  ![Carica immagine](images/35-uploaded-image.png)
 
6. In fondo alla pagina, fai clic su **Save** per salvare le tue modifiche.  
  
---

## Personalizza il tema del tuo portale sviluppatori
Il portale sviluppatori ti consente di modificare il tema cambiandone l'aspetto.

1. Per modificare il tema, seleziona **Appearance** dal menu in alto, poi **Settings** e **IBM API Connect Theme**. Questo è il tema predefinito quando hai creato il tuo portale sviluppatori.
  ![Tema IBM API Connect](images/41-APIC-theme.png) 


2. La scheda **Standard Layout** ti permette di modificare i layout dei dispositivi con schermate molto grandi, come i desktop. La scheda **Tablet Layout** ti permette di modificare i layout dei dispositivi tablet. La scheda **Smalltouch Layout** ti permette di modificare i layout utilizzati nei dispositivi come gli smartphone. Dopo aver ispezionato queste schede, seleziona **Panels & Gpanels**.
  ![Layout](images/42-layout.png)

3. In aggiunta alla modifica dei precedenti layout della barra laterale, il tema predefinito supporta l'utilizzo dei pannelli Responsive o Gpanels se installi il modulo Panels. Per controllare il layout dei pannelli nei dispositivi standard, tablet e smalltouch, espandi le sezioni e aggiorna le impostazioni.
  ![Panels](images/43-panels.png) 

4. Esistono altre impostazioni che puoi modificare, ma saltiamole e seleziona **Extensions**. Questa scheda ti permette di eseguire ulteriori impostazioni che puoi utilizzare per configurare lo stile del tuo portale sviluppatori.  
  ![Estensioni](images/44-extensions.png)

5. Le impostazioni delle estensioni abilitate nella scheda **Extensions** possono essere modificate nella sezione **Extensions** sotto le impostazioni principali.     
  ![Impostazioni estensioni](images/45-extension-settings.png)

6. Dopo aver completato le modifiche delle impostazioni, seleziona **Save configuration** in fondo alla pagina.

---

## Seleziona un tema diverso per il tuo portale sviluppatori
Il portale sviluppatori viene fornito con temi aggiuntivi che puoi scegliere e personalizzare per modificarne l'aspetto.

1. Per abilitare un tema differente, seleziona la scheda **List** all'inizio dell'impostazione dell'aspetto.
  ![Elenchi](images/51-list.png) 

2. All'inizio della scheda **Lists**, vengono visualizzati i temi abilitati.
  ![Temi abilitati](images/52-enabled-themes.png)

3. Il seguente elenco di temi abilitati è una raccolta di temi disabilitati. Puoi abilitare un tema selezionando **Enable**   
  ![Abilita tema](images/53-enable-theme.png) 

4. Dopo aver abilitato il tema, verrà visualizzato all'inizio della scheda **List** in **Enabled Themes**. Puoi personalizzarlo selezionando **Settings**.  
  ![Temi abilitati](images/54-theme-settings.png)

5. Dopo aver terminato di modificare le impostazioni, puoi impostare il tema come predefinito selezionando **Set Default**.     
  ![Imposta tema predefinito](images/55-set-default.png)

---

## Installa un nuovo tema per il tuo portale sviluppatori
Se modificando un tema non soddisfi i tuoi bisogni, il portale sviluppatori ti consente inoltre di installare un tema per modificarne l'aspetto.

1. Puoi utilizzare i moduli o i temi scaricati da [drupal.org ![Icona link esterno](../../../icons/launch-glyph.svg "Icona link esterno")](http://drupal.org){:new_window} per personalizzare il tuo portale sviluppatori o puoi crearne di tuoi.

2. Per installare un tema nel portale sviluppatori, seleziona **Appearance** dal menu in alto e **Install new theme**.  
  ![Installa nuovo tema](images/62-install-new.png)

3. Puoi installare i temi direttamente da [drupal.org ![Icona link esterno](../../../icons/launch-glyph.svg "Icona link esterno")](http://drupal.org){:new_window} utilizzando un URL o puoi caricare un tema che hai scaricato o creato facendo clic su **Choose File** e **Install**.  
  ![Installa](images/63-install.png) 

4. Quando il caricamento è completo, devi abilitare il tema. Seleziona **Enable newly added themes**.  
  ![Abilita il tema appena aggiunto](images/64-upload.png)

5. Scorri l'elenco e trova il tema appena installato. Seleziona **Enable and set default**.  
  ![Abilita tema e impostalo come predefinito](images/65-enable.png)

6. In fondo alla pagina, fai clic su **Save** per salvare le tue modifiche.  

---

## Riepilogo  
Congratulazioni, hai completato questa esercitazione. In questa esercitazione hai imparato come:

* Personalizzare la pagina di benvenuto del tuo portale sviluppatori
* Personalizzare il tema utilizzato dal tuo portale sviluppatori  
* Selezionare un tema differente da utilizzare con il tuo portale sviluppatori
* Installare un nuovo tema nel tuo portale sviluppatori

---

## Passo successivo

Impara [come un utente naviga nel portale sviluppatori](tut_discover_apis.html) o [come ottenere informazioni approfondite da analisi di base](tut_insights_analytics.html).

Create >Manage> Secure > ** Socialize ** > Analyze  

