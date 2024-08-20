---
title: Provisioning dell’ambiente
description: Scopri come viene eseguito il provisioning degli ambienti come parte del processo di onboarding di Cloud Manager.
exl-id: eade4255-89b5-4c65-a498-1c6d4e8c73ff
source-git-commit: 4c977cdfbef438fdabd90ee104d98887f2467b49
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 27%

---


# Provisioning dell’ambiente {#environments-provisioning}

Scopri come viene eseguito il provisioning degli ambienti come parte del processo di onboarding di Cloud Manager.

## Provisioning {#provisioning}

Durante il processo di onboarding, Adobe esegue automaticamente il provisioning di tutti gli ambienti cloud AEM acquistati e li collega al programma in [!UICONTROL Cloud Manager]. Ogni abbonamento a Managed Services Adobe include ambienti cloud AEM. In genere includono almeno un ambiente di produzione e un ambiente di staging. Facoltativamente, possono anche includere uno o più ambienti di sviluppo o di test.

## E-mail di benvenuto {#welcome-email}

Al termine del processo di provisioning dell&#39;ambiente, l&#39;amministratore del cliente designato riceve un messaggio e-mail di benvenuto con la conferma di accesso all&#39;Adobe [!UICONTROL Experience Cloud]. L&#39;e-mail di benvenuto contiene informazioni dettagliate su come iniziare a utilizzare i servizi [!UICONTROL Experience Cloud], gli ambienti cloud [!UICONTROL AEM Managed Services] e il portale self-service [!UICONTROL Cloud Manager]. Inoltre, l’e-mail contiene informazioni importanti come le informazioni di contatto del Customer Success Engineer (CSE), dove sono disponibili risorse di supporto, forum, domande frequenti e molto altro. Nell&#39;elenco delle risorse fornite nell&#39;e-mail vengono inoltre fornite informazioni su come accedere a [!UICONTROL Cloud Manager] per gli ambienti cloud AEM.

## Passaggi successivi {#next-steps}

Dopo aver ricevuto l’e-mail di benvenuto, sei pronto per accedere a [!UICONTROL Cloud Manager] in qualità di amministratore di sistema, utilizzando le credenziali Adobe IMS. Dopo aver effettuato l’accesso, puoi verificare che gli ambienti di produzione e non produzione cloud AEM siano disponibili e funzionino correttamente.

[!UICONTROL Cloud Manager] utilizza questi ambienti cloud AEM per eseguire la pipeline CI/CD. Distribuisce il codice dal relativo archivio Git all’ambiente di staging. Quindi distribuisce il codice nell’ambiente di produzione dell’AEM. Puoi anche accedere agli ambienti cloud AEM direttamente da [!UICONTROL Cloud Manager] quando sei pronto per iniziare a creare esperienze digitali per le tue proprietà web.
