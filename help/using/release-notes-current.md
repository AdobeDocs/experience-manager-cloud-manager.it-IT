---
title: Note sulla versione 2021.3.0
seo-title: Note sulla versione di AEM Cloud Manager 2021.3.0
description: Segui questa pagina per ottenere informazioni sulla versione 2021.3.0 di Cloud Manager
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2021.3.0 di AEM Cloud Manager
translation-type: tm+mt
source-git-commit: 47424ea0e087f1f69db0aef8ca2122de2352a6e0
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 3%

---

# Note sulla versione 2021.3.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per [!UICONTROL Cloud Manager] la versione 2021.3.0.

## Data di rilascio {#release-date}

La data di rilascio per la versione 2021.3.0 di [!UICONTROL Cloud Manager] è l’11 marzo 2021.

## Novità {#whats-new}

* Gli utenti con le autorizzazioni necessarie possono ora modificare il programma, consentendo loro di effettuare le seguenti operazioni in modalità self-service:

   * Aggiungi la soluzione Sites a un programma esistente con Assets (o viceversa).
   * Rimuovi Sites (o Assets) da un programma esistente sia con Sites che con Assets.
   * È possibile aggiungere (indietro) una soluzione al programma esistente o come nuovo programma.

* È stato introdotto un nuovo strumento per la qualità del codice [Dispatcher Optimization Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/custom-code-quality-rules.html?lang=en#dispatcher-optimization-tool-rules) per convalidare la configurazione del dispatcher cliente.

* Gli utenti possono ora visualizzare i propri ruoli di Cloud Manager selezionando l’opzione **Visualizza ruoli di Cloud Manager** dopo aver visualizzato l’icona Profilo utente (in alto a destra) di Unified Shell.

* L&#39;etichetta **Domanda di approvazione** è stata rinominata **Approvazione produzione** per una maggiore chiarezza.

* L’etichetta **Versione** è stata rinominata **Tag Git** nella schermata di esecuzione della pipeline di produzione.

* Le etichette che definiscono il comportamento quando le metriche importanti non soddisfano la soglia definita sono state rinominate per riflettere il loro comportamento vero: **Annulla immediatamente** e **Approva immediatamente**. Per ulteriori informazioni, consulta [Configurazione delle impostazioni della pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=en#configuring-the-pipeline-settings-from-cloud-manager) .

* Gli elenchi di elementi obsoleti di classi e metodi sono stati aggiornati in base alla versione `2021.3.4997.20210303T022849Z-210225` dell’SDK del Cloud Service AEM.

## Correzioni di bug {#bug-fixes}

* Alcuni problemi di qualità non sono stati rilevati correttamente quando i pacchetti sono stati incorporati in altri pacchetti.

* Talvolta, se l’utente si allontana dalla pagina di esecuzione della pipeline immediatamente dopo l’avvio di una pipeline, viene visualizzato un messaggio di errore che indica che l’azione non è riuscita, anche se l’esecuzione viene effettivamente avviata.