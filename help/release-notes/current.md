---
title: Note sulla versione 2023.10.0
description: Queste sono le note sulla versione 2023.10.0 di Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: a5a304541409bc1775090eef2a669e1e0bcf005e
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 58%

---


# Note sulla versione 2023.10.0 di Cloud Manager {#release-notes}

In questa pagina sono documentate le note sulla versione 2023.10.0 di [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Per le ultime note sulla versione di Cloud Manager in AEM as a Cloud Service, fai riferimento a [Cloud Manager nelle note sulla versione corrente di AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=it)

## Data di pubblicazione {#release-date}

La data di pubblicazione della versione 2023.10.0 di [!UICONTROL Cloud Manager] è il 5 ottobre 2023. La prossima versione è pianificata per il 2 novembre 2023.

## Novità {#what-is-new}

* Il **Responsabile dell’implementazione** ruolo può [configura un set di percorsi di contenuto che verranno invalidati o svuotati dalla cache del Dispatcher AEM quando viene eseguita una pipeline non di produzione.](/help/using/non-production-pipelines.md)
   * Queste azioni della cache verranno eseguite come parte del passaggio della pipeline di implementazione, subito dopo la distribuzione di eventuali pacchetti di contenuto.
   * Queste impostazioni utilizzano il comportamento standard del Dispatcher AEM.
* Con la versione di ottobre 2023 di Cloud Manager, le versioni Java sono in fase di aggiornamento tramite un rollout graduale.
   * Le versioni Java sono state aggiornate agli Oracli JDK 8u371 e Oracle JDK 11.0.20.
   * [Consulta l’avviso OpenJDK](https://openjdk.org/groups/vulnerability/advisories/) per informazioni dettagliate sulla sicurezza e sui bug risolti in questi aggiornamenti JDK.
