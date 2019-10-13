---
title: Note sulla versione 2019.10.0
seo-title: Note sulla versione di AEM Cloud Manager per la versione 2019.10.0
description: Segui questa pagina per ottenere informazioni sulla versione 2019.10.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2019.10.0 di AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 5a9d5fc71968741948c519681bcc25bb40d4da45

---

# Note sulla versione 2019.10.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per la [!UICONTROL Cloud Manager] release 2019.10.0 e aggiunge aggiornamenti ai passaggi di distribuzione e alla gestione della versione del progetto maven.
Seguite le sezioni riportate di seguito per ulteriori dettagli.

## Data di rilascio {#release-date}

La data di rilascio per la [!UICONTROL Cloud Manager] versione 2019.10.0 è il 10 ottobre 2019.

## Novità {#whats-new}

* Sono state rese più efficaci parti significative delle fasi di implementazione.
* Se appropriato, la versione del progetto Maven build ora incorporerà la versione del progetto in git.
* Al momento della creazione, sono disponibili nuove variabili di ambiente.
* Le tubazioni non di produzione possono essere eliminate dalla scheda nella pagina **Panoramica** e dall'API.
* È disponibile un nuovo passaggio di approvazione opzionale immediatamente dopo il passaggio di distribuzione dell'area di visualizzazione, ma prima del passaggio del test di protezione.
* Durante la configurazione di una pipeline CI/CD, è possibile saltare lo scollegamento e il collegamento delle istanze del dispatcher dal sistema di bilanciamento del carico per gli ambienti di sviluppo e di passaggio.
Per ulteriori informazioni, consulta **[Processo](deploying-code.md#deployment-process)** di distribuzione.
* L'interfaccia CLI di Cloud Manager è stata incrementata per supportare l'accesso ai log delle fasi di esecuzione.
* L'API Cloud Manager ora supporta la modifica del ramo configurato di una pipeline.
* Le richieste eseguite durante il test delle prestazioni ora includono un token specifico ***CloudManagerTest*** nell'agente utente.

## Correzioni dei bug {#bug-fixes}

* Alcune schede nella pagina **Panoramica** non erano allineate verticalmente correttamente.
* Alcune condizioni di errore non consentivano di contrassegnare correttamente le esecuzioni della pipeline e di impedire le successive esecuzioni.
