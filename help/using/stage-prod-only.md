---
title: Pipeline solo di staging e solo di produzione
description: Scopri come suddividere le distribuzioni di staging e di produzione utilizzando pipeline dedicate.
exl-id: b7dd0021-d346-464a-a49e-72864b01cce3
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 42%

---

# Pipeline solo di staging e solo di produzione {#stage-prod-only}

Scopri come suddividere le distribuzioni di staging e di produzione utilizzando pipeline dedicate.

>[!NOTE]
>
>Questa funzione è disponibile solo per [il programma per i primi utilizzatori](/help/release-notes/current.md#early-adoption).

## Panoramica {#overview}

Gli ambienti di staging e produzione sono strettamente associati. Per impostazione predefinita, le distribuzioni ad essi sono collegate a una singola pipeline. In altre parole, una pipeline di distribuzione viene distribuita sia negli ambienti di staging che in quelli di produzione di tale programma. Sebbene questo tipo di associazione sia di norma adeguato, alcuni casi d’uso presentano degli svantaggi:

* Se desideri eseguire la distribuzione solo nell&#39;area di staging, rifiuta il passaggio **Promuovi a Prod** nella pipeline. Tuttavia, l’esecuzione viene contrassegnata come annullata.
* Se desideri distribuire il codice più recente in un ambiente di staging nella produzione, devi ridistribuire l’intera pipeline, inclusa la distribuzione di staging, anche se non è stato modificato alcun codice.
* Gli ambienti non possono essere aggiornati durante le distribuzioni. Se si sospende il test nell’ambiente di staging per diversi giorni prima di passare alla produzione, l’ambiente di produzione rimane bloccato e non può essere aggiornato. Questo scenario rende impossibili attività non dipendenti, come l&#39;aggiornamento di [variabili di ambiente](/help/getting-started/build-environment.md#environment-variables).

Le pipeline solo di staging e solo di produzione offrono soluzioni a questi casi d’uso fornendo opzioni di distribuzione dedicate.

* **Pipeline di distribuzione solo staging:** distribuite solo in un ambiente di staging con l&#39;esecuzione completata al termine della distribuzione e dei test. Una pipeline solo di staging si comporta in modo identico alla pipeline di produzione full stack standard associata, ma senza i passaggi di distribuzione di produzione (approvazione, pianificazione, distribuzione).
* **Pipeline di distribuzione per sola produzione:** vengono distribuite solo in produzione selezionando un&#39;esecuzione della fase completata. Quindi distribuendo i relativi artefatti in produzione. Le pipeline di sola produzione riutilizzano gli artefatti di distribuzione dello stadio, ignorando la fase di build.

Le pipeline di sola staging e di sola produzione non vengono eseguite mentre è in corso una pipeline di produzione full stack e viceversa. Se sia la pipeline di produzione solo di staging che quella full stack dispongono del trigger **On Git Changes** configurato e indicano lo stesso ramo e archivio, viene avviata automaticamente la pipeline solo di staging. Le pipeline di sola produzione non avviano **`On Git Changes`** perché non sono collegate direttamente a un archivio.

Le pipeline di sola produzione vengono attivate manualmente, in quanto non sono collegate direttamente a un archivio per **In caso di modifiche Git**.

Queste pipeline dedicate offrono maggiore flessibilità, ma tieni presente i dettagli dell’operazione e le raccomandazioni seguenti.

>[!NOTE]
>
>Le pipeline di sola produzione utilizzano sempre gli artefatti della pipeline di sola visualizzazione. Questo processo rimane valido anche se nel frattempo la pipeline di produzione accoppiata standard ha implementato qualcos’altro per lo staging.
>
>* Ad esempio, uno scenario potrebbe causare rollback del codice indesiderati.
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

1. Dopo aver selezionato l&#39;opzione **Aggiungi pipeline non di produzione**, viene visualizzata la finestra di dialogo **Aggiungi pipeline non di produzione**.
1. Per creare una pipeline per sola fase, seleziona l&#39;ambiente di fase nel campo **Ambienti di distribuzione idonei** per la pipeline.
1. Compila i campi rimanenti.
1. Fai clic su **Continua**.

   ![Creazione di una pipeline solo di staging](/help/assets/configure-pipelines/stage-only.png)

1. Nella scheda **Test dello staging**, definisci il test da eseguire nell&#39;ambiente di staging.
1. Fai clic su **Salva**.

   ![Parametri di test per una pipeline solo di staging](/help/assets/configure-pipelines/stage-only-test.png)

### Pipeline solo di produzione {#prod-only}

1. Dopo aver selezionato l&#39;opzione **Aggiungi pipeline solo produzione**, viene visualizzata la finestra di dialogo **Aggiungi pipeline solo produzione**.
1. Nel campo **Nome pipeline** digitare il nome desiderato. Le altre opzioni e funzionalità della finestra di dialogo funzionano come quelle disponibili nella finestra di dialogo standard per la creazione di tubazioni accoppiate.
1. Nell&#39;angolo inferiore destro della finestra di dialogo fare clic su **Salva**.

   ![Creazione di una pipeline solo di produzione](/help/assets/configure-pipelines/prod-only-pipeline.png)

## Esecuzione di pipeline solo di produzione e solo di staging {#running}

Le pipeline di sola produzione e di sola staging vengono eseguite in gran parte nello stesso modo in cui vengono eseguite [tutte le altre pipeline](/help/using/managing-pipelines.md#running-pipelines). Per informazioni dettagliate, consulta la documentazione. Tuttavia, queste pipeline presentano due nuove funzioni.

* Le pipeline di sola fase e di sola produzione offrono una nuova [modalità emergenza](#emergency-mode) per saltare il test.
* L&#39;esecuzione della pipeline solo produzione può essere attivata direttamente dai dettagli di esecuzione di una [pipeline solo fase](#stage-only-run).

### Modalità di emergenza {#emergency-mode}

All’avvio delle pipeline online di sola produzione e di staging, viene richiesto di confermare l’avvio e la relativa modalità di avvio.

* **La modalità normale** è un&#39;esecuzione standard e include i passaggi del test dell&#39;area di visualizzazione.
* **Modalità emergenza** ignora i passaggi del test dello staging.

![Modalità emergenza](/help/assets/configure-pipelines/emergency-mode.png)

### Pipeline solo di staging {#stage-only-run}

Una pipeline esclusivamente solo di staging viene eseguita quasi allo stesso modo delle pipeline associate standard. Tuttavia, al termine dell&#39;esecuzione, dopo i passaggi di test, viene visualizzato un pulsante **Promuovi build**. Questo pulsante consente di avviare un’esecuzione della pipeline di sola produzione utilizzando gli artefatti distribuiti nell’area di visualizzazione durante l’esecuzione e distribuirli nell’ambiente di produzione.

![Esecuzione pipeline solo di staging](/help/assets/configure-pipelines/stage-only-pipeline-run.png)

Facendo clic su **Promuovi build** viene richiesto di confermare l&#39;esecuzione della pipeline correlata solo fase normalmente o in [modalità emergenza](#emergency-mode).

Se non esiste una pipeline di sola produzione, viene richiesto di crearne una.

### Pipeline solo di produzione {#prod-only-run}

Per le pipeline di sola produzione, assicurati di identificare gli artefatti di origine che desideri distribuire in produzione. Questi dettagli si trovano nel passaggio **Preparazione elemento**. Per ulteriori dettagli e registri, puoi passare a tali esecuzioni.

![Dettagli artefatto](/help/assets/configure-pipelines/prod-only-pipeline-run.png)
