---
title: Note sulla versione 2026.11.0 di Cloud Manager
description: Scopri la versione di Cloud Manager 2026.11.0 in Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
TQID: 'https://experienceleague.adobe.com/4zfTpSYuFwrJZ-oeL1SObT14v2Rd--Z1hKn5JllHAro'
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
    internal-label: Experience Manager Cloud Manager
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: ed762d86-a04b-452b-a08f-86359bb8ff27
    internal-label: Configuration and operations
subfeature_v2:
  - id: c21ccc2b-e0c8-4853-bf41-f12259ed93f8
    internal-label: Release information
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
source-git-commit: b48085c8209c0802f6f2d321865bd1a1ee786139
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 10%
---

# Note sulla versione 2026.11.0 di Cloud Manager in Adobe Managed Services {#release-notes}

<!-- add "hold: true" to metadata above to be able to commit/merge to Main WITHOUT Publishig -->

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Scopri la versione di [!UICONTROL Cloud Manager] 2026.11.0 in Adobe Managed Services.

Consulta anche le [note sulla versione corrente di Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/release-notes/home).

## Date di pubblicazione {#release-date}

La data di rilascio per [!UICONTROL Cloud Manager] 2026.11.0 è giovedì 5 novembre 2026.
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

La prossima versione pianificata è giovedì 3 dicembre 2026.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Nuove funzioni {#new-features}

### Pipeline a livello web per AEM Managed Services {#web-tier-pipelines}

Cloud Manager ora supporta le pipeline dedicate a livello web per i programmi AMS, consentendo ai team di distribuire configurazioni a livello web e Dispatcher indipendentemente dalle distribuzioni full stack. Questo consente un’iterazione più rapida sulle modifiche a livello web, riducendo al contempo le esecuzioni di pipeline complete non necessarie.

Quando viene configurata una pipeline a livello web, le pipeline full stack ignorano automaticamente la distribuzione a livello web per tale ambiente per evitare conflitti di distribuzione. La rimozione della pipeline a livello web ripristina automaticamente il comportamento di distribuzione predefinito. <!-- CMGR-27553 -->

Consulta [Pipeline di configurazione a livello web](/help/overview/ci-cd-pipelines.md#web-tier-config-pipelines).

## Programmi Beta {#beta-program}

Al momento non sono disponibili opportunità per programmi beta.

<!--
To get exclusive access to upcoming features before their general release, participate in Cloud Manager's beta programs.

>[!IMPORTANT]
>
>Beta releases contain issues and are provided without warranty of any kind. Adobe has no obligation to maintain, correct, update, change, modify or otherwise support (through Adobe Support Services or otherwise) the beta releases. Customers use beta releases at their own risk. Do not rely on the correct functioning or performance of beta releases, or on any accompanying documentation or materials. Features and APIs in beta are subject to change without notice. Any use of the beta releases is entirely at the customer's own risk.

The following beta program opportunity is currently available:
-->

## Correzioni di bug {#bug-fixes}


* La scansione della qualità del codice non riesce nei progetti di grandi dimensioni. L’analisi della qualità del codice (SonarQube) genera registri di debug di più gigabyte e viene interrotta durante la scansione di alcune librerie in bundle, a causa di un errore di compilazione. La scansione è stata corretta in modo da essere completata normalmente sui progetti interessati. (CMGR-80025)

* L’esportazione CSV di utilizzo dei siti mostrava che le etichette dei mesi venivano spostate di un mese. Nella pagina Licenza > Dettagli sull’utilizzo di Sites, l’esportazione CSV mostra le etichette dei mesi spostate un mese prima per gli utenti con fusi orari diversi da UTC. L’esportazione mostra ora le etichette del mese corrette indipendentemente dal fuso orario dell’utente. (CMGR-80903)

* Il nome di un token di accesso riutilizzato non sovrascrive più il token esistente. Il riutilizzo di un nome di token di accesso esistente all’interno di un programma sovrascrive il token condiviso e crea segreti di accesso duplicati. Cloud Manager ora gestisce correttamente il riutilizzo dei nomi dei token, evitando sovrascritture e duplicati accidentali. (CMGR-81236)


<!--
Known Issues {#known-issues}
-->
