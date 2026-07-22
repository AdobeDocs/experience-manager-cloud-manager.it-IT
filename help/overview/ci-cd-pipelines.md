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
source-git-commit: f83ddaa74a656abd2328cd3969ff0cc10b79d729
workflow-type: tm+mt
source-wordcount: 1085
ht-degree: 50%

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

### Origini del codice {#code-sources}

Le pipeline possono anche differire per il tipo di codice che distribuiscono, oltre che per la produzione e la non produzione.

* **[Pipeline full stack](#full-stack-pipeline)** - Distribuisci il codice completo dell&#39;applicazione AEM con le configurazioni HTTPD/Dispatcher.
* **[Pipeline di configurazione a livello web](#web-tier-config-pipelines)** - Distribuisci solo configurazioni HTTPD/Dispatcher.

### Pipeline full stack {#full-stack-pipeline}

Le pipeline full stack distribuiscono il codice completo dell’applicazione AEM nel runtime di AEM e, per impostazione predefinita, anche le configurazioni a livello web.

Si applicano le seguenti restrizioni.

* Per configurare o eseguire le pipeline è necessario che un utente con il ruolo **Responsabile dell&#39;implementazione** abbia eseguito l&#39;accesso.
* In qualsiasi momento può essere presente una sola pipeline full stack per ogni ambiente.

Di seguito viene descritto il modo in cui la pipeline full stack interagisce con una [pipeline di configurazione a livello web](#web-tier-config-pipelines).

* La pipeline full stack per un ambiente ignora la configurazione Dispatcher se esiste la pipeline di configurazione a livello web corrispondente.
* Se la pipeline di configurazione a livello web corrispondente per l’ambiente non esiste, l’utente può includere o ignorare la configurazione Dispatcher durante la configurazione della pipeline full stack.

Le pipeline full stack possono essere di qualità del codice o di distribuzione.

#### Configurare le pipeline full stack {#configure-full-stack}

Consulta [Aggiungere una pipeline di produzione](/help/using/production-pipelines.md#full-stack-code).
Consulta [Aggiungere una pipeline non di produzione](/help/using/non-production-pipelines.md#add-non-production-pipeline).

### Pipeline di configurazione a livello web {#web-tier-config-pipelines}

Le pipeline di configurazione a livello web consentono la distribuzione esclusiva della configurazione HTTPD/Dispatcher nel runtime di AEM, separandola dalle altre modifiche al codice. Si tratta di una pipeline semplificata che offre agli utenti che desiderano implementare solo le modifiche di configurazione Dispatcher un mezzo efficiente per farlo rapidamente.

>[!TIP]
>
>Le pipeline di configurazione a livello web consentono di memorizzare la configurazione web nella stessa posizione di origine o in una posizione diversa della pipeline full stack, a seconda di ciò che si adatta meglio alla struttura del progetto.

Si applicano le seguenti restrizioni.

* Per configurare o eseguire le pipeline è necessario che un utente con il ruolo **Responsabile dell&#39;implementazione** abbia eseguito l&#39;accesso.
* In qualsiasi momento può essere presente una sola pipeline di configurazione a livello web per ogni ambiente.
* L’utente non può configurare una pipeline di configurazione a livello web quando è in esecuzione la pipeline full stack corrispondente.

Di seguito viene descritto il modo in cui la pipeline di configurazione a livello web interagisce con la [pipeline full stack](#full-stack-pipeline).

* Se per un ambiente non è impostata una pipeline di configurazione a livello web, l’utente può scegliere di includere o ignorare la configurazione di Dispatcher durante la configurazione della pipeline full stack.
* Una volta configurata una pipeline di configurazione a livello web per un ambiente, la corrispondente pipeline full stack (se presente) ignora la configurazione Dispatcher durante l’esecuzione e la distribuzione.
* Dopo l’eliminazione di una pipeline di configurazione a livello web, la corrispondente pipeline full stack (se presente) viene reimpostata per distribuire le configurazioni di Dispatcher durante l’esecuzione.

>[!NOTE]
>
>Per i programmi AMS con distribuzione blu-verde abilitata, gli aggiornamenti a livello web utilizzano la distribuzione continua per impostazione predefinita. Utilizza una pipeline full stack se hai bisogno di una distribuzione blu-verde per le modifiche a livello web.

#### Configurare le pipeline a livello web {#configure-web-tier}

Consulta [Aggiungere una pipeline di produzione](/help/using/production-pipelines.md#web-tier-config).
Consulta [Aggiungere una pipeline non di produzione](/help/using/non-production-pipelines.md#add-non-production-pipeline).

### Build più veloci con Smart Build {#use=smart-build}

Cloud Manager utilizza ora una strategia di compilazione ottimizzata denominata **Smart Build**, che utilizza la memorizzazione nella cache a livello di modulo per accelerare il processo di compilazione. Durante ogni build, vengono rigenerati solo i moduli che sono stati modificati, mentre i moduli non modificati vengono riutilizzati dalla cache.

Smart Build è disponibile per le pipeline di distribuzione di qualità del codice e full stack (sviluppo, staging, produzione).

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
* **Importante**: i problemi importanti identificati dal gate fanno sì che la pipeline entri in uno stato di pausa. Un Responsabile dell’implementazione, un Project Manager o un lead di business può ignorare i problemi, consentendo alla pipeline di procedere. In alternativa, possono accettare i problemi, causando l’interruzione della pipeline con un errore.
* **Informazioni**: le problematiche di tipo informazione individuate dal gate sono fornite a scopo puramente informativo e non hanno alcun impatto sull’esecuzione della pipeline.

L’esempio seguente è un’analisi del codice con problemi identificati.

![Esempio di analisi del codice](/help/assets/quality-gate-failed.png)

### Come impostare i gate {#how-to-setup-gates}

Consulta il documento [Configurazione delle pipeline di produzione](/help/using/production-pipelines.md) per informazioni dettagliate sulla configurazione dei gate di codice, di qualità e prestazioni.
