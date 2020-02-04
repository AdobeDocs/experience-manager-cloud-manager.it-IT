---
title: Pipeline CI/CD
seo-title: Pipeline CI/CD
description: 'null'
seo-description: Seguite questa sezione per informazioni sulla pipeline CI/CD, che gestisce le distribuzioni per l'area di visualizzazione e la produzione in Cloud Manager.
uuid: 763ddb24-05cd-463f-8d72-a2e69bbe6b7e
topic-tags: introduction
discoiquuid: 1cdb76eb-1a91-4689-8579-0fa9fccc0592
translation-type: tm+mt
source-git-commit: 2d7b18ea55e2bd5879cf8bd896cafed4d46c0011

---

SHANKARI_TEST_CHANGE
# Pipeline CI/CD {#ci-cd-pipeline}

## Panoramica sulla tubazione {#pipeline-overview}

[!UICONTROL Cloud Manager] include un framework di integrazione continua (CI) e di consegna continua (CD) che consente ai team di implementazione di testare e distribuire rapidamente codice nuovo o aggiornato. Ad esempio, i team di implementazione possono configurare, configurare e avviare una pipeline CI/CD automatizzata che sfrutta le procedure ottimali di codifica Adobe per eseguire una scansione del codice approfondita e garantire la massima qualità del codice.

La pipeline CI/CD automatizza inoltre i processi di testing delle unità e delle prestazioni per aumentare l&#39;efficienza dell&#39;implementazione e identificare proattivamente i problemi critici che sono costosi da risolvere dopo l&#39;implementazione. I team di implementazione possono accedere a un report completo sulle prestazioni del codice per ottenere visibilità sul potenziale impatto sui KPI e sulle convalide di sicurezza critiche se il codice viene distribuito in produzione.

## Processo pipeline {#pipeline-process}

Il diagramma seguente illustra cosa accade quando una versione viene attivata in [!UICONTROL Cloud Manager]. La tabella di accompagnamento illustra ogni passaggio del flusso di lavoro.

![](assets/screen_shot_2018-05-30at82457pm.png)

Nella tabella seguente sono descritti in dettaglio gli eventi in corso in ogni fase del processo:

| Passaggio processo pipeline | Cosa sta succedendo? |
|---|---|
| 1. Avviare una versione | Un gestore della distribuzione attiva una release manualmente, con un commit Git o in base a una pianificazione periodica. |
| 2. Crea tag di rilascio | [!UICONTROL Cloud Manager] crea un tag Git per contrassegnare il rilascio utilizzando un numero di versione generato automaticamente. Ad esempio: 2018.531.245527.00000122 |
| 3. Costruito come versione con versione generata automaticamente | [!UICONTROL Cloud Manager] crea l&#39;applicazione con il numero di versione assegnato di recente. |
| 4. Valutazione qualità codice | [!UICONTROL Cloud Manager] analizza il codice sorgente e fornisce un riepilogo prima che il codice possa essere distribuito nell’ambiente del passaggio |
| 5. Artefatti con versione memorizzati | Gli artefatti relativi alla versione vengono memorizzati per un utilizzo successivo nei passaggi di distribuzione. |
| 6. Distribuzione automatica di artifact in AMS AEM Stage | L’artifact della versione viene distribuito nell’ambiente di visualizzazione. |
| 7. Attiva test automatici | [!UICONTROL Cloud Manager] esegue i test Prestazioni e Sicurezza sull&#39;artifact. |
| 8. Implementazione trigger produzione | Al termine dei test automatizzati [!UICONTROL Cloud Manager] viene avviata la distribuzione in produzione. |
| 9. ottiene gli [!UICONTROL Cloud Manager] artefatti da distribuire | [!UICONTROL Cloud Manager] richiama gli artefatti di rilascio memorizzati. |
| 10. Distribuisci artefatti alla produzione | Gli artefatti di rilascio vengono distribuiti nell&#39;ambiente di produzione. |

### Come impostare una tubazione CI/CD {#how-to-setup-a-ci-cd-pipeline}

Per ulteriori informazioni sulla configurazione della pipeline, vedere [Configurazione della pipeline](configuring-pipeline.md).

## Gate di qualità {#quality-gates}

La pipeline CI/CD fornisce dei cancelli di qualità, o criteri di accettazione, che devono essere soddisfatti prima che il codice possa essere spostato dall’ambiente di sviluppo all’ambiente di distribuzione. La conduttura prevede tre porte:

* Qualità del codice
* Test delle prestazioni
* Test di protezione

Per ciascuna di queste porte, sono stati individuati tre livelli di problemi:

* **Critiche** - problemi individuati dal gate che causano un immediato fallimento della conduttura.
* **Importante** - problemi identificati dal gate che causano l&#39;ingresso della pipeline in stato di pausa. Un gestore di distribuzione, un project manager o un proprietario aziendale possono ignorare i problemi, nel qual caso la pipeline procede, oppure accettare i problemi, nel qual caso la pipeline si interrompe con un errore.
* **Informazioni** - questioni individuate dalla porta che sono fornite esclusivamente a fini informativi e non hanno alcun impatto sull&#39;esecuzione della conduttura.

Di seguito è riportato un esempio di analisi del codice con problemi identificati per il codice:

![](assets/quality-gate-failed.png)

### Come impostare i cancelli {#how-to-setup-gates}

Consultate **[Configurazione dei cancelli](configuring-pipeline.md)**per informazioni dettagliate sulla configurazione del codice, della qualità e delle prestazioni.
