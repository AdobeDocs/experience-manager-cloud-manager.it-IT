---
title: Note sulla versione 2020.7.0
seo-title: Note sulla versione di AEM Cloud Manager per la versione 2020.7.0
description: Segui questa pagina per ottenere informazioni sulla versione 2020.7.0 di Cloud Manager
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2020.7.0 di AEM Cloud Manager
translation-type: tm+mt
source-git-commit: 0d46abc386460ccbaf7ba10b93286bc8e4af2395
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 6%

---

# Note sulla versione 2020.7.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per la [!UICONTROL Cloud Manager] release 2020.7.0.

## Data di rilascio {#release-date}

La data di rilascio per la [!UICONTROL Cloud Manager] versione 2020.7.0 è il 09 luglio 2020.

## Novità {#whats-new}

* Lo scollegamento e il collegamento delle istanze dello dispatcher dai bilanciatori del carico durante le distribuzioni di produzione ora funzionano in modo più coerente.

* Il contenitore di build di Cloud Manager ora supporta sia Java 8 che Java 11.

* Le pipeline di Cloud Manager ora supportano le variabili e i segreti del set di clienti.
Per ulteriori informazioni, vedere Variabili [](/help/using/create-an-application-project.md#pipeline-variables) tubazione.

## Correzioni di bug {#bug-fixes}

* Le opzioni **Annulla** e **Salva** nella pagina Modifica pipeline non produzione non erano sempre visibili.

* Alcuni errori nel processo di qualità del codice potrebbero causare la mancata generazione corretta del file di registro.

* Non è stato possibile scaricare in modo coerente alcuni log delle fasi della pipeline di grandi dimensioni tramite l&#39;interfaccia utente.

## Problemi noti {#known-issues}

* Quando un ambiente AMS contiene un&#39;istanza in standby, il messaggio registrato indica che l&#39;istanza è disattivata anziché in modalità standby.

* A causa di una modifica nella modalità di calcolo della copertura del codice, la versione _minima_ del plugin Jacoco è ora 0.7.5.201505241946 (rilasciata a maggio 2015). I clienti che fanno esplicito riferimento a una versione precedente riceveranno un messaggio di errore nel processo di qualità del codice.
