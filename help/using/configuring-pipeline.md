---
title: Configurare la pipeline CI/CD
seo-title: Configurare la pipeline CI/CD
description: Segui questa pagina per configurare le impostazioni della pipeline da Cloud Manager.
seo-description: 'Prima di iniziare a distribuire il codice, devi configurare le impostazioni della pipeline da AEM Cloud Manager. '
uuid: 35fd56ac-dc9c-4aca-8ad6-36c29c4ec497
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
content-type: reference
discoiquuid: ba6c763a-b78a-439e-8c40-367203a719b3
translation-type: tm+mt
source-git-commit: 5542942da33efc2926e62cce00ea39e3c65b3e16
workflow-type: tm+mt
source-wordcount: '1776'
ht-degree: 2%

---


# Configurare la pipeline CI/CD {#configure-your-ci-cd-pipeline}

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

### Configurazione delle impostazioni della pipeline da [!UICONTROL Cloud Manager] {#configuring-the-pipeline-settings-from-cloud-manager}

Una volta configurato il programma utilizzando l’interfaccia utente [!UICONTROL Cloud Manager], è possibile impostare la pipeline.

Per configurare il comportamento e le preferenze per la pipeline, effettua le seguenti operazioni:

1. Fai clic su **Imposta pipeline** per impostare e configurare la pipeline.

   ![](assets/Setup-Pipeline.png)

1. Viene visualizzata la schermata **Pipeline di installazione**.

   La procedura guidata in tre passaggi consente di configurare l&#39;ambiente **Branch**, **Environments** e **Testing**.
Seleziona il ramo Git e fai clic su **Avanti**.

   >[!NOTE]
   >
   >I rami trovati nell’archivio Git sono collegati al tuo programma.


1. Accedi alla scheda **Ambienti** per selezionare le opzioni **Stage** e **Produzione** .

   Puoi definire il trigger per avviare la pipeline:

   * **In Modifiche Git** : avvia la pipeline CI/CD ogni volta che vengono aggiunti dei commit al ramo Git configurato. Anche se selezioni questa opzione, puoi sempre avviare la pipeline manualmente.
   * **Manuale** : utilizzando l’interfaccia utente si avvia manualmente la pipeline.

   Durante la configurazione o la modifica della pipeline, Deployment Manager ha la possibilità di definire il comportamento della pipeline quando si verifica un errore importante in uno qualsiasi dei gate di qualità come la qualità del codice, il test di sicurezza e il test delle prestazioni.

   Questo è utile per i clienti che desiderano processi più automatizzati. Le opzioni disponibili sono:

* **Chiedi ogni volta**  - Questa è l&#39;impostazione predefinita e richiede un intervento manuale su qualsiasi errore importante.
* **Annulla immediatamente** : se selezionata, la pipeline verrà annullata ogni volta che si verifica un errore importante. In sostanza, questo sta simulando un utente che rifiuta manualmente ogni errore.
* **Approva immediatamente** : se selezionata, la pipeline procede automaticamente ogni volta che si verifica un errore importante. In sostanza, questo sta simulando un utente che approva manualmente ogni errore.

   Ora puoi definire i parametri che controllano l’implementazione di produzione. Le tre opzioni disponibili sono le seguenti:

* **Utilizzare l&#39;approvazione Go Live**  - Una distribuzione deve essere approvata manualmente da un proprietario business, da un project manager o da un manager di distribuzione tramite l&#39; [!UICONTROL Cloud Manager] interfaccia utente.
* **Utilizzare CSE Oversight** : un CSE è impegnato per avviare effettivamente l’implementazione. Durante la configurazione della pipeline o la modifica quando CSE Oversight è abilitato, Deployment Manager può selezionare:

   * **Qualsiasi caso**: si riferisce a qualsiasi CSE disponibile
   * **Caso**: si riferisce a un CSE specifico assegnato al cliente o al relativo backup, se il CSE è fuori sede

* **Pianificata** : questa opzione consente all&#39;utente di abilitare la distribuzione di produzione pianificata.

>[!NOTE]
>
>Se è selezionata l’opzione **Pianificato** , puoi pianificare la distribuzione di produzione nella pipeline **dopo** la distribuzione dell’area di visualizzazione (e **Usa approvazione GoLive**, se abilitata) in modo da attendere che venga impostata una pianificazione. L’utente può anche scegliere di eseguire immediatamente la distribuzione di produzione.
>
>Fai riferimento a [**Distribuisci il codice**](deploying-code.md) per impostare la pianificazione della distribuzione o eseguire la produzione immediatamente.

![](assets/configure-pipeline-new.png)

>[!NOTE]
>
>L’opzione **Usa controllo CSE** non è disponibile per tutti i clienti.

**Approva dopo la distribuzione dello stage**

È disponibile un passaggio facoltativo **Approva dopo la distribuzione della fase** che può essere configurato nella pipeline di produzione.
Questa opzione è abilitata in una nuova opzione nella schermata **Modifica pipeline** :

![](assets/post_deployment1.png)

