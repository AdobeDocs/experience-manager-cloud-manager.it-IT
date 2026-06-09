---
title: Aggiungere una pipeline di produzione
description: Scopri come utilizzare Cloud Manager per creare e configurare pipeline di produzione per distribuire il codice.
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
TQID: https://experienceleague.adobe.com/WH6W8bZNCWo0BAGLwnMOPpB3bk5P6Fd7c5b-dRT5Vc0
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: badb64b816e83ca08a39b2b39eda13335f6a3c1d
workflow-type: tm+mt
source-wordcount: 1665
ht-degree: 73%

---

# Aggiungere una pipeline di produzione {#configuring-production-pipelines}

Scopri come utilizzare Cloud Manager per creare e configurare pipeline di produzione per distribuire il codice. Per una panoramica delle nozioni di base sul funzionamento delle pipeline in Cloud Manager, consulta [Pipeline CI/CD](/help/overview/ci-cd-pipelines.md).

## Panoramica {#overview}

Utilizzando il riquadro **Impostazioni della pipeline** in [!UICONTROL Cloud Manager] puoi creare due diversi tipi di pipeline.

* **Pipeline di produzione**: una pipeline di produzione è una pipeline appositamente creata composta da una serie di passaggi orchestrati per portare il codice sorgente dall’archivio Git fino alla fase di produzione.
* **Pipeline non di produzione**: una pipeline non di produzione serve principalmente per eseguire scansioni di qualità del codice o per distribuire il codice sorgente in un ambiente di sviluppo.

Questo documento si concentra sulle pipeline di produzione. Per informazioni dettagliate su come configurare le pipeline non di produzione, consulta il documento [Configurazione delle pipeline non di produzione.](/help/using/non-production-pipelines.md)

Il ruolo di **Responsabile della distribuzione** è responsabile della configurazione della pipeline. La configurazione della pipeline è costituita da:

1. Definizione dell’attivatore che avvia la pipeline.
1. Definizione dei parametri che controllano la distribuzione di produzione.
1. Configurazione dei parametri del test delle prestazioni.

>[!NOTE]
>
>Non è possibile configurare una pipeline finché il relativo archivio Git associato non dispone di almeno un ramo e la [Configurazione del programma](/help/getting-started/program-setup.md) non è stata completata.

## Aggiungere una nuova pipeline di produzione {#adding-production-pipeline}

Una volta utilizzata l’interfaccia utente di [!UICONTROL Cloud Manager] per configurare il programma e disporre di almeno un ambiente, è possibile aggiungere una pipeline di produzione.

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Passa alla scheda **Pipeline** dalla pagina **Panoramica del programma**.

1. Fai clic su **Aggiungi**, quindi seleziona **Aggiungi pipeline di produzione**.

   ![Aggiungi una pipeline di produzione](/help/assets/configure-pipelines/add-prod7.png)

