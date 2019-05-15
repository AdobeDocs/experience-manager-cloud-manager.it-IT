---
title: Configurazione del programma
seo-title: Configurazione del programma
description: Dopo la registrazione, il proprietario dell'azienda dovrà effettuare una configurazione iniziale del programma.
seo-description: 'Dopo la registrazione, il proprietario dell''attività dovrà effettuare una determinata configurazione di Adobe AEM Cloud Manager. Ciò richiede l''impostazione della descrizione del programma e la definizione dei KPI che verranno utilizzati per il test delle prestazioni. '
uuid: 9 ecf 8743-1 f 5 a -4744-86 af-e 2256567642 f
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: getting-started
discoiquuid: c 2393540-e 852-4 f 7 c-aafd -1427209065 d 2
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Configurazione del programma {#setup-your-program}

Dopo la registrazione, il proprietario dell&#39;azienda dovrà completare alcune impostazioni iniziali del programma. Ciò richiede l&#39;impostazione della descrizione del programma e la definizione degli indicatori di prestazioni chiave (KPI) che verranno utilizzati per il test delle prestazioni. È possibile caricare una miniatura. Inoltre, il proprietario del business può configurare gli ambienti durante la configurazione del programma.

I KPI definiti fungono da linea di base per il test delle prestazioni che viene trasmesso ogni volta che la pipeline viene eseguita.

>[!NOTE]
>
>I KPI definiti sono misurati sui test eseguiti nell&#39;ambiente **dell&#39;area di visualizzazione** . In genere, questi KPI vengono ridotti in base alle capacità dell&#39;ambiente dell&#39;area di visualizzazione.
>
>Ad esempio, un utente prevede una media di 1000 visualizzazioni di pagina per minuto nel proprio **ambiente di produzione** e la presenza di quattro server di dispatcher/pubblicazione in produzione dovrebbe ridimensionare questo a 250 visualizzazioni di pagina al minuto (supponendo che l&#39;ambiente stage sia costituito da una sola coppia di server di dispatcher/pubblicazione).
>
>Inoltre, molti utenti dispongono di una rete CDN (Content Delivery Network), ad esempio Akamai o cloudfront davanti al loro ambiente di produzione. Poiché [!UICONTROL Cloud Manager] i test avvengono direttamente nell&#39;ambiente dell&#39;area di visualizzazione, la KPI deve riflettere solo il traffico previsto per passare attraverso la rete CDN, vale a dire la cache. In genere si tratta di un sottoinsieme relativamente piccolo del traffico di produzione totale.

## Utilizzo [!UICONTROL Cloud Manager] di Installazione del programma {#using-cloud-manager-to-setup-your-program}

Per configurare il programma e definire i KPI, effettuate le seguenti operazioni:

1. Click **Setup Program** to start the setup process in [!UICONTROL Cloud Manager].

   ![](assets/SetUpProgram1.png)

1. Nella schermata **Configurazione programma** sono visualizzate le informazioni sul programma.

1. Sono disponibili tre opzioni come **General**, **KPI** e **Provisioning** .

1. Nella **scheda Generale** , caricate una miniatura nel programma. Potete anche aggiungere una descrizione pertinente al programma.

   ![](assets/Setup_Program-General.png)

1. Sotto **KPI** potete definire i due KPI (aspettative per ogni distribuzione). I KPI separati vengono definiti per **AEM Sites** e **AEM Assets**. Potrete specificare i KPI per i prodotti con licenza.

   **AEM Sites**

   1. Qual è il decimo tempo di risposta percentile accettabile?

      * Valore consigliato - 3 secondi
   1. Quante visualizzazioni di pagina al minuto sono sotto il caricamento del picco?

      * Valore consigliato: 200 visualizzazioni di pagina al minuto
   **AEM Assets**

   Dalla sua versione iniziale, Cloud Manager è stato in grado di eseguire test delle prestazioni per i programmi AEM Sites. Con questa release, è stata aggiunta la funzionalità per eseguire test sulle prestazioni anche per programmi AEM Assets. Il test delle prestazioni delle risorse viene eseguito caricando ripetutamente le risorse in un periodo di prova di 30 minuti e misurando il tempo di elaborazione per ogni risorsa e diverse metriche a livello di sistema.
Durante la configurazione del programma, vengono specificati KPI specifici per risorse:

   * 95 ° percentile Tempo di elaborazione
   * Risorse caricate al minuto
   ![](assets/Setup_Program-KPIs.png)

1. In **Provisioning**, potete visualizzare o modificare la configurazione di provisioning per gli ambienti di produzione e non di produzione nel programma. Se per il programma è stata attivata l&#39;opzione Autoscena, **** visualizzerai Autoscena.

   >[!NOTE]
   >
   >* La funzionalità automatica è applicabile solo all&#39;ambiente di produzione e potrebbe non essere disponibile per tutti i programmi dei clienti.
   >* On-demand scaling is not available for this release of [!UICONTROL Cloud Manager].


   ![](assets/Setup_Program-Provisioning.png)

1. Fate clic **su Salva** per completare la procedura guidata di configurazione.

   >[!NOTE]
   >
   >Potete sempre modificare il programma una volta configurato il programma iniziale. Per ulteriori dettagli, segui i passaggi indicati di seguito.

## Modifica di un programma

1. Passa alla soluzione nella schermata iniziale di **Experience Manager** .

   ![](assets/SetUpProgram5.png)

1. Selezionate la soluzione e fate clic **su Modifica** per aggiornare o modificare il programma, come illustrato nella figura seguente.

   ![](assets/SetUpProgram6.png)

1. Viene visualizzata la schermata **Modifica programma** che consente di aggiornare o modificare il programma.

   ![](assets/Editing_Program-screen3.png)

## Passaggi successivi {#the-next-steps}

Se hai già impostato **la Pipeline**, l&#39;esecuzione successiva considera in account le impostazioni aggiornate. Se non hai ancora impostato la pipeline, segui i passaggi per impostare prima la pipeline.

Consultate [Configurare il pipeline CI/CD](https://helpx.adobe.com/experience-manager/cloud-manager/using/configuring-pipeline.html) per configurare la pipeline.
