---
title: Note sulla versione 2020.7.0
seo-title: Note sulla versione di AEM Cloud Manager 2020.7.0
description: Segui questa pagina per ottenere informazioni sulla versione 2020.7.0 di Cloud Manager
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2020.7.0 di AEM Cloud Manager
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 52%

---

# Note sulla versione 2020.7.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per la versione [!UICONTROL Cloud Manager] 2020.7.0.

## Data di rilascio {#release-date}

La data di rilascio per la versione 2020.7.0 è il 9 luglio 2020.[!UICONTROL Cloud Manager]

## Novità {#whats-new}

* Il collegamento e il collegamento delle istanze del dispatcher dai load balancer durante le distribuzioni di produzione ora funziona in modo più coerente.

* Il contenitore di build di Cloud Manager ora supporta sia Java 8 che Java 11.

* Le pipeline di Cloud Manager ora supportano variabili e segreti impostati dal cliente.
Per ulteriori informazioni, consulta [Variabili delle pipeline](/help/using/build-environment-details.md#pipeline-variables).

## Correzioni di bug {#bug-fixes}

* Le opzioni **Annulla** e **Salva** nella pagina Modifica pipeline non di produzione non erano sempre visibili.

* Alcuni errori nel processo di qualità del codice potevano causare la generazione non corretta del file di registro.

* Tramite l’interfaccia utente non si potevano scaricare in modo coerente i log di alcuni fasi di pipeline di grandi dimensioni.

## Problemi noti {#known-issues}

* Quando un ambiente AMS contiene un’istanza di standby, il messaggio registrato indica che l’istanza è inattiva anziché in modalità standby.

* A causa di una modifica nel modo in cui viene calcolata la copertura del codice, la versione _minima_ del plugin Jacoco è ora 0.7.5.201505241946 (rilasciata a maggio 2015). I clienti che fanno esplicito riferimento a una versione precedente riceveranno un messaggio di errore nel processo di qualità del codice.
