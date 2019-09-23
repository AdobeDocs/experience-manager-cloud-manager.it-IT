---
title: Concetti Prima Di Utilizzare Cloud Manager
seo-title: Concetti Prima Di Utilizzare Cloud Manager
description: 'null'
seo-description: 'null'
page-status-flag: mai attivato
uuid: 55cc551a-e812-4102-96c8-13d2cdd79c84
contentOwner: jsyal
discoiquuid: c3fd3f4e-0b57-4377-b923-a440c74773d8
preview: vero
translation-type: tm+mt
source-git-commit: f135526c6a47f1502395e6d53f9e286c0f935da5

---


# Concetti Prima Di Utilizzare Cloud Manager{#understanding-concepts-before-using-cloud-manager}

Questa sezione contiene concetti e terminologie che è utile conoscere prima di lavorare in Cloud Manager e illustra i seguenti argomenti:

* **Ambiente di distribuzione**
* **Repository del codice sorgente**
* **Sicurezza e privacy**
* **Panoramica sulla tubazione**
* **Risorse**

## Ambiente di distribuzione {#deployment-environment}

Potrebbe essere una novità di Adobe Experience Manager (AEM) 6.4 o è necessario effettuare l’aggiornamento ad AEM 6.4 Release.

Se non hai mai utilizzato AEM 6.4, hai già accesso a Cloud Manager.

Se sei già cliente, devi effettuare l’aggiornamento ad AEM 6.4 per poter accedere a Cloud Manager. Puoi iniziare a utilizzare Cloud Manager, dopo aver ricevuto l'URL e le credenziali dai Customer Success Engineers (CSE).

<!-- 

Comment Type: annotation
Last Modified By: ptager
Last Modified Date: 2018-05-02T17:19:24.147-0400

Section is redundant with the section in the Overview topic

 -->

## Repository del codice sorgente {#source-code-repository}

**Più Server** Git: In alcuni casi, i clienti avranno un repository Git esistente e desiderano continuare a utilizzarlo.

Per questi casi, è possibile utilizzare il supporto git per più repository remoti. Lo sviluppo quotidiano continuerebbe a verificarsi nel repository git. Quando si desidera una distribuzione, è sufficiente inviare il codice più recente al repository Git di Cloud Manager.

<!-- 

Comment Type: annotation
Last Modified By: ptager
Last Modified Date: 2018-05-02T17:20:46.002-0400

Looks like we lost some content, compared to the previous version

 -->

## Sicurezza e privacy {#security-and-privacy}

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-04-21T02:38:21.417-0400

Query for Brad B.

 -->

## Panoramica sulla tubazione {#pipeline-overview}

Cloud Manager supporterà un'unica pipeline per programma (definizione precedente) che gestisce le implementazioni in fase e produzione. ****

Il ramo git utilizzato per le distribuzioni di fase e produzione è master.

>[!NOTE]
>
>È consigliabile utilizzare master come ramo git per la fase e la produzione, ma è possibile utilizzare uno dei rami durante la configurazione della pipeline.

Il processo di tubazione singola è illustrato di seguito:

![](assets/screen_shot_2018-04-30at30318pm.png)

### Informazioni sul flusso {#understanding-the-flow}

Puoi configurare la pipeline dalla [!UICONTROL Pipeline Settings] sezione dall’interfaccia utente di Cloud Manager.

Fai riferimento a [Utilizzo di Cloud Manager,](hhttps://helpx.adobe.com/experience-manager/cloud-manager/using/using-cloud-manager.html) per ulteriori informazioni.

Gestione distribuzione è responsabile della configurazione della pipeline, ovvero:

* assegnazione di un ramo applicazione
* assegnazione di ambienti di distribuzione
* definizione delle opzioni di test

In questo caso, è innanzitutto necessario selezionare un ramo dal relativo repository git. Quindi, definire il trigger che avvierà la pipeline.

Quindi, potete definire i parametri che controllano la distribuzione di produzione.

Infine, sarete in grado di configurare i parametri del test delle prestazioni.

>[!NOTE]
>
>Per informazioni sulla configurazione del comportamento e delle preferenze per la pipeline, consulta **Configurazione della pipeline** in [Utilizzo di Cloud Manager](using-cloud-manager.md).

### Risorse {#help-resources}

Per assistenza, contattate il tecnico del successo dei servizi gestiti di Adobe.

### Passaggi successivi {#the-next-steps}

Ora hai una migliore comprensione dei concetti di Cloud Manager.

Per configurare il progetto, l'ambiente e il team (utenti e ruoli), consulta [Configurazione delle configurazioni generali per Cloud Manager](setting-configurations-for-cloud-manager.md).
