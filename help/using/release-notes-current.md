---
title: Note sulla versione 2022.3.0
description: Queste sono le note sulla versione per la versione 2022.3.0 di Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 0d14adda454889eebbb0a875978ceeaa5ee4f7ea
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 4%

---


# Note sulla versione per Cloud Manager versione 2022.3.0 {#release-notes}

Questa pagina documenta le note sulla versione per [!UICONTROL Cloud Manager] versione 2022.3.0.

>[!NOTE]
>
>Per le ultime note sulla versione di Cloud Manager in AEM as a Cloud Service, fai riferimento a [Cloud Manager nelle note sulla versione corrente di AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Data di pubblicazione {#release-date}

La data di rilascio per [!UICONTROL Cloud Manager] la versione 2022.3.0 è il 10 marzo 2022. La prossima versione è prevista per il 7 aprile 2022.

## Novità {#what-is-new}

* Solo per il Cloud Service: per accedere al registro dell’ambiente di AEM è possibile utilizzare il ruolo Sviluppatore .
* La [`reliability_rating` metrica critica](understand-your-test-results.md) è stato disattivato.


## Correzioni di bug {#bug-fixes}

* [La **Ignora modifiche di Load Balancer** opzione](configuring-production-pipelines.md#adding-production-pipeline) ora può essere disabilitato correttamente.
* [La **Ignora modifiche di Load Balancer** opzione](configuring-production-pipelines.md#adding-production-pipeline) viene ora visualizzato per il flusso di lavoro della pipeline di distribuzione di modifica.
* Un sottoinsieme di archivi git creati manualmente presentava valori di nome non corretti che ne influenzavano l’utilizzo [la funzione di riutilizzo degli artefatti di build.](setting-up-project.md#build-artifact-reuse) I nomi di tali archivi sono stati modificati e gli utenti vedranno il nome corretto nell’API/interfaccia utente di Cloud Manager.
* [Quando aggiungi o modifichi una pipeline di qualità del codice,](configuring-non-production-pipelines.md) le opzioni per gestire gli errori di metrica non vengono più visualizzate.
* Le configurazioni impreviste delle variabili della pipeline non causano più errori nel passaggio di compilazione.
