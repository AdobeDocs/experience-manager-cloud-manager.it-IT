---
title: Gestisci ambienti
description: Scopri come utilizzare Cloud Manager per gestire i tuoi ambienti.
exl-id: 700b0b4c-1e1a-4993-b366-426b14a98f8e
source-git-commit: 6f5d51ef59aef831574bd55cee6b12a29e3d70d2
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 86%

---


# Gestisci ambienti {#managing-environments}

Scopri come utilizzare Cloud Manager per gestire i tuoi ambienti.

## Pagina Panoramica {#overview-page}

La pagina **Panoramica** di Cloud Manager include il riquadro **Ambienti** che elenca tutti gli ambienti AEM gestiti.

Ciascuno degli ambienti elencati visualizza il proprio stato associato.

![Pagina Panoramica](/help/assets/Manage-Environ-Overview.png)

## Riquadro Ambienti {#environments-tile}

Il riquadro **Ambienti** visualizza gli ambienti di produzione e staging per i quali è stato eseguito il provisioning nel programma insieme allo stato.

Lo stato è lo stato di alimentazione ricalcolato tra i nodi dell’ambiente nell’ordine di priorità seguente.

* Verde: tutti i nodi sono in esecuzione
* Rosso: uno o più nodi sono interrotti.
* Blu: uno o più nodi è in arrivo.
* Giallo: uno o più nodi prestano uno stato di alimentazione non disponibile.

![Riquadro Ambienti](/help/assets/Environments-card-new.png)

## Gestire gli ambienti {#managing-environments-with-cloud-manager}

Nel riquadro **Ambienti**, fai clic sulla riga di qualsiasi ambiente per visualizzare la schermata **Ambienti**.

La schermata **Ambienti** visualizza ogni ambiente di produzione e di staging nel programma. Il nome dell&#39;ambiente viene visualizzato sopra ogni scheda. La scheda include una tabella di nodi nell’ambiente insieme alla dimensione della CPU, all’archiviazione, all’area e allo stato.

>[!NOTE]
>
>Lo **STATO** del nodo rappresenta lo stato di alimentazione della VM e non riflette lo stato di AEM sul server. Lo stato può essere:

* Verde: in esecuzione
* Rosso: interrotto
* Blu: in arrivo
* Giallo: non disponibile

![Scheda Ambienti](/help/assets/Environments-tab.png)

>[!NOTE]
>
>Una volta eseguito il provisioning, i dettagli dell’ambiente, come un nome, non possono essere modificati.

>[!NOTE]
>
>Richiedi i registri dell’ambiente tramite il Customer Success Engineer.

## Tutorial video {#video-tutorial}

Questo video fornisce una panoramica degli ambienti di Cloud Manager composti da istanze di authoring, pubblicazione e Dispatcher AEM.

>[!VIDEO](https://video.tv.adobe.com/v/26318/) (3 minuti, 1 secondo)
