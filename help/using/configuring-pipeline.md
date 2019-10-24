---
title: Configurare la pipeline CI/CD
seo-title: Configurare la pipeline CI/CD
description: Segui questa pagina per configurare le impostazioni della pipeline da Cloud Manager.
seo-description: 'Prima di iniziare a distribuire il codice, devi configurare le impostazioni della pipeline da AEM Cloud Manager. '
uuid: 35fd56ac-dc9c-4aca-8ad6-36c29c4ec497
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: utilizzo
content-type: reference
discoiquuid: ba6c763a-b78a-439e-8c40-367203a719b3
translation-type: tm+mt
source-git-commit: bc419b96554a40b84878140f8f532c9f4e10c9f3

---


# Configurare la pipeline CI/CD {#configure-your-ci-cd-pipeline}

Nella pagina seguente viene illustrato come configurare la **tubazione**. Per maggiori informazioni concettuali sul funzionamento della tubazione, consulta la panoramica [della pipeline](ci-cd-pipeline.md)CI/CD.

## Esercitazione video {#video-tutorial-one}

### Configurazione della pipeline in Cloud Manager {#config-pipeline-video}

La configurazione della pipeline di produzione CI/CD definisce il trigger che avvierà la pipeline, i parametri che controllano la distribuzione di produzione e i parametri di test delle prestazioni.

