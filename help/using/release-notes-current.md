---
title: Note sulla versione 2020.8.0
seo-title: Note sulla versione di AEM Cloud Manager per la versione 2020.8.0
description: Segui questa pagina per ottenere informazioni sulla versione 2020.8.0 di Cloud Manager
seo-description: Segui questa pagina per ottenere informazioni su AEM Cloud Manager Release 2020.8.0
translation-type: tm+mt
source-git-commit: 68330a3a6d9e1f95782418dbd72cbc0e6ee7362c
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 20%

---

# Note sulla versione 2020.8.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per la [!UICONTROL Cloud Manager] release 2020.8.0.

## Data di rilascio {#release-date}

La data di rilascio per la [!UICONTROL Cloud Manager] versione 2020.8.0 è il 6 agosto 2020.

## Novità {#whats-new}

* Il test delle prestazioni dei siti ora supporta l&#39;uso facoltativo dell&#39;autenticazione.

   Per informazioni su come autenticare  test delle prestazioni di AEM Sites, fare riferimento a Test [delle prestazioni dei siti](configuring-pipeline.md#authenticated-sites-performance) autenticati.

* Sono ora supportati i repository privati con binding di autenticazione.

## Correzioni di bug {#bug-fixes}

* Alcuni plug-in SonarQube non necessari e indesiderati venivano eseguiti come parte della scansione Code Quality.

* Nella pagina di esecuzione della pipeline, il nome del ramo non era formattato correttamente.

* Quando si distribuiva nelle topologie con un&#39;unica pubblicazione, un singolo dispatcher e un autore in standby a freddo, il dispatcher veniva erroneamente rimosso dal sistema di bilanciamento del carico.

* In alcuni casi, le esecuzioni completate della pipeline non sono state registrate come completate, impedendo così nuove esecuzioni della pipeline.

* Le esecuzioni delle tubazioni si *bloccavano* occasionalmente a causa di problemi di comunicazione interni.

* La descrizione comandi sulle schede del programma non era corretta in modo coerente.

* C&#39;è stata una mancata corrispondenza di colore nella pagina della panoramica.

## Problemi noti {#known-issues}

* Quando un ambiente AMS contiene un&#39;istanza in standby, il messaggio registrato indica che l&#39;istanza è disattivata anziché in modalità standby.

* A causa di una modifica nel modo in cui viene calcolata la copertura del codice, la versione _minima_ del plugin Jacoco è ora 0.7.5.201505241946 (rilasciata a maggio 2015). I clienti che fanno esplicito riferimento a una versione precedente riceveranno un messaggio di errore nel processo di qualità del codice.
