---
title: Configurare i rami della release
seo-title: Configurare i rami della release
description: Configura i rami di rilascio in Git per AEM Cloud Manager
seo-description: Seguite questa pagina per apprendere come configurare i rami di rilascio in git.
uuid: d 12 a 8 b 85-b 7 fd -4 b 55-a 05 a-a 0 f 874 ce 598 c
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: getting-started
discoiquuid: 53807 ea 6-9464-429 d -9322-85 c 9 f 405 dff 6
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Configurare i rami della release {#configure-your-release-branches}

## Impostazione del primo ramo in Git {#setting-up-your-first-branch-in-git}

Un singolo, inizialmente vuoto, **l&#39;archivio** Git viene fornito per ogni programma presente in Cloud Manager. Questo archivio può contenere un numero di rami (o pochissimi) all&#39;interno del processo di sviluppo, ma deve essere presente almeno un ramo utilizzato dalla pipeline CI/CD per distribuire il codice dell&#39;applicazione all&#39;area di visualizzazione e alla produzione. La procedura consigliata è quella di utilizzare `master` come nome di questo ramo. Questo è il comportamento predefinito dei client Git durante l&#39;impostazione di nuovi progetti.

Ad esempio, quando configurate un nuovo progetto, viene eseguito un set di comandi come:

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
>Non è necessario utilizzare il client della riga di comando. Esistono diversi client Git grafici disponibili come applicazioni autonome o come parte di un ambiente di sviluppo integrato (IDE) come Eclipse o intellij. Se l&#39;applicazione client supporta Git utilizzando HTTPS, deve essere compatibile [!UICONTROL Cloud Manager]con.

## Invio del primo ramo {#pushing-your-first-branch}

Dopo aver effettuato almeno una revisione, puoi aggiungere la [!UICONTROL Cloud Manager] directory archivio come **remoto** e quindi inviare i tuoi commenti:

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
>L&#39;URL specifico, insieme alle tue credenziali, verrà fornito al tuo Customer Success Engineering durante [!UICONTROL Cloud Manager] l&#39;onboarding.

## Rami aggiuntivi {#additional-branches}

Un `master` singolo ramo può essere sufficiente per progetti molto semplici, ma nella maggior parte dei casi sarà necessaria una strategia di branching più complessa. Molti clienti seguono un processo in cui le attività quotidiane di sviluppo vengono eseguite su un ramo chiamato `develop` e il ramo di sviluppo viene unito al `master` ramo quando è temporale per una distribuzione.

>[!NOTE]
>
>Per visualizzare i comandi git comuni, consultate [Git Cheat Sheet](https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf).

