---
title: Configurare la pipeline CI/CD
seo-title: Configure your CI/CD Pipeline
description: Segui questa pagina per configurare le impostazioni della pipeline da Cloud Manager.
seo-description: Before you start to deploy your code, you must configure your pipeline settings from the AEM Cloud Manager.
uuid: 35fd56ac-dc9c-4aca-8ad6-36c29c4ec497
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
content-type: reference
discoiquuid: ba6c763a-b78a-439e-8c40-367203a719b3
feature: CI-CD Pipeline
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
source-git-commit: fd172a7168074630e85f3b110e032f783d39ddca
workflow-type: tm+mt
source-wordcount: '1491'
ht-degree: 1%

---

# Configurare la pipeline CI/CD {#configure-your-ci-cd-pipeline}

>[!NOTE]
>Per informazioni su come configurare la pipeline CI/CD per Cloud Manager in AEM as a Cloud Service, consulta [qui](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=en#using-cloud-manager).

La pagina seguente spiega come configurare la **pipeline**. Per ulteriori informazioni concettuali sul funzionamento della pipeline, consulta la [panoramica della pipeline CI/CD](ci-cd-pipeline.md) .

## Tutorial video {#video-tutorial-one}

### Configurazione della pipeline in Cloud Manager {#config-pipeline-video}

La configurazione della pipeline di produzione CI/CD definisce il trigger che avvierà la pipeline, i parametri che controllano la distribuzione di produzione e i parametri del test delle prestazioni.

>[!VIDEO](https://video.tv.adobe.com/v/26314/)


## Informazioni sul flusso {#understanding-the-flow}

Puoi configurare la pipeline dalla sezione **Pipeline Settings (Impostazioni pipeline)** dell’interfaccia utente di [!UICONTROL Cloud Manager].

Gestione distribuzione è responsabile della configurazione della pipeline. In questo modo, seleziona prima un ramo dal **Archivio Git**. La configurazione della pipeline consiste in:

* definizione del trigger che avvierà la pipeline.
* definizione dei parametri che controllano la distribuzione di produzione.
* configurazione dei parametri del test delle prestazioni.

## Impostazione della pipeline {#setting-up-the-pipeline}

>[!CAUTION]
>
>Impossibile impostare la pipeline finché l’archivio Git non dispone di almeno un ramo e [Configurazione programma](setting-up-program.md) non è completato.

Prima di iniziare a distribuire il codice, devi configurare le impostazioni della pipeline da [!UICONTROL Cloud Manager].

>[!NOTE]
>
>È possibile modificare le impostazioni della pipeline dopo la configurazione iniziale.

## Aggiunta di una nuova pipeline di produzione dalla scheda Pipelines {#adding-production-pipeline}

Dopo aver configurato il programma e disporre di almeno un ambiente utilizzando l’interfaccia utente [!UICONTROL Cloud Manager], puoi aggiungere una pipeline di produzione.

Segui questi passaggi per configurare il comportamento e le preferenze per la pipeline di produzione:

1. Passa alla scheda **Pipelines** dalla pagina **Panoramica del programma** .

1. Fai clic su **+Aggiungi** e seleziona **Aggiungi pipeline di produzione**.

   ![](/help/using/assets/configure-pipelines/add-prod1.png)

1. **Viene visualizzata la finestra di dialogo Aggiungi** pipeline di produzione .

   1. Immettere il nome della pipeline. È possibile scegliere il **Repository** e il **Ramo Git**.

      ![](/help/using/assets/configure-pipelines/add-prod2.png)

   1. È possibile impostare **Trigger distribuzione** e **Comportamento errore importante** da **Opzioni di distribuzione**.

      ![](/help/using/assets/configure-pipelines/add-prod3.png)


      Puoi definire il trigger per avviare la pipeline:

      * **Manuale** : utilizzando l’interfaccia utente si avvia manualmente la pipeline.
      * **In Modifiche Git** : avvia la pipeline CI/CD ogni volta che vengono aggiunti dei commit al ramo Git configurato. Anche se selezioni questa opzione, puoi sempre avviare la pipeline manualmente.

         >[!NOTE]
         >Durante la configurazione o la modifica della pipeline, Deployment Manager ha la possibilità di definire il comportamento della pipeline quando si verifica un errore importante in uno qualsiasi dei gate di qualità.
      Questo è utile per i clienti che desiderano processi più automatizzati. Le opzioni disponibili sono:

      * **Chiedi ogni volta**  - Questa è l&#39;impostazione predefinita e richiede un intervento manuale su qualsiasi errore importante.
      * **Annulla immediatamente** : se selezionata, la pipeline verrà annullata ogni volta che si verifica un errore importante. In sostanza, questo sta simulando un utente che rifiuta manualmente ogni errore.
      * **Approva immediatamente** : se selezionata, la pipeline procede automaticamente ogni volta che si verifica un errore importante. In sostanza, questo sta simulando un utente che approva manualmente ogni errore.
   1. Selezionare le **Opzioni di distribuzione**.

      ![](/help/using/assets/configure-pipelines/add-prod4.png)

      * **L&#39;approvazione dopo la distribuzione delle fasi** funziona in modo simile all&#39;approvazione prima dell&#39;implementazione di produzione, ma avviene immediatamente dopo la fase di distribuzione dello stadio, ovvero prima che venga eseguito un test, rispetto all&#39;approvazione prima dell&#39;implementazione di produzione, che viene eseguita dopo il completamento di tutti i test.

      * **Salta il bilanciamento del carico**
   1. Seleziona **Configurazioni Dispatcher** per Stage. Inserisci il percorso, seleziona l’azione da **Tipo**, quindi fai clic su **Aggiungi percorso**. Puoi specificare fino a 100 percorsi per ambiente.

      ![](/help/using/assets/configure-pipelines/dispatcher-stage.png)

   1. Seleziona le **Opzioni di distribuzione** per Produzione. Ora puoi definire i parametri che controllano l’implementazione di produzione. Le tre opzioni disponibili sono le seguenti:

      * **Utilizzare l&#39;approvazione Go Live**  - Una distribuzione deve essere approvata manualmente da un proprietario business, da un project manager o da un manager di distribuzione tramite l&#39; [!UICONTROL Cloud Manager] interfaccia utente.
      * **Utilizzare CSE Oversight** : un CSE è impegnato per avviare effettivamente l’implementazione. Durante la configurazione della pipeline o la modifica quando CSE Oversight è abilitato, Deployment Manager può selezionare:

      * **Qualsiasi caso**: si riferisce a qualsiasi CSE disponibile
      * **Caso**: si riferisce a un CSE specifico assegnato al cliente o al relativo backup, se il CSE è fuori sede

      * **Pianificata** : questa opzione consente all&#39;utente di abilitare la distribuzione di produzione pianificata.

         >[!NOTE]
         >Se è selezionata l’opzione **Pianificato** , puoi pianificare la distribuzione di produzione nella pipeline **dopo** la distribuzione dell’area di visualizzazione (e **Usa approvazione GoLive**, se abilitata) in modo da attendere che venga impostata una pianificazione. L’utente può anche scegliere di eseguire immediatamente la distribuzione di produzione.
         >
         >Fai riferimento a [Distribuisci il codice](deploying-code.md) per impostare la pianificazione della distribuzione o eseguire la produzione immediatamente.
   1. Imposta le **Configurazioni del dispatcher** per la produzione. Inserisci il percorso, seleziona l’azione da **Tipo**, quindi fai clic su **Aggiungi percorso**. Puoi specificare fino a 100 percorsi per ambiente.

      ![](/help/using/assets/configure-pipelines/dispatcher-prod.png)

      In qualità di gestore dell’implementazione, puoi configurare un set di percorsi di contenuto che saranno **invalidati** o **scaricati** dalla cache del Dispatcher AEM per le istanze di pubblicazione, durante l’impostazione o la modifica della pipeline.

      È possibile configurare un set separato di percorsi per la distribuzione Stage e Production. Se configurate, queste azioni della cache verranno eseguite come parte del passaggio della pipeline di distribuzione, subito dopo la distribuzione di eventuali pacchetti di contenuto. Queste impostazioni utilizzano il comportamento standard AEM Dispatcher: l’opzione Annulla convalida esegue un’invalidazione della cache, simile a quando il contenuto viene attivato dall’autore alla pubblicazione; flush esegue un&#39;eliminazione della cache.

      In generale, l’utilizzo dell’azione di annullamento della validità è preferibile, ma in alcuni casi può essere richiesto lo scaricamento, soprattutto quando si utilizzano le librerie client di HTML.

      >[!NOTE]
      >
      >Fai riferimento a [Panoramica di Dispatcher](dispatcher-configurations.md) per ulteriori informazioni sul caching di Dispatcher.





1. Fai clic su **Continua** dopo aver selezionato tutte le opzioni.

1. Seleziona le opzioni dal passaggio **Test stage** . Puoi configurare i test delle prestazioni *AEM Sites* e *AEM Assets* in base ai prodotti per i quali hai concesso la licenza. Per ulteriori informazioni, consulta [Test delle prestazioni](understand-your-test-results.md#performance-testing) .

   1. Seleziona le opzioni da **Distribuzione dei contenuti dei siti/Peso del caricamento distribuito**. Per ulteriori informazioni, consulta [AEM Sites in Performance Testing](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#aem-sites) .

      ![](/help/using/assets/configure-pipelines/add-prod5.png)

   1. Seleziona le opzioni da **Distribuzione dei test di prestazioni delle risorse**. Per ulteriori informazioni, consulta [AEM Assets in Performance Testing](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#aem-assets) .

      ![](/help/using/assets/configure-pipelines/add-prod6.png)

1. Fai clic su **Salva** per completare l’aggiunta della pipeline di produzione.

### Modifica di una pipeline di produzione {#editing-prod-pipeline}

Puoi modificare le configurazioni della pipeline dalla pagina **Panoramica del programma** .

Per modificare la pipeline configurata, effettua le seguenti operazioni:

1. Passa alla scheda **Pipelines** dalla pagina **Panoramica del programma** .

1. Fai clic su **..** dalla scheda **Pipelines** e fai clic su **Modifica**, come illustrato nella figura seguente.


1. Viene visualizzata la finestra di dialogo **Modifica pipeline di produzione**.

   1. La scheda **Configurazione** ti consente di aggiornare il **Nome pipeline**, **Trigger distribuzione** e **Comportamento di errore delle metriche importanti**.

      >[!NOTE]
      >Per informazioni su come aggiungere e gestire archivi in Cloud Manager, consulta [Aggiunta e gestione di archivi](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) .


   1. La scheda **Origine** offre un’opzione per selezionare o deselezionare le opzioni **Pausa prima della distribuzione in Produzione** e **Pianificata** da **Opzioni di distribuzione di produzione**.


   1. L’opzione **Audit esperienze** consente di aggiornare o aggiungere nuove pagine.


1. Una volta completata la modifica della pipeline, fai clic su **Aggiorna** .

1. Fai clic su **Imposta pipeline** per impostare e configurare la pipeline.

   ![](assets/Setup-Pipeline.png)




## Solo pipeline non di produzione e di qualità del codice

Oltre alla pipeline principale che viene implementata in fase e produzione, i clienti possono impostare pipeline aggiuntive, denominate **Non-Production Pipelines**. Queste pipeline eseguono sempre i passaggi di creazione e qualità del codice. Facoltativamente, possono anche distribuire in ambiente Adobe Managed Services.

## Tutorial video {#video-tutorial-two}

### Pipelines solo per la qualità del codice e non di produzione di Cloud Manager {#non-prod-video}

Le pipeline CI/CD non di produzione sono suddivise in due categorie: pipeline di qualità del codice e pipeline di distribuzione. La qualità del codice pipeline tutto il codice da un ramo Git alla creazione ed è valutata in base alla scansione della qualità del codice di Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/26316/)

### Aggiunta di una pipeline non di produzione {#add-non-production-pipeline}

Nella schermata iniziale, queste pipeline sono elencate in una nuova scheda:

1. Accedi alla scheda **Pipelines** dalla schermata iniziale di Cloud Manager. Fai clic su **+Aggiungi** e seleziona **Aggiungi pipeline non di produzione**.

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. **Viene visualizzata la finestra di dialogo Aggiungi**  pipeline non di produzione. Selezionare il tipo di pipeline che si desidera creare, ovvero **Pipeline di qualità del codice** o **Pipeline di distribuzione**.

   Inoltre, è possibile impostare **Trigger distribuzione** e **Comportamento errore importante** da **Opzioni di distribuzione**. Fai clic su **Continua**.

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add2.png)


1. La pipeline non di produzione appena creata viene ora visualizzata nella scheda **Pipelines** .

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add4.png)


   La pipeline viene visualizzata sulla scheda nella schermata iniziale con tre azioni, come illustrato di seguito:

   * **Aggiungi** : consente di aggiungere una nuova pipeline.
   * **Accesso a informazioni sul repository** : consente all’utente di ottenere le informazioni necessarie per accedere all’archivio Git di Cloud Manager.
   * **Ulteriori informazioni** : descrive la risorsa della documentazione della pipeline CI/CD.

### Modifica di una pipeline non di produzione {#editing-nonprod-pipeline}

Puoi modificare le configurazioni della pipeline dalla **scheda Pipelines** dalla pagina **Panoramica del programma** .

Per modificare la pipeline non di produzione configurata, effettua le seguenti operazioni:

1. Passa alla scheda **Pipelines** dalla pagina **Panoramica del programma** .

1. Seleziona la pipeline non di produzione e fai clic su **..**. Fai clic su **Modifica**, come illustrato nella figura seguente.

   ![](/help/using/assets/configure-pipelines/non-prod-pipeline-edit1.png)

1. Viene visualizzata la finestra di dialogo **Modifica pipeline di produzione** che consente di aggiornare **Nome pipeline**, **Repository**, **Ramo Git**, **Trigger distribuzione** e **Comportamento errore metriche importanti**.

   ![](/help/using/assets/configure-pipelines/non-prod-pipeline-edit2.png)

   >[!NOTE]
   >Per informazioni su come aggiungere e gestire archivi in Cloud Manager, consulta [Aggiunta e gestione di archivi](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) .


1. Fai clic su **Aggiorna** una volta completata la modifica della pipeline non di produzione.


## Passaggi successivi {#the-next-steps}

Dopo aver configurato la pipeline, devi distribuire il codice.

Per ulteriori informazioni, consulta [Implementare il codice](deploying-code.md) .
