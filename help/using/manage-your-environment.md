---
title: Gestisci gli ambienti
seo-title: Gestisci gli ambienti
description: 'null'
seo-description: Seguite questa pagina per visualizzare l'elenco degli ambienti di produzione e non di produzione utilizzati per configurare ed eseguire la pipeline CI/CD in Cloud Manager.
uuid: 04 e 67572-11 db -4 d 5 d-acf 3-fd 7 f 644 a 95 f 0
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: utilizzo
discoiquuid: c 5 b 39 de 2-3 a 9 b -437 f -98 e 8-e 6 e 6249 a 5 b 3 a
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Gestisci gli ambienti {#manage-your-environments}

La **pagina Panoramica** di Cloud Manager include la sezione **Ambienti** in cui sono elencati tutti gli ambienti AEM gestiti.

Ciascuno degli ambienti elencati visualizza lo stato associato.

![](assets/Manage_Environments1.png)

## Accesso agli ambienti in Cloud Manager {#accessing-environments-in-cloud-manager}

Nella **sezione Ambienti** sono visualizzati gli ambienti Produzione e Area di visualizzazione forniti nel programma insieme allo stato.

Lo stato è lo stato di potenza cumulativo tra i nodi dell&#39;ambiente. È verde se tutti i nodi sono in esecuzione, rossi se anche un nodo viene interrotto, blu se anche un nodo sta per comparire, e giallo se anche un nodo ha uno stato di potenza non disponibile (in questo ordine di priorità).

![](assets/manage_environments-screen2.png)

### Ambienti {#environments}

Fate clic su **Gestisci** per visualizzare la **schermata Ambienti** .

Nella **schermata Ambienti** viene visualizzata una scheda per gli ambienti *Produzione* e *Area di visualizzazione* (se applicabile) nel programma. Il nome dell&#39;ambiente viene visualizzato sopra ogni scheda. La scheda include un sommario nell&#39;ambiente insieme alle dimensioni t-shirt della cpu, all&#39;archiviazione, alla regione e allo stato.

>[!NOTE]
>
>**Lo stato** del nodo rappresenta lo stato power della VM e non riflette lo stato di AEM sul server. Lo stato può essere **Esecuzione** (cerchio verde), **Interrotto** (cerchio rosso), **Entra** (cerchio blu) o **Non disponibile** (cerchio giallo).

![](assets/Manage_Environments2.png)
