---
title: Utilizzare la Creazione guidata nuovo progetto
description: Segui questa pagina per scoprire come utilizzare la procedura guidata per creare un progetto di applicazione AEM
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
source-git-commit: 11a6a53d8cbfb689810a9a8e7d82293a49863084
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 33%

---


# Utilizzare la procedura guidata Nuovo progetto {#using-the-wizard}

Al momento dell’onboarding in Cloud Manager come nuovo cliente, ti veniva fornito un archivio Git vuoto. Per aiutarti a iniziare, Cloud Manager offre una procedura guidata per creare un progetto AEM minimo utilizzando come punto di partenza l’[archetipo di progetto AEM](https://github.com/adobe/aem-project-archetype).

Segui questi passaggi per creare un progetto AEM utilizzando la procedura guidata.

1. Accedi a Cloud Manager all’indirizzo [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) e seleziona l’organizzazione appropriata.

1. Se non lo hai già fatto, [crea il tuo programma](program-setup.md). Al momento della creazione del programma, Cloud Manager rileva che gli archivi non sono ancora configurati. Nella schermata **Panoramica** viene quindi visualizzata una speciale scheda di invito all&#39;azione.

   ![Invito all’azione per creare un progetto](/help/assets/image2018-10-3_14-29-44.png)

1. Fai clic su **Crea** per avviare la procedura guidata e specifica i valori richiesti.

   * **Titolo** - Titolo del progetto. Per impostazione predefinita, è impostato sul nome del programma.
   * **Nome nuovo ramo**: il ramo iniziale degli archivi Git. Per impostazione predefinita è `main`.

   ![Valori del progetto](/help/assets/screen_shot_2018-10-08at55825am.png)

1. La finestra di dialogo contiene un cassetto che può essere aperto facendo clic sulla maniglia verso il basso. Nella forma espansa, la finestra di dialogo mostra tutti i parametri di configurazione per l’archetipo di progetto AEM. Questi parametri hanno valori predefiniti generati in base al **Titolo** già fornito e non richiedono modifiche. Le descrizioni di seguito vengono fornite unicamente a scopo informativo.

   ![Parametri dettagliati dell’archetipo](/help/assets/screen_shot_2018-10-08at60032am.png)

1. Fai clic su **Crea** per creare il progetto iniziale utilizzando l’archetipo e confermare il ramo Git denominato.

Ora hai un progetto di base. È ora di configurare le pipeline.

## Clienti esistenti o in fase di migrazione {#existing-migrating}

Se sei un cliente Managed Services (AMS) di Adobe o un cliente AEM on-premise in procinto di migrare a, probabilmente hai già un codice progetto in Git o in un altro sistema di controllo della versione.

In questi casi, puoi importare il progetto nell’archivio Git di Cloud Manager.
