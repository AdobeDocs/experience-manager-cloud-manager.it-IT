---
title: Concetti fondamentali prima di usare Cloud Manager
seo-title: Concetti fondamentali prima di usare Cloud Manager
description: 'null'
seo-description: 'null'
page-status-flag: never-activated
uuid: 55 cc 551 a-e 812-4102-96 c 8-13 d 2 cdd 79 c 84
contentOwner: jsyal
discoiquuid: c 3 fd 3 f 4 e -0 b 57-4377-b 923-a 440 c 74773 d 8
preview: vero
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Concetti fondamentali prima di usare Cloud Manager{#understanding-concepts-before-using-cloud-manager}

Questa sezione fornisce concetti e termini di terminazione utili prima di utilizzare Cloud Manager e illustra i seguenti argomenti:

* **Ambiente di distribuzione**
* **Archivio codice sorgente**
* **Protezione e privacy**
* **Panoramica della pipeline**
* **Risorse di aiuto**

## Ambiente di distribuzione {#deployment-environment}

Potresti essere nuovo in Adobe Experience Manager (AEM) 6.4 o richiedere un aggiornamento a AEM 6.4.

Se non sei nuovo di AEM 6.4, hai già accesso a Cloud Manager.

Se siete già clienti, dovete effettuare l&#39;aggiornamento ad AEM 6.4 per accedere a Cloud Manager. Puoi iniziare a utilizzare Cloud Manager, una volta ricevuti URL e credenziali da Customer Success Engineers (CSE).

<!-- 

Comment Type: annotation
Last Modified By: ptager
Last Modified Date: 2018-05-02T17:19:24.147-0400

Section is redundant with the section in the Overview topic

 -->

## Archivio codice sorgente {#source-code-repository}

**Più server Git**: In alcuni casi, i clienti dispongono di un archivio Git esistente e dovranno continuare a utilizzarlo.

In questi casi, è possibile utilizzare il supporto git per più archivi remoti. Lo sviluppo giorno-giorno continua a verificarsi nella directory archivio git. Quando si desidera distribuire una distribuzione, è sufficiente inviare il codice più recente all&#39;archivio git di Experience Manager.

<!-- 

Comment Type: annotation
Last Modified By: ptager
Last Modified Date: 2018-05-02T17:20:46.002-0400

Looks like we lost some content, compared to the previous version

 -->

## Protezione e privacy {#security-and-privacy}

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-04-21T02:38:21.417-0400

Query for Brad B.

 -->

## Panoramica della pipeline {#pipeline-overview}

Cloud Manager supporterà una singola pipeline per programma (definizione sopra) che gestisce le distribuzioni all&#39;area di visualizzazione e alla produzione. ****

Il ramo git utilizzato per le distribuzioni di fase e di produzione è principale.

>[!NOTE]
>
>È consigliabile utilizzare la mastro come ramo git per l&#39;area di visualizzazione e la produzione, ma potete utilizzare qualsiasi ramo durante la configurazione della pipeline.

Il processo di pipeline singola è illustrato di seguito:

![](assets/screen_shot_2018-04-30at30318pm.png)

### Informazioni sul flusso {#understanding-the-flow}

Puoi configurare la pipeline dalla [!UICONTROL Pipeline Settings] sezione dell&#39;interfaccia utente di Cloud Manager.

Per ulteriori informazioni, consulta [Utilizzo](hhttps://helpx.adobe.com/experience-manager/cloud-manager/using/using-cloud-manager.html) di Cloud Manager.

Gestione distribuzione è responsabile della configurazione della pipeline, ovvero:

* assegnazione ramo applicazione
* assegnazione di ambienti di distribuzione
* definizione delle opzioni di test

In tal modo, selezionate innanzitutto un ramo dal relativo repository git. Quindi, definite l&#39;attivatore che avvia la pipeline.

Successivamente, potete definire i parametri che controllano la distribuzione di produzione.

Infine, potrete configurare i parametri di test delle prestazioni.

>[!NOTE]
>
>Per informazioni sulla configurazione del comportamento e delle preferenze per la pipeline, consulta **Configurazione della** sezione Pipeline in [Utilizzo di Cloud Manager](using-cloud-manager.md).

### Risorse di aiuto {#help-resources}

Contatta l&#39;ingegnere Customer Success Engineering di Adobe Managed Services per assistenza.

### Passaggi successivi {#the-next-steps}

Ora è meglio comprendere i concetti di Cloud Manager.

Per configurare il progetto, l&#39;ambiente e il team (utenti e ruoli), fate riferimento [a Configurazione configurazioni generali per Cloud Manager](setting-configurations-for-cloud-manager.md).
