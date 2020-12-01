---
title: Note sulla versione 2020.8.0
seo-title: Note sulla versione di AEM Cloud Manager per la versione 2020.8.0
description: Segui questa pagina per ottenere informazioni sulla versione 2020.8.0 di Cloud Manager
seo-description: Segui questa pagina per ottenere informazioni su AEM Cloud Manager Release 2020.8.0
translation-type: tm+mt
source-git-commit: c1d07c95088a279376ef495001a5165c7e459642
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Note sulla versione 2020.8.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per la versione [!UICONTROL Cloud Manager] 2020.8.0.

## Data di rilascio {#release-date}

La data di rilascio per la versione [!UICONTROL Cloud Manager] 2020.8.0 è il 6 agosto 2020.

## Novità {#whats-new}

Sono ora supportati i repository privati con binding di autenticazione.

## Correzioni di bug {#bug-fixes}

* Alcuni plug-in SonarQube non necessari e indesiderati venivano eseguiti come parte della scansione Code Quality.

* Nella pagina di esecuzione della pipeline, il nome del ramo non era formattato correttamente.

* Quando si distribuiva nelle topologie con un&#39;unica pubblicazione, un singolo dispatcher e un autore in standby a freddo, il dispatcher veniva erroneamente rimosso dal sistema di bilanciamento del carico.

* In alcuni casi, le esecuzioni completate della pipeline non sono state registrate come completate, impedendo così nuove esecuzioni della pipeline.

* A volte le esecuzioni della tubazione vengono bloccate a causa di problemi di comunicazione interni.**

* La descrizione comandi sulle schede del programma non era corretta in modo coerente.

* C&#39;è stata una mancata corrispondenza di colore nella pagina **Panoramica**.

* Il test delle prestazioni dei siti ora supporta l&#39;uso facoltativo dell&#39;autenticazione.

* Le cache del dispatcher per le istanze di creazione vengono scaricate automaticamente quando le configurazioni del dispatcher vengono distribuite tramite Cloud Manager.

