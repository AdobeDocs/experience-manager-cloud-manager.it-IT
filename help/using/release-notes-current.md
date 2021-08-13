---
title: Note sulla versione 2021.8.0
description: Segui questa pagina per ottenere informazioni sulla versione 2021.8.0 di Cloud Manager
feature: Informazioni sulla versione
source-git-commit: c4deb06615652736ff7584566507a2b42a88bfb1
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 8%

---

# Note sulla versione 2021.8.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per [!UICONTROL Cloud Manager] la versione 2021.8.0.

>[!NOTE]
>Fai riferimento a [Note sulla versione corrente](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access) per visualizzare le ultime note sulla versione per Cloud Manager in AEM come Cloud Service.

## Data di rilascio {#release-date}

La data di rilascio per la versione 2021.8.0 di [!UICONTROL Cloud Manager] è il 12 agosto 2021.
La prossima versione è prevista per il 9 settembre 2021.

## Novità {#whats-new}

* Funzionalità self-service per consentire agli utenti di creare e gestire più archivi tramite l’interfaccia utente di Cloud Manager.

* SonarQube leggeva inutilmente i dati della cronologia di Git. Su basi di codice di grandi dimensioni, ciò potrebbe comportare una multa non necessaria per le prestazioni della build.

* È ora disponibile un’API per annullare la validità della cache di dipendenza Maven per pipeline.

* La versione di AEM Project Archetype utilizzata da Cloud Manager è stata aggiornata alla versione 29.

## Correzioni di bug {#bug-fixes}

* Talvolta, quando una pipeline viene attivata due volte per qualche motivo, si verifica un errore di una delle esecuzioni che non riesce con *non è in grado di aggiornare lo stato di esecuzione della pipeline*.