Viene quindi visualizzato come un passaggio separato durante l’esecuzione della pipeline:

![](assets/post_deployment2.png)

>[!NOTE]
>
>**L&#39;approvazione dopo la distribuzione delle fasi** funziona in modo simile all&#39;approvazione prima dell&#39;implementazione di produzione, ma avviene immediatamente dopo la fase di distribuzione dello stadio, ovvero prima che venga eseguito un test, rispetto all&#39;approvazione prima dell&#39;implementazione di produzione, che viene eseguita dopo il completamento di tutti i test.

**Annullamento della validità di Dispatcher**

In qualità di gestore dell’implementazione, puoi configurare un set di percorsi di contenuto che saranno **invalidati** o **scaricati** dalla cache del Dispatcher AEM per le istanze di pubblicazione, durante l’impostazione o la modifica della pipeline.

È possibile configurare un set separato di percorsi per la distribuzione Stage e Production. Se configurate, queste azioni della cache verranno eseguite come parte del passaggio della pipeline di distribuzione, subito dopo la distribuzione di eventuali pacchetti di contenuto. Queste impostazioni utilizzano il comportamento standard AEM Dispatcher: l’opzione Annulla convalida esegue un’invalidazione della cache, simile a quando il contenuto viene attivato dall’autore alla pubblicazione; flush esegue un&#39;eliminazione della cache.

In generale, l’utilizzo dell’azione di annullamento della validità è preferibile, ma in alcuni casi può essere richiesto lo scaricamento, soprattutto quando si utilizzano AEM librerie client HTML.

>[!NOTE]
>
>Fai riferimento a [Panoramica di Dispatcher](dispatcher-configurations.md) per ulteriori informazioni sul caching di Dispatcher.

Per configurare gli invalidamenti del Dispatcher, effettua le seguenti operazioni:

1. Fai clic su **Configura** nell’intestazione Configurazione del Dispatcher

   ![](assets/image2018-8-7_14-53-24.png)

1. Inserisci il percorso, seleziona l’azione da **Tipo**, quindi fai clic su **Aggiungi**. Puoi specificare fino a 100 percorsi per ambiente. Dopo aver aggiunto i percorsi, fai clic su **Applica**.

   ![](assets/image2018-8-7_14-58-11.png)

1. Una volta tornati alla pagina **Impostazioni pipeline**, viene visualizzato un riepilogo aggiornato delle selezioni.

   Fai clic su **Salva** per mantenere questa configurazione.

   ![](assets/image2018-8-7_15-4-30.png)


