---
title: Utilizzo della Creazione guidata nuovo progetto
description: Segui questa pagina per scoprire come utilizzare la procedura guidata per creare un progetto di applicazione AEM
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
source-git-commit: cb791a4f148ba394687b5e824b75fe1386d83c18
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---


# Utilizzo della Creazione guidata nuovo progetto {#using-the-wizard}

Quando effettui l’accesso a Cloud Manager come nuovo cliente, viene fornito un archivio Git vuoto. Per aiutarti a iniziare, Cloud Manager offre una procedura guidata per creare un progetto AEM minimo basato su [Archetipo di progetto AEM](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype) come punto di partenza.

Segui questi passaggi per creare un progetto AEM utilizzando la procedura guidata.

1. Accedi a Cloud Manager all&#39;indirizzo [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) e selezionare l&#39;organizzazione appropriata.

1. Se non lo hai già fatto, [crea il programma.](program-setup.md) Una volta creato il programma, Cloud Manager riconosce che gli archivi non sono ancora configurati e viene visualizzata una speciale scheda di invito all’azione nella sezione **Panoramica** schermo.

   ![Crea progetto CTA](/help/assets/image2018-10-3_14-29-44.png)

1. Fai clic su **Crea** per avviare la procedura guidata e fornire valori importanti.

   * **Titolo** - Il titolo del progetto è impostato per impostazione predefinita sul nome del programma.
   * **Nuovo nome della filiale** - Si tratta del ramo iniziale degli archivi git e, per impostazione predefinita, sarà `main`.

   ![Valori progetto](/help/assets/screen_shot_2018-10-08at55825am.png)

1. La finestra di dialogo ha un cassetto che può essere aperto facendo clic sul manico verso il basso. Nel modulo espanso, la finestra di dialogo mostra tutti i parametri di configurazione per l’archetipo di progetto AEM. Questi parametri hanno valori predefiniti che vengono generati in base alla **Titolo** hai già fornito e non richiedono modifiche. Sono spiegati qui per le vostre informazioni.

   ![Parametri dettagliati dell&#39;archetipo](/help/assets/screen_shot_2018-10-08at60032am.png)

1. Fai clic su **Crea** per creare il progetto iniziale utilizzando l’archetipo e eseguire il commit nel ramo git denominato.

Ora hai un progetto di base! Ora è possibile impostare le tubazioni.

## Clienti esistenti o in fase di migrazione {#existing-migrating}

Se sei un cliente di Adobe Managed Services (AMS) o un cliente on-premise AEM che effettua la migrazione a, probabilmente hai già un codice di progetto in git o in un altro sistema di controllo della versione.

In questi casi, puoi importare il progetto nell’archivio Git di Cloud Manager.
