---
title: Aggiunta di archivi privati in Cloud Manager
description: Scopri come configurare Cloud Manager per l’utilizzo di archivi GitHub privati.
feature: Release Information
exl-id: e0d103c9-c147-4040-bf53-835e93d78a0b
source-git-commit: 15e733117b4458cc53dec309dad5bde8cb17029f
workflow-type: tm+mt
source-wordcount: '855'
ht-degree: 100%

---


# Aggiunta di archivi privati in Cloud Manager {#private-repositories}

Scopri come configurare Cloud Manager per l’utilizzo di archivi GitHub privati.

## Panoramica {#overview}

Con la configurazione di Cloud Manager per l’utilizzo di archivi GitHub privati, puoi convalidare il codice direttamente all’interno dell’archivio GitHub tramite Cloud Manager, eliminando la necessità di sincronizzare in modo coerente il codice con l’archivio Adobe.

>[!NOTE]
>
>Questa funzionalità è esclusiva di GitHub pubblico. Il supporto per GitHub self-hosted non è disponibile.

## Configurazione {#configuration}

La configurazione consiste di due passaggi principali:

1. [Aggiungi archivio](#add-repo)
1. [Convalida della proprietà dell’archivio privato](#validate-ownership)

### Aggiungi archivio {#add-repo}

1. In Cloud Manager, nella pagina **Panoramica programma**, tocca o fai clic sulla scheda **Archivi** per passare alla pagina **Archivi** e fai clic su **Aggiungi archivio**.

1. Nella finestra di dialogo **Aggiungi archivio**, seleziona **Archivio privato** come tipo di archivio.

1. Specifica i dettagli dell’archivio

   * **Nome archivio**: un nome espressivo
   * **URL archivio**: l’URL dell’archivio, che deve terminare con `.git`
   * **Descrizione** (facoltativa): una descrizione più lunga dell’archivio in base alle esigenze

   ![Aggiungi un archivio personale](/help/assets/repositories/add-own-github.png)

1. Tocca o fai clic su **Salva**.

>[!TIP]
>
>Per informazioni dettagliate sulla gestione degli archivi in Cloud Manager, consulta il documento [Archivi di Cloud Manager.](/help/managing-code/managing-repositories.md)

### Convalida della proprietà dell’archivio privato {#validate-ownership}

Cloud Manager ora è a conoscenza del tuo archivio GitHub, ma deve ancora accedervi. Per concedere l’accesso, devi installare l’app Adobe GitHub e verificare di essere il proprietario dell’archivio specificato.

1. Dopo l’aggiunta del tuo archivio personale, verrà visualizzata la finestra di dialogo **Convalida delle proprietà dell’archivio privato**.

   ![Convalida delle proprietà dell’archivio privato](/help/assets/repositories/private-repo-validate.png)

1. Cloud Manager utilizza un’app GitHub per interagire in modo sicuro con l’archivio.
   * Un proprietario dell’organizzazione GitHub deve installare l’app che si trova in `https://github.com/apps/cloud-manager-for-aem` e concedere l’accesso all’archivio.
   * Consulta la documentazione di GitHub per informazioni dettagliate su come eseguire questa operazione.

1. Per una maggiore sicurezza, è necessario creare un file segreto nel ramo predefinito dell’archivio. Tocca o fai clic su **Genera**.

1. Conferma la generazione del file segreto toccando o facendo clic su **Conferma**.

   ![Conferma la generazione del segreto](/help/assets/repositories/confirm-generation.png)

1. Nella finestra **Convalida delle proprietà dell’archivio privato**, Cloud Manager ha generato il contenuto del file privato nel campo **Contenuto file segreto**. Copia il contenuto da quel campo.

   * Il contenuto del file segreto verrà visualizzato una sola volta. Se non copi il contenuto prima di chiudere questa finestra, dovrai generare nuovamente il segreto.

   ![Copia il contenuto del file segreto](/help/assets/repositories/new-secret.png)

1. Crea un nuovo file nel ramo predefinito dell’archivio GitHub denominato `.well-known/adobe/cloud-manager-challenge` e incolla il contenuto del file segreto in tale file e salvalo.

1. Una volta installata l’app e il file segreto è presente nell’archivio, puoi toccare o fare clic su **Convalida** nella finestra di dialogo **Convalida delle proprietà dell’archivio privato**.

L’app può essere installata e il file segreto può essere creato in qualsiasi ordine. Tuttavia, entrambi i passaggi devono essere completati prima di poter eseguire la convalida.

Fino alla convalida, l’archivio viene elencato con un’icona rossa, a indicare che non è ancora stato convalidato e non può ancora essere utilizzato.

![Archivio non convalidato](/help/assets/repositories/unvalidated-repo.png)

Tieni presente che la colonna **Tipo** identifica facilmente gli archivi forniti da Adobe (**Adobe**) e i tuoi archivi GitHub (**GitHub**).

Se per completare la convalida devi tornare all’archivio in un momento successivo, nella pagina **Archivi** tocca o fai clic sul pulsante con i puntini di sospensione nella riga che rappresenta l’archivio GitHub appena aggiunto e seleziona **Convalida proprietà** dal menu a discesa.

## Utilizzo di archivi privati con Cloud Manager {#using}

Dopo la convalida dell’archivio GitHub in Cloud Manager, l’integrazione è completata e puoi utilizzare l’archivio con Cloud Manager.

1. Quando crei una richiesta pull, viene avviata automaticamente una verifica GitHub.

   ![Verifiche GitHub](/help/assets/repositories/github-checks.png)

1. Per ogni richiesta pull, verrà creata automaticamente una [pipeline di qualità del codice full stack](/help/using/managing-pipelines.md). Tale pipeline viene avviata ogni volta che la richiesta pull viene aggiornata.

1. La verifica GitHub rimane in esecuzione fino al completamento dei controlli di qualità del codice. I risultati di qualità del codice verranno propagati quindi alla verifica GitHub.

   ![Controlli di qualità del codice GitHub](/help/assets/repositories/github-code-quality.png)

Quando la richiesta pull viene chiusa o unita, la pipeline di qualità del codice full-stack creata viene eliminata automaticamente.

>[!TIP]
>
>Consulta il documento [Annotazioni di verifica GitHub](github-annotations.md) per informazioni dettagliate sulle informazioni fornite tramite GitHub quando vengono eseguite le verifiche delle richieste pull.

>[!TIP]
>
>Puoi controllare le pipeline create automaticamente per convalidare ogni richiesta pull in un archivio privato. Per ulteriori informazioni, consulta il documento [Configurazione verifica GitHub per archivi privati](github-check-config.md).

## Associazione di archivi privati alle pipeline {#pipelines}

Gli archivi privati convalidati possono essere associati a [pipeline full-stack.](/help/overview/ci-cd-pipelines.md)

## Limitazioni {#limitations}

Quando si utilizzano archivi privati con Cloud Manager si applicano determinate limitazioni.

* Non puoi mettere in pausa la convalida della richiesta pull tramite la verifica GitHub di Cloud Manager.
   * Se l’archivio GitHub viene convalidato in Cloud Manager, Cloud Manager tenterà sempre di convalidare le richieste pull create per quell’archivio.
* Se l’app GitHub di Adobe viene rimossa dall’organizzazione GitHub, la funzione di convalida delle richieste pull verrà rimossa per tutti gli archivi.
* Quando si utilizzano archivi privati su pipeline di produzione full stack, non verrà creato e inviato alcun tag Git.
* Le pipeline che utilizzano archivi privati e il trigger di creazione su conferma non vengono avviate automaticamente quando viene eseguito il push di una nuova conferma nel ramo selezionato.
* La [funzionalità di riutilizzo degli artefatti](/help/getting-started/project-setup.md#build-artifact-reuse) non si applica agli archivi privati.
