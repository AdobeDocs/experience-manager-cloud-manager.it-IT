---
title: Note sulla versione 2020.8.0
seo-title: Note sulla versione di AEM Cloud Manager 2020.8.0
description: Segui questa pagina per ottenere informazioni sulla versione 2020.8.0 di Cloud Manager
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2020.8.0 di AEM Cloud Manager
feature: Informazioni sulla versione
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 7%

---

# Note sulla versione 2020.8.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per la versione [!UICONTROL Cloud Manager] 2020.8.0.

## Data di rilascio {#release-date}

La data di rilascio per la versione 2020.8.0 è il 6 agosto 2020.[!UICONTROL Cloud Manager]

## Novità {#whats-new}

Gli archivi Maven privati con associazione a autenticazione sono ora supportati.

## Correzioni di bug {#bug-fixes}

* Alcuni plug-in SonarQube superflui e indesiderati venivano eseguiti come parte della scansione Code Quality.

* Nella pagina di esecuzione della pipeline, il nome del ramo non era formattato correttamente.

* Durante la distribuzione nelle topologie con una sola pubblicazione, un singolo dispatcher e un autore in standby a freddo, il dispatcher è stato rimosso erroneamente dal load balancer.

* In alcuni casi, le esecuzioni completate della pipeline non sono state registrate correttamente come completate, impedendo così nuove esecuzioni della pipeline.

* Le esecuzioni delle pipeline verrebbero occasionalmente bloccate a causa di problemi di comunicazione interni.**

* La descrizione comandi sulle schede del programma non era corretta in modo coerente.

* C&#39;è stata una mancata corrispondenza dei colori nella pagina **Panoramica**.

* Il test delle prestazioni di Sites supporta ora l’utilizzo facoltativo dell’autenticazione.

* Le cache del Dispatcher per le istanze dell’autore vengono scaricate automaticamente quando le configurazioni del dispatcher vengono distribuite tramite Cloud Manager.

