---
title: Note sulla versione 2018.8.0
seo-title: Note sulla versione di AEM Cloud Manager 2018.8.0
description: Segui questa pagina per ottenere informazioni sulla versione 2018.8.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2018.8.0 di AEM Cloud Manager.
uuid: e8aaba32-89b4-4bc5-b295-09b753252612
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 9222ac3b-525e-47c1-b481-ac9d22e3d559
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 4%

---


# Note sulla versione 2018.8.0 {#release-notes-for}

Il rilascio di [!UICONTROL Cloud Manager] 2018.8.0 aggiunge il supporto per l’attivazione automatica della pipeline CI/CD con commit git e una nuova procedura guidata per la creazione di progetti di applicazione in git in base al tipo di progetto AEM.

## Data di rilascio {#release-date}

La data di rilascio di [!UICONTROL Cloud Manager] versione 2018.8.0 è il 4 ottobre 2018.

## Novità {#what-s-new}

* **Configurazione del programma**  - Nuova procedura guidata per creare un progetto di applicazione in git utilizzando AEM Project Archetype

* **Pipeline CI/CD**  - Le seguenti modifiche vengono aggiunte alla pipeline CI/CD. Per ulteriori informazioni, consulta [Configurare la pipeline CI/CD](configuring-pipeline.md) .

   * All’attivazione delle modifiche Git viene avviata la pipeline CI/CD ogni volta che vengono aggiunti dei commit al ramo Git configurato.
   * Le schede nella schermata principale ora sono collegate in profondità a sezioni specifiche della pagina di esecuzione della pipeline.
   * Nella pagina Attività è ora elencato il ramo specifico utilizzato per ogni esecuzione.
   * La pagina Attività ora indica la durata in ore e minuti.
   * Nella pagina di esecuzione della pipeline viene ora visualizzato il nome di versione/tag creato per l’esecuzione.
   * Aggiornamento della versione Apache Maven a 3.5.3.

* **Navigazione** : le seguenti modifiche vengono aggiunte al  [!UICONTROL Cloud Manager].

   * Il collegamento Risorse nella navigazione globale consente di accedere al Runbook in Sharepoint.
   * Il menu Aiuto è stato riorganizzato in modo da includere contenuti più [!UICONTROL Cloud Manager] specifici.

## Correzioni di bug {#bug-fixes}

* Alcuni dettagli nella finestra di dialogo Verifica prestazioni non erano visibili in Firefox.
* I timeout tra sistemi interni causano occasionalmente la segnalazione di errori di distribuzione.
* Il colore dell’icona nella pagina Attività non era corretto per alcune esecuzioni della pipeline riuscite.
* In alcuni casi, la finestra di dialogo Verifica prestazioni ha elencato la stessa metrica più volte.
* Se una nuova istanza è stata aggiunta dopo l’avvio della pipeline CI/CD, la distribuzione non verrà eseguita sull’istanza appena creata.

## Problemi noti {#known-issues}

* I rami creati con Creazione guidata progetto applicazione non possono contenere trattini.
* La barra laterale delle notifiche [!UICONTROL Experience Cloud] potrebbe non caricare le notifiche in modo coerente. Le notifiche, tuttavia, sono visibili in [!UICONTROL Experience Cloud] e, se configurate, saranno comunque inviate tramite e-mail.

