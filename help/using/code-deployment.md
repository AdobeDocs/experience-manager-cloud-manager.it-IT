---
title: Distribuzione del codice
description: Scopri come distribuire il codice e cosa accade in Cloud Manager quando lo fai.
exl-id: 3d6610e5-24c2-4431-ad54-903d37f4cdb6
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: ht
source-wordcount: '1609'
ht-degree: 100%

---


# Distribuzione del codice {#code-deployment}

Scopri come distribuire il codice e cosa accade in Cloud Manager quando lo fai.

## Distribuzione del codice con Cloud Manager {#deploying-code-with-cloud-manager}

Una volta configurata la pipeline di produzione, inclusi l’archivio e gli ambienti necessari, puoi distribuire il codice.

1. Da Cloud Manager, fai clic su **Distribuzione** per avviare il processo di distribuzione.

   ![Pulsante Distribuzione](/help/assets/Deploy1.png)

1. Viene visualizzata la schermata **Esecuzione della pipeline**. Fai clic su **Genera** per avviare il processo.

   ![Pulsante Genera](/help/assets/Deploy2.png)

Il processo di compilazione avvia il processo di distribuzione del codice, inclusi i seguenti passaggi:

* Distribuzione dello staging
* Test dello staging
* Distribuzione di produzione

Puoi rivedere i passaggi da vari processi di distribuzione visualizzando i registri o verificando i risultati per i criteri di test.

## Passaggi della distribuzione {#deployment-steps}

