---
title: Gestione degli archivi in Cloud Manager
description: Scopri come visualizzare, aggiungere ed eliminare gli archivi Git in Cloud Manager.
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '730'
ht-degree: 97%

---


# Gestione degli archivi in Cloud Manager {#cloud-manager-repos}

Scopri come visualizzare, aggiungere ed eliminare un archivio Git in Cloud Manager.

## Panoramica {#overview}

Gli archivi in Cloud Manager vengono utilizzati per archiviare e gestire il codice del progetto utilizzando Git. Per ogni *programma* aggiunto, viene automaticamente creato un archivio gestito da Adobe.

Inoltre, è disponibile l’opzione per creare altri archivi gestiti da Adobe e i tuoi archivi privati. Tutti gli archivi collegati al programma possono essere visualizzati nella pagina **Archivi**.

Gli archivi creati in Cloud Manager possono essere selezionati anche durante l’aggiunta o la modifica delle pipeline. Per ulteriori informazioni sulla configurazione delle pipeline, consulta [Pipeline CI/CD](/help/overview/ci-cd-pipelines.md).

Ogni pipeline è collegata a un archivio principale o a un ramo. Grazie al [supporto dei sottomoduli Git](/help/managing-code/git-submodules.md), tuttavia, durante il processo di creazione è possibile aggiungere numerosi rami secondari.

## Visualizzare la pagina Archivi {#repositories-window}

Nella pagina **Archivi** è possibile visualizzare i dettagli dell’archivio selezionato. Tra le informazioni disponibili è incluso anche il tipo di archivio in uso. Se l’archivio è contrassegnato come **Adobe**, significa che si tratta di un archivio gestito da Adobe. Se invece è etichettato come **GitHub**, fa riferimento a un archivio GitHub privato che gestisci tu direttamente. Nella pagina viene specificato anche quando è stato creato l’archivio e quali sono le pipeline associate.

Per intervenire su un archivio selezionato, è possibile fare clic su di esso e utilizzare l’![icona Altro](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) per aprire un menu a discesa. Per gli archivi gestiti da Adobe è disponibile l’opzione **[Controlla rami/Crea progetto](#check-branches)**.

![Azioni archivio](assets/repository-actions.png)
*Menu a discesa nella pagina Archivi.*

Altre azioni disponibili nel menu a discesa includono **[Copia URL archivio](#copy-url)**, **[Visualizza e aggiorna](#view-update)** ed **[Elimina](#delete)** l’archivio.

**Per visualizzare la pagina Archivi:**

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Nella pagina **Panoramica del programma**, dal menu laterale selezionare l’![icona Cartella](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **Archivi**.

1. Nella finestra **Archivi** vengono visualizzati tutti gli archivi associati al programma selezionato.

   ![Pagina Archivi](assets/repositories.png)
   *Pagina Archivi in Cloud Manager.*


## Aggiungere un archivio {#adding-repositories}

Per poter aggiungere un archivio, l’utente deve avere il ruolo di **Responsabile della distribuzione** o **Proprietario business**.

Nella pagina **Archivi** fai clic sull’opzione **Aggiungi archivio** nell’angolo in alto a destra.

![Finestra di dialogo Aggiungi archivio.](assets/repository-add.png)
*Finestra di dialogo Aggiungi archivio.*

Cloud Manager supporta due tipi di archivi: gli archivi gestiti da Adobe (**Archivio Adobe**) e quelli che puoi gestire direttamente (**Archivio privato**). I campi obbligatori dipendono dal tipo di archivio che scegli di aggiungere. Per ulteriori informazioni, consulta:

* [Aggiungere archivi Adobe in Cloud Manager](/help/managing-code/adobe-repositories.md)
* [Aggiungere archivi privati in Cloud Manager](/help/managing-code/private-repositories.md)

Per ogni azienda o organizzazione IMS, vi è un limite di 300 archivi per tutti i programmi.

## Accedere alle informazioni sull’archivio {#repo-info}

Quando visualizzi gli archivi nella finestra **Archivi**, puoi visualizzare i dettagli su come accedere agli archivi gestiti da Adobe a livello di programmazione facendo clic sul pulsante **Accedi a dati archivio** nella barra degli strumenti.

![Informazioni sull’archivio](assets/repository-access-repo-info2.png)

La finestra **Informazioni archivio** si apre con i dettagli. Per ulteriori informazioni sull’accesso alle informazioni dell’archivio, consulta [Accesso alle informazioni sull’archivio](/help/managing-code/accessing-repositories.md).

## Controlla rami/Crea progetto {#check-branches}

In **AEM Cloud Manager**, **Controlla rami/Crea progetto** ha due scopi, a seconda dello stato corrente dell&#39;archivio.

* Se l’archivio è stato appena creato, questa azione genera un progetto di esempio basato sull’[Archetipo progetto AEM](https://experienceleague.adobe.com/it/docs/experience-manager-core-components/using/developing/archetype/overview).
* Se il progetto di esempio è già stato creato nell’archivio, l’azione verifica lo stato dell’archivio e dei relativi rami, fornendo feedback sull’esistenza o meno del progetto di esempio.

  ![Azione Controlla rami](assets/check-branches.png)

## Copiare l’URL dell’archivio {#copy-url}

L’azione **Copia URL archivio** copia negli Appunti l’URL dell’archivio selezionato nella finestra **Archivi** per utilizzarlo altrove.

## Visualizzare e aggiornare un archivio {#view-update}

L’azione **Visualizza e aggiorna** apre la finestra di dialogo **Aggiorna archivio**, in cui è possibile visualizzare il **Nome** e l’**Anteprima URL dell’archivio**. Inoltre consente di aggiornare la **Descrizione** dell’archivio.

![Visualizzare e aggiornare le informazioni del dell’archivio](assets/repository-view-update.png)

## Eliminare un archivio {#delete}

L’azione **Elimina** rimuove l’archivio dal progetto. Un archivio non può essere eliminato se è associato a una pipeline.

![Eliminazione di un archivio](assets/delete.png)

Quando un archivio viene eliminato in Cloud Manager, viene contrassegnato come eliminato e non è più accessibile all’utente. Tuttavia, viene mantenuto nel sistema per scopi di ripristino.

Se tenti di creare un nuovo archivio dopo averne eliminato uno con lo stesso nome, riceverai il messaggio di errore seguente:

`An error has occurred while trying to create repository. Contact your CSE or Adobe Support.`

Se ricevi questo messaggio di errore, contatta il supporto Adobe. Ti potrà aiutare a rinominare l’archivio eliminato o a scegliere un nome diverso per il nuovo archivio.