1. La finestra di dialogo **Aggiungi pipeline di produzione** si apre sulla scheda **Configurazione** in cui è necessario definire una serie di opzioni per la pipeline. Queste opzioni sono raggruppate in sezioni comprimibili e sono descritte nei passaggi seguenti.

   1. Fornisci un nome descrittivo per la pipeline nel campo **Nome pipeline**.

   1. Nella sezione **Ambienti** definisci cosa attiva una distribuzione e come deve essere implementata in base all’ambiente.

      1. Nella sezione **STAGING** è possibile definire il modo in cui la pipeline viene eseguita nell’ambiente di staging.

         * **Trigger di implementazione**: per definire gli attivatori di distribuzione che avviano la pipeline, sono disponibili le seguenti opzioni.

            * **Manuale**: per avviare la pipeline manualmente utilizzando l’interfaccia utente di Cloud Manager.
            * **Cambiamenti su Git**: per avviare la pipeline CI/CD ogni volta che vengono aggiunti dei commit al ramo Git configurato. Con questa opzione, puoi comunque avviare la pipeline manualmente, in base alle esigenze.

         * **Comportamento in caso di errori di metriche importanti**: durante la configurazione o la modifica della pipeline, il Responsabile della distribuzione ha la possibilità di definire il comportamento della pipeline quando si verifica un errore importante in uno qualsiasi dei gate di qualità. Le opzioni disponibili sono:

            * **Chiedi ogni volta**: impostazione predefinita che richiede l’intervento manuale per tutti gli errori importanti.
            * **Interrompi subito**: la pipeline viene annullata ogni volta che si verifica un errore importante. Questa opzione simula il rifiuto manuale di ogni errore da parte dell’utente.
            * **Continua immediatamente**: la pipeline procede automaticamente ogni volta che si verifica un errore importante. Quest’opzione simula l’approvazione manuale di ogni errore da parte dell’utente.

         ![Trigger di implementazione](/help/assets/configure-pipelines/add-prod3.png)

         * **Opzioni di implementazione**: è possibile accelerare alcune attività di distribuzione.

            * **Approva implementazione post-staging**: questa approvazione si verifica dopo la distribuzione nell&#39;ambiente di staging prima di eseguire qualsiasi test. In caso contrario, l’approvazione si verifica prima dell’implementazione della produzione che viene eseguita al termine di tutti i test.

            * **Salta modifiche a load balancer**: non vengono apportate modifiche al load balancer.

         ![Opzioni di implementazione per staging](/help/assets/configure-pipelines/add-prod4.png)

         * **Configurazione del Dispatcher**: il ruolo di **Responsabile della distribuzione** può configurare un set di percorsi di contenuto che verranno invalidati o svuotati dalla cache del Dispatcher AEM quando viene eseguita una pipeline. Queste azioni della cache verranno eseguite come parte del passaggio di implementazione della pipeline, subito dopo la distribuzione di eventuali pacchetti di contenuti. Queste impostazioni utilizzano il comportamento standard del Dispatcher AEM. Per configurare, effettua le seguenti operazioni:

            1. Nel **PERCORSO** fornisci un percorso di contenuto.
            1. In **TIPO**, seleziona l’azione da intraprendere su quel percorso.

               * **Scaricamento**: esegui un’eliminazione della cache.
               * **Invalida**: esegui un’invalidazione della cache, simile a quando il contenuto viene attivato da un’istanza di authoring a un’istanza di pubblicazione.

            1. Fai clic su **Aggiungi percorso** per aggiungere il percorso specificato. Puoi aggiungere fino a 100 percorsi per ambiente.

         ![Configurazione del Dispatcher](/help/assets/configure-pipelines/dispatcher-stage.png)

         >[!TIP]
         >
         >In generale, l’utilizzo dell’azione di invalidazione è preferibile, ma in alcuni casi può essere richiesta la cancellazione, soprattutto quando si utilizzano le librerie lato client HTML AEM.

      1. Nella sezione **PRODUZIONE**, puoi definire il modo in cui la pipeline viene eseguita nell’ambiente di produzione.

         * **Opzioni di implementazione**: puoi definire i parametri che controllano la distribuzione di produzione.

            * **Utilizza l’approvazione Go Live**: una distribuzione deve essere approvata manualmente da un utente con il ruolo **Proprietario business**, **Project Manager** o **Responsabile della distribuzione** tramite l’interfaccia utente di [!UICONTROL Cloud Manager].
            * **Pianificata**: opzione che interrompe la pipeline prima dell’implementazione della produzione per consentirne la pianificazione. Se questa opzione è selezionata, la pipeline si interrompe dopo la distribuzione nell’ambiente di staging e richiede all’utente di intraprendere un’azione.
               * **`Now`**: opzione che distribuisce immediatamente in produzione, completando in modo efficace la pipeline.
               * **Data**: opzione che consente all’utente di pianificare un periodo in cui la distribuzione deve essere completata.
               * **Interrompi esecuzione**: opzione che interrompe la distribuzione in produzione.

           >[!TIP]
           >
           >Consulta la [Distribuzione del codice](/help/using/code-deployment.md) per scoprire come impostare la pianificazione della distribuzione o eseguire immediatamente la pipeline.

            * **Utilizza CSE Oversight**: se questa opzione è selezionata, viene attivato un CSE (Customer Success Engineer) per avviare la distribuzione effettiva. Se questa opzione è abilitata durante la creazione o la modifica di una pipeline, il ruolo **Responsabile della distribuzione** dispone delle seguenti opzioni.

               * **Qualsiasi CSE**: questa opzione consente a qualsiasi CSE disponibile di avviare la distribuzione.
               * **Il mio CSE**: questa opzione consente solo al CSE specifico assegnato al cliente di avviare la distribuzione. Questa opzione vale anche per il backup designato del CSE, se quello assegnato non è disponibile.

           ![Opzioni di implementazione di produzione](/help/assets/configure-pipelines/prod-deploymentoptions.png)

         * **Configurazione Dispatcher**: definisce la configurazione di Dispatcher per l’ambiente di produzione. Le opzioni sono le stesse dell’ambiente di staging.

