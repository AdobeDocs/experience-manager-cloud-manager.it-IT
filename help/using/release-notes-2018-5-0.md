---
title: Note sulla versione 2018.5.0
seo-title: Note sulla versione di AEM Cloud Manager per la versione 2018.5.0
description: Segui questa pagina per ottenere informazioni sulla versione 2018.5.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2018.5.0 di AEM Cloud Manager.
uuid: 37f8b155-6984-454d-83a8-3f5fb081be97
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: note sulla versione
discoiquuid: 6d1e7098-b56e-4172-8373-486f186f3d53
translation-type: tm+mt
source-git-commit: 15f75ca67c3d52ae511357c5b564daaa3d9def6b

---


# Note sulla versione 2018.5.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per la [!UICONTROL Cloud Manager] release 2018.5.0.

## Data di rilascio {#release-date}

La data di rilascio per la [!UICONTROL Cloud Manager] versione 2018.5.0 è il 12 luglio 2018.

## Novità {#what-s-new}

* **Notifiche** pipeline CI/CD - Gli utenti visualizzeranno ora [!UICONTROL Experience Cloud] le notifiche per gli eventi pipeline. Per ulteriori informazioni, consulta [Notifiche](notifications.md) .

* **Distribuzioni** produzione programmate: gli utenti ora possono pianificare una data o un'ora per le distribuzioni di produzione. Per ulteriori informazioni, fai riferimento a [Distribuzione del codice](deploying-code.md) .

* **La pagina Stato** ritorna ad **Attività**.

* Informazioni più specifiche visualizzate sulla pagina principale per i problemi riscontrati durante l'esecuzione della pipeline.
* Miglioramenti all'infrastruttura di test delle prestazioni.

## Correzioni dei bug {#bug-fixes}

* In alcune condizioni, è stato utilizzato il profilo SonarQube errato, che ha portato a metriche di qualità del codice errate.
* SonarQube check CQBP-75 ignorava alcune annotazioni OSGi.
* Quando la pipeline CI/CD è stata annullata, lo stato non veniva visualizzato in modo coerente.

## Problemi noti {#known-issues}

* I collegamenti ad **AEM** e al **monitoraggio** dalla schermata Elenco programmi sostituiscono la scheda corrente del browser e si aprono a una nuova scheda.

