---
title: Note sulla versione 2026.1.0 di Cloud Manager
description: Ulteriori informazioni sulla versione 2026.1.0 di Cloud Manager su Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 28841719e820e47577b411a4034ebc7a8e1bb556
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 51%

---

# Note sulla versione di Cloud Manager 2026.1.0 su Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Ulteriori informazioni sulla versione di [!UICONTROL Cloud Manager] 2026.1.0 su Adobe Managed Services.

Consulta anche le [note sulla versione corrente di Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/release-notes/home).

## Date di pubblicazione {#release-date}

La data di rilascio della versione 2026.1.0 di [!UICONTROL Cloud Manager] è il venerdì 22 gennaio 2026.

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

La prossima pubblicazione è pianificata per il venerdì 5 febbraio 2026.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Novità {#what-is-new}

* **Le pipeline di configurazione ora supportano i segreti gestiti**

  Ora gli utenti possono aggiungere e gestire i segreti direttamente nelle pipeline di configurazione di Cloud Manager. Questi segreti sostituiscono in modo sicuro i valori nelle specifiche di configurazione della pipeline e supportano distribuzioni flessibili e specifiche per l’ambiente.

  ![Opzione Visualizza/Modifica variabili nel menu a discesa per una pipeline selezionata](/help/release-notes/assets/view-edit-variables-option.png)
  *Opzione Visualizza/Modifica variabili nel menu a discesa per una pipeline selezionata.*

  ![Finestra di dialogo Configurazione variabili ](/help/release-notes/assets/view-edit-variables-variablesconfig-dialogbox.png)*Finestra di dialogo Configurazione variabili.*

* **Stabilità, prestazioni e affidabilità migliorate**

  Questa versione include aggiornamenti di ottimizzazione e manutenzione che migliorano la stabilità, le prestazioni e l’affidabilità di Cloud Manager.


## Programmi Beta {#beta-program}

Partecipa ai programmi Beta di Cloud Manager per ottenere accesso esclusivo alle prossime funzionalità prima del rilascio generale.

Sono attualmente disponibili le seguenti opportunità:

### Estensibilità e personalizzazione di Experience Hub {#exp-hub-extensibility}

[Experience Hub](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/experience-hub/experience-hub) funge da punto di accesso ad AEM, personalizzato in base alle esigenze della tua organizzazione. Comunica ad Adobe le tue estensioni dell’interfaccia utente di AEM esistenti, in modo che possano aiutarti ad abilitarle in Experience Hub con il minimo sforzo.

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

## Correzioni di bug {#bug-fixes}

Non vi sono correzioni di bug significativi nella versione di gennaio 2026 di Cloud Manager su AMS.

<!--
Known Issues {#known-issues}

* A -->
