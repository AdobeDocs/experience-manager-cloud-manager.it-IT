---
title: Note sulla versione 2020.3.0
seo-title: Note sulla versione di AEM Cloud Manager 2020.3.0
description: Segui questa pagina per ottenere informazioni sulla versione 2020.3.0 di Cloud Manager
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2020.3.0 di AEM Cloud Manager
feature: Informazioni sulla versione
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 51%

---

# Note sulla versione 2020.3.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per la versione [!UICONTROL Cloud Manager] 2020.3.0.

## Data di rilascio {#release-date}

La data di rilascio per la versione 2020.3.0 è il 5 marzo 2020.[!UICONTROL Cloud Manager]

## Novità {#whats-new}

* Il registro della fase di compilazione è ora disponibile durante l’esecuzione della compilazione.
* Alcuni dei messaggi nella pagina dei dettagli di esecuzione della pipeline sono stati modificati per maggiore chiarezza.

## Correzioni di bug {#bug-fixes}

* Alcune configurazioni di distribuzione potrebbero causare l’impossibilità dei registri per i passaggi di distribuzione se la distribuzione non è riuscita.
* Errori specifici nei passaggi di distribuzione per i programmi Managed Services potrebbero impedire l&#39;avvio delle esecuzioni successive.
* A volte, l’istanza temporanea SonarQube utilizzata nel passaggio di compilazione non veniva avviata entro l’intervallo di timeout configurato.
* In progetti specifici, gli *oggetti ResourceResolver che dovrebbero venire sempre chiusi* generavano un’eccezione Null Pointer che tuttavia non aveva alcun impatto sull’esecuzione della pipeline.