---
title: Note sulla versione 2020.7.0
seo-title: AEM Cloud Manager - Note sulla versione 2020.7.0
description: Segui questa pagina per ottenere informazioni sulla versione 2020.7.0 di Cloud Manager
seo-description: Segui questa pagina per ottenere informazioni su AEM Cloud Manager Release 2020.7.0
translation-type: tm+mt
source-git-commit: c35398110e9d8311bf58f217efdd082cf0cfd90a
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 51%

---

# Note sulla versione 2020.7.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per la [!UICONTROL Cloud Manager] release 2020.7.0.

## Data di rilascio {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2020.7.0 is July 09, 2020.

## Novità {#whats-new}

* Lo scollegamento e il collegamento delle istanze dello dispatcher dai bilanciatori del carico durante le distribuzioni di produzione ora funzionano in modo più coerente.

* Il contenitore di build di Cloud Manager ora supporta sia Java 8 che Java 11.

* Le pipeline di Cloud Manager ora supportano variabili e segreti impostati dal cliente.
Per ulteriori informazioni, consulta [Variabili delle pipeline](/help/using/build-environment-details.md#pipeline-variables).

## Correzioni di bug {#bug-fixes}

* The **Cancel** and **Save** options on the Non-Production Pipeline Edit page were not always visible.

* Alcuni errori nel processo di qualità del codice potevano causare la generazione non corretta del file di registro.

* Tramite l’interfaccia utente non si potevano scaricare in modo coerente i log di alcuni fasi di pipeline di grandi dimensioni.

## Problemi noti {#known-issues}

* Quando un ambiente AMS contiene un&#39;istanza in standby, il messaggio registrato indica che l&#39;istanza è disattivata anziché in modalità standby.

* A causa di una modifica nel modo in cui viene calcolata la copertura del codice, la versione _minima_ del plugin Jacoco è ora 0.7.5.201505241946 (rilasciata a maggio 2015). I clienti che fanno esplicito riferimento a una versione precedente riceveranno un messaggio di errore nel processo di qualità del codice.
