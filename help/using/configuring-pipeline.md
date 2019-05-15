---
title: Configurare la pipeline CI/CD
seo-title: Configurare la pipeline CI/CD
description: Segui questa pagina per configurare le impostazioni della pipeline da Cloud Manager.
seo-description: 'Prima di iniziare a distribuire il codice, devi configurare le impostazioni della pipeline da AEM Cloud Manager. '
uuid: 35 fd 56 ac-dc 9 c -4 aca -8 ad 6-36 c 29 c 4 ec 497
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: utilizzo
content-type: riferimento
discoiquuid: ba 6 c 763 a-b 78 a -439 e -8 c 40-367203 a 719 b 3
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Configurare la pipeline CI/CD {#configure-your-ci-cd-pipeline}

La pagina seguente spiega come configurare la **Pipeline**. Per esaminare ulteriori informazioni concettuali sul modo in cui la pipeline utilizza la panoramica della pipeline [CI/CD](ci-cd-pipeline.md).

## Informazioni sul flusso {#understanding-the-flow}

Puoi configurare la pipeline dalla sezione Impostazioni **pipeline** nell&#39; [!UICONTROL Cloud Manager] interfaccia utente.

Gestione distribuzione è responsabile della configurazione della pipeline. Per farlo, seleziona innanzitutto un ramo dall&#39;archivio **Git**. La configurazione pipeline consiste in:

* definizione dell&#39;attivatore che avvia la pipeline.
* definizione dei parametri che controllano la distribuzione della produzione.
* configurazione dei parametri di test delle prestazioni.

## Configurazione della pipeline {#setting-up-the-pipeline}

>[!CAUTION]
>
>La pipeline non può essere impostata finché l&#39;archivio Git non avrà almeno un ramo e [la configurazione](setting-up-program.md) Programma è completa.

Prima di iniziare a distribuire il codice, devi configurare le impostazioni della pipeline dall &#39; [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Potete modificare le impostazioni della pipeline dopo l&#39;impostazione iniziale.

### Configurazione delle impostazioni pipeline da [!UICONTROL Cloud Manager]{#configuring-the-pipeline-settings-from-cloud-manager}

Una volta configurato il programma utilizzando [!UICONTROL Cloud Manager] l&#39;interfaccia utente, è possibile configurare la pipeline.

Per configurare il comportamento e le preferenze per la pipeline, effettuate le seguenti operazioni:

1. Fai clic su **Pipeline pipeline** per configurare e configurare la pipeline.

   ![](assets/Configure_ci-cd-1.png)

1. **Viene visualizzata** la schermata Pipeline pipeline.

   La procedura guidata in tre fasi consente di configurare **i campi Ramo**, **Ambienti** e **Test** .
Selezionate il ramo Git e fate clic **su Avanti**.

   >[!NOTE]
   >
   >I rami presenti nell&#39;archivio Git sono collegati al programma.

   ![](assets/Configure_ci-cd-2.png)


1. Accedere alla scheda **Ambienti** per selezionare le opzioni **relative all&#39;area di visualizzazione** e **alla produzione** .

   Potete definire il trigger per avviare la pipeline:

   * **Su Git Changes** (Modifiche Git) avvia la pipeline CI/CD ogni volta che vengono aggiunti dei commenti al ramo git configurato. Anche se selezionate questa opzione, potete sempre avviare la pipeline manualmente.
   * **Manuale** : utilizzando l&#39;interfaccia utente viene avviata manualmente la pipeline.
   * **Pianificato** : questa opzione sarà disponibile a breve in una prossima release.
   Durante la configurazione o la modifica della pipeline, il Manager distribuzione ha l&#39;opzione di definire il comportamento della pipeline quando si riscontra un errore importante in qualsiasi gate di qualità come Qualità codice, Test di sicurezza e Test delle prestazioni.

   Ciò è utile per i clienti che desiderano processi più automatizzati. Le opzioni disponibili sono:

* **Chiedi sempre** : questa è l&#39;impostazione predefinita e richiede l&#39;intervento manuale su qualsiasi errore importante.
* **Errore immediatamente** : se selezionato, la pipeline verrà annullata ogni volta che si verifica un errore importante. In pratica viene emulato un utente che rifiuta manualmente ogni errore.
* **Continua immediatamente** : se selezionato, la pipeline si procederà automaticamente ogni volta che si verifica un errore importante. In pratica viene emulato un utente che approva manualmente ogni errore.

   Ora definite i parametri che controllano la distribuzione di produzione. Le tre opzioni disponibili sono le seguenti:

* **Usa approvazione** dal vivo: una distribuzione deve essere approvata manualmente da un proprietario aziendale, un manager progetto o un manager distribuzione tramite l&#39; [!UICONTROL Cloud Manager] interfaccia utente.
* **Utilizzo della Supervisione** CSE - Un CSE è coinvolto per avviare la distribuzione. Durante la configurazione della pipeline o la modifica quando è abilitata la funzione di ispezione CSE, Gestione distribuzione è in grado di selezionare:

   * **Qualsiasi CSE**: si riferisce a qualsiasi CSE disponibile
   * **My CSE**: si riferisce a una specifica CSE assegnata al cliente o al relativo backup, se il CSE è fuori ufficio

* **Pianificato** : questa opzione consente all&#39;utente di abilitare la distribuzione di produzione pianificata.

>[!NOTE]
>
>Se **è selezionata** l&#39;opzione Pianificate, potete pianificare la distribuzione di produzione al pipeline **dopo** la distribuzione dell&#39;area di visualizzazione (e **utilizzare golive Approval**, se questa è stata attivata) per attendere la configurazione di una pianificazione. L&#39;utente può anche scegliere di eseguire immediatamente la distribuzione di produzione.
>
>Consultate [**Implementare il codice**](deploying-code.md), per impostare la distribuzione o eseguire immediatamente la produzione.

![](assets/Configure_ci-cd-3.png)

>[!NOTE]
>
>L&#39;opzione **Use CSE Exchange** non è disponibile per tutti i clienti.

**Annullamento validità del dispatcher**

In qualità di Gestione distribuzione, potete configurare un set di percorsi che verranno **invalidati** o **scaricati** dalla cache di AEM Dispatcher, durante l&#39;impostazione o la modifica della pipeline.

Potete configurare un set di percorsi separati per la distribuzione di Stage e Produzione. Se configurate, queste azioni cache saranno eseguite come parte del passaggio della pipeline di distribuzione, subito dopo la distribuzione dei pacchetti di contenuto. Queste impostazioni utilizzano il comportamento standard di dispatcher AEM - invalidate esegue una verifica della cache, simile a quando il contenuto viene attivato dall&#39;autore per la pubblicazione; flush esegue un&#39;eliminazione cache.

In generale, l&#39;uso dell&#39;azione invalidate è preferibile, ma ci può essere un casi in cui l&#39;eliminazione è necessaria, soprattutto quando si utilizzano librerie client HTML.

>[!NOTE]
>
>Consultate Panoramica [del dispatcher](dispatcher-configurations.md) per ottenere ulteriori informazioni sul caching del dispatcher.

Per configurare le invalidazioni del dispatcher, effettuate le seguenti operazioni:

1. Fai clic su **Configura** nella intestazione Configurazione del dispatcher

   ![](assets/image2018-8-7_14-53-24.png)

1. Immettete il percorso, selezionate l&#39;azione da **Tipo** e fate clic **su Aggiungi**. Potete specificare fino a 100 percorsi per ambiente. Dopo aver aggiunto i percorsi, fate clic **su Applica**.

   ![](assets/image2018-8-7_14-58-11.png)

1. Una volta tornati nella pagina **Impostazioni pipeline,** vedrete un riepilogo aggiornato delle selezioni.

   Fate clic su **Salva** per mantenere questa configurazione.

   ![](assets/image2018-8-7_15-4-30.png)

1. Accedete alla **scheda Test** per definire i criteri di verifica per il programma.

   Ora potete configurare i parametri di test delle prestazioni.

   Puoi configurare *i test delle prestazioni di AEM Sites* e *AEM Assets* , a seconda dei prodotti con licenza.

   **AEM Sites:**

   Cloud Manager esegue test delle prestazioni per i programmi AEM Sites richiedendo pagine (come utente non autenticato) nel server di pubblicazione dell&#39;area di visualizzazione per un periodo di prova di 30 minuti e misurando il tempo di risposta per ogni pagina e diverse metriche a livello di sistema. Le pagine vengono selezionate tramite tre **set di pagine**; potete scegliere ovunque e in tutti e tre i set. La distribuzione del traffico è basata sul numero di set selezionati, ovvero se sono selezionati tutti e tre, il 33% delle visualizzazioni di pagina totale viene collocato verso ogni set; se sono selezionati due, 50% fa riferimento a ciascun set; Se è selezionata, il 100% del traffico passa a quel set.

   Ad esempio, supponiamo che esista una suddivisione tra le pagine Live Live e le nuove pagine (in questo esempio, altre Pagine live non utilizzate) e il set Nuove pagine contiene 3000 pagine. Le visualizzazioni di pagina per minuto KPI sono impostate su 200. Nel periodo di prova di 30 minuti:

   * Ciascuna delle 25 pagine del set Live Pages verrà reimpostata 240 volte - ((200 * 0.5)/ 25) * 30 = 120

   * Ciascuna delle 3000 pagine del set Nuove pagine verrà hit una volta - ((200 * 0.5)/ 3000) * 30 = 1
   ![](assets/Configuring_Pipeline_AEM-Sites.png)

   **AEM Assets:**

   Cloud Manager esegue test delle prestazioni per i programmi di Risorse AEM caricando ripetutamente le risorse per un periodo di prova di 30 minuti e misurando il tempo di elaborazione per ogni risorsa e diverse metriche a livello di sistema. Questa funzionalità può caricare immagini e documenti PDF. La distribuzione del numero di risorse di ciascun tipo viene caricata al minuto nella schermata Impostazione pipeline o Modifica.

   Ad esempio, se viene utilizzata una suddivisione 70/30, come mostrato nella figura seguente. Sono disponibili 10 risorse caricate al minuto, 7 immagini caricate al minuto e 3 documenti.

   ![](assets/Configuring_Pipeline_AEM-Assets.png)

   >[!NOTE]
   >
   >Esiste un&#39;immagine predefinita e un documento PDF, ma nella maggior parte dei casi i clienti dovranno caricare le proprie risorse. Questo può essere fatto dalla schermata Impostazione pipeline o Modifica. Sono supportati i formati di immagini comuni come JPEG, PNG, GIF e BMP con file Photoshop, Illustrator e Postscript.

1. Fate clic **su Salva** per completare la configurazione del processo di pipeline.

   >[!NOTE]
   >
   >Inoltre, una volta impostata la pipeline, potete comunque modificare le impostazioni con la sezione Impostazioni **pipeline** dall&#39; [!UICONTROL Cloud Manager] interfaccia utente.

   ![](assets/Configuring_Pipeline-Settings.png)

## Pipeline solo di produzione e non produzione

Oltre alla pipeline principale che distribuisce all&#39;area di visualizzazione e alla produzione, i clienti sono in grado di configurare altri gasini, definiti come pipeline **non di produzione**. Questi pipeline eseguono sempre i passaggi di creazione e qualità del codice. Possono anche distribuire nell&#39;ambiente dei servizi gestiti Adobe.

Nella schermata iniziale, questi pipeline sono elencati in una nuova scheda:

1. Accedere al **riquadro Non Production Pipeline** dalla schermata iniziale di Experience Manager.

   ![](assets/Configuring_Pipeline_Add-Production.png)

1. Fate clic sul pulsante Aggiungi per specificare il nome pipeline, il tipo pipeline e il ramo Git.

   Inoltre, potete anche configurare Attivazione distribuzione e Comportamento importante errori da Opzioni pipeline.

   ![](assets/Configuring_Pipeline_Add-Production2.png)

1. Fate clic **su Salva** e la pipeline viene visualizzata sulla scheda nella schermata iniziale con tre azioni:

   * **Modifica** : consente di modificare le impostazioni della pipeline
   * **Dettagli** : visualizza l&#39;ultima esecuzione della pipeline (se presente)
   * **Build** : passa alla pagina di esecuzione da cui può essere eseguita la pipeline
   ![](assets/Configuring_Pipeline_Add-Production3.png)

   >[!NOTE]
   >
   >Mentre la pipeline è in esecuzione, viene visualizzato il passaggio corrente e è disponibile solo l&#39;azione **Dettagli** .

## Passaggi successivi {#the-next-steps}

Una volta configurato il pipeline, devi distribuire il codice.

Per ulteriori informazioni, consulta [Distribuzione del codice](deploying-code.md) .
