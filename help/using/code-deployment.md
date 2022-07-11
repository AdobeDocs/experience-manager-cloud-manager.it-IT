---
title: Distribuzione del codice
description: Scopri come distribuire il codice e cosa succede in Cloud Manager quando lo fai.
exl-id: 3d6610e5-24c2-4431-ad54-903d37f4cdb6
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '1609'
ht-degree: 0%

---


# Distribuzione del codice {#code-deployment}

Scopri come distribuire il codice e cosa succede in Cloud Manager quando lo fai.

## Distribuzione del codice con Cloud Manager {#deploying-code-with-cloud-manager}

Una volta configurata la pipeline di produzione, inclusi l’archivio e gli ambienti necessari, puoi distribuire il codice.

1. Fai clic su **Distribuzione** da Cloud Manager per avviare il processo di distribuzione.

   ![Pulsante Distribuisci](/help/assets/Deploy1.png)

1. La **Esecuzione della pipeline** viene visualizzato lo schermo. Fai clic su **Crea** per avviare il processo.

   ![Pulsante Genera](/help/assets/Deploy2.png)

Il processo di compilazione avvia il processo di distribuzione del codice, inclusi i seguenti passaggi:

* Distribuzione delle fasi
* Test della fase
* Distribuzione di produzione

Puoi rivedere i passaggi da vari processi di distribuzione visualizzando i registri o rivedendo i risultati per i criteri di test.

## Passaggi di distribuzione {#deployment-steps}

