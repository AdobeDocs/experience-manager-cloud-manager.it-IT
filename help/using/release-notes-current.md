---
title: Note sulla versione 2020.3.0
seo-title: Note sulla versione di AEM Cloud Manager per la versione 2020.3.0
description: Segui questa pagina per ottenere informazioni sulla release 2020.3.0 di Cloud Manager
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2020.3.0 di AEM Cloud Manager
translation-type: tm+mt
source-git-commit: 44671d89edad0ccb6ded998b62beb5fa012678e9

---

# Note sulla versione 2020.3.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per la [!UICONTROL Cloud Manager] release 2020.3.0.

## Release Date {#release-date}

La Data di rilascio per la [!UICONTROL Cloud Manager] versione 2020.3.0 è il 05 marzo 2020.

## Novità {#whats-new}

* Il registro per il passaggio di compilazione ora è disponibile mentre il passaggio di compilazione è in esecuzione.
* Alcuni dei messaggi nella pagina dei dettagli dell&#39;esecuzione della pipeline sono stati modificati per maggiore chiarezza.

## Correzioni dei bug {#bug-fixes}

* Alcune configurazioni di distribuzione potrebbero causare la mancata disponibilità dei registri per i passaggi di distribuzione in caso di errore della distribuzione.
* Errori specifici all&#39;interno dei passaggi di distribuzione per i programmi dei servizi gestiti potrebbero causare il mancato avvio delle successive esecuzioni.
* L&#39;istanza temporanea SonarQube utilizzata nel passaggio di compilazione non riusciva a avviarsi all&#39;interno del timeout configurato.
* In progetti specifici, gli oggetti *ResourceResolver dovrebbero essere sempre chiusi* genererebbe un&#39;eccezione di puntatore Null; tuttavia, ciò non ha influito sull&#39;esecuzione della pipeline.


