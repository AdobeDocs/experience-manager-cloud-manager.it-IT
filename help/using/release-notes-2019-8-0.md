---
title: Note sulla versione 2019.8.0
seo-title: Note sulla versione di AEM Cloud Manager 2019.8.0
description: Segui questa pagina per ottenere informazioni sulla versione 2019.8.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2019.8.0 di AEM Cloud Manager.
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 8%

---

# Note sulla versione 2019.8.0 {#release-notes-for}

Il rilascio di [!UICONTROL Cloud Manager] 2019.8.0 aggiunge il supporto per pacchetti di contenuti selettivi, migliora le prestazioni di build e corregge una serie di bug minori.

## Data di rilascio {#release-date}

La data di rilascio per la versione 2019.8.0 di [!UICONTROL Cloud Manager] è il 19 agosto 2019.

## Novità {#whats-new}

* Nuova interfaccia della riga di comando per l’API Cloud Manager, basata su [Adobe I/O CLI](https://github.com/adobe/aio-cli-plugin-cloudmanager).
* I pacchetti di contenuto specifici prodotti dalla build possono essere dichiarati come ignorati e non verranno distribuiti. Per ulteriori informazioni, consulta [Ignora pacchetti di contenuto](/help/using/setting-up-project.md#skipping-content-packages) .
* Il set di dipendenze precaricate nel contenitore di build è stato rielaborato per evitare alcune richieste di rete superflue.
* Il messaggio nella pagina della panoramica per alcuni programmi configurati in modo errato è stato migliorato.

## Correzioni di bug {#bug-fixes}

* Quando si accede ai rapporti SLA, l’anno predefinito è 2018, non 2019.
* Per i nomi di ambiente lunghi, la dimensione del selettore di ambiente nella schermata Rapporti non è stata aumentata correttamente.
* La regola di qualità del codice ***ConfigAndInstallShouldOnlyContainOsgiNodes*** produceva falsi positivi quando veniva utilizzato il componente Sling Rewriter.
* La regola di qualità del codice ***ConfigAndInstallShouldOnlyContainOsgiNodes*** ha prodotto falsi positivi per alcune strutture di percorso non comuni.
* I clienti per sola risorsa potrebbero non essere stati in grado di navigare costantemente nei loro ambienti AEM.
* La finestra di dialogo Crea un ramo e un progetto è stata riprodotta in modo diverso tra i diversi browser.
