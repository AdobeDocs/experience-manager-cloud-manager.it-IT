---
title: Gestire gli ambienti
seo-title: Gestire gli ambienti
description: Scopri l'ambiente di Cloud Manager
seo-description: Seguite questa pagina per visualizzare l'elenco degli ambienti di produzione e non produzione utilizzati per configurare ed eseguire la pipeline CI/CD in Cloud Manager.
uuid: 04e67572-11db-4d5d-acf3-fd7f644a95f0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: c5b39de2-3a9b-437f-98e8-e6e6249a5b3a
translation-type: tm+mt
source-git-commit: 2dda85baa5e7ed9bfd8933df3580ec6fc3c210fd
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 3%

---


# Gestire gli ambienti {#manage-your-environments}

La pagina **Panoramica** di Cloud Manager include la sezione **Ambienti** che elenca tutti gli ambienti AEM gestiti.

Ciascuno degli ambienti elencati visualizza il relativo stato associato.

![](assets/Manage-Environ-Overview.png)

## Esercitazione video {#video-tutorial}

### Panoramica dell&#39;ambiente di Cloud Manager {#environ-video}

Il video seguente fornisce una panoramica sugli ambienti di Cloud Manager composti da istanze di AEM Author, AEM Publish e Dispatcher.

>[!VIDEO](https://video.tv.adobe.com/v/26318/)

## Accesso agli ambienti in Cloud Manager {#accessing-environments-in-cloud-manager}

La sezione **Ambienti** visualizza gli ambienti di produzione e fase predisposti nel programma insieme allo stato.

Lo stato è lo stato di alimentazione rollup tra i nodi nell&#39;ambiente. È verde se tutti i nodi sono in esecuzione, rosso se anche un nodo viene arrestato, blu se anche un nodo è in arrivo, giallo se anche un nodo ha uno stato di alimentazione non disponibile (in questo ordine di priorità).

![](assets/Environments-card-new.png)

### Ambienti {#environments}

Fare clic su **Gestisci** per visualizzare la schermata **Ambienti**.

Nella schermata **Ambienti** viene visualizzata una scheda per gli ambienti *Produzione* e *Stage* (a seconda dei casi) del programma. Il nome dell&#39;ambiente è visualizzato sopra ogni scheda. La scheda include una tabella di nodi nell&#39;ambiente insieme alla dimensione della t-shirt della cpu, dello storage, della regione e dello stato.

>[!NOTE]
>
>Il **STATUS** del nodo rappresenta lo stato di alimentazione della VM e non riflette lo stato del AEM sul server. Lo stato può essere **Running** (cerchio verde), **Stopped** (cerchio rosso), **Coming up** (cerchio blu) o **Unavailable** (cerchio giallo).

![](assets/Environments-tab.png)
