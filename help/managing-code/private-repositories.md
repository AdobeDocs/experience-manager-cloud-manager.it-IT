---
title: Aggiungere archivi privati in Cloud Manager
description: Scopri come configurare Cloud Manager per l’utilizzo di archivi GitHub privati.
feature: Release Information
exl-id: e0d103c9-c147-4040-bf53-835e93d78a0b
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 38%

---


# Aggiungere archivi privati in Cloud Manager {#private-repositories}

Scopri come configurare Cloud Manager per l’utilizzo di archivi GitHub privati.

## Panoramica {#overview}

La configurazione di Cloud Manager con gli archivi GitHub privati consente di convalidare il codice direttamente in GitHub, eliminando la necessità di sincronizzarsi frequentemente con l’archivio Adobe.

>[!NOTE]
>
>Questa funzionalità è esclusiva di GitHub pubblico. Il supporto per GitHub self-hosted non è disponibile.

## Configurazione {#configuration}

La configurazione consiste di due passaggi principali:

1. [Aggiungi archivio](#add-repo)
1. [Convalida della proprietà dell’archivio privato](#validate-ownership)

### Aggiungi archivio {#add-repo}

1. In Cloud Manager, dalla pagina **Panoramica del programma**, fare clic sulla scheda **Archivi** per passare alla pagina **Archivi** e fare clic su **Aggiungi archivio**.

1. Nella finestra di dialogo **Aggiungi archivio**, seleziona **Archivio privato** come tipo di archivio.

1. Specifica i dettagli dell’archivio

   * **Nome archivio**: un nome espressivo
   * **URL archivio**: l’URL dell’archivio, che deve terminare con `.git`
   * **Descrizione** (facoltativa): una descrizione più lunga dell’archivio in base alle esigenze

   ![Aggiungi un archivio personale](/help/assets/repositories/add-own-github.png)

1. Fai clic su **Salva**.

>[!TIP]
>
>Per informazioni dettagliate sulla gestione degli archivi in Cloud Manager, vedere [Archivi Cloud Manager](/help/managing-code/managing-repositories.md).

### Convalida della proprietà dell’archivio privato {#validate-ownership}

Cloud Manager ora è a conoscenza del tuo archivio GitHub, ma deve ancora accedervi. Per concedere l’accesso, devi installare l’app Adobe GitHub e verificare di essere il proprietario dell’archivio specificato.

1. Dopo aver aggiunto il tuo repository, viene visualizzata la finestra di dialogo **Convalida proprietà repository privato**.

   ![Convalida delle proprietà dell’archivio privato](/help/assets/repositories/private-repo-validate.png)

1. Cloud Manager utilizza un’app GitHub per interagire con l’archivio in modo sicuro.

   Un proprietario dell&#39;organizzazione GitHub deve installare l&#39;app in `https://github.com/apps/cloud-manager-for-aem` e concedere l&#39;accesso all&#39;archivio. Per informazioni dettagliate, consulta la documentazione di GitHub.

1. Per migliorare la sicurezza, crea un file segreto nel ramo predefinito dell’archivio. Fai clic su **Genera**.

1. Confermare la generazione del file segreto facendo clic su **Conferma**.

   ![Conferma la generazione del segreto](/help/assets/repositories/confirm-generation.png)

1. Nella finestra di dialogo **Convalida proprietà archivio privato**, Cloud Manager ha generato il contenuto nel campo **Contenuto file segreto**. Copia il contenuto da quel campo.

   Il contenuto del file segreto viene visualizzato una sola volta. Se non si copia il contenuto prima di chiudere la finestra, è necessario rigenerare il segreto.

   ![Copia il contenuto del file segreto](/help/assets/repositories/new-secret.png)

1. Crea un nuovo file nel ramo predefinito dell’archivio GitHub denominato `.well-known/adobe/cloud-manager-challenge` e incolla il contenuto del file segreto in tale file e salvalo.

1. Dopo che l&#39;app è stata installata e il file segreto esiste nel repository, è possibile fare clic su **Convalida** nella finestra di dialogo **Convalida proprietà repository privato**.

L’app può essere installata e puoi generare un file segreto in qualsiasi ordine. Tuttavia, entrambi i passaggi devono essere completati prima di poter eseguire la convalida.

Fino alla convalida, l’archivio viene elencato con un’icona rossa, a indicare che non è ancora stato convalidato e non può ancora essere utilizzato.

![Archivio non convalidato](/help/assets/repositories/unvalidated-repo.png)

Tieni presente che la colonna **Tipo** identifica facilmente gli archivi forniti da Adobe (**Adobe**) e i tuoi archivi GitHub (**GitHub**).

Per tornare al repository in un secondo momento e completare la convalida, passare alla pagina **Archivi**. Fai clic sul pulsante con i puntini di sospensione accanto all&#39;archivio GitHub aggiunto e seleziona **Convalida proprietà** dal menu a discesa.

## Utilizzare archivi privati con Cloud Manager {#using}

Dopo la convalida dell’archivio GitHub in Cloud Manager, l’integrazione viene completata e puoi utilizzare l’archivio con Cloud Manager.

1. Quando crei una richiesta di pull, viene avviato automaticamente un controllo GitHub.

   ![Verifiche GitHub](/help/assets/repositories/github-checks.png)

1. Per ogni richiesta di pull, viene creata automaticamente una [pipeline di qualità del codice full stack](/help/using/managing-pipelines.md). Tale pipeline viene avviata ogni volta che la richiesta pull viene aggiornata.

1. Il controllo GitHub rimane in esecuzione fino al completamento dei controlli di qualità del codice. I risultati della qualità del codice vengono quindi propagati al controllo GitHub.

   ![Controlli di qualità del codice GitHub](/help/assets/repositories/github-code-quality.png)

Quando la richiesta pull viene chiusa o unita, la pipeline di qualità del codice full-stack creata viene eliminata automaticamente.

>[!TIP]
>
>Consulta il documento [Annotazioni di verifica GitHub](github-annotations.md) per informazioni dettagliate sulle informazioni fornite tramite GitHub quando vengono eseguite le verifiche delle richieste pull.

>[!TIP]
>
>Puoi controllare le pipeline create automaticamente per convalidare ogni richiesta pull in un archivio privato. Per ulteriori informazioni, vedi [Configurazione controllo GitHub per archivi privati](github-check-config.md).

## Associare archivi privati alle pipeline {#pipelines}

Gli archivi privati convalidati possono essere associati a [pipeline full stack](/help/overview/ci-cd-pipelines.md).

## Limitazioni {#limitations}

Quando si utilizzano archivi privati con Cloud Manager si applicano determinate limitazioni.

* Non è possibile sospendere la convalida della richiesta di pull utilizzando il controllo GitHub di Cloud Manager. Se l’archivio GitHub viene convalidato in Cloud Manager, Cloud Manager tenta di convalidare le richieste pull create per tale archivio.
* Se l’app GitHub di Adobe viene rimossa dall’organizzazione GitHub, questa azione rimuove la funzione di convalida delle richieste di pull per tutti gli archivi.
* Quando si utilizzano archivi privati su pipeline full stack di produzione, non viene creato e inviato alcun tag Git.
* Le pipeline che utilizzano archivi privati e il trigger di creazione su conferma non vengono avviate automaticamente quando viene eseguito il push di una nuova conferma nel ramo selezionato.
* La [funzionalità di riutilizzo degli artefatti](/help/getting-started/project-setup.md#build-artifact-reuse) non si applica agli archivi privati.
