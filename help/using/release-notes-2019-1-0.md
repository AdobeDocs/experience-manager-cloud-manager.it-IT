---
title: Note sulla versione 2019.1.0
seo-title: Note sulla versione di AEM Cloud Manager 2019.1.0
description: Segui questa pagina per ottenere informazioni sulla versione 2019.1.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2019.1.0 di AEM Cloud Manager.
uuid: 3af5808f-828f-4846-bee4-1e62194b48ad
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 85a1dcf3-2eef-4ba8-b4d1-09e4a88c7bd0
feature: Informazioni sulla versione
translation-type: tm+mt
source-git-commit: c5d32d49782c899d013fcc60b9c4d2b67e9350ae
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 4%

---


# Note sulla versione 2019.1.0 {#release-notes-for}

La versione [!UICONTROL Cloud Manager] 2018.9.0 aggiunge il supporto per testare i programmi AEM Assets e altri tipi di pipeline che eseguono i passaggi di build e qualità del codice, distribuendo facoltativamente in un ambiente non di produzione.

## Data di rilascio {#release-date}

La data di rilascio di [!UICONTROL Cloud Manager] versione 2019.1.0 è il 17 gennaio 2019.

## Novità {#whats-new}

* È stato aggiunto il supporto per il test delle prestazioni di AEM Assets. Per ulteriori informazioni, consulta Configurare la [pipeline CI/CD](configuring-pipeline.md).
* È stato aggiunto il supporto per le pipeline che eseguono solo passaggi di generazione e qualità del codice e per le pipeline che vengono distribuite in ambienti non di produzione. Per ulteriori informazioni, consulta la sezione **Pipeline non di produzione e solo qualità del codice** in [Configurare la pipeline CI/CD](configuring-pipeline.md) .
* È stato aggiunto il supporto per le variabili di ambiente personalizzate nell’ambiente di creazione.
* Per i clienti con più ambienti di stage o produzione, nella pagina [Configura la pipeline CI/CD](configuring-pipeline.md) è disponibile una selezione di quale ambiente verrà distribuito come parte della pipeline di produzione.
* httxt2dbm è stato aggiunto al contenitore di build.
* Tutte le voci del menu della guida aprono una nuova scheda.

## Correzioni di bug {#bug-fixes}

* Durante la modifica di un programma, era possibile deselezionare tutti i set di pagine.
* Il passaggio di approvazione non era intitolato correttamente.
* In alcune situazioni, il logo del programma era mascherato in modo errato.
* Se è stato generato solo il pacchetto di configurazione del dispatcher, il passaggio di distribuzione non riesce.
* Gli ambienti che contenevano istanze di standby a freddo non venivano gestiti correttamente.
* Sul commutatore del programma sono stati visualizzati alcuni programmi terminati.
* Se un nuovo ramo è stato aggiunto all’archivio Git durante la modifica della pipeline, potrebbe non essere stato selezionato immediatamente.
* In alcune schermate, l&#39;icona Developer Connection del menu Guida non era visibile.
* Il tasto di tabulazione non è stato gestito correttamente nella finestra di dialogo di configurazione dello scaricamento del dispatcher.

## Problemi noti {#known-issues}

* Quando si apre un programma con Sites impostato ma non Assets, KPI, tutti gli utenti visualizzano una chiamata alla scheda azione con un pulsante **Programma di installazione** . Tuttavia, solo gli utenti con il ruolo Proprietario business possono fare clic sul pulsante **Programma di installazione**.