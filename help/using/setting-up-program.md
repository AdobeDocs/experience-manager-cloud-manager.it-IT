---
title: Configurazione del programma
seo-title: Configurazione del programma
description: Dopo l'imbarco, il proprietario dell'azienda dovrà effettuare una configurazione iniziale del programma.
seo-description: 'Dopo la registrazione, il proprietario dell''azienda dovrà effettuare una configurazione iniziale di Adobe AEM Cloud Manager. Ciò comporta l''impostazione della descrizione del programma e la definizione dei KPI che verranno utilizzati per il test delle prestazioni. '
uuid: 9ecf8743-1f5a-4744-86af-e2256567642f
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: guida introduttiva
discoiquuid: c2393540-e852-4f7c-aafd-1427209065d2
translation-type: tm+mt
source-git-commit: 2c05eb4610e35d5126c6c67e44f4b71f3026c887

---


# Configurazione del programma {#setup-your-program}

Dopo l'imbarco, il proprietario dell'azienda dovrà completare la configurazione iniziale del programma. Ciò comporta l'impostazione della descrizione del programma e la definizione degli indicatori prestazioni chiave (KPI) che verranno utilizzati per il test delle prestazioni. Facoltativamente, è possibile caricare una miniatura. Inoltre, il proprietario dell'azienda può configurare il provisioning degli ambienti durante la configurazione del programma.

I KPI definiti fungono da riferimento per il test delle prestazioni, che viene passato ogni volta che viene eseguita la pipeline.

>[!NOTE]
>
>I KPI definiti vengono misurati sui test eseguiti nell'ambiente **stage** . In genere, questi KPI vengono ridotti per adattarsi alle funzionalità dell’ambiente di visualizzazione.
>
>Ad esempio, un utente che prevede una media di 1000 visualizzazioni di pagina al minuto nell’ **ambiente** di produzione e che dispone di quattro server dispatcher/pubblicazione in produzione, deve ridimensionare tale visualizzazione a 250 visualizzazioni di pagina al minuto (supponendo che l’ambiente in cui si trova lo stage sia costituito da una sola coppia di server dispatcher/pubblicazione).
>
>Inoltre, molti utenti dispongono di una rete CDN (Content Delivery Network), come Akamai o CloudFront, davanti al proprio ambiente di produzione. Poiché [!UICONTROL Cloud Manager] i test vengono eseguiti direttamente sull’ambiente di passaggio, l’indicatore KPI deve riflettere solo il traffico previsto attraverso la rete CDN, ovvero gli errori della cache. In genere si tratta di un sottoinsieme relativamente piccolo del traffico di produzione totale.

## Utilizzo [!UICONTROL Cloud Manager] del programma {#using-cloud-manager-to-setup-your-program}

Per impostare il programma e definire KPI, procedere come segue:

1. Fate clic su **Programma** di installazione per avviare il processo di configurazione in [!UICONTROL Cloud Manager].

   ![](assets/SetUpProgram1.png)

1. Nella schermata **Programma** di installazione vengono visualizzate le informazioni sul programma di modifica.

1. Verranno visualizzate tre opzioni: **Generale**, **KPI** e **Provisioning** .

1. Nella scheda **Generale** , caricate una miniatura nel programma. È inoltre possibile aggiungere una descrizione pertinente al programma.

   ![](assets/Setup_Program-General.png)

1. In **KPI**, puoi definire i tuoi due KPI (aspettative per ogni distribuzione). I KPI separati sono definiti per **AEM Sites** e **AEM Assets**. Potrete specificare i KPI per i prodotti per i quali disponete della licenza.

   **AEM Sites**

   1. Qual è il tempo di risposta del 95° percentile accettabile per voi?

      * Valore consigliato - 3 secondi
   1. Quante visualizzazioni di pagina al minuto sotto il carico massimo?

      * Valore consigliato: 200 visualizzazioni di pagina al minuto
   **AEM Assets**

   Dalla versione iniziale, Cloud Manager è stato in grado di eseguire test delle prestazioni per i programmi AEM Sites. Con questa versione, è stata aggiunta la possibilità di eseguire test delle prestazioni anche per i programmi AEM Assets. Il test delle prestazioni delle risorse viene eseguito caricando ripetutamente le risorse durante un periodo di test di 30 minuti, misurando il tempo di elaborazione per ciascuna risorsa e varie metriche a livello di sistema.
Durante l’impostazione del programma, vengono specificati KPI specifici per le risorse:

   * 95° tempo di elaborazione percentuale
   * Risorse caricate al minuto
   ![](assets/Setup_Program-KPIs.png)

1. In **Provisioning**, potete visualizzare o modificare la configurazione di provisioning per gli ambienti di produzione e non di produzione del programma. Se è stato attivato il ridimensionamento automatico per il programma, verrà visualizzato **l'opzione Scala automatica attivata**.

   >[!NOTE]
   >
   >* La funzione di scalabilità automatica è applicabile solo all'ambiente di produzione e potrebbe non essere disponibile per tutti i programmi dei clienti.
   >* Il ridimensionamento su richiesta non è disponibile per questa versione di [!UICONTROL Cloud Manager].


   ![](assets/Setup_Program-Provisioning.png)

1. Fate clic su **Salva** per completare la procedura guidata di configurazione.

   >[!NOTE]
   >
   >È sempre possibile modificare il programma una volta che il programma iniziale è già stato impostato. Seguite i passaggi indicati di seguito per ulteriori dettagli.

## Modifica di un programma

1. Passa alla soluzione nella schermata iniziale di **Cloud Manager** .

   ![](assets/SetUpProgram5.png)

1. Selezionate la soluzione e fate clic su **Modifica** per aggiornare o modificare il programma, come mostrato nella figura seguente.

   ![](assets/SetUpProgram6.png)

1. Viene visualizzata la schermata **Modifica programma** che consente di aggiornare o modificare il programma.

   ![](assets/Editing_Program-screen3.png)

## Passaggi successivi {#the-next-steps}

Se hai già impostato la **tubazione**, la successiva esecuzione terrà conto delle impostazioni aggiornate. Se non avete ancora impostato la pipeline, seguite prima i passaggi necessari per impostare la pipeline.

Consulta [Configurare la pipeline](https://helpx.adobe.com/experience-manager/cloud-manager/using/configuring-pipeline.html) CI/CD per configurare la pipeline.
