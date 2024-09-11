---
title: Percorso dell’utente
description: Scopri i diversi scenari di onboarding e come iniziare a utilizzare Cloud Manager.
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '532'
ht-degree: 100%

---


# Percorso dell’utente {#user-journey}

In qualità di utente di AEM (Adobe Experience Manager), probabilmente rientri in uno dei seguenti scenari:

* Non hai familiarità con AEM.
* Utilizzi attualmente AEM 6.x.
* Devi eseguire l’aggiornamento ad AEM 6.5 per utilizzare [!UICONTROL Cloud Manager].

Questo documento illustra questi tre scenari e spiega il percorso per iniziare a utilizzare [!UICONTROL Cloud Manager].

>[!NOTE]
>
>[!UICONTROL Cloud Manager] è disponibile solo per i clienti di Adobe Managed Services (AMS) che utilizzano AEM 6.4 o versioni successive.

## Onboarding {#onboarding}

Il processo di onboarding varia a seconda se si sta utilizzando AMS per la prima volta oppure si è un cliente AMS esistente.

### Utilizzo di Adobe Managed Services per la prima volta {#new-to-ams}

In qualità di nuovo utente, inizierai a utilizzare [!UICONTROL Cloud Manager] come parte del processo di onboarding in Adobe Managed Services.

Come parte del processo di onboarding, riceverai un’e-mail di benvenuto che include:

* L’URL per accedere a [!UICONTROL Cloud Manager].
* Le istruzioni per l’accesso a [!UICONTROL Experience Cloud].
* Le istruzioni per utilizzare Admin Console per la gestione degli utenti e delle relative autorizzazioni in modo che possano accedere a [!UICONTROL Cloud Manager] se necessario.

### Cliente attuale di Adobe Managed Services {#existing-customer}

In qualità di cliente AMS esistente, devi prima aggiornare gli ambienti di produzione e non di produzione esistenti alla versione AEM 6.4 o superiore.

Durante l’aggiornamento, riceverai l’URL per accedere a [!UICONTROL Cloud Manager] e potrai iniziare a utilizzarlo. Inoltre, dovrai iniziare a utilizzare Admin Console per gestire gli utenti che devono accedere a [!UICONTROL Cloud Manager] insieme alle relative autorizzazioni.

Anche un progetto AEM esistente dovrà essere conforme alle best practice consigliate, poiché inizierai a utilizzare [!UICONTROL Cloud Manager] per la distribuzione di nuove modifiche al codice negli ambienti AEM.

Per ulteriori informazioni sui vantaggi dell’aggiornamento ad AEM 6.5, consulta [Aggiornamento ad AEM 6.5](https://experienceleague.adobe.com/it/docs/experience-manager-65/content/implementing/deploying/upgrading/upgrade).

## Accedere a [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Accedi alla pagina di destinazione [!UICONTROL Experience Cloud] utilizzando le credenziali di Adobe Identity Management. Da qui, seleziona AEM dal selettore della soluzione per accedere a [!UICONTROL Cloud Manager] e agli ambienti AEM.

Dopo aver effettuato la registrazione a [!UICONTROL Cloud Manager] per la prima volta, potrai accedere agli ambienti di AEM direttamente dall’interfaccia utente di [!UICONTROL Cloud Manager]. A questo punto, è tutto pronto per esplorare tutte le opportunità di [!UICONTROL Cloud Manager] e preparare il tuo primo ramo di codice da distribuire negli ambienti di staging e produzione.

Per iniziare a utilizzare [!UICONTROL Cloud Manager], consulta [Primo accesso](/help/getting-started/first-time-login.md).

Per ulteriori informazioni su AEM, consulta [Distribuzione e manutenzione](https://experienceleague.adobe.com/it/docs/experience-manager-65/content/implementing/deploying/deploying/deploy).

## Guida introduttiva a [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Dopo aver effettuato l’accesso a [!UICONTROL Cloud Manager], puoi iniziare con il progetto AEM effettuando le operazioni seguenti:

1. Configurazione dell’ambiente dell’archivio del codice.
1. Configurazione del team e dei ruoli. Le appartenenze al ruolo vengono assegnate aggiungendo l’utente a un profilo di [!UICONTROL Cloud Manager] utilizzando Admin Console.
1. Configurazione dei rami del codice sorgente nell’archivio Git.
1. Definizione degli obiettivi in termini di carico e di prestazioni dei KPI (Indicatori di prestazioni chiave).
1. Definizione degli scenari di test per la corretta distribuzione del codice negli ambienti di staging e produzione dopo che tutti i controlli di qualità sono stati superati.

## Percorso end-to-end {#end-to-end-journey}

Questo diagramma illustra il percorso cliente ad alto livello durante l’utilizzo di una pipeline CI/CD di [!UICONTROL Cloud Manager] per la distribuzione delle modifiche al codice negli ambienti di staging e produzione.

![Percorso end-to-end](/help/assets/screen_shot_2018-05-15at124004pm.png)
