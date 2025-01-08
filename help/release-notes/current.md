---
title: Note sulla versione 2024.12.0 di Cloud Manager
description: Ulteriori informazioni sulla versione 2024.12.0 di Cloud Manager su Adobe Managed Services.
feature: Release Information
exl-id: 811567af-66c9-4c1f-ae9e-60603b70ef80
source-git-commit: dcf2a4727b800f4364fcc7d757d281bde2738a55
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 87%

---

# Note sulla versione di Cloud Manager 2024.12.0 su Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release -->

Ulteriori informazioni sulla versione di [!UICONTROL Cloud Manager] 2024.12.0 su Adobe Managed Services.

>[!NOTE]
>
>Consulta le [note sulla versione corrente di Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/release-notes/home).

## Date di pubblicazione {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

La data di pubblicazione della versione 2024.12.0 di [!UICONTROL Cloud Manager] è il 5 dicembre 2024.

La prossima versione è pianificata per il 23 gennaio 2025.

## Novità {#what-is-new}

<!-- * The AEM Code Quality step now uses SonarQube 9.9 Server, replacing the older 7.4 version. This upgrade brings additional security, performance, and code quality checks, offering more comprehensive analysis and coverage for your projects. --> <!-- CMGR-45683 -->

* A partire da giovedì 13 febbraio 2025, il passaggio per la qualità del codice di Cloud Manager utilizza ora una versione aggiornata di SonarQube 9.9.5.90363.

  Le regole aggiornate, disponibili per AMS in [questo collegamento](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/using/code-quality-testing#code-quality-testing-step), determinano i punteggi di sicurezza e la qualità del codice per le pipeline di Cloud Manager. Questo aggiornamento può influire sui gate di qualità, bloccando potenzialmente le distribuzioni.

## Programma per i primi utilizzatori {#early-adoption}

Partecipa al programma per i primi utilizzatori di Cloud Manger e concediti la possibilità di testare le prossime funzionalità.

### Bring Your Own Git: ora con supporto per GitLab e Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

La funzione **Bring Your Own Git** è stata estesa in modo da includere il supporto per archivi esterni come GitLab e Bitbucket. Questo nuovo supporto si aggiunge a quello già esistente per archivi GitHub privati ed aziendali. Quando aggiungi questi nuovi archivi, puoi anche collegarli direttamente alle pipeline. Puoi inoltre ospitare questi archivi sia su piattaforme cloud pubbliche sia all’interno della tua infrastruttura o del tuo cloud privato. Questa integrazione elimina anche la necessità di sincronizzare continuamente il codice con l’archivio Adobe e offre la possibilità di convalidare le richieste pull prima di unirle in un ramo principale.

Le pipeline che utilizzano archivi esterni (esclusi quelli ospitati da GitHub) e il **Trigger di implementazione** impostato su **Cambiamenti su Git** ora vengono avviate automaticamente.

Consulta [Aggiungere archivi esterni in Cloud Manager](/help/managing-code/external-repositories.md).

![Finestra di dialogo Aggiungi archivio](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Attualmente, i controlli di qualità predefiniti per il codice di richiesta pull sono esclusivi degli archivi ospitati in GitHub, ma è in preparazione un aggiornamento per estendere questa funzionalità anche ad altri fornitori Git.

Se ti interessa testare questa nuova funzione e condividere il tuo feedback, invia un’e-mail a [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) dall’indirizzo e-mail associato al tuo Adobe ID. Se ti trovi in una struttura di archivio privata/pubblica o aziendale, assicurati di specificare la piattaforma Git che desideri utilizzare.


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
