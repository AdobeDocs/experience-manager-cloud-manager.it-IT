---
title: Gestione delle pipeline
description: Scopri come gestire, modificare, eseguire ed eliminare le pipeline esistenti.
exl-id: e36420d2-57c5-4375-99fb-dd47c1c8bffd
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '848'
ht-degree: 67%

---


# Gestione delle pipeline {#managing-pipelines}

Scopri come gestire, modificare, eseguire ed eliminare le pipeline esistenti.

## Scheda Pipeline {#pipeline-card}

La scheda **Pipeline** della pagina **Panoramica del programma** in Cloud Manager offre una panoramica di tutte le pipeline e del relativo stato corrente.

![Scheda Pipeline in Cloud Manager](/help/assets/configure-pipelines/pipelines-card.png)

Facendo clic sul pulsante con i puntini di sospensione accanto a ogni pipeline è possibile effettuare le seguenti operazioni.

* [Eseguire la pipeline](#running-pipelines)
* [Modificare la pipeline](#editing-pipelines)
* [Eliminare la pipeline](#deleting-pipelines)
* [Visualizza dettagli](#view-details)

Nella parte inferiore dell’elenco delle pipeline sono disponibili le opzioni generali.

* **Aggiungi**: per [aggiungere una nuova pipeline di produzione](/help/using/production-pipelines.md) o [aggiungere una nuova pipeline non di produzione](/help/using/non-production-pipelines.md)
* **Mostra tutto**: porta l’utente alla schermata **Pipeline** per visualizzare tutte le pipeline in una tabella più dettagliata
* **Accedi a dati archivio**: per visualizzare le informazioni necessarie per accedere all’archivio Git di Cloud Manager.
* **Ulteriori informazioni**: consente di accedere alle risorse della documentazione sulla pipeline CI/CD.

## Finestra Pipeline {#pipelines}

La finestra **Pipeline** mostra un elenco completo di tutte le pipeline per il programma selezionato. Questo è utile in quanto presenta informazioni più complete rispetto a quelle disponibili nella [scheda pipeline](#pipeline-card).

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Dalla pagina **Panoramica del programma**, fai clic sulla scheda **Pipeline** per passare alla finestra **Pipeline**.

1. Qui puoi visualizzare un elenco di tutte le pipeline per il programma e avviare e arrestare l&#39;esecuzione della pipeline come faresti nella **scheda Pipeline**.

Facendo clic sull&#39;icona `i` vengono visualizzati i dettagli sull&#39;ultima esecuzione o sull&#39;esecuzione corrente della pipeline.

![Dettagli di esecuzione della pipeline](/help/assets/configure-pipelines/pipeline-status.png)

Facendo clic su **Visualizza dettagli** puoi visualizzare [i dettagli dell&#39;esecuzione della pipeline](#view-details).

## Finestra Attività {#activity}

La finestra **Attività** mostra un elenco completo di tutte le esecuzioni di pipeline per il programma selezionato.

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Dalla pagina **Panoramica programma**, fai clic sulla scheda **Attività** per passare alla finestra **Attività**.

1. Qui puoi visualizzare un elenco di tutte le esecuzioni della pipeline del programma, comprese le esecuzioni correnti e quelle precedenti.

Facendo clic sull&#39;icona `i` vengono visualizzati i dettagli sull&#39;esecuzione della pipeline selezionata.

![Dettagli di esecuzione della pipeline](/help/assets/configure-pipelines/pipeline-activity.png)

Facendo clic su **Visualizza dettagli** puoi visualizzare [i dettagli dell&#39;esecuzione della pipeline](#view-details).

## Esecuzione delle pipeline {#running-pipelines}

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Passa alla scheda **Pipeline** dalla pagina **Panoramica del programma** e fai clic sul pulsante con i puntini di sospensione accanto alla pipeline eseguita, quindi seleziona **Esegui** dal menu.

1. L’esecuzione della pipeline viene avviata ed è indicata dalla colonna **Stato**.

Per visualizzare i dettagli dell’esecuzione, fai nuovamente clic sul pulsante con i puntini di sospensione e seleziona **[Visualizza dettagli](#view-details)**.

A seconda del tipo di pipeline, puoi annullare l’esecuzione facendo nuovamente clic sul pulsante con i puntini di sospensione e selezionando **Annulla**.

## Modifica delle pipeline {#editing-pipelines}

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Passa alla scheda **Pipeline** dalla pagina **Panoramica del programma**, fai clic sul pulsante con i puntini di sospensione accanto alla pipeline da modificare e seleziona **Modifica** dal menu.

1. Viene visualizzata la finestra di dialogo **Modifica pipeline di produzione** o **Modifica pipeline non di produzione**, che consente di modificare i dettagli inseriti durante la creazione della pipeline.

   * Per ulteriori informazioni su tutti i campi e le opzioni di configurazione disponibili per le pipeline, consulta le pagine successive.
      * [Configurazione delle pipeline di produzione](/help/using/production-pipelines.md)
      * [Configurazione delle pipeline non di produzione](/help/using/non-production-pipelines.md)

1. Dopo aver ultimato la modifica della pipeline, fai clic su **Aggiorna**.

>[!NOTE]
>
>Non è possibile modificare una pipeline in esecuzione.

## Eliminazione delle pipeline {#deleting-pipelines}

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Passa alla scheda **Pipeline** dalla pagina **Panoramica del programma** e fai clic sul pulsante con i puntini di sospensione accanto alla pipeline eseguita, quindi seleziona **Elimina** dal menu.

>[!NOTE]
>
>Non è possibile eliminare una pipeline in esecuzione.

## Visualizza dettagli {#view-details}

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Passa alla scheda **Pipeline** dalla pagina **Panoramica del programma** e fai clic sul pulsante con i puntini di sospensione accanto alla pipeline eseguita, quindi seleziona **Visualizza dettagli** dal menu.

1. L’opzione reindirizza alla pagina dei dettagli della pipeline in esecuzione.

![Dettagli della pipeline](/help/assets/configure-pipelines/pipeline-running-details.png)

Da qui puoi vedere lo stato dei vari passaggi della pipeline e recuperare i registri di creazione a scopo diagnostico. Consulta il documento [Distribuzione del codice](/help/using/code-deployment.md) per ulteriori informazioni.

Tutti i passaggi dell’esecuzione di una pipeline vengono visualizzati con quelli non ancora avviati non selezionabili. I passaggi completati mostrano la loro durata.

Una volta completato un passaggio della pipeline, viene presentato un riepilogo.

![Riepilogo del passaggio](/help/assets/configure-pipelines/pipeline-step.png)

Fai clic sul collegamento **Visualizza dettagli** per visualizzare la sezione **Durata**. Ciò include la durata media della pipeline in base alla tendenza storica per quel programma.

![Durata](/help/assets/configure-pipelines/duration.png)

Se la pipeline conteneva un passaggio **Analisi del codice** che ha generato problemi, puoi fare clic sul pulsante **Scarica dettagli** per visualizzare un elenco di [test di qualità del codice](/help/using/code-quality-testing.md) non superati.

![Problemi di qualità del codice](assets/managing-pipelines-code-quality-issues.png)

Nel file CSV, una colonna **Project File Location** (Percorso file di progetto) indica dove si trova il codice in cui è stato riscontrato un problema. Questa colonna contiene un percorso relativo al progetto, mentre la colonna **File Location** (Percorso file) è generata da Maven.

![Dettagli di problemi rilevati dalla scansione del codice del progetto](assets/managing-pipelines-code-quality-details.png)


>[!NOTE]
>
>È possibile visualizzare i dettagli solo per una pipeline in esecuzione o che è stata eseguita almeno una volta.
