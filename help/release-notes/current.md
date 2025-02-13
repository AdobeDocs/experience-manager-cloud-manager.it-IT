---
title: Note sulla versione 2025.2.0 di Cloud Manager
description: Ulteriori informazioni sulla versione 2025.2.0 di Cloud Manager su Adobe Managed Services.
feature: Release Information
exlid: 669b1f2d8fc68526eb091e0f93f70ab93033d193
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 9d9bf7d689c0ace41bce3f31febe8ba78636c01f
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 93%

---

# Note sulla versione di Cloud Manager 2025.2.0 su Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.02.0+Release -->

Ulteriori informazioni sulla versione di [!UICONTROL Cloud Manager] 2025.2.0 su Adobe Managed Services.

Consulta anche le [note sulla versione corrente di Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/release-notes/home).

## Date di pubblicazione {#release-date}

*Nessun bug o funzionalità di rilievo per la versione di febbraio di Cloud Manager.*

La data di pubblicazione della versione 2025.2.0 di [!UICONTROL Cloud Manager] è il venerdì 13 febbraio 2025.

La prossima pubblicazione è pianificata per il venerdì 13 marzo 2025.

## Novità {#what-is-new}

<!-- * The AEM Code Quality step now uses SonarQube 9.9 Server, replacing the older 7.4 version. This upgrade brings additional security, performance, and code quality checks, offering more comprehensive analysis and coverage for your projects. --> <!-- CMGR-45683 -->

* A partire da giovedì 13 febbraio 2025, il passaggio di qualità del codice di Cloud Manager utilizzerà una versione aggiornata di SonarQube 9.9.5.90363.

  Le regole aggiornate, disponibili per AMS in [questo collegamento](/help/using/code-quality-testing.md#code-quality-testing-step), determinano i punteggi di sicurezza e la qualità del codice per le pipeline di Cloud Manager. Questo aggiornamento può influire sui gate di qualità, bloccando potenzialmente le distribuzioni.

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
