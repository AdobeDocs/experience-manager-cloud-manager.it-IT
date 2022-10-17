---
title: Sicurezza e privacy
description: Scopri la sicurezza e la privacy del codice e delle risorse degli artefatti in Cloud Manager.
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
source-git-commit: d7751757c1d3bda3d60406a1d39cb41c61f5c863
workflow-type: ht
source-wordcount: '189'
ht-degree: 100%

---


# Sicurezza e privacy {#security-and-privacy}

Scopri la sicurezza e la privacy del codice e delle risorse degli artefatti in Cloud Manager.

## Ruoli e autorizzazioni {#roles}

[!UICONTROL Cloud Manager] dispone di ruoli preconfigurati con le autorizzazioni appropriate.

Per informazioni sui possibili ruoli che è possibile assegnare nell’Admin Console e sulle autorizzazioni per i ruoli utente, consulta il documento [Autorizzazioni basate sul ruolo.](/help/requirements/role-based-permissions.md)

## Isolamento risorse {#resource-isolation}

[!UICONTROL Cloud Manager] i clienti hanno bisogno delle credenziali IMS per autenticarsi in quanto tutte le autorizzazioni associate a [!UICONTROL Cloud Manager] sono collegate alle loro organizzazioni IMS. Durante il processo di onboarding, il team di provisioning assicura che l’isolamento delle risorse sia applicato in [!UICONTROL Cloud Manager].

## Sicurezza dei dati {#data-security}

Il codice in [!UICONTROL Cloud Manager] è crittografato in transito. Anche i file binari generati da Cloud Manager vengono crittografati in transito e al momento dell’archiviazione.

Ogni cliente ottiene il proprio archivio Git; il codice è sicuro e non condiviso con altre organizzazioni.

## Privacy dei dati {#data-privacy}

[!UICONTROL Cloud Manager] rispetta i principi sulla privacy definiti da Adobe. Gli sviluppatori inviano il codice in modo sicuro negli archivi Git tramite HTTPS.

L&#39;interfaccia utente di [!UICONTROL Cloud Manager] è basata su servizi conformi a un framework di controllo comune di Adobe. L’interfaccia utente di [!UICONTROL Cloud Manager] utilizza servizi sicuri di diversi provider cloud.
