---
title: Gestione delle pipeline
description: Scopri come gestire le pipeline esistenti, modificarle, eseguirle ed eliminarle.
exl-id: e36420d2-57c5-4375-99fb-dd47c1c8bffd
source-git-commit: 99325c28c379103db2ba4c19bb6d206849c6e126
workflow-type: ht
source-wordcount: '517'
ht-degree: 100%

---


# Gestione delle pipeline {#managing-pipelines}

Scopri come gestire le pipeline esistenti, modificarle, eseguirle ed eliminarle.

## Scheda pipeline {#pipeline-card}

La scheda **Pipeline** nella pagina **Panoramica del programma** in Cloud Manager offre una panoramica di tutte le pipeline e del loro stato corrente.

![Scheda pipeline in Cloud Manager](/help/assets/configure-pipelines/pipelines-card.png)

Facendo clic sul pulsante con i puntini di sospensione accanto a ciascuna pipeline puoi effettuare le seguenti operazioni.

* [Eseguire la pipeline](#running-pipelines)
* [Modificare la pipeline](#editing-pipelines)
* [Eliminare la pipeline](#deleting-pipelines)
* [Visualizza dettagli](#view-details)

Nella parte inferiore dell’elenco delle pipeline sono disponibili le opzioni generali.

* **Aggiungi**: per [aggiungere una nuova pipeline di produzione](/help/using/production-pipelines.md) o [aggiungere una nuova pipeline non di produzione](/help/using/non-production-pipelines.md)
* **Mostra tutto**: porta l’utente alla schermata **Pipeline** per visualizzare tutte le pipeline in una tabella più dettagliata
* **Accedi a dati archivio**: per visualizzare le informazioni necessarie per accedere all’archivio Git di Cloud Manager.
* **Ulteriori informazioni**: per passare alle risorse della documentazione della pipeline CI/CD.

## Eseguire la pipeline {#running-pipelines}

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Passa alla scheda **Pipeline** dalla pagina **Panoramica del programma**, fai clic sul pulsante dei puntini di sospensione accanto alla pipeline eseguita e seleziona **Esegui** dal menu.

1. Viene avviata l’esecuzione della pipeline ed è indicata dalla colonna **Stato**.

Per visualizzare i dettagli dell’esecuzione, fai nuovamente clic sul pulsante con i puntini di sospensione e seleziona **[Visualizza i dettagli.](#view-details)**

A seconda del tipo di pipeline, può essere possibile annullare l’esecuzione facendo nuovamente clic sul pulsante con i puntini di sospensione e selezionando **Annulla**.

## Modificare le pipeline {#editing-pipelines}

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Passa alla scheda **Pipeline** dalla pagina **Panoramica del programma**, fai clic sul pulsante dei puntini di sospensione accanto alla pipeline da modificare e seleziona **Modifica** dal menu.

1. Viene visualizzata la finestra di dialogo **Modifica pipeline di produzione** o **Modifica pipeline non di produzione** che consente di modificare gli stessi dettagli immessi durante la creazione della pipeline.

   * Per i dettagli su tutti i campi e le opzioni di configurazione disponibili per le pipeline, vedi le pagine seguenti.
      * [Configurazione delle pipeline di produzione](/help/using/production-pipelines.md)
      * [Configurazione di pipeline non di produzione](/help/using/non-production-pipelines.md)

1. Una volta completata la modifica della pipeline, fai clic su **Aggiorna**.

>[!NOTE]
>
>Non è possibile modificare una pipeline in esecuzione.

## Eliminare le pipeline {#deleting-pipelines}

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Passa alla scheda **Pipeline** dalla pagina **Panoramica del programma**, fai clic sul pulsante dei puntini di sospensione accanto alla pipeline eseguita e seleziona **Elimina** dal menu.

>[!NOTE]
>
>Non è possibile eliminare una pipeline in esecuzione.

## Visualizza dettagli {#view-details}

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Passa alla scheda **Pipeline** dalla pagina **Panoramica del programma**, fai clic sul pulsante dei puntini di sospensione accanto alla pipeline eseguita e seleziona **Visualizza dettagli** dal menu.

1. Viene visualizzata la pagina dei dettagli della pipeline in esecuzione.

![Dettagli della pipeline](/help/assets/configure-pipelines/pipeline-running-details.png)

Da qui puoi vedere lo stato dei vari passaggi della pipeline e recuperare i registri di creazione a scopo diagnostico. Consulta il documento [Distribuzione del codice](/help/using/code-deployment.md) per ulteriori informazioni.

>[!NOTE]
>
>È possibile visualizzare solo i dettagli di una pipeline in esecuzione o eseguita almeno una volta.
