---
title: Aggiungere una pipeline non di produzione
description: Scopri come utilizzare Cloud Manager per creare e configurare pipeline non di produzione per distribuire il codice.
exl-id: ccf4b4a2-6e29-4ede-821c-36318b568e5c
TQID: https://experienceleague.adobe.com/Dj7SjKdao6RU-cIS7D1AQxg5qpKrJMTcYQJBfiqc-Gg
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: badb64b816e83ca08a39b2b39eda13335f6a3c1d
workflow-type: tm+mt
source-wordcount: 2096
ht-degree: 22%

---

# Aggiungere una pipeline non di produzione {#configuring-non-production-pipelines}

Scopri come utilizzare Cloud Manager per creare e configurare pipeline non di produzione per distribuire il codice. Per una panoramica delle nozioni di base sul funzionamento delle pipeline in Cloud Manager, consulta [Pipeline CI/CD](/help/overview/ci-cd-pipelines.md).

## Panoramica {#overview}

Utilizzando il riquadro **Pipeline** in [!UICONTROL Cloud Manager], il **Responsabile della distribuzione** può creare due diversi tipi di pipeline.

* **Pipeline di produzione**: una pipeline di produzione è una pipeline appositamente creata composta da una serie di passaggi orchestrati per portare il codice sorgente fino alla produzione.
* **Pipeline non di produzione**: una pipeline non di produzione serve principalmente per eseguire scansioni di qualità del codice o per distribuire il codice sorgente in un ambiente di sviluppo.

Questo documento si concentra sulle pipeline non di produzione. Per informazioni dettagliate su come configurare le pipeline di produzione, consulta il documento [Configurazione delle pipeline di produzione](/help/using/production-pipelines.md).

Esistono due tipi di pipeline non di produzione:

* **Pipeline di qualità del codice**: eseguono controlli di qualità del codice in un ramo Git e i passaggi di generazione e qualità del codice.
* **Pipeline di implementazione**: oltre a eseguire i passaggi di generazione e qualità del codice come le pipeline di qualità del codice, queste pipeline implementano il codice in un ambiente non di produzione.

>[!NOTE]
>
>Non puoi impostare una pipeline finché il relativo archivio Git associato non dispone di almeno un ramo e la [configurazione del programma](/help/getting-started/program-setup.md) non è stata completata. Consulta il documento [Archivi di Cloud Manager](/help/managing-code/managing-repositories.md) per scoprire come aggiungere e gestire gli archivi in Cloud Manager.

## Aggiungere una nuova pipeline non di produzione {#add-non-production-pipeline}

Dopo aver configurato un programma e almeno un ambiente nell’interfaccia utente di Cloud Manager, puoi aggiungere pipeline non di produzione. Utilizza queste pipeline per testare la qualità del codice prima di implementarle negli ambienti di produzione.

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) e seleziona l’organizzazione e il programma appropriati.

