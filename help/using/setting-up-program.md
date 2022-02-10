---
title: Imposta il programma
seo-title: Set Up Your Program
description: Dopo l'onboarding, il proprietario dell'azienda dovrà effettuare una configurazione iniziale del programma.
seo-description: After onboarding, the business owner will need to do some initial setup of Adobe AEM Cloud Manager. This involves setting the program description and defining the KPIs which will be used for performance testing.
feature: Getting Started
exl-id: 795c7112-d564-4fbf-96a1-152a6c286bf2
source-git-commit: 71d44c7e3673ca62fcd2203ecc0bc4ed9fa22002
workflow-type: tm+mt
source-wordcount: '687'
ht-degree: 1%

---

# Configurare il programma {#setup-your-program}

Dopo l&#39;imbarco, il proprietario dell&#39;azienda dovrà completare una configurazione iniziale del programma. Ciò comporta l’impostazione della descrizione del programma e la definizione degli indicatori prestazioni chiave (KPI, Key Performance Indicators) che verranno utilizzati per il test delle prestazioni. Facoltativamente, è possibile caricare una miniatura. Inoltre, il proprietario aziendale può configurare il provisioning degli ambienti durante la configurazione del programma.

I KPI definiti fungono da linea di base per i test delle prestazioni che vengono trasmessi ogni volta che la pipeline viene eseguita.

>[!NOTE]
>I KPI definiti vengono misurati sui test eseguiti nel **stadio** ambiente. In genere, questi KPI vengono ridimensionati per adattarsi alle funzionalità dell’ambiente stage.
>Ad esempio, un utente si aspetta una media di 1000 visualizzazioni di pagina al minuto nella propria produzione **Ambiente** e avere quattro server dispatcher/publish in produzione dovrebbe portare questo a 250 visualizzazioni di pagina al minuto (supponendo che il loro ambiente stage sia costituito da una sola coppia di server dispatcher/publish).
>Inoltre, molti utenti disporranno di una rete CDN (Content Delivery Network), come Akamai o CloudFront, davanti al proprio ambiente di produzione. Da [!UICONTROL Cloud Manager] esegue direttamente i test sull’ambiente stage, il KPI deve riflettere solo il traffico previsto attraverso la CDN, ovvero la cache mancante. In genere si tratta di un sottoinsieme relativamente piccolo del traffico di produzione totale.

## Utilizzo [!UICONTROL Cloud Manager] per configurare il programma {#using-cloud-manager-to-setup-your-program}

Per impostare il programma e definire i KPI, effettua le seguenti operazioni:

1. Fai clic su **Programma di installazione** per avviare il processo di configurazione in [!UICONTROL Cloud Manager].

   ![image1](assets/set-up-program/setup1.png)

   >[!NOTE]
   > Puoi sempre cambiare, modificare o aggiungere un nuovo programma dalla barra delle azioni, come illustrato nella figura riportata di seguito.

   ![image1](assets/set-up-program/setup2.png)


1. La **Programma di installazione** Viene visualizzata la schermata Edit Program Information (Modifica informazioni programma).

1. Verranno visualizzate tre opzioni come **Generale**, **KPI** e **Provisioning** scheda .

1. In **Generale** , carica una miniatura nel programma. È inoltre possibile aggiungere una descrizione pertinente al programma.

   ![](assets/Setup_Program-General.png)

1. Sotto **KPI**, puoi definire i due KPI (aspettative per ogni distribuzione). I KPI separati sono definiti per **AEM Sites** e **AEM Assets**. Potrai specificare i KPI per i prodotti per i quali hai concesso la licenza.

   **AEM Sites**

   1. Qual è il tempo di risposta del 95° percentile accettabile per te?

      * Valore consigliato - 3 secondi
   1. Quante visualizzazioni di pagina al minuto al di sotto del carico di picco?

      * Valore consigliato - 200 visualizzazioni di pagina al minuto

   **AEM Assets**

   Dalla versione iniziale, Cloud Manager è stato in grado di eseguire test delle prestazioni per i programmi AEM Sites. A partire da questa versione, è stata aggiunta la possibilità di eseguire test delle prestazioni anche per i programmi AEM Assets. Il test delle prestazioni delle risorse viene eseguito caricando ripetutamente le risorse durante un periodo di test di 30 minuti e misurando il tempo di elaborazione per ciascuna risorsa e varie metriche a livello di sistema.
Durante l’impostazione del programma, vengono specificati i KPI specifici per le risorse:

   * 95° tempo di elaborazione percentuale
   * Risorse caricate al minuto

   ![](assets/Setup_Program-KPIs.png)

1. Sotto **Provisioning**, puoi visualizzare o modificare la configurazione di provisioning per gli ambienti di produzione e non di produzione nel tuo programma. Vedrai **Scalabilità automatica attivata**, se è stata attivata la scalabilità automatica per il programma.

   >[!NOTE]
   >La funzione di scalabilità automatica è applicabile solo all’ambiente di produzione e potrebbe non essere disponibile per tutti i programmi dei clienti.

   ![](assets/Setup_Program-Provisioning.png)

1. Fai clic su **Salva** per completare la configurazione guidata.

   >[!NOTE]
   >È sempre possibile modificare il programma una volta che il programma iniziale è già stato impostato. Per ulteriori informazioni, segui i passaggi riportati di seguito.

## Modifica di un programma {#editing-program}

1. Passa al programma dal **Cloud Manager** schermata iniziale.

1. Fai clic su **Modifica programma** per aggiornare o modificare il programma dalla **Panoramica** , come illustrato nella figura riportata di seguito.

   ![](assets/set-up-program/edit-program1.png)

1. La **Modifica programma** viene visualizzata una schermata che consente di aggiornare o modificare il programma.

   È possibile aggiornare la descrizione del programma dalla **Generale** scheda .

   ![](assets/set-up-program/edit-program-general.png)

   Passa a **KPI** per aggiornare le informazioni su AEM Sites e Assets.

   ![](assets/set-up-program/edit-program-kpi.png)

   Inoltre, puoi passare a **Provisioning** per modificare la configurazione di provisioning per gli ambienti di produzione e non di produzione nel programma.

   ![](assets/set-up-program/edit-program-provision.png)

1. Fai clic su **Aggiorna** per salvare le modifiche.

## Passaggi successivi {#the-next-steps}

Se hai già configurato la pipeline, l’esecuzione successiva terrà conto delle impostazioni aggiornate. Se la pipeline non è ancora stata impostata, segui prima i passaggi per configurarla.

Vedi i documenti [Configurazione delle pipeline di produzione](configuring-production-pipelines.md) e [Configurazione di pipeline non di produzione](configuring-non-production-pipelines.md) per l’impostazione della pipeline.
