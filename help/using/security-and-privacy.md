---
title: Sicurezza e privacy
seo-title: Sicurezza e privacy per AEM Cloud Manager
description: Segui questa pagina per saperne di più sulla sicurezza e la privacy delle tue risorse (codice/artifact).
seo-description: Segui questa pagina per saperne di più sulla sicurezza e la privacy delle tue risorse (codice/artifact) tramite AEM Cloud Manager.
uuid: 68bc2330-a62c-4c2c-925c-daa6788b143a
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: 67a54bae-99a9-4405-91e3-9a0a8b3ccc98
translation-type: tm+mt
source-git-commit: e2187565e7f06d64841eb2af9b4b1a56feb5ebe4
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Sicurezza e privacy {#security-and-privacy}

[!UICONTROL Cloud Manager] dispone di ruoli preconfigurati con autorizzazioni appropriate. In questa sezione vengono evidenziate la sicurezza e la privacy delle risorse (codice/artifact) mediante AEM Cloud Manager. Inoltre, [!UICONTROL Cloud Manager] dispone di ruoli preconfigurati con le autorizzazioni appropriate.

Per informazioni sui possibili ruoli che potete assegnare nel Admin Console  e nelle autorizzazioni per i ruoli utente, consultate [Autorizzazioni basate sui ruoli](/help/using/role-based-permissions.md).


## Isolamento risorse {#resource-isolation}

I clienti che utilizzano [!UICONTROL Cloud Manager] avranno bisogno delle proprie credenziali IMS per l&#39;autenticazione, in quanto tutte le autorizzazioni associate a [!UICONTROL Cloud Manager] verranno configurate e associate alla propria organizzazione IMS. Durante il processo di registrazione, il team di provisioning assicura che l&#39;isolamento delle risorse sia applicato in [!UICONTROL Cloud Manager].

## Protezione dei dati {#data-security}

Il codice in [!UICONTROL Cloud Manager] è crittografato in transito. I binari generati da Cloud Manager sono inoltre crittografati in transito e cifrati al momento della memorizzazione.

Ogni cliente ottiene il proprio **Git Repository** e il suo codice è sicuro e non condiviso con nessun altro **Organizations**.

## Privacy dei dati {#data-privacy}

[!UICONTROL Cloud Manager] aderisce ai principi di privacy definiti dal  Adobe. Gli sviluppatori inviano il codice in modo sicuro nell&#39; **Git Repository** attraverso il protocollo HTTPS.

L&#39;interfaccia utente per [!UICONTROL Cloud Manager] è basata su servizi conformi a un framework di controllo comune definito da  Adobe. L&#39;interfaccia utente per [!UICONTROL Cloud Manager] utilizza i servizi protetti di diversi fornitori di cloud.
