---
title: Aggiungi una pipeline non di produzione
description: Scopri come utilizzare Cloud Manager per creare e configurare pipeline non di produzione per distribuire il codice.
exl-id: ccf4b4a2-6e29-4ede-821c-36318b568e5c
source-git-commit: 1209faf71edbd74cd87acfe24ec438b98ddd4a3a
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 98%

---

# Aggiungere una pipeline di produzione {#configuring-non-production-pipelines}

Scopri come utilizzare Cloud Manager per creare e configurare pipeline non di produzione per distribuire il codice. Per una panoramica delle nozioni di base sul funzionamento delle pipeline in Cloud Manager, consulta [Pipeline CI/CD](/help/overview/ci-cd-pipelines.md).

## Panoramica {#overview}

Utilizzando il riquadro **Pipeline** in [!UICONTROL Cloud Manager], il **Responsabile della distribuzione** può creare due diversi tipi di pipeline.

* **Pipeline di produzione**: una pipeline di produzione è una pipeline appositamente creata composta da una serie di passaggi orchestrati per portare il codice sorgente fino alla produzione.
* **Pipeline non di produzione**: una pipeline non di produzione serve principalmente per eseguire scansioni di qualità del codice o per distribuire il codice sorgente in un ambiente di sviluppo.

Questo documento si concentra sulle pipeline non di produzione. Per informazioni dettagliate su come configurare le pipeline di produzione, consulta il documento [Configurazione delle pipeline di produzione](/help/using/production-pipelines.md).

Esistono due tipi di pipeline non di produzione:

* **Pipeline di qualità del codice**: eseguono controlli di qualità del codice in un ramo Git e i passaggi di generazione e qualità del codice.
* **Pipeline di distribuzione**: oltre a eseguire i passaggi di generazione e qualità del codice analogamente alle pipeline di qualità del codice, queste pipeline distribuiscono il codice in un ambiente di non produzione.

>[!NOTE]
>
>Non è possibile configurare una pipeline finché il relativo archivio Git associato non dispone di almeno un ramo e la [Configurazione del programma](/help/getting-started/program-setup.md) non è stata completata. Consulta il documento [Archivi di Cloud Manager](/help/managing-code/managing-repositories.md) per scoprire come aggiungere e gestire gli archivi in Cloud Manager.

## Aggiungi una nuova pipeline non di produzione {#add-non-production-pipeline}

Dopo aver configurato il programma e disporre di almeno un ambiente che utilizza l’interfaccia utente di Cloud Manager, puoi aggiungere una pipeline non di produzione seguendo la procedura riportata di seguito.

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) e seleziona l’organizzazione e il programma appropriati.

1. Accedi alla scheda Pipeline dalla schermata principale di Cloud Manager. Fai clic su **Aggiungi**, quindi seleziona **Aggiungi pipeline non di produzione**.

   ![Aggiungi pipeline non di produzione](/help/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. Sulla scheda **Configurazione** della finestra di dialogo **Aggiungi pipeline non di produzione**, seleziona il tipo di pipeline da creare oppure **Pipeline di qualità del codice** o **Pipeline di implementazione**.

   ![Scegli il tipo di pipeline](/help/assets/configure-pipelines/add-non-production-pipeline.png)

1. Fornisci una descrizione della pipeline nel campo **Nome della pipeline non di produzione**.

1. Se hai scelto di aggiungere una **Pipeline di implementazione**, seleziona l’ambiente di distribuzione di destinazione dal menu a discesa **Ambienti di implementazione idonei**.

1. Fornisci l’archivio in cui la pipeline deve recuperare il codice.

   * **Archivio**: definisce da quale archivio Git la pipeline deve recuperare il codice.
   * **Ramo Git**: definisce il ramo della pipeline selezionata dal quale deve essere recuperato il codice.

1. Definisci le opzioni di implementazione.

   1. In **Trigger di implementazione**, definisci l’evento che attiva la pipeline.

      * **Manuale**: ti consente di avviare manualmente la pipeline.
      * **Cambiamenti su Git**: avvia la pipeline ogni volta che vengono aggiunti dei commit al ramo Git configurato. Con questa opzione, puoi comunque avviare la pipeline manualmente in base alle esigenze.

   1. Per le pipeline di implementazione, in **Comportamento in caso di errori di metriche importanti**, definisci il comportamento della pipeline quando si verifica un errore importante in uno qualsiasi dei gate di qualità.

      * **Chiedi sempre**: impostazione predefinita che richiede l’intervento manuale per tutti gli errori importanti.
      * **Interrompi subito**: la pipeline viene annullata ogni volta che si verifica un errore importante. In sostanza, questa opzione simula il rifiuto manuale di ogni errore da parte dell’utente.
      * **Continua immediatamente**: la pipeline procede automaticamente ogni volta che si verifica un errore importante. In sostanza, quest’opzione simula l’approvazione manuale di ogni errore da parte dell’utente.

   1. **Configurazione Dispatcher**: il ruolo di **Responsabile della distribuzione** può configurare un set di percorsi di contenuto che verranno invalidati o svuotati dalla cache del Dispatcher AEM quando viene eseguita una pipeline. Queste azioni della cache vengono eseguite come parte del passaggio di implementazione della pipeline, subito dopo la distribuzione di eventuali pacchetti di contenuto. Queste impostazioni utilizzano il comportamento standard del Dispatcher AEM. Per configurare:

      1. Nel **PERCORSO** fornisci un percorso di contenuto.
      1. In **TIPO**, seleziona l’azione da intraprendere su quel percorso.

         * **Scaricamento**: esegui un’eliminazione della cache.
         * **Invalida**: esegui un’invalidazione della cache, simile a quando il contenuto viene attivato da un’istanza di authoring a un’istanza di pubblicazione.

      1. Fai clic su **Aggiungi percorso** per aggiungere il percorso specificato. Puoi aggiungere fino a 100 percorsi per ambiente.

1. Fai clic su **Salva**.

## Passaggi successivi {#the-next-steps}

Dopo aver configurato la pipeline, puoi distribuire il codice. Per ulteriori dettagli, consulta la sezione [Distribuzione del codice](/help/using/code-deployment.md).

## Tutorial video {#video-tutorial}

Questo video fornisce una panoramica del processo di creazione della pipeline, descritto in questo documento.

>[!VIDEO](https://video.tv.adobe.com/v/26316/)
