---
title: Note sulla versione 2019.9.0
seo-title: Note sulla versione di AEM Cloud Manager 2019.9.0
description: Segui questa pagina per ottenere informazioni sulla versione 2019.9.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2019.9.0 di AEM Cloud Manager.
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 5%

---

# Note sulla versione 2019.9.0 {#release-notes-for}

La versione [!UICONTROL Cloud Manager] 2019.9.0 aggiorna i criteri dei test di sicurezza, aggiunge grafici di monitoraggio scaricabili e risolve alcuni problemi di usabilità riportati dai clienti.

## Data di rilascio {#release-date}

La data di rilascio per la versione 2019.9.0 di [!UICONTROL Cloud Manager] è il 12 settembre 2019.

## Novità {#whats-new}

* La categorizzazione del controllo dello stato di salute del filtro di riferimento Sling è stata modificata da Critico a Importante.
* La categorizzazione del controllo dello stato di configurazione di Gestione librerie HTML è stata modificata da Critico a Importante.
* È ora possibile scaricare i grafici di monitoraggio. Per ulteriori informazioni, consulta [Monitorare gli ambienti](monitor-your-environments.md) .
* Se un programma non dispone di un ambiente di produzione AEM, facendo clic sulla scheda del programma dalla pagina di destinazione si passa alla pagina di panoramica di Cloud Manager e non viene visualizzata una finestra di dialogo di errore.
* La scheda **Impostazioni pipeline** nella pagina **Panoramica** è stata rinominata **Impostazioni pipeline di produzione**.
* I pulsanti di scelta Comportamento errore importante sono stati rimossi solo dalle pipeline di qualità codice.
* Nella pagina **Attività** viene ora visualizzato il nome della pipeline per ogni esecuzione.
* Nella pagina di esecuzione viene ora visualizzato il nome della pipeline.
* La finestra di dialogo Riepilogo qualità codice mostra ora una descrizione per ogni valutazione.

## Correzioni di bug {#bug-fixes}

* Alcuni utenti non potevano visualizzare i dettagli di un&#39;esecuzione in attesa di approvazione.
* Nella pagina **Panoramica**, il margine destro non era coerente.
* Il contenitore di build potrebbe esaurire la memoria nei progetti di grandi dimensioni.
* In alcune circostanze, la regola BannedPaths OakPAL non identificava il contenuto installato sotto /libs.
* Quando un gate di qualità è stato rifiutato, l&#39;intestazione della finestra di dialogo mostrava ancora *Superato parzialmente*.

## Problemi noti {#known-issues}

* Il download di grafici di monitoraggio non è disponibile in Safari.
