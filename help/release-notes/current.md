---
title: Note sulla versione 2023.10.0
description: Queste sono le note sulla versione 2023.10.0 di Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 851364e74864c28b3bcd9285dfbe06ddb530eb10
workflow-type: ht
source-wordcount: '226'
ht-degree: 100%

---


# Note sulla versione 2023.10.0 di Cloud Manager {#release-notes}

In questa pagina sono documentate le note sulla versione 2023.10.0 di [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Per le ultime note sulla versione di Cloud Manager in AEM as a Cloud Service, fai riferimento a [Cloud Manager nelle note sulla versione corrente di AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=it)

## Data di pubblicazione {#release-date}

La data di pubblicazione della versione 2023.10.0 di [!UICONTROL Cloud Manager] è il 5 ottobre 2023. La prossima versione è pianificata per il 2 novembre 2023.

## Novità {#what-is-new}

* Il ruolo di **Responsabile della distribuzione** può [configurare un set di percorsi di contenuto che verranno invalidati o svuotati dalla cache del Dispatcher AEM quando viene eseguita una pipeline non di produzione.](/help/using/non-production-pipelines.md)
   * Queste azioni della cache verranno eseguite come parte del passaggio della pipeline di implementazione, subito dopo la distribuzione di eventuali pacchetti di contenuto.
   * Queste impostazioni utilizzano il comportamento standard del Dispatcher AEM.
* Con la versione di ottobre 2023 di Cloud Manager, le versioni di Java sono in fase di aggiornamento tramite un rollout graduale.
   * Le versioni secondarie di Java 8 e 11 e Maven sono state aggiornate e verranno implementate in modo graduale nei prossimi 2 mesi. La nuova versione include diverse correzioni di sicurezza e di bug. Le nuove versioni sono:
   * *Maven: 3.8.8*
   * *Java 8 versione: /usr/lib/jvm/jdk1.8.0_371*
   * *Java 11 versione: /usr/lib/jvm/jdk-11.0.20*
   * [Consulta i consigli OpenJDK](https://openjdk.org/groups/vulnerability/advisories/) per informazioni dettagliate sulle correzioni di sicurezza e dei bug in questi aggiornamenti JDK.