Durante ogni fase della distribuzione si verificano diverse azioni, descritte in questa sezione. Vedi la sezione [Dettagli del processo di distribuzione](#deployment-process) per informazioni tecniche su come il codice stesso viene distribuito dietro le quinte.

### Passaggio di implementazione della fase {#stage-deployment}

La **Distribuzione delle fasi** Il passaggio include le azioni seguenti:

* **Convalida**: Questo passaggio assicura che la pipeline sia configurata per utilizzare le risorse attualmente disponibili, ad esempio che il ramo configurato esista e che gli ambienti siano disponibili.
* **Build &amp; Unit Testing**: Questo passaggio esegue un processo di compilazione containerizzato. Vedere il documento [Ambiente di creazione](/help/getting-started/build-environment.md) per i dettagli.
* **Scansione del codice**: Questo passaggio valuta la qualità del codice dell&#39;applicazione. Vedere il documento [Risultati dei test](/help/using/code-quality-testing.md) per informazioni dettagliate sul processo di test.
* **Distribuisci su Stage**

![Distribuzione delle fasi](/help/assets/Stage_Deployment1.png)

### Passaggio di test della fase {#stage-testing}

La **Test della fase** Il passaggio include le azioni seguenti:

* **Test di sicurezza**: Questo passaggio valuta l’impatto sulla sicurezza del codice nell’ambiente AEM. Vedere il documento [Risultati dei test](/help/using/code-quality-testing.md) per informazioni dettagliate sul processo di test.
   * **Test delle prestazioni**: Questo passaggio valuta le prestazioni del codice. Vedi [Risultati dei test](/help/using/code-quality-testing.md) per informazioni dettagliate sul processo di test.

   ![Test della fase](/help/assets/Stage_Testing1.png)

### Passaggio all&#39;implementazione della produzione {#production-deployment}

La **Distribuzione di produzione** , include le azioni seguenti:

* **Domanda di approvazione**
   * Questa opzione è abilitata durante la configurazione della pipeline.
   * Utilizzando questa opzione, puoi pianificare la distribuzione di produzione oppure fare clic su **Ora** per eseguire immediatamente la distribuzione di produzione.
* **Pianificazione distribuzione produzione**
   * Questa opzione è abilitata durante la configurazione della pipeline.
   * La data e l’ora pianificate vengono specificate in termini di fuso orario dell’utente.
      ![Pianificazione della distribuzione](/help/assets/Production_Deployment1.png)
* **Supporto CSE** (se attivato)
* **Distribuzione in produzione**

![Distribuzione di produzione](/help/assets/Prod_Deployment1.png)

Una volta completata la distribuzione, il codice si trova nel relativo ambiente di destinazione e puoi visualizzare i registri.

![Implementazione completata](/help/assets/Production_Deployment2.png)

## Timeout {#timeouts}

I seguenti passaggi si interrompono se rimangono in attesa del feedback degli utenti:

| Incremento | Timeout |
|--- |--- |
| Test della qualità del codice | 14 giorni |
| Test di sicurezza | 14 giorni |
| Test delle prestazioni | 14 giorni |
| Domanda di approvazione | 14 giorni |
| Pianificazione distribuzione produzione | 14 giorni |
| Supporto CSE | 14 giorni |

## Dettagli del processo di distribuzione {#deployment-process}

Cloud Manager carica tutti i file target/*.zip prodotti dal processo di compilazione in una posizione di archiviazione. Questi artefatti vengono recuperati da questa posizione durante le fasi di distribuzione della pipeline.

Quando Cloud Manager viene implementato in topologie non di produzione, l’obiettivo è quello di completare l’implementazione il più rapidamente possibile e, pertanto, gli artefatti vengono distribuiti simultaneamente su tutti i nodi come segue:

1. Cloud Manager determina se ogni artefatto è un pacchetto AEM o dispatcher.
1. Cloud Manager rimuove tutti i dispatcher dal load balancer per isolare l’ambiente durante la distribuzione.

   * Se non è configurato diversamente, è possibile saltare le modifiche del load balancer nelle implementazioni di sviluppo e staging, ad esempio per l’ambiente di sviluppo, scollegare e allegare i passaggi sia nelle pipeline non di produzione che nell’ambiente di staging la pipeline di produzione.

   ![Salta il load balancer](/help/assets/load_balancer.png)

   >[!NOTE]
   >
   >Questa funzione dovrebbe essere utilizzata principalmente da 1-1-1 clienti.

1. Ciascun artefatto AEM viene distribuito a ogni istanza AEM tramite API di Gestione pacchetti, con dipendenze dei pacchetti che determinano l’ordine di distribuzione.

   * Per ulteriori informazioni su come utilizzare i pacchetti per installare nuove funzionalità, trasferire contenuti tra le istanze e eseguire il backup del contenuto dell’archivio, consulta il documento [Gestione pacchetti.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager.html)
   >[!NOTE]
   >
   >Tutti gli artefatti AEM vengono distribuiti sia all’autore che agli editori. Le modalità di esecuzione devono essere utilizzate quando sono necessarie configurazioni specifiche per il nodo. Per ulteriori informazioni su come le modalità di esecuzione ti consentono di regolare la tua istanza di AEM per uno scopo specifico, fai riferimento al [Esegui modalità sezione del documento Distribuzione AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html#runmodes)

1. L’artefatto del dispatcher viene distribuito a ciascun dispatcher come segue:

   1. Le configurazioni correnti vengono sottoposte a backup e copiate in una posizione temporanea.
   1. Tutte le configurazioni vengono eliminate tranne i file immutabili. Consulta il documento [Configurazioni del Dispatcher](/help/getting-started/dispatcher-configurations.md) per ulteriori dettagli. Questo cancella le directory per garantire che non vengano lasciati indietro i file orfani.
   1. L’artefatto viene estratto nel `httpd` directory. I file immutabili non vengono sovrascritti. Eventuali modifiche apportate ai file immutabili nell’archivio Git verranno ignorate al momento della distribuzione. Questi file sono di base del framework del dispatcher AMS e non possono essere modificati.
   1. Apache esegue un test di configurazione. Se non viene rilevato alcun errore, il servizio viene ricaricato. Se si verifica un errore, le configurazioni vengono ripristinate dal backup, il servizio viene ricaricato e l&#39;errore viene riportato a Cloud Manager.
   1. Ogni percorso specificato nella configurazione della pipeline viene invalidato o scaricato dalla cache del dispatcher.

   >[!NOTE]
   >
   >Cloud Manager prevede che l’artefatto del dispatcher contenga l’intero set di file. Tutti i file di configurazione del dispatcher devono essere presenti nell’archivio Git. File o cartelle mancanti causeranno un errore di distribuzione.

1. Dopo la corretta distribuzione di tutti i pacchetti AEM e dispatcher a tutti i nodi, i dispatcher vengono aggiunti nuovamente al load balancer e la distribuzione è completa.

   >[!NOTE]
   >
   >è possibile saltare le modifiche del load balancer nelle implementazioni di sviluppo e staging, ovvero per l’ambiente di sviluppo, scollegare e allegare i passaggi sia nelle pipeline non di produzione che nell’ambiente di staging della pipeline di produzione.

### Fase di implementazione a produzione {#deployment-production-phase}

Il processo di distribuzione nelle topologie di produzione è leggermente diverso per ridurre al minimo l’impatto sui visitatori AEM sito.

Le distribuzioni di produzione seguono generalmente gli stessi passaggi indicati in precedenza, ma in modo continuo:

1. Distribuisci pacchetti AEM per l’authoring.
1. Scollega dispatcher1 dal load balancer.
1. Distribuisci pacchetti AEM a publish1 e il pacchetto dispatcher a dispatcher1 in parallelo, svuota la cache del dispatcher.
1. Rimetti dispatcher1 nel load balancer.
1. Una volta che dispatcher1 è tornato in servizio, scollega dispatcher2 dal load balancer.
1. Distribuisci pacchetti AEM a publish2 e il pacchetto dispatcher a dispatcher2 in parallelo, svuota la cache del dispatcher.
1. Rimetti dispatcher2 nel load balancer.

Questo processo continua fino a quando la distribuzione non raggiunge tutti gli editori e i dispatcher nella topologia.

## Modalità di esecuzione della tubazione di emergenza {#emergency-pipeline}

In situazioni critiche, i clienti di Adobe Managed Services potrebbero dover implementare modifiche al codice nei rispettivi ambienti di stage e produzione senza attendere l’esecuzione di un ciclo di test completo di Cloud Manager.

Per risolvere queste situazioni, la pipeline di produzione di Cloud Manager può essere eseguita in modalità di emergenza. Quando si utilizza questa modalità, i passaggi del test di sicurezza e prestazioni non vengono eseguiti. Tutti gli altri passaggi, compresi eventuali passaggi di approvazione configurati, vengono eseguiti come nella normale modalità di esecuzione della pipeline.

>[!NOTE]
>
>La funzione della modalità di esecuzione della pipeline di emergenza viene attivata a livello di programma dai tecnici del successo del cliente.

### Utilizzo della modalità di esecuzione della pipeline di emergenza {#using-emergency-pipeline}

Quando si avvia un’esecuzione della pipeline di produzione, se la funzione della modalità di esecuzione della pipeline di emergenza è stata attivata per il programma, è possibile avviare l’esecuzione in modalità normale o di emergenza da una finestra di dialogo.

![Eseguire le opzioni della pipeline](/help/assets/execution-emergency1.png)

Quando si visualizza la pagina dei dettagli di esecuzione della pipeline per un’esecuzione in modalità di emergenza, le breadcrumb nella parte superiore dello schermo mostrano un indicatore dell’esecuzione della pipeline in modalità di emergenza.

![Breadcrumb in modalità di emergenza](/help/assets/execution-emergency2.png)

L’esecuzione di una pipeline in modalità di emergenza può essere eseguita anche tramite l’API di Cloud Manager o CLI. Per avviare un&#39;esecuzione in modalità di emergenza, invia una `PUT` richiesta all’endpoint di esecuzione della pipeline con il parametro query `?pipelineExecutionMode=EMERGENCY` oppure, quando si utilizza CLI:

```
$ aio cloudmanager:pipeline:create-execution PIPELINE_ID --emergency
```

## Esegui nuovamente una distribuzione di produzione {#re-execute-deployment}

La riesecuzione del passaggio di distribuzione di produzione è disponibile per le esecuzioni in cui il passaggio di distribuzione di produzione è stato completato. Il tipo di completamento non è importante. La distribuzione potrebbe avere esito positivo (solo per i programmi AMS), essere annullata o non essere riuscita. Il caso di utilizzo principale è il caso in cui il passaggio di distribuzione della produzione non è riuscito per motivi transitori. La nuova esecuzione crea una nuova esecuzione utilizzando la stessa pipeline. Questa nuova esecuzione consiste in tre fasi:

1. **Passaggio di convalida** - Si tratta essenzialmente della stessa convalida che si verifica durante una normale esecuzione della pipeline.
1. **Passaggio di compilazione** - Nel contesto di una nuova esecuzione, il passaggio di compilazione copia gli artefatti e non esegue effettivamente un nuovo processo di compilazione.
1. **Passaggio di distribuzione della produzione** - Questa opzione utilizza la stessa configurazione e le stesse opzioni del passaggio di distribuzione di produzione in una normale esecuzione della pipeline.

Il passaggio della build può essere etichettato in modo diverso nell’interfaccia utente per indicare che sta copiando gli artefatti, non sta ricostruendo.

![Riesecuzione](/help/assets/Re-deploy.png)

### Limitazioni  {#limitations}

* La riesecuzione del passaggio di distribuzione di produzione è disponibile solo per l’ultima esecuzione.
* La riesecuzione non è disponibile per le esecuzioni di rollback o le esecuzioni di aggiornamenti push.
* Se l’ultima esecuzione non è riuscita in un qualsiasi punto prima della fase di distribuzione della produzione, non è possibile eseguire nuovamente l’esecuzione.

### Identificazione di una nuova esecuzione {#identifying}

Per identificare se un’esecuzione è un’esecuzione di nuova esecuzione, il `trigger` può essere esaminato. Il suo valore sarà `RE_EXECUTE`.

### Attivazione di una nuova esecuzione {#triggering}

Per attivare una nuova esecuzione, è necessario `PUT` è necessario effettuare la richiesta al collegamento HAL `http://ns.adobe.com/adobecloud/rel/pipeline/reExecute` sullo stato del passaggio di distribuzione di produzione. Se questo collegamento è presente, l’esecuzione può essere riavviata da quel passaggio. Se è assente, l’esecuzione non può essere riavviata da quel passaggio. Questo collegamento sarà sempre presente solo nel passaggio di distribuzione della produzione

```Javascript
 {
  "_links": {
    "http://ns.adobe.com/adobecloud/rel/pipeline/logs": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/logs",
      "templated": false
    },
    "http://ns.adobe.com/adobecloud/rel/pipeline/reExecute": {
      "href": "/api/program/4/pipeline/1/execution?stepId=2983530",
      "templated": false
    },
    "http://ns.adobe.com/adobecloud/rel/pipeline/metrics": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/metrics",
      "templated": false
    },
    "self": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530",
      "templated": false
    }
  },
  "id": "6187842",
  "stepId": "2983530",
  "phaseId": "1575676",
  "action": "deploy",
  "environment": "weretail-global-b75-prod",
  "environmentType": "prod",
  "environmentId": "59254",
  "startedAt": "2022-01-20T14:47:41.247+0000",
  "finishedAt": "2022-01-20T15:06:19.885+0000",
  "updatedAt": "2022-01-20T15:06:20.803+0000",
  "details": {
  },
  "status": "FINISHED"
```

Sintassi del collegamento HAL `href` non è destinato ad essere utilizzato come punto di riferimento. Il valore effettivo deve sempre essere letto dal collegamento HAL e non generato.

Invio di un `PUT` la richiesta a questo endpoint darà luogo a un `201` in caso di esito positivo, l’organo di risposta sarà la rappresentazione della nuova esecuzione. È simile all’avvio di un’esecuzione regolare tramite l’API .
