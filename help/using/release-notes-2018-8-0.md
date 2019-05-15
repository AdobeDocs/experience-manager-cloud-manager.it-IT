---
title: Note sulla versione 2018.8.0
seo-title: Note sulla versione di AEM Cloud Manager per 2018.8.0
description: Segui questa pagina per ottenere informazioni sulla versione 2018.8.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2018.8.0 di AEM Cloud Manager.
uuid: e 8 aaba 32-89 b 4-4 bc 5-b 295-09 b 753252612
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: note sulla versione
discoiquuid: 9222 ac 3 b -525 e -47 c 1-b 481-ac 9 d 22 e 3 d 559
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Note sulla versione 2018.8.0 {#release-notes-for}

La [!UICONTROL Cloud Manager] versione 2018.8.0 aggiunge il supporto per l&#39;attivazione automatica della pipeline CI/CD su Git commits e una nuova procedura guidata per la creazione di progetti applicativi in base all&#39;archivio di progetti AEM.

## Data di rilascio {#release-date}

La Data di rilascio per [!UICONTROL Cloud Manager] la versione 2018.8.0 è il 04 ottobre 2018.

## Novità {#what-s-new}

* **Configurazione** programma - Nuova procedura guidata per creare un progetto applicazione in git utilizzando l&#39;archetype progetto AEM Per ulteriori informazioni, consultate [Creazione di un progetto](create-an-application-project.md) applicazione AEM.

* **Pipeline CI/CD** - Le seguenti modifiche vengono aggiunte alla pipeline CI/CD. Per ulteriori informazioni, consulta [Configurare il tuo pipeline](configuring-pipeline.md) CI/CD.

   * Sul trigger Git Changes, che avvia la pipeline CI/CD ogni volta che vengono aggiunti dei commenti al ramo git configurato.
   * Le schede sulla schermata iniziale ora contengono collegamenti profondi in sezioni specifiche della pagina di esecuzione della pipeline.
   * La pagina Attività ora elenca il ramo specifico utilizzato per ogni esecuzione.
   * La pagina Attività ora indica la durata in ore e minuti.
   * La pagina di esecuzione della pipeline ora mostra il nome di versione/tag creato per l&#39;esecuzione.
   * Apache Maven versione aggiornata a 3.5.3.

* **Navigazione** : le seguenti modifiche vengono aggiunte al [!UICONTROL Cloud Manager]gruppo.

   * Il collegamento Risorse nella navigazione globale consente di individuare il runbook in Sharepoint.
   * Il menu Aiuto è stato riorganizzato per includere contenuti più [!UICONTROL Cloud Manager]specifici.

## Correzioni di bug {#bug-fixes}

* Alcuni dettagli nella finestra di dialogo di verifica delle prestazioni non erano visibili in Firefox.
* Talvolta i timeout tra sistemi interni causano errori di distribuzione.
* Il colore dell&#39;icona nella pagina Attività non era corretto per alcune esecuzioni di pipeline completate.
* In alcuni casi, la finestra di dialogo di verifica delle prestazioni elenca più volte la stessa metrica.
* Se una nuova istanza è stata aggiunta dopo l&#39;avvio della pipeline CI/CD, la distribuzione non viene eseguita sulla nuova istanza creata.

## Problemi noti {#known-issues}

* I rami creati utilizzando la procedura guidata di creazione dei progetti non possono contenere trattini.
* La [!UICONTROL Experience Cloud] barra laterale notifica non può caricare le notifiche in modo coerente. Le notifiche, tuttavia, sono visibili nella [!UICONTROL Experience Cloud] e, se configurate, continueranno a essere inviate tramite e-mail.

