---
title: Customer Journey
seo-title: Percorso del cliente di Adobe AEM Cloud Manager
description: Segui questa pagina per scoprire come iniziare a usare Cloud Manager in qualità di cliente.
seo-description: Segui questa pagina per scoprire come iniziare a usare Adobe AEM Cloud Manager in qualità di cliente.
uuid: d4468eb6-5bde-48dd-b96e-0cc61e046f96
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: bc9a0d63-ae6b-4fe9-81e5-bf9844f04e54
translation-type: tm+mt
source-git-commit: 77b7e2fc81880a7f1878fa9553ce2ae8078d1b78
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 0%

---


# Customer Journey {#customer-journey}

In qualità di cliente, potresti essere un nuovo Adobe Experience Manager (AEM), al momento usare AEM 6.4, o dover effettuare l’aggiornamento alla versione AEM 6.4 per poter utilizzare [!UICONTROL Cloud Manager]. Gli scenari seguenti illustrano il percorso come cliente nuovo o esistente con cui iniziare [!UICONTROL Cloud Manager].

>[!NOTE]
>
>[!UICONTROL Cloud Manager] è disponibile solo per i clienti dei servizi gestiti Adobe che utilizzano AEM 6.4 o versione successiva.

## On-boarding a [!UICONTROL Cloud Manager]{#on-boarding-to-cloud-manager}

1. **Nuovo cliente AEM su Adobe Managed Services**

   Come nuovo cliente, l&#39;utente sarà imbarcato [!UICONTROL Cloud Manager] nell&#39;ambito del processo di registrazione al servizio cloud gestito di Adobe.

   L’URL a cui accedere [!UICONTROL Cloud Manager] verrà incluso nel messaggio e-mail di benvenuto, insieme alle istruzioni per accedere a [!UICONTROL Experience Cloud]e utilizzare Adobe Admin Console per gestire i tuoi utenti e le loro rispettive autorizzazioni, per gli utenti a cui è necessario accedere [!UICONTROL Cloud Manager].

1. **Cliente AEM esistente su Adobe Managed Services**

   In qualità di cliente esistente, dovrete prima aggiornare gli ambienti di produzione e non produzione esistenti alla versione AEM 6.4. Contemporaneamente all&#39;esecuzione dell&#39;aggiornamento, l&#39;utente verrà imbarcato e gli verrà fornito l&#39;URL a cui accedere [!UICONTROL Cloud Manager]. Inoltre, dovrai iniziare a utilizzare Adobe Admin Console per gestire i tuoi utenti e le loro rispettive autorizzazioni, per gli utenti a cui è necessario accedere [!UICONTROL Cloud Manager].

   Anche il progetto AEM esistente dovrà essere conforme alle best practice consigliate, in quanto inizierete a utilizzare [!UICONTROL Cloud Manager] per distribuire nuove modifiche al codice negli ambienti AEM.

   Per ulteriori informazioni sui vantaggi dell’aggiornamento ad AEM 6.4, consulta [Aggiornamento ad AEM 6.4](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/upgrade.html).

## Accesso [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Per accedere a [!UICONTROL Cloud Manager] e agli ambienti AEM, è sufficiente accedere alla pagina di [!UICONTROL Experience Cloud] destinazione, utilizzare le credenziali di Adobe Identity Management e selezionare AEM dall’interfaccia dello switcher di soluzione.

Dopo aver effettuato [!UICONTROL Cloud Manager] il primo accesso, potrete accedere agli ambienti AEM direttamente dall’ [!UICONTROL Cloud Manager] interfaccia utente. A questo punto, è possibile esplorare tutte le possibilità di [!UICONTROL Cloud Manager], una volta che il primo ramo di codice sarà pronto per essere distribuito nelle fasi e negli ambienti di produzione.

Per esplorare e iniziare con [!UICONTROL Cloud Manager], consulta Accesso [alla](first-time-login.md)prima volta. Per ulteriori informazioni su AEM, consultate [Guida introduttiva ad AEM 6.4](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/deploy.html). Per ulteriori informazioni, consulta Risorse [](https://www.adobe.com/marketing-cloud/experience-manager/resources.html?promoid=759X6WV8&amp;mv=other) AEM.

## Getting Started with [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Una volta effettuato l’accesso, [!UICONTROL Cloud Manager]la prima cosa da fare è configurare l’ambiente dell’archivio di codice, quindi il team e i ruoli. Nello specifico, le appartenenze ai ruoli vengono assegnate aggiungendo l&#39;utente a un [!UICONTROL Cloud Manager] profilo utilizzando l&#39;interfaccia utente di Admin Console.

Successivamente, è necessario impostare i rami del codice sorgente nell&#39;archivio **** Git, definire gli obiettivi in termini di KPI per carico e prestazioni e scenari di test per distribuire correttamente il codice nell&#39;area di visualizzazione e negli ambienti di produzione una volta che tutti i controlli di qualità siano stati superati.

## Fine del viaggio {#end-to-end-journey}

Il diagramma seguente illustra il percorso del cliente ad alto livello, quando si utilizza la pipeline [!UICONTROL Cloud Manager] CI/CD per distribuire le modifiche del codice allo stadio e agli ambienti di produzione.

![](assets/screen_shot_2018-05-15at124004pm.png)

