---
title: Utilizzo di più archivi Git
description: Invece di utilizzare direttamente l’archivio Git di Cloud Manager, scopri come utilizzare il tuo archivio Git o più archivi Git.
exl-id: 53bf78bb-489a-4a83-8459-c361f532d54a
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: ht
source-wordcount: '738'
ht-degree: 100%

---

# Utilizzo di più archivi Git di origine {#working-with-multiple-source-git-repos}

Invece di utilizzare direttamente l’archivio Git di Cloud Manager, scopri come utilizzare il tuo archivio Git o più archivi Git.

## Sincronizzazione degli archivi Git gestiti dal cliente {#syncing-customer-managed-git-repositories}

Per mantenere aggiornato l’archivio Git di Cloud Manager, imposta un processo di sincronizzazione automatizzato se utilizzi un archivio o più archivi personalizzati.

A seconda della posizione in cui è ospitato l’archivio Git, per configurare l’automazione è possibile utilizzare un’azione GitHub o una soluzione di integrazione continua come Jenkins. Con un’automazione implementata, ogni implementazione nel tuo archivio può essere inoltrata automaticamente all’archivio Git di Cloud Manager.

Sebbene un’automazione di questo tipo per un singolo archivio Git di proprietà del cliente sia semplice, la configurazione per più archivi richiede una configurazione iniziale più complessa. I contenuti di più archivi Git devono essere mappati su directory diverse all’interno di un singolo archivio Git di Cloud Manager. Il provisioning dell’archivio Git di Cloud Manager deve essere eseguito con un file radice Maven `pom.xml`, elencando i diversi sottoprogetti nella sezione moduli

Di seguito è riportato un esempio `pom.xml` per due archivi Git di proprietà del cliente. Il primo progetto verrà collocato nella directory denominata `project-a`, mentre il secondo progetto nella directory denominata `project-b`.

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

Tale radice `pom.xml` viene inviata a un ramo nell’archivio Git di Cloud Manager. Quindi è necessario configurare i due progetti per inoltrare automaticamente le modifiche all’archivio Git di Cloud Manager.

Ad esempio, un invio a un ramo nel progetto A può attivare un’azione GitHub. L’azione verifica il progetto A e l’archivio Git di Cloud Manager. Copia tutti i contenuti del progetto A nella directory `project-a` dell’archivio Git di Cloud Manager. Quindi conferma e implementa la modifica.

Ad esempio, una modifica nel ramo `main` nel progetto A viene inviata automaticamente al ramo `main` nell’archivio Git di Cloud Manager. Naturalmente potrebbe esserci una mappatura tra rami così come un invio in un ramo denominato `dev` nel progetto A viene inviato a un ramo denominato `development` nell’archivio Git di Cloud Manager. Passaggi simili sono necessari per il progetto B.

A seconda della strategia e dei flussi di lavoro e di ramificazione, la sincronizzazione può essere configurata per rami diversi. Se l’archivio Git utilizzato non fornisce un concetto simile alle azioni GitHub, è possibile anche un’integrazione tramite Jenkins (o simile). In questo caso, un webhook attiva un processo Jenkins che esegue l’operazione.

Per aggiungere una nuova (di terze parti) origine o un nuovo archivio:

1. Aggiungi una nuova azione GitHub al nuovo archivio per eseguire gli invii delle modifiche da tale archivio a quello Git di Cloud Manager.
1. Esegui questa azione almeno una volta per verificare che il codice del progetto sia riportato nell’archivio Git di Cloud Manager.
1. Aggiungi un riferimento alla nuova directory nella radice Maven `pom.xml` nell’archivio Git di Cloud Manager.

## Azione GitHub di esempio {#sample-github-action}

Un invio al ramo `main` attiva questa azione GitHub di esempio, che quindi esegue gli invii in una sottodirectory dell’archivio Git di Cloud Manager. È necessario fornire alle azioni GitHub due segreti, `MAIN_USER` e `MAIN_PASSWORD`, per connettersi e inviare notifiche push all’archivio Git di Cloud Manager.

