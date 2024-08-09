---
title: Note sulla versione 2024.7.0
description: Scopri le note sulla versione di Cloud Manager 2024.7.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 4%

---


# Note sulla versione per Cloud Manager 2024.7.0 {#release-notes}

In questa pagina sono documentate le note sulla versione di [!UICONTROL Cloud Manager] 2024.7.0.

>[!NOTE]
>
>Per le ultime note sulla versione di Cloud Manager in AEM as a Cloud Service, vedi [Cloud Manager nelle note sulla versione corrente di AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current).

## Data di rilascio {#release-date}

La data di rilascio per [!UICONTROL Cloud Manager] 2024.7.0 è il 18 luglio 2024. La prossima versione è pianificata per il 13 agosto 2024.

## Novità {#what-is-new}

* La [pipeline di produzione](/help/using/production-pipelines.md#adding-production-pipeline) e la [pipeline non di produzione](/help/using/non-production-pipelines.md#adding-non-production-pipeline) attivano **Modifiche Git** per avviare la pipeline in un commit è ora disponibile per [archivi privati](/help/managing-code/private-repositories.md).
* Una pipeline di pre-produzione può essere attivata solo manualmente e non può essere configurata come **In caso di modifiche Git**.
* Per le pipeline solo di produzione, l’elenco delle esecuzioni promozionali include le esecuzioni con una versione dell’artefatto maggiore della versione dell’artefatto distribuita nell’ambiente di produzione.
* [L&#39;archetipo del progetto AEM](https://experienceleague.adobe.com/it/docs/experience-manager-core-components/using/developing/archetype/overview) è stato aggiornato alla [versione 49](https://github.com/adobe/aem-project-archetype/tree/aem-project-archetype-49).

## Programma di adozione anticipata {#early-adoption}

Partecipa al programma di adozione anticipata di Cloud Manager e prova alcune delle prossime funzionalità

### Pipeline di sola staging e sola produzione {#staging-production-only-pipelines}

È stato introdotto il supporto per [pipeline di sola staging e di sola produzione](/help/using/stage-prod-only.md), che consente di suddividere le pipeline di distribuzione di produzione full stack in implementazioni più piccole e specializzate.

Se ti interessa testare questa nuova funzionalità e condividere i tuoi commenti, invia un&#39;e-mail a `Grp-cloudmanager_splitpipelines@adobe.com` dal tuo indirizzo e-mail associato al tuo Adobe ID.
