---
title: Implementare il codice
seo-title: Implementare il codice
description: 'null'
seo-description: Dopo aver configurato la pipeline (archivio, ambiente e ambiente di test), puoi distribuire il codice. Segui questa pagina per saperne di più.
uuid: 4 e 3807 e 1-437 e -4922-ba 48-0 bums bcadf 293 a 99
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: utilizzo
discoiquuid: 832 a 4647-9 b 83-4 a 9 d-b 373-30 fe 16092 b 15
translation-type: tm+mt
source-git-commit: 548d18f251cf8c4c827d2208fec04cde235ce731

---


# Implementare il codice {#deploy-your-code}

## Distribuzione del codice con Cloud Manager {#deploying-code-with-cloud-manager}

Dopo aver configurato **la pipeline** (archivio, ambiente e ambiente di test), puoi distribuire il codice.

1. Fate clic **su Distribuisci** da Cloud Manager per avviare il processo di distribuzione.

   ![](assets/Deploy1.png)

1. Viene visualizzata **la schermata Esecuzione** pipeline.

   Fate clic su **Genera** per avviare il processo.

   ![](assets/Deploy2.png)

1. Il processo completo di build distribuisce il codice.

   Le seguenti fasi sono coinvolte nel processo di creazione:

   1. Distribuzione dell'area di visualizzazione
   1. Test dello stage
   1. Distribuzione produzione
   >[!NOTE]
   >
   >Inoltre, potete esaminare i passaggi da vari processi di distribuzione visualizzando i registri, o rivedendo i risultati, per i criteri di test.

   La distribuzione **** dell'area di visualizzazione comprende i seguenti passaggi:

   * Creazione e test di unità
   * Scansione codice
   * Distribuisci nello stage
   ![](assets/Stage_Deployment1.png)

   La verifica **** dell'area di visualizzazione comprende i seguenti passaggi:

   * Test di sicurezza
   * Test delle prestazioni
   ![](assets/Stage_Testing1.png)

   La distribuzione **** produzione comprende i seguenti passaggi:

   * **Applicazione per approvazione** (se abilitata)
   * **Pianificazione distribuzione produzione** (se abilitata)
   * **Supporto CSE** (se abilitato)
   * **Distribuzione in produzione**
   ![](assets/Prod_Deployment1.png)

   >[!NOTE]
   >
   >La distribuzione **della produzione pianificata** è abilitata durante la configurazione della pipeline.
   >
   >
   >Utilizzando questa opzione potete pianificare il delframento della produzione o fare clic **su Ora** per eseguire immediatamente la distribuzione di produzione.
   >
   >
   >La data e l'ora pianificate sono specificate in termini di fuso orario dell'utente.
   >
   >
   >Fate clic **su Conferma** per verificare le impostazioni.

   ![](assets/Production_Deployment1.png)

   Una volta confermata la pianificazione della distribuzione, la distribuzione del codice viene completata.

   Viene visualizzata la schermata seguente, quando **l** 'opzione Ora è selezionata dal passaggio precedente.

   ![](assets/Production_Deployment2.png)

## Processo di distribuzione {#deployment-process}

Nella sezione seguente sono descritti i pacchetti di AEM e di dispatcher distribuiti nella fase dell'area di visualizzazione e nella fase di produzione.

Cloud Manager carica tutti i file di destinazione/*.zip generati dal processo di creazione in un percorso di archiviazione. Questi artefatti vengono recuperati da questa posizione durante le fasi distribuite della pipeline.

Quando Cloud Manager distribuisce in topologie di non produzione, l'obiettivo è quello di completare la distribuzione il più rapidamente possibile e quindi gli artefatti vengono distribuiti simultaneamente in tutti i nodi come segue:

1. Cloud Manager determina se ogni artefatto è un pacchetto AEM o dispatcher.
1. Cloud Manager rimuove tutti i dispatcher dal sistema di bilanciamento del carico per isolare l'ambiente durante la distribuzione.
1. Ogni artefatto AEM viene distribuito in ogni istanza AEM tramite API Package Manager, con dipendenze del pacchetto che determinano l'ordine di distribuzione.

   Per ulteriori informazioni su come utilizzare i pacchetti per installare nuove funzionalità, trasferire il contenuto tra le istanze ed eseguire il backup del contenuto dell'archivio, consultate Come utilizzare i pacchetti.

   >[!NOTE]
   >
   >Tutti gli artefatti AEM vengono distribuiti sia all'autore che agli editori. I runmodes devono essere utilizzati quando sono necessarie configurazioni specifiche del nodo. Per ulteriori informazioni su come i runmodes consentono di ottimizzare l'istanza di AEM per una funzione specifica, consultate Modalità di esecuzione.

1. L'artefatto del dispatcher viene distribuito a ogni dispatcher come segue:

   1. Le configurazioni correnti vengono sottoposte a backup e copiate in una posizione temporanea
   1. Tutte le configurazioni vengono eliminate eccetto i file immutabili. Per ulteriori informazioni, consulta Gestione delle configurazioni del dispatcher. In questo modo si cancella le directory per assicurare che non vengano lasciati precedenti i file orfani.
   1. L'artefatto viene estratto nella directory httpd. I file immutabili non vengono sovrascritti. Eventuali modifiche apportate a file immutabili nell'archivio Git verranno ignorate al momento della distribuzione. Questi file sono fondamentali per il framework di dispatcher AMS e non possono essere modificati.
   1. Apache esegue un test di configurazione. Se non vengono trovati errori, il servizio viene ricaricato. Se si verifica un errore, le configurazioni vengono ripristinate dal backup, il servizio viene ricaricato e l'errore viene riportato nuovamente a Cloud Manager.
   1. Ogni percorso specificato nella configurazione della pipeline viene invalidato o scaricato dalla cache del dispatcher.
   >[!NOTE]
   >
   >Cloud Manager prevede che l'artefatto del dispatcher contenga il set completo di file. Tutti i file di configurazione di dispatcher devono essere presenti nell'archivio git. I file o le cartelle mancanti generano un errore di distribuzione.

1. Dopo l'avvenuta distribuzione di tutti i pacchetti AEM e di dispatcher a tutti i nodi, i dispatcher vengono aggiunti nuovamente al sistema di bilanciamento del carico e la distribuzione è completa.

### Distribuzione a fase produzione {#deployment-production-phase}

Il processo di distribuzione delle topologie di produzione varia leggermente per ridurre al minimo l'impatto sui visitatori del sito AEM.

Le distribuzioni di produzione seguono in genere gli stessi passaggi descritti qui sopra, ma in modalità di scorrimento:

1. Distribuisci pacchetti AEM all'autore.
1. Scollegare dispatcher 1 da un sistema di bilanciamento del carico.
1. Distribuite i pacchetti AEM per pubblicare 1 e il pacchetto di dispatcher su dispatcher 1, svuotate la cache del dispatcher.
1. Porta il dispatcher 1 nel sistema di bilanciamento del carico.
1. Una volta che dispatcher 1 è tornato in servizio, dissociate dispatcher 2 da the load finder.
1. Distribuite i pacchetti AEM per pubblicare 2 e il pacchetto di dispatcher su dispatcher 2, svuotate la cache del dispatcher.
1. Porta il dispatcher 2 nel sistema di bilanciamento del carico.
Questo processo continua finché la distribuzione non raggiunge tutti gli editori e i dispatcher nella topologia.


