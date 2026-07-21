---
title: Sicurezza e privacy
description: Scopri la sicurezza e la privacy del codice e delle risorse degli artefatti in Adobe Cloud Manager.
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
TQID: https://experienceleague.adobe.com/mtWOzJnzV8k403LlyD9Fn9WSE5XTgjHzyVuA4j62MMg
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: d5a34a9f6d050eaff241c0f42c9cf023cbc8036a
workflow-type: tm+mt
source-wordcount: 201
ht-degree: 26%

---

# Sicurezza e privacy {#security-and-privacy}

Scopri la sicurezza e la privacy del codice e delle risorse degli artefatti in Adobe Cloud Manager.

## Ruoli e autorizzazioni {#roles}

Cloud Manager dispone di ruoli preconfigurati con le autorizzazioni appropriate.

Per informazioni sui possibili ruoli che è possibile assegnare in Admin Console e sulle autorizzazioni per i ruoli utente, consulta [Autorizzazioni basate sul ruolo](/help/requirements/role-based-permissions.md).

## Isolamento risorse {#resource-isolation}

I clienti Cloud Manager hanno bisogno delle credenziali IMS per autenticarsi perché tutte le autorizzazioni associate a Cloud Manager sono collegate alle loro organizzazioni IMS. Durante il processo di onboarding, il team di provisioning assicura che l’isolamento delle risorse sia applicato in Cloud Manager.

## Sicurezza dei dati {#data-security}

Il codice Cloud Manager è crittografato in transito. Cloud Manager crea file binari crittografati anche durante la trasmissione e memorizzati in un formato crittografato.

Ogni cliente ottiene il proprio archivio Git e il codice è protetto e non condiviso con altre organizzazioni.

## Privacy dei dati {#data-privacy}

Cloud Manager rispetta i principi sulla privacy definiti da Adobe. Gli sviluppatori inviano il codice negli archivi Git in modo sicuro tramite HTTPS.

L’interfaccia utente di Cloud Manager utilizza servizi conformi al framework di controllo comune di Adobe. L’interfaccia utente di Cloud Manager utilizza servizi sicuri di diversi provider cloud.
