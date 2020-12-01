---
title: Note sulla versione 2018.5.0
seo-title: Note sulla versione di AEM Cloud Manager per la versione 2018.5.0
description: Segui questa pagina per ottenere informazioni sulla versione 2018.5.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni su AEM Cloud Manager Release 2018.5.0.
uuid: 37f8b155-6984-454d-83a8-3f5fb081be97
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 6d1e7098-b56e-4172-8373-486f186f3d53
translation-type: tm+mt
source-git-commit: 15f75ca67c3d52ae511357c5b564daaa3d9def6b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Note sulla versione 2018.5.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per la versione [!UICONTROL Cloud Manager] 2018.5.0.

## Data di rilascio {#release-date}

La data di rilascio per la versione [!UICONTROL Cloud Manager] 2018.5.0 è il 12 luglio 2018.

## Novità {#what-s-new}

* **Notifiche**  pipeline CI/CD - Gli utenti visualizzeranno ora  [!UICONTROL Experience Cloud] le notifiche per gli eventi pipeline. Per ulteriori informazioni, fare riferimento alla sezione [Notifiche](notifications.md).

* **Distribuzioni**  produzione programmate: gli utenti possono ora pianificare una data o un&#39;ora per le distribuzioni di produzione. Per ulteriori informazioni, fare riferimento a [Distribuzione del codice](deploying-code.md).

* **Pagina** Statuspage restituita  **Attività**.

* Informazioni più specifiche visualizzate sulla pagina principale per i problemi riscontrati durante l&#39;esecuzione della pipeline.
* Miglioramenti all&#39;infrastruttura di test delle prestazioni.

## Correzioni di bug {#bug-fixes}

* In alcune condizioni, è stato utilizzato il profilo SonarQube errato, che ha portato a metriche di qualità del codice errate.
* SonarQube check CQBP-75 ignorava alcune annotazioni OSGi.
* Quando la pipeline CI/CD è stata annullata, lo stato non veniva visualizzato in modo coerente.

## Problemi noti {#known-issues}

* I collegamenti a **AEM** e **Monitoring** dalla schermata Elenco programmi sostituiscono la scheda del browser corrente e si aprono a una nuova scheda.

