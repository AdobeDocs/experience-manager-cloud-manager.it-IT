---
title: Configurare il programma
seo-title: Configurare il programma
description: Dopo l'imbarco, il proprietario dell'azienda dovrà effettuare una configurazione iniziale del programma.
seo-description: 'Dopo l''imbarco, il proprietario dell''azienda dovrà effettuare una configurazione iniziale  Adobe AEM Cloud Manager. Ciò comporta l''impostazione della descrizione del programma e la definizione dei KPI che verranno utilizzati per il test delle prestazioni. '
uuid: 9ecf8743-1f5a-4744-86af-e2256567642f
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: getting-started
discoiquuid: c2393540-e852-4f7c-aafd-1427209065d2
translation-type: tm+mt
source-git-commit: 6851884b08c0c0a971242a958f72a7673a1a1196
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Configurare il programma {#setup-your-program}

Dopo l&#39;imbarco, il proprietario dell&#39;azienda dovrà completare la configurazione iniziale del programma. Ciò comporta l&#39;impostazione della descrizione del programma e la definizione degli indicatori prestazioni chiave (KPI) che verranno utilizzati per il test delle prestazioni. Facoltativamente, è possibile caricare una miniatura. Inoltre, il proprietario dell&#39;azienda può configurare il provisioning degli ambienti durante la configurazione del programma.

I KPI definiti fungono da riferimento per il test delle prestazioni, che viene passato ogni volta che viene eseguita la pipeline.

>[!NOTE]
>
>I KPI definiti vengono misurati sui test eseguiti nell&#39;ambiente **stage**. In genere, questi KPI vengono ridotti per adattarsi alle funzionalità dell’ambiente di visualizzazione.
>
>Ad esempio, un utente che prevede una media di 1000 visualizzazioni di pagina al minuto nella propria produzione **Ambiente** e che dispone di quattro server dispatcher/pubblicazione in produzione, deve ridimensionare questo valore a 250 visualizzazioni di pagina al minuto (supponendo che l&#39;ambiente di fase sia costituito da una sola coppia di server dispatcher/pubblicazione).
>
>Inoltre, molti utenti dispongono di una rete CDN (Content Delivery Network), come Akamai o CloudFront, davanti al proprio ambiente di produzione. Poiché [!UICONTROL Cloud Manager] viene eseguito direttamente il test sull&#39;ambiente di passaggio, l&#39;indicatore KPI deve riflettere solo il traffico previsto attraverso la rete CDN, ovvero la cache non riesce. In genere si tratta di un sottoinsieme relativamente piccolo del traffico di produzione totale.

## Utilizzo di [!UICONTROL Cloud Manager] per impostare il programma {#using-cloud-manager-to-setup-your-program}

Per impostare il programma e definire KPI, procedere come segue:

1. Fare clic su **Programma di installazione** per avviare il processo di configurazione in [!UICONTROL Cloud Manager].

   ![image1](assets/set-up-program/setup1.png)

   >[!NOTE]
   > Puoi sempre cambiare, modificare o aggiungere un nuovo programma dalla barra delle azioni, come mostrato nella figura seguente.

   ![image1](assets/set-up-program/setup2.png)


1. Nella schermata **Programma di installazione** vengono visualizzate le informazioni sul programma di modifica.

1. Verranno visualizzate tre opzioni: **Generale**, **KPI** e **Provisioning**.

1. Nella scheda **Generale**, caricate una miniatura nel programma. È inoltre possibile aggiungere una descrizione pertinente al programma.

   ![](assets/Setup_Program-General.png)

1. In **KPI** è possibile definire i due KPI (aspettative per ogni implementazione). I KPI separati sono definiti per **AEM Sites** e **AEM Assets**. Potrete specificare i KPI per i prodotti per i quali disponete della licenza.

   **AEM Sites**

   1. Qual è il tempo di risposta del 95° percentile accettabile per voi?

      * Valore consigliato - 3 secondi
   1. Quante visualizzazioni di pagina al minuto sotto il carico di picco?

      * Valore consigliato: 200 visualizzazioni di pagina al minuto

   **AEM Assets**

   Dalla versione iniziale, Cloud Manager è stato in grado di eseguire test delle prestazioni per  programmi AEM Sites. Con questa versione, è stata aggiunta la capacità di eseguire test di prestazioni anche per  programmi AEM Assets. Il test delle prestazioni delle risorse viene eseguito caricando ripetutamente le risorse durante un periodo di test di 30 minuti, misurando il tempo di elaborazione per ciascuna risorsa e varie metriche a livello di sistema.
Durante l’impostazione del programma, vengono specificati KPI specifici per le risorse:

   * 95° tempo di elaborazione percentuale
   * Risorse caricate al minuto

   ![](assets/Setup_Program-KPIs.png)

1. In **Provisioning** è possibile visualizzare o modificare la configurazione di provisioning per gli ambienti di produzione e non di produzione nel programma. **La scalabilità automatica è attivata in**, se è stato attivato il ridimensionamento automatico per il programma.

   >[!NOTE]
   >
   >* La funzione di scalabilità automatica è applicabile solo all&#39;ambiente di produzione e potrebbe non essere disponibile per tutti i programmi dei clienti.
   >* Il ridimensionamento su richiesta non è disponibile per questa versione di [!UICONTROL Cloud Manager].


   ![](assets/Setup_Program-Provisioning.png)

1. Fare clic su **Salva** per completare la procedura guidata di configurazione.

   >[!NOTE]
   >
   >È sempre possibile modificare il programma una volta che il programma iniziale è già stato impostato. Seguite i passaggi indicati di seguito per ulteriori dettagli.

## Modifica di un programma

1. Andate alla soluzione nella schermata principale **Cloud Manager**.

   ![](assets/SetUpProgram5.png)

1. Selezionate la soluzione e fate clic su **Modifica** per aggiornare o modificare il programma, come illustrato nella figura seguente.

   ![](assets/SetUpProgram6.png)

1. Viene visualizzata la schermata **Edit Program** che consente di aggiornare o modificare il programma.

   ![](assets/Editing_Program-screen3.png)

## Passaggi successivi {#the-next-steps}

Se è già stata impostata la **Pipeline**, l&#39;esecuzione successiva terrà conto delle impostazioni aggiornate. Se non avete ancora impostato la pipeline, seguite prima i passaggi necessari per impostare la pipeline.

Per impostare la pipeline, vedere [Configurare la pipeline CI/CD](https://helpx.adobe.com/experience-manager/cloud-manager/using/configuring-pipeline.html).
