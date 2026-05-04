---
title: Pipeline CI/CD
description: Scopri le pipeline CI/CD e come gestiscono le implementazioni negli ambienti di staging e di produzione in Cloud Manager.
exl-id: 7130e5b7-6986-48c8-900c-90f3e4187f91
TQID: https://experienceleague.adobe.com/BwkZH2MIbXrzSxf0yk9yeDZZIpw7-Ldue-OPQPkWrdg
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
  - id: ff09c71c-26a9-449a-85f8-2aeb8ce96100
subfeature_v2:
  - id: c14b2f98-ee16-4c49-b87b-919c91b01d9d
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 50eb58593d7f78492fd384c99c3727c5f731c989
workflow-type: tm+mt
source-wordcount: 639
ht-degree: 81%

---

# Pipeline CI/CD {#ci-cd-pipeline}

Scopri le pipeline CI/CD e come gestiscono le implementazioni negli ambienti di staging e di produzione in Cloud Manager.

## Panoramica {#overview}

[!UICONTROL Cloud Manager] include un framework di integrazione continua/distribuzione continua (CI/CD) che consente ai team di implementazione di testare e consegnare rapidamente il codice nuovo o aggiornato. I team di implementazione possono impostare, configurare e avviare una pipeline CI/CD automatizzata. Questa pipeline segue alcune best practice di codifica Adobe per eseguire un’analisi completa del codice e garantirne la massima qualità.

La pipeline CI/CD automatizza inoltre i processi di test delle unità e delle prestazioni per aumentare l’efficienza della distribuzione e per identificare in modo proattivo i problemi critici, costosi da risolvere dopo la distribuzione. I team di implementazione possono accedere a un rapporto completo sulle prestazioni del codice in modo tale da ottenere visibilità sul potenziale impatto sui KPI e sulle convalide di sicurezza critiche se il codice venisse distribuito in produzione.

## Informazioni sul processo della pipeline {#pipeline-process}

Il seguente diagramma illustra cosa accade quando una versione viene attivata in [!UICONTROL Cloud Manager] mediante una pipeline.

![Il processo della pipeline](/help/assets/screen_shot_2018-05-30at82457pm.png)

| Passaggio della pipeline | Descrizione |
| --- | --- |
| &#x200B;1. Avviare una versione | Un responsabile della distribuzione attiva una versione manualmente, con un commit Git, o in base a una pianificazione ricorrente. |
| &#x200B;2. Creare un tag di versione | [!UICONTROL Cloud Manager] crea un tag Git per contrassegnare la versione utilizzando un numero di versione generato automaticamente, ad esempio `2018.531.245527.0000001222`. |
| &#x200B;3. Creato come versione con versione generata automaticamente | [!UICONTROL Cloud Manager] crea l’applicazione con il numero di versione appena assegnato. |
| &#x200B;4. Valuta la qualità del codice | [!UICONTROL Cloud Manager] analizza il codice sorgente e fornisce un riepilogo prima che il codice possa essere distribuito nell’ambiente di staging. |
| &#x200B;5. Artefatti con versione archiviati | Gli artefatti della versione vengono archiviati per un utilizzo successivo nei passaggi di implementazione. |
| &#x200B;6. Distribuzione automatica degli artefatti nello staging AMS AEM | L’artefatto della versione viene distribuito nell’ambiente di staging. |
| &#x200B;7. Attiva test automatizzati | [!UICONTROL Cloud Manager] esegue test di prestazioni e sicurezza sull’artefatto. |
| &#x200B;8. Distribuzione del trigger di produzione | Una volta completati i test automatizzati, [!UICONTROL Cloud Manager] avvia la distribuzione in produzione. |
| &#x200B;9. [!UICONTROL Cloud Manager] ottiene gli artefatti da distribuire | [!UICONTROL Cloud Manager] richiama gli artefatti di rilascio archiviati. |
| &#x200B;10. Distribuire gli artefatti in produzione | Gli artefatti della versione vengono implementati nell’ambiente di produzione. |

### Build più veloci con Smart Build {#use=smart-build}

Cloud Manager utilizza ora una strategia di compilazione ottimizzata denominata **Smart Build**, che utilizza la memorizzazione nella cache a livello di modulo per velocizzare il processo di compilazione. Durante ogni build, vengono rigenerati solo i moduli che sono stati modificati, mentre i moduli non modificati vengono riutilizzati dalla cache.

Smart Build è disponibile solo per le pipeline di distribuzione di Code Quality e Dev Full Stack.

Consulta [Aggiungere una pipeline non di produzione](/help/using/non-production-pipelines.md#add-non-production-pipeline) e [Informazioni sull&#39;utilizzo di Smart Build in una pipeline non di produzione](/help/using/non-production-pipelines.md#about-smart-build).


### Come impostare una pipeline CI/CD {#how-to-setup-a-ci-cd-pipeline}

Per ulteriori informazioni sulla configurazione della pipeline, consulta i documenti [Configurazione delle pipeline di produzione](/help/using/production-pipelines.md) e [Configurazione delle pipeline non di produzione](/help/using/non-production-pipelines.md).

## Gate di qualità {#quality-gates}

La pipeline CI/CD fornisce gate di qualità, o criteri di accettazione, che devono essere soddisfatti prima che il codice possa essere spostato dall’ambiente di staging all’ambiente di distribuzione. La pipeline è composta da tre gate:

* Qualità del codice
* Test delle prestazioni
* Test di sicurezza

Per ciascuno di questi gate, è possibile identificare tre livelli di problemi:

* **Critico**: i problemi critici individuati dal gate causano un errore immediato della pipeline.
* **Importante**: i problemi importanti identificati dal gate fanno sì che la pipeline entri in uno stato di pausa. Un Responsabile della distribuzione, un Project manager o un Proprietario business può ignorare i problemi, consentendo alla pipeline di procedere. In alternativa, possono accettare i problemi, causando l’interruzione della pipeline con un errore.
* **Informazioni**: le problematiche di tipo informazione individuate dal gate sono fornite a scopo puramente informativo e non hanno alcun impatto sull’esecuzione della pipeline.

L’esempio seguente è un’analisi del codice con problemi identificati.

![Esempio di analisi del codice](/help/assets/quality-gate-failed.png)

### Come impostare i gate {#how-to-setup-gates}

Consulta il documento [Configurazione delle pipeline di produzione](/help/using/production-pipelines.md) per informazioni dettagliate sulla configurazione dei gate di codice, di qualità e prestazioni.
