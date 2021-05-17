---
title: Implementare il codice
seo-title: Implementare il codice
description: Fornisce una panoramica sul processo di implementazione in Cloud Manager
seo-description: Scopri come distribuire il codice una volta configurata la pipeline (archivio, ambiente e ambiente di test)
uuid: 4e3807e1-437e-4922-ba48-0bcadf293a99
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: 832a4647-9b83-4a9d-b373-30fe16092b15
feature: Distribuzione del codice
exl-id: 3d6610e5-24c2-4431-ad54-903d37f4cdb6
source-git-commit: df2f598f91201d362f54b17e4092ff6bd6a72cec
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 1%

---

# Implementare il codice {#deploy-your-code}

## Distribuzione del codice con Cloud Manager {#deploying-code-with-cloud-manager}

>[!NOTE]
>Per informazioni sulla distribuzione del codice per Cloud Manager in AEM come Cloud Service, consulta [qui](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#using-cloud-manager).

Dopo aver configurato la pipeline di produzione (archivio, ambiente e ambiente di test), è possibile distribuire il codice.

1. Fai clic su **Distribuisci** da Cloud Manager per avviare il processo di distribuzione.

   ![](assets/Deploy1.png)

1. Viene visualizzata la schermata **Esecuzione pipeline** .

   Fai clic su **Genera** per avviare il processo.

   ![](assets/Deploy2.png)

1. Il processo di compilazione completo distribuisce il codice.

   Nel processo di creazione sono coinvolte le seguenti fasi:

   1. Implementazione fase
   1. Test della fase
   1. Distribuzione di produzione

   >[!NOTE]
   >
   >Inoltre, puoi rivedere i passaggi dei vari processi di distribuzione visualizzando i registri o rivedendo i risultati per i criteri di test.

   La **distribuzione della fase** prevede i seguenti passaggi:

   * Convalida: Questo passaggio assicura che la pipeline sia configurata per utilizzare le risorse attualmente disponibili, ad esempio che il ramo configurato esista, che gli ambienti siano disponibili.
   * Build &amp; Unit Testing: Questo passaggio esegue un processo di compilazione containerizzato. Per informazioni dettagliate sull’ambiente di creazione, consulta [Informazioni sull’ambiente di generazione](/help/using/build-environment-details.md) .
   * Scansione del codice: Questo passaggio valuta la qualità del codice dell&#39;applicazione. Per informazioni dettagliate sul processo di test, consulta [Comprendere i risultati del test](understand-your-test-results.md) .
   * Distribuisci su Stage

   ![](assets/Stage_Deployment1.png)

   La **prova della fase** prevede i seguenti passaggi:

   * Test di sicurezza: Questo passaggio valuta l&#39;impatto sulla sicurezza del codice dell&#39;applicazione nell&#39;ambiente AEM. Per informazioni dettagliate sul processo di test, consulta [Comprendere i risultati del test](understand-your-test-results.md) .
   * Test delle prestazioni: Questo passaggio valuta le prestazioni del codice dell&#39;applicazione. Per informazioni dettagliate sul processo di test, consulta [Comprendere i risultati del test](understand-your-test-results.md) .

   ![](assets/Stage_Testing1.png)

   La **distribuzione di produzione** prevede i seguenti passaggi:

   * **Domanda di approvazione**  (se abilitata)
   * **Pianificazione distribuzione produzione**  (se abilitata)
   * **Supporto CSE**  (se abilitato)
   * **Distribuzione in produzione**

   ![](assets/Prod_Deployment1.png)

   >[!NOTE]
   >
   >Durante la configurazione della pipeline, viene abilitato **Pianifica distribuzione di produzione** .
   >
   >
   >Utilizzando questa opzione, puoi pianificare la distribuzione di produzione oppure fare clic su **Now** per eseguire immediatamente la distribuzione di produzione.
   >
   >
   >La data e l’ora pianificate vengono specificate in termini di fuso orario dell’utente.
   >
   >
   >Fai clic su **Conferma** per verificare le impostazioni.

   ![](assets/Production_Deployment1.png)

   Una volta confermata la pianificazione della distribuzione, la distribuzione del codice viene completata.

   Viene visualizzata la seguente schermata quando l’opzione **Now** è selezionata dal passaggio precedente.

   ![](assets/Production_Deployment2.png)

## Timeout {#timeouts}

I seguenti passaggi si interrompono se rimangono in attesa del feedback degli utenti:

| Incremento | Timeout |
|--- |--- |
| Test della qualità del codice | 7 giorni |
| Test di sicurezza | 7 giorni |
| Test delle prestazioni | 7 giorni |
| Domanda di approvazione | 7 giorni |
| Pianificazione distribuzione produzione | 7 giorni |
| Supporto CSE | 7 giorni |

## Processo di distribuzione {#deployment-process}

La sezione seguente descrive come i pacchetti AEM e dispatcher vengono distribuiti nella fase di stage e nella fase di produzione.

Cloud Manager carica tutti i file target/*.zip prodotti dal processo di compilazione in una posizione di archiviazione.  Questi artefatti vengono recuperati da questa posizione durante le fasi di distribuzione della pipeline.

Quando Cloud Manager viene implementato in topologie non di produzione, l’obiettivo è quello di completare l’implementazione il più rapidamente possibile e, pertanto, gli artefatti vengono distribuiti simultaneamente su tutti i nodi come segue:

1. Cloud Manager determina se ogni artefatto è un pacchetto AEM o dispatcher.
1. Cloud Manager rimuove tutti i dispatcher dal Load Balancer per isolare l’ambiente durante la distribuzione.

   A meno che non sia configurato diversamente, è possibile saltare le modifiche del Load Balancer nelle implementazioni di sviluppo e stage, ovvero scollegare e allegare i passaggi sia nelle pipeline non di produzione, per gli ambienti di sviluppo e nella pipeline di produzione, per gli ambienti di stage.

   ![](assets/load_balancer.png)

   >[!NOTE]
   >
   >Questa funzione dovrebbe essere utilizzata principalmente da 1-1-1 clienti.

1. Ciascun artefatto AEM viene distribuito a ogni istanza AEM tramite API di Gestione pacchetti, con dipendenze dei pacchetti che determinano l’ordine di distribuzione.

   Per ulteriori informazioni su come utilizzare i pacchetti per installare nuove funzionalità, trasferire contenuti tra le istanze e eseguire il backup del contenuto dell’archivio, consulta Come utilizzare i pacchetti.

   >[!NOTE]
   >
   >Tutti gli artefatti AEM vengono distribuiti sia all’autore che agli editori. Le modalità di esecuzione devono essere utilizzate quando sono necessarie configurazioni specifiche per il nodo. Per ulteriori informazioni su come le modalità di esecuzione consentono di ottimizzare l&#39;istanza AEM per uno scopo specifico, consulta Modalità di esecuzione .

1. L’artefatto del dispatcher viene distribuito a ciascun dispatcher come segue:

   1. Le configurazioni correnti vengono sottoposte a backup e copiate in una posizione temporanea
   1. Tutte le configurazioni vengono eliminate tranne i file immutabili. Per ulteriori informazioni, consulta Gestire le configurazioni del Dispatcher . Questo cancella le directory per garantire che non vengano lasciati indietro i file orfani.
   1. L’artefatto viene estratto nella directory `httpd`.  I file immutabili non vengono sovrascritti. Eventuali modifiche apportate ai file immutabili nell’archivio Git verranno ignorate al momento della distribuzione.  Questi file sono di base del framework del dispatcher AMS e non possono essere modificati.
   1. Apache esegue un test di configurazione. Se non viene rilevato alcun errore, il servizio viene ricaricato. Se si verifica un errore, le configurazioni vengono ripristinate dal backup, il servizio viene ricaricato e l&#39;errore viene riportato a Cloud Manager.
   1. Ogni percorso specificato nella configurazione della pipeline viene invalidato o scaricato dalla cache del dispatcher.

   >[!NOTE]
   >Cloud Manager prevede che l’artefatto del dispatcher contenga l’intero set di file.  Tutti i file di configurazione del dispatcher devono essere presenti nell’archivio Git. File o cartelle mancanti causeranno un errore di distribuzione.

1. Dopo la corretta distribuzione di tutti i pacchetti AEM e dispatcher a tutti i nodi, i dispatcher vengono aggiunti nuovamente al load balancer e la distribuzione è completa.

   >[!NOTE]
   >È possibile saltare le modifiche di Load Balancer nelle distribuzioni di sviluppo e stage, ovvero scollegare e allegare i passaggi sia nelle pipeline non di produzione, per gli ambienti di sviluppo e nella pipeline di produzione, per gli ambienti di stage.

### Fase di distribuzione alla produzione {#deployment-production-phase}

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
