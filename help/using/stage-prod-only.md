---
title: Pipeline solo di staging e solo di produzione
description: Scopri come suddividere le distribuzioni di staging e produzione utilizzando pipeline dedicate.
exl-id: b7dd0021-d346-464a-a49e-72864b01cce3
source-git-commit: 77eb1c824ba766e43dfd8e2b0f6f6edc71f043e5
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 31%

---

# Pipeline solo per staging e solo per la produzione {#stage-prod-only}

Scopri come suddividere le distribuzioni di staging e produzione utilizzando pipeline dedicate.

>[!NOTE]
>
>Questa funzionalità è disponibile solo per [il programma per l&#39;adozione anticipata](/help/release-notes/current.md#early-adoption).

## Panoramica {#overview}

Gli ambienti di staging e produzione sono strettamente associati. Per impostazione predefinita, le distribuzioni ad essi sono collegate a una singola pipeline. In altre parole, una pipeline di distribuzione viene distribuita sia negli ambienti di staging che in quelli di produzione di tale programma. Sebbene questo tipo di associazione sia di norma adeguato, alcuni casi d’uso presentano degli svantaggi:

* Se desideri eseguire la distribuzione solo nell&#39;area di staging, rifiuta il passaggio **Promuovi a Prod** nella pipeline. Tuttavia, l’esecuzione viene contrassegnata come annullata.
* Se desideri distribuire in produzione il codice più recente in un ambiente di staging, devi ridistribuire l’intera pipeline, inclusa la distribuzione di staging, anche se non è stato modificato alcun codice.
* Gli ambienti non possono essere aggiornati durante le distribuzioni. Se si sospende il test nell’ambiente di staging per diversi giorni prima di passare alla produzione, l’ambiente di produzione rimane bloccato e non può essere aggiornato. Questo scenario rende impossibili attività non dipendenti, come l&#39;aggiornamento di [variabili di ambiente](/help/getting-started/build-environment.md#environment-variables).

Le pipeline solo di staging e solo di produzione offrono soluzioni a questi casi d’uso fornendo opzioni di distribuzione dedicate.

* **Pipeline di distribuzione solo staging:** distribuite solo in un ambiente di staging con l&#39;esecuzione completata al termine della distribuzione e dei test. Una pipeline solo di staging si comporta in modo identico alla pipeline di produzione full stack standard associata, ma senza i passaggi di distribuzione di produzione (approvazione, pianificazione, distribuzione).
* **Pipeline di distribuzione di sola produzione:** vengono distribuite solo in produzione selezionando un&#39;esecuzione della fase completata. Quindi distribuendo i relativi artefatti in produzione. Le pipeline di sola produzione riutilizzano gli artefatti di distribuzione dello stadio, ignorando la fase di build.

Le pipeline di sola staging e di sola produzione non vengono eseguite mentre è in corso una pipeline di produzione full stack e viceversa. Se sia la pipeline di produzione solo di staging che quella full stack dispongono del trigger **On Git Changes** configurato e indicano lo stesso ramo e archivio, viene avviata automaticamente la pipeline solo di staging. Le pipeline di sola produzione non avviano **`On Git Changes`** perché non sono collegate direttamente a un archivio.

Le pipeline di sola produzione vengono attivate manualmente, in quanto non sono collegate direttamente a un archivio per **In caso di modifiche Git**.

Queste pipeline dedicate offrono maggiore flessibilità, ma tieni presente i dettagli di funzionamento e le raccomandazioni seguenti.

>[!NOTE]
>
>Le pipeline di sola produzione utilizzano sempre gli artefatti della pipeline di sola visualizzazione. Questo processo rimane valido anche se nel frattempo la pipeline di produzione accoppiata standard ha implementato qualcos’altro per lo staging.
>
>* Ad esempio, uno scenario potrebbe causare rollback del codice indesiderati.
>* Adobe consiglia di interrompere l’utilizzo della pipeline di produzione standard associate dopo aver iniziato a utilizzare le pipeline solo di produzione e solo di staging.
>* Se decidi comunque di eseguire sia le pipeline standard associate che le pipeline solo di staging/produzione, considera di riutilizzare gli artefatti per evitare ripristini del codice.

## Creazione di pipeline {#pipeline-creation}

Le pipeline di sola produzione e di sola staging vengono create in modo simile alle [pipeline di produzione](/help/using/production-pipelines.md) e [pipeline non di produzione](/help/using/non-production-pipelines.md) accoppiate standard. Per informazioni dettagliate, consulta questi documenti.

1. Nella finestra **Pipeline**, fai clic su **Aggiungi pipeline**.

   * Seleziona **Aggiungi pipeline non di produzione** per creare una pipeline solo di staging.
   * Seleziona **Aggiungi pipeline solo di produzione** per creare una pipeline solo di produzione.

   ![Creazione di una pipeline solo di produzione/staging](/help/assets/configure-pipelines/prod-stage-pipelines.png)

>[!NOTE]
>
>Alcune opzioni potrebbero essere disattivate se le pipeline corrispondenti esistono già.
>
>* **Aggiungi pipeline di sola produzione** non disponibile se non esiste ancora una pipeline di sola fase.
>* **Aggiungi pipeline di produzione** non è disponibile se esiste già una pipeline accoppiata standard.
>* Sono consentite pipeline solo di produzione e solo di staging per programma.

### Pipeline solo stage {#stage-only}

1. Dopo aver selezionato l&#39;opzione **Aggiungi pipeline non di produzione**, viene visualizzata la finestra di dialogo **Aggiungi pipeline non di produzione**.
1. Per creare una pipeline solo di staging, seleziona l’ambiente di staging nel campo **Ambienti di implementazione idonei** per la pipeline. Completare i campi rimanenti e fare clic su **Continua**.

   ![Creazione di una pipeline solo di staging](/help/assets/configure-pipelines/stage-only.png)

1. Nella scheda **Test dello staging** è quindi possibile definire i test da eseguire nell&#39;ambiente di staging. Fai clic su **Salva** per salvare la nuova pipeline.

   ![Parametri di test per una pipeline solo di staging](/help/assets/configure-pipelines/stage-only-test.png)

### Pipeline di sola produzione {#prod-only}

1. Dopo aver selezionato l&#39;opzione **Aggiungi pipeline solo produzione**, viene visualizzata la finestra di dialogo **Aggiungi pipeline solo produzione**.
1. Fornisci un **Nome pipeline**. Le altre opzioni e funzionalità della finestra di dialogo funzionano come quelle disponibili nella finestra di dialogo standard per la creazione di tubazioni accoppiate. Fai clic su **Salva** per salvare la pipeline.

   ![Creazione di una pipeline solo di produzione](/help/assets/configure-pipelines/prod-only-pipeline.png)

## Eseguire pipeline solo produzione e solo staging {#running}

Le pipeline di sola produzione e di sola staging vengono eseguite in gran parte nello stesso modo in cui vengono eseguite [ tutte le altre pipeline.](/help/using/managing-pipelines.md#running-pipelines) Per informazioni dettagliate, consulta la documentazione. Tuttavia, queste pipeline presentano due nuove funzioni.

* Le pipeline di sola fase e di sola produzione offrono una nuova [modalità emergenza](#emergency-mode) per consentire di saltare i test.
* L&#39;esecuzione della pipeline di sola produzione può essere attivata direttamente dai dettagli di esecuzione di una pipeline di [sola fase.](#stage-only-run)

### Modalità di emergenza {#emergency-mode}

Ogni volta che avvii le pipeline online di sola produzione e di staging, ti viene richiesto di confermare l’avvio e come verrà avviato.

* **La modalità normale** è un&#39;esecuzione standard e include i passaggi del test dell&#39;area di visualizzazione.
* **Modalità emergenza** ignora i passaggi del test dello staging.

![Modalità emergenza](/help/assets/configure-pipelines/emergency-mode.png)

### Pipeline solo stage {#stage-only-run}

Una pipeline esclusivamente solo di staging viene eseguita quasi allo stesso modo delle pipeline associate standard. Tuttavia, al termine dell&#39;esecuzione, dopo i passaggi di test, viene visualizzato un pulsante **Promuovi build**. Questo pulsante consente di avviare un’esecuzione della pipeline di sola produzione utilizzando gli artefatti distribuiti nell’area di visualizzazione durante l’esecuzione e distribuirli nell’ambiente di produzione.

![Esecuzione pipeline solo di staging](/help/assets/configure-pipelines/stage-only-pipeline-run.png)

Facendo clic su **Promuovi build** viene richiesto di confermare l&#39;esecuzione della pipeline correlata solo fase normalmente o in [modalità emergenza.](#emergency-mode)

Se non esiste una pipeline di sola produzione, viene richiesto di crearne una.

### Pipeline di sola produzione {#prod-only-run}

Per le pipeline di sola produzione, è importante identificare gli artefatti di origine da distribuire in produzione. Questi dettagli sono disponibili nel passaggio **Preparazione degli artefatti**. Puoi passare a tali esecuzioni per ulteriori dettagli e registri.

![Dettagli artefatto](/help/assets/configure-pipelines/prod-only-pipeline-run.png)
