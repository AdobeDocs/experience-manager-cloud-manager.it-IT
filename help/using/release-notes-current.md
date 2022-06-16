---
title: Note sulla versione 2022.6.0
description: Queste sono le note sulla versione per la versione 2022.6.0 di Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: dab08a2499b521b7026ab2bd17b82cb241f26fb6
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 3%

---


# Note sulla versione per Cloud Manager versione 2022.6.0 {#release-notes}

Questa pagina documenta le note sulla versione per [!UICONTROL Cloud Manager] versione 2022.6.0.

>[!NOTE]
>
>Per le ultime note sulla versione di Cloud Manager in AEM as a Cloud Service, fai riferimento a [Cloud Manager nelle note sulla versione corrente di AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Data di pubblicazione {#release-date}

La data di rilascio per [!UICONTROL Cloud Manager] la versione 2022.6.0 è il 9 giugno 2022. La prossima versione è prevista per il 30 giugno 2022.

## Novità {#what-is-new}

* Una nuova scheda di benvenuto nella pagina di destinazione di Cloud Manager consente agli utenti di accedere rapidamente alle esercitazioni di onboarding e alle metriche di avanzamento correlate al tenant.
   * Questa funzione verrà implementata in un approccio graduale durante la settimana successiva alla versione 2022.06.0.
* [È ora possibile riutilizzare gli artefatti di creazione](/help/using/setting-up-project.md#build-artifact-reuse) quando si utilizza il mirroring git.

## Modifiche API {#api-changes}

* La [`List Programs`](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getPrograms) L’API è stata dichiarata obsoleta e [`List Programs for Tenant`](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getProgramsForTenant) Deve essere invece utilizzato.
   * `List Programs` continua a funzionare, ma il suo utilizzo genererà messaggi di avviso nei registri.
   * Non sarà più supportato dopo tre mesi.
