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
source-git-commit: 9e33b90818c686f0b7aacaf0955c3f2eba05488f

---


# Evaluation Phase {#evaluation}

The first phase in the Product Update wizard is **[!UICONTROL Evaluation]** phase.
Qui è possibile valutare la complessità dell&#39;aggiornamento con il rilevatore pattern accessibile direttamente dalla procedura guidata. Alla fine di questo passaggio, potrai accedere al rapporto di valutazione.

Il rapporto generato consente di controllare l&#39;istanza Author per l&#39;upgradabilità rilevando pattern che:

* Violano determinate regole e vengono eseguite nelle aree che saranno interessate o sovrascritte dall&#39;aggiornamento.

* Utilizza una funzione AEM 6. x o un&#39;API non compatibile con il nuovo AEM e può interruzioni potenzialmente dopo l&#39;aggiornamento.

Questo serve da valutazione dell&#39;impegno di sviluppo coinvolto nell&#39;aggiornamento ad Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>To learn more about pattern detector, refer to [Assessing the Upgrade Complexity with the Pattern Detector](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/pattern-detector.html)

## Running the Evaluator {#running-evaluator}

Per generare report di valutazione, effettuate le seguenti operazioni:

1. Click on **[!UICONTROL Run Evaluation]**.

   >[!NOTE]
   >Il rilevatore pattern può essere eseguito in qualsiasi ambiente. Tuttavia, per aumentare il tasso di rilevamento ed evitare eventuali rallentamenti sulle istanze decisive di business, Cloud Manager lo eseguirà nell&#39;ambiente di verifica nell&#39;istanza di authoring.

   ![](assets/Run-Evaluation.png)

1. La procedura guidata vi informerà dello stato dell&#39;azione. You will notice **In progress** or **completed** as applicable when the evaluation report is being generated.

   Once the report is generated, you can click on **[!UICONTROL Download report]** to save a copy.

   ![](assets/Evaluation-1.png)


>[!NOTE]
>The current release of Product Update wizard in Cloud Manager supports the **Evaluation** phase only. The other four phases namely **Remediation**, **Execution**, **Validation**, and **Completion** are coming soon.