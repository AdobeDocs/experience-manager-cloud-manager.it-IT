---
title: Monitorare gli ambienti
description: Scopri come monitorare gli ambienti in Cloud Manager.
exl-id: 32886133-d6c0-4aed-8bb0-81b84f63e825
source-git-commit: 53fb666ab6caff7a697d7f1942ce25f2bf27a2ce
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 98%

---


# Monitorare gli ambienti {#monitoring-environments}

Scopri come monitorare gli ambienti in Cloud Manager.

## Soglie delle metriche {#thresholds}

Il monitoraggio del sistema in [!UICONTROL Cloud Manager] viene eseguito osservando le singole istanze all’interno di un ambiente e tenendo traccia di varie metriche per ogni istanza. Ogni metrica dispone di due soglie definite: una soglia di *avvertenza* e una soglia *critica*.

Se una metrica supera la soglia di avvertenza (ma non la soglia critica), viene considerata in uno stato di avvertenza.

Se una metrica supera la soglia critica, viene considerata in uno stato critico.

Adobe Managed Services imposta le soglie, che è possibile visualizzare in [!UICONTROL Cloud Manager]. Nella maggior parte dei casi, le soglie sono uguali per tutti, ma in alcuni casi Adobe Managed Services può modificarle in base a esigenze specifiche. Per eventuali domande relative alle soglie, rivolgiti al tuo Customer Success Engineer (CSE).

## Accedere al monitoraggio del sistema {#accessing-system-monitoring}

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) e seleziona l’organizzazione e il programma appropriati.

1. Fai clic sull&#39;icona ![Altro, puntini di sospensione](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) del programma che desideri monitorare.
1. Nel menu, sotto l’intestazione **Gestisci**, fai clic su **Mostra monitoraggio** per aprire la pagina **Rapporti** che mostra le informazioni di monitoraggio del sistema.

   ![Impostazioni](/help/assets/first-timea1.png)

.

## Panoramica del Monitoraggio del sistema {#system-monitoring-overview}

Nella sezione **Monitoraggio del sistema** della pagina **Rapporti** sono elencati gli ambienti monitorati nel programma. Riporta lo stato di integrità di alto livello nelle seguenti quattro categorie separate:

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

Per visualizzare i dettagli di metriche specifiche, fai clic su una delle colonne di categoria di un’istanza specifica o sul titolo della categoria nel menu di navigazione a sinistra. Ogni pagina di dettagli mostra una serie di grafici per le metriche della categoria in questiione. Puoi visualizzare le metriche per tutte le istanze in un ambiente o per un’istanza specifica. Per passare dall’ambiente alle istanze, utilizza le caselle a discesa in alto a destra.

![Selezionare l’ambiente](/help/assets/System_Monitoring1.png)

Nella barra di navigazione a sinistra vengono visualizzate le metriche disponibili nella categoria attualmente selezionata per la quale sono presenti dati relativi all’ambiente e alle istanze attualmente selezionati.

Un singolo grafico mostra lo stato e un grafico dei dati nel tempo con le relative soglie. Se vengono visualizzate più istanze, i dati di ciascuna istanza sono in una serie separata.

![Grafico delle metriche](/help/assets/Monitoring_Graphs1.png)

Per nascondere una singola serie sul grafico, fai clic sulla serie nella legenda.
Ad esempio, se fai clic sulla serie delle soglie di avvertenza, verrà visualizzata solo la soglia critica.

![Modificare il grafico](/help/assets/Monitoring_Graphs2.png)

### Definizioni delle metriche {#metric-definitions}

#### Host {#host}

* **Cario per core**: numero di processi in esecuzione nella CPU. In alternativa, il numero di processi messi in coda che si trovano in uno stato di attesa medio su un periodo di uno (load1), cinque (load5) e quindici (load15) minuti.
* **Conteggio processi**: numero di processi attualmente aperti.
* **Conteggio utenti**: numero di utenti con una sessione shell attiva.
* **Utilizzo memoria**: percentuale di memoria di sistema attualmente allocata
* **Memoria JVM**: dimensione (in megabyte) dell’heap Java allocato
* **Spazio di vecchia generazione**: percentuale di memoria JVM di vecchia generazione attualmente allocata

#### Rete {#network}

* **Controllo porta CQ**: tempo di risposta in secondi per accedere a AEM o alla porta Dispatcher Esistono metriche diverse per authoring, pubblicazione e Dispatcher.

#### Archiviazione {#storage}

* **Spazio su disco**: spazio su disco utilizzato (in megabyte) per ogni punto di montaggio sull’host. Esistono metriche diverse per ogni punto di montaggio. Vi sono metriche almeno per `/` e `/mnt`, ma potrebbero essere disponibili metriche di montaggio aggiuntive relative ai punti di montaggio a seconda della configurazione specifica dell’istanza.
* **Dimensione cartella**
* **Archivio segmenti AEM**: spazio su disco (in gigabyte) utilizzato per l’archivio segmenti AEM.

#### Applicazione {#application}

* **Agente di replica**: tempo (in secondi) per un evento di replica di prova
   * Esistono metriche separate per ogni agente di replica.
* **Eliminazione dispatcher**: numero di elementi attualmente nella coda di eliminazione dispatcher

## Generazione rapporti SLA {#sla-reporting}

Scopri come visualizzare le prestazioni dell’ambiente di produzione AEM relative al contratto del livello di servizio (SLA) sottoscritto.

Il grafico seguente mostra il traguardo mensile dello SLA per il 2019.

![Grafico SLA 2018](/help/assets/SLA-Reports-one.png)

Come per i grafici di monitoraggio del sistema, quando si passa il pultatore su un punto dati vengono visualizzati i valori specifici per quel mese.

![Passaggio del puntatore su un punto dati](/help/assets/SLA-Reports-two.png)

La sezione **Analisi degli eventi** sotto questo grafico mostra l’insieme di incidenti verificatisi per il programma durante l’anno attualmente selezionato. Per ogni incidente sono riportati intervallo di tempo, causa e commenti.

![Analisi degli eventi](/help/assets/sla-reporting3.png)

## Metriche SLA {#sla-metrics}

* **Contratto autore**: SLA definito nel contratto con Adobe Managed Services per il livello di authoring.
* **SLA di authoring AMS**: disponibilità misurata per gli incidenti di factoring del livello di authoring in produzione causati da Adobe o dai nostri fornitori.
* **SLA autore**: tempo di attività misurato per il livello di authoring, esclusi i periodi di inattività pianificati, ad esempio le finestre di manutenzione.
* **Contratto utente finale**: SLA definito nel contratto con Adobe Managed Services per il livello di pubblicazione.
* **AMS SLA utente finale**: disponibilità misurate per gli incidenti di factoring del livello di pubblicazione in produzione causati da Adobe o dai nostri fornitori.
* **SLA utente finale**: tempo di attività misurato per il livello di pubblicazione, esclusi i periodi di inattività pianificati, ad esempio le finestre di manutenzione.

## Tutorial video {#video-tutorial}

Questo video descrive a grandi linee come utilizzare i grafici prodotti dai rapporti di Cloud Manager per ottenere informazioni sugli ambienti dei programmi.

>[!VIDEO](https://video.tv.adobe.com/v/328128?captions=ita)