1. Dalla schermata iniziale di Cloud Manager, apri la scheda Pipeline e fai clic su **Aggiungi**, quindi seleziona **Aggiungi pipeline non di produzione**.

   ![Aggiungi pipeline non di produzione](/help/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. Nella scheda **Configurazione** della finestra di dialogo **Aggiungi pipeline non di produzione**, seleziona il tipo di pipeline da creare in uno dei seguenti modi:

   * **Pipeline di qualità del codice**: crea una pipeline che genera il codice, esegue unit test e valuta la qualità del codice senza distribuirla in un ambiente.
   * **Pipeline di distribuzione** - Crea una pipeline che genera il codice, esegue unit test, valuta la qualità del codice e distribuisce in un ambiente.

   ![Scegli il tipo di pipeline](/help/using/assets/add-non-production-pipeline-cm-ams.png)

>[!BEGINTABS]

>[!TAB Pipeline di qualità del codice - Scheda Configurazione]

| Sezione | Opzione | Descrizione |
| --- | --- | --- |
| **Configurazione pipeline** | **Nome pipeline non di produzione** | Immetti una descrizione per la pipeline nel campo **Nome pipeline non di produzione**. |
|  | **Test** | Visibile solo quando si modifica una pipeline non di produzione.<br>L&#39;interfaccia utente mostra le categorie di test eseguite dalla pipeline nell&#39;ambito della convalida della qualità del codice.<ul><li>**Test del codice statico** - Analizza il codice per individuare eventuali problemi di qualità e correttezza.<li>**Test di carico/prestazioni** - Valuta il comportamento relativo alle prestazioni come parte del test della pipeline.<li>**Test di sicurezza** - Controlla il codice e l&#39;output della pipeline per individuare eventuali problemi relativi alla sicurezza. |
| **Opzioni di distribuzione** | **Trigger distribuzione** | <ul><li>**Manuale**: ti consente di avviare manualmente la pipeline.<li>**Cambiamenti su Git**: avvia la pipeline ogni volta che vengono aggiunti dei commit al ramo Git configurato. Con questa opzione, puoi comunque avviare la pipeline manualmente in base alle esigenze. |
|  | **Comportamento in caso di errori di metriche importanti** | <ul><li>**Chiedi ogni volta**: questo comportamento è l’impostazione predefinita che richiede l’intervento manuale per tutti gli errori importanti.<li>**Interrompi subito** - Selezionando questa opzione, la pipeline viene annullata ogni volta che si verifica un errore importante. In sostanza, emula un utente che rifiuta manualmente ogni errore.<li>**Continua immediatamente** - Se selezionata, la pipeline procede automaticamente ogni volta che si verifica un errore importante. In sostanza, emula un utente che approva manualmente ogni errore.</li></ul> |
|  | **Approva dopo la distribuzione nell&#39;ambiente di staging**, casella di controllo | Visibile solo quando si modifica una pipeline non di produzione.<br>Selezionare questa opzione per richiedere l&#39;approvazione dopo la distribuzione nell&#39;ambiente di staging prima che la pipeline possa continuare. Se questa opzione non è selezionata, la pipeline continua in base al comportamento configurato. |

>[!TAB Pipeline di distribuzione - Scheda Configurazione]

| Sezione | Opzione | Descrizione |
| --- | --- | --- |
| **Configurazione pipeline** | **Nome pipeline non di produzione** | Immetti una descrizione per la pipeline nel campo **Nome pipeline non di produzione**. |
|   | **Ambiente di distribuzione idoneo** | Se la pipeline è di distribuzione, seleziona gli ambienti in cui Cloud Manager distribuisce il codice. |
|   | **Test** | Visibile solo quando si modifica una pipeline non di produzione.<br>L&#39;interfaccia utente mostra le categorie di test eseguite dalla pipeline nell&#39;ambito della convalida della qualità del codice.<ul><li>**Test del codice statico** - Analizza il codice per individuare eventuali problemi di qualità e correttezza.<li>**Test di carico/prestazioni** - Valuta il comportamento relativo alle prestazioni come parte del test della pipeline.<li>**Test di sicurezza** - Controlla il codice e l&#39;output della pipeline per individuare eventuali problemi relativi alla sicurezza.</li></ul> |
| **Opzioni di distribuzione** | **Trigger distribuzione** | <ul><li>**Manuale**: ti consente di avviare manualmente la pipeline.<li>**Cambiamenti su Git**: avvia la pipeline ogni volta che vengono aggiunti dei commit al ramo Git configurato. Con questa opzione, puoi comunque avviare la pipeline manualmente in base alle esigenze. |
|   | **Comportamento in caso di errori di metriche importanti** | <ul><li>**Chiedi ogni volta** - Impostazione predefinita che richiede all&#39;utente di decidere come procedere quando una metrica importante non riesce.<li>**Genera errore immediatamente** - La pipeline viene annullata ogni volta che si verifica un errore in una metrica importante. In sostanza, questa opzione simula il rifiuto manuale di ogni errore da parte dell’utente.<li>**Continua immediatamente** - La pipeline procede automaticamente ogni volta che una metrica importante non riesce. In sostanza, quest’opzione simula l’approvazione manuale di ogni errore da parte dell’utente.</li></ul> |
|  | **Approva dopo la distribuzione nell&#39;ambiente di staging**, casella di controllo | Visibile solo quando si modifica una pipeline non di produzione.<br>Selezionare questa opzione per richiedere l&#39;approvazione dopo la distribuzione nell&#39;ambiente di staging prima che la pipeline possa continuare. Se questa opzione non è selezionata, la pipeline continua in base al comportamento configurato. |
|  | **Ignora modifiche del load balancer**, casella di controllo | Seleziona questa opzione per impedire che la pipeline apporti modifiche al load balancer durante la distribuzione. |
|  | **Configurazione Dispatcher** | Il ruolo **Responsabile della distribuzione** può configurare un set di percorsi di contenuto invalidati o svuotati dalla cache di AEM Dispatcher quando viene eseguita una pipeline. Cloud Manager esegue queste azioni cache come parte del passaggio della pipeline di distribuzione, subito dopo la distribuzione di eventuali pacchetti di contenuto. Queste impostazioni utilizzano il comportamento standard del Dispatcher AEM. Per configurare `Dispatcher`, eseguire le operazioni seguenti:<ul><li>In **PATH**, fornisci un percorso di contenuto di cui vuoi eseguire lo scaricamento o l&#39;annullamento della validità della pipeline.<li>In **TIPO**, seleziona l’azione da intraprendere su quel percorso.<ul><li>**Svuotamento** - Eseguire un&#39;eliminazione della cache nel percorso specificato.</li><li>**Invalida**: esegui un’invalidazione della cache, simile a quando il contenuto viene attivato da un’istanza di authoring a un’istanza di pubblicazione.</li><li>Fai clic su **Aggiungi percorso** per aggiungere il percorso specificato. Puoi aggiungere fino a 100 percorsi per ambiente.</li></ul> |
| **Pipeline** | Casella di controllo **Audit dell&#39;esperienza** | Seleziona questa opzione per includere un passaggio di audit dell’esperienza nella pipeline. Quando è abilitata, la pipeline include il passaggio Audit dell’esperienza dopo la scheda Codice Source. |

>[!ENDTABS]

1. Nell&#39;angolo inferiore destro della finestra di dialogo **Aggiungi pipeline non di produzione** fare clic su **Continua**.
1. Seleziona il tipo di codice che la pipeline è configurata per generare e distribuire.

>[!BEGINTABS]

>[!TAB Scheda Codice Source - Codice full stack]

Distribuisce l’applicazione AEM completa, compreso il codice dell’applicazione e, per impostazione predefinita, la configurazione a livello web.

>[!NOTE]
>
>Se per l’ambiente selezionato esiste già una pipeline del codice full stack, la selezione viene disabilitata.

| Sezione | Opzione | Descrizione |
| --- | --- | --- |
| **Codice Source** | **Archivio** | Dall’elenco a discesa, scegli l’archivio Git utilizzato dalla pipeline come origine. Cloud Manager crea il codice dall’archivio scelto qui. |
|   | **Ramo Git** | Dall’elenco a discesa, scegli il ramo nell’archivio selezionato da cui generare la pipeline. Il valore predefinito è `main`. La pipeline utilizza il ramo scelto come origine per la generazione e la distribuzione. Se necessario, fare clic su **Aggiorna** per aggiornare l&#39;elenco dei rami disponibili per l&#39;archivio selezionato. Utilizza questa opzione se un ramo creato di recente non viene visualizzato nell’elenco. |
|   | **Strategia di compilazione** | <ul><li>**Build completa** - Genera tutti i moduli nell&#39;archivio ogni volta<li>BETA **Smart Build** - Genera solo moduli che sono stati modificati dopo l&#39;ultimo commit.<br>Ulteriori informazioni sull&#39;utilizzo di [Smart Build in una pipeline non di produzione](#about-smart-build).</li></ol>**Importante**: Smart Build è disponibile solo per le pipeline di qualità del codice e per le pipeline di distribuzione del codice full stack di sviluppo. |
|   | **Casella di controllo Ignora configurazione livello Web** | Seleziona questa opzione per saltare la distribuzione della configurazione a livello web in una pipeline di codice full stack. Lascia deselezionata l’opzione per distribuire la configurazione a livello web insieme al codice della pipeline. |
| **Pipeline** | Casella di controllo **Audit dell&#39;esperienza** | Seleziona questa opzione per includere un passaggio di audit dell’esperienza nella pipeline. Quando è abilitata, la pipeline include il passaggio Audit dell’esperienza dopo la scheda Codice Source. |

>[!TAB Codice Source - Configurazione livello Web]

Distribuisce solo la configurazione a livello web, ad esempio le proprietà di Dispatcher utilizzate per archiviare, elaborare e distribuire pagine web al client. Quando si seleziona **Configurazione livello Web**, Cloud Manager crea una pipeline dedicata alla distribuzione della configurazione a livello Web.

Se esiste già una pipeline full stack, Cloud Manager visualizza un avviso che la creazione di una pipeline di configurazione a livello web fa sì che la pipeline full stack esistente ignori la configurazione a livello web. Dopo aver creato la pipeline di configurazione a livello web, Cloud Manager gestisce le distribuzioni di configurazione a livello web tramite tale pipeline anziché tramite la pipeline full stack.

>[!NOTE]
>
>Se per l’ambiente selezionato esiste già una pipeline di configurazione a livello web, questa selezione viene disabilitata. In qualsiasi momento può essere presente una sola pipeline di configurazione a livello web per ogni ambiente.

| Sezione | Opzione | Descrizione |
| --- | --- | --- |
| **Codice Source** | **Archivio** | Dall’elenco a discesa, seleziona l’archivio Git contenente la configurazione a livello web. |
|   | **Ramo Git** | Seleziona il ramo nell’archivio scelto utilizzato da Cloud Manager per la distribuzione. Se necessario, fare clic su **Aggiorna** per aggiornare l&#39;elenco dei rami disponibili per l&#39;archivio selezionato. Utilizza questa opzione se un ramo creato di recente non viene visualizzato nell’elenco. |
|   | **Posizione codice** | Immetti il percorso nell’archivio selezionato contenente la configurazione a livello web da distribuire. Il percorso predefinito è la directory principale dell&#39;archivio (`/`). |

>[!NOTE]
>
>Se Posizione codice non fa riferimento al percorso del codice del dispatcher, è possibile inserire codice aggiuntivo dell’applicazione nel pacchetto dell’artefatto e distribuirlo al dispatcher, causando un errore di Apache al riavvio e un errore della pipeline. Assicurati di impostare il percorso corretto per i file dispatcher nell’archivio.

>[!ENDTABS]

1. Fai clic su **Salva**.

## Informazioni sull’utilizzo di Smart Build in una pipeline non di produzione{#about-smart-build}

**Smart Build** in Cloud Manager è una strategia di compilazione ottimizzata per le pipeline non di produzione. Smart Build riduce i tempi di generazione memorizzando nella cache i moduli e ricostruendo solo quelli che sono stati modificati dopo l’ultima esecuzione riuscita. I moduli invariati vengono riutilizzati dalla cache, mentre vengono ricostruiti solo i moduli modificati e le relative dipendenze, migliorando l’efficienza dei flussi di lavoro di sviluppo iterativi.

Smart Build è attualmente disponibile solo per:

* pipeline di qualità del codice.
* Sviluppare pipeline di distribuzione full stack.

>[!NOTE]
>
>La prima esecuzione dopo l’abilitazione di Smart Build si comporta come una Build completa perché la cache è vuota.

Si consiglia di utilizzare Smart Build nei seguenti casi:
* Stai sviluppando attivamente e apportando frequenti modifiche incrementali.
* Il progetto contiene più moduli Maven.
* Le build complete richiedono molto tempo.

Smart Build non è sempre ideale quando si dispone dei seguenti elementi:
* La build si basa principalmente su plug-in che eseguono operazioni al di fuori del grafico delle dipendenze di Maven.
* È necessaria la convalida completa della ricompilazione a ogni esecuzione.

### Comprendere le prestazioni della build{#smart-build-performance}

Il miglioramento delle prestazioni derivante dall’utilizzo di Smart Build dipende da diversi fattori, tra cui i seguenti:

* Il numero di moduli nel progetto.
* Frequenza e ambito delle modifiche al codice.
* La distribuzione delle dipendenze tra i moduli.

In generale, i progetti con molti moduli indipendenti possono vedere il miglioramento maggiore.

### Rinuncia alla cache per modulo{#smart-build-cache-optout}

Smart Build fornisce un controllo dettagliato che consente di disabilitare la memorizzazione nella cache per moduli specifici. Questa funzionalità è utile quando alcuni moduli:

* Utilizzare i plug-in, ad esempio `exec-maven-plugin` o `maven-antrun-plugin`.
* Eseguire operazioni sui file non tracciate dalle dipendenze Maven.
* Produrre risultati incoerenti quando memorizzato nella cache.

### Disattiva la memorizzazione in cache per un modulo{#smart-build-disable-caching}

È possibile aggiungere la seguente proprietà al `pom.xml` del modulo interessato:

```xml
<properties>
  <maven.build.cache.enabled>false</maven.build.cache.enabled>
</properties>
```

Questa sintassi forza la ricostruzione del modulo su ogni esecuzione della pipeline, mentre altri moduli continuano a beneficiare della memorizzazione in cache.

### Limitazioni e considerazioni sull’utilizzo di Smart Build{#smart-build-limitations}

Quando usi Smart Build, tieni presente quanto segue:

* Smart Build si basa sull’analisi delle dipendenze Maven.
* Le modifiche che non rientrano nel grafico delle dipendenze potrebbero non attivare le ricompilazioni.
* Alcuni plug-in potrebbero non essere completamente compatibili con il caching.
* Puoi tornare a **Build completa** in qualsiasi momento modificando la pipeline non di produzione.

Se si verifica un comportamento di compilazione imprevisto, è consigliabile disabilitare la memorizzazione nella cache per moduli specifici o cambiare temporaneamente la strategia di compilazione in **Build completa**.

### Risoluzione dei problemi di Smart Build{#smart-build-troubleshoot}

| Problema | Soluzioni consigliate |
| --- | --- |
| I risultati della build non sono coerenti | · Disattivare la memorizzazione nella cache per i moduli interessati.<br>· Verificare il comportamento del plug-in (in particolare `exec`/`antrun` plug-in). |
| Nessun miglioramento delle prestazioni | · Verificare che siano state eseguite più esecuzioni (riscaldamento della cache).<br>· Verificare se la maggior parte dei moduli cambia frequentemente. |
| Artefatti imprevisti o modifiche mancanti | · Verificare se le modifiche non rientrano nel tracciamento delle dipendenze Maven.<br>· Utilizzare **Build completa** per la verifica. |

Consulta [Aggiungere una pipeline non di produzione](#add-non-production-pipeline) per abilitare Smart Build.



<!-- 
1. If you chose to add a **Deployment Pipeline**, select the target deployment environment from the **Eligible Deployment Environments** dropdown.

1. Enter the repository where the pipeline should retrieve the code.

   * **Repository** - Select the Git repository that the pipeline retrieves code from.
   * **Git Branch** - Select the branch in the Git repository that the selected pipeline retrieves code from.

1. Define your deployment options.

   1. Under **Deployment Trigger**, define what event activates the pipeline.

      * **Manual** - Lets you manually start the pipeline.
      * **On Git Changes** - Starts the pipeline when commits are added to the configured Git branch. With this option, you can still start the pipeline manually, as required.

   1. For deployment pipelines, under **Important Metric Failures Behavior**, define the behavior of the pipeline when an important failure is encountered in any of the quality gates.

       * **Ask every time** - The default setting and requires manual intervention on any important failure.
       * **Fail Immediately** - Cloud Manager cancels the pipeline whenever an important failure occurs. It is essentially emulating a user manually rejecting each failure.
       * **Continue Immediately** - The pipeline proceeds automatically whenever an important failure occurs. It is essentially emulating a user manually approving each failure.

   1. **Dispatcher Configuration** - The **Deployment Manager** role can configure a set of content paths that Cloud Manager invalidates or flushes from the AEM Dispatcher cache when a pipeline is run. These cache actions are performed as part of the deployment pipeline step, just after any content packages are deployed. These settings use standard AEM Dispatcher behavior. To configure:

      1. Under **PATH** provide a content path.
      1. Under **TYPE**, select the action to be taken on that path.

         * **Flush** - Perform a cache deletion.
         * **Invalidate** - Perform a cache invalidation, similar to when content is activated from an authoring instance to a publishing instance.
         
      1. Click **Add Path** to add your specified path. You can add up to 100 paths per environment.

1. Click **Save**.
-->

## Passaggi successivi {#the-next-steps}

Dopo aver configurato la pipeline, puoi distribuire il codice. Per ulteriori dettagli, consulta la sezione [Distribuzione del codice](/help/using/code-deployment.md).

## Tutorial video {#video-tutorial}

Questo video fornisce una panoramica del processo di creazione della pipeline, descritto in questo documento.

>[!VIDEO](https://video.tv.adobe.com/v/328577?captions=ita)
