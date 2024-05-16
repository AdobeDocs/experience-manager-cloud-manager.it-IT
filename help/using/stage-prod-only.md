---
title: Pipeline solo stage e solo produzione
description: Scopri come suddividere le distribuzioni di staging e produzione utilizzando pipeline dedicate.
source-git-commit: c09fbf30270523018a36b128d43cbf10e65daf54
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 1%

---


# Pipeline solo per staging e solo produzione {#stage-prod-only}

Scopri come suddividere le distribuzioni di staging e produzione utilizzando pipeline dedicate.

>[!NOTE]
>
>Questa funzione è disponibile solo per [il programma di adozione anticipata.](/help/release-notes/current.md#early-adoption)

## Panoramica {#overview}

Gli ambienti di staging e produzione sono strettamente collegati. Per impostazione predefinita, le distribuzioni a essi sono collegate a una singola pipeline. Si tratta di una pipeline di distribuzione distribuita sia negli ambienti di staging che in quelli di produzione in tale programma. Sebbene questo tipo di accoppiamento sia di norma adeguato, in alcuni casi sono presenti svantaggi:

* Se desideri eseguire la distribuzione solo in staging, puoi eseguire questa operazione solo rifiutando il **Promuovi a Prod** nella pipeline. Tuttavia, l’esecuzione verrà contrassegnata come annullata.
* Se desideri distribuire in produzione il codice più recente in un ambiente di staging, devi ridistribuire l’intera pipeline, inclusa la distribuzione di staging, anche se non è stato modificato alcun codice.
* Poiché gli ambienti non possono essere aggiornati durante le distribuzioni, se desideri sospendere e testare nell’ambiente di staging per più giorni prima di passare alla produzione, l’ambiente di produzione non può essere aggiornato. In questo modo vengono eseguite attività non dipendenti, ad esempio l&#39;aggiornamento [variabili di ambiente](/help/getting-started/build-environment.md#environment-variables) impossibile.

Le pipeline solo stage e solo produzione offrono soluzioni a questi casi d’uso fornendo opzioni di distribuzione dedicate.

* **Pipeline di implementazione per sola fase** implementa solo in un ambiente di staging con l’esecuzione che termina una volta completati la distribuzione e i test.
   * Una pipeline di sola fase si comporta in modo identico alla pipeline di produzione full stack standard associata, ma senza i passaggi di distribuzione della produzione (approvazione, pianificazione, distribuzione).
* **Pipeline di distribuzione solo produzione** distribuisci solo in un ambiente di produzione con l’opzione di selezionare un’esecuzione completata e convalidata correttamente sullo stage e distribuirne gli artefatti sul prod.
   * Le pipeline di sola produzione riutilizzeranno gli artefatti delle distribuzioni dello stage, saltando la fase di creazione.

Durante l’esecuzione di una pipeline di produzione full stack e viceversa, non verranno eseguite né pipeline di sola fase né pipeline di sola produzione.

Queste pipeline dedicate offrono maggiore flessibilità, ma tieni presente i dettagli di funzionamento e le raccomandazioni seguenti.

>[!NOTE]
>
>Le pipeline solo produzione utilizzeranno sempre gli artefatti della pipeline solo stadio, indipendentemente da ciò che nel frattempo potrebbe essere stato distribuito sullo stadio tramite la pipeline di produzione accoppiata standard.
>
>* Questo potrebbe causare rollback del codice indesiderati.
>* L’Adobe consiglia di interrompere l’utilizzo della pipeline di produzione accoppiata standard dopo aver iniziato a utilizzare le pipeline di sola produzione e di sola staging.
>* Se decidi comunque di eseguire sia le pipeline accoppiate standard che le pipeline di staging/sola produzione, tieni presente che riutilizzi gli artefatti per evitare rollback del codice.

## Creazione di pipeline {#pipeline-creation}

Le pipeline solo produzione e solo staging vengono create in modo simile all’accoppiamento standard [pipeline di produzione](/help/using/production-pipelines.md) e [pipeline non di produzione.](/help/using/non-production-pipelines.md) Per informazioni dettagliate, consulta i documenti.

1. In **Pipeline** finestra, tocca o fai clic su **Aggiungi pipeline**.

   * Seleziona **Aggiungi pipeline non di produzione** per creare una pipeline per sola fase.
   * Seleziona **Aggiungi pipeline solo produzione** per creare una pipeline di sola produzione.

   ![Creazione di una pipeline di sola produzione/staging](/help/assets/configure-pipelines/prod-stage-pipelines.png)

>[!NOTE]
>
>Alcune opzioni possono essere disattivate se le pipeline corrispondenti esistono già.
>
>* **Aggiungi pipeline solo produzione** non sarà disponibile se non esiste ancora una pipeline per sola fase.
>* **Aggiungi pipeline di produzione** non sarà disponibile se esiste già una pipeline accoppiata standard.
>* È consentita una sola pipeline per sola produzione e una sola pipeline per sola fase per programma.

### Pipeline solo stage {#stage-only}

1. Dopo aver selezionato **Aggiungi pipeline non di produzione** , l&#39;opzione **Aggiungi pipeline non di produzione** viene visualizzata una finestra di dialogo.
1. Per creare una pipeline per sola fase, seleziona l’ambiente di staging in **Ambienti di implementazione idonei** per la pipeline. Completa i campi rimanenti e tocca o fai clic su **Continua**.

   ![Creazione di una pipeline solo stage](/help/assets/configure-pipelines/stage-only.png)

1. Il giorno **Test dello staging** , è quindi possibile definire i test da eseguire nell’ambiente di staging. Tocca o fai clic su **Salva** per salvare la nuova pipeline.

   ![Parametri di test per una pipeline destinata solo allo stadio](/help/assets/configure-pipelines/stage-only-test.png)

### Pipeline di sola produzione {#prod-only}

1. Dopo aver selezionato **Aggiungi pipeline solo produzione** , l&#39;opzione **Aggiungi pipeline solo produzione** viene visualizzata una finestra di dialogo.
1. Fornisci un **Nome pipeline**. Le opzioni e le funzionalità rimanenti della finestra di dialogo funzionano come quelle della finestra di dialogo standard per la creazione di tubazioni accoppiate. Tocca o fai clic su **Salva** per salvare la pipeline.

   ![Creazione di una pipeline solo di produzione](/help/assets/configure-pipelines/prod-only-pipeline.png)

## Esecuzione di pipeline solo produzione e solo staging {#running}

Le pipeline di sola produzione e di sola staging vengono eseguite con le stesse modalità [vengono eseguite tutte le altre pipeline.](/help/using/managing-pipelines.md#running-pipelines) Per informazioni dettagliate, consulta la documentazione.

Inoltre, un’esecuzione della pipeline di sola produzione può essere attivata direttamente dai dettagli di esecuzione di una pipeline di sola fase.

### Pipeline solo stage {#stage-only-run}

Una pipeline esclusivamente stage viene eseguita quasi allo stesso modo delle pipeline accoppiate standard. Tuttavia, al termine dell’esecuzione, dopo i passaggi di test, viene **Promuovi build** consente di avviare un’esecuzione della pipeline di sola produzione che utilizza gli artefatti distribuiti nell’area di visualizzazione da questa esecuzione e li distribuisce nell’ambiente di produzione.

![Esecuzione pipeline solo stage](/help/assets/configure-pipelines/stage-only-pipeline-run.png)

Il **Promuovi build** Questo pulsante viene visualizzato solo se ti trovi nell’ultima esecuzione riuscita della pipeline solo della fase. Una volta toccato o fatto clic, ti verrà richiesto di confermare l’esecuzione della pipeline di sola produzione o di crearne una, se non ne esiste già una.

### Pipeline di sola produzione {#prod-only-run}

Per le pipeline di sola produzione è importante identificare gli artefatti di origine da distribuire in produzione. Questi dettagli sono disponibili nella sezione **Preparazione degli artefatti** passaggio. Puoi passare a tali esecuzioni per ulteriori dettagli e registri.

![Dettagli artefatto](/help/assets/configure-pipelines/prod-only-pipeline-run.png)
