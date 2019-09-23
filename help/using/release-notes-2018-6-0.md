---
title: Note sulla versione 2018.6.0
seo-title: Note sulla versione di AEM Cloud Manager per la versione 2018.6.0
description: Segui questa pagina per ottenere informazioni sulla versione 2018.6.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2018.6.0 di AEM Cloud Manager.
uuid: 211b6e1b-10fb-46b0-b591-44d5e44abd77
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: note sulla versione
discoiquuid: 8584f467-3e61-41ea-98e4-f79e68c86469
translation-type: tm+mt
source-git-commit: 15f75ca67c3d52ae511357c5b564daaa3d9def6b

---


# Note sulla versione 2018.6.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per la [!UICONTROL Cloud Manager] release 2018.6.0 e aggiunge il supporto per l’annullamento della validità del dispatcher durante le distribuzioni, notifiche aggiuntive e miglioramenti all’usabilità.

## Data di rilascio {#release-date}

La data di rilascio per la [!UICONTROL Cloud Manager] versione 2018.6.0 è il 9 agosto 2018.

## Novità {#what-s-new}

* **Pipeline** CI/CD - Annullamento configurazione del dispatcher e scaricamento della cache sia sullo stage che sulla produzione durante l'esecuzione della tubazione CI/CD. Per ulteriori informazioni, consultare [Configurare la pipeline](configuring-pipeline.md) CI/CD.

* **Pipeline** CI/CD - Durante l'impostazione della tubazione, è ora possibile definire il funzionamento della tubazione quando si verifica un errore importante in una delle porte di qualità. Per ulteriori informazioni, consultare [Configurare la pipeline](configuring-pipeline.md) CI/CD.

* **Pipeline** CI/CD - Durante la configurazione della tubazione, è ora possibile scegliere se eseguire CSE Oversight da parte del CSE o di eventuali CSE disponibili. Per ulteriori informazioni, consultare [Configurare la pipeline](configuring-pipeline.md) CI/CD.

* **Pipeline** CI/CD - Quando la pipeline CI/CD raggiunge la fase di approvazione aziendale, verrà inviata una notifica agli utenti autorizzati ad approvare la distribuzione. Per ulteriori informazioni, consulta [Notifiche](notifications.md) .

* **Pipeline** CI/CD - Quando la pipeline CI/CD raggiunge il set di programmi, verrà inviata una notifica agli utenti autorizzati a impostare il programma. Per ulteriori informazioni, consulta [Notifiche](notifications.md) .

* **Analisi** della qualità del codice - Nuove regole per identificare le richieste HTTP/HTTPS in uscita configurate in modo non corretto. Per ulteriori informazioni, fare riferimento a Regole [di qualità del codice](custom-code-quality-rules.md) personalizzate.

## Correzioni dei bug {#bug-fixes}

* In alcuni casi, il test delle prestazioni non è stato distribuito completamente tra più istanze del dispatcher e della pubblicazione.
* La navigazione dell'intestazione è scomparsa nelle finestre del browser strette.
* Alcune impostazioni della pipeline non sono state disattivate durante l'esecuzione della pipeline.
* I collegamenti ad AEM e al monitoraggio dalla schermata dell'elenco Programmi hanno sostituito la scheda corrente del browser e aperto una nuova scheda.
* In alcune circostanze, un periodo di approvazione prolungato potrebbe causare un errore di distribuzione.
