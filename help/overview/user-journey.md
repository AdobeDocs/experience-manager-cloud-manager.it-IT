---
title: Percorso utente
description: Questo documento illustra i diversi scenari di onboarding e spiega il tuo percorso guida introduttiva con Cloud Manager.
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: b0dbb602253939464ff034941ffbad84b7df77df
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 0%

---


# Percorso utente {#user-journey}

In qualità di utente di Adobe Experience Manager, puoi:

* Siate nuovi a AEM.
* Stai attualmente utilizzando AEM 6.x.
* È necessario eseguire l’aggiornamento a AEM versione 6.5 per utilizzare [!UICONTROL Cloud Manager].

Questo documento illustra questi scenari e spiega il tuo percorso per iniziare a utilizzare [!UICONTROL Cloud Manager].

>[!NOTE]
>
>[!UICONTROL Cloud Manager] è disponibile solo per i clienti di Adobe Managed Services (AMS) che utilizzano AEM 6.4 o versioni successive.

## Onboarding {#onboarding}

Il processo di onboarding varia a seconda che si tratti di un cliente AMS nuovo o esistente.

### Novità di Adobe Managed Services {#new-to-ams}

In qualità di nuovo cliente, effettuerai l’onboarding in [!UICONTROL Cloud Manager] come parte del processo di onboarding in Adobe Managed Services.

Come parte del processo di onboarding, riceverai un’e-mail di benvenuto che include:

* URL a cui accedere [!UICONTROL Cloud Manager]
* Istruzioni per l’accesso a [!UICONTROL Experience Cloud]
* Istruzioni per utilizzare l’Admin Console per la gestione degli utenti e delle relative autorizzazioni in modo che possano accedere [!UICONTROL Cloud Manager] se necessario.

### Cliente Adobe Managed Services esistente {#existing-customer}

In qualità di cliente AMS esistente, dovrai prima aggiornare gli ambienti di produzione e non di produzione esistenti a AEM 6.4 o superiore.

Durante l’aggiornamento, accederai a Cloud Manager e riceverai l’URL per accedervi [!UICONTROL Cloud Manager]. Inoltre, per gli utenti che devono accedere a [!UICONTROL Cloud Manager], dovrai iniziare a utilizzare l’Admin Console per gestirli e le relative autorizzazioni.

Anche il progetto AEM esistente dovrà conformarsi alle best practice consigliate, poiché inizierà a utilizzare [!UICONTROL Cloud Manager] per la distribuzione di nuove modifiche al codice negli ambienti AEM.

Per ulteriori informazioni sui vantaggi dell&#39;aggiornamento a AEM 6.5, consulta il documento [Aggiornamento a AEM 6.5.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/upgrade.html)

## Accesso [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Accesso a [!UICONTROL Cloud Manager] e i tuoi ambienti AEM semplicemente accedendo al [!UICONTROL Experience Cloud] pagina di destinazione utilizzando le credenziali Identity Management di Adobe e selezionando AEM dall’interfaccia del commutatore della soluzione.

Dopo l&#39;accesso [!UICONTROL Cloud Manager] per la prima volta, potrai accedere agli ambienti di AEM direttamente dal [!UICONTROL Cloud Manager] Interfaccia utente. A questo punto, sei pronto ad esplorare tutte le possibilità di [!UICONTROL Cloud Manager] e prepara il tuo primo ramo di codice da distribuire negli ambienti di stage e produzione.

Per iniziare a utilizzare [!UICONTROL Cloud Manager], vedere il documento [Primo accesso](/help/getting-started/first-time-login.md).

Per ulteriori informazioni su AEM, consulta il documento [Distribuzione e manutenzione.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html)

## Guida introduttiva [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Dopo aver effettuato l’accesso a [!UICONTROL Cloud Manager] per iniziare a utilizzare il progetto AEM:

1. Configurazione dell&#39;ambiente dell&#39;archivio del codice.
1. Configurazione del team e dei ruoli.
   * Le appartenenze al ruolo vengono assegnate aggiungendo l’utente a un [!UICONTROL Cloud Manager] utilizzando l’Admin Console .
1. Impostazione dei rami del codice sorgente nell’archivio Git.
1. Definizione degli obiettivi in termini di prestazioni e di carico KPI.
1. Definizione degli scenari di test per la corretta distribuzione del codice nell’area di visualizzazione e negli ambienti di produzione dopo che tutti i controlli di qualità sono stati superati.

## Percorso end-to-end {#end-to-end-journey}

Questo diagramma illustra il percorso dei clienti ad alto livello quando si utilizza [!UICONTROL Cloud Manager] pipeline CI/CD per la distribuzione delle modifiche al codice negli ambienti di staging e produzione.

![Percorso end-to-end](/help/assets/screen_shot_2018-05-15at124004pm.png)
