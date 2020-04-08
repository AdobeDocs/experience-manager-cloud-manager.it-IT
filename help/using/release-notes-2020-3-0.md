---
title: Note sulla versione 2020.3.0
seo-title: Note sulla versione di AEM Cloud Manager per la versione 2020.3.0
description: Segui questa pagina per ottenere informazioni sulla release 2020.3.0 di Cloud Manager
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2020.3.0 di AEM Cloud Manager
translation-type: tm+mt
source-git-commit: e7da473a22bec1d3d9b3d39bf654af0c596fe86d

---

# Note sulla versione 2020.3.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per la [!UICONTROL Cloud Manager] release 2020.3.0.

## Release Date {#release-date}

La Data di rilascio per la [!UICONTROL Cloud Manager] versione 2020.3.0 è il 05 marzo 2020.

## Novità {#whats-new}

* Il registro della fase di compilazione è ora disponibile durante l’esecuzione della compilazione.
* Alcuni dei messaggi nella pagina dei dettagli di esecuzione della pipeline sono stati modificati per maggiore chiarezza.

## Correzioni di bug {#bug-fixes}

* Alcune configurazioni di distribuzione potrebbero causare la mancata disponibilità dei registri per i passaggi di distribuzione in caso di errore della distribuzione.
* Errori specifici all&#39;interno dei passaggi di distribuzione per i programmi dei servizi gestiti potrebbero causare il mancato avvio delle successive esecuzioni.
* A volte, l’istanza temporanea SonarQube utilizzata nel passaggio di compilazione non veniva avviata entro l’intervallo di timeout configurato.
* In progetti specifici, gli *oggetti ResourceResolver che dovrebbero venire sempre chiusi* generavano un’eccezione Null Pointer che tuttavia non aveva alcun impatto sull’esecuzione della pipeline.