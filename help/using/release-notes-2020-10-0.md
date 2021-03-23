---
title: Note sulla versione 2020.10.0
seo-title: Note sulla versione di AEM Cloud Manager 2020.10.0
description: Segui questa pagina per ottenere informazioni sulla versione 2020.10.0 di Cloud Manager
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2020.10.0 di AEM Cloud Manager
feature: Informazioni sulla versione
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 11%

---

# Note sulla versione 2020.10.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per [!UICONTROL Cloud Manager] la versione 2020.10.0.

## Data di rilascio {#release-date}

La data di rilascio per la versione 2020.10.0 è il 10 ottobre 2020.[!UICONTROL Cloud Manager]

## Correzioni di bug {#bug-fixes}

* Il crawler utilizzato per il test delle prestazioni considerava erroneamente alcuni tipi di risorse come collegamenti web validi.

* In alcune situazioni, la fase di completamento del test delle prestazioni non è stata gestita correttamente e ciò ha comportato passaggi di lunga durata.

* Quando è stata configurata l’invalidazione della cache del dispatcher per le distribuzioni di produzione, l’annullamento della validità veniva talvolta eseguito due volte.