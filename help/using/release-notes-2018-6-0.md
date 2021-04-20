---
title: Note sulla versione 2018.6.0
seo-title: Note sulla versione di AEM Cloud Manager 2018.6.0
description: Segui questa pagina per ottenere informazioni sulla versione 2018.6.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2018.6.0 di AEM Cloud Manager.
uuid: 211b6e1b-10fb-46b0-b591-44d5e44abd77
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 8584f467-3e61-41ea-98e4-f79e68c86469
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 4%

---


# Note sulla versione 2018.6.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per [!UICONTROL Cloud Manager] la versione 2018.6.0 e aggiunge il supporto per l’invalidazione del dispatcher durante le distribuzioni, notifiche aggiuntive e miglioramenti a livello di usabilità.

## Data di rilascio {#release-date}

La data di rilascio per la versione 2018.6.0 di [!UICONTROL Cloud Manager] è il 9 agosto 2018.

## Novità {#what-s-new}

* **Pipeline CI/CD**  - Annullamento della validità del dispatcher configurabile e scaricamento della cache sia sullo stage che sulla produzione durante l’esecuzione della pipeline CI/CD. Per ulteriori informazioni, consulta [Configurare la pipeline CI/CD](configuring-pipeline.md) .

* **Pipeline CI/CD** : durante la configurazione della pipeline è ora possibile definire il comportamento della pipeline quando si verifica un errore importante in uno dei gate di qualità. Per ulteriori informazioni, consulta [Configurare la pipeline CI/CD](configuring-pipeline.md) .

* **Pipeline CI/CD** : durante la configurazione della pipeline è ora possibile selezionare se si desidera che la CSE Oversight venga eseguita dal CSE o da un CSE disponibile. Per ulteriori informazioni, consulta [Configurare la pipeline CI/CD](configuring-pipeline.md) .

* **Pipeline CI/CD** : quando la pipeline CI/CD raggiunge la fase di approvazione aziendale, viene inviata una notifica agli utenti autorizzati ad approvare la distribuzione. Per ulteriori informazioni, consulta [Notifiche](notifications.md) .

* **Pipeline CI/CD** : quando la pipeline CI/CD raggiunge il set di pianificazione, viene inviata una notifica agli utenti autorizzati a impostare la pianificazione. Per ulteriori informazioni, consulta [Notifiche](notifications.md) .

* **Analisi della qualità del codice**  - Nuove regole per identificare le richieste HTTP/HTTPS in uscita configurate in modo errato. Per ulteriori informazioni, consulta [Regole per la qualità del codice personalizzato](custom-code-quality-rules.md) .

## Correzioni di bug {#bug-fixes}

* In alcuni casi, il test delle prestazioni non era completamente distribuito tra più istanze del dispatcher e di pubblicazione.
* La navigazione delle intestazioni è scomparsa nelle finestre del browser strette.
* Alcune impostazioni della pipeline non sono state disabilitate durante l’esecuzione della pipeline.
* I collegamenti alle AEM e al monitoraggio dalla schermata dell’elenco dei programmi hanno sostituito la scheda del browser corrente e hanno aperto una nuova scheda.
* In alcune circostanze, un periodo di approvazione a lungo termine potrebbe causare un errore di distribuzione.
