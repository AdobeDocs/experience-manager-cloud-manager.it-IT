---
title: Note sulla versione 2019.10.0
seo-title: Note sulla versione di AEM Cloud Manager 2019.10.0
description: Segui questa pagina per ottenere informazioni sulla versione 2019.10.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2019.10.0 di AEM Cloud Manager.
feature: Informazioni sulla versione
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 5%

---

# Note sulla versione 2019.10.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per [!UICONTROL Cloud Manager] la versione 2019.10.0 e aggiunge aggiornamenti ai passaggi di distribuzione e alla gestione delle versioni dei progetti Maven.
Per ulteriori informazioni, consulta le sezioni seguenti.

## Data di rilascio {#release-date}

La data di rilascio per la versione 2019.10.0 di [!UICONTROL Cloud Manager] è il 10 ottobre 2019.

## Novità {#whats-new}

* Sono state rese più performanti parti significative delle fasi di implementazione.
* Se appropriato, la versione del progetto Maven di build ora incorporerà la versione del progetto in git.
* Al momento della creazione, sono disponibili nuove variabili di ambiente.
* Le pipeline non di produzione possono essere eliminate dalla scheda nella pagina **Panoramica** e nell’API .
* È disponibile un nuovo passaggio di approvazione opzionale immediatamente dopo il passaggio di distribuzione dello stadio, ma prima del passaggio del test di sicurezza.
* Durante la configurazione di una pipeline CI/CD, è possibile saltare lo scollegamento e il collegamento delle istanze del dispatcher dal load balancer per gli ambienti di sviluppo e stage.
Per ulteriori informazioni, consulta **[Processo di distribuzione](deploying-code.md#deployment-process)** .
* Cloud Manager CLI è stato migliorato per supportare l’accesso ai registri delle fasi di esecuzione.
* L’API di Cloud Manager ora supporta la modifica del ramo configurato di una pipeline.
* Le richieste eseguite durante il test delle prestazioni ora includono un token specifico ***CloudManagerTest*** nell&#39;agente utente.

## Correzioni di bug {#bug-fixes}

* Alcune delle schede nella pagina **Panoramica** non erano allineate verticalmente correttamente.
* Alcune condizioni di errore non consentivano di contrassegnare correttamente le esecuzioni della pipeline e impedivano successive esecuzioni.
