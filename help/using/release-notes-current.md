---
title: Note sulla versione 2021.4.0
description: Segui questa pagina per ottenere informazioni sulla versione 2021.4.0 di Cloud Manager
feature: Informazioni sulla versione
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
translation-type: tm+mt
source-git-commit: 1f7f87a4b944d1fadc708958a96a1bda7d41da5d
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 7%

---

# Note sulla versione 2021.4.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per [!UICONTROL Cloud Manager] la versione 2021.4.0.

## Data di rilascio {#release-date}

La data di rilascio per la versione 2021.4.0 è il 8 aprile 2021.
[!UICONTROL Cloud Manager]
La prossima versione è prevista per il 6 maggio 2021.

## Novità {#whats-new}

* Il timeout della richiesta per gli utenti virtuali del test delle prestazioni è stato aumentato da 20 a 60 secondi.

* Il pulsante Manage Git (Gestisci Git) viene visualizzato sulla scheda Pipelines (Pipelines) anche se non è stata configurata alcuna pipeline.

* Durante la fase di distribuzione della pagina di esecuzione della pipeline, l’utente sarà in grado di visualizzare i passaggi di distribuzione completati e futuri, oltre al passaggio corrente nell’interfaccia utente per lo stato *In corso* .

* La versione dell’archetipo di progetto AEM utilizzato da Cloud Manager è stata aggiornata alla versione 27.

* È stato chiarito il messaggio di errore durante l’avvio di una pipeline quando un ambiente è stato eliminato.

* I bundle OSGi forniti dai progetti Eclipse ora sono esclusi dalla regola `CQBP-84--dependencies`.

## Correzioni di bug {#bug-fixes}

* Errori rari e transitori che possono verificarsi al passaggio *Assets Test* nella pipeline di produzione.

* Una barra finale nel test di caricamento della pipeline di produzione causava un errore 404.

* Il controllo `Runmode` produceva falsi positivi sui nodi non presenti nelle cartelle.