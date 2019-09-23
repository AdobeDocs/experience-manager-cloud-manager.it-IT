---
title: Configurare i rami di rilascio
seo-title: Configurare i rami di rilascio
description: Configurare le filiali di rilascio in Git per AEM Cloud Manager
seo-description: Segui questa pagina per apprendere come configurare i rami della release in git.
uuid: d12a8b85-b7fd-4b55-a05a-a0f874ce598c
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: guida introduttiva
discoiquuid: 53807ea6-9464-429d-9322-85c9f405dff6
translation-type: tm+mt
source-git-commit: 9c0df236c1e800802d62dea09996bb8e1e7033f7

---


# Configurare i rami di rilascio {#configure-your-release-branches}

## Impostazione del primo ramo in Git {#setting-up-your-first-branch-in-git}

Viene fornito un unico archivio **Git inizialmente vuoto** per ciascun programma fornito su Cloud Manager. Questo repository può contenere un numero illimitato di filiali (o un numero ridotto) come segue nel processo di sviluppo, ma deve essere presente almeno un ramo utilizzato dalla pipeline CI/CD per distribuire il codice dell'applicazione allo stage e alla produzione. La procedura ottimale consiste nell'utilizzare `master` come nome di questo ramo. Comodamente, questo è il comportamento predefinito dei client Git quando si configurano nuovi progetti.

Ad esempio, quando si configura un nuovo progetto, verrà eseguito un set di comandi come quello seguente:

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
>Non è necessario utilizzare il client della riga di comando. Sono disponibili diversi client Git grafici sia come applicazioni autonome che come parte di un ambiente di sviluppo integrato (IDE) come Eclipse o IntelliJ. Fintanto che l'applicazione client supporta Git utilizzando HTTPS, dovrebbe essere compatibile con [!UICONTROL Cloud Manager].

## Invio della prima diramazione {#pushing-your-first-branch}

Una volta completata almeno una revisione, potete aggiungere l' [!UICONTROL Cloud Manager] archivio come **remoto** e quindi inviarvi i commit:

```shell
$ git remote add adobe <url>
$ git push adobe master
Counting objects: 36, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (27/27), done.
Writing objects: 100% (36/36), 7.31 KiB | 1.83 MiB/s, done.
Total 36 (delta 6), reused 0 (delta 0)
To <url>
 * [new branch]      master -> master
```

>[!NOTE]
>
>L'URL specifico, insieme alle credenziali, verrà fornito al cliente dal Customer Success Engineering durante la [!UICONTROL Cloud Manager] registrazione.

## Altri rami {#additional-branches}

Un solo `master` ramo può essere sufficiente per progetti molto semplici, ma nella maggior parte dei casi sarà necessaria una strategia di ramificazione più complessa. Molti clienti seguono un processo in cui le attività di sviluppo quotidiane vengono eseguite su un ramo denominato `develop` e il ramo di sviluppo viene unito nel `master` ramo quando è il momento di una distribuzione.

>[!NOTE]
>
>Per visualizzare i comandi git comuni, vedere il [Git Cheat Sheet](https://github.github.com/training-kit/downloads/github-git-cheat-sheet).
