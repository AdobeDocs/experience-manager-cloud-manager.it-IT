---
title: Gestire gli ambienti
seo-title: Manage your Environments
description: Informazioni sull’ambiente Cloud Manager
seo-description: Follow this page to view the list of production and non-production environments that are used for setting up and running the CI/CD pipeline in Cloud Manager.
uuid: 04e67572-11db-4d5d-acf3-fd7f644a95f0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: c5b39de2-3a9b-437f-98e8-e6e6249a5b3a
feature: Environments
exl-id: 700b0b4c-1e1a-4993-b366-426b14a98f8e
source-git-commit: 6ff704ec11dd4a5f73d5b5df5721c4fee649527b
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 6%

---

# Gestire gli ambienti {#manage-your-environments}

>[!NOTE]
>Per informazioni sulla gestione degli ambienti per Cloud Manager in AEM as a Cloud Service, consulta [qui](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=it#using-cloud-manager).

La **Panoramica** la pagina di Cloud Manager include **Ambienti** riquadro che elenca tutti gli ambienti AEM gestiti.

Ciascuno degli ambienti elencati visualizza il proprio stato associato.

![](assets/Manage-Environ-Overview.png)

## Tutorial video {#video-tutorial}

### Panoramica dell’ambiente di Cloud Manager {#environ-video}

Il video seguente fornisce una panoramica degli ambienti Cloud Manager composti da istanze di AEM Author, AEM Publish e Dispatcher.

>[!VIDEO](https://video.tv.adobe.com/v/26318/)

## Accesso agli ambienti in Cloud Manager {#accessing-environments-in-cloud-manager}

La **Ambienti** visualizza gli ambienti di produzione e stage impostati nel programma insieme allo stato .

Lo stato è lo stato di alimentazione rollup nei nodi dell’ambiente. È verde se tutti i nodi sono in esecuzione, rosso se anche un nodo viene arrestato, blu se anche un nodo sta arrivando, e giallo se anche un nodo ha uno stato di alimentazione non disponibile (in questo ordine di priorità).

![](assets/Environments-card-new.png)

### Ambienti {#environments}

Fai clic su **Gestisci** per visualizzare **Ambienti** schermo.

La **Ambienti** visualizza una scheda per *Produzione* e *Stage* ambienti (come applicabile) nel programma. Il nome dell&#39;ambiente viene visualizzato sopra ogni scheda. La scheda include una tabella di nodi nell’ambiente insieme alla dimensione della t-shirt della cpu, all’archiviazione, alla regione e allo stato.

>[!NOTE]
>
>La **STATO** del nodo rappresenta lo stato di alimentazione della VM e non riflette lo stato di AEM sul server. Lo stato può essere **In esecuzione** (cerchio verde), **Arrestato** (cerchio rosso), **In arrivo** (cerchio blu) o **Non disponibile** (cerchio giallo).

![](assets/Environments-tab.png)

>[!NOTE]
>
>Se hai bisogno dei registri dell’ambiente, puoi richiederli tramite il tuo Customer Success Engineer.
