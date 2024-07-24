---
title: Note sulla versione 2024.7.0
description: Queste sono le note sulla versione 2024.7.0 di Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 87c603a89b99f6984828280cba2041da8c72e839
workflow-type: ht
source-wordcount: '238'
ht-degree: 100%

---


# Note sulla versione 2024.7.0 di Cloud Manager {#release-notes}

In questa pagina sono documentate le note sulla versione 2024.7.0 di [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Per le ultime note sulla versione di Cloud Manager in AEM as a Cloud Service, fai riferimento a [Cloud Manager nelle note sulla versione corrente di AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=it)

## Data di pubblicazione {#release-date}

La data di pubblicazione di [!UICONTROL Cloud Manager] versione 2024.7.0 è il 18 luglio 2024. La prossima versione è prevista per l’8 agosto 2024.

## Novità {#what-is-new}

* Il trigger di [pipeline di produzione](/help/using/production-pipelines.md#adding-production-pipeline) e [pipeline non di produzione](/help/using/non-production-pipelines.md#adding-non-production-pipeline) **Cambiamenti su Git** per avviare la pipeline in un commit è ora disponibile per gli [archivi privati.](/help/managing-code/private-repositories.md)
* Una pipeline di pre-produzione può essere attivata solo manualmente e non può essere configurata come **Cambiamenti su Git**.
* Per le pipeline solo di produzione, l’elenco delle esecuzioni promozionali include quelle con una versione dell’artefatto superiore alla versione dell’artefatto distribuita nell’ambiente di produzione.
* [L’Archetipo progetto AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=it) è stato aggiornato alla [versione 49.](https://github.com/adobe/aem-project-archetype/tree/aem-project-archetype-49)


## Programma per i primi utilizzatori {#early-adoption}

Partecipa al nostro programma per i primi utilizzatori e concediti la possibilità di testare alcune delle prossime funzionalità

### Pipeline solo di staging e solo di produzione {#staging-production-only-pipelines}

È stato introdotto il supporto per le [pipeline solo di staging e solo di produzione](/help/using/stage-prod-only.md), che consente di suddividere le pipeline di distribuzione di produzione full stack in distribuzioni più piccole e specializzate.

Se ti interessa testare questa nuova funzionalità e condividere il feedback, invia un’e-mail a `Grp-cloudmanager_splitpipelines@adobe.com` dall’indirizzo e-mail associato all’Adobe ID.
