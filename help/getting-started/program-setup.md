---
title: Configurazione del programma
description: Dopo l'onboarding, il proprietario dell'azienda dovrà effettuare una configurazione iniziale del programma.
exl-id: 795c7112-d564-4fbf-96a1-152a6c286bf2
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 1%

---


# Configurazione del programma {#program-setup}

Dopo l’onboarding, il proprietario dell’azienda completa la configurazione iniziale del programma, inclusa l’impostazione della descrizione del programma e la definizione degli indicatori prestazioni chiave (KPI, Key Performance Indicators) utilizzati per il test delle prestazioni.

## Configurazione del programma con [!UICONTROL Cloud Manager] {#program-setup-cloud-manager}

Segui questi passaggi per impostare il programma e definire i KPI.

1. Accedi a Cloud Manager all&#39;indirizzo [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) e selezionare l&#39;organizzazione appropriata.

1. Fai clic su **Programma di installazione** per avviare il processo di configurazione.

   ![Imposta programma](/help/assets/set-up-program/setup1.png)

1. In **Programma di installazione** è possibile inserire informazioni sul programma in tre schede:

   * **Generale**
   * **KPI**
   * **Provisioning**

1. Sulla **Generale** aggiungi una descrizione del programma e, facoltativamente, carica una miniatura facendo clic su **Modifica foto**.

   ![Scheda Generale](/help/assets/Setup_Program-General.png)

1. Sulla **KPI** , definisci i KPI. In questo esempio, vengono definiti KPI separati per **AEM Sites** e **AEM Assets**. Potrai specificare i KPI per i prodotti per i quali hai concesso la licenza.

   * Vedi la sezione [KPI](#kpis) per ulteriori dettagli sulla misurazione dei KPI in Cloud Manager.

   ![Definizione dei KPI](/help/assets/Setup_Program-KPIs.png)

1. Sulla **Provisioning** Se per il programma è abilitata la funzione di scalabilità automatica, puoi definire le opzioni di ridimensionamento on-demand per i tuoi ambienti.

   * La scalabilità automatica è applicabile solo all’ambiente di produzione e potrebbe non essere disponibile per tutti i programmi dei clienti.

   ![Opzioni di provisioning](/help/assets/Setup_Program-Provisioning.png)

1. Fai clic su **Salva** per completare la configurazione guidata.

Il programma verrà creato. Potrebbero essere necessari diversi minuti prima che il programma sia pronto per l&#39;uso per il provisioning delle risorse.

## Modifica di un programma {#editing-program}

È possibile modificare i programmi dopo la loro configurazione. Segui questi passaggi per modificare un programma.

1. Accedi a Cloud Manager all&#39;indirizzo [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) e selezionare l&#39;organizzazione appropriata.

1. Passa al programma dalla schermata iniziale di Cloud Manager.

1. Fai clic su **Modifica programma** per aggiornare o modificare il programma dalla **Panoramica** pagina.

   ![Opzione Modifica programma](/help/assets/set-up-program/edit-program1.png)

1. La **Modifica programma** viene visualizzata una finestra di dialogo che consente di aggiornare il programma. Vedi la sezione [Configurazione del programma con Cloud Manager](#program-setup-cloud-manager) per informazioni dettagliate sui campi disponibili.

   ![Finestra di dialogo Modifica programma](/help/assets/set-up-program/edit-program-general.png)

1. Fai clic su **Aggiorna** per salvare le modifiche.

Le modifiche vengono salvate immediatamente in Cloud Manager, ma non verranno applicate negli ambienti fino alla successiva esecuzione della pipeline.

Se non hai ancora creato una pipeline, consulta i documenti [Configurazione delle pipeline di produzione](/help/using/production-pipelines.md) e [Configurazione delle pipeline non di produzione.](/help/using/non-production-pipelines.md)

## Passaggio tra programmi {#swithing-programs}

Quando lavori a un programma, puoi passare rapidamente a un altro programma senza tornare alla pagina di panoramica di Cloud Manager.

Utilizzare la barra delle azioni per passare a un altro programma, modificare il programma corrente o aggiungere un nuovo programma.

![Switcher di programma](/help/assets/set-up-program/setup2.png)

## KPI {#kpis}

I KPI dei siti vengono misurati sui test eseguiti nell’ambiente di staging. In genere, questi KPI vengono ridimensionati per adattarsi alle funzionalità dell’ambiente di staging.

Ad esempio, un utente che si aspetta una media di 1000 visualizzazioni di pagina al minuto nel proprio ambiente di produzione e dispone di quattro server di pubblicazione/dispatcher in produzione dovrebbe ridimensionarla a 250 visualizzazioni di pagina al minuto. Ciò presuppone che il loro ambiente di gestione temporanea sia costituito da una sola coppia di server dispatcher/publish.

Il test delle prestazioni delle risorse viene eseguito caricando ripetutamente le risorse durante un periodo di test di 30 minuti e misurando il tempo di elaborazione per ciascuna risorsa e varie metriche a livello di sistema.

È possibile che davanti all’ambiente di produzione sia presente una rete CDN (Content Delivery Network) come Akamai o CloudFront. Da [!UICONTROL Cloud Manager] esegue direttamente i test sull’ambiente di staging, l’indicatore KPI deve riflettere solo il traffico previsto attraverso la rete CDN, ovvero la cache mancante. In genere si tratta di un sottoinsieme relativamente piccolo del traffico di produzione totale.

## Panoramica video {#video}

>[!VIDEO](https://video.tv.adobe.com/v/26313/)
