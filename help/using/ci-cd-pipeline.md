---
title: Pipeline CI/CD
seo-title: Pipeline CI/CD
description: 'null'
seo-description: Segui questa sezione per informazioni sulla pipeline CI/CD, che gestisce le distribuzioni all'area di visualizzazione e alla produzione in Cloud Manager.
uuid: 763 ddb 24-05 cd -463 f -8 d 72-a 2 e 69 bbe 6 b 7 e
topic-tags: introduction
discoiquuid: 1 cdb 76 eb -1 a 91-4689-8579-0 fa 9 fccc 0592
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Pipeline CI/CD {#ci-cd-pipeline}

## Panoramica della pipeline {#pipeline-overview}

[!UICONTROL Cloud Manager] include un framework di integrazione continua (CI) e distribuzione continua (CD) che consente ai team di implementazione di testare e fornire rapidamente il codice nuovo o aggiornato. Ad esempio, i team di implementazione possono configurare, configurare e avviare una pipeline CI/CD automatizzata che sfrutta le best practice di codifica di Adobe per eseguire una scansione approfondita del codice e garantire la massima qualità del codice.

La pipeline CI/CD automatizza inoltre i processi di testing delle unità e delle prestazioni per migliorare l&#39;efficienza di distribuzione e identificare proattivamente i problemi critici da correggere dopo la distribuzione. I team di implementazione possono accedere a un report completo sulle prestazioni del codice per ottenere visibilità su potenziali impatto sui KPI e sulla convalida di sicurezza critica se il codice viene distribuito in produzione.

## Processo pipeline {#pipeline-process}

Nel diagramma seguente viene illustrato cosa accade una volta che viene attivata una release [!UICONTROL Cloud Manager]. La tabella associata spiega ogni passaggio nel flusso di lavoro.

![](assets/screen_shot_2018-05-30at82457pm.png)

La seguente tabella dettagliata illustra cosa succede durante ogni fase del processo:

| Passaggio processo pipeline | Cosa succede? |
|---|---|
| 1. Avvio di una versione | Un manager distribuzione attiva una versione manualmente, con un Git commit o basato su una pianificazione ricorrente. |
| 2. Crea tag, tag | [!UICONTROL Cloud Manager] crea un tag Git per contrassegnare il rilascio utilizzando un numero di versione generato automaticamente. Ad esempio: 2018.531.245527.0000001222 |
| 3. Creato come versione con versione generata automaticamente | [!UICONTROL Cloud Manager] crea l&#39;applicazione con il numero di versione appena assegnato. |
| 4. Valuta qualità codice | [!UICONTROL Cloud Manager] analizza il codice sorgente e fornisce un riepilogo prima che il codice possa essere distribuito nell&#39;ambiente dell&#39;area di visualizzazione |
| 5. Artefatto delle versioni memorizzato | Gli artefatti del rilascio vengono memorizzati per un utilizzo successivo nei passaggi di distribuzione. |
| 6. Distribuzione automatica di artefatto su AMS AEM Stage | Il artefatto della release viene distribuito nell&#39;ambiente dell&#39;area di visualizzazione. |
| 7. Attivazione di test automatizzati | [!UICONTROL Cloud Manager] esegue i test Prestazioni e Sicurezza sull&#39;artefatto. |
| 8. Distribuzione trigger produzione | Una volta completati i test [!UICONTROL Cloud Manager] automatizzati, viene avviata la distribuzione alla produzione. |
| 9. [!UICONTROL Cloud Manager] Get Artefatti (s) da distribuire | [!UICONTROL Cloud Manager] estrae gli artefatti del rilascio memorizzato. |
| 10. Deplica artefatti alla produzione | Gli artefatti del rilascio vengono distribuiti nell&#39;ambiente Produzione. |

### Come impostare una pipeline CI/CD {#how-to-setup-a-ci-cd-pipeline}

Per ulteriori informazioni sulla configurazione della pipeline, consultate [Configurazione della pipeline](configuring-pipeline.md).

## Qualità Gates {#quality-gates}

Il pipeline CI/CD fornisce i gate di qualità o i criteri di accettazione, che devono essere soddisfatti prima che il codice possa essere spostato dall&#39;ambiente dell&#39;area di visualizzazione all&#39;ambiente di distribuzione. La pipeline contiene tre gate:

* Qualità codice
* Test delle prestazioni
* Test di sicurezza

Per ciascuno di questi tipi di dispositivi, sono identificati tre livelli di problemi:

* **Critici** - problemi identificati dal gate che causano un errore immediato della pipeline.
* **Importante** : i problemi identificati dal gate che provocano la messa in pausa della pipeline. Un manager distribuzione, un manager progetto o un proprietario aziendale può ignorare i problemi, nel qual caso la pipeline procede oppure possono accettare i problemi, nel qual caso la pipeline si interrompe con un errore.
* **Informazioni** - Problemi identificati dal gate che sono forniti esclusivamente a scopo informativo e non hanno alcun impatto sull&#39;esecuzione della pipeline.

Esempio di scansione codice con problemi identificati per il codice:

![](assets/quality-gate-failed.png)

### Come impostare i gate {#how-to-setup-gates}

Consultate **[Configurazione di Gates](configuring-pipeline.md)** per informazioni su come configurare il codice, la qualità e le prestazioni delle prestazioni.
