---
title: Implementare il codice
seo-title: Implementare il codice
description: Fornisce una panoramica sul processo di distribuzione in Cloud Manager
seo-description: Scopri come distribuire il codice dopo aver configurato la pipeline (repository, ambiente e ambiente di testing)
uuid: 4e3807e1-437e-4922-ba48-0bcadf293a99
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: 832a4647-9b83-4a9d-b373-30fe16092b15
translation-type: tm+mt
source-git-commit: 2dda85baa5e7ed9bfd8933df3580ec6fc3c210fd
workflow-type: tm+mt
source-wordcount: '957'
ht-degree: 1%

---


# Implementare il codice {#deploy-your-code}

## Distribuzione del codice con Cloud Manager {#deploying-code-with-cloud-manager}

Dopo aver configurato la pipeline di produzione (repository, ambiente e ambiente di test), potete distribuire il codice.

1. Fai clic su **Distribuisci** da Cloud Manager per avviare il processo di distribuzione.

   ![](assets/Deploy1.png)

1. Viene visualizzata la schermata **Esecuzione tubazione**.

   Fare clic su **Build** per avviare il processo.

   ![](assets/Deploy2.png)

1. Il processo di compilazione completo distribuisce il codice.

   Nel processo di creazione sono coinvolte le seguenti fasi:

   1. Implementazione stage
   1. Test fase
   1. Distribuzione di produzione

   >[!NOTE]
   >
   >Inoltre, potete esaminare i passaggi da vari processi di distribuzione visualizzando i registri o rivedendo i risultati per i criteri di test.

   La **distribuzione della fase** prevede i seguenti passaggi:

   * Convalida: Questo passaggio assicura che la pipeline sia configurata per utilizzare le risorse attualmente disponibili, ad esempio che il ramo configurato esiste, gli ambienti sono disponibili.
   * Build e unit test: Questo passaggio esegue un processo di compilazione containerizzato. Per informazioni sull&#39;ambiente di compilazione, vedere [Informazioni sull&#39;ambiente di generazione](/help/using/build-environment-details.md).
   * Scansione del codice: Questo passaggio valuta la qualità del codice dell’applicazione. Per informazioni dettagliate sul processo di test, vedere [Comprendere i risultati dei test](understand-your-test-results.md).
   * Distribuisci nello stage

   ![](assets/Stage_Deployment1.png)

   La **fase di test** prevede i seguenti passaggi:

   * Test di protezione: Questo passaggio valuta l&#39;impatto del codice dell&#39;applicazione sull&#39;ambiente AEM. Per informazioni dettagliate sul processo di test, vedere [Comprendere i risultati dei test](understand-your-test-results.md).
   * Test delle prestazioni: Questo passaggio valuta le prestazioni del codice dell&#39;applicazione. Per informazioni dettagliate sul processo di test, vedere [Comprendere i risultati dei test](understand-your-test-results.md).

   ![](assets/Stage_Testing1.png)

   La **distribuzione di produzione** prevede i seguenti passaggi:

   * **Domanda di approvazione**  (se abilitata)
   * **Pianificazione distribuzione**  produzione (se abilitata)
   * **Supporto**  CSE (se abilitato)
   * **Distribuisci in produzione**

   ![](assets/Prod_Deployment1.png)

   >[!NOTE]
   >
   >La **distribuzione di produzione programmata** è abilitata durante la configurazione della pipeline.
   >
   >
   >Utilizzando questa opzione, potete pianificare la distribuzione di produzione oppure fare clic su **Now** per eseguire immediatamente la distribuzione di produzione.
   >
   >
   >La data e l&#39;ora pianificate vengono specificate in termini di fuso orario dell&#39;utente.
   >
   >
   >Fare clic su **Conferma** per verificare le impostazioni.

   ![](assets/Production_Deployment1.png)

   Una volta confermata la pianificazione della distribuzione, la distribuzione del codice viene completata.

   Viene visualizzata la schermata seguente, quando l&#39;opzione **Now** è selezionata nel passaggio precedente.

   ![](assets/Production_Deployment2.png)

## Processo di distribuzione {#deployment-process}

La sezione seguente descrive come i pacchetti AEM e dispatcher vengono distribuiti nella fase di fase e nella fase di produzione.

