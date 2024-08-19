---
title: Configurazione del programma
description: Dopo l’onboarding, il proprietario business deve effettuare una configurazione iniziale del programma.
exl-id: 795c7112-d564-4fbf-96a1-152a6c286bf2
source-git-commit: 11a6a53d8cbfb689810a9a8e7d82293a49863084
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 53%

---


# Configurazione del programma {#program-setup}

Dopo l’onboarding, il proprietario business imposta il programma aggiungendo una descrizione e definendo gli indicatori prestazioni chiave (KPI, Key Performance Indicator). Questi KPI vengono quindi utilizzati per il test delle prestazioni.

## Configurazione del programma con [!UICONTROL Cloud Manager] {#program-setup-cloud-manager}

Segui questi passaggi per configurare il programma e definire i KPI.

1. Accedi a Cloud Manager all’indirizzo [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) e seleziona l’organizzazione appropriata.

1. Fai clic su **Programma di configurazione** per avviare il processo di configurazione.

   ![Configurare il programma](/help/assets/set-up-program/setup1.png)

1. Nella finestra di dialogo **Programma di installazione** è possibile immettere informazioni sul programma in tre schede:

   * **Generale**
   * **KPI**
   * **Provisioning**

1. Nella scheda **Generale**, aggiungi una descrizione del programma e, facoltativamente, carica una miniatura facendo clic su **Cambia foto**.

   ![Scheda Generale](/help/assets/Setup_Program-General.png)

1. Nella scheda **KPI**, definisci i KPI. In questo esempio, vengono definiti KPI separati per **AEM Sites** e **AEM Assets**. Specifica i KPI per i prodotti per i quali hai concesso la licenza.

   Consulta la sezione [KPI](#kpis) per ulteriori dettagli sulla misurazione dei KPI in Cloud Manager.

   ![Definizione dei KPI](/help/assets/Setup_Program-KPIs.png)

1. Nella scheda **Provisioning**, se per il programma è abilitata la scalabilità automatica, è possibile definire le opzioni di ridimensionamento on-demand per i tuoi ambienti.

   La scalabilità automatica è applicabile solo all’ambiente di produzione e potrebbe non essere disponibile per tutti i programmi dei clienti.

   ![Opzioni di provisioning](/help/assets/Setup_Program-Provisioning.png)

1. Fai clic su **Salva**.

Il programma viene creato. Potrebbero essere necessari diversi minuti per il provisioning delle risorse prima che il programma sia pronto per l’uso.

## Modificare un programma {#editing-program}

È possibile modificare i programmi dopo averli impostati. Per modificare un programma, effettua le seguenti operazioni.

1. Accedi a Cloud Manager all’indirizzo [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) e seleziona l’organizzazione appropriata.

1. Passa al programma dalla schermata iniziale di Cloud Manager.

1. Fai clic su **Modifica programma** per aggiornare o modificare il programma dalla pagina **Panoramica**.

   ![Opzione Modifica programma](/help/assets/set-up-program/edit-program1.png)

1. Viene visualizzata la finestra di dialogo **Modifica programma**, in cui è possibile aggiornare il programma. Consulta la sezione [Configurazione del programma con Cloud Manager](#program-setup-cloud-manager) per informazioni dettagliate sui campi disponibili.

   ![Finestra di dialogo di modifica del programma](/help/assets/set-up-program/edit-program-general.png)

1. Fai clic su **Aggiorna** per salvare le modifiche.

Tieni presente che le modifiche vengono salvate immediatamente in Cloud Manager, ma non verranno applicate negli ambienti fino alla successiva esecuzione della pipeline.

Se non hai ancora creato una pipeline, consulta [Configurazione delle pipeline di produzione](/help/using/production-pipelines.md) e [Configurazione delle pipeline non di produzione](/help/using/non-production-pipelines.md).

## Passa da un programma all&#39;altro {#swithing-programs}

Quando lavori a un programma, puoi passare rapidamente a un altro senza tornare alla pagina della panoramica di Cloud Manager.

Utilizza la barra delle azioni per passare a un altro programma, modificare il programma in uso o aggiungerne uno nuovo.

![Selettore di programma](/help/assets/set-up-program/setup2.png)

## KPI {#kpis}

I KPI dei siti vengono misurati nei test eseguiti nell’ambiente di staging. In genere, questi KPI vengono ridimensionati per adattarsi alle funzionalità dell’ambiente di pre-produzione.

Ad esempio, un utente che si aspetta una media di 1000 visualizzazioni di pagina al minuto nel proprio ambiente di produzione e dispone di quattro server di pubblicazione/Dispatcher in produzione, dovrebbe ridimensionare questo scenario a 250 visualizzazioni di pagina al minuto. Questo scenario presuppone che il loro ambiente di staging sia costituito da una sola coppia di server dispatcher/di pubblicazione.

Il test delle prestazioni di Assets prevede il caricamento ripetuto delle risorse in un periodo di 30 minuti. Il tempo di elaborazione di ciascuna risorsa e di varie metriche a livello di sistema vengono misurati durante l’intero test.

È possibile che davanti all’ambiente di produzione sia presente una rete per la distribuzione dei contenuti (CDN, Content Delivery Network) come Akamai o CloudFront. Poiché [!UICONTROL Cloud Manager] esegue direttamente i test nell&#39;ambiente di gestione temporanea, l&#39;indicatore KPI deve riflettere solo il traffico che si prevede passi attraverso la rete CDN. In altre parole, la cache non funziona. In genere, questa esperienza è un sottoinsieme relativamente piccolo del traffico di produzione totale.

## Panoramica video {#video}

>[!VIDEO](https://video.tv.adobe.com/v/26313/)
