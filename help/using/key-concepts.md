---
title: Concetti fondamentali
seo-title: Concetti fondamentali
description: In questa pagina sono elencati i termini chiave associati a Cloud Manager.
seo-description: Leggi questa pagina per comprendere i termini chiave associati a Cloud Manager.
uuid: 2a37810b-98f8-4f01-90de-1e52c754ad16
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: b702dfc0-3534-4d90-af19-8559d8baf6a6
feature: Getting Started
level: Beginner
translation-type: tm+mt
source-git-commit: c5d32d49782c899d013fcc60b9c4d2b67e9350ae
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 2%

---


# Concetti fondamentali {#key-concepts}

Questa pagina descrive alcuni termini di base utilizzati in Cloud Manager. Si consiglia vivamente di leggere questa pagina prima di rivedere il resto della documentazione di Cloud Manager.

**** ApplicazioneL’insieme di personalizzazioni e configurazioni create da un cliente per adattare la soluzione sottostante per i casi d’uso specifici e le esigenze del cliente. Un&#39;applicazione è un&#39;unità logica che può essere composta da più artefatti.

Ad esempio, *We.Retail*.

**** ArtifactUn’unità distribuibile. Il risultato di un processo di compilazione che trasforma il codice sorgente in una singola unità. Ad esempio, un file ZIP contenente il codice sorgente.

**Artifact** RepositoryUna posizione di archiviazione in cui gli artefatti specifici del cliente vengono salvati e protetti.

**** AmbienteUn singolo cluster di macchine virtuali all&#39;interno di un programma. Per AEM, è composto da un’istanza dell’autore (facoltativamente con un’istanza dell’autore in standby a freddo aggiuntiva), da zero o più istanze di pubblicazione, da una o più istanze del dispatcher e da un load balancer.

**Percorso Git** RepositoryUna posizione in cui viene memorizzato il codice sorgente specifico del cliente, accessibile utilizzando il protocollo Git.

**** InstanceUn server virtuale specifico che esegue la soluzione AEM. Le istanze rappresentano una singola unità logica dal punto di vista della distribuzione.

**** Crea organizzazioneAdobe che rappresenta un cliente Enterprise. Una società può avere più organizzazioni a seconda di come sono state originariamente fornite nel sistema Identity Management di Adobe.

**** PipelineUn insieme di passaggi di distribuzione eseguiti in sequenza.

**** ProdottoUn set specifico di funzionalità all’interno di una soluzione concessa in licenza da un’organizzazione. I diversi programmi all&#39;interno di un&#39;organizzazione possono avere diritto a diversi tipi di prodotti. Ad esempio, Sites, Assets di Forms.

**** ProgrammaUn set di ambienti che supportano un raggruppamento logico di iniziative dei clienti, solitamente corrispondente a un contratto a livello di servizio (SLA) acquistato. Ogni programma ha esattamente un ambiente di produzione e può avere molti ambienti non di produzione.

**** SoluzioneUna delle  [!UICONTROL Experience Cloud] soluzioni Adobe. Ad esempio, Adobe Experience Manager, Adobe Target o Adobe Analytics.

**** Passaggio: set di istruzioni configurato per l’esecuzione di alcune unità di lavoro, blocco predefinito di una pipeline.