>[!VIDEO](https://video.tv.adobe.com/v/26314/?captions=ita)


## Informazioni sul flusso {#understanding-the-flow}

Potete configurare la tubazione dalla sezione Impostazioni **** tubazione nell’ [!UICONTROL Cloud Manager] interfaccia utente.

Gestione distribuzione è responsabile della configurazione della pipeline. In questo caso, selezionate prima un ramo dall'archivio **Git**. La configurazione della tubazione è costituita da:

* definizione del trigger che avvierà la pipeline.
* definizione dei parametri che controllano la distribuzione di produzione.
* configurazione dei parametri del test delle prestazioni.

## Impostazione della tubazione {#setting-up-the-pipeline}

>[!CAUTION]
>
>Impossibile impostare la pipeline finché l'archivio Git non dispone di almeno una diramazione e l'impostazione [del](setting-up-program.md) programma non è completa.

Prima di iniziare a distribuire il codice, devi configurare le impostazioni della pipeline dal [!UICONTROL Cloud Manager].

>[!NOTE]
>
>È possibile modificare le impostazioni della pipeline dopo la configurazione iniziale.

### Configurazione delle impostazioni della tubazione da [!UICONTROL Cloud Manager]{#configuring-the-pipeline-settings-from-cloud-manager}

Una volta configurato il programma utilizzando l' [!UICONTROL Cloud Manager] interfaccia utente, è possibile impostare la pipeline.

Per configurare il comportamento e le preferenze della pipeline, effettuate le seguenti operazioni:

1. Fate clic su **Imposta tubazione** per impostare e configurare la tubazione.

   ![](assets/Configure_ci-cd-1.png)

1. Viene visualizzata la schermata **Configurazione tubazione** .

   La procedura guidata in tre fasi consente di configurare l'ambiente **ramo**, **ambienti** e **test** .
Selezionate il ramo Git e fate clic su **Avanti**.

   >[!NOTE]
   >
   >Le filiali presenti nel repository Git sono collegate al programma.

   ![](assets/Configure_ci-cd-2.png)


1. Accedete alla scheda **Ambienti** per selezionare le opzioni **Stage** e **Produzione** .

   È possibile definire il trigger per avviare la pipeline:

   * **Su modifiche** Git - avvia la pipeline CI/CD ogni volta che vengono aggiunti impegni al ramo git configurato. Anche se selezionate questa opzione, potete sempre avviare la pipeline manualmente.
   * **Manuale** : l'utilizzo dell'interfaccia utente consente di avviare manualmente la pipeline.
   * **Pianificato** : questa opzione sarà disponibile a breve in una prossima release.
   Durante la configurazione o la modifica della pipeline, Gestione distribuzione ha la possibilità di definire il comportamento della pipeline quando si verifica un errore importante in una delle porte di qualità come Qualità del codice, Test di sicurezza e Test delle prestazioni.

   Questo è utile per i clienti che desiderano un maggior numero di processi automatizzati. Le opzioni disponibili sono:

* **Chiedi ogni volta** - Questa è l'impostazione predefinita e richiede l'intervento manuale su qualsiasi errore importante.
* **Errore immediato** - Se selezionato, la pipeline verrà annullata ogni volta che si verifica un errore importante. In pratica, questo consente di emulare manualmente un utente che rifiuta ogni errore.
* **Continua immediatamente** : se questa opzione è selezionata, la pipeline procederà automaticamente ogni volta che si verifica un errore importante. Si tratta essenzialmente di un'emulazione manuale di un utente che approva ogni errore.

   Ora definite i parametri che controllano la distribuzione di produzione. Le tre opzioni disponibili sono le seguenti:

* **Usa approvazione** Go Live - Una distribuzione deve essere approvata manualmente da un proprietario aziendale, da un project manager o da un manager distribuzione tramite l' [!UICONTROL Cloud Manager] interfaccia utente.
* **Usa CSE Oversight** : un CSE è impegnato per avviare effettivamente la distribuzione. Durante l'impostazione della pipeline o la modifica quando CSE Oversight è abilitato, Gestione distribuzione può selezionare:

   * **Eventuali CSE**: si riferisce a qualsiasi CSE disponibile
   * **CSE** personale: si riferisce a un caso specifico assegnato al cliente o al suo backup, se il caso è fuori ufficio

* **Pianificato** : questa opzione consente all'utente di abilitare la distribuzione di produzione pianificata.

>[!NOTE]
>
>Se è selezionata l'opzione **Pianificato** , potete pianificare la distribuzione di produzione nella pipeline **dopo** la distribuzione dell'area di visualizzazione (e **utilizzare l'opzione Approvazione** GoLive, se è stata attivata) in modo da attendere l'impostazione di una pianificazione. L'utente può anche scegliere di eseguire immediatamente la distribuzione di produzione.
>
>Fare riferimento a [**Distribuzione del codice**](deploying-code.md), per impostare la pianificazione della distribuzione o eseguire la produzione immediatamente.

![](assets/Configure_ci-cd-3.png)

>[!NOTE]
>
>L'opzione **Usa controllo** CSE non è disponibile per tutti i clienti.

**Approva dopo la distribuzione dello stage**

È disponibile un passaggio facoltativo **Approva dopo la distribuzione** dell'area di produzione che può essere configurato nella pipeline di produzione.
Questa opzione è attivata in una nuova opzione nella schermata di modifica **della** tubazione:

![](assets/post_deployment1.png)

Viene quindi visualizzata come un passaggio separato durante l'esecuzione della pipeline:

![](assets/post_deployment2.png)

>[!NOTE]
>
>**L'approvazione dopo la distribuzione** dello stage funziona in modo simile all'approvazione prima dell'implementazione della produzione, ma avviene immediatamente dopo il passaggio di distribuzione dello stadio, ovvero prima che venga eseguito un test, rispetto all'approvazione prima dell'implementazione della produzione, che viene fatta dopo che il test è stato completato.

**Annullamento convalida dispatcher**

In qualità di Gestione distribuzione, potete configurare un set di percorsi che verranno **invalidati** o **scaricati** dalla cache del dispatcher AEM, durante la configurazione o la modifica della pipeline.

Potete configurare un set di percorsi separato per la distribuzione di Stage e Produzione. Se configurate, queste azioni della cache verranno eseguite come parte del passaggio della pipeline di distribuzione, subito dopo la distribuzione di eventuali pacchetti di contenuto. Queste impostazioni utilizzano il comportamento standard di AEM Dispatcher. L'annullamento della validità esegue un'annullamento della validità della cache, simile a quando il contenuto viene attivato dall'autore alla pubblicazione; flush esegue un'eliminazione della cache.

In generale, l'utilizzo dell'azione di annullamento della validità è preferibile, ma in alcuni casi potrebbe essere necessario eseguire lo scaricamento, soprattutto quando si utilizzano le librerie client HTML di AEM.

>[!NOTE]
>
>Fare riferimento a [Dispatcher Overview (Panoramica](dispatcher-configurations.md) del dispatcher) per ulteriori informazioni sul caching del dispatcher.

Per configurare le invalide del dispatcher, effettuate le seguenti operazioni:

1. Fate clic su **Configura** sotto l’intestazione Configurazione dispatcher

   ![](assets/image2018-8-7_14-53-24.png)

1. Immettete il percorso, selezionate l’azione da **Tipo** e fate clic su **Aggiungi**. Potete specificare fino a 100 percorsi per ambiente. Dopo aver aggiunto i percorsi, fate clic su **Applica**.

   ![](assets/image2018-8-7_14-58-11.png)

1. Una volta visualizzata nuovamente la pagina Impostazioni **** tubazione, viene visualizzato un riepilogo aggiornato delle selezioni.

   Fate clic su **Salva** per mantenere la configurazione.

   ![](assets/image2018-8-7_15-4-30.png)


1. Accedete alla scheda **Test** per definire i criteri di test per il programma.

   Ora potete configurare i parametri del test delle prestazioni.

   Puoi configurare *AEM Sites* e *AEM Assets* Performance Testing, a seconda dei prodotti per i quali hai concesso la licenza.

   **AEM Sites:**

   Cloud Manager esegue il test delle prestazioni per i programmi AEM Sites richiedendo pagine (come utente non autenticato) sul server di pubblicazione dell’area di visualizzazione per un periodo di test di 30 minuti e misurando il tempo di risposta per ciascuna pagina e varie metriche a livello di sistema.Le pagine sono selezionate da tre set **di** pagine; potete scegliere da uno a tutti e tre i set. La distribuzione del traffico si basa sul numero di set selezionati, ossia, se tutti e tre i set sono selezionati, il 33% delle visualizzazioni di pagina totali viene indirizzato verso ciascun set; se sono selezionati due, il 50% va a ciascun set; se ne è selezionata una, il 100% del traffico arriva a quel set.

   Ad esempio, supponiamo che esista una divisione del 50%/50% tra le pagine Live popolari e le nuove pagine impostate (in questo esempio, non vengono utilizzate altre pagine Live) e che il set Nuove pagine contenga 3000 pagine. L'indicatore KPI per le visualizzazioni di pagina al minuto è impostato su 200. Nel periodo di prova di 30 minuti:

   * Ognuna delle 25 pagine del set Popular Live Pages verrà visualizzata 240 volte - (200 * 0.5) / 25) * 30 = 120

   * Ognuna delle 3000 pagine del set di nuove pagine verrà visualizzata una volta - (200 * 0,5) / 3000) * 30 = 1
   ![](assets/Configuring_Pipeline_AEM-Sites.png)

   **AEM Assets:**

   Cloud Manager esegue test delle prestazioni per i programmi AEM Assets caricando ripetutamente risorse per un periodo di test di 30 minuti e misurando il tempo di elaborazione per ciascuna risorsa, nonché varie metriche a livello di sistema. Questa funzione può caricare sia immagini che documenti PDF. La distribuzione del numero di risorse di ciascun tipo caricate al minuto viene impostata nella schermata Impostazione tubazione o Modifica.

   Ad esempio, se viene utilizzata una divisione 70/30, come illustrato nella figura riportata di seguito. Ci sono 10 risorse caricate al minuto, 7 immagini saranno caricate al minuto e 3 documenti.

   ![](assets/Configuring_Pipeline_AEM-Assets.png)

   >[!NOTE]
   >
   >Esiste un’immagine e un documento PDF predefiniti, ma nella maggior parte dei casi i clienti desiderano caricare le proprie risorse. Questa operazione può essere eseguita dalla schermata Configurazione tubazione o Modifica. Sono supportati i formati immagine più comuni, come JPEG, PNG, GIF e BMP, insieme ai file Photoshop, Illustrator e Postscript.

