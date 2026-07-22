---
title: Pipeline suddivise solo per staging e solo produzione
description: Scopri come suddividere le distribuzioni di staging e di produzione utilizzando pipeline dedicate.
exl-id: b7dd0021-d346-464a-a49e-72864b01cce3
TQID: https://experienceleague.adobe.com/whq-Hkwp3mjTr0iftoKZHKdsi0xaKtVXazXjUENoaLk
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 6b0075d2405e89dce1c883a2b5fc0bd952a3fddd
workflow-type: tm+mt
source-wordcount: 975
ht-degree: 53%

---

# Dividere le pipeline solo stadio e solo produzione {#stage-prod-only}

Puoi suddividere le distribuzioni di staging e produzione utilizzando pipeline dedicate.

## Panoramica {#overview}

Gli ambienti di staging e di produzione sono strettamente associati. Per impostazione predefinita, le distribuzioni ad essi sono collegate a una singola pipeline. Una pipeline di distribuzione viene distribuita sia negli ambienti di staging che in quelli di produzione all’interno di tale programma. Sebbene questo tipo di accoppiamento sia di norma adatto, in alcuni casi si verificano svantaggi:

* Se desideri eseguire la distribuzione nell&#39;area di gestione temporanea, salta il passaggio **Promuovi a Prod** nella pipeline. Tuttavia, l’esecuzione è contrassegnata come annullata.
* Se desideri distribuire il codice più recente da un ambiente di staging alla produzione, devi ridistribuire l’intera pipeline, inclusa la distribuzione di staging, anche se non è stato modificato alcun codice.
* Gli ambienti non possono essere aggiornati durante le distribuzioni. Se ritardi il test nell’ambiente di staging per diversi giorni prima di passare alla produzione, l’ambiente di produzione rimane bloccato e non può essere aggiornato. Questo scenario rende impossibili le attività non dipendenti come ad esempio l’aggiornamento delle [variabili di ambiente](/help/getting-started/build-environment.md#environment-variables).

Le pipeline solo stage e solo produzione offrono soluzioni a questi casi d’uso fornendo opzioni di distribuzione dedicate.

* **Pipeline di distribuzione solo staging:** eseguire la distribuzione solo in un ambiente di staging con l&#39;esecuzione completata al termine della distribuzione e dei test. Una pipeline solo di staging si comporta in modo identico alla pipeline di produzione full stack standard associata, ma senza i passaggi di distribuzione di produzione (approvazione, pianificazione, distribuzione).
* **Pipeline di distribuzione solo produzione:** Distribuire solo in produzione selezionando l&#39;esecuzione della fase più recente completata. Quindi, distribuisci gli artefatti in produzione. Le pipeline di sola produzione riutilizzano gli artefatti di distribuzione dello stadio, saltando la fase di build.

Le pipeline solo di staging e solo di produzione non vengono eseguite mentre è in corso una pipeline di produzione full stack e viceversa. Se sia la pipeline di produzione solo di staging che quella full stack dispongono del trigger **Cambiamenti su Git** configurato e indicano lo stesso ramo e archivio, viene avviata automaticamente la pipeline solo di staging. Le pipeline di sola produzione non attivano **`On Git Changes`** perché non sono collegate direttamente a un archivio.

Le pipeline solo di produzione vengono attivate manualmente, in quanto non sono collegate direttamente a un archivio per **Cambiamenti su Git**.

Queste pipeline dedicate offrono maggiore flessibilità, ma tieni presente i dettagli di funzionamento e le raccomandazioni seguenti:

>[!NOTE]
>
>Le pipeline solo per produzione utilizzano sempre gli artefatti della pipeline solo per staging. Questo processo rimane valido anche se nel frattempo la pipeline di produzione accoppiata standard ha implementato qualcos’altro per lo staging.
>
>* Tale scenario comporta rollback di codice indesiderati.
>* Adobe consiglia di interrompere l’utilizzo della pipeline di produzione accoppiata standard dopo aver iniziato a utilizzare le pipeline di sola produzione e di sola staging.
>* Se decidi comunque di eseguire sia le pipeline standard associate che le pipeline solo per staging o produzione, considera di riutilizzare gli artefatti per evitare rollback del codice.

## Creazione di pipeline {#pipeline-creation}

Le pipeline di sola produzione e di sola staging vengono create in modo simile alle [pipeline di produzione](/help/using/production-pipelines.md) e alle [pipeline non di produzione](/help/using/non-production-pipelines.md) accoppiate standard. Per informazioni dettagliate, consulta questi documenti.

1. Nella finestra delle **Pipeline**, fai clic su **Aggiungi pipeline**.

   * Seleziona **Aggiungi pipeline non di produzione** per creare una pipeline solo di staging.
   * Seleziona **Aggiungi pipeline di sola produzione** per creare una pipeline di sola produzione.

   ![Creazione di una pipeline solo di produzione/staging](/help/assets/configure-pipelines/prod-stage-pipelines.png)

>[!NOTE]
>
>Alcune opzioni sono disattivate se le pipeline corrispondenti esistono già.
>
>* **Aggiungi pipeline di sola produzione** non disponibile se non esiste ancora una pipeline di sola fase.
>* **Aggiungi pipeline di produzione** non sarà disponibile se esiste già una pipeline standard associata.
>* È consentita una sola pipeline di sola produzione e una sola pipeline di sola fase per programma.

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

1. Dopo aver fatto clic su **Aggiungi pipeline di sola produzione**, viene visualizzata la relativa finestra di dialogo associata.
1. Nel campo **Nome pipeline**, digita il nome desiderato. Le opzioni e le funzionalità rimanenti della finestra di dialogo funzionano come quelle della finestra di dialogo per la creazione di pipeline standard associate.
1. Nell’angolo inferiore a destra della finestra di dialogo, fai clic su **Salva**.

   ![Creazione di una pipeline solo di produzione](/help/assets/configure-pipelines/prod-only-pipeline.png)

## Esecuzione di pipeline solo di produzione e solo di staging {#running}

Le pipeline solo di produzione e solo di staging vengono eseguite in gran parte con le stesse modalità [di tutte le altre pipeline](/help/using/managing-pipelines.md#running-pipelines). Per ulteriori dettagli, consulta la documentazione. Tuttavia, sono disponibili due nuove funzioni di queste pipeline.

* Le pipeline solo di staging e solo di produzione offrono una nuova [modalità di emergenza](#emergency-mode) per passare il test.
* È possibile attivare un&#39;esecuzione di pipeline di sola produzione direttamente dai dettagli di esecuzione di una [pipeline di sola fase](#stage-only-run).

### Modalità di emergenza {#emergency-mode}

Quando si avviano le pipeline di sola produzione e di sola gestione temporanea, viene richiesto di confermare l’avvio e il modo in cui procede.

* **La modalità normale** è un’esecuzione standard e include i passaggi del test di staging.
* **Modalità di emergenza** ignora i passaggi del test di staging.

![Modalità di emergenza](/help/assets/configure-pipelines/emergency-mode.png)

### Pipeline solo di staging {#stage-only-run}

Una pipeline esclusivamente solo di staging viene eseguita quasi allo stesso modo delle pipeline standard associate. Tuttavia, al termine dell’esecuzione, dopo i passaggi di test, viene visualizzato un pulsante **Promuovi versione**. Questo pulsante ti consente di avviare un’esecuzione della pipeline di sola produzione. Utilizza gli artefatti distribuiti per l’esecuzione nell’ambiente di staging. Quindi li distribuisce in produzione.

![Esecuzione pipeline solo di staging](/help/assets/configure-pipelines/stage-only-pipeline-run.png)

Facendo clic su **Promuovi build** viene richiesto di confermare l&#39;esecuzione della pipeline di sola produzione correlata normalmente o in [modalità emergenza](#emergency-mode).

Se non esiste una pipeline solo di produzione, viene richiesto di crearne una.

### Pipeline solo di produzione {#prod-only-run}

Per le pipeline solo per produzione, assicurati di identificare gli artefatti di origine che desideri implementare in produzione. Questi dettagli sono disponibili nel passaggio **Preparazione degli artefatti**. Per ulteriori dettagli e registri, puoi passare a tali esecuzioni.

![Dettagli artefatto](/help/assets/configure-pipelines/prod-only-pipeline-run.png)

