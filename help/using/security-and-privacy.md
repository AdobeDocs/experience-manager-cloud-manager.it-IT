---
title: Sicurezza e privacy
seo-title: Sicurezza e privacy per AEM Cloud Manager
description: Segui questa pagina per scoprire la sicurezza e la privacy delle tue risorse (codice/artefatti).
seo-description: Leggi questa pagina per scoprire la sicurezza e la privacy delle risorse (codice/artefatti) tramite AEM Cloud Manager.
uuid: 68bc2330-a62c-4c2c-925c-daa6788b143a
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: 67a54bae-99a9-4405-91e3-9a0a8b3ccc98
feature: Guida introduttiva
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 3%

---


# Sicurezza e privacy {#security-and-privacy}

[!UICONTROL Cloud Manager] dispone di ruoli preconfigurati con le autorizzazioni appropriate. Questa sezione evidenzia la sicurezza e la privacy delle risorse (codice/artifact) utilizzando AEM Cloud Manager. Inoltre, [!UICONTROL Cloud Manager] dispone di ruoli preconfigurati con le autorizzazioni appropriate.

Per informazioni sui ruoli possibili da assegnare nelle autorizzazioni per i ruoli di Admin Console e utente, consulta [Autorizzazioni basate sul ruolo](/help/using/role-based-permissions.md).


## Isolamento risorsa {#resource-isolation}

I clienti che utilizzano [!UICONTROL Cloud Manager] avranno bisogno delle proprie credenziali IMS per l’autenticazione, in quanto tutte le autorizzazioni associate a [!UICONTROL Cloud Manager] saranno configurate e associate alla propria organizzazione IMS. Durante il processo di onboarding, il team di provisioning assicura che l&#39;isolamento delle risorse sia applicato in [!UICONTROL Cloud Manager].

## Sicurezza dei dati {#data-security}

Il codice in [!UICONTROL Cloud Manager] è crittografato in transito. Anche i file binari generati da Cloud Manager vengono crittografati durante il transito e crittografati al momento della memorizzazione.

Ogni cliente ottiene il proprio **archivio Git** e il proprio codice è sicuro e non condiviso con nessun altro **Organizations**.

## Privacy dei dati {#data-privacy}

[!UICONTROL Cloud Manager] aderisce ai principi sulla privacy definiti dall&#39;Adobe. Gli sviluppatori inviano il codice in modo sicuro nell’ **archivio Git** tramite HTTPS.

L’interfaccia utente di per [!UICONTROL Cloud Manager] è basata su servizi conformi a un framework di controllo comune definito in Adobe. L&#39;interfaccia utente per [!UICONTROL Cloud Manager] utilizza servizi sicuri di diversi provider cloud.
