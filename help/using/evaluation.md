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
source-git-commit: 8d1a100420129d234fe21911f165621405a04a9b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Fase di valutazione {#evaluation}

La prima fase della procedura guidata Aggiornamento prodotto è **[!UICONTROL Evaluation]**.
Qui è possibile valutare la complessità dell&#39;aggiornamento con il rilevatore di pattern accessibile direttamente dalla procedura guidata. Al termine di questo passaggio, avrete accesso al rapporto di valutazione.

Il rapporto generato consente di controllare l&#39;istanza Author per l&#39;aggiornamento rilevando pattern che:

* Violare determinate regole e vengono eseguite in aree che saranno interessate o sovrascritte dall&#39;aggiornamento.

* Utilizzate una funzione AEM 6.x o un&#39;API non compatibile con le versioni precedenti sul nuovo AEM e che può interrompersi dopo l&#39;aggiornamento.

Questo serve come valutazione dello sforzo di sviluppo che comporta l’aggiornamento ad Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>
>Per ulteriori informazioni sul rilevatore di pattern, vedere [Valutare la complessità dell&#39;aggiornamento con il rilevatore di pattern](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/pattern-detector.html)

## Esecuzione del valutatore {#running-evaluator}

Per generare il rapporto di valutazione, effettuate le operazioni seguenti:

1. Fare clic su **[!UICONTROL Run Evaluation]**.

   >[!NOTE]
   >
   >Il rilevatore di pattern può essere eseguito in qualsiasi ambiente. Tuttavia, al fine di aumentare il tasso di rilevamento ed evitare eventuali rallentamenti nelle istanze business critical, Cloud Manager lo eseguirà nell&#39;ambiente di pubblicazione temporanea nell&#39;istanza di creazione.

   ![](assets/Run-Evaluation.png)

1. La procedura guidata vi informa dello stato dell’azione. Al momento della generazione del rapporto di valutazione verrà visualizzato **In corso** o **completato**.

   Una volta generato il rapporto, potete fare clic su **[!UICONTROL Download report]** per salvare una copia.

   ![](assets/Evaluation-1.png)


   >[!NOTE]
   >
   >La versione corrente della procedura guidata Aggiornamento prodotto in Cloud Manager supporta solo la fase **Evaluation**. Le altre quattro fasi, ovvero **Correzione**, **Esecuzione**, **Convalida** e **Completamento**, sono in arrivo a breve.
