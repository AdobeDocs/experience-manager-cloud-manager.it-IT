---
title: Note sulla versione 2019.9.0
seo-title: Note sulla versione di AEM Cloud Manager per 2019.9.0
description: Segui questa pagina per ottenere informazioni sulla versione 2019.9.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2019.9.0 di AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 26014cfabfee6226033ba2fc1167d8f5509e17c6

---

# Note sulla versione 2019.9.0 {#release-notes-for}

La [!UICONTROL Cloud Manager] versione 2019.9.0 aggiorna i criteri di verifica della sicurezza, aggiunge grafici di monitoraggio scaricabili e risolve alcuni problemi di usabilità segnalati dal cliente.

## Data di rilascio {#release-date}

La Data di rilascio per [!UICONTROL Cloud Manager] la versione 2019.9.0 è il 12 settembre 2019.

## Novità {#whats-new}

* La categorizzazione della verifica dello stato dei filtri Sling Referrer è stata modificata da Importante a Importante.
* La categorizzazione della verifica dello stato di configurazione HTML Library Manager è stata modificata da Critico a Importante.
* Ora è possibile scaricare i grafici. Per ulteriori dettagli, consulta [Monitorare gli ambienti.](monitor-your-environments.md)
* Se un programma non dispone di un ambiente AEM di produzione, facendo clic sulla scheda del programma dalla pagina di destinazione passerai alla pagina Panoramica di Experience Manager, non a una finestra di dialogo di errore.
* La **scheda Impostazioni** pipeline nella pagina **Panoramica** è stata reintitolata alle impostazioni pipeline **produzione**.
* I pulsanti di scelta Errori importanti sono stati rimossi dai soli pipeline di qualità del codice.
* La **pagina Attività** ora visualizza il nome della pipeline per ogni esecuzione.
* La pagina di esecuzione ora mostra il nome della pipeline.
* La finestra di dialogo Riepilogo qualità codice ora mostra una descrizione per ogni valutazione.

## Correzioni di bug {#bug-fixes}

* Alcuni utenti non potevano visualizzare i dettagli di esecuzione quando erano in attesa di approvazione.
* Nella **pagina Panoramica** , il margine destro non era coerente.
* Il contenitore di generazione potrebbe esaurirsi in progetti di grandi dimensioni.
* In alcune circostanze, la regola oakpal di bannedpaths non identificava il contenuto installato in /libs.
* Quando un gate di qualità è stato rifiutato, l'intestazione di dialogo continuava a essere visualizzata *Parzialmente.*

## Problemi noti {#known-issues}

* Il download dei grafici di monitoraggio non è disponibile in Safari.
