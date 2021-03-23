---
title: Customer Journey
seo-title: Percorso cliente Adobe AEM Cloud Manager
description: Per iniziare a utilizzare Cloud Manager, segui questa pagina per saperne di più sul tuo percorso come cliente.
seo-description: Per iniziare a utilizzare Adobe AEM Cloud Manager, segui questa pagina per saperne di più sul tuo percorso come cliente.
uuid: d4468eb6-5bde-48dd-b96e-0cc61e046f96
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: bc9a0d63-ae6b-4fe9-81e5-bf9844f04e54
feature: Guida introduttiva
level: Principiante
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 2%

---


# Customer Journey {#customer-journey}

In qualità di cliente, potresti essere un nuovo cliente di Adobe Experience Manager (AEM), attualmente utilizzando AEM 6.4, o potrebbe essere necessario eseguire l’aggiornamento alla versione AEM 6.4 per utilizzare [!UICONTROL Cloud Manager]. Gli scenari seguenti spiegano il tuo percorso come cliente nuovo o esistente con cui iniziare a usare [!UICONTROL Cloud Manager].

>[!NOTE]
>
>[!UICONTROL Cloud Manager] è disponibile solo per i clienti di Adobe Managed Services che utilizzano AEM 6.4 o versioni successive.

## On-boarding su [!UICONTROL Cloud Manager]{#on-boarding-to-cloud-manager}

1. **Nuovo cliente AEM su Adobe Managed Services**

   In qualità di nuovo cliente, l’utente verrà imbarcato in [!UICONTROL Cloud Manager] come parte del processo di onboarding in Adobe Managed Services.

   L&#39;URL per l&#39;accesso [!UICONTROL Cloud Manager] verrà incluso nell&#39;e-mail di benvenuto, insieme alle istruzioni per l&#39;accesso a [!UICONTROL Experience Cloud] e utilizzerà Adobe Admin Console per gestire i tuoi utenti e le rispettive autorizzazioni, per gli utenti che devono accedere a [!UICONTROL Cloud Manager].

1. **Cliente AEM esistente su Adobe Managed Services**

   In qualità di cliente esistente, dovrai prima aggiornare gli ambienti di produzione e non di produzione esistenti alla versione 6.4 di AEM. Contemporaneamente all&#39;esecuzione dell&#39;aggiornamento, riceverai l&#39;URL per accedere a [!UICONTROL Cloud Manager]. Inoltre, dovrai iniziare a utilizzare Adobe Admin Console per gestire i tuoi utenti e le loro rispettive autorizzazioni, per gli utenti che devono accedere a [!UICONTROL Cloud Manager].

   Il progetto AEM esistente dovrà inoltre conformarsi alle best practice consigliate, in quanto inizierà a utilizzare [!UICONTROL Cloud Manager] per distribuire nuove modifiche al codice negli ambienti di AEM.

   Per ulteriori informazioni sui vantaggi dell&#39;aggiornamento a AEM 6.4, consulta [Aggiornamento a AEM 6.4](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/upgrade.html).

## Accesso a [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Per accedere a [!UICONTROL Cloud Manager] e agli ambienti di AEM, effettua l’accesso alla pagina di destinazione [!UICONTROL Experience Cloud] utilizzando le credenziali Adobe Identity Management e seleziona AEM dall’interfaccia del commutatore della soluzione.

Dopo aver effettuato l’accesso a [!UICONTROL Cloud Manager] per la prima volta, avrai accesso ai tuoi ambienti di AEM direttamente dall’ [!UICONTROL Cloud Manager] interfaccia utente. A questo punto, sei pronto per esplorare tutte le possibilità di [!UICONTROL Cloud Manager], una volta che avrai a disposizione il tuo primo ramo di codice pronto per essere implementato nel tuo stage e negli ambienti di produzione.

Per esplorare e iniziare a utilizzare [!UICONTROL Cloud Manager], consulta [Primo accesso](first-time-login.md). Per ulteriori informazioni su AEM, consulta [Guida introduttiva a AEM 6.4](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/deploy.html). Inoltre, per ulteriori informazioni, fai riferimento a [Risorse AEM](https://www.adobe.com/marketing-cloud/experience-manager/resources.html?promoid=759X6WV8&amp;mv=other) .

## Guida introduttiva a [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Una volta effettuato l’accesso a [!UICONTROL Cloud Manager], la prima cosa da fare è configurare l’ambiente dell’archivio di codice, quindi il team e i ruoli. In particolare, le appartenenze ai ruoli vengono assegnate aggiungendo l’utente a un profilo [!UICONTROL Cloud Manager] utilizzando l’interfaccia utente di Admin Console.

Successivamente, è necessario impostare i rami del codice sorgente in **Git Repository**, definire gli obiettivi in termini di KPI di carico e prestazioni e scenari di test per distribuire correttamente il codice nel tuo ambiente di stage e produzione una volta che tutti i controlli di qualità sono stati superati.

## Fine del percorso {#end-to-end-journey}

Il diagramma seguente illustra il percorso di clienti di alto livello quando si utilizza la pipeline CI/CD [!UICONTROL Cloud Manager] per distribuire le modifiche al codice negli ambienti di stage e produzione.

![](assets/screen_shot_2018-05-15at124004pm.png)

