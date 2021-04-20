---
title: Configurare i rami della versione
seo-title: Configurare i rami della versione
description: Configurare le ramificazioni di rilascio in Git per AEM Cloud Manager
seo-description: Segui questa pagina per scoprire come configurare i rami della versione in git.
uuid: d12a8b85-b7fd-4b55-a05a-a0f874ce598c
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: getting-started
discoiquuid: 53807ea6-9464-429d-9322-85c9f405dff6
feature: Git Repositories
translation-type: tm+mt
source-git-commit: c5d32d49782c899d013fcc60b9c4d2b67e9350ae
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 3%

---


# Configurare i rami della versione {#configure-your-release-branches}

## Impostazione della prima filiale in Git {#setting-up-your-first-branch-in-git}

Per ogni programma integrato in Cloud Manager è disponibile un singolo **Archivio Git** inizialmente vuoto. Questo archivio può contenere tutti i rami (o un numero ridotto) del processo di sviluppo successivo, ma deve esserci almeno un ramo utilizzato dalla pipeline CI/CD per distribuire il codice dell’applicazione nell’area di visualizzazione e produzione. La best practice prevede l’utilizzo di `master` come nome di questo ramo. Comodamente, si tratta del comportamento predefinito dei clienti Git durante la configurazione di nuovi progetti.

Ad esempio, quando imposti un nuovo progetto, eseguirai un set di comandi come questo:

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
>Non è necessario utilizzare il client della riga di comando. Sono disponibili diversi client Git grafici come applicazioni autonome o come parte di un ambiente di sviluppo integrato (IDE) come Eclipse o IntelliJ. Se l’applicazione client supporta Git utilizzando HTTPS, deve essere compatibile con [!UICONTROL Cloud Manager].

## Invio del primo ramo {#pushing-your-first-branch}

Una volta impegnata almeno una revisione, puoi aggiungere l’archivio [!UICONTROL Cloud Manager] come **remoto** e quindi inviare i tuoi impegni:

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
>L’URL specifico, insieme alle credenziali, verrà fornito al tuo dal Customer Success Engineering durante l’ [!UICONTROL Cloud Manager] onboarding.

## Rami aggiuntivi {#additional-branches}

Un singolo ramo `master` può essere sufficiente per progetti molto semplici, ma nella maggior parte dei casi sarà necessaria una strategia di diramazione più complessa. Molti clienti seguono un processo in cui le attività di sviluppo quotidiane vengono eseguite su un ramo denominato `develop` e il ramo di sviluppo viene unito al ramo `master` quando è il momento di una distribuzione.

>[!NOTE]
>
>Per visualizzare i comandi git comuni, consulta la [Guida di riferimento per Git](https://github.github.com/training-kit/downloads/github-git-cheat-sheet).
