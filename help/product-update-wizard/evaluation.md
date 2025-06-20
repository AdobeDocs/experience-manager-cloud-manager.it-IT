---
title: Fase di valutazione
seo-title: Evaluation Phase
description: Scopri in che modo la fase di valutazione della procedura guidata di aggiornamento del prodotto valuta la complessità dell’aggiornamento con il rilevatore pattern.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 57%

---


# Fase di valutazione {#evaluation}

La prima fase della procedura guidata di aggiornamento del prodotto è la fase **[!UICONTROL Valutazione]**. Esegue il rilevatore pattern all’interno della procedura guidata per valutare la complessità dell’aggiornamento. Al termine di questo passaggio, puoi visualizzare il rapporto di valutazione.

Il rapporto controlla l’istanza di authoring per verificare la fattibilità dell’aggiornamento rilevando i pattern per i seguenti elementi:

* Violazioni delle regole nelle aree interessate o sovrascritte dall’aggiornamento.
* Utilizza funzioni o API di AEM 6.x che non sono compatibili con le versioni precedenti e potrebbero interrompersi dopo l’aggiornamento.

Questo rapporto consente di stimare lo sforzo di sviluppo necessario per effettuare l’aggiornamento a Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>
>Per ulteriori informazioni sul rilevatore pattern, consulta [Valutazione della complessità dell’aggiornamento con il rilevatore pattern](https://experienceleague.adobe.com/it/docs/experience-manager-65/content/implementing/deploying/upgrading/pattern-detector).

## Eseguire il rapporto di valutazione {#running}

Il rilevatore pattern può essere eseguito in qualsiasi ambiente. Tuttavia, per aumentare il tasso di rilevamento ed evitare rallentamenti nelle istanze aziendali critiche, Cloud Manager lo esegue nell’ambiente di staging dell’istanza di authoring.

**Per eseguire il rapporto di valutazione:**

1. Avvia la procedura guidata come descritto nel documento [Procedura guidata di aggiornamento del prodotto](/help/product-update-wizard/overview.md).

1. Fai clic su **[!UICONTROL Esegui valutazione]**.

   ![Esegui valutazione](/help/assets/Run-Evaluation.png)

1. La procedura guidata ti informa sullo stato dell’azione. Al momento della generazione del rapporto di valutazione, noterai la dicitura **in corso** o **completato**, a seconda dei casi.

1. Una volta generato il rapporto, puoi fare clic su **[!UICONTROL Scarica rapporto]** per salvarne una copia.

   ![Rapporto creato](/help/assets/Evaluation-1.png)

L&#39;attuale procedura guidata di aggiornamento del prodotto in Cloud Manager supporta solo la fase **Valutazione**. Le altre quattro fasi **Rimedio**, **Esecuzione**, **Convalida** e **Completamento** saranno presto disponibili.
