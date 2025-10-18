---
title: Utilizzo della procedura guidata Nuovo progetto
description: Segui questa pagina per scoprire come utilizzare la procedura guidata per creare un progetto di applicazione AEM.
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
source-git-commit: b98e1711f1f98f52977dd6cb4cd2bc834d81a360
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 82%

---


# Utilizza la procedura guidata per un nuovo progetto {#using-the-wizard}

Quando effettui l’onboarding in Cloud Manager come nuovo cliente, ti viene fornito un archivio Git vuoto. Per aiutarti a iniziare, Cloud Manager offre una procedura guidata per creare un progetto AEM minimo utilizzando come punto di partenza l’[archetipo di progetto AEM](https://github.com/adobe/aem-project-archetype).

Segui questi passaggi per creare un progetto AEM utilizzando la procedura guidata.

1. Accedi a Cloud Manager all’indirizzo [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) e seleziona l’organizzazione appropriata.

1. Se non lo hai già fatto, [crea il programma](program-setup.md). Una volta che hai creato il programma, Cloud Manager rileva che gli archivi non sono ancora configurati. Nella schermata **Panoramica** viene quindi visualizzata una scheda speciale di invito all’azione.

   ![Invito all’azione per creare un progetto](/help/assets/image2018-10-3_14-29-44.png)

1. Fai clic su **Crea** per avviare la procedura guidata e specifica i valori richiesti.

   * **Titolo**: il titolo del progetto. Per impostazione predefinita, è impostato sul nome del programma.
   * **Nome nuovo ramo**: il ramo iniziale degli archivi Git. Per impostazione predefinita, è `main`.

   ![Valori del progetto](/help/assets/screen_shot_2018-10-08at55825am.png)

1. La finestra di dialogo presenta una sezione che può essere aperta facendo clic sulla maniglia verso il basso. Quando è espansa, la finestra di dialogo presenta tutti i parametri di configurazione per l’archetipo di progetto AEM. Questi parametri hanno valori predefiniti generati in base al **Titolo** già specificato e non richiedono modifiche. Le descrizioni di seguito vengono fornite unicamente a scopo informativo.

   ![Parametri dettagliati dell’archetipo](/help/assets/screen_shot_2018-10-08at60032am.png)

1. Fai clic su **Crea** per creare il progetto iniziale utilizzando l’archetipo e confermare il ramo Git denominato.

Ora hai un progetto di base. È il momento di configurare le pipeline.

## Clientela esistente o in fase di migrazione {#existing-migrating}

Se sei un cliente Adobe Managed Services (AMS) corrente o un cliente AEM on-premise che sta eseguendo la migrazione, è probabile che il codice del progetto sia già presente in Git o in un altro sistema di controllo della versione.

In questi casi, puoi importare il progetto nell’archivio Git di Cloud Manager.
