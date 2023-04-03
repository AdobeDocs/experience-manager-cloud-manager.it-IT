---
title: Archivi di Cloud Manager
description: Scopri come accedere, creare e modificare gli archivi per i programmi Cloud Manager.
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966
source-git-commit: 63cbcf8724a840efa67b8fafc4c321e04a5d70d9
workflow-type: ht
source-wordcount: '796'
ht-degree: 100%

---


# Archivi di Cloud Manager {#cloud-manager-repos}

Gli archivi sono il luogo in cui gestisci il codice utilizzando Git. Scopri come creare archivi per i programmi Cloud Manager.

## Accesso agli archivi {#accessing-repos}

Puoi accedere e gestire gli archivi Git in un self-service da Cloud Manager.

Per accedere al tuo archivio, utilizza il pulsante **Accedi a dati archivio** disponibile in Cloud Manager, che si trova in primo piano sulla scheda della pipeline.

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) e seleziona l’organizzazione e il programma appropriati.

1. Passa alla scheda **Pipeline** dalla pagina **Panoramica del programma** e visualizzerai l’opzione **Accedi a dati archivio** per accedere e gestire l’archivio Git [configurato con questa pipeline.](/help/using/production-pipelines.md)

   ![Pulsante Accedi a dati archivio](/help/assets/access-repo1.png)

1. Se passi alla scheda pipeline **Non di produzione** l’opzione **Accedi a dati archivio** è disponibile anche in questo caso, in quanto [configurata per la pipeline.](/help/using/non-production-pipelines.md)

   ![Pipeline non di produzione](/help/assets/access-repo-nonprod.png)

1. Fai clic sul pulsante **Accedi a dati archivio** per aprire una finestra di dialogo che presenta:

   * L’URL dell’archivio Git
   * Nome utente
   * Password
   * Il comando Git da eseguire per clonare l’archivio in locale

   ![Finestra di dialogo Informazioni archivio](/help/assets/access-repo-create.png)

Utilizza le informazioni fornite per clonare l’archivio in locale in modo da poter iniziare lo sviluppo locale.

>[!NOTE]
>
>L’opzione **Accedi a dati archivio** è visibile agli utenti con il ruolo di **Sviluppatore** o **Responsabile della distribuzione**.

## Aggiunta di archivi {#add-repos}

Per aggiungere archivi in Cloud Manager, segui i passaggi seguenti:

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) e seleziona l’organizzazione e il programma appropriati.

1. Dalla pagina **Panoramica del programma**, fai clic sulla scheda **Archivi** e passa alla pagina **Archivi**.

1. Fai clic su **Aggiungi archivio** per avviare la procedura guidata.

   >[!NOTE]
   >
   >Per aggiungere un archivio devi avere il ruolo di **Responsabile della distribuzione** o **Proprietario business**.

   ![Aggiungi archivio](/help/assets/create-repo2.png)

1. Inserisci il nome e la descrizione come richiesto e fai clic su **Salva**.

   ![Dettagli dell’archivio](/help/assets/repo-1.png)

1. Seleziona **Salva**.

Verrà visualizzato l’archivio appena creato.

![Nuovo archivio creato](/help/assets/create-repo3.png)

Gli archivi creati in Cloud Manager sono disponibili per la selezione quando [crei le pipeline.](/help/overview/ci-cd-pipelines.md)

## Visualizzare e modificare gli archivi {#edit-repos}

Per modificare e visualizzare gli archivi in Cloud Manager, segui i passaggi seguenti:

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) e seleziona l’organizzazione e il programma appropriati.

1. Dalla pagina **Panoramica del programma**, fai clic sulla scheda **Archivi** e passa alla pagina **Archivi**. Qui puoi visualizzare i dettagli degli archivi esistenti.

1. Seleziona l’archivio e fai clic sul pulsante con i puntini di sospensione all’estrema destra della tabella per **Copia URL archivio** o **Visualizza e aggiorna** l’archivio.

