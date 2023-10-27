---
title: Configurazione delle pipeline di produzione
description: Scopri come utilizzare Cloud Manager per creare e configurare pipeline di produzione per distribuire il codice.
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
source-git-commit: 33ccb0f2139162845cc1b72505b6a5bfc7cf43e7
workflow-type: ht
source-wordcount: '1302'
ht-degree: 100%

---


# Configurazione delle pipeline di produzione {#configuring-production-pipelines}

Scopri come utilizzare Cloud Manager per creare e configurare pipeline di produzione per distribuire il codice. Per una panoramica delle nozioni di base sul funzionamento delle pipeline in Cloud Manager, consulta il documento [Pipeline CI/CD.](/help/overview/ci-cd-pipelines.md)

## Panoramica {#overview}

Utilizzando il riquadro **Impostazioni della pipeline** in [!UICONTROL Cloud Manager] puoi creare due diversi tipi di pipeline.

* **Pipeline di produzione**: una pipeline di produzione è una pipeline appositamente creata composta da una serie di passaggi orchestrati per portare il codice sorgente dall’archivio Git fino alla fase di produzione.
* **Pipeline non di produzione**: una pipeline non di produzione serve principalmente per eseguire scansioni di qualità del codice o per distribuire il codice sorgente in un ambiente di sviluppo.

Questo documento si concentra sulle pipeline di produzione. Per informazioni dettagliate su come configurare le pipeline non di produzione, consulta il documento [Configurazione delle pipeline non di produzione.](/help/using/non-production-pipelines.md)

Il ruolo di **Responsabile della distribuzione** è responsabile della configurazione della pipeline. La configurazione della pipeline è costituita da:

1. Definizione dell’attivatore che avvierà la pipeline.
1. Definizione dei parametri che controllano la distribuzione di produzione.
1. Configurazione dei parametri del test delle prestazioni.

>[!NOTE]
>
>Non è possibile impostare una pipeline finché il relativo archivio Git associato non dispone di almeno un ramo e la [Configurazione del programma](/help/getting-started/program-setup.md) non è stata completata.

## Aggiunta di una nuova pipeline di produzione {#adding-production-pipeline}

Una volta utilizzata l’interfaccia utente di [!UICONTROL Cloud Manager] per configurare il programma e disporre di almeno un ambiente, è possibile aggiungere una pipeline di produzione.

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Passa alla scheda **Pipeline** dalla pagina **Panoramica del programma**, fai clic su **+Aggiungi** e seleziona **Aggiungi pipeline di produzione**.

   ![Aggiungi una pipeline di produzione](/help/assets/configure-pipelines/add-prod1.png)

