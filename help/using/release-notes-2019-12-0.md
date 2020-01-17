---
title: Note sulla versione 2019.12.0
seo-title: Note sulla versione di AEM Cloud Manager per la versione 2019.12.0
description: Segui questa pagina per ottenere informazioni sulla versione 2019.12.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2019.12.0 di AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 0fa1fedccb013e82c8df5838a612ce26a1efb7e8

---


# Note sulla versione 2019.12.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per la [!UICONTROL Cloud Manager] release 2019.12.0 e aggiunge aggiornamenti all&#39;esecuzione della pipeline e miglioramenti alle analisi di qualità del codice.
Seguite le sezioni riportate di seguito per ulteriori dettagli.

## Release Date {#release-date}

La data di rilascio per la [!UICONTROL Cloud Manager] versione 2019.12.0 è il 12 dicembre 2019.

## Novità {#whats-new}

* I passaggi nell&#39;esecuzione della pipeline ora mostrano la marca temporale di completamento per ogni passaggio.
* La scansione della qualità del codice per i progetti che non contengono codice Java ora segnala un tasso di copertura del codice pari al 100%.
* Il controllo dello stato di configurazione del dispatcher CQ è stato rimosso.

## Correzioni dei bug {#bug-fixes}

* Le date non venivano visualizzate correttamente in alcuni browser.
* In rari casi, la pipeline di produzione passava alla fase di approvazione mentre era ancora in esecuzione la verifica delle prestazioni.
* In alcuni stati, i pulsanti nella parte superiore della pagina della panoramica non erano allineati correttamente.
* In alcune circostanze, gli utenti non autorizzati hanno visto un pulsante per avviare la pipeline, anche se il pulsante stesso non era selezionabile.
* I pulsanti di azione per le condotte non di produzione talvolta venivano visualizzati nella posizione sbagliata.
* I pacchetti con il tipo di nodo granito:Classificazione non sono stati in grado di essere analizzati per determinate violazioni delle regole di qualità.
* Alcuni errori nel processo di qualità del codice venivano erroneamente considerati come bug.
* Impossibile caricare i dati di monitoraggio per alcune topologie.
