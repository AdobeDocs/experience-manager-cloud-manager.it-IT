---
title: Note sulla versione 2021.3.0
description: Segui questa pagina per ottenere informazioni sulla versione 2021.3.0 di Cloud Manager
feature: Informazioni sulla versione
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea,e05b22fe-f071-4b69-9db1-e3d7ee4cfbcc
translation-type: tm+mt
source-git-commit: 9c3e748f8aed969af861b505ee336eb5501d826f
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 5%

---

# Note sulla versione 2021.3.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per [!UICONTROL Cloud Manager] la versione 2021.3.0.

## Data di rilascio {#release-date}

La data di rilascio per la versione 2021.3.0 di [!UICONTROL Cloud Manager] è l’11 marzo 2021.
La prossima versione è prevista per il 08 aprile 2021.

## Novità {#whats-new}

* È stato introdotto un nuovo strumento per la qualità del codice [Dispatcher Optimization Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/custom-code-quality-rules.html?lang=en#dispatcher-optimization-tool-rules) per convalidare la configurazione del dispatcher cliente.

* Gli utenti possono ora visualizzare i propri ruoli di Cloud Manager selezionando l’opzione **Visualizza ruoli di Cloud Manager** dopo aver visualizzato l’icona Profilo utente (in alto a destra) di Unified Shell.

* L&#39;etichetta **Domanda di approvazione** è stata rinominata **Approvazione produzione** per una maggiore chiarezza.

* L’etichetta **Versione** è stata rinominata **Tag Git** nella schermata di esecuzione della pipeline di produzione.

* Le etichette che definiscono il comportamento quando le metriche importanti non soddisfano la soglia definita sono state rinominate per riflettere il loro comportamento vero: **Annulla immediatamente** e **Approva immediatamente**. Per ulteriori informazioni, consulta [Configurazione delle impostazioni della pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=en#configuring-the-pipeline-settings-from-cloud-manager) .

* Gli elenchi di elementi obsoleti di classi e metodi sono stati aggiornati in base alla versione `2021.3.4997.20210303T022849Z-210225` dell’SDK del Cloud Service AEM.

## Correzioni di bug {#bug-fixes}

* Alcuni problemi di qualità non sono stati rilevati correttamente quando i pacchetti sono stati incorporati in altri pacchetti.

* Talvolta, se l’utente si allontana dalla pagina di esecuzione della pipeline immediatamente dopo l’avvio di una pipeline, viene visualizzato un messaggio di errore che indica che l’azione non è riuscita, anche se l’esecuzione viene effettivamente avviata.
