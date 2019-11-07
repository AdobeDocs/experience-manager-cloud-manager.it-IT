---
title: Gestire gli ambienti
seo-title: Gestire gli ambienti
description: 'null'
seo-description: Seguite questa pagina per visualizzare l'elenco degli ambienti di produzione e non produzione utilizzati per configurare ed eseguire la pipeline CI/CD in Cloud Manager.
uuid: 04e67572-11db-4d5d-acf3-fd7f644a95f0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: utilizzo
discoiquuid: c5b39de2-3a9b-437f-98e8-e6e6249a5b3a
translation-type: tm+mt
source-git-commit: c81243708d938a8bffdec8a35f32a2cf552c1c95

---


# Gestire gli ambienti {#manage-your-environments}

La pagina **Panoramica** di Cloud Manager include il riquadro **Ambienti** in cui sono elencati tutti gli ambienti AEM gestiti.

Ciascuno degli ambienti elencati visualizza il relativo stato associato.

![](assets/Manage-Environ-Overview.png)

## Esercitazione video {#video-tutorial}

### Panoramica ambiente di Cloud Manager {#environ-video}

Il video seguente fornisce una panoramica sugli ambienti di Cloud Manager composti da istanze di AEM Author, AEM Publish e Dispatcher.

>[!VIDEO](https://video.tv.adobe.com/v/26318/?captions=ita)

## Accesso agli ambienti in Cloud Manager {#accessing-environments-in-cloud-manager}

Nella sezione **Ambienti** sono visualizzati gli ambienti Produzione e Fase predisposti nel programma insieme allo stato.

Lo stato è lo stato di alimentazione rollup tra i nodi nell'ambiente. È verde se tutti i nodi sono in esecuzione, rosso se anche un nodo viene arrestato, blu se anche un nodo è in arrivo, giallo se anche un nodo ha uno stato di alimentazione non disponibile (in questo ordine di priorità).

![](assets/Environments-card-new.png)

### Ambienti {#environments}

Fate clic su **Gestisci** per visualizzare la schermata **Ambienti** .

Nella schermata **Ambienti** viene visualizzata una scheda per ogni *ambiente di produzione* e *fase* (in base alle esigenze) del programma. Il nome dell'ambiente è visualizzato sopra ogni scheda. La scheda include una tabella di nodi nell'ambiente insieme alla dimensione della t-shirt della cpu, dello storage, della regione e dello stato.

>[!NOTE]
>
>Lo **STATO** del nodo rappresenta lo stato di alimentazione della VM e non riflette lo stato di AEM sul server. Lo stato può essere **Corrente** (cerchio verde), **Interrotto** (cerchio rosso), **In alto** (cerchio blu) o **Non disponibile** (cerchio giallo).

![](assets/Environments-tab.png)
