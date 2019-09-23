---
title: Concetti chiave
seo-title: Concetti chiave
description: In questa pagina sono elencati i termini chiave associati a Cloud Manager.
seo-description: Segui questa pagina per comprendere i termini chiave associati a Cloud Manager.
uuid: 2a37810b-98f8-4f01-90de-1e52c754ad16
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduzione
discoiquuid: b702dfc0-3534-4d90-af19-8559d8baf6a6
translation-type: tm+mt
source-git-commit: aa4ff4eb2f3292fe4cb0baf8087b4d0213443cf4

---


# Concetti chiave {#key-concepts}

Questa pagina descrive alcuni termini di base utilizzati in Cloud Manager. È consigliabile leggere questa pagina prima di consultare la documentazione di Cloud Manager.

**Applicazione** L'insieme di personalizzazioni e configurazioni create da un cliente (o dal suo cliente) per adattare la soluzione sottostante ai casi e alle esigenze di utilizzo specifici. Un'applicazione è un'unità logica che può essere composta da più artefatti.

Ad esempio, *We.Retail*.

**Artifact** Un'unità distribuibile. Il risultato di un processo di compilazione che trasforma il codice sorgente in una singola unità. Ad esempio, un file ZIP contenente il codice sorgente.

**Archivio** artefatti Una posizione di archiviazione in cui vengono salvati e protetti gli artefatti specifici del cliente.

**Ambiente** Un singolo cluster di macchine virtuali all'interno di un programma. Per AEM, si tratta di un’istanza di creazione (facoltativamente con un’istanza di creazione in standby), zero o più istanze di pubblicazione, una o più istanze del dispatcher e un sistema di bilanciamento del carico.

**Repository** Git Una posizione in cui viene memorizzato il codice sorgente specifico del cliente, accessibile utilizzando il protocollo Git.

**Istanza** Un server virtuale specifico che esegue la soluzione AEM. Le istanze rappresentano una singola unità logica dal punto di vista della distribuzione.

**Organizzazione** di Adobe che rappresenta un cliente Enterprise. Una società può avere più organizzazioni a seconda di come è stato originariamente effettuato il provisioning nel sistema di gestione dell'identità di Adobe.

**Pipeline** Un insieme di passaggi di distribuzione eseguiti in sequenza.

**Prodotto** Un insieme specifico di funzionalità all'interno di una soluzione concessa in licenza da un'organizzazione. All'interno di un'organizzazione possono essere concessi diversi programmi a diversi gruppi di prodotti. Ad esempio, Siti, Risorse di moduli.

**Programma** Un insieme di ambienti che supportano un logico raggruppamento di iniziative dei clienti, solitamente corrispondenti a un contratto di servizio (SLA) acquistato. Ogni programma ha esattamente un ambiente di produzione e può avere molti ambienti non di produzione.

**Soluzione** Una delle [!UICONTROL Experience Cloud] soluzioni Adobe. Ad esempio, Adobe Experience Manager, Adobe Target o Adobe Analytics.

**Passaggio** Un insieme di istruzioni configurato per l'esecuzione di alcune unità di lavoro, blocco di generazione di una pipeline.
