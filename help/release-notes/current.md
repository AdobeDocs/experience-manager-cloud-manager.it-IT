---
title: Note sulla versione 2023.9.0
description: Queste sono le note sulla versione 2023.9.0 di Cloud Manager.
feature: Release Information
source-git-commit: a3e926fa13d54da1322f3a5219519fae07ddb273
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 52%

---


# Note sulla versione 2023.9.0 di Cloud Manager {#release-notes}

In questa pagina sono documentate le note sulla versione 2023.9.0 di [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Per le ultime note sulla versione di Cloud Manager in AEM as a Cloud Service, fai riferimento a [Cloud Manager nelle note sulla versione corrente di AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=it)

## Data di pubblicazione {#release-date}

La data di pubblicazione della versione 2023.9.0 di [!UICONTROL Cloud Manager] è l’14 settembre 2023. La prossima versione è prevista per il 5 ottobre 2023.

## Novità {#what-is-new}

* Questa versione include correzioni di bug solo per Cloud Manager.

## Correzioni di bug {#bug-fixes}

* Quando un programma viene eliminato, viene eliminata anche qualsiasi pipeline in esecuzione associata, garantendo che la pipeline non venga erroneamente designata come stato di errore.
* Talvolta, quando tutti i passaggi di un’esecuzione della pipeline sono &quot;completati&quot;, lo stato della pipeline viene visualizzato come &quot;in esecuzione&quot;, facendola sembrare in uno stato bloccato. Ora viene visualizzato come &#39;Completo&#39;.
* Per i rami dell’archivio generati utilizzando l’archetipo del generatore di codice, la pipeline CI/CD non riesce.
