---
title: Concetti fondamentali
seo-title: Concetti fondamentali
description: In questa pagina sono elencati i termini chiave associati a Cloud Manager.
seo-description: Segui questa pagina per comprendere i termini chiave associati a Cloud Manager.
uuid: 2a37810b-98f8-4f01-90de-1e52c754ad16
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: b702dfc0-3534-4d90-af19-8559d8baf6a6
translation-type: tm+mt
source-git-commit: ace032fbb26235d87d61552a11996ec2bb42abce
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 1%

---


# Concetti fondamentali {#key-concepts}

Questa pagina descrive alcuni termini di base utilizzati in Cloud Manager. È consigliabile leggere questa pagina prima di consultare la documentazione di Cloud Manager.

**Applicazione** L&#39;insieme di personalizzazioni e configurazioni create da un cliente per adattare la soluzione sottostante per i casi e le esigenze di utilizzo specifici. Un&#39;applicazione è un&#39;unità logica che può essere composta da più artefatti.

Ad esempio, *We.Retail*.

**Artifact** Un&#39;unità distribuibile. Il risultato di un processo di compilazione che trasforma il codice sorgente in una singola unità. Ad esempio, un file ZIP contenente il codice sorgente.

**Archivio** artefatti Una posizione di archiviazione in cui vengono salvati e protetti gli artefatti specifici del cliente.

**Ambiente** Un singolo cluster di macchine virtuali all&#39;interno di un programma. Ad AEM, è composto da un’istanza di creazione (facoltativamente con un’istanza di creazione in standby a freddo), da zero o più istanze di pubblicazione, da una o più istanze del dispatcher e da un sistema di bilanciamento del carico.

**Repository** Git Una posizione in cui viene memorizzato il codice sorgente specifico del cliente, accessibile utilizzando il protocollo Git.

**Istanza** Un server virtuale specifico che esegue la soluzione AEM. Le istanze rappresentano una singola unità logica dal punto di vista della distribuzione.

**Struttura del Adobe  organizzazione** che rappresenta un cliente Enterprise. Una società può avere più organizzazioni a seconda di come è stato originariamente effettuato il provisioning in  Adobe  Identity Management System.

**Pipeline** Un insieme di passaggi di distribuzione eseguiti in sequenza.

**Prodotto** Un insieme specifico di funzionalità all&#39;interno di una soluzione concessa in licenza da un&#39;organizzazione. Diversi programmi all&#39;interno di un&#39;organizzazione possono avere diritto a diversi gruppi di prodotti. Ad esempio, Siti, Risorse di Forms.

**Programma** Un insieme di ambienti che supportano un logico raggruppamento di iniziative dei clienti, solitamente corrispondenti a un contratto di servizio (SLA) acquistato. Ogni programma ha esattamente un ambiente di produzione e può avere molti ambienti non di produzione.

**Soluzione** Una delle [!UICONTROL Experience Cloud] soluzioni di Adobe . Ad esempio, Adobe Experience Manager,  Adobe Target o  Adobe Analytics.

**Passaggio** Un insieme di istruzioni configurato per l&#39;esecuzione di alcune unità di lavoro, blocco di generazione di una pipeline.
