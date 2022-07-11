---
title: Gestione degli ambienti
description: Scopri come utilizzare Cloud Manager per gestire i tuoi ambienti.
exl-id: 700b0b4c-1e1a-4993-b366-426b14a98f8e
source-git-commit: 80f8707e00357f5a08dd835b846c9ee610f3e573
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 2%

---


# Gestione degli ambienti {#managing-environments}

Scopri come utilizzare Cloud Manager per gestire i tuoi ambienti.

## Pagina Panoramica {#overview-page}

La **Panoramica** la pagina di Cloud Manager include **Ambienti** riquadro che elenca tutti gli ambienti AEM gestiti.

Ciascuno degli ambienti elencati visualizza il proprio stato associato.

![Pagina Panoramica](/help/assets/Manage-Environ-Overview.png)

## Riquadro ambienti {#environments-tile}

La **Ambienti** visualizza gli ambienti di produzione e staging impostati nel programma con lo stato .

Lo stato è lo stato di alimentazione rollup tra i nodi dell’ambiente nell’ordine di priorità seguente.

* Verde - Tutti i nodi sono in esecuzione
* Rosso - Uno o più nodi vengono interrotti.
* Blu - Uno o più nodi in arrivo.
* Giallo: uno o più nodi hanno uno stato di alimentazione non disponibile.

![riquadro Ambienti](/help/assets/Environments-card-new.png)

## Gestione degli ambienti {#managing-environments-with-cloud-manager}

Sulla **Ambienti** riquadro, fai clic su **Gestisci** per visualizzare **Ambienti** schermo.

La **Ambienti** visualizza una scheda per gli ambienti di produzione e di staging (a seconda dei casi) nel programma. Il nome dell&#39;ambiente viene visualizzato sopra ogni scheda. La scheda include una tabella di nodi nell’ambiente insieme alla dimensione della t-shirt della cpu, all’archiviazione, alla regione e allo stato.

>[!NOTE]
>
>La **STATO** del nodo rappresenta lo stato di alimentazione della VM e non riflette lo stato di AEM sul server. Lo stato può essere:

* Verde - In esecuzione
* Rosso - Arrestato
* Blu - In arrivo
* Giallo - Non disponibile

![Scheda Ambienti](/help/assets/Environments-tab.png)

>[!NOTE]
>
>Se hai bisogno dei registri dell’ambiente, puoi richiederli tramite il tuo Customer Success Engineer.

## Tutorial video {#video-tutorial}

Questo video fornisce una panoramica degli ambienti Cloud Manager composti da istanze di authoring, pubblicazione e Dispatcher AEM.

>[!VIDEO](https://video.tv.adobe.com/v/26318/)
