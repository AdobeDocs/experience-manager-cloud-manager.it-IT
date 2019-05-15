---
title: Note sulla versione 2019.1.0
seo-title: Note sulla versione di AEM Cloud Manager per 2019.1.0
description: Segui questa pagina per ottenere informazioni sulla versione 2019.1.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2019.1.0 di AEM Cloud Manager.
uuid: 3 af 5808 f -828 f -4846-bee 4-1 e 62194 b 48 ad
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: note sulla versione
discoiquuid: 85 a 1 dcf 3-2 eef -4 ba 8-b 4 d 1-09 e 4 a 88 c 7 bd 0
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Note sulla versione 2019.1.0 {#release-notes-for}

La [!UICONTROL Cloud Manager] versione 2018.9.0 aggiunge il supporto per il test dei programmi di Risorse AEM e per i tipi di pipeline aggiuntivi che eseguono i passaggi di creazione e qualità del codice, distribuendo facoltativamente in un ambiente non di produzione.

## Data di rilascio {#release-date}

La Data di rilascio per [!UICONTROL Cloud Manager] la versione 2019.1.0 è il 17 gennaio 2019.

## Novità {#whats-new}

* È stato aggiunto il supporto per il test delle prestazioni di AEM Assets. Per ulteriori informazioni, consultate Configurare i [pipeline](configuring-pipeline.md)CI/CD.
* È stato aggiunto il supporto per i pipeline che eseguono solo passaggi di qualità e qualità del codice e che distribuiscono in ambienti non di produzione. Per **ulteriori informazioni, consultate la sezione Pipeline** di solo produzione e qualità codice in [Configura la pipeline](configuring-pipeline.md) CI/CD.
* Aggiunto supporto per variabili d&#39;ambiente personalizzate nell&#39;ambiente di creazione. Per ulteriori informazioni, consultate [Creare un progetto](create-an-application-project.md) applicazione AEM.
* Per i clienti con più ambienti di fase o produzione, la selezione dell&#39;ambiente in cui verrà distribuito l&#39;ambiente come parte del pipeline di produzione è disponibile in [Configura la pagina Pipeline](configuring-pipeline.md) CI/CD.
* È stato aggiunto il dbm httxt 2 per creare il contenitore.
* Tutti gli elementi del menu della guida aprono una nuova scheda.

## Correzioni di bug {#bug-fixes}

* Durante la modifica di un programma, era possibile deselezionare tutti i set di pagine.
* Il passaggio di approvazione non è stato titolato correttamente.
* In alcune situazioni, il logo del programma veniva mascherato in modo errato.
* Se è stato creato solo il pacchetto di configurazione del dispatcher, il passaggio di distribuzione non riesce.
* Gli ambienti che contenevano istanze di standby fredde non venivano gestiti correttamente.
* Alcuni programmi terminati sono stati visualizzati nel commutatore del programma.
* Se un nuovo ramo è stato aggiunto all&#39;archivio git durante la modifica della pipeline, potrebbe non essere stato immediatamente selezionabile.
* In alcune schermate, l&#39;icona Developer Connection nel menu Aiuto non era visibile.
* Il tasto di tabulazione non è stato gestito correttamente nella finestra di dialogo di eliminazione del dispatcher.

## Problemi noti {#known-issues}

* Quando si apre un programma che dispone di Siti, ma non di Risorse, KPI, tutti gli utenti visualizzano una scheda di invito all&#39;azione con un **pulsante Installazione programma** . Tuttavia, solo gli utenti del ruolo Proprietario business possono fare clic sul pulsante **Setup Program** .