---
title: Ambienti di monitoraggio
description: Scopri come monitorare gli ambienti in Cloud Manager.
exl-id: 32886133-d6c0-4aed-8bb0-81b84f63e825
source-git-commit: 5907ca6337d33c26ff19a14bfeb358cd9f7b935d
workflow-type: tm+mt
source-wordcount: '933'
ht-degree: 0%

---


# Ambienti di monitoraggio {#monitoring-environments}

Scopri come monitorare gli ambienti in Cloud Manager.

## Soglie metriche {#thresholds}

Monitoraggio del sistema in [!UICONTROL Cloud Manager] viene eseguito osservando le singole istanze all’interno di un ambiente e monitorando una varietà di metriche per ogni istanza. Ogni metrica ha due soglie definite: una soglia di avviso e una soglia critica.

Se una metrica supera la soglia critica, viene considerata in uno stato critico. Se una metrica supera la soglia di avviso (ma è al di sotto della soglia critica), viene considerata come in uno stato di avviso. Le soglie sono impostate da Adobe Managed Services e possono essere visualizzate in [!UICONTROL Cloud Manager]. Nella maggior parte dei casi, le soglie sono coerenti tra i clienti, ma in alcuni casi Adobe Managed Services modificherà le soglie in base a specifiche esigenze dei clienti. Le domande sulle soglie devono essere indirizzate al tuo Customer Success Engineer (CSE).

## Accesso al monitoraggio del sistema {#accessing-system-monitoring}

Segui questi passaggi per accedere al monitoraggio del sistema.

1. Accedi a **Managed Services - Programmi** pagina di destinazione.

   ![Programmi di servizi gestiti](/help/assets/ProgramLanding.png)

1. Fai clic sulla quarta icona sulla scheda del programma.

   ![Impostazioni](/help/assets/first-timea1.png)


In alternativa, puoi passare alla **Monitoraggio del sistema** pagina di destinazione attraverso **Rapporti** voce di menu di navigazione globale all&#39;interno di [!UICONTROL Cloud Manager].

## Panoramica del monitoraggio del sistema {#system-monitoring-overview}

Nella pagina Panoramica sul monitoraggio del sistema sono elencati gli ambienti monitorati nel programma e vengono forniti rapporti sullo stato di salute di alto livello in quattro diverse categorie:

* Host
* Archiviazione
* Rete
* Applicazione

Lo stato di ciascuna categoria è un riepilogo delle singole metriche. Se una metrica in una categoria si trova nello stato critico, l’intera categoria si trova in uno stato critico ai fini della pagina di panoramica. Lo stesso riepilogo può essere visualizzato a livello di ambiente e di istanza.

![Panoramica sul monitoraggio del sistema](/help/assets/System-Monitoring-Reports.png)

>[!NOTE]
>
>Per impostazione predefinita, quando si passa a questa pagina, le istanze dell’ambiente di produzione sono visibili, ma è possibile visualizzare anche altri ambienti.

## Dettagli sul monitoraggio del sistema {#system-monitoring-detail}

Per visualizzare i dettagli di metriche specifiche, puoi fare clic su una delle categorie nella navigazione a sinistra oppure fare clic su uno degli indicatori di categoria per una specifica istanza. Ogni pagina di dettaglio mostra una serie di grafici per le metriche all’interno di tale categoria. Puoi visualizzare le metriche per tutte le istanze in un ambiente o per un&#39;istanza specifica. Puoi passare dall’ambiente alle istanze utilizzando le caselle a discesa nell’angolo in alto a destra.

![Seleziona ambiente](/help/assets/System_Monitoring1.png)

Nella navigazione a sinistra vengono visualizzate le metriche disponibili all’interno della categoria attualmente selezionata per la quale sono presenti dati per l’ambiente e le istanze selezionati.

![Monitoraggio delle metriche](/help/assets/System_Monitoring2.png)

Un singolo grafico mostra lo stato e un grafico dei dati nel tempo insieme alle soglie. Se vengono visualizzate più istanze, i dati di ciascuna istanza saranno su una serie separata.

![Grafico delle metriche](/help/assets/Monitoring_Graphs1.png)

