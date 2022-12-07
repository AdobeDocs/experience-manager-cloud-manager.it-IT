---
title: Ambienti di monitoraggio
description: Scopri come monitorare gli ambienti in Cloud Manager.
exl-id: 32886133-d6c0-4aed-8bb0-81b84f63e825
source-git-commit: 5907ca6337d33c26ff19a14bfeb358cd9f7b935d
workflow-type: ht
source-wordcount: '939'
ht-degree: 100%

---


# Ambienti di monitoraggio {#monitoring-environments}

Scopri come monitorare gli ambienti in Cloud Manager.

## Soglie delle metriche {#thresholds}

Il monitoraggio del sistema in [!UICONTROL Cloud Manager] viene eseguito osservando le singole istanze all’interno di un ambiente e tenendo traccia di varie metriche per ogni istanza. Ogni metrica ha due soglie definite: una soglia di avvertenza e una soglia critica.

Se una metrica supera la soglia critica, viene considerata in uno stato critico. Se una metrica supera la soglia di avvertenza (ma non la soglia critica), viene considerata in uno stato di avvertenza. Le soglie sono impostate da Adobe Managed Services e possono essere visualizzate in [!UICONTROL Cloud Manager]. Nella maggior parte dei casi, le soglie sono uguali per tutti i clienti, ma in alcuni casi Adobe Managed Services potrà modificarle in base a esigenze specifiche. Per eventuali domande sulle soglie, rivolgiti al tuo Customer Success Engineer (CSE).

## Accesso al monitoraggio del sistema {#accessing-system-monitoring}

Segui questi passaggi per accedere al monitoraggio del sistema.

1. Accedi alla pagina di destinazione **Managed Services - Programmi**.

   ![Programmi Managed Services](/help/assets/ProgramLanding.png)

1. Fai clic sulla quarta icona nella scheda dei programmi.

   ![Impostazioni](/help/assets/first-timea1.png)


In alternativa, puoi passare alla pagina di destinazione del **Monitoraggio del sistema** attraverso la voce del menu di navigazione globale **Rapporti** in [!UICONTROL Cloud Manager].

## Panoramica di Monitoraggio del sistema {#system-monitoring-overview}

Nella pagina di panoramica di Monitoraggio del sistema sono elencati gli ambienti monitorati nel programma e i rapporti sullo stato di salute di alto livello in quattro categorie diverse:

* Host
* Archiviazione
* Rete
* Applicazione

Lo stato di ciascuna categoria è un riepilogo delle singole metriche. Se una metrica in una categoria si trova nello stato critico, l’intera categoria si trova in uno stato critico ai fini della pagina di panoramica. Lo stesso riepilogo può essere visualizzato a livello di ambiente e di istanza.

![Panoramica di Monitoraggio del sistema](/help/assets/System-Monitoring-Reports.png)

>[!NOTE]
>
>Per impostazione predefinita, quando si passa a questa pagina, sono visibili le istanze dell’ambiente di produzione, ma è possibile visualizzare anche altri ambienti.

## Dettagli di Monitoraggio del sistema {#system-monitoring-detail}

Per visualizzare i dettagli di specifiche metriche, fai clic su una delle categorie nella barra di navigazione a sinistra oppure su uno degli indicatori di categoria per una specifica istanza. Ogni pagina di dettagli mostra una serie di grafici per le metriche della categoria in questiione. Puoi visualizzare le metriche per tutte le istanze in un ambiente o per un’istanza specifica. Per passare dall’ambiente alle istanze, utilizza le caselle a discesa in alto a destra.

![Selezionare l’ambiente](/help/assets/System_Monitoring1.png)

Nella barra di navigazione a sinistra vengono visualizzate le metriche disponibili nella categoria attualmente selezionata per la quale sono presenti dati relativi all’ambiente e alle istanze attualmente selezionati.

![Metriche del monitoraggio](/help/assets/System_Monitoring2.png)

Un singolo grafico mostra lo stato, un grafico dei dati nel tempo e le relative soglie. Se vengono visualizzate più istanze, i dati di ciascuna istanza saranno su una serie separata.

![Grafico delle metriche](/help/assets/Monitoring_Graphs1.png)

