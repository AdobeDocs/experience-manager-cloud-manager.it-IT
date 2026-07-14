---
title: Utilizzo della procedura guidata Nuovo progetto
description: Segui questa pagina per scoprire come utilizzare la procedura guidata per creare un progetto di applicazione AEM.
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
TQID: https://experienceleague.adobe.com/zoiHL1lNC2XN-T9g0dh3pQyL4Yw3uYgFpHs8d6hkj3M
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: fa6be369b979682cebf68852603725d8754605ab
workflow-type: tm+mt
source-wordcount: 317
ht-degree: 54%

---

# Utilizza la procedura guidata per un nuovo progetto {#using-the-wizard}

Quando effettui l’onboarding in Cloud Manager come nuovo cliente, ti viene fornito un archivio Git vuoto. Per aiutarti a iniziare, Cloud Manager offre una procedura guidata per la creazione di un progetto AEM minimo basato sull&#39;[archetipo progetto AEM](https://github.com/adobe/aem-project-archetype) come punto di partenza.

**Per utilizzare la creazione guidata nuovo progetto:**

1. Accedi a Cloud Manager all’indirizzo [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) e seleziona l’organizzazione appropriata.

1. Se non lo hai già fatto, [crea il programma](program-setup.md). Al momento della creazione del programma, Cloud Manager rileva che l’archivio non è configurato. Nella schermata **Panoramica** viene quindi visualizzata una speciale scheda di richiesta.

   ![Invito all’azione per creare un progetto](/help/assets/image2018-10-3_14-29-44.png)

1. Fai clic su **Crea** per avviare la procedura guidata e specifica i valori richiesti.

   * **Titolo**: il titolo del progetto. Per impostazione predefinita, è impostato sul nome del programma.
   * **Nome nuovo ramo**: il ramo iniziale dell&#39;archivio Git. Per impostazione predefinita, è `main`.

   ![Valori del progetto](/help/assets/screen_shot_2018-10-08at55825am.png)

1. La finestra di dialogo contiene una sezione che è possibile visualizzare facendo clic sull&#39;icona accanto alla parte inferiore. Quando è espansa, la finestra di dialogo presenta tutti i parametri di configurazione per l’archetipo di progetto AEM. Questi parametri hanno valori predefiniti generati in base al **Titolo** già specificato e non richiedono modifiche. Le descrizioni di seguito vengono fornite unicamente a scopo informativo.

   ![Parametri dettagliati dell’archetipo](/help/assets/screen_shot_2018-10-08at60032am.png)

1. Fai clic su **Crea** per creare il progetto iniziale utilizzando l’archetipo e confermare il ramo Git denominato.

Ora hai un progetto di base. Ora puoi configurare le pipeline.

## Clientela esistente o in fase di migrazione {#existing-migrating}

Se sei un cliente Adobe Managed Services (AMS) corrente o un cliente AEM on-premise che sta eseguendo la migrazione, il codice del progetto è già in Git o in un altro sistema di controllo della versione.

In questi casi, puoi importare il progetto nell’archivio Git di Cloud Manager.
