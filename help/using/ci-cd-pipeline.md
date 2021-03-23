---
title: Pipeline CI/CD
seo-title: Pipeline CI/CD
description: Panoramica sulla pipeline CI/CD, che gestisce le implementazioni in stage e produzione in Cloud Manager
seo-description: Leggi questa sezione per informazioni sulla pipeline CI/CD, che gestisce le implementazioni per lo stage e la produzione in Cloud Manager.
uuid: 763ddb24-05cd-463f-8d72-a2e69bbe6b7e
topic-tags: introduction
discoiquuid: 1cdb76eb-1a91-4689-8579-0fa9fccc0592
feature: Pipeline CI-CD
translation-type: tm+mt
source-git-commit: c5d32d49782c899d013fcc60b9c4d2b67e9350ae
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 1%

---


# Pipeline CI/CD {#ci-cd-pipeline}

## Panoramica della pipeline {#pipeline-overview}

[!UICONTROL Cloud Manager] include un framework CI (Continuous Integration) e CD (Continuous Delivery) che consente ai team di implementazione di testare e consegnare rapidamente il codice nuovo o aggiornato. Ad esempio, i team di implementazione possono configurare, configurare e avviare una pipeline CI/CD automatizzata che sfrutta le best practice di codifica Adobe per eseguire una scansione approfondita del codice e garantire la massima qualità del codice.

La pipeline CI/CD automatizza inoltre i processi di testing delle unità e delle prestazioni per aumentare l’efficienza dell’implementazione e identificare in modo proattivo i problemi critici che sono costosi da risolvere dopo la distribuzione. I team di implementazione possono accedere a un rapporto completo sulle prestazioni del codice per ottenere visibilità sul potenziale impatto sui KPI e sulle convalide di sicurezza critiche se il codice viene distribuito in produzione.

## Processo della pipeline {#pipeline-process}

Il diagramma seguente illustra cosa accade quando una versione viene attivata in [!UICONTROL Cloud Manager]. La tabella che accompagna viene illustrata ogni fase del flusso di lavoro.

![](assets/screen_shot_2018-05-30at82457pm.png)

La tabella seguente descrive cosa succede in ogni fase del processo:

| Passaggio del processo della pipeline | Cosa succede? |
|---|---|
| 1. Avvia una versione | Un gestore della distribuzione attiva una versione manualmente, con un commit Git o in base a una pianificazione ricorrente. |
| 2. Creare il tag di rilascio | [!UICONTROL Cloud Manager] crea un tag Git per contrassegnare il rilascio utilizzando un numero di versione generato automaticamente. Ad esempio: 2018.531.245527.00000122 |
| 3. Rilascio predefinito con versione generata automaticamente | [!UICONTROL Cloud Manager] crea l&#39;applicazione con il numero di versione appena assegnato. |
| 4. Valutare la qualità del codice | [!UICONTROL Cloud Manager] analizza il codice sorgente e fornisce un riepilogo prima che il codice possa essere distribuito nell’ambiente stage |
| 5. Artifact con versioni memorizzate | Gli artefatti di rilascio vengono memorizzati per un utilizzo successivo nei passaggi di distribuzione. |
| 6. Distribuzione automatica degli artifact in AMS AEM fase | L’artefatto di rilascio viene distribuito nell’ambiente stage. |
| 7. Attivare test automatizzati | [!UICONTROL Cloud Manager] esegue i test Prestazioni e Sicurezza sull&#39;artefatto. |
| 8. Distribuzione di trigger di produzione | Al termine dei test automatizzati [!UICONTROL Cloud Manager] avvia la distribuzione in produzione. |
| 9. [!UICONTROL Cloud Manager] ottiene artifact da distribuire | [!UICONTROL Cloud Manager] richiama gli artefatti di rilascio memorizzati. |
| 10. Distribuire gli artifact alla produzione | Gli artefatti di rilascio vengono distribuiti nell’ambiente di produzione. |

### Come impostare una pipeline CI/CD {#how-to-setup-a-ci-cd-pipeline}

Per ulteriori informazioni sulla configurazione della pipeline, consulta [configurazione della pipeline](configuring-pipeline.md).

## Cancelli di qualità {#quality-gates}

La pipeline CI/CD fornisce gate di qualità, o criteri di accettazione, che devono essere soddisfatti prima che il codice possa essere spostato dall’ambiente stage all’ambiente di distribuzione. La pipeline è composta da tre gate:

* Qualità del codice
* Test delle prestazioni
* Test di sicurezza

Per ciascuno di questi cancelli, esistono tre livelli di problemi identificati:

* **Problemi critici** : problemi identificati dal gate che causano un errore immediato della pipeline.
* **Importante** : problemi identificati dal gate che fanno sì che la pipeline entri in uno stato di pausa. Un manager distribuzione, un project manager o un proprietario business possono ignorare i problemi, nel qual caso la pipeline procede, oppure possono accettare i problemi, nel qual caso la pipeline si interrompe con un errore.
* **Informazioni** : problemi identificati dal gate che sono forniti a scopo puramente informativo e non hanno alcun impatto sull’esecuzione della pipeline.

Di seguito è riportato un esempio di scansione del codice con problemi identificati per il codice:

![](assets/quality-gate-failed.png)

### Come impostare i cancelli {#how-to-setup-gates}

Consulta **[Configurazione di gate](configuring-pipeline.md)** per informazioni dettagliate sulla configurazione del codice, della qualità e delle prestazioni.
