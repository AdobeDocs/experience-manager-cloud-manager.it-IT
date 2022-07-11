---
title: Concetti fondamentali
description: Come tutti gli strumenti potenti, Cloud Manager include molti concetti e termini. Questo documento riepiloga alcuni dei più importanti per te durante l’utilizzo di Cloud Manager.
exl-id: 86dfc976-f3da-479a-9faa-08f40ca909e0
source-git-commit: 73e322cf93dc7709b7581860974079c8d94034ba
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 4%

---


# Concetti fondamentali {#key-concepts}

Come tutti gli strumenti potenti, Cloud Manager include molti concetti e termini. Questo documento riepiloga alcuni dei più importanti per te durante l’utilizzo di Cloud Manager.

## Applicazione {#application}

E applicazione è l&#39;insieme di personalizzazioni e configurazioni create da un cliente per adattare il sottostante [soluzione](#solution) (ad esempio AEM Sites o AEM Assets) per i casi d’uso e le esigenze specifiche degli utenti. Un&#39;applicazione è un&#39;unità logica che può essere composta da più [artefatti.](#artifact)

Un&#39;applicazione di esempio è fittizia [Applicazione WKND lifestyle.](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=it)

## Artefatto {#artifact}

Un artefatto è un’unità distribuibile ed è il risultato di un processo di compilazione che trasforma il codice sorgente in una singola unità. Ad esempio, un file .zip contenente il codice sorgente.

## Archivio Artifact {#artifact-repository}

Un archivio di artefatti è un percorso di archiviazione in cui specifico del cliente [artefatti](#artifact) vengono salvati e protetti.

## di authoring {#environment}

Un ambiente è un singolo cluster di macchine virtuali all&#39;interno di un [programma.](#program) Per AEM, è composto da un’istanza di authoring (facoltativamente con un’ulteriore istanza di authoring in standby a freddo), da zero o più istanze di pubblicazione, da una o più istanze del dispatcher e da un load balancer.

## archivio Git {#git-repository}

Un archivio Git è un percorso in cui il codice sorgente specifico del cliente viene memorizzato ed è accessibile [utilizzo di git.](https://git-scm.com)

## Istanza {#instance}

Un&#39;istanza è un server virtuale specifico che esegue il AEM [soluzione.](#solution) Le istanze rappresentano una singola unità logica dal punto di vista della distribuzione.

## Organizzazione {#organization}

Un&#39;organizzazione è un costrutto di Adobe che rappresenta un cliente aziendale. Una società può avere più organizzazioni a seconda di come sono state fornite in Adobe Identity Management System (IMS).

## Pipeline {#pipeline}

Una pipeline è un insieme di passaggi di distribuzione eseguiti in sequenza.

## Prodotto {#product}

Un prodotto è un set specifico di funzionalità all’interno di un [soluzione](#solution) concesso in licenza da un&#39;organizzazione. Diverso [programmi](#program) all’interno di un’organizzazione può essere consentito l’utilizzo di diversi set di prodotti, ad esempio AEM Sites, AEM Assets o AEM Forms.

## Programma {#program}

Un programma è un insieme di ambienti che supportano un raggruppamento logico di iniziative dei clienti, di solito corrispondente a un contratto a livello di servizio acquistato (SLA, Service Level Agreement). Ogni programma ha esattamente un ambiente di produzione e può avere molti ambienti non di produzione.

## Soluzione {#solution}

Una soluzione è uno degli Adobi [!UICONTROL Experience Cloud] soluzioni. Ad esempio, Adobe Experience Manager, Adobe Target o Adobe Analytics.

## Incremento {#step}

Un passaggio è un set di istruzioni configurato che esegue alcune unità di lavoro come blocco predefinito di un [pipeline.](#pipeline)
