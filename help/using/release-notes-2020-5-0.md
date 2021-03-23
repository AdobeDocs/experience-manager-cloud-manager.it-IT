---
title: Note sulla versione 2020.5.0
seo-title: Note sulla versione di AEM Cloud Manager 2020.5.0
description: Segui questa pagina per ottenere informazioni sulla versione 2020.5.0 di Cloud Manager
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2020.5.0 di AEM Cloud Manager
feature: Informazioni sulla versione
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 67%

---

# Note sulla versione 2020.5.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per la versione [!UICONTROL Cloud Manager] 2020.5.0.

## Data di rilascio {#release-date}

La data di rilascio per la versione 2020.5.0 è il 7 maggio 2020.[!UICONTROL Cloud Manager]

## Novità {#whats-new}

* Sono state aggiunte altre sei regole per la qualità del codice, per aiutare i clienti a identificare potenziali problemi durante la pianificazione di una migrazione a Cloud Service.

* È stata aggiunta la nuova metrica *Compatibilità Cloud Service* che consente di ottenere un riepilogo del numero di problemi correlati alla compatibilità.

* Sono state migliorate le prestazioni della pagina Attività e dell’API dell’elenco di esecuzioni della pipeline.

* Il registro della qualità del codice contiene ora le tracce dello stack complete per le eccezioni.

## Correzioni di bug {#bug-fixes}

* Durante l’esecuzione della pipeline di produzione nella pagina della panoramica veniva visualizzata una scheda fuorviante.

* La regola per la qualità del codice *DontImplementOrExtendProviderTypesPomCheck* restituiva talvolta un’eccezione Null Pointer.

* Alcuni collegamenti della documentazione nella pagina della panoramica non funzionavano correttamente.

* Alcune schede nella pagina della panoramica non visualizzavano correttamente i nomi delle entità.

* Alcune configurazioni di topologia genererebbero un errore durante il passaggio del test delle prestazioni, anziché riportare le metriche mancanti.