1. Accedi alla scheda **Testing** per definire i criteri di test per il programma.

   Ora puoi configurare i parametri del test delle prestazioni.

   Puoi configurare i test delle prestazioni *AEM Sites* e *AEM Assets* in base ai prodotti per i quali hai concesso la licenza.

   **AEM Sites:**

   Cloud Manager esegue test delle prestazioni per i programmi AEM Sites richiedendo pagine (come utente non autenticato per impostazione predefinita) sul server di pubblicazione dell’area di visualizzazione per un periodo di test di 30 minuti e misurando il tempo di risposta per ciascuna pagina e varie metriche a livello di sistema. Queste richieste vengono effettuate da un set di indirizzi noti e dedicati. Gli intervalli di indirizzi possono essere ottenuti dal tuo Customer Success Engineer o rappresentante di Adobe.

   Prima dell’inizio del periodo di test di 30 minuti, Cloud Manager eseguirà la ricerca per indicizzazione dell’ambiente Stage utilizzando un set di uno o più URL *seed* configurati dal Customer Success Engineer. A partire da questi URL, l’HTML di ogni pagina viene esaminato e i collegamenti vengono attraversati in modo molto semplice. Questo processo di ricerca per indicizzazione è limitato a un massimo di 5000 pagine. Le richieste del crawler hanno un timeout fisso di 10 secondi.

   Le pagine sono selezionate da tre **set di pagine**; puoi scegliere da uno a tutti e tre i set. La distribuzione del traffico si basa sul numero di set selezionati, ovvero, se sono selezionati tutti e tre, il 33% delle visualizzazioni di pagina totali viene indirizzato a ciascun set; se sono selezionati due, il 50% va a ciascun set; se ne è selezionato uno, il 100% del traffico viene indirizzato a tale set.

   Ad esempio, supponiamo che ci sia una divisione del 50%/50% tra le pagine popolari Live e le nuove pagine impostate (in questo esempio, non vengono utilizzate altre pagine Live) e che il set Nuove pagine contenga 3000 pagine. Il KPI per le visualizzazioni di pagina al minuto è impostato su 200. Nel periodo di prova di 30 minuti:

   * Ognuna delle 25 pagine del set di pagine popolari in tempo reale verrà visualizzata 120 volte - (200 * 0.5) / 25) * 30 = 120

   * Ognuna delle 3000 pagine del set di nuove pagine verrà visualizzata una volta - (200 * 0.5) / 3000) * 30 = 1

   ![](assets/Configuring_Pipeline_AEM-Sites.png)

   Per ulteriori informazioni, consulta [Test delle prestazioni autenticate](#authenticated-performance-testing) .

   **AEM Assets:**

   Cloud Manager esegue test delle prestazioni per i programmi AEM Assets caricando ripetutamente le risorse per un periodo di test di 30 minuti e misurando il tempo di elaborazione per ciascuna risorsa e varie metriche a livello di sistema. Questa funzionalità può caricare sia immagini che documenti PDF. La distribuzione del numero di risorse di ciascun tipo caricate al minuto viene impostata nella schermata Configurazione della pipeline o Modifica.

   Ad esempio, se si utilizza una suddivisione 70/30, come illustrato nella figura riportata di seguito. Le risorse caricate al minuto sono 10, verranno caricate 7 immagini al minuto e 3 documenti.

   ![](assets/Configuring_Pipeline_AEM-Assets.png)

   >[!NOTE]
   >
   >Esiste un’immagine e un documento PDF predefiniti, ma nella maggior parte dei casi i clienti desiderano caricare le proprie risorse. Questa operazione può essere eseguita dalla schermata Configurazione della pipeline o Modifica. Sono supportati i formati immagine più comuni, come JPEG, PNG, GIF e BMP, insieme ai file Photoshop, Illustrator e Postscript.

1. Fai clic su **Salva** per completare la configurazione del processo di pipeline.

   >[!NOTE]
   >
   >Inoltre, una volta impostata la pipeline, è comunque possibile modificare le impostazioni per la stessa tramite la sezione **Impostazioni pipeline di produzione** dell’interfaccia utente [!UICONTROL Cloud Manager].

   ![](assets/Production-Pipeline.png)

### Test delle prestazioni autenticati {#authenticated-performance-testing}

I clienti AMS con siti autenticati possono specificare un nome utente e una password che Cloud Manager utilizzerà per accedere al sito web durante il test delle prestazioni di Sites.

Il nome utente e la password sono specificati come [Variabili della pipeline](/help/using/build-environment-details.md#pipeline-variables) con i nomi `CM_PERF_TEST_BASIC_USERNAME` e `CM_PERF_TEST_BASIC_PASSWORD`.

Sebbene non sia strettamente richiesto, si consiglia di utilizzare il tipo di variabile stringa per il nome utente e il tipo di variabile secretString per la password. Se vengono specificati entrambi, ogni richiesta del crawler dei test delle prestazioni e degli utenti virtuali del test conterrà queste credenziali come autenticazione HTTP Basic.

Per impostare queste variabili utilizzando la [CLI di Cloud Manager](https://github.com/adobe/aio-cli-plugin-cloudmanager), esegui:

`$ aio cloudmanager:set-pipeline-variables <pipeline id> --variable CM_PERF_TEST_BASIC_USERNAME <username> --secret CM_PERF_TEST_BASIC_PASSWORD <password>`

## Solo pipeline non di produzione e di qualità del codice

Oltre alla pipeline principale che viene implementata in fase e produzione, i clienti possono impostare pipeline aggiuntive, denominate **Non-Production Pipelines**. Queste pipeline eseguono sempre i passaggi di creazione e qualità del codice. Facoltativamente, possono anche distribuire in ambiente Adobe Managed Services.

## Tutorial video {#video-tutorial-two}

### Pipeline solo per la qualità del codice e non di produzione di Cloud Manager {#non-prod-video}

Le pipeline CI/CD non di produzione sono suddivise in due categorie: pipeline di qualità del codice e pipeline di distribuzione. La qualità del codice pipeline tutto il codice da un ramo Git alla creazione ed è valutata in base alla scansione della qualità del codice di Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/26316/)

Nella schermata iniziale, queste pipeline sono elencate in una nuova scheda:

1. Accedi alla sezione **pipeline non di produzione** dalla schermata iniziale di Cloud Manager.

   ![](assets/Non-Production-Pipeline.png)

1. Fate clic sul pulsante Aggiungi per specificare il nome della pipeline, il tipo di pipeline e la diramazione Git.

   Inoltre, è possibile impostare il trigger di distribuzione e il comportamento di errore importante dalle opzioni della pipeline.

   ![](assets/non-prod-pipe.png)

1. Fai clic su **Salva** e la pipeline viene visualizzata sulla scheda nella schermata iniziale con tre azioni:

   * **Modifica** : consente di modificare le impostazioni della pipeline
   * **Dettaglio** : visualizza l’ultima esecuzione della pipeline (se presente)
   * **Build** : consente di passare alla pagina di esecuzione dalla quale è possibile eseguire la pipeline.

   ![](assets/Non-prod-2.png)

   >[!NOTE]
   >
   >Durante l’esecuzione della pipeline, viene visualizzato il passaggio corrente ed è disponibile solo l’azione **Dettagli** .

## Passaggi successivi {#the-next-steps}

Dopo aver configurato la pipeline, devi distribuire il codice.

Per ulteriori informazioni, consulta [Implementare il codice](deploying-code.md) .
