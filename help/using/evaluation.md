---
title: Valutazione
seo-title: Valutazione
description: 'Questa pagina funge da punto di partenza per imparare la fase di valutazione nella procedura guidata Aggiornamento prodotto. '
seo-description: Questa pagina funge da punto di partenza per imparare la fase di valutazione nella procedura guidata Aggiornamento prodotto.
uuid: 62d68e79-c2ba-4d8b-ba7d-33709014d5b6
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: ebcc91a5-be9e-4684-8146-d88f4013d4d1
translation-type: tm+mt
source-git-commit: 3bb435aae932b9446867c30b7dd6b0a8e0839ee2
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 0%

---


# Fase di valutazione {#evaluation}

La prima fase della procedura guidata Aggiornamento prodotto è la **[!UICONTROL Evaluation]** fase.
Qui è possibile valutare la complessità dell&#39;aggiornamento con il rilevatore di pattern accessibile direttamente dalla procedura guidata. Al termine di questo passaggio, avrete accesso al rapporto di valutazione.

Il rapporto generato consente di controllare l&#39;istanza Author per la aggiornabilità rilevando pattern che:

* Violare determinate regole e vengono eseguite in aree che saranno interessate o sovrascritte dall&#39;aggiornamento.

* Utilizzate una funzione AEM 6.x o un&#39;API che non sia compatibile con le versioni precedenti del nuovo AEM e che possa interrompersi dopo l&#39;aggiornamento.

Questo serve come valutazione dello sforzo di sviluppo associato all’aggiornamento  Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>
>Per ulteriori informazioni sul rilevatore di pattern, vedere [Valutazione della complessità dell&#39;aggiornamento con il rilevatore di pattern](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/pattern-detector.html)

## Esecuzione di Valutazione {#running-evaluator}

Per generare il rapporto di valutazione, effettuate le operazioni seguenti:

1. Fate clic su **[!UICONTROL Run Evaluation]**.

   >[!NOTE]
   >Il rilevatore di pattern può essere eseguito in qualsiasi ambiente. Tuttavia, al fine di aumentare il tasso di rilevamento ed evitare eventuali rallentamenti nelle istanze business critical, Cloud Manager lo eseguirà nell&#39;ambiente di pubblicazione temporanea nell&#39;istanza di creazione.

   ![](assets/Run-Evaluation.png)

1. La procedura guidata vi informa dello stato dell’azione. Al momento della generazione del rapporto di valutazione noterete **In corso** o **completati** .

   Una volta generato il rapporto, potete fare clic su **[!UICONTROL Download report]** per salvarne una copia.

   ![](assets/Evaluation-1.png)


   >[!NOTE]
   >
   >La versione corrente della procedura guidata Aggiornamento prodotto in Cloud Manager supporta solo la fase di **valutazione** . Le altre quattro fasi, ovvero **riparazione**, **esecuzione**, **convalida** e **completamento** , sono in arrivo a breve.
