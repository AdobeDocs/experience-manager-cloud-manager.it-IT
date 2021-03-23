---
title: Valutazione
seo-title: Valutazione
description: 'Questa pagina funge da punto di partenza per imparare la fase di valutazione nella procedura guidata di aggiornamento del prodotto. '
seo-description: Questa pagina funge da punto di partenza per imparare la fase di valutazione nella procedura guidata di aggiornamento del prodotto.
uuid: 62d68e79-c2ba-4d8b-ba7d-33709014d5b6
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: ebcc91a5-be9e-4684-8146-d88f4013d4d1
feature: Guida introduttiva
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 1%

---


# Fase di valutazione {#evaluation}

La prima fase della procedura guidata di aggiornamento del prodotto è **[!UICONTROL Evaluation]**.
Qui puoi valutare la complessità dell’aggiornamento con il rilevatore di pattern accessibile direttamente dalla procedura guidata. Al termine di questo passaggio, potrai accedere al rapporto di valutazione.

Il rapporto generato ti consente di controllare l’istanza di authoring per l’aggiornamento rilevando pattern che:

* Violano determinate regole e vengono eseguite in aree che saranno influenzate o sovrascritte dall’aggiornamento.

* Utilizza una funzione AEM 6.x o un&#39;API che non è compatibile con le versioni precedenti sul nuovo AEM e che può potenzialmente interrompersi dopo l&#39;aggiornamento.

Questo serve come valutazione dello sforzo di sviluppo che è coinvolto nell&#39;aggiornamento a Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>
>Per ulteriori informazioni sul rilevatore di pattern, consulta [Valutazione della complessità di aggiornamento con il rilevatore pattern](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/pattern-detector.html)

## Esecuzione del valutatore {#running-evaluator}

Per generare il rapporto di valutazione, effettua le seguenti operazioni:

1. Fai clic su **[!UICONTROL Run Evaluation]**.

   >[!NOTE]
   >
   >Il rilevatore di pattern può essere eseguito in qualsiasi ambiente. Tuttavia, per aumentare il tasso di rilevamento ed evitare rallentamenti nelle istanze business critical, Cloud Manager lo eseguirà nell’ambiente di staging sull’istanza di authoring.

   ![](assets/Run-Evaluation.png)

1. La procedura guidata ti informa dello stato dell’azione. Noterai **In corso** o **completato** come applicabile al momento della generazione del rapporto di valutazione.

   Una volta generato il rapporto, puoi fare clic su **[!UICONTROL Download report]** per salvare una copia.

   ![](assets/Evaluation-1.png)


   >[!NOTE]
   >
   >La versione corrente della procedura guidata di aggiornamento del prodotto in Cloud Manager supporta solo la fase **Evaluation** . Le altre quattro fasi, ovvero **Rimediazione**, **Esecuzione**, **Convalida** e **Completamento**, sono in arrivo a breve.