Cloud Manager carica tutti i file target/*.zip prodotti dal processo di creazione in una posizione di archiviazione.  Questi artefatti vengono recuperati da questa posizione durante le fasi di distribuzione della pipeline.

Quando Cloud Manager si distribuisce su topologie non di produzione, l&#39;obiettivo è completare la distribuzione il più rapidamente possibile e, di conseguenza, gli artefatti vengono distribuiti simultaneamente a tutti i nodi come segue:

1. Cloud Manager determina se ogni artifact è un pacchetto AEM o dispatcher.
1. Cloud Manager rimuove tutti i dispatcher dal sistema di bilanciamento del carico per isolare l&#39;ambiente durante la distribuzione.

   Se non è configurata diversamente, è possibile saltare le modifiche del sistema di bilanciamento del carico nelle implementazioni di sviluppo e fasi, ovvero scollegare e allegare i passaggi sia nelle condotte non di produzione, per gli ambienti di sviluppo, sia nella pipeline di produzione, per gli ambienti di fase.

   ![](assets/load_balancer.png)

   >[!NOTE]
   >
   >Questa funzionalità dovrebbe essere utilizzata principalmente da 1-1-1 clienti.

1. Ogni AEM artifact viene distribuito in ogni istanza AEM tramite le API di Package Manager, con dipendenze del pacchetto che determinano l&#39;ordine di distribuzione.

   Per ulteriori informazioni su come utilizzare i pacchetti per installare nuove funzionalità, trasferire contenuti tra le istanze ed eseguire il backup del contenuto del repository, vedere Come utilizzare i pacchetti.

   >[!NOTE]
   >
   >Tutti AEM artifact vengono distribuiti sia all&#39;autore che agli editori. Le modalità di esecuzione devono essere utilizzate quando sono necessarie configurazioni specifiche per il nodo. Per ulteriori informazioni sulle modalità di esecuzione che consentono di sintonizzare l&#39;istanza di AEM per uno scopo specifico, fare riferimento a Modalità di esecuzione.

1. L&#39;artifact del dispatcher viene distribuito a ciascun dispatcher come indicato di seguito:

   1. Le configurazioni correnti vengono sottoposte a backup e copiate in una posizione temporanea
   1. Tutte le configurazioni vengono eliminate tranne i file immutabili. Per ulteriori informazioni, consulta Gestione delle configurazioni del dispatcher. In questo modo le directory vengono cancellate per evitare che vengano lasciati indietro i file orfani.
   1. L&#39;artifact viene estratto nella directory `httpd`.  I file immutabili non vengono sovrascritti. Eventuali modifiche apportate ai file immutabili nel repository git verranno ignorate al momento della distribuzione.  Questi file sono fondamentali per il framework del dispatcher AMS e non possono essere modificati.
   1. Apache esegue un test di configurazione. Se non viene rilevato alcun errore, il servizio viene ricaricato. Se si verifica un errore, le configurazioni vengono ripristinate dal backup, il servizio viene ricaricato e l&#39;errore viene riportato a Cloud Manager.
   1. Ogni percorso specificato nella configurazione della pipeline viene invalidato o scaricato dalla cache del dispatcher.

   >[!NOTE]
   >Cloud Manager prevede che l&#39;artifact del dispatcher contenga l&#39;intero set di file.  Tutti i file di configurazione del dispatcher devono essere presenti nel repository git. I file o le cartelle mancanti genereranno un errore di distribuzione.

1. Dopo la corretta distribuzione di tutti i pacchetti di AEM e dispatcher a tutti i nodi, i dispatcher vengono aggiunti nuovamente al sistema di bilanciamento del carico e la distribuzione è completa.

   >[!NOTE]
   >È possibile ignorare le modifiche al sistema di bilanciamento del carico nelle implementazioni di sviluppo e fasi, ovvero scollegare e allegare i passaggi sia nelle condotte non di produzione, per gli ambienti di sviluppo, sia nel ciclo di produzione, per gli ambienti di fase.

### Fase di produzione {#deployment-production-phase}

Il processo di implementazione nelle topologie di produzione è leggermente diverso per ridurre al minimo l&#39;impatto sui visitatori AEM sito.

Le distribuzioni di produzione seguono generalmente gli stessi passaggi sopra, ma in modo continuo:

1. Distribuire AEM pacchetti per l&#39;authoring.
1. Scollegare dispatcher1 dal sistema di bilanciamento del carico.
1. Distribuire pacchetti AEM per publish1 e il pacchetto dispatcher per dispatcher1 nella cache del dispatcher dello scaricamento parallelo.
1. Rimettere dispatcher1 nel sistema di bilanciamento del carico.
1. Una volta che dispatcher1 è tornato in servizio, scollegare dispatcher2 dal sistema di bilanciamento del carico.
1. Distribuire pacchetti AEM a publish2 e il pacchetto dispatcher a dispatcher2 nella cache del dispatcher dello scaricamento parallelo.
1. Rimettere dispatcher2 nel sistema di bilanciamento del carico.
Questo processo continua finché la distribuzione non raggiunge tutti gli editori e i dispatcher nella topologia.