Le singole serie possono essere nascoste su un grafico facendo clic sulla serie nella legenda.
Ad esempio, se fai clic sulla serie di soglie di avviso, visualizzerai solo la soglia critica.

![Modifica grafico](/help/assets/Monitoring_Graphs2.png)

### Definizioni delle metriche {#metric-definitions}

#### Host {#host}

* **Carica per core**: Il numero di processi che vengono eseguiti dalla CPU o che si trovano in uno stato di attesa medio su un periodo di uno (carico1), cinque (carico5) e quindici (carico15) minuti
* **Conteggio processi**: Numero di processi attualmente aperti
* **Conteggio utenti**: Il numero di utenti con una sessione shell attiva
* **Utilizzo della memoria**: Percentuale di memoria di sistema attualmente allocata
* **Memoria JVM**: Dimensione (in megabyte) dell&#39;heap Java allocato
* **Spazio di vecchia generazione**: Percentuale della memoria di vecchia generazione JVM attualmente allocata

#### Rete {#network}

* **Controllo porta CQ**: Tempo di risposta in secondi per accedere alla porta AEM o Dispatcher
   * Esistono diverse metriche per l’autore, la pubblicazione e il dispatcher.

#### Archiviazione {#storage}

* **Spazio su disco**: Lo spazio su disco utilizzato (in megabyte) per ogni punto di montaggio sull&#39;host
   * Esistono diverse metriche per ogni punto di montaggio.
   * Almeno ci sono metriche per `/` e `/mnt`, ma potrebbero essere disponibili metriche aggiuntive relative ai punti di montaggio a seconda della configurazione specifica dell’istanza.
* **Dimensioni cartella**
* **Archivio segmenti AEM**: Spazio su disco utilizzato (in gigabyte) per l’archivio segmenti AEM

#### Applicazione {#application}

* **Agente di replica**: Tempo (in secondi) per un evento di replica di prova
   * Esistono metriche separate per ogni agente di replica.
* **Flush del Dispatcher**: Numero di elementi attualmente nella coda di scaricamento del dispatcher

## Generazione rapporti SLA {#sla-reporting}

I clienti possono vedere le prestazioni del proprio ambiente di produzione AEM rispetto al contratto di servizio (SLA). È disponibile tramite un sottomenu nella sezione **Rapporti** schermo.

Il grafico seguente mostra il raggiungimento mensile dello SLA per il 2018.

![Grafico SLA 2018](/help/assets/SLA-Reports-one.png)

Come per i grafici di monitoraggio del sistema, il passaggio in un punto dati mostra i valori specifici per quel mese.

![Rotazione punto dati](/help/assets/SLA-Reports-two.png)

La **Analisi degli eventi** la sezione sotto questo grafico mostra l&#39;insieme di incidenti verificatisi per il programma durante l&#39;anno attualmente selezionato. Ogni incidente ha un intervallo di tempo, una causa e una serie di commenti.

![Analisi degli eventi](/help/assets/sla-reporting3.png)

## Metriche SLA {#sla-metrics}

* **Contratto autore**: Si tratta dello SLA definito nel contratto con Adobe Managed Services per il livello di authoring.
* **SLA autore AMS**: Questo è il tempo di attività misurato degli incidenti di factoring del livello di authoring di produzione causati da Adobi o nostri fornitori.
* **Author SLA**: Questo è il tempo di attività misurato del livello di authoring che ignora i tempi di inattività pianificati, come le finestre di manutenzione.
* **Contratto per l&#39;utente finale**: Si tratta dello SLA definito nel contratto con Adobe Managed Services per il livello di pubblicazione.
* **SLA utente finale AMS**: Questo è il tempo di attività misurato degli incidenti di factoring del livello di pubblicazione della produzione causati da Adobe o nostri fornitori.
* **SLA utente finale**: Questo è il tempo di attività misurato del livello di pubblicazione ignorando i tempi di inattività pianificati, come le finestre di manutenzione.

## Tutorial video {#video-tutorial}

Questo video fornisce una panoramica sull’utilizzo dei grafici prodotti da Cloud Manager Reports per una visualizzazione negli ambienti dei programmi.

>[!VIDEO](https://video.tv.adobe.com/v/26315/)
