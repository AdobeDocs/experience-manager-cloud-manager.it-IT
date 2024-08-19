---
title: Supporto per i sottomoduli Git
description: Scopri come utilizzare i sottomoduli Git per unire il contenuto di più rami tra archivi Git in fase di creazione.
exl-id: f946d7e7-114a-4e33-bb82-2625d37bba2f
source-git-commit: 11a6a53d8cbfb689810a9a8e7d82293a49863084
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 28%

---

# Supporto dei moduli Git secondari per gli archivi Adobe {#git-submodule-support}

I sottomoduli Git possono essere utilizzati per unire il contenuto di più rami tra archivi Git in fase di creazione.

Quando il processo di build di Cloud Manager viene eseguito, prima clona l’archivio della pipeline ed estrae il ramo configurato. Se il ramo contiene un file `.gitmodules` nella directory radice, il comando viene eseguito.

```
$ git submodule update --init
```

Questo processo estrae ogni sottomodulo nella directory appropriata. Questa tecnica rappresenta una potenziale alternativa all&#39;utilizzo di [più archivi Git di origine](/help/managing-code/multiple-git-repos.md) per le organizzazioni che hanno familiarità con l&#39;utilizzo dei sottomoduli Git e che non desiderano gestire un processo di unione esterno.

Supponiamo ad esempio la presenza di tre archivi, ciascuno contenente un singolo ramo denominato `main`. Nell&#39;archivio &quot;principale&quot;, ovvero quello configurato nelle pipeline, il ramo `main` ha un file `pom.xml` che dichiara i progetti contenuti negli altri due archivi:

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

Quindi aggiungi i sottomoduli per gli altri due archivi:

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

Per ulteriori informazioni sui sottomoduli Git, consultare il [Manuale di riferimento Git](https://git-scm.com/book/en/v2/Git-Tools-Submodules).

## Limitazioni {#limitations}

Quando utilizzi i moduli Git secondari, tieni presente quanto segue:

* L’URL Git deve avere esattamente la sintassi descritta sopra.
* Per motivi di sicurezza, non incorporare le credenziali in questi URL.
* Sono supportati solo i sottomoduli nella directory principale del ramo.
* I riferimenti ai sottomoduli Git vengono memorizzati in commit Git specifici. Di conseguenza, quando vengono apportate modifiche all’archivio dei sottomoduli, il commit a cui si fa riferimento deve essere aggiornato. Ad esempio, utilizzando `git submodule update --remote`.
* Se non diversamente necessario, Adobe consiglia di utilizzare sottomoduli &quot;superficiali&quot; eseguendo `git config -f .gitmodules submodule.<submodule path>.shallow true` per ogni sottomodulo.


## Supporto dei moduli Git secondari per archivi privati {#private-repositories}

Il supporto per i sottomoduli Git quando si utilizzano [archivi privati](private-repositories.md) è in gran parte lo stesso di quando si utilizzano archivi Adobe.

Tuttavia, dopo aver configurato il file `pom.xml` e aver eseguito i comandi `git submodule`, affinché Cloud Manager possa rilevare la configurazione del sottomodulo è necessario aggiungere un file `.gitmodules` nella directory principale dell’archivio dell’aggregatore.

![File .gitmodules](assets/gitmodules.png)

![Aggregatore](assets/aggregator.png)

### Limitazioni e raccomandazioni {#limitations-recommendations-private-repos}

Quando utilizzi dei sottomoduli Git con archivi privati, tieni presente le seguenti limitazioni.

* Gli URL Git per i sottomoduli possono essere in formato HTTPS o SSH, ma devono essere collegati a un archivio Github.com. L’aggiunta di un sottomodulo dell’archivio Adobe a un archivio di aggregazione GitHub o viceversa non funziona.
* I sottomoduli GitHub devono essere accessibili all’app GitHub Adobe.
* Si applicabili anche le [limitazioni dell’utilizzo dei sottomoduli Git con archivi gestiti da Adobe](#limitations-recommendations).
