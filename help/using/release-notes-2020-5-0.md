---
title: Note sulla versione 2020.5.0
seo-title: Note sulla versione di AEM Cloud Manager per la versione 2020.5.0
description: Segui questa pagina per ottenere informazioni sulla versione 2020.5.0 di Cloud Manager
seo-description: Segui questa pagina per ottenere informazioni su AEM Cloud Manager Release 2020.5.0
translation-type: tm+mt
source-git-commit: 0652436ec0c1c95d270a06a600424dbfd0140b27
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Note sulla versione 2020.5.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per la versione [!UICONTROL Cloud Manager] 2020.5.0.

## Data di rilascio {#release-date}

La data di rilascio per la versione [!UICONTROL Cloud Manager] 2020.5.0 è il 07 maggio 2020.

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

* Alcune configurazioni di topologia genererebbero un errore nel passaggio del test delle prestazioni, anziché riportare le metriche mancanti.

