---
title: Supporto per i sottomoduli Git
description: Scopri come i moduli Git secondari possono essere utilizzati per unire il contenuto di più rami tra archivi Git diversi al momento della creazione.
exl-id: f946d7e7-114a-4e33-bb82-2625d37bba2f
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '412'
ht-degree: 100%

---

# Supporto dei moduli Git secondari per gli archivi Adobe {#git-submodule-support}

I moduli Git secondari possono essere utilizzati per unire il contenuto di più rami tra archivi Git al momento della creazione.

Quando viene eseguito il processo di creazione di Cloud Manager, per prima cosa viene clonato l’archivio della pipeline ed estratto il ramo configurato. Se il ramo contiene un file `.gitmodules` nella directory principale, allora viene eseguito il comando.

```
$ git submodule update --init
```

In questo modo, ogni modulo secondario verrà registrato nella directory appropriata. Questa tecnica è una potenziale alternativa all’[utilizzo di più archivi Git di origine](/help/managing-code/multiple-git-repos.md) per le organizzazioni che hanno familiarità con l’utilizzo dei moduli Git secondari e che non desiderano gestire un processo di unione esterno.

Ad esempio, supponiamo la presenza di tre archivi, ciascuno contenente un singolo ramo denominato `main`. Nell’archivio “principale”, ovvero quello configurato nelle pipeline, il ramo `main` include un file `pom.xml` dove sono riportati i progetti contenuti negli altri due archivi:

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

Aggiungi quindi i moduli secondari per gli altri due archivi:

```shell
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectA/ project-a
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectB/ project-b
```

I risultati nel file `.gitmodules` sono simili ai seguenti:

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

Per ulteriori informazioni sui moduli Git secondari, consulta il [Manuale di riferimento Git](https://git-scm.com/book/en/v2/Git-Tools-Submodules).

## Limitazioni {#limitations}

Quando utilizzi dei moduli Git secondari, tieni presente che:

* L’URL Git deve avere esattamente la sintassi descritta sopra.
* Per motivi di sicurezza, non incorporare le credenziali in questi URL.
* Sono supportati solo i sottomoduli nella directory principale del ramo.
* I riferimenti ai moduli secondari vengono memorizzati in commit Git specifici. Di conseguenza, quando si apportano modifiche all’archivio dei moduli secondari, il commit a cui si fa riferimento deve essere aggiornato. Ad esempio, utilizzando `git submodule update --remote`.
* Se non diversamente necessario, Adobe consiglia di utilizzare moduli secondari “base” eseguendo una `git config -f .gitmodules submodule.<submodule path>.shallow true` per ogni modulo secondario.


## Supporto dei moduli Git secondari per archivi privati {#private-repositories}

Il supporto dei moduli Git secondari quando si utilizzano [archivi privati](private-repositories.md) è in gran parte lo stesso di quando si utilizzano archivi Adobe.

Tuttavia, dopo aver configurato il file `pom.xml` e aver eseguito i comandi `git submodule`, affinché Cloud Manager possa rilevare la configurazione del sottomodulo è necessario aggiungere un file `.gitmodules` nella directory principale dell’archivio dell’aggregatore.

![File .gitmodules](assets/gitmodules.png)

![Aggregatore](assets/aggregator.png)

### Limitazioni e consigli {#limitations-recommendations-private-repos}

Quando utilizzi dei moduli Git secondari con archivi privati, tieni presente le seguenti limitazioni.

* Gli URL Git per i moduli secondari possono essere in formato HTTPS o SSH, ma devono essere collegati a un archivio Github.com. L’aggiunta di un modulo secondario dell’archivio Adobe a un archivio di aggregazione GitHub o viceversa, non funziona.
* I moduli GitHub secondari devono essere accessibili all’app GitHub di Adobe.
* Si applicano anche le [limitazioni all’utilizzo dei moduli Git secondari con archivi gestiti da Adobe](#limitations-recommendations).
