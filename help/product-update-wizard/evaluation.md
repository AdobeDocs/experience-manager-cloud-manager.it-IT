---
title: Fase di valutazione
seo-title: Evaluation Phase
description: Scopri in che modo la fase di valutazione della procedura guidata di aggiornamento del prodotto valuta la complessità dell’aggiornamento con il rilevatore pattern.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
source-git-commit: ce2145da3b9e605e8a41bac28df520f14e255557
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 100%

---


# Fase di valutazione {#evaluation}

La prima fase della procedura guidata di aggiornamento del prodotto è quella di **[!UICONTROL valutazione]** che valuta la complessità dell’aggiornamento con il rilevatore pattern direttamente all’interno della procedura guidata. Al termine di questa fase, potrai accedere a un rapporto di valutazione.

Il rapporto generato ti consente di verificare l’istanza di authoring per l’idoneità all’aggiornamento rilevando pattern che:

* Violano alcune regole relative alle aree che saranno interessate o sovrascritte dall’aggiornamento.

* Utilizzano una funzione AEM 6.x o un’API che non è compatibile con le versioni precedenti della nuova versione di AEM e può potenzialmente interrompersi dopo l’aggiornamento.

Il rapporto serve come valutazione dello sforzo di sviluppo che è coinvolto nell’aggiornamento ad Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>
>Per ulteriori informazioni sul rilevatore pattern, fare riferimento al documento [Valutazione della complessità dell’aggiornamento con il rilevatore pattern.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/pattern-detector.html?lang=it)

## Esecuzione della valutazione {#running}

Il rilevatore pattern può essere eseguito in qualsiasi ambiente. Tuttavia, per aumentare il tasso di rilevamento ed evitare rallentamenti nelle istanze aziendali critiche, Cloud Manager lo eseguirà nell’ambiente di staging dell’istanza di authoring.

Per generare il rapporto di valutazione, segui i passaggi seguenti.

1. Avvia la procedura guidata come descritto nel documento [Procedura guidata di aggiornamento del prodotto.](/help/product-update-wizard/overview.md)

1. Fai clic su **[!UICONTROL Esegui valutazione]**.

   ![Esegui valutazione](/help/assets/Run-Evaluation.png)

1. La procedura guidata ti informa sullo stato dell’azione. Al momento della generazione del rapporto di valutazione, noterai la dicitura **in corso** o **completato**, a seconda dei casi.

1. Una volta generato il rapporto, puoi fare clic su **[!UICONTROL Scarica rapporto]** per salvare una copia.

   ![Rapporto creato](/help/assets/Evaluation-1.png)

La versione corrente della procedura guidata di aggiornamento del prodotto in Cloud Manager supporta solo la fase **Valutazione**. Le altre quattro fasi **Rimedio**, **Esecuzione**, **Convalida** e **Completamento** saranno presto disponibili.
