---
title: Monitorare gli ambienti
seo-title: Monitorare gli ambienti
description: 'null'
seo-description: Segui questa pagina per saperne di più sul monitoraggio del sistema in Cloud Manager che viene fatto osservando le singole istanze all'interno di un ambiente e monitorando una serie di metriche per ogni istanza.
translation-type: tm+mt
source-git-commit: 548d18f251cf8c4c827d2208fec04cde235ce731

---


# Monitoraggio del sistema {#system-monitoring}

Il monitoraggio del sistema in [!UICONTROL Cloud Manager] viene eseguito osservando le singole istanze all'interno di un ambiente e monitorando una serie di metriche per ogni istanza. Ogni metrica ha due soglie definite, una soglia *di* avviso e una soglia ** critica.

Se una metrica supera la sua soglia critica, è considerata in stato critico; se una metrica supera la soglia di avviso (ma è al di sotto della soglia critica), viene considerata in stato di avviso. Le soglie sono impostate da Adobe Managed Services e possono essere visualizzate in [!UICONTROL Cloud Manager]. Nella maggior parte dei casi, le soglie sono coerenti tra i clienti, ma in alcuni casi i servizi gestiti Adobe modificheranno le soglie in base a specifiche esigenze dei clienti. Le domande sulle soglie devono essere indirizzate al Customer Success Engineer (CSE).

## Passaggio al monitoraggio del sistema {#navigating-system-monitoring}

Per accedere alla funzione di monitoraggio del sistema è possibile procedere in due modi.

1. Accedi alla pagina di destinazione **Servizi gestiti - Programmi** .

   ![](assets/ProgramLanding.png)

1. Fare clic sulla terza icona sulla scheda del programma.

   ![](assets/program-card.png)

   *Oppure*,

* Passate alla pagina di destinazione **System Monitoring** (Monitoraggio **del sistema) attraverso la voce di menu di navigazione globale** Reports [!UICONTROL Cloud Manager]all'interno.


## Pagina Panoramica del monitoraggio del sistema {#system-monitoring-overview-page}

Nella pagina Panoramica del monitoraggio del sistema sono elencati gli ambienti monitorati nel programma e vengono riportati i loro stati di salute di alto livello in quattro diverse categorie:

* **Host**
* **Archiviazione**
* **Rete**
* **Applicazione**

Lo stato di ciascuna categoria è un riepilogo di singole metriche. Se una metrica in una categoria è in stato critico, l’intera categoria è in stato critico ai fini della pagina di panoramica. Lo stesso riepilogo può essere visualizzato a livello di ambiente e di istanza.

![](assets/Reports.png)

>[!NOTE]
>
>Per impostazione predefinita, quando si passa a questa pagina, le istanze dell'ambiente di produzione sono visibili, ma è possibile aprire anche altri ambienti.

## Dettagli di monitoraggio del sistema {#system-monitoring-detail}

Per visualizzare i dettagli di metriche specifiche, potete fare clic su una delle categorie nella navigazione a sinistra oppure fare clic su uno degli indicatori di categoria per un'istanza specifica. Ogni pagina di dettaglio mostra una serie di grafici per le metriche all'interno di tale categoria. Puoi visualizzare le metriche per tutte le istanze in un ambiente o per un'istanza specifica. È possibile passare dall'ambiente alle istanze utilizzando le caselle a discesa nell'angolo superiore destro.

![](assets/System_Monitoring1.png)

La navigazione a sinistra mostrerà le metriche disponibili all'interno della categoria attualmente selezionata per la quale sono presenti dati per l'ambiente e le istanze selezionati.

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
* Memoria JVM (heap): la dimensione (in megabyte) dell'heap Java allocato.
* Spazio di vecchia generazione: la percentuale di memoria di vecchia generazione JVM attualmente allocata.

**Rete**

* Controllo porta CQ: Tempo di risposta in secondi per accedere alla porta AEM o Dispatcher. Esistono diverse metriche per autore, pubblicazione e dispatcher.

**Archiviazione**

* Spazio su disco: Lo spazio su disco utilizzato (in megabyte) per ogni punto di montaggio sull'host. Esistono diverse metriche per ogni punto di montaggio. Vedrai almeno le metriche per "/" e "/mnt", ma potrebbero essere disponibili ulteriori metriche del punto di montaggio a seconda della configurazione dell'istanza specifica.
* Dimensione cartella: Archivio segmenti AEM: Lo spazio su disco utilizzato (in Gigabyte) per AEM Segment Store.

**Applicazione**

* Agente di replica: Tempo, in secondi, per un evento di replica di prova. Esistono metriche separate per ciascun agente di replica.
* Dispatcher Flush: Numero di elementi attualmente presenti nella coda di eliminazione del dispatcher.

## Report SLA {#sla-reporting}

I clienti possono vedere le prestazioni dell’ambiente AEM di produzione in relazione al contratto di assistenza a livello di contratto (SLA). È disponibile tramite un sottomenu nella schermata Rapporti.
Ad esempio, il grafico seguente mostra il raggiungimento mensile dello SLA per il 2018.

![](assets/sla-reporting1.png)

Come per i grafici di monitoraggio del sistema, il passaggio del mouse su un punto dati mostra i valori specifici per quel mese.

![](assets/sla-reporting2.png)

La sezione Analisi evento sotto questo grafico mostra la serie di incidenti verificatisi per il programma durante l'anno attualmente selezionato. Ogni incidente ha un intervallo di tempo, una causa e una serie di commenti.

![](assets/sla-reporting3.png)

## Metriche SLA {#sla-metrics}

* **Contratto** autore: Si tratta dello SLA definito nel contratto con Adobe Managed Services per il livello di autore.

* **SLA** autore AMS: Questo è il tempo di attività misurato degli incidenti di factoring relativi al livello dell'autore della produzione causati da Adobe o dai nostri fornitori.

* **SLA** autore: Si tratta del tempo di attività misurato del livello di authoring, ignorando i tempi di inattività pianificati come finestre di manutenzione.

* **Contratto** utente finale: Si tratta dello SLA definito nel contratto con Adobe Managed Services per il livello di pubblicazione.

* **SLA** utente finale AMS: Questo è il tempo di attività misurato degli incidenti di factoring del livello di pubblicazione della produzione causati da Adobe o dai nostri fornitori.

* **SLA** utente finale: Si tratta del tempo di attività misurato del livello di pubblicazione, ignorando i tempi di inattività pianificati come finestre di manutenzione.