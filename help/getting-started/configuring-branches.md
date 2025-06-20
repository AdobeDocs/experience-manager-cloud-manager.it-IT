---
title: Configurazione dei rami
description: Scopri come configurare il primo ramo in Git e come viene utilizzato dalla pipeline CI/CD per distribuire il codice dell’applicazione.
exl-id: ff2ae28f-902e-4fb2-aeb1-3636cb5cd9bb
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 95%

---


# Configurare i rami {#configuring-branches}

Scopri come configurare il primo ramo in Git e come viene utilizzato dalla pipeline CI/CD per distribuire il codice dell’applicazione.

## Configura il primo ramo in Git {#setting-up-your-first-branch-in-git}

Viene [eseguito il provisioning](/help/requirements/environment-provisioning.md) di un singolo archivio Git, inizialmente vuoto, per ogni programma integrato in Cloud Manager. Questo archivio può contenere tutti i rami necessari per il processo di sviluppo, ma deve esserci almeno un ramo utilizzato dalla pipeline CI/CD per distribuire il codice dell’applicazione in staging e produzione. La best practice è quella di utilizzare `main` come nome di questo ramo. Essendo vantaggioso, questò è il comportamento predefinito dei client Git durante la configurazione di nuovi progetti.

Ad esempio, quando configuri un nuovo progetto, esegui un set di comandi simili a quelli riportati di seguito.

```shell
$ git init
Initialized empty Git repository in /Users/myname/workspace/new-project/.git/
... steps which add Maven build files and source code ...
$ git add pom.xml core/pom.xml core/src ui.apps/pom.xml ui.apps/src
$ git commit -m "initial commit"
 19 files changed, 777 insertions(+)
 create mode 100644 core/pom.xml
 create mode 100644 pom.xml
 create mode 100644 ui.apps/pom.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/config.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/definition/.content.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/filter.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/nodetypes.cnd
 create mode 100644 ui.apps/src/main/content/META-INF/vault/properties.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/apps/my-aem-project/install/.vltignore
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/policies/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/policies/_rep_policy.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/template-types/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/template-types/_rep_policy.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/templates/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/templates/_rep_policy.xml
```

>[!NOTE]
>
>Non è necessario utilizzare il client della riga di comando. Sono disponibili diversi client Git grafici come applicazioni standalone o come parte di un ambiente di sviluppo integrato (IDE, Integrated Development Environment) come Eclipse o IntelliJ. Se l’applicazione client supporta i Git che utilizzano HTTPS, dovrebbe essere compatibile con [!UICONTROL Cloud Manager].

## Invio del primo ramo {#pushing-your-first-branch}

Dopo aver eseguito il commit di almeno una revisione, puoi aggiungere l’archivio di [!UICONTROL Cloud Manager] in modalità remota e quindi eseguire l’invio dei commit.

```shell
$ git remote add adobe <url>
$ git push adobe master
Counting objects: 36, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (27/27), done.
Writing objects: 100% (36/36), 7.31 KiB | 1.83 MiB/s, done.
Total 36 (delta 6), reused 0 (delta 0)
To <url>
 * [new branch]      main -> main
```

>[!NOTE]
>
>L’URL specifico, insieme alle tue credenziali, viene fornito dal Customer Success Engineering (CSE) di Adobe durante l’onboarding di [!UICONTROL Cloud Manager].

## Rami aggiuntivi {#additional-branches}

Un singolo ramo `main` può essere sufficiente per progetti molto semplici, ma nella maggior parte dei casi sarà necessaria una strategia di ramificazione più complessa. Molti clienti seguono un processo in cui le attività di sviluppo quotidiane vengono eseguite su un ramo denominato `develop`. Il ramo `develop` viene quindi unito al ramo `main` quando è il momento di una distribuzione.

>[!TIP]
>
>Per visualizzare i comandi Git comuni, consulta la sezione [Scheda di riferimento Git](https://training.github.com/downloads/github-git-cheat-sheet).