In questa sezione sono descritte le diverse azioni che si verificano durante ogni passaggio della distribuzione. Consulta la sezione [Dettagli del processo di distribuzione](#deployment-process) per informazioni tecniche su come il codice stesso viene distribuito dietro le quinte.

### Passaggio della distribuzione dello staging {#stage-deployment}

Il passaggio **Distribuzione dello staging** include le seguenti azioni:

* **Convalida**: questo passaggio assicura che la pipeline sia configurata per utilizzare le risorse attualmente disponibili, ad esempio che il ramo configurato esista e che gli ambienti siano disponibili.
* **Test di compilazione e dell’unità**: questo passaggio esegue un processo di compilazione containerizzato. Per dettagli, consulta il documento [Ambiente di creazione](/help/getting-started/build-environment.md).
* **Scansione del codice**: questo passaggio valuta la qualità del codice dell’applicazione. Per informazioni dettagliate sulla procedura di test, consulta il documento [Informazioni sui risultati dei test](/help/using/code-quality-testing.md).
* **Distribuzione allo staging**

![Distribuzione dello staging](/help/assets/Stage_Deployment1.png)

### Passaggio del test dello staging {#stage-testing}

Il passaggio del **test dello staging** include le azioni seguenti:

* **Test di sicurezza**: questo passaggio valuta l’impatto sulla sicurezza del codice nell’ambiente AEM. Per informazioni dettagliate sulla procedura di test, consulta il documento [Informazioni sui risultati dei test](/help/using/code-quality-testing.md).
   * **Test delle prestazioni**: questo passaggio valuta le prestazioni del codice. Per informazioni dettagliate sulla proceduta di test, consulta [Informazioni sui risultati dei test](/help/using/code-quality-testing.md).

   ![Test dello staging](/help/assets/Stage_Testing1.png)

### Passaggio della distribuzione di produzione {#production-deployment}

Il passaggio della **Distribuzione di produzione**, include le azioni seguenti:

* **Domanda di approvazione**
   * Questa opzione è abilitata durante la configurazione della pipeline.
   * Utilizzando questa opzione, puoi pianificare la distribuzione di produzione oppure fare clic su **Ora** per eseguirla immediatamente.
* **Pianificazione della distribuzione di produzione**
   * Questa opzione è abilitata durante la configurazione della pipeline.
   * La data e l’ora pianificate vengono specificate in termini di fuso orario dell’utente.
      ![Pianificazione della distribuzione](/help/assets/Production_Deployment1.png)
* **Supporto CSE** (se attivato)
* **Distribuzione alla produzione**

![Distribuzione di produzione](/help/assets/Prod_Deployment1.png)

Una volta completata la distribuzione, il codice si trova nel relativo ambiente di destinazione e puoi visualizzare i registri.

![Distribuzione completata](/help/assets/Production_Deployment2.png)

## Interruzioni {#timeouts}

Per i seguenti passaggi è previsto un timeout in caso di attesa del feedback dell’utente:

| Passaggio | Timeout |
|--- |--- |
| Test di qualità del codice | 14 giorni |
| Test di sicurezza | 14 giorni |
| Test delle prestazioni | 14 giorni |
| Domanda di approvazione | 14 giorni |
| Pianificazione della distribuzione nell’ambiente di produzione | 14 giorni |
| Supporto CSE | 14 giorni |

## Dettagli del processo di distribuzione {#deployment-process}

Cloud Manager carica tutti i file target/*.zip prodotti dal processo di compilazione in un percorso di archiviazione. Questi artefatti vengono recuperati da questo percorso durante le fasi di distribuzione della pipeline.

Quando Cloud Manager viene implementato in topologie non di produzione, l’obiettivo è quello di completare la distribuzione il più rapidamente possibile e, pertanto, gli artefatti vengono distribuiti simultaneamente su tutti i nodi nel modo seguente:

1. Cloud Manager determina se ogni artefatto è un pacchetto AEM o dispatcher.
1. Cloud Manager rimuove tutti i dispatcher dal load balancer per isolare l’ambiente durante la distribuzione.

   * Se non è configurato diversamente, è possibile ignorare le modifiche del load balancer nelle distribuzioni di sviluppo e staging, ad esempio per l’ambiente di sviluppo, scollegare e allegare i passaggi anche nelle pipeline non di produzione, mentre per l’ambiente di staging nella pipeline di produzione.

   ![Ignora il load balancer](/help/assets/load_balancer.png)

   >[!NOTE]
   >
   >Questa funzione dovrebbe essere utilizzata principalmente dai clienti 1-1-1.

1. Ciascun artefatto AEM viene distribuito in ogni istanza di AEM tramite le API della Gestione pacchetti, con le dipendenze dei pacchetti che determinano l’ordine di distribuzione.

   * Per ulteriori informazioni su come utilizzare i pacchetti per installare nuove funzionalità, trasferire contenuti tra le istanze ed eseguire il backup del contenuto dell’archivio, consulta il documento [Gestione pacchetti.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager.html?lang=it)
   >[!NOTE]
   >
   >Tutti gli artefatti AEM vengono distribuiti sia all’autore che agli editori. Le modalità di esecuzione devono essere utilizzate quando sono necessarie configurazioni specifiche per il nodo. Per ulteriori informazioni su come le modalità di esecuzione consentono di regolare l’istanza di AEM per uno scopo specifico, fare riferimento a [Eseguire la modalità sezione del documento Distribuzione su AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html?lang=it#runmodes)

1. L’artefatto del dispatcher viene distribuito a ciascun dispatcher nel modo seguente:

   1. Le configurazioni correnti vengono sottoposte a backup e copiate in un percorso temporaneo.
   1. Tutte le configurazioni vengono eliminate tranne i file immutabili. Consulta il documento [Configurazioni del Dispatcher](/help/getting-started/dispatcher-configurations.md) per ulteriori dettagli. Questo cancella le directory per garantire che non vengano lasciati indietro i file orfani.
   1. L’artefatto viene estratto nella directory `httpd`. I file immutabili non vengono sovrascritti. Eventuali modifiche apportate ai file immutabili nell’archivio Git verranno ignorate al momento della distribuzione. Questi file sono fondamentali per il framework del dispatcher di AMS e non possono essere modificati.
   1. Apache esegue un test di configurazione. Se non viene rilevato alcun errore, il servizio viene ricaricato. Se si verifica un errore, le configurazioni vengono ripristinate dal backup, il servizio viene ricaricato e l’errore viene segnalato a Cloud Manager.
   1. Ogni percorso specificato nella configurazione della pipeline viene invalidato o svuotato dalla cache del dispatcher.

   >[!NOTE]
   >
   >Cloud Manager prevede che l’artefatto del dispatcher contenga l’intero set di file. Tutti i file di configurazione del dispatcher devono essere presenti nell’archivio Git. I file o le cartelle mancanti causeranno un errore di distribuzione.

1. In seguito alla corretta distribuzione di tutti i pacchetti AEM e dispatcher a tutti i nodi, i dispatcher vengono aggiunti nuovamente al load balancer e la distribuzione è completa.

   >[!NOTE]
   >
   >è possibile ignorare le modifiche del load balancer nelle distribuzioni di sviluppo e staging, ad esempio per l’ambiente di sviluppo, scollegare e allegare i passaggi anche nelle pipeline non di produzione, mentre per l’ambiente di staging nella pipeline di produzione.

### Fase dalla distribuzione alla produzione {#deployment-production-phase}

Il processo di distribuzione nelle topologie di produzione è leggermente diverso per ridurre al minimo l’impatto sui visitatori del sito AEM.

Le distribuzioni di produzione seguono generalmente gli stessi passaggi indicati in precedenza, ma in modo continuativo:

1. Distribuisci pacchetti AEM per l’authoring.
1. Scollega dispatcher1 dal load balancer.
1. Distribuisci pacchetti AEM a publish1 e il pacchetto dispatcher a dispatcher1 in parallelo, svuota la cache del dispatcher.
1. Ricolloca il dispatcher1 nel load balancer.
1. Una volta che dispatcher1 è rimesso in servizio, scollega dispatcher2 dal load balancer.
1. Distribuisci pacchetti AEM a publish2 e il pacchetto dispatcher a dispatcher2 in parallelo, svuota la cache del dispatcher.
1. Ricolloca il dispatcher2 nel load balancer.

Questo processo continua fino a quando la distribuzione non raggiunge tutti gli editori e i dispatcher nella topologia.

## Esecuzione di una pipeline in modalità emergenza {#emergency-pipeline}

In situazioni critiche, i clienti di Adobe Managed Services potrebbero dover distribuire modifiche al codice nei rispettivi ambienti di staging e produzione senza attendere l’esecuzione di un ciclo di test completo di Cloud Manager.

Per risolvere queste situazioni, la pipeline di produzione di Cloud Manager può essere eseguita in modalità emergenza. Quando si utilizza questa modalità, i passaggi del test di sicurezza e prestazioni non vengono eseguiti. Tutti gli altri passaggi, compresi eventuali passaggi di approvazione configurati, vengono eseguiti come nella normale modalità di esecuzione della pipeline.

>[!NOTE]
>
>La funzione di esecuzione di una pipeline in modalità emergenza viene attivata a livello di programma dal CSE (Customer Success Engineers).

### Utilizzo dell’esecuzione di una pipeline in modalità emergenza {#using-emergency-pipeline}

Quando si avvia un’esecuzione della pipeline di produzione, se la funzione della modalità di esecuzione di emergenza della pipeline è stata attivata per il programma, è possibile avviare l’esecuzione in modalità normale o emergenza da una finestra di dialogo.

![Eseguire le opzioni della pipeline](/help/assets/execution-emergency1.png)

Quando si visualizza la pagina dei dettagli di esecuzione della pipeline per un’esecuzione in modalità emergenza, le breadcrumb nella parte superiore dello schermo mostrano un indicatore dell’esecuzione della pipeline in modalità emergenza.

![Breadcrumb in modalità emergenza](/help/assets/execution-emergency2.png)

L’esecuzione di una pipeline in modalità emergenza può essere eseguita anche tramite l’API di Cloud Manager o CLI. Per avviare un&#39;esecuzione in modalità emergenza, invia una richiesta `PUT` all’endpoint di esecuzione della pipeline con il parametro query `?pipelineExecutionMode=EMERGENCY` oppure, se utilizzi CLI:

```
$ aio cloudmanager:pipeline:create-execution PIPELINE_ID --emergency
```

## Eseguire nuovamente una distribuzione di produzione {#re-execute-deployment}

Una nuova esecuzione del passaggio di distribuzione di produzione è disponibile per le esecuzioni in cui il passaggio di distribuzione di produzione è stato completato. Il tipo di completamento non è importante. La distribuzione potrebbe avere esito positivo (solo per i programmi AMS), essere annullata o non essere riuscita. Il caso di utilizzo principale è il caso in cui il passaggio di distribuzione della produzione non è riuscito per motivi transitori. La riesecuzione crea una nuova esecuzione utilizzando la stessa pipeline. Questa nuova esecuzione è composta da tre passaggi:

1. **Passaggio di convalida**: si tratta essenzialmente della stessa convalida che si verifica durante una normale esecuzione della pipeline.
1. **Passaggio di compilazione**: nel contesto di una riesecuzione, il passaggio di build copia gli artefatti e non esegue effettivamente un nuovo processo di build.
1. **Passaggio di distribuzione della produzione**: questa opzione utilizza la stessa configurazione e le stesse opzioni del passaggio di distribuzione di produzione in una normale esecuzione della pipeline.

Il passaggio di compilazione può essere etichettato in modo diverso nell’interfaccia utente per rispecchiare la copia degli artefatti non la ricompilazione.

![Riesecuzione](/help/assets/Re-deploy.png)

### Limitazioni {#limitations}

* La riesecuzione del passaggio di distribuzione di produzione è disponibile solo per l’ultima esecuzione.
* La riesecuzione non è disponibile per le esecuzioni di ripristino o le esecuzioni di aggiornamenti push.
* Se l’ultima esecuzione non è riuscita in un qualsiasi punto prima della fase di distribuzione della produzione, non è possibile eseguirla nuovamente.

### Identificazione di una riesecuzione {#identifying}

Per identificare se un’esecuzione è una riesecuzione, si può esaminare il campo `trigger`. Il valore sarà `RE_EXECUTE`.

### Attivazione di una riesecuzione {#triggering}

Per attivare una riesecuzione, è necessario effettuare una richiesta `PUT` al collegamento HAL `http://ns.adobe.com/adobecloud/rel/pipeline/reExecute` sullo stato del passaggio di distribuzione di produzione. Se tale collegamento è presente, l’esecuzione può essere riavviata da quel passaggio. Se è assente, l’esecuzione non può essere riavviata da quel passaggio. Questo collegamento sarà sempre presente solo nel passaggio di distribuzione della produzione

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

La sintassi del valore `href` del collegamento HAL non è destinata ad essere utilizzata come punto di riferimento. Il valore effettivo deve sempre essere letto dal collegamento HAL e non generato.

L&#39;invio di una richiesta `PUT` a questo endpoint può causare una risposta `201` in caso di esito positivo e il corpo della risposta sarà la rappresentazione della nuova esecuzione. È simile all’avvio di un’esecuzione regolare tramite l’API.
