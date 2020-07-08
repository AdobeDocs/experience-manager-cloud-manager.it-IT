---
title: Note sulla versione 2019.1.0
seo-title: Note sulla versione di AEM Cloud Manager per la versione 2019.1.0
description: Segui questa pagina per ottenere informazioni sulla versione 2019.1.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2019.1.0 di AEM Cloud Manager.
uuid: 3af5808f-828f-4846-bee4-1e62194b48ad
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 85a1dcf3-2eef-4ba8-b4d1-09e4a88c7bd0
translation-type: tm+mt
source-git-commit: cdf2c82192c2e9c375316ae6e28646594ba2a462
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 4%

---


# Note sulla versione 2019.1.0 {#release-notes-for}

La release [!UICONTROL Cloud Manager] 2018.9.0 aggiunge programmi di AEM Assets di test di supporto e altri tipi di pipeline che eseguono i passaggi di creazione e qualità del codice, distribuendo facoltativamente in un ambiente non di produzione.

## Data di rilascio {#release-date}

La data di rilascio per la [!UICONTROL Cloud Manager] versione 2019.1.0 è il 17 gennaio 2019.

## Novità {#whats-new}

* È stato aggiunto il supporto per il test delle prestazioni dei AEM Assets. Per ulteriori informazioni, consulta Configurare la [pipeline](configuring-pipeline.md)CI/CD.
* È stato aggiunto il supporto per le condutture che eseguono solo passaggi per la creazione e la qualità del codice e per le tubazioni distribuite in ambienti non di produzione. Per ulteriori informazioni, consultare la sezione **Non produzione e solo tubazioni** di qualità del codice in [Configurare la tubazione](configuring-pipeline.md) CI/CD.
* È stato aggiunto il supporto per le variabili di ambiente personalizzate nell&#39;ambiente di generazione. Per ulteriori informazioni, consultate [Creazione di un progetto](/help/using/create-an-application-project.md) applicazione AEM.
* Per i clienti con più fasi o ambienti di produzione, nella pagina [Configura la pipeline](configuring-pipeline.md) CI/CD è disponibile la selezione dell’ambiente a cui verrà distribuito come parte della pipeline di produzione.
* httxt2dbm è stato aggiunto al contenitore di generazione.
* Tutte le voci del menu della Guida aprono una nuova scheda.

## Correzioni di bug {#bug-fixes}

* Durante la modifica di un programma, era possibile deselezionare tutti i set di pagine.
* Il passaggio di approvazione non aveva il titolo corretto.
* In alcuni casi, il logo del programma era erroneamente formattato.
* Se è stato creato solo il pacchetto di configurazione del dispatcher, il passaggio di distribuzione non riesce.
* Gli ambienti che contenevano istanze di standby a freddo non venivano gestiti correttamente.
* Alcuni programmi terminati venivano visualizzati sullo switcher di programma.
* Se un nuovo ramo è stato aggiunto al repository git durante la modifica della pipeline, potrebbe non essere stato selezionato immediatamente.
* In alcune schermate, l&#39;icona Developer Connection nel menu Guida non era visibile.
* Il tasto di tabulazione non è stato gestito correttamente nella finestra di dialogo di configurazione dello scaricamento del dispatcher.

## Problemi noti {#known-issues}

* Quando si apre un programma con Siti, ma non Risorse, KPI impostati, tutti gli utenti visualizzano una chiamata alla scheda azione con un pulsante **Programma** di installazione. Tuttavia, solo gli utenti con il ruolo Proprietario business possono fare clic sul pulsante **Programma** di installazione.