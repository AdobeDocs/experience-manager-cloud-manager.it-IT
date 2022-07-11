---
title: Fase di valutazione
seo-title: Evaluation Phase
description: Scopri in che modo la fase di valutazione della procedura guidata di aggiornamento del prodotto valuta la complessità dell'aggiornamento con il rilevatore di pattern.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
source-git-commit: ce2145da3b9e605e8a41bac28df520f14e255557
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---


# Fase di valutazione {#evaluation}

La prima fase della procedura guidata di aggiornamento del prodotto è **[!UICONTROL Evaluation]** fase, che valuta la complessità dell&#39;aggiornamento con il rilevatore di pattern direttamente all’interno della procedura guidata. Al termine di questo passaggio, potrai accedere a un rapporto di valutazione.

Il rapporto generato ti consente di verificare l’istanza di authoring per l’idoneità all’aggiornamento rilevando pattern che:

* Viola alcune regole relative alle aree che saranno interessate o sovrascritte dall’aggiornamento.

* Utilizza una funzione AEM 6.x o un&#39;API che non è compatibile con la nuova versione di AEM e può potenzialmente interrompersi dopo l&#39;aggiornamento.

La relazione serve come valutazione dello sforzo di sviluppo che è coinvolto nell&#39;aggiornamento ad Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>
>Per ulteriori informazioni sul rilevatore di pattern, fare riferimento al documento [Valutazione della complessità dell’aggiornamento con il rilevatore pattern.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/pattern-detector.html?lang=en)

## Esecuzione della valutazione {#running}

Il rilevatore di pattern può essere eseguito in qualsiasi ambiente. Tuttavia, per aumentare il tasso di rilevamento ed evitare rallentamenti nelle istanze business critical, Cloud Manager lo eseguirà nell’ambiente di staging dell’istanza di authoring.

Segui questi passaggi per generare il rapporto di valutazione.

1. Avvia la procedura guidata come descritto nel documento [Aggiornamento guidato del prodotto.](/help/product-update-wizard/overview.md)

1. Fai clic su **[!UICONTROL Run Evaluation]**.

   ![Esegui valutazione](/help/assets/Run-Evaluation.png)

1. La procedura guidata ti informa dello stato dell’azione. Lo noterete **In corso** o **completato** se del caso al momento della generazione della relazione di valutazione.

1. Una volta generato il rapporto, puoi fare clic su **[!UICONTROL Download report]** per salvare una copia.

   ![Report creato](/help/assets/Evaluation-1.png)

La versione corrente della procedura guidata di aggiornamento del prodotto in Cloud Manager supporta **Valutazione** solo fase. Le altre quattro fasi sono: **Rimedio**, **Esecuzione**, **Convalida** e **Completamento** verranno presto.
