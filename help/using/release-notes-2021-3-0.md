---
title: Note sulla versione 2021.3.0
description: Segui questa pagina per ottenere informazioni sulla versione 2021.3.0 di Cloud Manager
feature: Release Information
source-git-commit: 09dd8fe608d95cd9dbc95129cf86b9693c2839b5
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 5%

---

# Note sulla versione 2021.3.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione di [!UICONTROL Cloud Manager] Versione 2021.3.0.

## Data di pubblicazione {#release-date}

Data di rilascio per [!UICONTROL Cloud Manager] La versione 2021.3.0 è l’11 marzo 2021.
La prossima versione è prevista per il 08 aprile 2021.

## Novità {#whats-new}

* Nuovo strumento per la qualità del codice [Strumento di ottimizzazione del dispatcher](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/custom-code-quality-rules.html?lang=en#dispatcher-optimization-tool-rules) è stato introdotto per convalidare la configurazione del dispatcher cliente.

* Gli utenti possono ora visualizzare i propri ruoli di Cloud Manager selezionando **Visualizzare i ruoli di Cloud Manager** dopo aver visualizzato l’icona Profilo utente (in alto a destra) di Unified Shell.

* Etichetta **Domanda di approvazione** è stato riassegnato a **Approvazione produzione** per una maggiore chiarezza.

* La **Versione** l’etichetta è stata rinominata in **Tag Git** nella schermata di esecuzione della pipeline di produzione .

* Le etichette che definiscono il comportamento quando le metriche importanti non soddisfano la soglia definita sono state rinominate per riflettere il loro comportamento effettivo - **Annulla immediatamente** e **Approva immediatamente**. Fai riferimento a [Configurazione delle impostazioni della pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=en#configuring-the-pipeline-settings-from-cloud-manager) per ulteriori dettagli.

* Gli elenchi di elementi obsoleti di classi e metodi sono stati aggiornati in base alla versione `2021.3.4997.20210303T022849Z-210225` dell’SDK AEM Cloud Service.

## Correzioni di bug {#bug-fixes}

* Alcuni problemi di qualità non sono stati rilevati correttamente quando i pacchetti sono stati incorporati in altri pacchetti.

* Talvolta, se l’utente si allontana dalla pagina di esecuzione della pipeline immediatamente dopo l’avvio di una pipeline, viene visualizzato un messaggio di errore che indica che l’azione non è riuscita, anche se l’esecuzione viene effettivamente avviata.
