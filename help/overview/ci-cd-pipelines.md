---
title: Pipeline CI/CD
description: Scopri le pipeline CI/CD e come gestiscono le distribuzioni negli ambienti di staging e produzione in Cloud Manager.
exl-id: 7130e5b7-6986-48c8-900c-90f3e4187f91
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: ht
source-wordcount: '552'
ht-degree: 100%

---


# Pipeline CI/CD {#ci-cd-pipeline}

Scopri le pipeline CI/CD e come gestiscono le distribuzioni negli ambienti di staging e produzione in Cloud Manager.

## Panoramica {#overview}

[!UICONTROL Cloud Manager] include un framework di integrazione continua/distribuzione continua (CI/CD) che consente ai team di implementazione di testare e consegnare rapidamente il codice nuovo o aggiornato. Ad esempio, i team di implementazione possono impostare, configurare e avviare una pipeline CI/CD automatizzata che sfrutta le best practice di codifica di Adobe per eseguire un’analisi approfondita del codice e garantirne la massima qualità.

La pipeline CI/CD automatizza inoltre i processi di test delle unità e delle prestazioni per aumentare l’efficienza della distribuzione e per identificare in modo proattivo i problemi critici, costosi da risolvere dopo la distribuzione. I team di implementazione possono accedere a un rapporto completo sulle prestazioni del codice in modo tale da ottenere visibilità sul potenziale impatto sui KPI e sulle convalide di sicurezza critiche se il codice venisse distribuito in produzione.

## Il processo della pipeline {#pipeline-process}

Questo diagramma illustra cosa accade quando una versione viene attivata in [!UICONTROL Cloud Manager] mediante una pipeline.

![Il processo della pipeline](/help/assets/screen_shot_2018-05-30at82457pm.png)

| Passaggio della pipeline | Descrizione |
|---|---|
| 1. Avviare una versione | Un gestore della distribuzione attiva una versione manualmente, con un commit Git o in base a una pianificazione ricorrente. |
| 2. Creare il tag della versione | [!UICONTROL Cloud Manager] crea un tag Git per contrassegnare la versione utilizzando un numero di versione generato automaticamente, ad esempio `2018.531.245527.0000001222`. |
| 3. Creare la versione con versione generata automaticamente | [!UICONTROL Cloud Manager] crea l’applicazione con il numero di versione appena assegnato. |
| 4. Valutare la qualità del codice | [!UICONTROL Cloud Manager] analizza il codice sorgente e fornisce un riepilogo prima che il codice possa essere distribuito nell’ambiente di staging. |
| 5. Artefatti con versione archiviata | Gli artefatti della versione vengono archiviati per un utilizzo successivo nei passaggi di distribuzione. |
| 6. Distribuzione automatica degli artefatti nello staging AMS AEM | L’artefatto della versione viene distribuito nell’ambiente di staging. |
| 7. Attivare i test automatizzati | [!UICONTROL Cloud Manager] esegue test di prestazioni e sicurezza sull’artefatto. |
| 8. Distribuzione dell’attivatore di produzione | Una volta completati i test automatizzati, [!UICONTROL Cloud Manager] avvia la distribuzione in produzione. |
| 9. [!UICONTROL Cloud Manager] ottiene gli artefatti da distribuire | [!UICONTROL Cloud Manager] richiama gli artefatti di rilascio archiviati. |
| 10. Distribuire gli artefatti in produzione | Gli artefatti della versione vengono distribuiti nell’ambiente di produzione. |

### Come impostare una pipeline CI/CD {#how-to-setup-a-ci-cd-pipeline}

Per ulteriori informazioni sulla configurazione della pipeline, consulta i documenti [Configurazione delle pipeline di produzione](/help/using/production-pipelines.md) e [Configurazione delle pipeline non di produzione.](/help/using/non-production-pipelines.md)

## Gate di qualità {#quality-gates}

La pipeline CI/CD fornisce gate di qualità, o criteri di accettazione, che devono essere soddisfatti prima che il codice possa essere spostato dall’ambiente di staging all’ambiente di distribuzione. La pipeline è composta da tre gate:

* Qualità del codice
* Test delle prestazioni
* Test di sicurezza

Per ciascuno di questi gate, è possibile identificare tre livelli di problemi:

* **Critico**: i problemi critici individuati dal gate causano un errore immediato della pipeline.
* **Importante**: i problemi importanti identificati dal gate fanno sì che la pipeline entri in uno stato di pausa. Un Responsabile della distribuzione, un Project Manager o un Proprietario business possono ignorare i problemi, nel qual caso la pipeline procede, oppure possono accettare i problemi, nel qual caso la pipeline si interrompe con un errore.
* **Informazioni**: le problematiche di tipo informazione individuate dal gate sono fornite a scopo puramente informativo e non hanno alcun impatto sull’esecuzione della pipeline.

Questo è un esempio di analisi del codice con problemi identificati.

![Esempio di analisi del codice](/help/assets/quality-gate-failed.png)

### Come impostare i gate {#how-to-setup-gates}

Consulta il documento [Configurazione delle pipeline di produzione](/help/using/production-pipelines.md) per informazioni dettagliate sulla configurazione dei gate di codice, qualità e prestazioni.
