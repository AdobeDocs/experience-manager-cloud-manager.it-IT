---
title: Impostazione del progetto
description: Scopri come configurare il progetto in modo da gestirlo e distribuirlo con Cloud Manager.
exl-id: ed994daf-0195-485a-a8b1-87796bc013fa
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '1432'
ht-degree: 2%

---


# Configurazione del progetto {#setting-up-your-project}

Scopri come configurare il progetto in modo da gestirlo e distribuirlo con Cloud Manager.

## Modifica di progetti esistenti {#modifying-project-setup-details}

Per poter essere generati e distribuiti correttamente con Cloud Manager, i progetti AEM esistenti devono rispettare alcune regole di base.

* I progetti devono essere generati utilizzando Apache Maven.
* Ci deve essere un `pom.xml` nella directory principale dell’archivio git.
   * Questo `pom.xml` file può fare riferimento a tutti i sottomoduli (che a loro volta possono avere altri sottomoduli), a seconda delle necessità.
   * Puoi aggiungere riferimenti ad altri archivi di artefatti Maven nel tuo `pom.xml` file.
   * Accesso a [archivi di artefatti protetti da password](#password-protected-maven-repositories) è supportato quando è configurato. Tuttavia, l&#39;accesso agli archivi di artefatti protetti dalla rete non è supportato.
* I pacchetti di contenuto distribuibile vengono rilevati eseguendo la scansione dei file .zip dei pacchetti di contenuto contenuti contenuti in una directory denominata `target`.
   * Un numero qualsiasi di sottomoduli può produrre pacchetti di contenuti.
* Gli artefatti del Dispatcher distribuibili vengono rilevati tramite la ricerca di `zip` file contenenti sottodirectory di `target` denominato `conf` e `conf.d`.
* Se sono presenti più pacchetti di contenuto, l’ordine delle distribuzioni dei pacchetti non è garantito.
* Se è necessario un ordine specifico, le dipendenze del pacchetto di contenuti possono essere utilizzate per definire l’ordine.
* I pacchetti possono essere [saltato](#skipping-content-packages) dalla distribuzione.

## Attivazione dei profili Maven in Cloud Manager {#activating-maven-profiles-in-cloud-manager}

In alcuni casi limitati, potrebbe essere necessario variare leggermente il processo di generazione quando si esegue in Cloud Manager rispetto a quando si esegue su workstation per sviluppatori. Per questi casi, [Profili Maven](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) può essere utilizzato per definire in che modo la build deve essere diversa in ambienti diversi, incluso Cloud Manager.

L’attivazione di un profilo Maven nell’ambiente di build di Cloud Manager deve essere eseguita cercando `CM_BUILD` [variabile di ambiente](/help/getting-started/build-environment.md#environment-variables) variabile di ambiente. Al contrario, un profilo destinato a essere utilizzato solo al di fuori dell’ambiente di build di Cloud Manager deve essere fatto cercando l’assenza di questa variabile.

Ad esempio, se desideri inviare un messaggio semplice solo quando la build viene eseguita in Cloud Manager, effettua le seguenti operazioni:

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                  <property>
                        <name>env.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running inside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

>[!NOTE]
>
>Per testare questo profilo su una workstation sviluppatore, puoi abilitarlo sulla riga di comando (con `-PcmBuild`) o nell&#39;ambiente di sviluppo integrato (IDE).

E se desideri inviare un messaggio semplice solo quando la build viene eseguita al di fuori di Cloud Manager, effettua le seguenti operazioni:

```xml
        <profile>
            <id>notCMBuild</id>
            <activation>
                  <property>
                        <name>!env.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running outside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

## Supporto dell&#39;archivio Maven protetto da password {#password-protected-maven-repositories}

Gli artefatti provenienti da un archivio Maven protetto da password devono essere utilizzati con molta cautela, in quanto il codice distribuito tramite questo meccanismo non viene eseguito attraverso tutte le regole di qualità implementate nei gate di qualità di Cloud Manager. Si consiglia inoltre di distribuire le origini Java e l&#39;intero codice sorgente del progetto insieme al binario.

>[!TIP]
>
>Gli artefatti degli archivi Maven protetti da password devono essere utilizzati solo in rari casi e per il codice non legato a AEM.

Per utilizzare un archivio Maven protetto da password da Cloud Manager, specifica la password (e facoltativamente il nome utente) come segreto [Variabile pipeline](/help/getting-started/build-environment.md#pipeline-variables) e poi fai riferimento a quel segreto all&#39;interno di un file denominato `.cloudmanager/maven/settings.xml` nell’archivio git. Questo file segue [File impostazioni Maven](https://maven.apache.org/settings.html) schema.

All’avvio del processo di creazione di Cloud Manager, la `<servers>` l&#39;elemento in questo file verrà unito all&#39;elemento predefinito `settings.xml` file fornito da Cloud Manager. ID server che iniziano con `adobe` e `cloud-manager` sono considerati riservati e non devono essere utilizzati da server personalizzati. Gli ID del server che non corrispondono a uno di questi prefissi o all&#39;ID predefinito `central` Cloud Manager non verrà mai eseguito il mirroring.

Con questo file attivo, viene fatto riferimento all&#39;ID server all&#39;interno di un `<repository>` e/o `<pluginRepository>` all’interno dell’elemento `pom.xml` file. In generale, questi `<repository>` e/o `<pluginRepository>` elementi sarebbero contenuti all&#39;interno di un [Profilo specifico di Cloud Manager](#activating-maven-profiles-in-cloud-manager), anche se ciò non è strettamente necessario.

Ad esempio, supponiamo che l’archivio si trovi in `https://repository.myco.com/maven2`, il nome utente Cloud Manager deve utilizzare is `cloudmanager` e la password è `secretword`.

Innanzitutto, imposta la password come segreto sulla pipeline:

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword
```

Quindi fai riferimento a questo dal `.cloudmanager/maven/settings.xml` file:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
    <servers>
        <server>
            <id>myco-repository</id>
            <username>cloudmanager</username>
            <password>${env.CUSTOM_MYCO_REPOSITORY_PASSWORD}</password>
        </server>
    </servers>
</settings>
```

Infine, fai riferimento all&#39;ID server all&#39;interno del `pom.xml` file:

```xml
<profiles>
    <profile>
        <id>cmBuild</id>
        <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
        </activation>
        <build>
            <repositories>
                <repository>
                    <id>myco-repository</id>
                    <name>MyCo Releases</name>
                    <url>https://repository.myco.com/maven2</url>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                </repository>
            </repositories>
            <pluginRepositories>
                <pluginRepository>
                    <id>myco-repository</id>
                    <name>MyCo Releases</name>
                    <url>https://repository.myco.com/maven2</url>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                </pluginRepository>
            </pluginRepositories>
        </build>
    </profile>
</profiles>
```

### Distribuzione di origini {#deploying-sources}

È buona prassi distribuire le origini Java insieme al binario in un archivio Maven.

Configura le `maven-source-plugin` nel progetto:

```xml
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-source-plugin</artifactId>
            <executions>
                <execution>
                    <id>attach-sources</id>
                    <goals>
                        <goal>jar-no-fork</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
```

### Distribuzione di origini di progetto {#deploying-project-sources}

È buona prassi distribuire l’intera origine del progetto insieme al binario in un archivio Maven. Questo permette di ricostruire l&#39;artefatto esatto.

Configura le `maven-assembly-plugin` nel progetto:

```xml
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-assembly-plugin</artifactId>
            <executions>
                <execution>
                    <id>project-assembly</id>
                    <phase>package</phase>
                    <goals>
                        <goal>single</goal>
                    </goals>
                    <configuration>
                        <descriptorRefs>
                            <descriptorRef>project</descriptorRef>
                        </descriptorRefs>
                    </configuration>
                </execution>
            </executions>
        </plugin>
```

## Ignora pacchetti di contenuto {#skipping-content-packages}

In Cloud Manager, le build possono produrre un numero qualsiasi di pacchetti di contenuto. Per vari motivi, può essere opportuno creare un pacchetto di contenuti ma non distribuirlo. Ciò può essere utile, ad esempio, quando si creano pacchetti di contenuto utilizzati solo per il test o che verranno reimballati da un altro passaggio del processo di compilazione, ovvero come pacchetto secondario di un altro pacchetto.

Per soddisfare questi scenari, Cloud Manager cercherà una proprietà denominata `cloudManagerTarget` tra le proprietà dei pacchetti di contenuto incorporati. Se questa proprietà è impostata su `none`, il pacchetto verrà ignorato e non distribuito. Il meccanismo per impostare questa proprietà dipende dal modo in cui la build produce il pacchetto di contenuto. Ad esempio, con `filevault-maven-plugin` configura il plug-in in questo modo:

```xml
        <plugin>
            <groupId>org.apache.jackrabbit</groupId>
            <artifactId>filevault-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```

Con la `content-package-maven-plugin` è simile:

```xml
        <plugin>
            <groupId>com.day.jcr.vault</groupId>
            <artifactId>content-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```

## Crea riuso artifact {#build-artifact-reuse}

In molti casi, lo stesso codice viene distribuito a più ambienti AEM. Laddove possibile, Cloud Manager evita di ricostruire la base di codice quando rileva che lo stesso commit git viene utilizzato in più esecuzioni di pipeline complete.

All’avvio di un’esecuzione, viene estratto il commit corrente di HEAD per la pipeline di ramo. L’hash di commit è visibile nell’interfaccia utente e tramite l’API . Al completamento del passaggio della build, gli artefatti risultanti vengono memorizzati in base a tale hash di commit e possono essere riutilizzati nelle esecuzioni successive della pipeline.

I pacchetti vengono riutilizzati tra le pipeline se si trovano nello stesso programma. Quando cerchi pacchetti che possono essere riutilizzati, AEM ignora le ramificazioni e riutilizza gli artefatti tra rami.

Quando si verifica un riutilizzo, i passaggi di creazione e qualità del codice vengono effettivamente sostituiti con i risultati dell’esecuzione originale. Il file di registro per la fase di compilazione elenca gli artefatti e le informazioni di esecuzione utilizzate per generarli originariamente.

Di seguito è riportato un esempio di tale output di log.

```shell
The following build artifacts were reused from the prior execution 4 of pipeline 1 which used commit f6ac5e6943ba8bce8804086241ba28bd94909aef:
build/aem-guides-wknd.all-2021.1216.1101633.0000884042.zip (content-package)
build/aem-guides-wknd.dispatcher.cloud-2021.1216.1101633.0000884042.zip (dispatcher-configuration)
```

Il registro del passaggio di qualità del codice conterrà informazioni simili.

### Esempi {#example-reuse}

#### Esempio 1 {#example-1}

Considera che il tuo programma dispone di due pipeline di sviluppo:

* Pipeline 1 su ramo `foo`
* Pipeline 2 su ramo `bar`

Entrambi i rami si trovano sullo stesso ID commit.

1. Prima di tutto, l’esecuzione della pipeline 1 genererà i pacchetti normalmente.
1. L’esecuzione della pipeline 2 riutilizzerà i pacchetti creati dalla pipeline 1.

#### Esempio 2 {#example-2}

Considera che il programma ha due rami:

* Ramo `foo`
* Ramo `bar`

Entrambi i rami hanno lo stesso ID commit.

1. Viene generata ed eseguita una pipeline di sviluppo `foo`.
1. Successivamente viene creata ed eseguita una pipeline di produzione `bar`.

In questo caso, l&#39;artefatto di `foo` verrà riutilizzato per la pipeline di produzione poiché è stato identificato lo stesso hash di commit.

### Rinuncia {#opting-out}

Se lo desideri, puoi disattivare il comportamento di riutilizzo per specifiche pipeline impostando la variabile di pipeline `CM_DISABLE_BUILD_REUSE` a `true`. Se questa variabile è impostata, l’hash di commit viene ancora estratto e gli artefatti risultanti verranno memorizzati per un uso successivo, ma gli eventuali artefatti memorizzati in precedenza non verranno riutilizzati. Per comprendere questo comportamento, considera lo scenario seguente.

1. Viene creata una nuova pipeline.
1. La pipeline viene eseguita (esecuzione n. 1) e il commit corrente di HEAD è `becdddb`. L&#39;esecuzione ha esito positivo e gli artefatti risultanti vengono memorizzati.
1. La `CM_DISABLE_BUILD_REUSE` è impostata.
1. La pipeline viene rieseguita senza modificare il codice. Anche se sono presenti artefatti memorizzati associati a `becdddb`, non vengono riutilizzati a causa del `CM_DISABLE_BUILD_REUSE` variabile.
1. Il codice viene modificato e la pipeline viene eseguita. Il commit di HEAD è ora `f6ac5e6`. L&#39;esecuzione ha esito positivo e gli artefatti risultanti vengono memorizzati.
1. La `CM_DISABLE_BUILD_REUSE` viene eliminata.
1. La pipeline viene rieseguita senza modificare il codice. Poiché sono presenti artefatti memorizzati associati a `f6ac5e6`, questi artefatti vengono riutilizzati.

### Avvertenze {#caveats}

* Gli artefatti di creazione non vengono riutilizzati in diversi programmi, indipendentemente dal fatto che l’hash di commit sia identico.
* Gli artefatti di creazione vengono riutilizzati all’interno dello stesso programma anche se il ramo e/o la pipeline sono diversi.
* [Gestione delle versioni Maven](/help/managing-code/maven-project-version.md) sostituisci la versione del progetto solo nelle pipeline di produzione. Pertanto, se lo stesso commit viene utilizzato sia su un’esecuzione di distribuzione di sviluppo che su un’esecuzione di pipeline di produzione e la pipeline di distribuzione di sviluppo viene eseguita per prima, le versioni verranno distribuite sullo stage e la produzione senza essere modificate. Tuttavia, in questo caso verrà comunque creato un tag .
* Se il recupero degli artefatti memorizzati non ha esito positivo, il passaggio di compilazione verrà eseguito come se non fosse stato memorizzato alcun artefatto.
* Variabili di pipeline diverse da `CM_DISABLE_BUILD_REUSE` non vengono considerati quando Cloud Manager decide di riutilizzare gli artefatti di build creati in precedenza.

## Sviluppa il codice in base alle best practice {#develop-your-code-based-on-best-practices}

I team di ingegneria e consulenza Adobe hanno sviluppato un [set completo di best practice per sviluppatori AEM.](https://experienceleague.adobe.com/docs/experience-manager-65/developing/bestpractices/best-practices.html)
