---
title: Configurazione di pipeline non di produzione
description: Scopri come utilizzare Cloud Manager per creare e configurare pipeline non di produzione per distribuire il codice.
exl-id: ccf4b4a2-6e29-4ede-821c-36318b568e5c
source-git-commit: 567a16a032bf80451b5e8ba4e3d842cb617a615f
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 1%

---

# Configurazione di pipeline non di produzione {#configuring-non-production-pipelines}

Scopri come utilizzare Cloud Manager per creare e configurare pipeline non di produzione per distribuire il codice. Per una panoramica più concettuale del funzionamento delle pipeline in Cloud Manager, consulta il documento [Pipelines CI/CD.](/help/overview/ci-cd-pipelines.md)

## Panoramica {#overview}

Utilizzo della **Tubi** piastrelle [!UICONTROL Cloud Manager], **Gestione distribuzione** può creare due diversi tipi di pipeline.

* **Pipe di produzione** - Una pipeline di produzione è una pipeline appositamente costruita composta da una serie di passaggi orchestrati per portare il codice sorgente fino alla produzione.
* **Pipeline non di produzione** - Una pipeline non di produzione serve principalmente per eseguire scansioni di qualità del codice o per distribuire il codice sorgente in un ambiente di sviluppo.

Questo documento si concentra sulle condutture non di produzione. Per informazioni dettagliate su come configurare le pipeline di produzione, consulta il documento [Configurazione delle pipeline di produzione.](/help/using/production-pipelines.md)

Esistono due tipi di gasdotti non di produzione:

* **Pipeline di qualità del codice** - Questa funzione esegue la scansione del codice in un ramo git ed esegue i passaggi di creazione e qualità del codice.
* **Pipeline di distribuzione** - Oltre a eseguire la generazione e i passaggi di qualità del codice come le pipeline di qualità del codice, queste pipeline distribuiscono il codice in un ambiente non di produzione.

>[!NOTE]
>
>Non è possibile impostare una pipeline finché il relativo archivio Git associato non dispone di almeno un ramo e [configurazione del programma](/help/getting-started/program-setup.md) è completo. Vedere il documento [Repository di Cloud Manager](/help/managing-code/repositories.md) per scoprire come aggiungere e gestire archivi in Cloud Manager.

## Tutorial video {#video-tutorial}

Questo video fornisce una panoramica del processo di creazione della pipeline, descritto in questo documento.

>[!VIDEO](https://video.tv.adobe.com/v/26316/)

## Aggiunta di una pipeline non di produzione {#add-non-production-pipeline}

Dopo aver configurato il programma e disporre di almeno un ambiente utilizzando l’interfaccia utente di Cloud Manager, puoi aggiungere una pipeline non di produzione seguendo questi passaggi.

1. Accedi a Cloud Manager all&#39;indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) e selezionare l&#39;organizzazione e il programma appropriati.

1. Accedi alla scheda Pipelines dalla schermata principale di Cloud Manager. Fai clic su **Aggiungi** e seleziona **Aggiungi pipeline non di produzione**.

   ![Aggiungere una pipeline non di produzione](/help/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. Sulla **Configurazione** della scheda **Aggiungi pipeline non di produzione** selezionate il tipo di pipeline da creare, oppure **Pipeline di qualità del codice** o **Pipeline di distribuzione**.

   ![Scegli il tipo di pipeline](/help/assets/configure-pipelines/add-non-production-pipeline.png)

1. Fornisci una descrizione della pipeline nel **Nome della pipeline non di produzione** campo .

1. Se hai scelto di aggiungere un **Pipeline di distribuzione**, seleziona l’ambiente di distribuzione di destinazione dal **Ambienti di distribuzione idonei** a discesa.

1. Fornisci l’archivio in cui la pipeline deve recuperare il codice.

   * **Archivio** - Questa opzione definisce da quale git repo la pipeline deve recuperare il codice.
   * **Ramo Git** - Questa opzione definisce da quale ramo della pipeline selezionata deve essere recuperato il codice.

1. Definisci le opzioni di distribuzione.

   1. Sotto **Trigger distribuzione**, definisci l’evento che attiva la pipeline.

      * **Manuale** - Utilizzare questa opzione per avviare manualmente la pipeline.
      * **Su modifiche Git** - Questa opzione avvia la pipeline ogni volta che vengono aggiunti dei commit al ramo git configurato. Con questa opzione, potete comunque avviare la pipeline manualmente come necessario.
   1. Per le condotte di distribuzione, in **Comportamento di errori di metrica importanti**, definisci il comportamento della pipeline quando si verifica un errore importante in uno qualsiasi dei gate di qualità.

      * **Chiedi sempre** - Questa è l&#39;impostazione predefinita e richiede l&#39;intervento manuale su qualsiasi errore importante.
      * **Non riuscito immediatamente** - Se selezionata, la pipeline verrà annullata ogni volta che si verifica un errore importante. In sostanza, questo sta simulando un utente che rifiuta manualmente ogni errore.
      * **Continua immediatamente** - Se selezionata, la pipeline procede automaticamente ogni volta che si verifica un errore importante. In sostanza, questo sta simulando un utente che approva manualmente ogni errore.


1. Fai clic su **Salva** per salvare la pipeline.

## Passaggi successivi {#the-next-steps}

Dopo aver configurato la pipeline, devi distribuire il codice. Vedi il documento [Distribuzione del codice](/help/using/code-deployment.md) per ulteriori dettagli.
