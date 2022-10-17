---
title: Utilizzo della procedura guidata Nuovo progetto
description: Segui questa pagina per scoprire come utilizzare la procedura guidata per creare un progetto di applicazione AEM
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
source-git-commit: cb791a4f148ba394687b5e824b75fe1386d83c18
workflow-type: ht
source-wordcount: '330'
ht-degree: 100%

---


# Utilizzo della procedura guidata Nuovo progetto {#using-the-wizard}

Quando effettui l’accesso a Cloud Manager come nuovo cliente, ti viene fornito un archivio Git vuoto. Per aiutarti a iniziare, Cloud Manager offre una procedura guidata per creare un progetto AEM minimo utilizzando come punto di partenza l’[archetipo di progetto AEM](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).

Segui questi passaggi per creare un progetto AEM utilizzando la procedura guidata.

1. Accedi a Cloud Manager all’indirizzo [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) e seleziona l’organizzazione appropriata.

1. Se non lo hai già fatto, [crea il programma.](program-setup.md) Una volta creato il programma, Cloud Manager riconosce che gli archivi non sono ancora configurati e nella sezione **Panoramica** viene visualizzata una speciale scheda di invito all’azione.

   ![Invito all’azione per creare un progetto](/help/assets/image2018-10-3_14-29-44.png)

1. Fai clic su **Crea** per avviare la procedura guidata e specifica i valori richiesti.

   * **Titolo**: titolo del progetto; per impostazione predefinita corrisponde al nome del programma.
   * **Nome nuovo ramo**: si tratta del ramo iniziale degli archivi Git; l’impostazione predefinita è `main`.

   ![Valori del progetto](/help/assets/screen_shot_2018-10-08at55825am.png)

1. La finestra di dialogo presenta una sezione che può essere aperta facendo clic sulla maiglia verso il basso. Quando è espansa, la finestra di dialogo presenta tutti i parametri di configurazione per l’archetipo di progetto AEM. I parametri hanno valori predefiniti generati in base al **Titolo** già specificato e non richiedono modifiche. Le descrizioni di seguito vengono fornite unicamente a scopo informativo.

   ![Parametri dettagliati dell’archetipo](/help/assets/screen_shot_2018-10-08at60032am.png)

1. Fai clic su **Crea** per creare il progetto iniziale utilizzando l’archetipo e confermare il ramo Git denominato.

Ora hai un progetto di base. A questo punto, puoi impostare le pipeline.

## Clienti esistenti o in fase di migrazione {#existing-migrating}

Se sei cliente di Adobe Managed Services (AMS) oppure di AEM on-premise in procinto di migrare ad AMS, probabilmente hai già un codice progetto in Git o in un altro sistema di controllo della versione.

In questi casi, puoi importare il progetto nell’archivio Git di Cloud Manager.
