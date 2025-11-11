---
title: Note sulla versione 2025.11.0 di Cloud Manager
description: Ulteriori informazioni sulla versione 2025.11.0 di Cloud Manager su Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: de56679c3b6cea8b11e412ec9e489eeab3de190a
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 72%

---

# Note sulla versione di Cloud Manager 2025.11.0 su Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Ulteriori informazioni sulla versione di [!UICONTROL Cloud Manager] 2025.11.0 su Adobe Managed Services.

Consulta anche le [note sulla versione corrente di Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/release-notes/home).

## Date di pubblicazione {#release-date}

La data di rilascio della versione 2025.11.0 di [!UICONTROL Cloud Manager] è il venerdì 13 novembre 2025.

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

La prossima versione è pianificata per il venerdì 4 dicembre 2025.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Novità {#what-is-new}

Non vi sono nuove funzioni significative nella versione di novembre 2025 di Cloud Manager su AMS.


## Programmi Beta {#beta-program}

Partecipa ai programmi Beta di Cloud Manager per ottenere accesso esclusivo alle prossime funzionalità prima del rilascio generale.

Sono attualmente disponibili le seguenti opportunità:

### Estensibilità e personalizzazione di Experience Hub {#exp-hub-extensibility}

[Experience Hub](https://experienceleague.adobe.com/it/docs/experience-manager-65/content/experience-hub/experience-hub) funge da punto di accesso ad AEM, personalizzato in base alle esigenze della tua organizzazione. Comunica ad Adobe le tue estensioni dell’interfaccia utente di AEM esistenti, in modo che possano aiutarti ad abilitarle in Experience Hub con il minimo sforzo.

![Diagramma del workflow di estensibilità e personalizzazione di Experience Hub](/help/release-notes/assets/experience-hub-extensibility-customization.png)

Incorpora esperienze personalizzate in Experience Hub per estendere e personalizzare il dashboard della tua organizzazione. Oltre ai widget incorporati di Adobe, aggiungi quelli personalizzati utilizzando il framework [Estensibilità dell’interfaccia utente](https://developer.adobe.com/uix/docs/). Crea app dell’interfaccia utente basate su JavaScript e mostrale agli utenti per soddisfare requisiti e flussi di lavoro specifici per l’azienda.

Ti interessa la versione beta? Invia un’e-mail a [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) con il tuo OrgID Adobe e una breve descrizione della personalizzazione che intendi creare.

### Build più veloci con il caching dei moduli {#quick-build-cm-pipelines}

Un nuovo modello di build compila solo i moduli modificati (anziché l’intero archivio) utilizzando il caching a livello di modulo per ridurre i tempi della build. Si applica alle pipeline di qualità del codice, full stack e di solo staging.

![Finestra di dialogo Modifica pipeline non di produzione con le due opzioni Strategia di compilazione Full Build e Smart Build](/help/release-notes/assets/non-production-pipeline-edit.png)
*Finestra di dialogo Modifica pipeline non di produzione che mostra le due opzioni Strategia di compilazione, Build completa e Build avanzata.*

Nella finestra di dialogo **Aggiungi/Modifica pipeline**, nella scheda **Codice Source**, una nuova sezione **Strategia di compilazione** consente di scegliere una delle seguenti opzioni di compilazione:

* **Build completa**: crea tutti i moduli nell&#39;archivio a ogni esecuzione.
* **Smart Build**: crea solo i moduli che sono cambiati dall&#39;ultimo commit, riducendo così il tempo di compilazione complessivo.

Puoi controllare quali pipeline utilizzano **Smart build**. Durante la versione beta, questa opzione viene visualizzata solo per le pipeline **Qualità codice** e **Distribuzione sviluppatore**.

Ti interessa? Invia un’e-mail a [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com) indicando il tuo OrgID Adobe e l’ID programma.

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline variables](/help/getting-started/build-environment.md#pipeline-variables). -->


### Integra il tuo Git personale (BYOG) {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

Ora è possibile portare in Cloud Manager i propri archivi Git Azure DevOps, con supporto per i nuovi archivi Azure DevOps e gli archivi legacy VSTS (Visual Studio Team Services).

* Per chi usa Edge Delivery Services, l’archivio di cui è stato eseguito l’onboarding può essere utilizzato per sincronizzare e distribuire il codice del sito.
* Per chi usa AEM as a Cloud Service e Adobe Managed Services (AMS), l’archivio può essere collegato sia a pipeline full stack che front-end.

Verranno presto introdotti anche il supporto di ulteriori tipi di pipeline e la convalida di richieste pull tramite pipeline per la qualità del codice.

Consulta [Aggiungere archivi esterni in Cloud Manager](/help/managing-code/external-repositories.md).

![Finestra di dialogo Aggiungi archivio](/help/release-notes/assets/azure-repo.png)

Se ti interessa testare questa nuova funzione e condividere il tuo feedback, invia un’e-mail a [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) dall’indirizzo e-mail associato al tuo Adobe ID. Se ti trovi in una struttura di archivio privata/pubblica o aziendale, assicurati di specificare la piattaforma Git che desideri utilizzare.

#### Gestire i token di accesso{#manage-access-tokens}

Utilizza **Gestisci token di accesso** in Cloud Manager per visualizzare, rinominare ed eliminare i token di accesso associati agli archivi BYOG esterni, ad esempio GitHub Enterprise, GitLab, Bitbucket e Azure DevOps.

Consulta [Gestisci token di accesso](/help/managing-code/manage-access-tokens.md).

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) from your email address associated with your Adobe ID. -->

## Correzioni di bug {#bug-fixes}

Non vi sono correzioni di bug significativi nella versione di novembre 2025 di Cloud Manager su AMS.

<!--
Known Issues {#known-issues}

* A -->
