---
title: Configurazione dei rami
description: Scopri come impostare il primo ramo in git e come viene utilizzato dalla pipeline CI/CD per distribuire il codice dell’applicazione.
exl-id: ff2ae28f-902e-4fb2-aeb1-3636cb5cd9bb
source-git-commit: 4c051cd1696f8a00d0278131c9521ad4dcb956a3
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---


# Configurazione dei rami {#configuring-branches}

Scopri come impostare il primo ramo in git e come viene utilizzato dalla pipeline CI/CD per distribuire il codice dell’applicazione.

## Impostazione della prima diramazione in Git {#setting-up-your-first-branch-in-git}

Archivio Git singolo, inizialmente vuoto [è predisposto](/help/requirements/environment-provisioning.md) per ogni programma integrato in Cloud Manager. Questo archivio può contenere tutti i rami necessari per il processo di sviluppo, ma deve esserci almeno un ramo utilizzato dalla pipeline CI/CD per distribuire il codice dell’applicazione nell’area di visualizzazione e nella produzione. La best practice è quella di utilizzare `main` come nome di questo ramo. Comodamente, si tratta del comportamento predefinito dei client Git durante la configurazione di nuovi progetti.

Ad esempio, quando imposti un nuovo progetto, eseguirai un insieme di comandi simili a quelli riportati di seguito.

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
>Non è necessario utilizzare il client della riga di comando. Sono disponibili diversi client Git grafici come applicazioni standalone o come parte di un ambiente di sviluppo integrato (IDE) come Eclipse o IntelliJ. Se l’applicazione client supporta git utilizzando HTTPS, deve essere compatibile con [!UICONTROL Cloud Manager].

## Invio della prima diramazione {#pushing-your-first-branch}

Dopo aver eseguito il commit di almeno una revisione, puoi aggiungere la [!UICONTROL Cloud Manager] come archivio remoto e quindi invia le tue conferme ad esso.

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
>L’URL specifico, insieme alle tue credenziali, verrà fornito al tuo da Customer Success Engineering durante [!UICONTROL Cloud Manager] imbarco.

## Rami aggiuntivi {#additional-branches}

Un singolo `main` può essere sufficiente per progetti molto semplici, ma nella maggior parte dei casi sarà necessaria una strategia di diramazione più complessa. Molti clienti seguono un processo in cui le attività di sviluppo quotidiane vengono eseguite su un ramo denominato `develop` e il ramo di sviluppo viene unito nel `main` quando è il momento di una distribuzione.

>[!TIP]
>
>Per visualizzare i comandi git comuni, consulta la sezione [Foglio di riferimento Git](https://github.github.com/training-kit/downloads/github-git-cheat-sheet).