1. La finestra di dialogo **Aggiungi pipeline di produzione** si apre sulla scheda **Configurazione** in cui è necessario definire una serie di opzioni per la pipeline. Queste opzioni sono raggruppate in sezioni comprimibili e sono descritte nei passaggi seguenti.

   1. Fornisci un nome descrittivo per la pipeline nel campo **Nome pipeline**.

   1. Nella sezione **Codice sorgente**, definisci dove la pipeline recupera il codice che elaborerà.

      * **Archivio**: questa opzione definisce da quale archivio Git la pipeline deve recuperare il codice.

      >[!TIP]
      >
      >Consulta il documento [Configurazione del programma](/help/getting-started/program-setup.md) per scoprire come aggiungere e gestire archivi in Cloud Manager.

      * **Ramo Git**: questa opzione definisce da quale ramo della pipeline selezionata deve essere recuperato il codice.
      * **Posizione codice**: questa opzione definisce il percorso nel ramo dell’archivio selezionato da cui la pipeline deve recuperare il codice.

      ![Definire l&#39;archivio per la pipeline](/help/assets/configure-pipelines/add-prod2.png)

   1. Nella sezione **Ambienti** definisci cosa attiva una distribuzione e come deve essere implementata in base all’ambiente.

      1. Nella sezione **STAGING** è possibile definire il modo in cui la pipeline viene eseguita nell’ambiente di staging.

         * **Trigger di implementazione**: per definire gli attivatori di distribuzione che avviano la pipeline, sono disponibili le seguenti opzioni.

            * **Manuale**: utilizza questa opzione per avviare manualmente la pipeline utilizzando l’interfaccia utente di Cloud Manager.
            * **Cambiamenti su Git**: questa opzione avvia la pipeline CI/CD ogni volta che vengono aggiunti dei commit al ramo Git configurato. Con questa opzione, puoi comunque avviare la pipeline manualmente, in base alle esigenze.

         * **Comportamento in caso di errori di metriche importanti**: durante la configurazione o la modifica della pipeline, il Responsabile della distribuzione ha la possibilità di definire il comportamento della pipeline quando si verifica un errore importante in uno qualsiasi dei gate di qualità. Le opzioni disponibili sono:

            * **Chiedi ogni volta**: impostazione predefinita che richiede l’intervento manuale per tutti gli errori importanti.
            * **Interrompi subito**: selezionando questa opzione, la pipeline viene annullata ogni volta che si verifica un errore importante. In sostanza, quest’opzione simula un utente che rifiuta manualmente ogni errore.
            * **Continua immediatamente**: selezionando questa opzione, la pipeline avanza automaticamente ogni volta che si verifica un errore importante. In sostanza, questa opzione simula un utente che approva manualmente ogni errore.

         ![Trigger di implementazione](/help/assets/configure-pipelines/add-prod3.png)

         * **Opzioni di implementazione**: è possibile accelerare alcune attività di distribuzione.

            * **Approva implementazione post-staging**: questa approvazione si verifica dopo la distribuzione nell&#39;ambiente di staging prima di eseguire qualsiasi test. In caso contrario, l’approvazione si verifica prima della distribuzione di produzione che viene eseguita al termine di tutti i test.

            * **Salta modifiche a load balancer**: non vengono apportate modifiche al load balancer.

         ![Opzioni di implementazione per staging](/help/assets/configure-pipelines/add-prod4.png)

         * **Configurazione del Dispatcher**: il ruolo di **Responsabile della distribuzione** può configurare un set di percorsi di contenuto che verranno invalidati o svuotati dalla cache del dispatcher AEM quando viene eseguita una pipeline. Queste azioni della cache verranno eseguite come parte del passaggio della pipeline di implementazione, subito dopo la distribuzione di eventuali pacchetti di contenuto. Queste impostazioni utilizzano il comportamento standard del Dispatcher AEM. Per configurare:

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

            * **Utilizza l’approvazione lancio**: una distribuzione deve essere approvata manualmente da un utente con il ruolo di **Proprietario business**, **Project Manager** oppure **Responsabile della distribuzione** tramite l’interfaccia utente di [!UICONTROL Cloud Manager].
            * **Pianificato**: questa opzione interrompe la pipeline prima dell’implementazione di produzione per consentirne la pianificazione. Se questa opzione è selezionata, la pipeline si arresta dopo la distribuzione nell’ambiente di staging e richiede all’utente di eseguire l’azione.
               * **Ora**: questa opzione distribuisce immediatamente in produzione, completando in modo efficace la pipeline.
               * **Data**: questa opzione consente all’utente di pianificare un’ora in cui la distribuzione deve essere completata.
               * **Interrompi esecuzione**: questa opzione interrompe la distribuzione in produzione.

           >[!TIP]
           >
           >Fare riferimento al documento [Distribuzione del codice,](/help/using/code-deployment.md) per scoprire come impostare la pianificazione della distribuzione o eseguire immediatamente la pipeline.

            * **Utilizza CSE Oversight**: se questa opzione è selezionata, viene attivato un CSE per avviare effettivamente la distribuzione. Se questa opzione è abilitata durante la creazione o la modifica di una pipeline, il ruolo **Responsabile della distribuzione** dispone delle seguenti opzioni.

               * **Qualsiasi CSE**: questa opzione consente a qualsiasi CSE disponibile di avviare la distribuzione.
               * **Il mio CSE**: questa opzione consente solo al CSE specifico assegnato al cliente di avviare la distribuzione. Questo vale anche per il backup designato del CSE, se quello assegnato non è disponibile.

           ![Opzioni di implementazione di produzione](/help/assets/configure-pipelines/prod-deploymentoptions.png)

         * **Configurazione del Dispatcher**: definisce la configurazione del dispatcher per l’ambiente di produzione. Le opzioni sono le stesse dell’ambiente di staging.

1. Fai clic su **Continua** per passare alla scheda **Test dello staging**, in cui puoi configurare il test di prestazione di AEM Sites e AEM Assets, a seconda dei prodotti per i quali hai concesso la licenza.

   >[!TIP]
   >
   >Consulta il documento [Test della qualità del codice](/help/using/code-quality-testing.md#performance-testing) per maggiori dettagli sulle opzioni disponibili nella scheda **Test dello staging**.

   1. Nella sezione **Consegna dei contenuti dei siti/Peso del caricamento distribuito**, puoi definire com’è configurato il test delle prestazioni dei siti in base alla ponderazione delle richieste di pagina tra i tre set di pagine, che può essere abilitato o disabilitato.

      * **Pagine live popolari**
      * **Altre pagine live**
      * **Nuove pagine**

      ![Peso di caricamento dei siti](/help/assets/configure-pipelines/add-prod5.png)

   1. Nella sezione **Distribuzione dei test delle prestazioni delle risorse**, puoi definire la distribuzione di test di immagini e PDF e le tue risorse di test.

      * **Immagini**: regola il cursore per adeguare la suddivisione del test tra immagini e PDF.
      * **PDF**: regola il cursore per adeguare la suddivisione del test tra immagini e PDF.

      * Definisci le risorse personalizzate caricandole.

         1. **FORMATO**: scegli se la risorsa personalizzata è un PDF di un’immagine.
         1. **NOME FILE**: utilizza il pulsante di browser del file per selezionare un’immagine dal computer locale.
         1. **Aggiungi file di test**: fai clic per caricare la risorsa selezionata.

      ![Distribuzione dei test delle risorse](/help/assets/configure-pipelines/add-prod6.png)

1. Fai clic su **Salva** per completare l’aggiunta della pipeline di produzione.

## Passaggi successivi {#the-next-steps}

Dopo aver configurato la pipeline, è necessario distribuire il codice. Per ulteriori dettagli, consulta il documento [Distribuzione del codice](/help/using/code-deployment.md).

## Tutorial video {#video-tutorial-one}

Questo video fornisce una panoramica del processo di creazione della pipeline, descritto in questo documento.

>[!VIDEO](https://video.tv.adobe.com/v/26314/)
