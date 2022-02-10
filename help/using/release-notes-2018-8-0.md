---
title: Note sulla versione 2018.8.0
seo-title: AEM Cloud Manager Release Notes for 2018.8.0
description: Segui questa pagina per ottenere informazioni sulla versione 2018.8.0 di Cloud Manager.
seo-description: Follow this page to get information for AEM Cloud Manager Release 2018.8.0.
uuid: e8aaba32-89b4-4bc5-b295-09b753252612
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 9222ac3b-525e-47c1-b481-ac9d22e3d559
feature: Release Information
exl-id: 20f87048-30f7-4869-aad0-13ca383a404b
source-git-commit: 4f0e1d163001fd18cfa838256c813152d65c3b4c
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 4%

---

# Note sulla versione 2018.8.0 {#release-notes-for}

La [!UICONTROL Cloud Manager] Con la versione 2018.8.0 è stato aggiunto il supporto per l’attivazione automatica della pipeline CI/CD con commit git e una nuova procedura guidata per la creazione di progetti di applicazione in git in base al tipo di progetto AEM.

## Data di pubblicazione {#release-date}

Data di rilascio per [!UICONTROL Cloud Manager] La versione 2018.8.0 è il 4 ottobre 2018.

## Novità {#what-s-new}

* **Configurazione del programma** - Nuova procedura guidata per creare un progetto di applicazione in git utilizzando AEM Project Archetype

* **Pipeline CI/CD** - Le seguenti modifiche vengono aggiunte alla pipeline CI/CD. Fare riferimento al documento [Configurare le pipeline di produzione](configuring-production-pipelines.md) per saperne di più.

   * All’attivazione delle modifiche Git viene avviata la pipeline CI/CD ogni volta che vengono aggiunti dei commit al ramo Git configurato.
   * Le schede nella schermata principale ora sono collegate in profondità a sezioni specifiche della pagina di esecuzione della pipeline.
   * Nella pagina Attività è ora elencato il ramo specifico utilizzato per ogni esecuzione.
   * La pagina Attività ora indica la durata in ore e minuti.
   * Nella pagina di esecuzione della pipeline viene ora visualizzato il nome di versione/tag creato per l’esecuzione.
   * Aggiornamento della versione Apache Maven a 3.5.3.

* **Navigazione** - Le seguenti modifiche vengono aggiunte al [!UICONTROL Cloud Manager].

   * Il collegamento Risorse nella navigazione globale consente di accedere al Runbook in Sharepoint.
   * Il menu Aiuto è stato riorganizzato per includere ulteriori informazioni [!UICONTROL Cloud Manager]Contenuto specifico.

## Correzioni di bug {#bug-fixes}

* Alcuni dettagli nella finestra di dialogo Verifica prestazioni non erano visibili in Firefox.
* I timeout tra sistemi interni causano occasionalmente la segnalazione di errori di distribuzione.
* Il colore dell’icona nella pagina Attività non era corretto per alcune esecuzioni della pipeline riuscite.
* In alcuni casi, la finestra di dialogo Verifica prestazioni ha elencato la stessa metrica più volte.
* Se una nuova istanza è stata aggiunta dopo l’avvio della pipeline CI/CD, la distribuzione non verrà eseguita sull’istanza appena creata.

## Problemi noti {#known-issues}

* I rami creati con Creazione guidata progetto applicazione non possono contenere trattini.
* La [!UICONTROL Experience Cloud] la barra laterale di notifica potrebbe non caricare le notifiche in modo coerente. Le notifiche, tuttavia, sono visibili nel [!UICONTROL Experience Cloud] e, se configurato, verrà comunque inviato tramite e-mail.
