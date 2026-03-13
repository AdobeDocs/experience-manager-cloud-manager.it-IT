---
title: Note sulla versione per Cloud Manager 2026.3.0
description: Scopri la versione di Cloud Manager 2026.3.0 su Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: ee49b0732fdb870c4f768764aa75b240fd101b59
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 19%

---

# Note sulla versione per Cloud Manager 2026.3.0 su Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Scopri la versione di [!UICONTROL Cloud Manager] 2026.3.0 su Adobe Managed Services.

Consulta anche le [note sulla versione corrente di Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/release-notes/home).

## Date di pubblicazione {#release-date}

La data di rilascio per [!UICONTROL Cloud Manager] 2026.3.0 è giovedì 5 marzo 2026.
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

La prossima versione pianificata è giovedì 2 aprile 2026.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Novità {#what-is-new}

* **Supporto per l&#39;estensibilità dell&#39;interfaccia utente in AEM Experience Hub**
Il supporto per le estensioni dell&#39;interfaccia utente in [AEM Experience Hub](https://experienceleague.adobe.com/it/docs/experience-manager-65/content/experience-hub/experience-hub) è ora abilitato e consente agli sviluppatori di estendere l&#39;interfaccia con funzionalità personalizzate e widget generati con Adobe App Builder.

  Per ulteriori informazioni, consulta [AEM Experience Hub](https://developer.adobe.com/uix/docs/services/aem-experience-hub/).

* **Le pipeline di configurazione ora supportano i segreti gestiti**

  Ora gli utenti possono aggiungere e gestire i segreti direttamente nelle pipeline di configurazione di Cloud Manager. Questi segreti sostituiscono in modo sicuro i valori nelle specifiche di configurazione della pipeline e supportano distribuzioni flessibili e specifiche per l’ambiente.

  ![Opzione Visualizza/Modifica variabili nel menu a discesa per una pipeline selezionata](/help/release-notes/assets/view-edit-variables-option.png)
  *Opzione Visualizza/Modifica variabili nel menu a discesa per una pipeline selezionata.*

  ![Finestra di dialogo Configurazione variabili &#x200B;](/help/release-notes/assets/view-edit-variables-variablesconfig-dialogbox.png)*Finestra di dialogo Configurazione variabili.*

* **Stabilità, prestazioni e affidabilità migliorate**

  Questa versione include aggiornamenti di ottimizzazione e manutenzione che migliorano la stabilità, le prestazioni e l’affidabilità di Cloud Manager.


## Programmi Beta {#beta-program}

Partecipa ai programmi Beta di Cloud Manager per ottenere accesso esclusivo alle prossime funzionalità prima del rilascio generale.

Sono attualmente disponibili le seguenti opportunità:

<!--
### Experience Hub Extensibility and Customization {#exp-hub-extensibility}

[Experience Hub](https://experienceleague.adobe.com/it/docs/experience-manager-65/content/experience-hub/experience-hub) serves as your entry point to AEM, customized for your organization's needs. Tell Adobe about your existing AEM UI extensions so they can help you enable them in Experience Hub with minimal effort.

![Diagram of Experience Hub extensibility and customization workflow](/help/release-notes/assets/experience-hub-extensibility-customization.png)

Embed custom experiences in Experience Hub to extend and personalize your organization's dashboard. In addition to Adobe's built-in widgets, add your own using the [UI Extensibility](https://developer.adobe.com/uix/docs/) framework. Build JavaScript-based UI apps and surface them to your users to meet business-specific requirements and workflows. 

Interested in the beta? Email [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) with your Adobe OrgID and a short description of the customization you intend to create.
-->

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

## Correzioni di bug {#bug-fixes}

Non vi sono correzioni di bug significativi nella versione di marzo 2026 di Cloud Manager su AMS.

<!--
Known Issues {#known-issues}

* A 
-->
