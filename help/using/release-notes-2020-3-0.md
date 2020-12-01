---
title: Note sulla versione 2020.3.0
seo-title: AEM Cloud Manager - Note sulla versione 2020.3.0
description: Segui questa pagina per ottenere informazioni sulla release 2020.3.0 di Cloud Manager
seo-description: Segui questa pagina per ottenere informazioni su AEM Cloud Manager Release 2020.3.0
translation-type: tm+mt
source-git-commit: e7da473a22bec1d3d9b3d39bf654af0c596fe86d
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Note sulla versione 2020.3.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per la versione [!UICONTROL Cloud Manager] 2020.3.0.

## Data di rilascio {#release-date}

La data di rilascio per la versione [!UICONTROL Cloud Manager] 2020.3.0 è il 05 marzo 2020.

## Novità {#whats-new}

* Il registro della fase di compilazione è ora disponibile durante l’esecuzione della compilazione.
* Alcuni dei messaggi nella pagina dei dettagli di esecuzione della pipeline sono stati modificati per maggiore chiarezza.

## Correzioni di bug {#bug-fixes}

* Alcune configurazioni di distribuzione potrebbero causare la mancata disponibilità dei registri per i passaggi di distribuzione in caso di errore della distribuzione.
* Errori specifici all&#39;interno dei passaggi di distribuzione per i programmi Managed Services potrebbero causare il mancato avvio delle successive esecuzioni.
* A volte, l’istanza temporanea SonarQube utilizzata nel passaggio di compilazione non veniva avviata entro l’intervallo di timeout configurato.
* In progetti specifici, gli *oggetti ResourceResolver che dovrebbero venire sempre chiusi* generavano un’eccezione Null Pointer che tuttavia non aveva alcun impatto sull’esecuzione della pipeline.