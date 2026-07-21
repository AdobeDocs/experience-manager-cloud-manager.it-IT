---
title: Onboarding degli utenti
description: Scopri i diversi scenari di onboarding e come iniziare a utilizzare Cloud Manager.
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
TQID: https://experienceleague.adobe.com/EnNaMZzu5bLUD3Jjsp6ovqFvoFM30ju4FOQJfmySLEk
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 2cd89edca1c1dfac7f1b7b68eccdf1416efb4724
workflow-type: tm+mt
source-wordcount: 567
ht-degree: 62%

---

# Onboarding degli utenti {#user-journey}

In qualità di utente di AEM (Adobe Experience Manager), puoi soddisfare uno dei seguenti scenari:

* Non hai familiarità con AEM.
* Utilizzi attualmente AEM 6.x.
* Devi eseguire l’aggiornamento ad AEM 6.5 per utilizzare [!UICONTROL Cloud Manager].

Questo documento descrive questi tre scenari e spiega il processo per iniziare a utilizzare [!UICONTROL Cloud Manager].

>[!NOTE]
>
>[!UICONTROL Cloud Manager] è disponibile solo per i clienti di Adobe Managed Services (AMS) che utilizzano AEM 6.4 o versioni successive.

## Onboarding {#onboarding}

Il processo di onboarding varia a seconda se si sta utilizzando AMS per la prima volta oppure si è un cliente AMS esistente.

### Utilizzo di Adobe Managed Services per la prima volta {#new-to-ams}

In qualità di nuovo cliente, hai effettuato l&#39;onboarding in [!UICONTROL Cloud Manager] nell&#39;ambito del processo di onboarding in Adobe Managed Services.

Come parte del processo di onboarding, riceverai un’e-mail di benvenuto che include:

* L’URL per accedere a [!UICONTROL Cloud Manager].
* Le istruzioni per l’accesso a [!UICONTROL Experience Cloud].
* Le istruzioni per utilizzare l’Admin Console per la gestione degli utenti e delle relative autorizzazioni in modo che possano accedere a Cloud Manager se necessario.

### Cliente attuale di Adobe Managed Services {#existing-customer}

In qualità di cliente AMS esistente, devi prima aggiornare gli ambienti di produzione e non di produzione esistenti alla versione AEM 6.4 o superiore.

Durante l’aggiornamento, riceverai l’URL per accedere a [!UICONTROL Cloud Manager] e potrai iniziare a utilizzarlo. Inoltre, dovrai iniziare a utilizzare Admin Console per gestire gli utenti che devono accedere a [!UICONTROL Cloud Manager] insieme alle relative autorizzazioni.

Anche il progetto AEM esistente deve essere conforme alle procedure consigliate, perché inizia a utilizzare [!UICONTROL Cloud Manager] per distribuire nuove modifiche al codice negli ambienti AEM.

Per ulteriori informazioni sui vantaggi dell’aggiornamento ad AEM 6.5, consulta [Aggiornamento ad AEM 6.5](https://experienceleague.adobe.com/it/docs/experience-manager-65/content/implementing/deploying/upgrading/upgrade).

## Accedere a [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Accedi alla pagina di destinazione [!UICONTROL Experience Cloud] utilizzando le credenziali di Adobe Identity Management. Seleziona AEM dal commutatore della soluzione per accedere a [!UICONTROL Cloud Manager] e ai tuoi ambienti AEM.

Dopo aver effettuato la registrazione a [!UICONTROL Cloud Manager] per la prima volta, potrai accedere agli ambienti di AEM direttamente dall’interfaccia utente di [!UICONTROL Cloud Manager]. A questo punto, puoi utilizzare tutte le funzionalità di [!UICONTROL Cloud Manager] e preparare il tuo primo ramo di codice da distribuire negli ambienti di staging e produzione.

Per iniziare a utilizzare [!UICONTROL Cloud Manager], consulta [Primo accesso](/help/getting-started/first-time-login.md).

Per ulteriori informazioni su AEM, consulta [Distribuzione e manutenzione](https://experienceleague.adobe.com/it/docs/experience-manager-65/content/implementing/deploying/deploying/deploy).

## Guida introduttiva a [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Dopo aver effettuato l’accesso a [!UICONTROL Cloud Manager], puoi iniziare con il progetto AEM effettuando le operazioni seguenti:

1. Configurazione dell’ambiente dell’archivio del codice.
1. Configurazione del team e dei ruoli. L’iscrizione a un ruolo viene assegnata aggiungendo l’utente a un profilo di [!UICONTROL Cloud Manager] utilizzando Admin Console.
1. Configurazione dei rami del codice sorgente nell’archivio Git.
1. Definisci i KPI (Key Performance Indicators) di carico e prestazioni.
1. Definizione degli scenari di test per la corretta implementazione del codice negli ambienti di staging e di produzione una volta superati tutti i controlli di qualità.

## Panoramica del processo {#end-to-end-journey}

Il diagramma seguente riepiloga il processo durante l&#39;utilizzo della pipeline CI/CD [!UICONTROL Cloud Manager] per la distribuzione delle modifiche al codice negli ambienti di staging e produzione.

![percorso di clienti per l&#39;onboarding in Cloud Manager, che mostra il percorso per i clienti nuovi ed esistenti attraverso il provisioning o gli aggiornamenti dell&#39;ambiente, la gestione di utenti e ruoli, l&#39;implementazione del progetto e la pipeline CI/CD.](/help/assets/screen_shot_2018-05-15at124004pm.png)
