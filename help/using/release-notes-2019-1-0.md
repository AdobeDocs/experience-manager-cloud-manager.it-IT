---
title: Note sulla versione 2019.1.0
seo-title: AEM Cloud Manager Release Notes for 2019.1.0
description: Segui questa pagina per ottenere informazioni sulla versione 2019.1.0 di Cloud Manager.
seo-description: Follow this page to get information for AEM Cloud Manager Release 2019.1.0.
uuid: 3af5808f-828f-4846-bee4-1e62194b48ad
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 85a1dcf3-2eef-4ba8-b4d1-09e4a88c7bd0
feature: Release Information
exl-id: 383ca5a0-4b0b-48e9-aa48-1d1388875329
source-git-commit: 4f0e1d163001fd18cfa838256c813152d65c3b4c
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 4%

---

# Note sulla versione 2019.1.0 {#release-notes-for}

La [!UICONTROL Cloud Manager] La versione 2018.9.0 aggiunge il supporto per i programmi AEM Assets e ulteriori tipi di pipeline che eseguono i passaggi di creazione e qualità del codice, distribuendo facoltativamente in un ambiente non di produzione.

## Data di pubblicazione {#release-date}

Data di rilascio per [!UICONTROL Cloud Manager] La versione 2019.1.0 è il 17 gennaio 2019.

## Novità {#whats-new}

* È stato aggiunto il supporto per il test delle prestazioni di AEM Assets. Fare riferimento al documento [Configurare le pipeline di produzione](configuring-production-pipelines.md) per saperne di più.
* È stato aggiunto il supporto per le pipeline che eseguono solo passaggi di generazione e qualità del codice e per le pipeline che vengono distribuite in ambienti non di produzione. Fare riferimento al documento [Configurare pipeline non di produzione](configuring-non-production-pipelines.md) per saperne di più.
* È stato aggiunto il supporto per le variabili di ambiente personalizzate nell’ambiente di creazione.
* Per i clienti con più ambienti di stage o produzione, è disponibile una selezione dell’ambiente a cui verrà distribuito come parte della pipeline di produzione. Fare riferimento al documento [Configurare le pipeline di produzione](configuring-production-pipelines.md) per saperne di più.
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

* Quando si apre un programma con Sites impostato ma non Assets, KPI, tutti gli utenti visualizzano una scheda di chiamata all’azione con un **Programma di installazione** pulsante . Tuttavia, solo gli utenti con il ruolo Proprietario business possono fare clic sul **Programma di installazione** pulsante .
