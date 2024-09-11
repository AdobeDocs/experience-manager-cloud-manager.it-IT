---
title: Gestire le pipeline
description: Scopri come gestire, modificare, eseguire ed eliminare le pipeline esistenti.
exl-id: e36420d2-57c5-4375-99fb-dd47c1c8bffd
source-git-commit: 8e2c57d2594691e7fb18d8a538caa9b54a26b6bb
workflow-type: ht
source-wordcount: '840'
ht-degree: 100%

---


# Gestire le pipeline {#managing-pipelines}

Scopri come gestire, modificare, eseguire ed eliminare le pipeline esistenti.

## Scheda pipeline {#pipeline-card}

La scheda **Pipeline** della pagina **Panoramica del programma** in Cloud Manager offre una panoramica di tutte le pipeline e del relativo stato corrente.

![Scheda Pipeline in Cloud Manager](/help/assets/configure-pipelines/pipelines-card.png)

Facendo clic sul pulsante con i puntini di sospensione accanto a ogni pipeline, puoi effettuare le seguenti operazioni:

* [Eseguire la pipeline](#running-pipelines).
* [Modificare la pipeline](#editing-pipelines).
* [Eliminare la pipeline](#deleting-pipelines).
* [Visualizzare i dettagli](#view-details).

Nella parte inferiore dell’elenco delle pipeline sono disponibili le opzioni generali.

* **Aggiungi**: per [aggiungere una nuova pipeline di produzione](/help/using/production-pipelines.md) o [una nuova pipeline di non produzione](/help/using/non-production-pipelines.md).
* **Mostra tutto**: porta l’utente alla schermata **Pipeline** per visualizzare tutte le pipeline in una tabella più dettagliata.
* **Accesso a dati archivio**: consente di visualizzare le informazioni necessarie per accedere all’archivio Git di Cloud Manager.
* **Ulteriori informazioni**: consente di accedere alle risorse della documentazione sulla pipeline CI/CD.

## Finestra Pipeline {#pipelines}

La finestra **Pipeline** mostra un elenco completo di tutte le pipeline per il programma selezionato. Questo elenco è utile in quanto presenta informazioni più complete rispetto a quelle disponibili nella [Scheda pipeline](#pipeline-card).

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Nella pagina **Panoramica del programma**, fai clic sulla scheda **Pipeline** per passare alla finestra **Pipeline**.

1. Qui puoi visualizzare un elenco di tutte le pipeline del programma, nonché avviare e interrompere l’esecuzione della pipeline come faresti nella **Scheda Pipeline**.

Facendo clic sull’icona `i` vengono visualizzati i dettagli sull’ultima o attuale esecuzione della pipeline.

![Dettagli di esecuzione della pipeline](/help/assets/configure-pipelines/pipeline-status.png)

Facendo clic su **Visualizza dettagli**, vieni reindirizzato ai [dettagli dell’esecuzione della pipeline](#view-details).

## Finestra Attività {#activity}

La finestra **Attività** mostra un elenco completo di tutte le esecuzioni di pipeline per il programma selezionato.

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Nella pagina **Panoramica del programma**, fai clic sulla scheda **Attività** per passare alla finestra **Attività**.

1. Qui puoi visualizzare un elenco di tutte le esecuzioni della pipeline del programma, comprese le esecuzioni correnti e quelle precedenti.

Facendo clic sull’icona `i` vengono mostrati i dettagli sull’esecuzione della pipeline selezionata.

![Dettagli di esecuzione della pipeline](/help/assets/configure-pipelines/pipeline-activity.png)

Fai clic su **Visualizza dettagli**, per rivedere i [dettagli dell’esecuzione della pipeline](#view-details).

## Eseguire le pipeline {#running-pipelines}

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.
1. Passa alla scheda **Pipeline** dalla pagina **Panoramica del programma**.
1. Fai clic sul pulsante con i puntini di sospensione accanto alla pipeline eseguita, quindi seleziona **Esegui** dal menu.

   La colonna Stato indica quando inizia l’esecuzione della pipeline.

   Per visualizzare i dettagli dell’esecuzione, fai nuovamente clic sul pulsante con i puntini di sospensione e seleziona **[Visualizza i dettagli](#view-details)**.

   A seconda del tipo di pipeline, può essere possibile annullare l’esecuzione facendo nuovamente clic sul pulsante con i puntini di sospensione e selezionando **Annulla**.

## Modificare pipeline {#editing-pipelines}

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Passa alla scheda **Pipeline** dalla pagina **Panoramica del programma**, fai clic sul pulsante con i puntini di sospensione accanto alla pipeline da modificare e seleziona **Modifica** dal menu.

1. Viene visualizzata la finestra di dialogo **Modifica pipeline di produzione** o **Modifica pipeline di non produzione**. Puoi modificare gli stessi dettagli immessi durante la creazione della pipeline.

   Consulta [Configurazione delle pipeline di produzione](/help/using/production-pipelines.md) e [Configurazione delle pipeline di non produzione](/help/using/non-production-pipelines.md) per informazioni dettagliate sui campi e sulle opzioni di configurazione disponibili per le pipeline.

1. Al termine, fai clic su **Aggiorna**.

>[!NOTE]
>
>Non è possibile modificare una pipeline in esecuzione.

## Eliminare pipeline {#deleting-pipelines}

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Passa alla scheda **Pipeline** dalla pagina **Panoramica del programma** e fai clic sul pulsante con i puntini di sospensione accanto alla pipeline eseguita, quindi seleziona **Esegui** dal menu.

>[!NOTE]
>
>Non è possibile eliminare una pipeline in esecuzione.

## Visualizzare dettagli {#view-details}

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Passa alla scheda **Pipeline** dalla pagina **Panoramica del programma** e fai clic sul pulsante con i puntini di sospensione accanto alla pipeline eseguita, quindi seleziona **Visualizza i dettagli**.

1. L’opzione reindirizza alla pagina dei dettagli della pipeline in esecuzione.

![Dettagli della pipeline](/help/assets/configure-pipelines/pipeline-running-details.png)

Da qui è possibile visualizzare lo stato dei vari passaggi della pipeline e recuperare i registri della build per finalità diagnostiche. Per ulteriori informazioni, consulta il documento [Distribuzione del codice](/help/using/code-deployment.md).

Tutti i passaggi dell’esecuzione di una pipeline vengono visualizzati con quelli non ancora avviati non selezionabili. I passaggi completati mostrano la loro durata.

Una volta completato un passaggio della pipeline, viene presentato un riepilogo.

![Riepilogo del passaggio](/help/assets/configure-pipelines/pipeline-step.png)

Fai clic sul collegamento **Visualizza dettagli** per visualizzare la sezione **Durata**. Questa sezione include la durata media della pipeline in base alla tendenza storica per quel programma.

![Durata](/help/assets/configure-pipelines/duration.png)

Se la pipeline conteneva un passaggio **Scansione del codice** durante il quale sono stati rilevati dei problemi, puoi fare clic sul pulsante **Scarica dettagli** per visualizzare un elenco dei [test di qualità del codice](/help/using/code-quality-testing.md) che non sono stati superati.

![Problemi di qualità del codice](assets/managing-pipelines-code-quality-issues.png)

Nel file CSV, una colonna **Project File Location** (Percorso file di progetto) indica dove si trova il codice in cui è stato riscontrato un problema. Questa colonna contiene un percorso relativo al progetto, mentre la colonna **File Location** (Percorso file) è generata da Maven.

![Dettagli di problemi rilevati dalla scansione del codice del progetto](assets/managing-pipelines-code-quality-details.png)


>[!NOTE]
>
>È possibile visualizzare i dettagli solo per una pipeline in esecuzione o che è stata eseguita almeno una volta.
