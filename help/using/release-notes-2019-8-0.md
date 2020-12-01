---
title: Note sulla versione 2019.8.0
seo-title: Note sulla versione di AEM Cloud Manager per la versione 2019.8.0
description: Segui questa pagina per ottenere informazioni sulla versione 2019.8.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni su AEM Cloud Manager Release 2019.8.0.
translation-type: tm+mt
source-git-commit: 2ada697ca21acd0c73dbce2bce3e9481ac50272c
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Note sulla versione 2019.8.0 {#release-notes-for}

Il rilascio di [!UICONTROL Cloud Manager] 2019.8.0 aggiunge il supporto per i pacchetti di contenuto predefiniti selettivi, migliora le prestazioni di build e risolve una serie di bug minori.

## Data di rilascio {#release-date}

La data di rilascio per la versione [!UICONTROL Cloud Manager] 2019.8.0 è il 19 agosto 2019.

## Novità {#whats-new}

* Nuova interfaccia della riga di comando per l&#39;API di Cloud Manager, basata su [ CLI di Adobe I/O](https://github.com/adobe/aio-cli-plugin-cloudmanager).
* I pacchetti di contenuto specifici prodotti dalla build possono essere dichiarati come ignorati e non verranno distribuiti. Per ulteriori informazioni, consultate [Skipping Content Packages](/help/using/setting-up-project.md#skipping-content-packages) (Ignora pacchetti di contenuti).
* L&#39;insieme di dipendenze precaricate nel contenitore di build è stato rielaborato per evitare alcune richieste di rete superflue.
* È stato migliorato il messaggio nella pagina di panoramica per alcuni programmi configurati in modo non corretto.

## Correzioni di bug {#bug-fixes}

* Quando si accede ai rapporti SLA, l&#39;anno predefinito era 2018, non 2019.
* Per i nomi di ambiente lunghi, il selettore di ambiente nella schermata Rapporti non aumentava correttamente le dimensioni.
* La regola di qualità del codice ***ConfigAndInstallShouldOnlyContainOsgiNodes*** produceva falsi positivi quando veniva utilizzato il componente Sling Rewriter.
* La regola di qualità del codice ***ConfigAndInstallShouldOnlyContainOsgiNodes*** ha prodotto falsi positivi per alcune strutture di percorso non comuni.
* I clienti con solo risorse potrebbero non essere stati in grado in modo coerente di passare agli ambienti AEM.
* La finestra di dialogo Crea un ramo e un progetto veniva rappresentata in modo diverso tra i vari browser.
