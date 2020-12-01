---
title: Monitorare gli ambienti
seo-title: Monitorare gli ambienti
description: 'null'
seo-description: Segui questa pagina per saperne di più sul monitoraggio del sistema in Cloud Manager che viene fatto osservando le singole istanze all'interno di un ambiente e monitorando una serie di metriche per ogni istanza.
translation-type: tm+mt
source-git-commit: 16893b8bcd2b2d681a14bb6be3786e358e1952fb
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Monitoraggio del sistema {#system-monitoring}

Il monitoraggio del sistema in [!UICONTROL Cloud Manager] viene eseguito osservando le singole istanze all&#39;interno di un ambiente e monitorando diverse metriche per ogni istanza. Ogni metrica ha due soglie definite: una *soglia di avviso* e una *soglia critica*.

Se una metrica supera la sua soglia critica, è considerata in stato critico; se una metrica supera la soglia di avviso (ma è al di sotto della soglia critica), viene considerata in stato di avviso. Le soglie sono impostate da Adobe Managed Services e possono essere visualizzate in [!UICONTROL Cloud Manager]. Nella maggior parte dei casi, le soglie sono coerenti tra i clienti, ma in alcuni casi i servizi gestiti Adobe modificheranno le soglie in base a specifiche esigenze dei clienti. Le domande sulle soglie devono essere indirizzate al Customer Success Engineer (CSE).

## Passaggio al monitoraggio del sistema {#navigating-system-monitoring}

Per accedere alla funzione di monitoraggio del sistema è possibile procedere in due modi.

1. Accedete alla pagina di destinazione **Managed Services - Programmi**.

   ![](assets/ProgramLanding.png)

1. Fare clic sulla quarta icona sulla scheda del programma.

   ![](assets/first-timea1.png)

   *Oppure*,

* Andate alla pagina di destinazione **System Monitoring** attraverso la voce di menu di navigazione globale **Reports** all&#39;interno di [!UICONTROL Cloud Manager].


## Pagina Panoramica del monitoraggio del sistema {#system-monitoring-overview-page}

Nella pagina Panoramica del monitoraggio del sistema sono elencati gli ambienti monitorati nel programma e vengono riportati i loro stati di salute di alto livello in quattro diverse categorie:

* **Host**
* **Archiviazione**
* **Rete**
* **Applicazione**

Lo stato di ciascuna categoria è un riepilogo di singole metriche. Se una metrica in una categoria è in stato critico, l’intera categoria è in stato critico ai fini della pagina di panoramica. Lo stesso riepilogo può essere visualizzato a livello di ambiente e di istanza.

![](assets/System-Monitoring-Reports.png)

>[!NOTE]
>
>Per impostazione predefinita, quando si passa a questa pagina, le istanze dell&#39;ambiente di produzione sono visibili, ma è possibile aprire anche altri ambienti.

## Esercitazione video {#video-tutorial}

### Panoramica dei report di Cloud Manager {#reports-video}

I report di Cloud Manager forniscono una visualizzazione degli ambienti e delle istanze AEM del programma tramite un set di grafici che eseguono il report e tengono traccia di una serie di metriche per ogni istanza AEM.
Per ulteriori informazioni, consulta il video sottostante.

>[!VIDEO](https://video.tv.adobe.com/v/26315/)

## Dettagli di monitoraggio del sistema {#system-monitoring-detail}

Per visualizzare i dettagli di metriche specifiche, potete fare clic su una delle categorie nella navigazione a sinistra oppure fare clic su uno degli indicatori di categoria per un&#39;istanza specifica. Ogni pagina di dettaglio mostra una serie di grafici per le metriche all&#39;interno di tale categoria. Puoi visualizzare le metriche per tutte le istanze in un ambiente o per un&#39;istanza specifica. È possibile passare dall&#39;ambiente alle istanze utilizzando le caselle a discesa nell&#39;angolo superiore destro.

![](assets/System_Monitoring1.png)

La navigazione a sinistra mostrerà le metriche disponibili all&#39;interno della categoria attualmente selezionata per la quale sono presenti dati per l&#39;ambiente e le istanze selezionati.

![](assets/System_Monitoring2.png)

Un singolo grafico mostra lo stato e un grafico dei dati nel tempo, insieme alle soglie. Se vengono visualizzate più istanze, i dati di ciascuna istanza si trovano in una serie separata.

![](assets/Monitoring_Graphs1.png)

È possibile nascondere una singola serie su un grafico facendo clic sulla serie nella legenda.
Ad esempio, se fai clic sulla serie di soglie di avviso, verrà visualizzata solo la soglia critica.

![](assets/Monitoring_Graphs2.png)

### Definizioni metriche {#metric-definitions}

**Host**

* Carica per core: il numero di processi che vengono eseguiti dalla CPU o che si trovano in uno stato di attesa medio su un periodo di uno (load1), cinque (load5) e quindici (load15) minuti.
* Conteggio processi: il numero di processi attualmente aperti.
* Conteggio utenti: il numero di utenti con una sessione shell attiva.
* Utilizzo memoria: la percentuale di memoria di sistema attualmente allocata.
* Memoria JVM (heap): la dimensione (in megabyte) dell&#39;heap Java allocato.
* Spazio di vecchia generazione: la percentuale di memoria di vecchia generazione JVM attualmente allocata.

**Rete**

* Controllo porta CQ: Tempo di risposta in secondi per accedere alla porta AEM o Dispatcher. Esistono diverse metriche per autore, pubblicazione e dispatcher.

**Archiviazione**

* Spazio su disco: Lo spazio su disco utilizzato (in megabyte) per ogni punto di montaggio sull&#39;host. Esistono diverse metriche per ogni punto di montaggio. Vedrai almeno le metriche per &quot;/&quot; e &quot;/mnt&quot;, ma potrebbero essere disponibili ulteriori metriche del punto di montaggio a seconda della configurazione dell&#39;istanza specifica.
* Dimensione cartella: AEM archivio segmenti: Lo spazio su disco utilizzato (in Gigabyte) per AEM Segment Store.

**Applicazione**

* Agente di replica: Tempo, in secondi, per un evento di replica di prova. Esistono metriche separate per ciascun agente di replica.
* Dispatcher Flush: Numero di elementi attualmente presenti nella coda di eliminazione del dispatcher.

## Report SLA {#sla-reporting}

I clienti possono vedere le prestazioni del proprio ambiente di produzione AEM rispetto al contratto di assistenza (SLA). Questo è disponibile tramite un sottomenu nella schermata Rapporti.
Ad esempio, il grafico seguente mostra il raggiungimento mensile dello SLA per il 2018.

![](assets/SLA-Reports-one.png)

Come per i grafici di monitoraggio del sistema, il passaggio del mouse su un punto dati mostra i valori specifici per quel mese.

![](assets/SLA-Reports-two.png)

La sezione Analisi evento sotto questo grafico mostra la serie di incidenti verificatisi per il programma durante l&#39;anno selezionato. Ogni incidente ha un intervallo di tempo, una causa e una serie di commenti.

![](assets/sla-reporting3.png)

## Metriche SLA {#sla-metrics}

* **Contratto** autore: Si tratta dello SLA definito nel contratto con Adobe Managed Services per il livello di autore.

* **SLA** autore AMS: Questo è il tempo di attività misurato degli incidenti di factoring di livello autore di produzione causati da  Adobe o i nostri venditori.

* **SLA** autore: Si tratta del tempo di attività misurato del livello di authoring, ignorando i tempi di inattività pianificati come finestre di manutenzione.

* **Contratto** utente finale: Si tratta dello SLA definito nel contratto con Adobe Managed Services per il livello di pubblicazione.

* **SLA** utente finale AMS: Questo è il tempo di attività misurato degli incidenti di factoring del livello di pubblicazione della produzione causati dal Adobe  o dai nostri venditori.

* **SLA** utente finale: Si tratta del tempo di attività misurato del livello di pubblicazione, ignorando i tempi di inattività pianificati come finestre di manutenzione.