![Modifica archivio](/help/assets/create-repo3.png)

## Eliminazione degli archivi {#delete-repos}

Per eliminare un archivio, segui gli stessi passaggi [per visualizzare e modificare gli archivi](#edit-repos), ma nella pagina **Archivi** seleziona **Elimina** dal pulsante con puntini di sospensione dell’archivio da eliminare.

Nota che quando un archivio viene eliminato in Cloud Manager, viene contrassegnato come eliminato e non è più accessibile all’utente, ma viene mantenuto nel sistema a scopo di ripristino.

Se tenti di creare un nuovo archivio dopo averne eliminato uno con lo stesso nome, riceverai il messaggio di errore “Si è verificato un errore durante il tentativo di creazione dell’archivio. Contatta il CSE o il supporto Adobe.”

Se ricevi questo messaggio di errore, contatta il supporto Adobe in modo che possano aiutarti a rinominare l’archivio eliminato o scegliere un nome diverso per il tuo nuovo archivio.

## Supporto per i moduli Git secondari {#git-submodule-support}

È possibile utilizzare i moduli Git secondari per unire il contenuto di più rami tra archivi Git al momento della generazione.

Quando viene eseguito il processo di generazione di Cloud Manager, dopo che l’archivio configurato per la pipeline è stato clonato e il ramo configurato viene registrato, se il ramo contiene un file `.gitmodules` nella directory principale, il comando viene eseguito.

```
$ git submodule update --init
```

In questo modo, ogni sottomodulo verrà registrato nella directory appropriata. Questa tecnica è una potenziale alternativa all’[utilizzo di più archivi Git di origine](/help/managing-code/multiple-git-repos.md) per le organizzazioni che hanno familiarità con l’utilizzo dei sottomoduli Git e che non desiderano gestire un processo di unione esterno.

Ad esempio, supponiamo che ci siano tre archivi, ciascuno contenente un singolo ramo denominato `main`. Nell’archivio “principale”, ovvero quello configurato nelle pipeline, il ramo `main` ha un file `pom.xml` che dichiara i progetti contenuti negli altri due archivi:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
   
    <groupId>customer.group.id</groupId>
    <artifactId>customer-reactor</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <packaging>pom</packaging>
   
    <modules>
        <module>project-a</module>
        <module>project-b</module>
    </modules>
   
</project>
```

Aggiungi quindi i sottomoduli per gli altri due archivi:

```shell
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectA/ project-a
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectB/ project-b
```

Questo determina un file `.gitmodules` con questo aspetto:

```text
[submodule "project-a"]
    path = project-a
    url = https://git.cloudmanager.adobe.com/ProgramName/projectA/
    branch = main
[submodule "project-b"]
    path = project-b
    url = https://git.cloudmanager.adobe.com/ProgramName/projectB/
    branch = main
```

Ulteriori informazioni sui sottomoduli Git sono disponibili nella sezione [Manuale di riferimento Git](https://git-scm.com/book/en/v2/Git-Tools-Submodules).

### Limitazioni  {#limitations}

Quando utilizzi i sottomoduli Gt, tieni presente che:

* L’URL Git deve avere esattamente la sintassi descritta sopra.
* Per motivi di sicurezza, non incorporare le credenziali in questi URL.
* Sono supportati solo i sottomoduli nella directory principale del ramo.
* I riferimenti ai sottomoduli Git vengono archiviati in commit specifici Git.
   * Di conseguenza, quando vengono apportate modifiche all’archivio dei sottomoduli, il commit a cui si fa riferimento deve essere aggiornato, ad esempio, utilizzando `git submodule update --remote`.
* Se non diversamente necessario, consigliamo vivamente di utilizzare sottomoduli “superficiali”.
   * Per farlo, esegui `git config -f .gitmodules submodule.<submodule path>.shallow true` per ciascun sottomodulo.
