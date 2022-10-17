---
title: Percorso dell’utente
description: Questo documento illustra i diversi scenari di onboarding e spiega il tuo percorso per iniziare a utilizzare Cloud Manager.
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: b0dbb602253939464ff034941ffbad84b7df77df
workflow-type: ht
source-wordcount: '504'
ht-degree: 100%

---


# Percorso dell’utente {#user-journey}

In qualità di utente di Adobe Experience Manager, puoi:

* Utilizzare AEM per la prima volta.
* Utilizzare attualmente AEM 6.x.
* Avere la necessità di eseguire l’aggiornamento a AEM versione 6.5 per utilizzare [!UICONTROL Cloud Manager].

Questo documento illustra questi scenari e spiega il tuo percorso per iniziare a utilizzare [!UICONTROL Cloud Manager].

>[!NOTE]
>
>[!UICONTROL Cloud Manager] è disponibile solo per i clienti di Adobe Managed Services (AMS) che utilizzano AEM 6.4 o versioni successive.

## Onboarding {#onboarding}

Il processo di onboarding varia a seconda se si sta utilizzando AMS per la prima volta oppure si è un cliente AMS esistente.

### Utilizzo di Adobe Managed Services per la prima volta {#new-to-ams}

In qualità di nuovo cliente, inizierai a utilizzare [!UICONTROL Cloud Manager] come parte del processo di onboarding in Adobe Managed Services.

Come parte del processo di onboarding, riceverai un’e-mail di benvenuto che include:

* L’URL di accesso [!UICONTROL Cloud Manager]
* Le istruzioni per l’accesso a [!UICONTROL Experience Cloud]
* Le istruzioni per utilizzare l’Admin Console per la gestione degli utenti e delle relative autorizzazioni in modo che possano accedere [!UICONTROL Cloud Manager] se necessario.

### Cliente esistente di Adobe Managed Services {#existing-customer}

In qualità di cliente AMS esistente, dovrai prima aggiornare gli ambienti di produzione e non di produzione esistenti a AEM 6.4 o versione superiore.

Durante l’aggiornamento, potrai iniziare a utilizzare Cloud Manager e riceverai l’URL per accedervi [!UICONTROL Cloud Manager]. Inoltre, dovrai iniziare a utilizzare l’Admin Console per gestire gli utenti che devono accedere a [!UICONTROL Cloud Manager] insieme alle relative autorizzazioni.

Anche un progetto AEM esistente dovrà essere conforme alle best practice consigliate, poiché inizierai a utilizzare [!UICONTROL Cloud Manager] per la distribuzione di nuove modifiche al codice negli ambienti AEM.

Per ulteriori informazioni sui vantaggi dell’aggiornamento a AEM 6.5, consulta il documento [Aggiornamento a AEM 6.5.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/upgrade.html?lang=it)

## Accesso [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Effettuerai l’accesso a [!UICONTROL Cloud Manager] e agli ambienti AEM semplicemente registrandoti nella pagina di destinazione di [!UICONTROL Experience Cloud] utilizzando le credenziali di Adobe Identity Management e selezionando AEM dall’interfaccia del selettore della soluzione.

Dopo esserti registrato in [!UICONTROL Cloud Manager] per la prima volta, potrai accedere agli ambienti di AEM direttamente dall&#39; interfaccia utente di [!UICONTROL Cloud Manager]. A questo punto, sei pronto per esplorare tutte le opportunità di [!UICONTROL Cloud Manager] e preparare il tuo primo ramo di codice da distribuire negli ambienti di staging e produzione.

Per iniziare a utilizzare [!UICONTROL Cloud Manager], consulta il documento [Primo accesso](/help/getting-started/first-time-login.md).

Per ulteriori informazioni su AEM, consulta il documento [Distribuzione e manutenzione.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html?lang=it)

## Guida introduttiva a [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Dopo aver effettuato l’accesso a [!UICONTROL Cloud Manager] puoi iniziare a utilizzare il progetto AEM:

1. Configurando l’ambiente dell&#39;archivio del codice.
1. Configurando il team e i ruoli.
   * Le appartenenze al ruolo vengono assegnate aggiungendo l’utente a un profilo di [!UICONTROL Cloud Manager] utilizzando l’Admin Console.
1. Configurando i rami del codice sorgente nell’archivio Git.
1. Definendo gli obiettivi in termini di prestazioni e di carico dei KPI.
1. Definendo gli scenari di test per la corretta distribuzione del codice negli ambienti di staging e produzione dopo che tutti i controlli di qualità sono stati superati.

## Percorso end-to-end {#end-to-end-journey}

Questo diagramma illustra il percorso del cliente ad alto livello quando si utilizza una pipeline CI/CD di [!UICONTROL Cloud Manager] per la distribuzione delle modifiche al codice negli ambienti di staging e produzione.

![Percorso end-to-end](/help/assets/screen_shot_2018-05-15at124004pm.png)
