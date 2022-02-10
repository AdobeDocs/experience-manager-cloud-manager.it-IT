---
title: Configurazione delle pipeline di produzione
description: Scopri come utilizzare Cloud Manager per creare e configurare pipeline di produzione per distribuire il codice.
uuid: 35fd56ac-dc9c-4aca-8ad6-36c29c4ec497
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
content-type: reference
discoiquuid: ba6c763a-b78a-439e-8c40-367203a719b3
feature: CI-CD Pipeline
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
source-git-commit: 205113735cc743e11e140b1161413002844f5b79
workflow-type: tm+mt
source-wordcount: '1551'
ht-degree: 0%

---

# Configurazione delle pipeline di produzione {#configuring-production-pipelines}

Scopri come utilizzare Cloud Manager per creare e configurare pipeline di produzione per distribuire il codice. per una panoramica più concettuale del funzionamento delle pipeline in Cloud Manager, consulta la sezione [Documentazione sulla panoramica della pipeline CI/CD.](ci-cd-pipeline.md)

>[!NOTE]
>
>Per informazioni su come configurare le pipeline CI/CD per Cloud Manager in AEM as a Cloud Service, consulta [la documentazione di AEMaaCS.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html#using-cloud-manager)

## Panoramica {#understanding-the-flow}

Puoi configurare le pipeline utilizzando la **Impostazioni della pipeline** nella sezione [!UICONTROL Cloud Manager] Interfaccia utente.

Puoi creare due diversi tipi di pipeline.

* **Pipe di produzione** - Una pipeline di produzione è una pipeline appositamente costruita composta da una serie di passaggi orchestrati per portare il codice sorgente fino alla produzione.
* **Pipeline non di produzione** - Una pipeline non di produzione serve principalmente per eseguire scansioni di qualità del codice o per distribuire il codice sorgente in un ambiente di sviluppo.

Questo documento si concentra sulle condutture di produzione. Per informazioni dettagliate su come configurare le pipeline non di produzione, consulta il documento [Configurazione delle pipeline non di produzione.](configuring-non-production-pipelines.md)

La **Gestione distribuzione** Il ruolo è responsabile della configurazione della pipeline. La configurazione della pipeline consiste in:

1. Definizione del trigger che avvierà la pipeline.
1. Definizione dei parametri che controllano la distribuzione di produzione.
1. Configurazione dei parametri del test delle prestazioni.

>[!NOTE]
>
>Non è possibile impostare una pipeline finché il relativo archivio Git associato non dispone di almeno un ramo e [configurazione del programma](setting-up-program.md) è completo.

>[!NOTE]
>
>È possibile modificare le impostazioni della pipeline dopo la configurazione iniziale.

## Tutorial video {#video-tutorial-one}

Guarda questo video per una panoramica del processo di creazione della pipeline.

>[!VIDEO](https://video.tv.adobe.com/v/26314/)

## Aggiunta di una nuova pipeline di produzione {#adding-production-pipeline}

Una volta utilizzato il [!UICONTROL Cloud Manager] Interfaccia utente per configurare il programma e disporre di almeno un ambiente, puoi aggiungere una pipeline di produzione.

1. Accedi a Cloud Manager all&#39;indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selezionare l&#39;organizzazione e il programma appropriati.

1. Passa a **Tubi** scheda da **Panoramica del programma** e fai clic su **+Aggiungi** e seleziona **Aggiungi pipeline di produzione**.

   ![Aggiungere una pipeline di produzione](/help/using/assets/configure-pipelines/add-prod1.png)

1. La **Aggiungi pipeline di produzione** viene visualizzata la finestra di dialogo **Configurazione** scheda in cui è necessario definire una serie di opzioni per la pipeline. Queste opzioni sono raggruppate in sezioni comprimibili e sono descritte nei passaggi seguenti.

   1. Fornisci un nome descrittivo per la pipeline nel **Nome della pipeline** campo .

   1. Sotto la **Codice sorgente** , definisci dove la pipeline recupera il codice che elaborerà.

      * **Archivio** - Questa opzione definisce da quale git repo la pipeline deve recuperare il codice.
      >[!TIP]
      >
      >Vedere il documento [Imposta il programma](setting-up-program.md) per scoprire come aggiungere e gestire archivi in Cloud Manager.

      * **Ramo Git** - Questa opzione definisce da quale ramo della pipeline selezionata deve essere recuperato il codice.
      * **Posizione codice** - Questa opzione definisce il percorso nel ramo dell’archivio selezionato da cui la pipeline deve recuperare il codice.

      ![Definire i repository per la pipeline](/help/using/assets/configure-pipelines/add-prod2.png)

   1. Sotto la **Ambienti** definisci cosa attiva una distribuzione e come deve essere implementata in base all’ambiente.

      1. In **FASE** È possibile definire il modo in cui la pipeline viene eseguita nell’ambiente di staging.

         * **Trigger distribuzione** - Per definire gli attivatori di distribuzione che avviano la pipeline, sono disponibili le seguenti opzioni.

            * **Manuale** - Utilizza questa opzione per avviare manualmente la pipeline utilizzando l’interfaccia utente di Cloud Manager.
            * **Su modifiche Git** - Questa opzione avvia la pipeline CI/CD ogni volta che vengono aggiunti dei commit al ramo git configurato. Con questa opzione, potete comunque avviare la pipeline manualmente come necessario.
         * **Comportamento di errori di metrica importanti** - Durante la configurazione o la modifica della pipeline, Deployment Manager ha la possibilità di definire il comportamento della pipeline quando si verifica un errore importante in uno qualsiasi dei gate di qualità. Le opzioni disponibili sono:

            * **Chiedi sempre** - Questa è l&#39;impostazione predefinita e richiede l&#39;intervento manuale su qualsiasi errore importante.
            * **Non riuscito immediatamente** - Se selezionata, la pipeline verrà annullata ogni volta che si verifica un errore importante. In sostanza, questo sta simulando un utente che rifiuta manualmente ogni errore.
            * **Continua immediatamente** - Se selezionata, la pipeline procede automaticamente ogni volta che si verifica un errore importante. In sostanza, questo sta simulando un utente che approva manualmente ogni errore.

         ![Trigger di distribuzione](/help/using/assets/configure-pipelines/add-prod3.png)

         * **Opzioni di distribuzione** - È possibile accelerare alcune attività di distribuzione.

            * **Approva dopo la distribuzione dello stage** - Questa approvazione si verifica dopo la distribuzione nell&#39;ambiente di staging prima di eseguire qualsiasi test. In caso contrario, l&#39;approvazione viene eseguita prima della distribuzione di produzione, che viene eseguita al termine di tutti i test.

            * **Ignora modifiche di Load Balancer** - Non vengono apportate modifiche al load balancer.

         ![Opzioni di distribuzione per staging](/help/using/assets/configure-pipelines/add-prod4.png)

         * **Configurazione del Dispatcher** - **Gestione distribuzione** Il ruolo può configurare un set di percorsi di contenuto che verranno invalidati o scaricati dalla cache di Dispatcher AEM quando viene eseguita una pipeline. Queste azioni della cache verranno eseguite come parte del passaggio della pipeline di distribuzione, subito dopo la distribuzione di eventuali pacchetti di contenuto. Queste impostazioni utilizzano il comportamento standard AEM Dispatcher. Per configurare:

            1. Sotto **PERCORSO** fornisci un percorso di contenuto.
            1. Sotto **TIPO**, seleziona l’azione da intraprendere su quel percorso.
            * **Flush** - Esegui un’invalidazione della cache, simile a quando il contenuto viene attivato da un’istanza di authoring a un’istanza di pubblicazione.
            * **Annulla validità** - Esegue l&#39;eliminazione della cache.
            1. Fai clic su **Aggiungi percorso** per aggiungere il percorso specificato. Puoi aggiungere fino a 100 percorsi per ambiente.

         ![Configurazione del Dispatcher](/help/using/assets/configure-pipelines/dispatcher-stage.png)

         >[!TIP]
         >
         >In generale, l’utilizzo dell’azione di annullamento della validità è preferibile, ma in alcuni casi può essere richiesto lo scaricamento, soprattutto quando si utilizzano le librerie client di HTML AEM.

      1. In **PRODUZIONE** Puoi definire il modo in cui la pipeline viene eseguita nell’ambiente di produzione.

         * **Opzioni di distribuzione** - Puoi definire i parametri che controllano la distribuzione di produzione.

            * **Usa approvazione in tempo reale** - Una distribuzione deve essere approvata manualmente da un utente con **Proprietario business**, **Project Manager** oppure **Gestione distribuzione** tramite [!UICONTROL Cloud Manager] Interfaccia utente.
            * **Pianificato** - Questa opzione interrompe la pipeline prima dell’implementazione di produzione per consentirne la pianificazione. Se questa opzione è selezionata, la pipeline si arresta dopo la distribuzione nell’ambiente di staging e richiede all’utente di eseguire l’azione.
               * **Ora** - Questa opzione viene implementata immediatamente in produzione, completando in modo efficace la pipeline.
               * **Data** - Questa opzione consente all’utente di pianificare un’ora in cui la distribuzione deve essere completata.
               * **Interrompi esecuzione** - Questa opzione interrompe la distribuzione in produzione.

            >[!TIP]
            >
            >Fare riferimento al documento [Distribuisci il tuo codice,](deploying-code.md) per scoprire come impostare la pianificazione della distribuzione o eseguire immediatamente la pipeline.

            * **Usa sorveglianza CSE** - Se questa opzione è selezionata, viene attivato un CSE per avviare effettivamente la distribuzione. Quando crei o modifichi una pipeline quando questa opzione è abilitata, la funzione **Gestione distribuzione** Il ruolo dispone delle seguenti opzioni.

               * **Qualsiasi caso** - Questa opzione consente a qualsiasi CSE disponibile di avviare la distribuzione.
               * **Il mio caso** - Questa opzione consente di avviare la distribuzione solo il CSE specifico assegnato al cliente. Questo vale anche per il backup designato del CSE se il CSE assegnato non è disponibile.

            ![Opzioni di distribuzione di produzione](/help/using/assets/configure-pipelines/prod-deploymentoptions.png)

         * **Configurazione del Dispatcher** - Definisci la configurazione del dispatcher per l’ambiente di produzione. Le opzioni sono le stesse dell&#39;ambiente di staging.











1. Fai clic su **Continua** per passare al **Test della fase** scheda in cui puoi configurare AEM Sites e AEM Assets Performance Testing, a seconda dei prodotti per i quali hai concesso la licenza.

   >[!TIP]
   >
   >Consulta il documento [Risultati dei test](understand-your-test-results.md#performance-testing) per maggiori dettagli sulle opzioni disponibili nella **Test della fase** scheda .

   1. Sotto la **Distribuzione dei contenuti dei siti/Peso del caricamento distribuito** Questa sezione descrive come configurare il test delle prestazioni dei siti in base alla ponderazione delle richieste di pagina tra i tre set di pagine, che può essere abilitata o disabilitata.

      * **Pagine Live popolari**
      * **Altre pagine live**
      * **Nuove pagine**

      ![Peso di carico dei siti](/help/using/assets/configure-pipelines/add-prod5.png)

   1. Sotto la **Distribuzione di test delle prestazioni delle risorse** definisci la distribuzione di test di immagini e PDF e le tue risorse di test.

      * **Immagini** - Regolare il cursore per regolare la suddivisione del test tra immagini e PDF.
      * **PDF** - Regolare il cursore per regolare la suddivisione del test tra immagini e PDF.

      * Definisci le risorse personalizzate caricandole.

         1. **FORMATO** - Scegli se la risorsa personalizzata è un PDF di un’immagine.
         1. **NOME FILE** - Utilizzare il pulsante del browser file per selezionare un&#39;immagine dal computer locale.
         1. **Aggiungi file di prova** - Fai clic su per caricare la risorsa selezionata.

      ![Distribuzione dei test delle risorse](/help/using/assets/configure-pipelines/add-prod6.png)



1. Fai clic su **Salva** per completare l’aggiunta della pipeline di produzione.














### Modifica di una pipeline di produzione {#editing-prod-pipeline}

Puoi modificare le configurazioni della pipeline dalla sezione **Panoramica del programma** pagina.

Per modificare la pipeline configurata, effettua le seguenti operazioni:

1. Passa a **Tubi** scheda da **Panoramica del programma** pagina.

1. Fai clic su **...** dal **Tubi** scheda e fai clic su **Modifica**, come illustrato nella figura seguente.

   ![](/help/using/assets/configure-pipelines/edit-prod1.png)

1. La **Modifica pipeline di produzione** viene visualizzata la finestra di dialogo.

   1. La **Configurazione** consente di aggiornare **Nome della pipeline**, **Archivio**, **Ramo Git**, **Trigger distribuzione**, **Comportamento di errore delle metriche importanti**, **Opzioni di distribuzione** e **Configurazioni del Dispatcher**.

      >[!NOTE]
      >Vedi [Aggiunta e gestione di archivi](/help/using/cloud-manager-repositories.md) per scoprire come aggiungere e gestire archivi in Cloud Manager.


   1. La **Test della fase** La scheda ti offre un’opzione per selezionare nuovamente le opzioni da **Distribuzione dei contenuti dei siti/Peso del caricamento distribuito** e **Distribuzione di test delle prestazioni delle risorse**.

1. Fai clic su **Aggiorna** una volta completata la modifica della pipeline.

### Azioni aggiuntive della pipeline di produzione {#additional-prod-actions}

#### Esecuzione di una pipeline di produzione {#run-prod}

Puoi eseguire la pipeline di produzione dalla scheda Pipelines :

1. Passa a **Tubi** scheda da **Panoramica del programma** pagina.

1. Fai clic su **...** dal **Tubi** scheda e fai clic su **Esegui**, come illustrato nella figura seguente.

   ![](/help/using/assets/configure-pipelines/prod-run.png)

#### Eliminazione di una pipeline di produzione {#delete-prod}

Puoi eliminare la pipeline di produzione dalla scheda Pipelines :

1. Passa a **Tubi** scheda da **Panoramica del programma** pagina.

1. Fai clic su **...** dal **Tubi** scheda e fai clic su **Elimina**, come illustrato nella figura seguente.

   ![](/help/using/assets/configure-pipelines/prod-delete.png)

   >[!NOTE]
   >Un utente con il ruolo di Deployment Manager ora può eliminare la pipeline di produzione in modo self-service tramite il **Elimina** dalla scheda Pipeline.

