---
title: Note sulla versione 2019.9.0
seo-title: Note sulla versione di AEM Cloud Manager per la versione 2019.9.0
description: Segui questa pagina per ottenere informazioni sulla versione 2019.9.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2019.9.0 di AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: de9d2834ffa6c235e580227bd020fb8a0b94d22c

---

# Note sulla versione 2019.9.0 {#release-notes-for}

La release [!UICONTROL Cloud Manager] 2019.9.0 aggiorna i criteri di test di sicurezza, aggiunge grafici di monitoraggio scaricabili e risolve alcuni problemi di usabilità riportati dai clienti.

## Data di rilascio {#release-date}

La data di rilascio per la [!UICONTROL Cloud Manager] versione 2019.9.0 è il 12 settembre 2019.

## Novità {#whats-new}

* La categorizzazione del controllo dello stato del filtro Sling Referrer è stata modificata da Critico a Importante.
* La categorizzazione del controllo dello stato di configurazione di HTML Library Manager è stata modificata da Critico a Importante.
* È ora possibile scaricare i grafici di monitoraggio. Per ulteriori informazioni, consulta [Monitorare gli ambienti](monitor-your-environments.md) .
* Se un programma non dispone di un ambiente AEM di produzione, facendo clic sulla scheda del programma dalla pagina di destinazione si passa alla pagina di panoramica di Cloud Manager e non viene visualizzata alcuna finestra di dialogo di errore.
* La scheda Impostazioni **** tubazione nella pagina **Panoramica** è stata rinominata in Impostazioni **pipeline** produzione.
* I pulsanti di scelta Comportamento errore importante sono stati rimossi solo dalle pipeline di qualità codice.
* Nella pagina **Attività** viene ora visualizzato il nome della pipeline per ogni esecuzione.
* Nella pagina di esecuzione viene ora visualizzato il nome della pipeline.
* Nella finestra di dialogo Riepilogo qualità codice viene ora visualizzata una descrizione per ogni valutazione.

## Correzioni dei bug {#bug-fixes}

* Alcuni utenti non potevano visualizzare i dettagli di esecuzione in attesa di approvazione.
* Nella pagina **Panoramica** , il margine destro non era coerente.
* Il contenitore di compilazione potrebbe non disporre di memoria sufficiente nei progetti di grandi dimensioni.
* In alcune circostanze, la regola BanningPaths OakPAL non identificava il contenuto installato in /libs.
* Quando un cancello di qualità è stato rifiutato, l'intestazione della finestra di dialogo veniva visualizzata ancora *Parzialmente Superata*.

## Problemi noti {#known-issues}

* Il download dei grafici di monitoraggio non è disponibile in Safari.
