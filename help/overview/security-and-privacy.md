---
title: Sicurezza e privacy
description: Scopri la sicurezza e la privacy del codice e delle risorse degli artefatti in Cloud Manager.
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
TQID: https://experienceleague.adobe.com/mtWOzJnzV8k403LlyD9Fn9WSE5XTgjHzyVuA4j62MMg
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 50eb58593d7f78492fd384c99c3727c5f731c989
workflow-type: tm+mt
source-wordcount: 202
ht-degree: 100%

---

# Sicurezza e privacy {#security-and-privacy}

Scopri la sicurezza e la privacy del codice e delle risorse degli artefatti in Cloud Manager.

## Ruoli e autorizzazioni {#roles}

[!UICONTROL Cloud Manager] dispone di ruoli preconfigurati con autorizzazioni appropriate.

Per informazioni sui possibili ruoli che è possibile assegnare in Admin Console e sulle autorizzazioni per i ruoli utente, consulta [Autorizzazioni basate sul ruolo](/help/requirements/role-based-permissions.md).

## Isolamento risorse {#resource-isolation}

I clienti di [!UICONTROL Cloud Manager] hanno bisogno delle credenziali IMS per autenticarsi in quanto tutte le autorizzazioni associate a [!UICONTROL Cloud Manager] sono collegate alle loro organizzazioni IMS. Durante il processo di onboarding, il team di provisioning assicura che l’isolamento delle risorse sia applicato in [!UICONTROL Cloud Manager].

## Sicurezza dei dati {#data-security}

Il codice in [!UICONTROL Cloud Manager] è crittografato in transito. Anche i file binari generati da Cloud Manager vengono crittografati in transito e al momento dell’archiviazione.

Ogni cliente ottiene il proprio archivio Git: il codice è sicuro e non condiviso con altre organizzazioni.

## Privacy dei dati {#data-privacy}

[!UICONTROL Cloud Manager] rispetta i principi sulla privacy definiti da Adobe. Gli sviluppatori inviano il codice negli archivi Git in modo sicuro tramite HTTPS.

L’interfaccia utente di [!UICONTROL Cloud Manager] è basata su servizi conformi a un’infrastruttura di controllo comune di Adobe. L’interfaccia utente di [!UICONTROL Cloud Manager] utilizza servizi sicuri di diversi provider cloud.
