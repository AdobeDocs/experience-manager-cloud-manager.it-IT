---
title: Percorso dell’utente
description: Scopri i diversi scenari di onboarding e come iniziare a utilizzare Cloud Manager.
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: 6a5615c0db91c62fc8858b967021b46c7b383aa0
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 21%

---


# Percorso utenti {#user-journey}

In qualità di utente AEM (Adobe Experience Manager), probabilmente rientra in uno dei seguenti scenari:

* Lei è nuovo all&#39;AEM.
* Attualmente sta usando AEM 6.x.
* Devi eseguire l&#39;aggiornamento a AEM 6.5 per utilizzare [!UICONTROL Cloud Manager].

Questo documento illustra questi tre scenari e spiega il percorso per iniziare a utilizzare [!UICONTROL Cloud Manager].

>[!NOTE]
>
>[!UICONTROL Cloud Manager] è disponibile solo per i clienti di Adobe Managed Services (AMS) che utilizzano AEM 6.4 o versioni successive.

## Onboarding {#onboarding}

Il processo di onboarding varia a seconda se si sta utilizzando AMS per la prima volta oppure si è un cliente AMS esistente.

### Utilizzo di Adobe Managed Services per la prima volta {#new-to-ams}

In qualità di nuovo cliente, inizierai a utilizzare [!UICONTROL Cloud Manager] come parte del processo di onboarding in Adobe Managed Services.

Come parte del processo di onboarding, ricevi un’e-mail di benvenuto che include quanto segue:

* URL per accedere a [!UICONTROL Cloud Manager].
* Istruzioni per accedere a [!UICONTROL Experience Cloud].
* Le istruzioni per utilizzare l’Admin Console per la gestione degli utenti e delle relative autorizzazioni in modo che possano accedere a [!UICONTROL Cloud Manager] se necessario.

### Cliente Managed Services Adobe corrente {#existing-customer}

In qualità di cliente AMS esistente, devi prima aggiornare gli ambienti di produzione e non di produzione esistenti a AEM 6.4 o versione successiva.

Durante l&#39;aggiornamento, hai effettuato l&#39;onboarding in Cloud Manager e ti è stato fornito l&#39;URL per accedere a [!UICONTROL Cloud Manager]. Inoltre, per gli utenti che devono accedere a [!UICONTROL Cloud Manager], devi iniziare a utilizzare l&#39;Admin Console per gestirli insieme alle relative autorizzazioni.

Anche il progetto AEM esistente deve essere conforme alle best practice consigliate, perché inizia a utilizzare [!UICONTROL Cloud Manager] per la distribuzione di nuove modifiche al codice negli ambienti AEM.

Per ulteriori informazioni sui vantaggi dell&#39;aggiornamento a AEM 6.5, vedere [Aggiornamento a AEM 6.5](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/upgrading/upgrade).

## Accedi a [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Accedi alla pagina di destinazione [!UICONTROL Experience Cloud] utilizzando le credenziali Identity Management dell&#39;Adobe. Da qui, seleziona AEM dal commutatore della soluzione per accedere a [!UICONTROL Cloud Manager] e agli ambienti AEM.

Dopo il primo accesso a [!UICONTROL Cloud Manager], potrai accedere agli ambienti AEM direttamente dall&#39;interfaccia utente di [!UICONTROL Cloud Manager]. A questo punto, sei pronto per esplorare tutte le opportunità di [!UICONTROL Cloud Manager] e preparare il tuo primo ramo di codice da distribuire negli ambienti di staging e produzione.

Per iniziare a utilizzare [!UICONTROL Cloud Manager], vedi [Primo accesso](/help/getting-started/first-time-login.md).

Per ulteriori informazioni sull&#39;AEM, vedere [Distribuzione e manutenzione](https://experienceleague.adobe.com/it/docs/experience-manager-65/content/implementing/deploying/deploying/deploy).

## Introduzione a [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Dopo aver effettuato l&#39;accesso a [!UICONTROL Cloud Manager], è possibile iniziare con il progetto AEM eseguendo le operazioni seguenti:

1. Configura l’ambiente dell’archivio del codice.
1. Imposta il team e i ruoli. Le appartenenze al ruolo vengono assegnate aggiungendo l’utente a un profilo di [!UICONTROL Cloud Manager] utilizzando l’Admin Console.
1. Configura i rami del codice sorgente nell’archivio Git.
1. Definisci gli obiettivi in termini di KPI (Key Performance Indicators) di carico e prestazioni.
1. Definisci gli scenari di test per distribuire correttamente il codice negli ambienti di staging e produzione dopo che tutti i controlli di qualità sono stati superati.

## Percorso completo {#end-to-end-journey}

Questo diagramma illustra il percorso del cliente ad alto livello quando si utilizza la pipeline CI/CD [!UICONTROL Cloud Manager] per la distribuzione delle modifiche al codice negli ambienti di staging e produzione.

![Percorso end-to-end](/help/assets/screen_shot_2018-05-15at124004pm.png)
