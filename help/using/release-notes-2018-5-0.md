---
title: Note sulla versione 2018.5.0
seo-title: Note sulla versione di AEM Cloud Manager 2018.5.0
description: Segui questa pagina per ottenere informazioni sulla versione 2018.5.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2018.5.0 di AEM Cloud Manager.
uuid: 37f8b155-6984-454d-83a8-3f5fb081be97
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 6d1e7098-b56e-4172-8373-486f186f3d53
feature: Release Information
translation-type: tm+mt
source-git-commit: c5d32d49782c899d013fcc60b9c4d2b67e9350ae
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 8%

---


# Note sulla versione 2018.5.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per [!UICONTROL Cloud Manager] la versione 2018.5.0.

## Data di rilascio {#release-date}

La data di rilascio di [!UICONTROL Cloud Manager] versione 2018.5.0 è il 12 luglio 2018.

## Novità {#what-s-new}

* **Notifiche di pipeline CI/CD**  - Gli utenti visualizzano ora  [!UICONTROL Experience Cloud] le notifiche per gli eventi di pipeline. Per ulteriori informazioni, consulta le [Notifiche](notifications.md) .

* **Implementazioni di produzione pianificate** : gli utenti possono ora pianificare una data o un’ora per le distribuzioni di produzione. Per ulteriori informazioni, fai riferimento a [Implementa il codice](deploying-code.md) .

* **** La pagina di stato ritorna ad  **Attività**.

* Informazioni più specifiche visualizzate nella home page dei problemi rilevati durante l’esecuzione della pipeline.
* Miglioramenti dell&#39;infrastruttura per il test delle prestazioni.

## Correzioni di bug {#bug-fixes}

* In alcune condizioni, è stato utilizzato il profilo SonarQube errato, dando luogo a metriche di qualità del codice errate.
* SonarQube check CQBP-75 ha ignorato alcune annotazioni OSGi.
* Quando la pipeline CI/CD è stata annullata, lo stato non veniva visualizzato in modo coerente.

## Problemi noti {#known-issues}

* I collegamenti a **AEM** e **Monitoraggio** dalla schermata Elenco programmi sostituiscono la scheda del browser corrente e si aprono a una nuova scheda.

