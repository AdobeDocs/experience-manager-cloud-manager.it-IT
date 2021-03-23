---
title: Note sulla versione 2019.12.0
seo-title: Note sulla versione di AEM Cloud Manager 2019.12.0
description: Segui questa pagina per ottenere informazioni sulla versione 2019.12.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2019.12.0 di AEM Cloud Manager.
feature: Informazioni sulla versione
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 6%

---


# Note sulla versione 2019.12.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per [!UICONTROL Cloud Manager] la versione 2019.12.0 e aggiunge aggiornamenti all’esecuzione della pipeline e miglioramenti alla scansione della qualità del codice.
Per ulteriori informazioni, consulta le sezioni seguenti.

## Data di rilascio {#release-date}

La data di rilascio per la versione 2019.12.0 di [!UICONTROL Cloud Manager] è il 12 dicembre 2019.

## Novità {#whats-new}

* I passaggi nell’esecuzione della pipeline ora mostrano la marca temporale di completamento per ogni passaggio.
* La qualità del codice cerca progetti che non contengono codice Java ora segnalano un tasso di copertura del codice del 100%.
* Il controllo dello stato di configurazione del Dispatcher CQ è stato rimosso.

## Correzioni di bug {#bug-fixes}

* Le date non venivano visualizzate correttamente in alcuni browser.
* In rari casi, la pipeline di produzione passava alla fase di approvazione mentre il test delle prestazioni era ancora in esecuzione.
* In alcuni stati, i pulsanti nell’area superiore della pagina della panoramica non erano allineati correttamente.
* In alcune circostanze, gli utenti non autorizzati hanno visualizzato un pulsante per avviare la pipeline, anche se non era possibile fare clic sul pulsante stesso.
* I pulsanti di azione per le pipeline non di produzione talvolta venivano visualizzati nella posizione sbagliata.
* I pacchetti con il tipo di nodo granite:Ranking non sono stati in grado di essere analizzati per determinate violazioni delle regole di qualità.
* Alcuni errori nel processo di qualità del codice venivano erroneamente conteggiati come bug.
* Impossibile caricare i dati di monitoraggio per alcune topologie.
