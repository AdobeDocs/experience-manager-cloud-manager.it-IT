---
title: Note sulla versione 2019.8.0
seo-title: Note sulla versione di AEM Cloud Manager per 2019.8.0
description: Segui questa pagina per ottenere informazioni sulla versione 2019.8.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2019.8.0 di AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 365cd6dfe65059c0c529f774bbcda946d47b0db5

---

# Note sulla versione 2019.8.0 {#release-notes-for}

La [!UICONTROL Cloud Manager] versione 2019.8.0 aggiunge il supporto per pacchetti di contenuti strutturati selettivi, migliora le prestazioni di creazione e risolve diversi bug minori.

## Data di rilascio {#release-date}

La Data di rilascio per [!UICONTROL Cloud Manager] la versione 2019.8.0 è il 19 agosto 2019.

## Novità {#whats-new}

* Nuova interfaccia riga di comando all'API di Cloud Manager, basata su [Adobe I/O CLI](https://github.com/adobe/aio-cli-plugin-cloudmanager).
* I pacchetti di contenuto specifici generati dalla build possono essere dichiarati come non consentiti e non verranno distribuiti. Per ulteriori informazioni, consulta ***la*** sezione Sui pacchetti di contenuto ignorati in [Creazione di un progetto](create-an-application-project.md) applicazione AEM.
* Il set di dipendenze precaricate nel contenitore di build è stato rielaborato per evitare alcune richieste di rete superflue.
* È stato migliorato il messaggio sulla pagina della panoramica di alcuni programmi configurati in modo errato.

## Correzioni di bug {#bug-fixes}

* Durante l'accesso ai report SLA, l'anno predefinito era 2018, non 2019.
* Per i nomi di ambiente lunghi, il selettore dell'ambiente nella schermata Rapporti non aumenta in modo corretto.
* La regola di qualità ***del*** codice configandinstallshoulwerodes generava falsi positivi quando veniva utilizzato il componente Sling Rewriter.
* La regola di qualità ***del*** codice configandinstallshoulwerodes generava falsi positivi per alcune strutture di percorso non comuni.
* I clienti solo delle risorse potrebbero non essere stati in grado di navigare nei propri ambienti AEM.
* [!UICONTROL Create a Branch and Project] La finestra di dialogo viene visualizzata in modo diverso su diversi browser.
