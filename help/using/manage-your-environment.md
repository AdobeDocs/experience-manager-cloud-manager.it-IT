---
title: Gestire gli ambienti
seo-title: Gestire gli ambienti
description: Informazioni sull’ambiente Cloud Manager
seo-description: Segui questa pagina per visualizzare l’elenco degli ambienti di produzione e non di produzione utilizzati per configurare ed eseguire la pipeline CI/CD in Cloud Manager.
uuid: 04e67572-11db-4d5d-acf3-fd7f644a95f0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: c5b39de2-3a9b-437f-98e8-e6e6249a5b3a
feature: Ambienti
translation-type: tm+mt
source-git-commit: c5d32d49782c899d013fcc60b9c4d2b67e9350ae
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 4%

---


# Gestire gli ambienti {#manage-your-environments}

La pagina **Panoramica** di Cloud Manager include il riquadro **Ambienti** che elenca tutti gli ambienti AEM gestiti.

Ciascuno degli ambienti elencati visualizza il proprio stato associato.

![](assets/Manage-Environ-Overview.png)

## Tutorial video {#video-tutorial}

### Panoramica dell’ambiente di Cloud Manager {#environ-video}

Il video seguente fornisce una panoramica degli ambienti Cloud Manager composti da istanze di AEM Author, AEM Publish e Dispatcher.

>[!VIDEO](https://video.tv.adobe.com/v/26318/)

## Accesso agli ambienti in Cloud Manager {#accessing-environments-in-cloud-manager}

La sezione **Ambienti** visualizza gli ambienti di produzione e stage impostati nel programma insieme allo stato .

Lo stato è lo stato di alimentazione rollup nei nodi dell’ambiente. È verde se tutti i nodi sono in esecuzione, rosso se anche un nodo viene arrestato, blu se anche un nodo sta arrivando, e giallo se anche un nodo ha uno stato di alimentazione non disponibile (in questo ordine di priorità).

![](assets/Environments-card-new.png)

### Ambienti {#environments}

Fai clic su **Gestisci** per visualizzare la schermata **Ambienti** .

Nella schermata **Ambienti** viene visualizzata una scheda per ciascun ambiente *Produzione* e *Stage* (a seconda dei casi) del programma. Il nome dell&#39;ambiente viene visualizzato sopra ogni scheda. La scheda include una tabella di nodi nell’ambiente insieme alla dimensione della t-shirt della cpu, all’archiviazione, alla regione e allo stato.

>[!NOTE]
>
>Il **STATUS** del nodo rappresenta lo stato di alimentazione della VM e non riflette lo stato di AEM sul server. Lo stato può essere **Running** (cerchio verde), **Stopped** (cerchio rosso), **Proing Up** (cerchio blu) o **Unavailable** (cerchio giallo).

![](assets/Environments-tab.png)