1. Fare clic su **Salva** per completare la configurazione del processo di pipeline.

   >[!NOTE]
   >
   >Inoltre, una volta impostata la pipeline, puoi comunque modificare le impostazioni per la stessa cosa utilizzando la sezione Impostazioni **pipeline di** produzione dall' [!UICONTROL Cloud Manager] interfaccia utente.

   ![](assets/Prod-Pipeline-Settings-Dialog.png)

## Tubazioni non di produzione e di qualità del codice

Oltre alla pipeline principale che viene implementata per fasi e produzione, i clienti sono in grado di impostare altri oleodotti, denominati **Non-Production Pipelines**. Tali pipeline eseguono sempre i passaggi di creazione e qualità del codice. Facoltativamente, possono anche essere distribuiti nell'ambiente Adobe Managed Services.

## Esercitazione video {#video-tutorial-two}

### Pipeline Solo Qualità Codice E Non Produzione Di Cloud Manager {#non-prod-video}

I gasdotti CI/CD non di produzione sono suddivisi in due categorie, i gasdotti Code Quality e i gasdotti di distribuzione. La qualità del codice distribuisce tutto il codice da un ramo Git per creare e per essere valutato in base alla scansione della qualità del codice di Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/26316/?captions=ita)

Nella schermata iniziale, queste condotte sono elencate in una nuova scheda:

1. Accedete alla sezione **Tubi** non di produzione dalla schermata iniziale di Cloud Manager.

   ![](assets/Configuring_Pipeline_Add-Production.png)

1. Fate clic sul pulsante Aggiungi per specificare il nome della tubazione, il tipo di tubazione e il ramo Git.

   Inoltre, puoi impostare l'attivatore di distribuzione e un importante comportamento di errore dalle opzioni della pipeline.

   ![](assets/Configuring_Pipeline_Add-Production2.png)

1. Fate clic su **Salva** e la pipeline viene visualizzata sulla scheda nella schermata iniziale con tre azioni:

   * **Modifica** : consente di modificare le impostazioni della pipeline
   * **Dettaglio** : visualizza l'ultima esecuzione della pipeline (se presente)
   * **Genera** : consente di passare alla pagina di esecuzione dalla quale è possibile eseguire la pipeline
   ![](assets/Configuring_Pipeline_Add-Production3.png)

   >[!NOTE]
   >
   >Durante l'esecuzione della pipeline, viene visualizzato il passaggio corrente ed è disponibile solo l'azione **Dettagli** .

## Passaggi successivi {#the-next-steps}

Dopo aver configurato la pipeline, è necessario distribuire il codice.

Per ulteriori informazioni, consulta [Distribuzione del codice](deploying-code.md) .
