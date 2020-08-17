---
title: Note sulla versione 2020.8.0
seo-title: Note sulla versione di AEM Cloud Manager per la versione 2020.8.0
description: Segui questa pagina per ottenere informazioni sulla versione 2020.8.0 di Cloud Manager
seo-description: Segui questa pagina per ottenere informazioni su AEM Cloud Manager Release 2020.8.0
translation-type: tm+mt
source-git-commit: c2f5caf50f2e20c07807369aee7914c17fded4de
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 6%

---

# Note sulla versione 2020.8.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per la [!UICONTROL Cloud Manager] release 2020.8.0.

## Data di rilascio {#release-date}

La data di rilascio per la [!UICONTROL Cloud Manager] versione 2020.8.0 è il 6 agosto 2020.

## Novità {#whats-new}

Sono ora supportati i repository privati con binding di autenticazione.

## Correzioni di bug {#bug-fixes}

* Alcuni plug-in SonarQube non necessari e indesiderati venivano eseguiti come parte della scansione Code Quality.

* Nella pagina di esecuzione della pipeline, il nome del ramo non era formattato correttamente.

* Quando si distribuiva nelle topologie con un&#39;unica pubblicazione, un singolo dispatcher e un autore in standby a freddo, il dispatcher veniva erroneamente rimosso dal sistema di bilanciamento del carico.

* In alcuni casi, le esecuzioni completate della pipeline non sono state registrate come completate, impedendo così nuove esecuzioni della pipeline.

* Le esecuzioni delle tubazioni si *bloccavano* occasionalmente a causa di problemi di comunicazione interni.

* La descrizione comandi sulle schede del programma non era corretta in modo coerente.

* Nella pagina **Panoramica** si verificava una mancata corrispondenza dei colori.

* Il test delle prestazioni dei siti ora supporta l&#39;uso facoltativo dell&#39;autenticazione.

* Le cache del dispatcher per le istanze di creazione vengono scaricate automaticamente quando le configurazioni del dispatcher vengono distribuite tramite Cloud Manager.

