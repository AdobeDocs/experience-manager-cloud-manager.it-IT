---
title: Pipeline solo di staging e solo di produzione
description: Scopri come suddividere le distribuzioni di staging e produzione utilizzando pipeline dedicate.
exl-id: b7dd0021-d346-464a-a49e-72864b01cce3
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '878'
ht-degree: 72%

---

# Pipeline solo per staging e solo per la produzione {#stage-prod-only}

Scopri come suddividere le distribuzioni di staging e produzione utilizzando pipeline dedicate.

>[!NOTE]
>
>Questa funzionalità è disponibile solo per [il programma per l&#39;adozione anticipata](/help/release-notes/current.md#early-adoption).

## Panoramica {#overview}

Gli ambienti di staging e produzione sono strettamente associati. Per impostazione predefinita, le distribuzioni ad essi sono collegate a una singola pipeline. Si tratta di una pipeline di distribuzione che distribuisce sia negli ambienti di staging che in quelli di produzione in tale programma. Sebbene questo tipo di associazione sia di norma adeguato, alcuni casi d’uso presentano degli svantaggi:

* Se desideri eseguire la distribuzione solo nell&#39;ambiente di staging, puoi eseguire questa operazione solo rifiutando il passaggio **Promuovi in produzione** nella pipeline. Tuttavia, l’esecuzione verrà contrassegnata come annullata.
* Se desideri distribuire in produzione il codice più recente in un ambiente di staging, devi ridistribuire l’intera pipeline, inclusa la distribuzione di staging, anche se non è stato modificato alcun codice.
* Poiché gli ambienti non possono essere aggiornati durante le distribuzioni, se desideri sospendere e testare nell’ambiente di staging per più giorni prima della promozione alla produzione, l’ambiente di produzione non può essere aggiornato. Questo rende impossibili le attività non dipendenti come ad esempio l’aggiornamento delle [variabili di ambiente](/help/getting-started/build-environment.md#environment-variables).

Le pipeline solo di staging e solo di produzione offrono soluzioni a questi casi d’uso fornendo opzioni di distribuzione dedicate.

* Le **pipeline di distribuzione solo di staging** distribuiscono solo in un ambiente di staging con l’esecuzione che termina una volta completati la distribuzione e i test.
   * Una pipeline solo di staging si comporta in modo identico alla pipeline di produzione full stack standard associata, ma senza i passaggi di distribuzione di produzione (approvazione, pianificazione, distribuzione).
* Le **pipeline di distribuzione solo di produzione** distribuiscono esclusivamente in un ambiente di produzione con l’opzione di selezionare un’esecuzione completata e convalidata correttamente in staging e di distribuire gli artefatti in produzione.
   * Le pipeline solo di produzione riutilizzeranno gli artefatti dalle distribuzioni di staging, saltando la fase di creazione.

Né le pipeline solo di staging, né quelle solo di solo produzione verranno eseguite mentre una pipeline di produzione full-stack è in esecuzione e viceversa. Se sia la pipeline di produzione solo di staging che quella full stack dispongono del trigger **On Git Changes** configurato e indicano lo stesso ramo e archivio, viene avviata automaticamente la pipeline solo di staging. Le pipeline di solo produzione non sono avviate su **On Git Changes** in quanto non sono collegate direttamente a un archivio.

Queste pipeline dedicate offrono maggiore flessibilità, ma tieni presente i dettagli di funzionamento e le raccomandazioni seguenti.

>[!NOTE]
>
>Le pipeline solo di produzione utilizzeranno sempre gli artefatti dalla pipeline solo di staging, indipendentemente da ciò che nel frattempo potrebbe essere stato distribuito in staging tramite la pipeline di produzione standard associata.
>
>* Questo potrebbe causare ripristini del codice indesiderati.
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

1. Sulla scheda **Test di staging**, è quindi possibile definire i test da eseguire nell’ambiente di staging. Fai clic su **Salva** per salvare la nuova pipeline.

   ![Parametri di test per una pipeline solo di staging](/help/assets/configure-pipelines/stage-only-test.png)

### Pipeline di sola produzione {#prod-only}

1. Dopo aver selezionato l’opzione **Aggiungi pipeline solo di produzione**, viene aperta la finestra di dialogo **Aggiungi pipeline solo di produzione**.
1. Fornisci un **Nome pipeline**. Le opzioni e le funzionalità rimanenti della finestra di dialogo funzionano come quelle della finestra di dialogo per la creazione di pipeline standard associate. Fai clic su **Salva** per salvare la pipeline.

   ![Creazione di una pipeline solo di produzione](/help/assets/configure-pipelines/prod-only-pipeline.png)

## Eseguire pipeline solo produzione e solo staging {#running}

Le pipeline di sola produzione e di sola staging vengono eseguite nello stesso modo in cui vengono eseguite [tutte le altre pipeline](/help/using/managing-pipelines.md#running-pipelines). Per informazioni dettagliate, consulta la documentazione.

Inoltre, un’esecuzione della pipeline solo di produzione può essere attivata direttamente dai dettagli di esecuzione di una pipeline solo di staging.

### Pipeline solo stage {#stage-only-run}

Una pipeline esclusivamente solo di staging viene eseguita quasi allo stesso modo delle pipeline associate standard. Tuttavia, al termine dell’esecuzione, dopo i passaggi di test, il pulsante **Promuovi versione** consente di avviare un’esecuzione della pipeline solo di produzione che utilizza gli artefatti distribuiti durante lo staging da questa esecuzione e li distribuisce nell’ambiente di produzione.

![Esecuzione pipeline solo di staging](/help/assets/configure-pipelines/stage-only-pipeline-run.png)

Il pulsante **Promuovi versione** viene visualizzato solo se ti trovi nell’ultima esecuzione riuscita della pipeline solo di staging. Dopo aver fatto clic su, viene richiesto di confermare l’esecuzione della pipeline di sola produzione o di crearne una, se non esiste già.

### Pipeline di sola produzione {#prod-only-run}

Per le pipeline solo di produzione è importante identificare gli artefatti di origine da distribuire in produzione. Questi dettagli sono disponibili nel passaggio **Preparazione degli artefatti**. Puoi passare a tali esecuzioni per ulteriori dettagli e registri.

![Dettagli artefatto](/help/assets/configure-pipelines/prod-only-pipeline-run.png)
