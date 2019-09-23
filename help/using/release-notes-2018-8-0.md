---
title: Note sulla versione 2018.8.0
seo-title: Note sulla versione di AEM Cloud Manager per la versione 2018.8.0
description: Segui questa pagina per ottenere informazioni sulla versione 2018.8.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2018.8.0 di AEM Cloud Manager.
uuid: e8aaba32-89b4-4bc5-b295-09b753252612
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: note sulla versione
discoiquuid: 9222ac3b-525e-47c1-b481-ac9d22e3d559
translation-type: tm+mt
source-git-commit: 15f75ca67c3d52ae511357c5b564daaa3d9def6b

---


# Note sulla versione 2018.8.0 {#release-notes-for}

La release [!UICONTROL Cloud Manager] 2018.8.0 aggiunge il supporto per attivare automaticamente la pipeline CI/CD quando si impegna git e una nuova procedura guidata per la creazione di progetti di applicazione in git basata su AEM Project Archetype.

## Data di rilascio {#release-date}

La data di rilascio per la [!UICONTROL Cloud Manager] versione 2018.8.0 è il 4 ottobre 2018.

## Novità {#what-s-new}

* **Impostazione** programma - Nuova procedura guidata per creare un progetto di applicazione in git utilizzando il tipo di archivio del progetto AEM. Per ulteriori informazioni, fare riferimento a [Creazione di un progetto](create-an-application-project.md) di applicazione AEM.

* **Pipeline** CI/CD - Le seguenti modifiche sono aggiunte alla tubazione CI/CD. Per ulteriori informazioni, consultare [Configurare la pipeline](configuring-pipeline.md) CI/CD.

   * In Modifiche Git viene attivato il ciclo di produzione CI/CD ogni volta che vengono aggiunti impegni al ramo git configurato.
   * Le schede nella schermata principale ora si collegano in sezioni specifiche della pagina di esecuzione della pipeline.
   * Nella pagina Activity (Attività) è ora riportato il ramo specifico utilizzato per ogni esecuzione.
   * La pagina Attività ora indica la durata in ore e minuti.
   * Nella pagina di esecuzione della pipeline viene ora visualizzato il nome della versione o del tag creato per l'esecuzione.
   * Versione Apache Maven aggiornata alla 3.5.3.

* **Navigazione** - Sono state aggiunte le seguenti modifiche alla [!UICONTROL Cloud Manager].

   * Il collegamento delle risorse nella navigazione globale passa al Runbook in Sharepoint.
   * Il menu Aiuto è stato riorganizzato per includere contenuto più [!UICONTROL Cloud Manager]specifico.

## Correzioni dei bug {#bug-fixes}

* Alcuni dettagli nella finestra di dialogo Verifica prestazioni non erano visibili in Firefox.
* I timeout tra i sistemi interni causerebbero occasionalmente errori di distribuzione.
* Il colore dell'icona nella pagina Attività non era corretto per alcune esecuzioni della pipeline riuscite.
* In alcuni casi, la finestra di dialogo Verifica prestazioni ha elencato più volte la stessa metrica.
* Se una nuova istanza è stata aggiunta dopo l’avvio della pipeline CI/CD, la distribuzione non verrà eseguita nell’istanza appena creata.

## Problemi noti {#known-issues}

* I rami creati con la Creazione guidata progetto applicazione non possono contenere trattini.
* La barra laterale delle [!UICONTROL Experience Cloud] notifiche potrebbe non caricare le notifiche in modo coerente. Le notifiche, tuttavia, sono visibili nel [!UICONTROL Experience Cloud] file e, se configurate, vengono comunque inviate tramite e-mail.

