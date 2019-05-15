---
title: Note sulla versione 2018.6.0
seo-title: Note sulla versione di AEM Cloud Manager per 2018.6.0
description: ollow this page to get information for Cloud Manager Release 2018.6.0.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2018.6.0 di AEM Cloud Manager.
uuid: 211 b 6 e 1 b -10 fb -46 b 0-b 591-44 d 5 e 44 abd 77
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: note sulla versione
discoiquuid: 8584 f 467-3 e 61-41 ea -98 e 4-f 79 e 68 c 86469
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Note sulla versione 2018.6.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per [!UICONTROL Cloud Manager] la release 2018.6.0 e aggiunge il supporto per la convalida del dispatcher durante le distribuzioni, notifiche aggiuntive e miglioramenti della fruibilità.

## Data di rilascio {#release-date}

La Data di rilascio per [!UICONTROL Cloud Manager] la versione 2018.6.0 è il 9 agosto 2018.

## Novità {#what-s-new}

* **Pipeline CI/CD** - Annullamento del dispatcher configurabile e annullamento della cache sia sullo stage che sulla produzione durante l&#39;esecuzione della pipeline CI/CD. Per ulteriori informazioni, consulta [Configurare il tuo pipeline](configuring-pipeline.md) CI/CD.

* **Pipeline CI/CD** - Durante la configurazione della pipeline, è ora possibile definire il funzionamento della pipeline quando viene rilevato un errore importante in uno dei gate di qualità. Per ulteriori informazioni, consulta [Configurare il tuo pipeline](configuring-pipeline.md) CI/CD.

* **Pipeline CI/CD** - Durante la configurazione della pipeline, è ora possibile selezionare se il CSE o qualsiasi CSE disponibile deve essere eseguito da CSE. Per ulteriori informazioni, consulta [Configurare il tuo pipeline](configuring-pipeline.md) CI/CD.

* **Pipeline CI/CD** - Quando la pipeline CI/CD raggiunge il passaggio di approvazione aziendale, viene inviata una notifica agli utenti autorizzati a approvare la distribuzione. Per ulteriori informazioni, consulta [Notifiche](notifications.md) .

* **Pipeline CI/CD** - Quando il pipeline CI/CD raggiunge il set di pianificazione, viene inviata una notifica agli utenti autorizzati a impostare la pianificazione. Per ulteriori informazioni, consulta [Notifiche](notifications.md) .

* **Analisi di qualità del codice** - Nuove regole per identificare le richieste HTTP/HTTPS in uscita non corrette. Per ulteriori informazioni, consulta [Regole](custom-code-quality-rules.md) di qualità codice personalizzate.

## Correzioni di bug {#bug-fixes}

* In alcuni casi, il test delle prestazioni non era distribuito completamente tra più istanze di dispatcher e pubblicazione.
* La navigazione dell&#39;intestazione è scomparsa in finestre browser strette.
* Alcune impostazioni della pipeline non sono state disattivate durante l&#39;esecuzione della pipeline.
* I collegamenti alla schermata di elenco AEM e Monitoraggio dalla schermata di riepilogo hanno sostituito sia la scheda corrente del browser che l&#39;apertura di una nuova scheda.
* In alcune circostanze, un periodo di approvazione prolungato potrebbe dare luogo a una distribuzione non riuscita.
