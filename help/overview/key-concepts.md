---
title: Concetti fondamentali
description: Come tutti gli strumenti potenti, Cloud Manager include molti concetti e termini. Questo documento riepiloga alcuni dei più importanti per iniziare a utilizzare Cloud Manager.
exl-id: 86dfc976-f3da-479a-9faa-08f40ca909e0
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 49%

---


# Concetti chiave {#key-concepts}

Come tutti gli strumenti potenti, Cloud Manager include molti concetti e termini. Questo documento riepiloga alcuni dei più importanti per iniziare a utilizzare Cloud Manager.

## Applicazione {#application}

Un&#39;applicazione è il set di personalizzazioni e configurazioni create da un cliente per adattare la [soluzione](#solution) sottostante (ad esempio AEM Sites o AEM Assets) ai casi d&#39;uso e alle esigenze specifiche. Un&#39;applicazione è un&#39;unità logica che può essere composta da più [artefatti](#artifact).

Un&#39;applicazione di esempio è l&#39;applicazione [WKND lifestyle fittizia](https://experienceleague.adobe.com/it/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview).

## Artefatto {#artifact}

Un artefatto è un’unità distribuibile ed è il risultato di un processo di compilazione che trasforma il codice sorgente in una singola unità. Ad esempio, un file .zip contenente il codice sorgente.

## Archivio artefatti {#artifact-repository}

Un archivio di artefatti è un percorso di archiviazione in cui gli [artefatti](#artifact) specifici del cliente vengono salvati e protetti.

## Ambiente {#environment}

Un ambiente è un singolo cluster di macchine virtuali in un [programma](#program). Per l’AEM, questo ambiente è composto da un’istanza di authoring (facoltativamente con un’ulteriore istanza di authoring in standby a freddo), da zero o più istanze di pubblicazione, da una o più istanze di Dispatcher e da un load balancer.

## Archivio Git {#git-repository}

Un archivio Git è un percorso in cui viene archiviato il codice sorgente specifico del cliente ed è accessibile [tramite Git](https://git-scm.com).

## Istanza {#instance}

Un&#39;istanza è un server virtuale specifico che esegue la [soluzione](#solution) AEM. Le istanze rappresentano una singola unità logica dal punto di vista della distribuzione.

## Organizzazione {#organization}

Un’organizzazione è un costrutto di Adobe che rappresenta un cliente aziendale. Un’azienda può avere più organizzazioni a seconda di come sono state fornite in Adobe Identity Management (IMS).

## Pipeline  {#pipeline}

Una pipeline è un set di passaggi di distribuzione eseguiti o &quot;eseguiti&quot; in sequenza.

## Prodotto {#product}

Un prodotto è un set specifico di funzionalità all’interno di una [soluzione](#solution) concessa in licenza da un&#39;organizzazione. Diversi [programmi](#program) all’interno di un’organizzazione possono essere autorizzati all’utilizzo di diversi set di prodotti, ad esempio AEM Sites, AEM Assets o AEM Forms.

## Programma {#program}

Un programma è un set di ambienti che supporta un raggruppamento logico di iniziative dei clienti, di solito corrispondente agli accordi sul livello del servizio acquistato (SLA). Ogni programma dispone esattamente un ambiente di produzione e può avere molti ambienti non di produzione.

## Soluzione {#solution}

Una soluzione è una delle soluzioni di Adobe [!UICONTROL Experience Cloud]. Ad esempio, Adobe Experience Manager, Adobe Target o Adobe Analytics.

## Passaggio {#step}

Un passaggio è un set di istruzioni configurato che esegue alcune unità di lavoro come blocco predefinito di una [pipeline](#pipeline).
