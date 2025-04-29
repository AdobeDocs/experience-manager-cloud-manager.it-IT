---
title: Pipeline solo di staging e solo di produzione
description: Scopri come suddividere le distribuzioni di staging e di produzione utilizzando pipeline dedicate.
badge: label="Adottatore anticipato" type="Positive" url="/help/release-notes/current.md#staging-production-only-pipelines"
exl-id: b7dd0021-d346-464a-a49e-72864b01cce3
source-git-commit: b830c30bb6b2b99ef442577325a30de6b9953ec8
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 99%

---

# Pipeline solo di staging e solo di produzione {#stage-prod-only}

Scopri come suddividere le distribuzioni di staging e di produzione utilizzando pipeline dedicate.

>[!NOTE]
>
>Questa funzione è disponibile solo per [il programma per i primi utilizzatori](/help/release-notes/current.md#staging-production-only-pipelines).

## Panoramica {#overview}

Gli ambienti di staging e produzione sono strettamente associati. Per impostazione predefinita, le distribuzioni ad essi sono collegate a una singola pipeline. Si tratta di una pipeline di distribuzione che distribuisce sia negli ambienti di staging che in quelli di produzione in tale programma. Sebbene questo tipo di associazione sia di norma adeguato, alcuni casi d’uso presentano degli svantaggi:

* Se desideri eseguire una distribuzione solo di staging, rifiuta il passaggio nella pipeline **Promuovi per produrre**. Tuttavia, l’esecuzione verrà contrassegnata come annullata.
* Se desideri distribuire il codice più recente in un ambiente di staging nella produzione, devi ridistribuire l’intera pipeline, inclusa la distribuzione di staging, anche se non è stato modificato alcun codice.
* Gli ambienti non possono essere aggiornati durante le distribuzioni. Se sospendi il test nell’ambiente di staging per diversi giorni prima di passare alla produzione, l’ambiente di produzione rimane bloccato e non può essere aggiornato. Questo scenario rende impossibili le attività non dipendenti come ad esempio l’aggiornamento delle [variabili di ambiente](/help/getting-started/build-environment.md#environment-variables).

Le pipeline solo di staging e solo di produzione offrono soluzioni a questi casi d’uso fornendo opzioni di distribuzione dedicate.

* **Pipeline di distribuzione solo di staging:** vengono distribuite solo in un ambiente di staging con l’esecuzione che termina una volta completati la distribuzione e i test. Una pipeline solo di staging si comporta in modo identico alla pipeline di produzione full stack standard associata, ma senza i passaggi di distribuzione di produzione (approvazione, pianificazione, distribuzione).
* **Pipeline di distribuzione per solo produzione:** vengono distribuite solo in produzione selezionando l’esecuzione della fase più recente completata correttamente. Quindi distribuendo i relativi artefatti in produzione. Le pipeline di sola produzione riutilizzano gli artefatti di distribuzione della fase, ignorando la fase di build.

Le pipeline solo di staging e solo di produzione non vengono eseguite mentre è in corso una pipeline di produzione full stack e viceversa. Se sia la pipeline di produzione solo di staging che quella full stack dispongono del trigger **Cambiamenti su Git** configurato e indicano lo stesso ramo e archivio, viene avviata automaticamente la pipeline solo di staging. Le pipeline solo di produzione non avviano i **`On Git Changes`** perché non sono collegate direttamente a un archivio.

Le pipeline solo di produzione vengono attivate manualmente, in quanto non sono collegate direttamente a un archivio per **Cambiamenti su Git**.

Queste pipeline dedicate offrono maggiore flessibilità, ma tieni presente i dettagli dell’operazione e le raccomandazioni seguenti.

>[!NOTE]
>
>Le pipeline solo di produzione utilizzano sempre gli artefatti della pipeline solo di staging. Questo processo rimane valido anche se nel frattempo la pipeline di produzione standard associata ha implementato qualcos’altro per lo staging.
>
>* Tale scenario potrebbe causare ripristini del codice indesiderati.
>* Adobe consiglia di interrompere l’utilizzo della pipeline di produzione standard associate dopo aver iniziato a utilizzare le pipeline solo di produzione e solo di staging.
>* Se decidi comunque di eseguire sia le pipeline standard associate che le pipeline solo di staging/produzione, considera di riutilizzare gli artefatti per evitare ripristini del codice.

## Creazione di pipeline {#pipeline-creation}

Le pipeline solo di produzione e solo di staging vengono create in modo simile alle [pipeline di produzione](/help/using/production-pipelines.md) standard associate e alle [pipeline non di produzione](/help/using/non-production-pipelines.md). Per informazioni dettagliate, consulta questi documenti.

1. Nella finestra delle **Pipeline**, fai clic su **Aggiungi pipeline**.

   * Seleziona **Aggiungi pipeline non di produzione** per creare una pipeline solo di staging.
   * Seleziona **Aggiungi pipeline solo di produzione** per creare una pipeline solo di produzione.

   ![Creazione di una pipeline solo di produzione/staging](/help/assets/configure-pipelines/prod-stage-pipelines.png)

>[!NOTE]
>
>Alcune opzioni potrebbero essere disattivate se le pipeline corrispondenti esistono già.
>
>* **Aggiungi pipeline solo di produzione** non sarà disponibile se non esiste ancora una pipeline solo di staging.
>* **Aggiungi pipeline di produzione** non sarà disponibile se esiste già una pipeline standard associata.
>* Sono consentite pipeline solo di produzione e solo di staging per programma.

### Pipeline solo di staging {#stage-only}

1. Dopo aver selezionato l’opzione **Aggiungi pipeline non di produzione**, viene aperta la finestra di dialogo **Aggiungi pipeline non di produzione**.
1. Per creare una pipeline solo di staging, seleziona l’ambiente di staging nel campo **Ambienti di implementazione idonei** per la pipeline.
1. Completa i campi rimanenti.
1. Fai clic su **Continua**.

   ![Creazione di una pipeline solo di staging](/help/assets/configure-pipelines/stage-only.png)

1. Nella scheda **Test di staging**, definisci il test da eseguire nell’ambiente di staging.
1. Fai clic su **Salva**.

   ![Parametri di test per una pipeline solo di staging](/help/assets/configure-pipelines/stage-only-test.png)

### Pipeline solo di produzione {#prod-only}

1. Dopo aver selezionato l’opzione **Aggiungi pipeline solo di produzione**, viene aperta la finestra di dialogo **Aggiungi pipeline solo di produzione**.
1. Nel campo **Nome pipeline**, digita il nome desiderato. Le opzioni e le funzionalità rimanenti della finestra di dialogo funzionano come quelle della finestra di dialogo per la creazione di pipeline standard associate.
1. Nell’angolo inferiore a destra della finestra di dialogo, fai clic su **Salva**.

   ![Creazione di una pipeline solo di produzione](/help/assets/configure-pipelines/prod-only-pipeline.png)

## Esecuzione di pipeline solo di produzione e solo di staging {#running}

Le pipeline solo di produzione e solo di staging vengono eseguite in gran parte con le stesse modalità [di tutte le altre pipeline](/help/using/managing-pipelines.md#running-pipelines). Per ulteriori dettagli, consulta la documentazione. Tuttavia, sono disponibili due nuove funzioni di queste pipeline.

* Le pipeline solo di staging e solo di produzione offrono una nuova [modalità di emergenza](#emergency-mode) per passare il test.
* Un’esecuzione della pipeline solo di produzione può essere attivata direttamente dai dettagli di esecuzione di una [pipeline solo di staging](#stage-only-run).

### Modalità di emergenza {#emergency-mode}

All’avvio delle pipeline online solo di produzione e solo di staging, viene richiesto di confermare l’avvio e la relativa modalità di avvio.

* **La modalità normale** è un’esecuzione standard e include i passaggi del test di staging.
* **Modalità di emergenza** ignora i passaggi del test di staging.

![Modalità di emergenza](/help/assets/configure-pipelines/emergency-mode.png)

### Pipeline solo di staging {#stage-only-run}

Una pipeline esclusivamente solo di staging viene eseguita quasi allo stesso modo delle pipeline standard associate. Tuttavia, al termine dell’esecuzione, dopo i passaggi di test, viene visualizzato un pulsante **Promuovi versione**. Questo pulsante consente di avviare un’esecuzione della pipeline solo di produzione utilizzando gli artefatti distribuiti nell’ambiente di staging durante l’esecuzione, e distribuirli nell’ambiente di produzione.

![Esecuzione pipeline solo di staging](/help/assets/configure-pipelines/stage-only-pipeline-run.png)

Facendo clic su **Promuovi versione** viene richiesto di confermare l’esecuzione della pipeline solo di staging correlata normalmente o in [modalità di emergenza](#emergency-mode).

Se non esiste una pipeline solo di produzione, viene richiesto di crearne una.

### Pipeline solo di produzione {#prod-only-run}

Per le pipeline solo di produzione, assicurati di identificare gli artefatti di origine che desideri implementare in produzione. Questi dettagli sono disponibili nel passaggio **Preparazione degli artefatti**. Per ulteriori dettagli e registri, puoi passare a tali esecuzioni.

![Dettagli artefatto](/help/assets/configure-pipelines/prod-only-pipeline-run.png)

