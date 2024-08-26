---
title: Fase di valutazione
seo-title: Evaluation Phase
description: Scopri in che modo la fase di valutazione della procedura guidata di aggiornamento del prodotto valuta la complessità dell’aggiornamento con il rilevatore pattern.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
source-git-commit: 11a6a53d8cbfb689810a9a8e7d82293a49863084
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 31%

---


# Fase di valutazione {#evaluation}

La prima fase della procedura guidata di aggiornamento del prodotto è la fase **[!UICONTROL Valutazione]**, che valuta la complessità dell&#39;aggiornamento con il rilevatore pattern direttamente all&#39;interno della procedura guidata. Al termine di questo passaggio, puoi accedere al rapporto di valutazione.

Il rapporto generato consente di verificare l’istanza di authoring per l’idoneità all’aggiornamento rilevando i seguenti pattern che:

* Interrompi alcune regole relative alle aree interessate o sovrascritte dall’aggiornamento.

* Utilizza una funzione AEM 6.x o un’API che non è compatibile con le versioni precedenti della nuova versione dell’AEM e può potenzialmente interrompersi dopo un aggiornamento.

Il rapporto serve come valutazione dello sforzo di sviluppo che è coinvolto nell’aggiornamento ad Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>
>Per ulteriori informazioni sul rilevatore pattern, vedere [Valutazione della complessità dell&#39;aggiornamento con il rilevatore pattern](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/upgrading/pattern-detector).

## Eseguire il rapporto di valutazione {#running}

Il rilevatore pattern può essere eseguito in qualsiasi ambiente. Tuttavia, per aumentare il tasso di rilevamento ed evitare rallentamenti nelle istanze business critical, Cloud Manager lo esegue nell’ambiente di staging dell’istanza di authoring.

**Per eseguire il rapporto di valutazione:**

1. Avvia la procedura guidata come descritto nel documento [Procedura guidata di aggiornamento del prodotto](/help/product-update-wizard/overview.md).

1. Fai clic su **[!UICONTROL Esegui valutazione]**.

   ![Esegui valutazione](/help/assets/Run-Evaluation.png)

1. La procedura guidata ti informa sullo stato dell’azione. Al momento della generazione del rapporto di valutazione, noterai la dicitura **in corso** o **completato**, a seconda dei casi.

1. Dopo aver generato il report, puoi fare clic su **[!UICONTROL Scarica report]** per salvare una copia.

   ![Rapporto creato](/help/assets/Evaluation-1.png)

La versione corrente della procedura guidata di aggiornamento del prodotto in Cloud Manager supporta solo la fase **Valutazione**. Le altre quattro fasi **Rimedio**, **Esecuzione**, **Convalida** e **Completamento** saranno presto disponibili.