Per nascondere una singola serie sul grafico, fai clic sulla serie nella legenda.
Ad esempio, se fai clic sulla serie delle soglie di avvertenza, verrà viusalizzata solo la soglia critica.

![Modificare il grafico](/help/assets/Monitoring_Graphs2.png)

### Definizioni delle metriche {#metric-definitions}

#### Host {#host}

* **Carico per core**: numero di processi che vengono eseguiti dalla CPU o che sono in uno stato di attesa medio su un periodo di uno (load1), cinque (load5) e quindici (load15) minuti
* **Conteggio processi**: numero di processi attualmente aperti
* **Conteggio utenti**: numero di utenti con una sessione shell attiva
* **Utilizzo della memoria**: percentuale di memoria di sistema attualmente allocata
* **Memoria JVM**: dimensione (in megabyte) dell’heap Java allocato
* **Spazio di vecchia generazione**: percentuale della memoria JVM di vecchia generazione attualmente allocata

#### Rete {#network}

* **Controllo porta CQ**: tempo di risposta in secondi per accedere alla porta di AEM o Dispatcher
   * Esistono metriche diverse per authoring, pubblicazione e Dispatcher.

#### Archiviazione {#storage}

* **Spazio su disco**: spazio su disco utilizzato (in megabyte) per ogni punto di montaggio sull’host
   * Esistono metriche diverse per ogni punto di montaggio.
   * Vi sono metriche almeno per `/` e `/mnt`, ma potrebbero essere disponibili metriche di montaggio aggiuntive relative ai punti di montaggio a seconda della configurazione specifica dell’istanza.
* **Dimensione cartella**
* **Archivio di segmenti AEM**: spazio su disco (in gigabyte) utilizzato per l’archivio di segmenti AEM

#### Applicazione {#application}

* **Agente di replica**: tempo (in secondi) per un evento di replica di prova
   * Esistono metriche separate per ogni agente di replica.
* **Svuotamento del Dispatcher**: numero di elementi attualmente nella coda di svuotamento del dispatcher

## Generazione rapporti SLA {#sla-reporting}

È possibile vedere le prestazioni del proprio ambiente di produzione AEM rispetto al livello di servizio previsto dal contratto (SLA). Tali dati sono accessibili da un sottomenu nella schermata **Rapporti**.

Il grafico seguente mostra il traguardo mensile dello SLA per il 2018.

![Grafico SLA 2018](/help/assets/SLA-Reports-one.png)

Come per i grafici di monitoraggio del sistema, quando si passa il pultatore su un punto dati vengono visualizzati i valori specifici per quel mese.

![Passaggio del puntatore su un punto dati](/help/assets/SLA-Reports-two.png)

La sezione **Analisi degli eventi** sotto questo grafico mostra l’insieme di incidenti verificatisi per il programma durante l’anno attualmente selezionato. Per ogni incidente sono riportati intervallo di tempo, causa e commenti.

![Analisi degli eventi](/help/assets/sla-reporting3.png)

## Metriche SLA {#sla-metrics}

* **Contratto autore**: SLA definito nel contratto con Adobe Managed Services per il livello di authoring.
* **SLA autore AMS**: tempo di attività misurato per gli incidenti di factoring del livello di authoring in produzione causati da Adobe o dai nostri fornitori.
* **SLA autore**: tempo di attività misurato per il livello di authoring, esclusi i periodi di inattività pianificati, ad esempio le finestre di manutenzione.
* **Contratto utente finale**: SLA definito nel contratto con Adobe Managed Services per il livello di pubblicazione.
* **AMS SLA utente finale**: tempo di attività misurato per gli incidenti di factoring del livello di pubblicazione in produzione causati da Adobe o dai nostri fornitori.
* **SLA utente finale**: tempo di attività misurato per il livello di pubblicazione, esclusi i periodi di inattività pianificati, ad esempio le finestre di manutenzione.

## Tutorial video {#video-tutorial}

Questo video descrive a grandi linee come utilizzare i grafici prodotti dai rapporti di Cloud Manager per ottenere informazioni sugli ambienti dei programmi.

>[!VIDEO](https://video.tv.adobe.com/v/26315/)