```java
name: SYNC
env:
  # Username/email used to commit to Cloud Manager's Git repository
  USER_NAME: <NAME>
  USER_EMAIL: <EMAIL>
  # Directory within the Cloud Manager Git repository
  PROJECT_DIR: project-a
  # Cloud Manager's Git repository
  MAIN_REPOSITORY: https://$MAIN_USER:$MAIN_PASSWORD@git.cloudmanager.adobe.com/<PATH>
  # The branch in Cloud Manager's Git repository to push to
  MAIN_BRANCH : <BRANCH_NAME>
 
# Only run on a push to this branch
on:
  push:
     branches: [ main ]
 
jobs:
  build:
    runs-on: ubuntu-latest
 
    steps:
      # Checkout this project into a sub folder
      - uses: actions/checkout@v2
        with:
          path: sub
      # Cleanup sub project
      - name: Clean project
        run: |
          git -C sub log --format="%an : %s" -n 1 > commit.txt
          rm -rf sub/.git
          rm -rf sub/.github
      # Set global git configuration
      - name: Set git config
        run: |
          git config --global credential.helper cache
          git config --global user.email ${USER_EMAIL}
          git config --global user.name ${USER_NAME}
      # Checkout the main project
      - name: Checkout main project
        run:
          git clone -b ${MAIN_BRANCH} https://${{ secrets.PAT }}@github.com/${MAIN_REPOSITORY}.git main 
      # Move sub project
      - name: Move project to main project
        run: |
          rm -rf main/${PROJECT_DIR} 
          mv sub main/${PROJECT_DIR}
      - name: Commit Changes
        run: |
          git -C main add -f ${PROJECT_DIR}
          git -C main commit -F ../commit.txt
          git -C main push
```

Come mostrato in precedenza, l’utilizzo di un’azione GitHub è flessibile. È possibile eseguire qualsiasi mappatura tra i rami degli archivi Git e qualsiasi mappatura di progetti Git distinti nel layout di directory del progetto principale.

>[!NOTE]
>
>Lo script di cui sopra utilizza `git add` per aggiornare l’archivio, presupponendo che siano incluse le rimozioni. A seconda della configurazione predefinita di Git, potrebbe essere necessario sostituirlo con `git add --all`.

## Esempio di processo Jenkins {#sample-jenkins-job}

Questo è uno script di esempio che può essere utilizzato in un processo Jenkins o simile. Una modifica in un archivio Git lo attiva. Il processo Jenkins verifica lo stato più recente del progetto o del ramo e quindi attiva questo script.

Questo script a sua volta verifica l’archivio Git di Cloud Manager e conferma il codice del progetto in una sottodirectory.

Il processo Jenkins deve essere fornito con due segreti, `MAIN_USER` e `MAIN_PASSWORD`, per connettersi e inviare notifiche push all’archivio Git di Cloud Manager.

```java
# Username/email used to commit to Cloud Manager's Git repository
export USER_NAME=<NAME>
export USER_EMAIL=<EMAIL>
# Directory within the Cloud Manager Git repository
export PROJECT_DIR=project-a
# Cloud Manager's Git repository
export MAIN_REPOSITORY=https://$MAIN_USER:$MAIN_PASSWORD@git.cloudmanager.adobe.com/<PATH>
# The branch in Cloud Manager's Git repository to push to
export MAIN_BRANCH=<BRANCH_NAME>
 
# clean up and init
rm -rf target
mkdir target
 
# mv project to sub folder
mkdir target/sub
for f in .* *
do
    if [ "$f" != "." -a "$f" != ".." -a "$f" != "target" ]
    then
        mv "$f" target/sub
    fi
done
cd target
 
# capture log and remove git info
cd sub
git log --format="%an : %s" -n 1 > ../commit.txt
rm -rf .git
rm -rf .github
cd ..
 
# checkout main repository
git clone -b $MAIN_BRANCH $MAIN_REPOSITORY main
cd main
 
# configure main repository
git config credential.helper cache
git config user.email $USER_EMAIL
git config user.name $USER_NAME
 
# update project in main
rm -rf $PROJECT_DIR
mv ../sub $PROJECT_DIR
 
# commit changes to main
git add -f $PROJECT_DIR
git commit -F ../commit.txt
git push
```

Come mostrato in precedenza, l’utilizzo di un processo Jenkins è molto flessibile. È possibile eseguire qualsiasi mappatura tra i rami degli archivi Git e qualsiasi mappatura di progetti Git distinti nel layout di directory del progetto principale.

>[!NOTE]
>
>Lo script di cui sopra utilizza `git add` per aggiornare l’archivio, presupponendo che siano incluse le rimozioni. A seconda della configurazione predefinita di Git, potrebbe essere necessario sostituire `git add` con `git add --all`.
