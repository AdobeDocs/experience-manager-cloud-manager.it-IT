---
title: Valutazione
seo-title: Valutazione
description: 'Questa pagina funge da punto di partenza per la fase di apprendimento in Procedura guidata di aggiornamento prodotto. '
seo-description: Questa pagina funge da punto di partenza per la fase di apprendimento in Procedura guidata di aggiornamento prodotto.
uuid: 62 d 68 e 79-c 2 ba -4 d 8 b-ba 7 d -33709014 d 5 b 6
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: ebcc 91 a 5-be 9 e -4684-8146-d 88 f 4013 d 4 d 1
translation-type: tm+mt
source-git-commit: 47331787d45fe68144cb90c4b907560fe0079b3c

---


# Evaulation Phase {#evaluation}

Dopo aver fatto clic su Avvia aggiornamento, la prima fase di Aggiornamento prodotto guidata è la fase Valutazione. In questa fase, potete valutare la complessità dell&#39;aggiornamento con il rilevatore pattern accessibile direttamente dalla procedura guidata. Alla fine di questo passaggio, potrai accedere al rapporto di valutazione.

Il rapporto generato consente di controllare l&#39;istanza Author per ottenere l&#39;upgradabilità rilevando i pattern in uso:

* Violano determinate regole e vengono eseguite nelle aree che saranno interessate o sovrascritte dall&#39;aggiornamento.

* Utilizza una funzione AEM 6. x o un&#39;API non compatibile con il nuovo AEM e può interruzioni potenzialmente dopo l&#39;aggiornamento.


Questo serve da valutazione dell&#39;impegno di sviluppo coinvolto nell&#39;aggiornamento ad Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>To learn more about pattern detector, refer to [Assessing the Upgrade Complexity with the Pattern Detector](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/pattern-detector.html)

## Running the Evaluator {#running-evaluator}

Effettuate le seguenti operazioni per eseguire il valutatore:

1. Select [!UICONTROL Run evaluation] to run the pattern detector. Il rilevatore pattern può essere eseguito in qualsiasi ambiente. Tuttavia, per aumentare il tasso di rilevamento ed evitare eventuali rallentamenti sulle istanze decisive di business, Cloud Manager lo eseguirà nell&#39;ambiente di verifica nell&#39;istanza di authoring.

1. La procedura guidata indica lo stato dell&#39;azione. You will notice **In progress** or **completed** as applicable when the evaluation report is being generated.

Once the report is generated, you can select [!UICONTROL Download] to save a copy of the evaluation report.

>[!NOTE]
>The other four phases succeeding **Evaluation** namely **Remediation**, **Execution**, **Validation**, and **Completion** are coming soon and are not available in the current release.
