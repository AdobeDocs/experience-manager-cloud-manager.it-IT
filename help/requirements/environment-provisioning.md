---
title: Provisioning dell’ambiente
description: Scopri come viene eseguito il provisioning degli ambienti come parte del processo di onboarding di Cloud Manager.
exl-id: eade4255-89b5-4c65-a498-1c6d4e8c73ff
TQID: https://experienceleague.adobe.com/xLjZdRZeCiqF0KxHQ1nBI4IBBsh4BDTqETv79lrypR0
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: 02ecd16a1735fe37ac606d275da0f61406841f56
workflow-type: tm+mt
source-wordcount: 287
ht-degree: 66%

---

# Provisioning dell’ambiente {#environments-provisioning}

Scopri come viene eseguito il provisioning degli ambienti come parte del processo di onboarding di Cloud Manager.

## Provisioning {#provisioning}

Durante il processo di onboarding, Adobe esegue automaticamente il provisioning di tutti gli ambienti cloud AEM acquistati e li collega al programma in [!UICONTROL Cloud Manager]. Ogni abbonamento ad Adobe Managed Services include ambienti cloud AEM. In genere includono almeno un ambiente di produzione e un ambiente di staging. Facoltativamente, possono anche includere uno o più ambienti di sviluppo o test.

## E-mail di benvenuto {#welcome-email}

Al termine del processo di provisioning dell&#39;ambiente, l&#39;amministratore del cliente designato riceve un messaggio e-mail di benvenuto con la conferma di poter accedere ad Adobe [!UICONTROL Experience Cloud]. L’e-mail di benvenuto contiene informazioni dettagliate su come iniziare a utilizzare i servizi di [!UICONTROL Experience Cloud], gli ambienti cloud di [!UICONTROL AEM Managed Services], nonché il portale self-service di [!UICONTROL Cloud Manager]. Inoltre, l’e-mail fornisce al Customer Success Engineer (CSE) informazioni di contatto, risorse di supporto, forum e domande comuni. Nell’elenco delle risorse fornite nell’e-mail, riceverai anche informazioni su come accedere a [!UICONTROL Cloud Manager] per gli ambienti cloud AEM.

## Passaggi successivi {#next-steps}

Dopo aver ricevuto l&#39;e-mail di benvenuto, puoi accedere a [!UICONTROL Cloud Manager] come amministratore di sistema, utilizzando le tue credenziali Adobe IMS. Dopo aver effettuato l’accesso, puoi verificare che gli ambienti di produzione e non produzione cloud AEM siano disponibili e funzionino correttamente.

[!UICONTROL Cloud Manager] utilizza tali ambienti cloud AEM per eseguire la pipeline CI/CD. Distribuisce il codice dal relativo archivio Git nell’ambiente di staging. Quindi distribuisce il codice nell’ambiente di produzione di AEM. Potrai anche accedere agli ambienti cloud AEM direttamente da [!UICONTROL Cloud Manager] quando sarà tutto pronto per iniziare a creare esperienze digitali per le tue proprietà Web.
