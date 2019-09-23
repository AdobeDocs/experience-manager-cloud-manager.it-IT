---
title: Note sulla versione 2019.4.0
seo-title: Note sulla versione di AEM Cloud Manager per la versione 2019.4.0
description: Segui questa pagina per ottenere informazioni sulla versione 2019.4.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2019.4.0 di AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: b368c46c2a9f40d0c3867db6eb2a333bd71fe22a

---


# Note sulla versione 2019.4.0 {#release-notes-for}

La versione [!UICONTROL Cloud Manager] 2019.4.0 non contiene modifiche funzionali significative. Seguite le sezioni riportate di seguito per ulteriori dettagli.

## Data di rilascio {#release-date}

La data di rilascio per la [!UICONTROL Cloud Manager] versione 2019.4.0 è il 18 aprile 2019.

## Novità {#whats-new}

* L'interfaccia utente di Cloud Manager è ora disponibile in inglese, francese, tedesco e giapponese.
* I passaggi di distribuzione ora contengono il processo in esecuzione, ovvero, quando è in esecuzione un backup, i pacchetti vengono installati e i bilanciatori di carico vengono riconfigurati

## Correzioni dei bug {#bug-fixes}

* L’approccio di distribuzione utilizzato per le modifiche del dispatcher è stato migliorato per gestire ulteriori casi di utilizzo.
* Alcuni tipi di dimensioni dell'istanza non venivano visualizzati correttamente nella pagina Ambienti.
* Le regole di qualità del codice relative alle dipendenze CQBP-84 generavano falsi positivi per le librerie Adobe incorporate, come i componenti core di WCM e i commons di condivisione delle risorse.
* Il pulsante dei dettagli per la fase di scansione del codice era attivato quando i dettagli non erano disponibili.
* Il messaggio di errore che veniva visualizzato quando si specificava un valore non valido per l'indicatore KPI delle visualizzazioni pagina per minuto conteneva un limite inferiore errato.
* La categoria di distribuzione in una pipeline non di produzione è stata capitalizzata in modo errato.
* La chiamata alla scheda delle azioni nella pagina **Panoramica** conteneva testo non corretto quando il repository git non era configurato correttamente.

## Problemi noti {#known-issues}

* I valori SLA potrebbero essere arrotondati in modo errato.
