---
title: Repository di Cloud Manager
description: Scopri come accedere, creare e modificare archivi per i programmi Cloud Manager.
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 2%

---


# Repository di Cloud Manager {#cloud-manager-repos}

Gli archivi sono il luogo in cui gestisci il codice utilizzando git. Scopri come creare archivi per i programmi Cloud Manager.

## Accesso agli archivi {#accessing-repos}

Puoi accedere e gestire gli archivi Git in un self-service da Cloud Manager.

Per accedere al tuo archivio, utilizza le **Accesso alle informazioni sul repository** pulsante disponibile in Cloud Manager, che si trova principalmente sulla scheda della pipeline.

1. Accedi a Cloud Manager all&#39;indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) e selezionare l&#39;organizzazione e il programma appropriati.

1. Passa a **Tubi** scheda da **Panoramica del programma** e visualizzerai la pagina **Accesso alle informazioni sul repository** opzione per accedere e gestire l’archivio git [con questa pipeline.](/help/using/production-pipelines.md)

   ![Pulsante Informazioni repository](/help/assets/access-repo1.png)

1. Se passi alla **Non produzione** scheda pipeline **Accesso alle informazioni sul repository** è disponibile anche in questo caso, in quanto [configurato per la pipeline.](/help/using/non-production-pipelines.md)

   ![gasdotti non di produzione](/help/assets/access-repo-nonprod.png)

1. Fai clic sul pulsante **Accesso alle informazioni sul repository** per aprire una finestra di dialogo che presenta:

   * URL dell’archivio Git
   * Nome utente
   * Password
   * Comando Git da eseguire per clonare l’archivio localmente

   ![Finestra di dialogo Informazioni archivio](/help/assets/access-repo-create.png)

Utilizza le informazioni fornite per clonare l’archivio localmente in modo da poter iniziare lo sviluppo locale.

>[!NOTE]
>
>La **Accesso alle informazioni sul repository** è visibile agli utenti nella **Sviluppatore** o **Gestione distribuzione** ruolo.

## Aggiunta di archivi {#add-repos}

Per aggiungere archivi in Cloud Manager, effettua le seguenti operazioni:

1. Accedi a Cloud Manager all&#39;indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) e selezionare l&#39;organizzazione e il programma appropriati.

1. Da **Panoramica del programma** pagina, fai clic su **Repository** e passa alla **Repository** pagina.

1. Fai clic su **Aggiungi archivio** per avviare la procedura guidata.

   >[!NOTE]
   >
   >Devi avere la **Gestione distribuzione** o **Proprietario business** ruolo per aggiungere un archivio.

   ![Aggiungi archivio](/help/assets/create-repo2.png)

1. Inserisci il nome e la descrizione come richiesto e fai clic su **Salva**.

   ![Dettagli sulle operazioni pronti contro termine](/help/assets/repo-1.png)

1. Seleziona **Salva**.

Verrà visualizzato il repository appena creato.

![Nuovo repository creato](/help/assets/create-repo3.png)

Gli archivi creati in Cloud Manager sono disponibili per la selezione quando [crea le tubazioni.](/help/overview/ci-cd-pipelines.md)

## Visualizzare e modificare gli archivi {#edit-repos}

Segui questi passaggi per modificare e visualizzare gli archivi in Cloud Manager:

1. Accedi a Cloud Manager all&#39;indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) e selezionare l&#39;organizzazione e il programma appropriati.

1. Da **Panoramica del programma** pagina, fai clic su **Repository** e passa alla **Repository** pagina. Qui puoi visualizzare i dettagli degli archivi esistenti.

1. Seleziona l’archivio e fai clic sul pulsante con i puntini di sospensione all’estrema destra della tabella per **Copia URL archivio**, **Visualizza e aggiorna** o **Elimina** l’archivio.

![Modifica repository](/help/assets/create-repo3.png)

## Supporto per i sottomoduli Git {#git-submodule-support}

I sottomoduli Git possono essere utilizzati per unire il contenuto di più rami tra archivi Git in fase di creazione.

Quando viene eseguito il processo di creazione di Cloud Manager, dopo che l’archivio configurato per la pipeline è stato clonato e il ramo configurato viene estratto, se il ramo contiene un `.gitmodules` file nella directory principale, il comando viene eseguito.

```
$ git submodule update --init
```

In questo modo, ogni sottomodulo verrà sottoposto a Check-Out nella directory appropriata. Questa tecnica è una potenziale alternativa a [utilizzo di più archivi Git di origine](/help/managing-code/multiple-git-repos.md) per le organizzazioni che hanno familiarità con l’utilizzo dei sottomoduli git e che non desiderano gestire un processo di unione esterno.

Ad esempio, supponiamo che ci siano tre archivi, ciascuno contenente un singolo ramo denominato `main`. Nell’archivio &quot;principale&quot;, ovvero quello configurato nelle pipeline, la `main` un ramo `pom.xml` file che dichiara i progetti contenuti negli altri due archivi:

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

Questo determina un `.gitmodules` file con questo aspetto:

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

Ulteriori informazioni sui sottomoduli git sono disponibili nella sezione [Manuale di riferimento Git](https://git-scm.com/book/en/v2/Git-Tools-Submodules).

### Limitazioni  {#limitations}

Quando utilizzi i sottomoduli git, tieni presente quanto segue:

* L’URL Git deve essere esattamente nella sintassi descritta sopra.
* Per motivi di sicurezza, non incorporare le credenziali in questi URL.
* Sono supportati solo i sottomoduli nella directory principale del ramo.
* I riferimenti ai sottomoduli Git vengono archiviati in commit specifici Git.
   * Di conseguenza, quando vengono apportate modifiche all’archivio dei sottomoduli, il commit a cui si fa riferimento deve essere aggiornato, ad esempio, utilizzando `git submodule update --remote`.
* Se non diversamente necessario, si consiglia vivamente di utilizzare sottomoduli &quot;superficiali&quot;.
   * Per eseguire questa operazione, esegui `git config -f .gitmodules submodule.<submodule path>.shallow true` per ciascun sottomodulo.
