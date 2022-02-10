---
title: Configurazione di pipeline non di produzione
description: Scopri come utilizzare Cloud Manager per creare e configurare pipeline non di produzione per distribuire il codice.
source-git-commit: 205113735cc743e11e140b1161413002844f5b79
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 0%

---


# Configurazione di pipeline non di produzione {#configuring-non-production-pipelines}

Scopri come utilizzare Cloud Manager per creare e configurare pipeline non di produzione per distribuire il codice. per una panoramica più concettuale del funzionamento delle pipeline in Cloud Manager, consulta la sezione [Documentazione sulla panoramica della pipeline CI/CD.](ci-cd-pipeline.md)

>[!NOTE]
>
>Per informazioni su come configurare le pipeline CI/CD per Cloud Manager in AEM as a Cloud Service, consulta [la documentazione di AEMaaCS.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html#using-cloud-manager)

## Panoramica {#understanding-the-flow}

La **Gestione distribuzione** è responsabile della configurazione della pipeline utilizzando **Tubi** nella sezione [!UICONTROL Cloud Manager] Interfaccia utente.

Puoi creare due diversi tipi di pipeline.

* **Pipe di produzione** - Una pipeline di produzione è una pipeline appositamente costruita composta da una serie di passaggi orchestrati per portare il codice sorgente fino alla produzione.
* **Pipeline non di produzione** - Una pipeline non di produzione serve principalmente per eseguire scansioni di qualità del codice o per distribuire il codice sorgente in un ambiente di sviluppo.

Questo documento si concentra sulle condutture non di produzione. Per informazioni dettagliate su come configurare le pipeline non di produzione, consulta il documento [Configurazione delle pipeline non di produzione.](configuring-non-production-pipelines.md)

Esistono due tipi di gasdotti non di produzione:

* **Pipeline di qualità del codice** - Questa funzione esegue la scansione del codice in un ramo git ed esegue i passaggi di creazione e qualità del codice.
* **Pipeline di distribuzione** - Oltre a eseguire la generazione e i passaggi di qualità del codice come le pipeline di qualità del codice, queste pipeline distribuiscono il codice in un ambiente non di produzione.

>[!NOTE]
>
>Non è possibile impostare una pipeline finché il relativo archivio Git associato non dispone di almeno un ramo e [configurazione del programma](setting-up-program.md) è completo. Vedi [Aggiunta e gestione di archivi](cloud-manager-repositories.md) per scoprire come aggiungere e gestire archivi in Cloud Manager.

## Tutorial video {#video-tutorial-two}

>[!VIDEO](https://video.tv.adobe.com/v/26316/)

## Aggiunta di una pipeline non di produzione {#add-non-production-pipeline}

Dopo aver configurato il programma e disporre di almeno un ambiente utilizzando l’interfaccia utente di Cloud Manager, puoi aggiungere una pipeline non di produzione seguendo questi passaggi.

1. Accedi a Cloud Manager all&#39;indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) e selezionare l&#39;organizzazione e il programma appropriati.

1. Accedi alla scheda Pipelines dalla schermata principale di Cloud Manager. Fai clic su **Aggiungi** e seleziona **Aggiungi pipeline non di produzione**.

   ![Aggiungere una pipeline non di produzione](/help/using/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. Sulla **Configurazione** della scheda **Aggiungi pipeline non di produzione** selezionate il tipo di pipeline da creare, oppure **Pipeline di qualità del codice** o **Pipeline di distribuzione**.


   ![Scegli il tipo di pipeline](/help/using/assets/configure-pipelines/add-non-production-pipeline.png)

1. Fornisci una descrizione della pipeline nel **Nome della pipeline non di produzione** campo .

1. Se hai scelto di aggiungere un **Pipeline di distribuzione**, seleziona l’ambiente di distribuzione di destinazione dal **Ambienti di distribuzione idonei** a discesa.

1. Fornisci l’archivio in cui la pipeline deve recuperare il codice.

   * **Archivio** - Questa opzione definisce da quale git repo la pipeline deve recuperare il codice.
   * **Ramo Git** - Questa opzione definisce da quale ramo della pipeline selezionata deve essere recuperato il codice.

1. Definisci le opzioni di distribuzione.

   1. Sotto **Trigger distribuzione**, definisci l’evento che attiva la pipeline.

      * **Manuale** - Utilizzare questa opzione per avviare manualmente la pipeline.
      * **Su modifiche Git** - Questa opzione avvia la pipeline ogni volta che vengono aggiunti dei commit al ramo git configurato. Con questa opzione, potete comunque avviare la pipeline manualmente come necessario.
   1. Sotto **Comportamento di errori di metrica importanti**, definisci il comportamento della pipeline quando si verifica un errore importante in uno qualsiasi dei gate di qualità.

      * **Chiedi sempre** - Questa è l&#39;impostazione predefinita e richiede l&#39;intervento manuale su qualsiasi errore importante.
      * **Non riuscito immediatamente** - Se selezionata, la pipeline verrà annullata ogni volta che si verifica un errore importante. In sostanza, questo sta simulando un utente che rifiuta manualmente ogni errore.
      * **Continua immediatamente** - Se selezionata, la pipeline procede automaticamente ogni volta che si verifica un errore importante. In sostanza, questo sta simulando un utente che approva manualmente ogni errore.


1. Fai clic su **Salva** per salvare la pipeline.

## Passaggi successivi {#the-next-steps}

Dopo aver configurato la pipeline, devi distribuire il codice.

Vedi il documento [Distribuisci il codice](deploying-code.md) per ulteriori dettagli.
