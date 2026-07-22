---
title: Gestire gli ambienti
description: Scopri come utilizzare Cloud Manager per gestire i tuoi ambienti.
exl-id: 700b0b4c-1e1a-4993-b366-426b14a98f8e
TQID: https://experienceleague.adobe.com/Dz3Z5i-gSNSorc7Na74RKgm3e0P9b-3vjVRdJvu6a0c
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: 0dde660205ad28bc5924a5cc14404c48a0533ceb
workflow-type: tm+mt
source-wordcount: 261
ht-degree: 57%

---

# Gestire gli ambienti {#managing-environments}

Scopri come utilizzare Cloud Manager per gestire i tuoi ambienti.

## Pagina Panoramica {#overview-page}

La pagina **Panoramica** di Cloud Manager include il riquadro **Ambienti** che elenca tutti gli ambienti AEM gestiti.

Ciascuno degli ambienti elencati visualizza il proprio stato associato.

![Pagina Panoramica](/help/assets/Manage-Environ-Overview.png)

## Riquadro Ambienti {#environments-tile}

Il riquadro **Ambienti** visualizza gli ambienti di produzione e staging per i quali è stato eseguito il provisioning nel programma insieme allo stato.

Lo stato è lo stato di alimentazione aggregato tra i nodi dell’ambiente elencati in ordine.

* Verde: tutti i nodi sono in esecuzione
* Rosso: uno o più nodi vengono arrestati.
* Blu: avvio di uno o più nodi.
* Giallo: uno o più nodi hanno uno stato di alimentazione non disponibile.

![Riquadro Ambienti](/help/assets/Environments-card-new.png)

## Gestire gli ambienti {#managing-environments-with-cloud-manager}

Nel riquadro **Ambienti**, fai clic sulla riga di qualsiasi ambiente per visualizzare la schermata **Ambienti**.

Nella schermata **Ambienti** vengono visualizzati tutti gli ambienti di produzione e di gestione temporanea del programma. Il nome dell’ambiente viene visualizzato sopra ogni scheda. La scheda include una tabella di nodi nell’ambiente insieme alle dimensioni di CPU, archiviazione, area geografica e stato.

>[!NOTE]
>
>Lo **STATO** del nodo rappresenta lo stato di alimentazione della VM e non riflette lo stato di AEM sul server. Lo stato può essere:

* Verde: in esecuzione
* Rosso: interrotto
* Blu - Avvio
* Giallo: non disponibile

![Scheda Ambienti](/help/assets/Environments-tab.png)

>[!NOTE]
>
>Una volta eseguito il provisioning, i dettagli dell’ambiente, come il nome, non possono essere modificati.

>[!NOTE]
>
>Richiedi i registri dell’ambiente tramite il rappresentante del successo dei clienti.

## Tutorial video {#video-tutorial}

Questo video fornisce un’introduzione agli ambienti Cloud Manager composti da istanze di authoring, pubblicazione e Dispatcher di AEM.

>[!VIDEO](https://video.tv.adobe.com/v/328127?captions=ita)

*(3 minuti, 1 secondo)*