1. Fai clic su **Continua** per passare alla scheda **Codice Source** in cui selezioni il tipo di codice da distribuire e configurare l&#39;archivio di origine.

   1. In **Seleziona il codice da distribuire**, scegli il tipo di distribuzione:

      * **[Codice full stack](#full-stack-code)** - Codice per l&#39;applicazione AEM completa.
      * **[Configurazione a livello web](#web-tier-config)** - Proprietà di Dispatcher per archiviare, elaborare e distribuire pagine Web al client.

      Per ulteriori informazioni su questi tipi di distribuzione, consulta [Pipeline CI/CD](/help/overview/ci-cd-pipelines.md#code-sources). I passaggi rimanenti per completare la configurazione della pipeline dipendono dal tipo selezionato. Segui i collegamenti riportati qui sopra per passare alla sezione pertinente di questo documento.

1. Fai clic su **Continua** per passare alla scheda **Test della fase**, in cui puoi configurare il test di prestazione di AEM Sites e AEM Assets, a seconda dei prodotti per i quali disponi della licenza. {#stage-testing}

   >[!TIP]
   >
   >Consulta [Test della qualità del codice](/help/using/code-quality-testing.md#performance-testing) per maggiori dettagli sulle opzioni disponibili nella scheda **Test della fase**.

   1. Nella sezione **Consegna dei contenuti dei siti/Peso di carico distribuito** puoi configurare il test delle prestazioni del sito in base alla ponderazione delle richieste di pagina tra tre set di pagine. Puoi abilitare o disabilitare i set di pagine in base alle esigenze.

      * **Pagine live popolari**
      * **Altre pagine live**
      * **Nuove pagine**

      ![Peso di caricamento dei siti](/help/assets/configure-pipelines/add-prod8.png)

   1. Nella sezione **Distribuzione dei test delle prestazioni delle risorse**, puoi definire la distribuzione di test di immagini e PDF e le risorse di test.

      * **Immagini**: regola il cursore per adeguare la suddivisione del test tra immagini e PDF.
      * **PDF**: regola il cursore per adeguare la suddivisione del test tra immagini e PDF.

      * Definisci le risorse personalizzate caricandole.

         1. **FORMATO**: scegli se la risorsa personalizzata è un PDF di un’immagine.
         1. **NOME FILE**: utilizza il pulsante di browser del file per selezionare un’immagine dal computer locale.
         1. **Aggiungi file di test**: fai clic per caricare la risorsa selezionata.

      ![Distribuzione dei test delle risorse](/help/assets/configure-pipelines/add-prod6.png)

1. Fai clic su **Salva** per completare l’aggiunta della pipeline di produzione.

### Codice full stack {#full-stack-code}

Una pipeline del codice full stack distribuisce le build del codice back-end e front-end insieme alla configurazione HTTPD/Dispatcher.

>[!NOTE]
>
>Se esiste già una pipeline di produzione full stack, questa selezione viene disabilitata.

**Per configurare una pipeline di produzione del codice full stack:**

1. Nella scheda **Codice Source**, definisci le opzioni seguenti.

   * **Archivio**: definisce l’archivio Git dal quale la pipeline deve recuperare il codice.

   >[!TIP]
   >
   >Consulta il documento [Configurazione del programma](/help/getting-started/program-setup.md) per scoprire come aggiungere e gestire archivi in Cloud Manager.

   * **Ramo Git** - Definisce da quale ramo la pipeline deve recuperare il codice.
   * **Ignora configurazione a livello web**: se questa opzione è selezionata, la pipeline non distribuisce la configurazione a livello web. Se per lo stesso ambiente esiste già una pipeline di configurazione a livello web, questa casella di controllo viene selezionata e disabilitata automaticamente perché la configurazione a livello web viene gestita da tale pipeline. Se non esiste alcuna pipeline di configurazione a livello web, puoi selezionare o deselezionare questa opzione per controllare se la pipeline full stack distribuisce la configurazione Dispatcher.

   ![Origine codice full stack](/help/assets/configure-pipelines/add-prod-fullstack-source.png)

1. Fai clic su **Continua** per passare alla scheda **Test dello staging**. Per ulteriori dettagli, consulta [Test dello staging](#stage-testing).

### Configurazione livello web {#web-tier-config}

Una pipeline di configurazione a livello web distribuisce solo la configurazione HTTPD/Dispatcher. Per ulteriori dettagli su questo tipo di pipeline, consulta [Pipeline CI/CD](/help/overview/ci-cd-pipelines.md#deployment-types).

>[!NOTE]
>
>Se esiste già una pipeline di produzione di configurazione a livello web, questa selezione viene disabilitata.

Se crei una pipeline di configurazione a livello web per un ambiente con una pipeline full stack esistente, la configurazione a livello web nella pipeline full stack viene ignorata. Questa modifica influisce solo sulla configurazione a livello web in tale ambiente.

**Per configurare una pipeline di produzione di configurazione a livello web:**

1. Nella scheda **Codice Source**, definisci le opzioni seguenti.

   * **Archivio** - Dall&#39;elenco a discesa, selezionare l&#39;archivio Git contenente la configurazione a livello Web.
   * **Ramo Git** - Selezionare il ramo nell&#39;archivio scelto utilizzato da Cloud Manager per la distribuzione.
   * **Posizione codice** - Immettere il percorso nell&#39;archivio selezionato che contiene la configurazione a livello Web da distribuire. Il percorso predefinito è la directory principale dell&#39;archivio (`/`).

   >[!NOTE]
   >
   >Se Posizione codice non fa riferimento al percorso del codice del dispatcher, è possibile inserire codice aggiuntivo dell’applicazione nel pacchetto dell’artefatto e distribuirlo al dispatcher, causando un errore di Apache al riavvio e un errore della pipeline. Assicurati di impostare il percorso corretto per i file dispatcher nell’archivio.

   ![Origine configurazione livello Web](/help/assets/configure-pipelines/add-prod-webtier-source.png)

1. Fai clic su **Continua** per passare alla scheda **Test dello staging**. Per ulteriori dettagli, consulta [Test dello staging](#stage-testing).

## Passaggi successivi {#the-next-steps}

Dopo aver configurato la pipeline, puoi distribuire il codice. Per ulteriori dettagli, consulta la sezione [Distribuzione del codice](/help/using/code-deployment.md).

## Tutorial video {#video-tutorial-one}

Questo video fornisce una panoramica del processo di creazione della pipeline, descritto in questo documento.

>[!VIDEO](https://video.tv.adobe.com/v/26314/)
