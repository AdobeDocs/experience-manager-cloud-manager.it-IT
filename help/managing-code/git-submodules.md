---
title: Supporto per i sottomoduli Git
description: Scopri come i sottomoduli Git possono essere utilizzati per unire il contenuto di più rami tra archivi Git diversi in fase di creazione.
exl-id: f946d7e7-114a-4e33-bb82-2625d37bba2f
source-git-commit: e93285f7c7495ec9d2f11d289adaf6aaba7e58ea
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 100%

---

# Supporto dei sottomoduli Git per gli archivi Adobe {#git-submodule-support}

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

## Limitazioni  {#limitations}

Quando utilizzi i sottomoduli Gt, tieni presente che:

* L’URL Git deve avere esattamente la sintassi descritta sopra.
* Per motivi di sicurezza, non incorporare le credenziali in questi URL.
* Sono supportati solo i sottomoduli nella directory principale del ramo.
* I riferimenti ai sottomoduli Git vengono archiviati in commit specifici Git.
   * Di conseguenza, quando vengono apportate modifiche all’archivio dei sottomoduli, il commit a cui si fa riferimento deve essere aggiornato, ad esempio, utilizzando `git submodule update --remote`.
* Se non diversamente necessario, consigliamo vivamente di utilizzare sottomoduli “superficiali”.
   * Per farlo, esegui `git config -f .gitmodules submodule.<submodule path>.shallow true` per ciascun sottomodulo.


## Supporto dei sottomoduli Git per archivi privati {#private-repositories}

Il supporto dei sottomoduli Git quando si utilizzano [archivi privati](private-repositories.md) è in gran parte lo stesso di quando si utilizzano archivi Adobe.

Tuttavia, dopo aver configurato il file `pom.xml` e aver eseguito i comandi `git submodule`, affinché Cloud Manager possa rilevare la configurazione del sottomodulo è necessario aggiungere un file `.gitmodules` nella directory principale dell’archivio dell’aggregatore.

![File .gitmodules](assets/gitmodules.png)

![Aggregatore](assets/aggregator.png)

### Limitazioni e consigli {#limitations-recommendations-private-repos}

Quando utilizzi dei sottomoduli Git con archivi privati, tieni presente le seguenti limitazioni.

* Gli URL Git per i sottomoduli possono essere in formato HTTPS o SSH, ma devono essere collegati a un archivio github.com
   * L’aggiunta di un sottomodulo dell’archivio Adobe a un archivio di aggregazione GitHub o viceversa non funziona.
* I sottomoduli GitHub devono essere accessibili all’app GitHub Adobe.
* Si applicabili anche le [limitazioni dell’utilizzo dei sottomoduli Git con archivi gestiti da Adobe](#limitations-recommendations).
