---
title: Note sulla versione 2019.10.0
seo-title: Note sulla versione di AEM Cloud Manager per la versione 2019.10.0
description: Segui questa pagina per ottenere informazioni sulla versione 2019.10.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2019.10.0 di AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: de9d2834ffa6c235e580227bd020fb8a0b94d22c

---

# Note sulla versione 2019.10.0 {#release-notes-for}

La release [!UICONTROL Cloud Manager] 2019.10.0 aggiorna i criteri di test di sicurezza, aggiunge grafici di monitoraggio scaricabili e risolve alcuni problemi di usabilità riportati dai clienti.

## Data di rilascio {#release-date}

La data di rilascio per la [!UICONTROL Cloud Manager] versione 2019.10.0 è il 12 ottobre 2019.

## Novità {#whats-new}

* Sono state rese più efficaci parti significative delle fasi di implementazione.
* Se appropriato, la versione del progetto Maven build ora incorporerà la versione del progetto in git.
* Al momento della creazione, sono disponibili nuove variabili di ambiente.
* Le tubazioni non di produzione possono essere eliminate dalla scheda nella pagina Panoramica e dall'API.
* È disponibile un nuovo passaggio di approvazione opzionale immediatamente dopo il passaggio di distribuzione dell'area di visualizzazione, ma prima del passaggio del test di protezione.
* Durante la configurazione di una pipeline CI/CD, è possibile saltare lo scollegamento e il collegamento delle istanze del dispatcher dal sistema di bilanciamento del carico per gli ambienti di sviluppo e di passaggio.
* L'interfaccia CLI di Cloud Manager è stata incrementata per supportare l'accesso ai log delle fasi di esecuzione.
* L'API Cloud Manager ora supporta la modifica del ramo configurato di una pipeline.
* Le richieste eseguite durante il test delle prestazioni ora includono un token specifico ("CloudManagerTest") nell'agente utente.

## Correzioni dei bug {#bug-fixes}

* Alcune schede nella pagina Panoramica non erano allineate verticalmente correttamente.
* Alcune condizioni di errore non consentivano di contrassegnare correttamente le esecuzioni della pipeline e di impedire le esecuzioni successive.
