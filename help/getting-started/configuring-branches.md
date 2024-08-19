---
title: Configurazione dei rami
description: Scopri come configurare il primo ramo in Git e come viene utilizzato dalla pipeline CI/CD per distribuire il codice dell’applicazione.
exl-id: ff2ae28f-902e-4fb2-aeb1-3636cb5cd9bb
source-git-commit: 11a6a53d8cbfb689810a9a8e7d82293a49863084
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 14%

---


# Configurare i rami {#configuring-branches}

Scopri come configurare il primo ramo in Git e come viene utilizzato dalla pipeline CI/CD per distribuire il codice dell’applicazione.

## Configurare il primo ramo in Git {#setting-up-your-first-branch-in-git}

Inizialmente viene [eseguito il provisioning](/help/requirements/environment-provisioning.md) di un singolo archivio Git vuoto per ogni programma integrato in Cloud Manager. Questo archivio può contenere tutti i rami necessari per il processo di sviluppo, ma deve esserci almeno un ramo utilizzato dalla pipeline CI/CD per distribuire il codice dell’applicazione nell’area di staging e produzione. La best practice è quella di utilizzare `main` come nome di questo ramo. Questo approccio è il comportamento predefinito dei client Git durante la configurazione di nuovi progetti.

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
>Non è necessario utilizzare il client della riga di comando. Esistono diversi client Git grafici disponibili come applicazioni standalone o come parte di un ambiente di sviluppo integrato (IDE) come Eclipse o IntelliJ. Se l’applicazione client supporta i Git che utilizzano HTTPS, deve essere compatibile con [!UICONTROL Cloud Manager].

## Invia il primo ramo {#pushing-your-first-branch}

Dopo aver eseguito il commit di almeno una revisione, è possibile aggiungere l&#39;archivio [!UICONTROL Cloud Manager] in modalità remota e quindi eseguire l&#39;invio dei commit.

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
>L&#39;URL specifico, insieme alle tue credenziali, viene fornito dall&#39;Adobe CSE (Customer Success Engineer) durante l&#39;onboarding di [!UICONTROL Cloud Manager].

## Rami aggiuntivi {#additional-branches}

Un singolo ramo `main` può essere sufficiente per progetti molto semplici, ma nella maggior parte dei casi è necessaria una strategia di ramificazione più complessa. Molti clienti seguono un processo in cui le attività di sviluppo quotidiane vengono eseguite su un ramo denominato `develop`. Il ramo di sviluppo viene quindi unito al ramo `main` quando è il momento di una distribuzione.

>[!TIP]
>
>Per visualizzare i comandi Git comuni, vedere [Scheda di riferimento Git](https://training.github.com/downloads/github-git-cheat-sheet).
