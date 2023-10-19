---
title: Configurazione di pipeline non di produzione
description: Scopri come utilizzare Cloud Manager per creare e configurare pipeline non di produzione per distribuire il codice.
exl-id: ccf4b4a2-6e29-4ede-821c-36318b568e5c
source-git-commit: 33ccb0f2139162845cc1b72505b6a5bfc7cf43e7
workflow-type: ht
source-wordcount: '716'
ht-degree: 100%

---

# Configurazione di pipeline non di produzione {#configuring-non-production-pipelines}

Scopri come utilizzare Cloud Manager per creare e configurare pipeline non di produzione per distribuire il codice. Per una panoramica delle nozioni di base sul funzionamento delle pipeline in Cloud Manager, consulta il documento [Pipeline CI/CD.](/help/overview/ci-cd-pipelines.md)

## Panoramica {#overview}

Utilizzando il riquadro **Pipeline** in [!UICONTROL Cloud Manager], il **Responsabile della distribuzione** può creare due diversi tipi di pipeline.

* **Pipeline di produzione**: una pipeline di produzione è una pipeline appositamente creata composta da una serie di passaggi orchestrati per portare il codice sorgente fino alla produzione.
* **Pipeline non di produzione**: una pipeline non di produzione serve principalmente per eseguire scansioni di qualità del codice o per distribuire il codice sorgente in un ambiente di sviluppo.

Questo documento si concentra sulle pipeline non di produzione. Per informazioni dettagliate su come configurare le pipeline di produzione, consulta il documento [Configurazione delle pipeline di produzione.](/help/using/production-pipelines.md)

Esistono due tipi di pipeline non di produzione:

* **Pipeline di qualità del codice**: eseguono controlli di qualità del codice in un ramo Git ed eseguono i passaggi di generazione e qualità del codice.
* **Pipeline di implementazione**: oltre a eseguire la generazione e i passaggi di qualità del codice come le pipeline di qualità del codice, queste pipeline distribuiscono il codice in un ambiente non di produzione.

>[!NOTE]
>
>Non è possibile configurare una pipeline finché il relativo archivio Git associato non dispone di almeno un ramo e la [Configurazione del programma](/help/getting-started/program-setup.md) non è stata completata. Consultare il documento [Archivi di Cloud Manager](/help/managing-code/repositories.md) per scoprire come aggiungere e gestire gli archivi in Cloud Manager.

## Aggiunta di una pipeline non di produzione {#add-non-production-pipeline}

Dopo aver configurato il programma e disponi di almeno un ambiente utilizzando l’interfaccia utente di Cloud Manager, puoi aggiungere una pipeline non di produzione seguendo questi passaggi.

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) e seleziona l’organizzazione e il programma appropriati.

1. Accedi alla scheda Pipeline dalla schermata principale di Cloud Manager. Fai clic su **Aggiungi** e seleziona **Aggiungi pipeline non di produzione**.

   ![Aggiungi pipeline non di produzione](/help/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. Sulla scheda **Configurazione** della finestra di dialogo **Aggiungi pipeline non di produzione**, seleziona il tipo di pipeline da creare oppure **Pipeline di qualità del codice** o **Pipeline di implementazione**.

   ![Scegli il tipo di pipeline](/help/assets/configure-pipelines/add-non-production-pipeline.png)

1. Fornisci una descrizione della pipeline nel campo **Nome della pipeline non di produzione**.

1. Se hai scelto di aggiungere una **Pipeline di implementazione**, seleziona l’ambiente di distribuzione di destinazione dal menu a discesa **Ambienti di implementazione idonei**.

1. Fornisci l’archivio in cui la pipeline deve recuperare il codice.

   * **Archivio**: questa opzione definisce da quale archivio Git la pipeline deve recuperare il codice.
   * **Ramo Git**: questa opzione definisce da quale ramo della pipeline selezionata deve essere recuperato il codice.

1. Definisci le opzioni di implementazione.

   1. In **Trigger di implementazione**, definisci l’evento che attiva la pipeline.

      * **Manuale**: utilizza questa opzione per avviare manualmente la pipeline.
      * **Cambiamenti su Git**: questa opzione avvia la pipeline ogni volta che vengono aggiunti dei commit al ramo git configurato. Con questa opzione, puoi comunque avviare la pipeline manualmente, in base alle esigenze.

   1. Per le pipeline di implementazione, in **Comportamento in caso di errori di metriche importanti**, definisci il comportamento della pipeline quando si verifica un errore importante in uno qualsiasi dei gate di qualità.

      * **Chiedi ogni volta**: questa è l’impostazione predefinita e richiede l’intervento manuale su qualsiasi errore importante.
      * **Interrompi subito**: selezionando questa opzione, la pipeline viene annullata ogni volta che si verifica un errore importante. In sostanza, quest’opzione simula un utente che rifiuta manualmente ogni errore.
      * **Continua immediatamente**: selezionando questa opzione, la pipeline avanza automaticamente ogni volta che si verifica un errore importante. In sostanza, quest’opzione simula un utente che approva manualmente ogni errore.

   1. **Configurazione del Dispatcher**: il ruolo di **Responsabile della distribuzione** può configurare un set di percorsi di contenuto che verranno invalidati o svuotati dalla cache del dispatcher AEM quando viene eseguita una pipeline. Queste azioni della cache verranno eseguite come parte del passaggio della pipeline di implementazione, subito dopo la distribuzione di eventuali pacchetti di contenuto. Queste impostazioni utilizzano il comportamento standard del Dispatcher AEM. Per configurare:

      1. Nel **PERCORSO** fornisci un percorso di contenuto.
      1. In **TIPO**, seleziona l’azione da intraprendere su quel percorso.

         * **Scaricamento**: esegui un’eliminazione della cache.
         * **Invalida**: esegui un’invalidazione della cache, simile a quando il contenuto viene attivato da un’istanza di authoring a un’istanza di pubblicazione.
      1. Fai clic su **Aggiungi percorso** per aggiungere il percorso specificato. Puoi aggiungere fino a 100 percorsi per ambiente.

1. Fai clic su **Salva** per salvare la pipeline.

## Passaggi successivi {#the-next-steps}

Dopo aver configurato la pipeline, è necessario distribuire il codice. Per ulteriori dettagli, consulta il documento [Distribuzione del codice](/help/using/code-deployment.md).

## Tutorial video {#video-tutorial}

Questo video fornisce una panoramica del processo di creazione della pipeline, descritto in questo documento.

>[!VIDEO](https://video.tv.adobe.com/v/26316/)
