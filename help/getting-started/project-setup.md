---
title: Configura il progetto
description: Scopri come configurare il progetto in modo da gestirlo e distribuirlo con Cloud Manager.
exl-id: ed994daf-0195-485a-a8b1-87796bc013fa
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '1395'
ht-degree: 53%

---


# Configurare il progetto {#setting-up-your-project}

Scopri come configurare il progetto in modo da gestirlo e distribuirlo con Cloud Manager.

## Modifica progetti esistenti {#modifying-project-setup-details}

I progetti AEM esistenti devono rispettare alcune regole di base in modo che possano essere generati e distribuiti correttamente con Cloud Manager.

* I progetti devono essere generati utilizzando Apache Maven.
* Nella radice dell&#39;archivio Git deve essere presente un file `pom.xml`.
   * Il file `pom.xml` può fare riferimento a tutti i sottomoduli (che a loro volta possono avere altri sottomoduli), a seconda delle necessità.
   * Puoi aggiungere riferimenti ad altri archivi di artefatti Maven nei tuoi file `pom.xml`.
   * Quando configurato, l’accesso agli [archivi di artefatti protetti da password](#password-protected-maven-repositories) è supportato. Tuttavia, l’accesso agli archivi di artefatti protetti dalla rete non è supportato.
* I pacchetti di contenuto distribuibili vengono rilevati eseguendo la scansione dei file .zip dei pacchetti di contenuto presenti in una directory denominata `target`.
   * Un numero qualsiasi di sottomoduli può produrre pacchetti di contenuti.
* Gli artefatti del Dispatcher distribuibili vengono rilevati tramite la ricerca di file `zip` contenenti sottodirectory di `target` denominate `conf` e `conf.d`.
* Se sono presenti più pacchetti di contenuto, l’ordine delle distribuzioni dei pacchetti non è garantito.
* Se è necessario un ordine specifico, le dipendenze del pacchetto di contenuto possono essere utilizzate per definirlo.
* I pacchetti possono essere [ignorati](#skipping-content-packages) dalla distribuzione.

## Attivare i profili Maven in Cloud Manager {#activating-maven-profiles-in-cloud-manager}

In alcuni casi limitati, potrebbe essere necessario variare leggermente il processo di generazione quando si esegue in Cloud Manager rispetto a quando si esegue su workstation per sviluppatori. Per questi casi, i [Profili Maven](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) possono essere utilizzati per definire in che modo la build deve essere diversa in ambienti diversi, incluso Cloud Manager.

L&#39;attivazione di un profilo Maven nell&#39;ambiente di build Cloud Manager deve essere eseguita cercando `CM_BUILD` [variabile di ambiente](/help/getting-started/build-environment.md#environment-variables). Al contrario, un profilo destinato a essere utilizzato solo al di fuori dell’ambiente di build di Cloud Manager deve essere fatto cercando l’assenza di questa variabile.

Ad esempio, per inviare un semplice messaggio solo quando la build viene eseguita in Cloud Manager, effettua le seguenti operazioni:

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
>Per testare questo profilo su una workstation per sviluppatori, puoi abilitarlo sulla riga di comando (con `-PcmBuild`) o nell’ambiente di sviluppo integrato (IDE).

Per inviare un semplice messaggio solo quando la build viene eseguita al di fuori di Cloud Manager, effettua le seguenti operazioni:

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

## Supporto dell’archivio Maven protetto da password {#password-protected-maven-repositories}

Gli artefatti di un archivio Maven protetto da password devono essere utilizzati con cautela perché il codice distribuito in questo modo non è completamente soggetto ai controlli di qualità imposti dai gate di qualità di Cloud Manager. Adobe consiglia inoltre di distribuire le origini Java e l’intero codice sorgente del progetto insieme al binario.

>[!TIP]
>
>Gli artefatti degli archivi Maven protetti da password devono essere utilizzati solo in rari casi e per il codice non legato ad AEM.

Per utilizzare un archivio Maven protetto da password da Cloud Manager, specifica la password (e facoltativamente il nome utente) come [Variabile pipeline](/help/getting-started/build-environment.md#pipeline-variables) segreta e quindi fai riferimento a tale segreto all&#39;interno di un file denominato `.cloudmanager/maven/settings.xml` nell&#39;archivio Git. Questo file segue lo schema del [File impostazioni di Maven](https://maven.apache.org/settings.html).

All&#39;avvio del processo di compilazione di Cloud Manager, l&#39;elemento `<servers>` in questo file viene unito al file predefinito `settings.xml` fornito da Cloud Manager. I server personalizzati non devono utilizzare ID server che iniziano con `adobe` e `cloud-manager`. Tali ID sono considerati riservati. Cloud Manager esegue il mirroring solo degli ID server corrispondenti a uno dei prefissi specificati o all&#39;ID predefinito `central`.

Con questo file attivo, viene fatto riferimento all’ID server all’interno di un elemento `<repository>` e/o `<pluginRepository>` all’interno del file `pom.xml`. In generale, questi elementi `<repository>` e/o `<pluginRepository>` sarebbero contenuti all’interno di un [Profilo specifico di Cloud Manager](#activating-maven-profiles-in-cloud-manager), anche se ciò non è strettamente necessario.

Si supponga, ad esempio, che l&#39;archivio si trovi in `https://repository.myco.com/maven2`, che il nome utente Cloud Manager debba utilizzare sia `cloudmanager` e che la password sia `secretword`.

Innanzitutto, imposta la password come segreta sulla pipeline:

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword
```

Quindi fare riferimento a quanto segue dal file `.cloudmanager/maven/settings.xml`:

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

Infine, fai riferimento all’ID server all’interno del file `pom.xml`:

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

### Distribuisci origini {#deploying-sources}

È buona prassi distribuire le origini Java insieme al binario in un archivio Maven.

Configura il `maven-source-plugin` nel progetto:

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

### Distribuisci origini progetto {#deploying-project-sources}

È buona prassi distribuire l’intera origine del progetto insieme ai dati binari in un archivio Maven. In questo modo è possibile ricostruire l’artefatto esatto.

Configura il `maven-assembly-plugin` nel progetto:

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

## Ignora pacchetti di contenuti {#skipping-content-packages}

In Cloud Manager le build possono produrre qualsiasi numero di pacchetti di contenuti. Per diversi motivi può essere utile produrre un pacchetto di contenuti ma non distribuirlo. Ad esempio, questo approccio può essere utile quando si creano pacchetti di contenuti solo a scopo di test o quando un altro passaggio nel processo di build li ricompila. Cioè, come pacchetto secondario di un altro pacchetto.

Per soddisfare questi scenari, Cloud Manager cerca una proprietà denominata `cloudManagerTarget` tra le proprietà dei pacchetti di contenuto della build. Se questa proprietà è impostata su `none`, il pacchetto viene ignorato e non distribuito. Il meccanismo per impostare questa proprietà dipende dal modo in cui la build produce il pacchetto di contenuti. Ad esempio, con `filevault-maven-plugin` si configura il plug-in come segue:

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

Con `content-package-maven-plugin`, è simile:

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

## Riutilizzo degli artefatti di build {#build-artifact-reuse}

In molti casi, lo stesso codice viene distribuito in più ambienti AEM. Laddove possibile, Cloud Manager evita di ricostruire la base di codice quando rileva che viene utilizzato lo stesso commit Git in più esecuzioni di pipeline full-stack.

All’avvio di un’esecuzione, viene estratto il commit HEAD corrente per la pipeline del ramo. L’hash del commit è visibile nell’interfaccia utente e tramite l’API. Al termine della fase di build, gli artefatti risultanti vengono archiviati in base a tale hash di commit e possono essere riutilizzati nelle esecuzioni successive della pipeline.

Se si trovano nello stesso programma, i pacchetti vengono riutilizzati tra le pipeline. Durante la ricerca di pacchetti da poter riutilizzare, AEM ignora i rami e riutilizza gli artefatti tra rami.

In caso di un riutilizzo, i passaggi di build e qualità del codice vengono effettivamente sostituiti con i risultati dell’esecuzione originale. Il file di registro della fase di build elenca gli artefatti e le informazioni di esecuzione utilizzate per generarli originariamente.

Di seguito è riportato un esempio di tale output di registro.

```shell
The following build artifacts were reused from the prior execution 4 of pipeline 1 which used commit f6ac5e6943ba8bce8804086241ba28bd94909aef:
build/aem-guides-wknd.all-2021.1216.1101633.0000884042.zip (content-package)
build/aem-guides-wknd.dispatcher.cloud-2021.1216.1101633.0000884042.zip (dispatcher-configuration)
```

Il registro del passaggio di qualità del codice contiene informazioni simili.

### Esempi {#example-reuse}

#### Esempio 1 {#example-1}

Ipotizza di utilizzare un programma con due pipeline di sviluppo:

* Pipeline 1 su ramo `foo`
* Pipeline 2 su ramo `bar`

Entrambi i rami presentano lo stesso ID commit.

1. L’esecuzione della pipeline 1 genera innanzitutto i pacchetti normalmente.
1. L’esecuzione della pipeline 2 riutilizza i pacchetti creati dalla pipeline 1.

#### Esempio 2 {#example-2}

Considera che il programma ha due rami: Ramo `foo` e Ramo `bar`.

Entrambi i rami presentano lo stesso ID commit.

1. Una pipeline di sviluppo genera ed esegue `foo`.
1. Successivamente, una pipeline di produzione genera ed esegue `bar`.

In questo caso, l&#39;artefatto di `foo` viene riutilizzato per la pipeline di produzione perché è stato identificato lo stesso hash di commit.

### Rinuncia {#opting-out}

Se lo desideri, puoi disattivare il comportamento di riutilizzo per specifiche pipeline impostando la variabile di pipeline `CM_DISABLE_BUILD_REUSE` su `true`. Se questa variabile è impostata, l’hash del commit viene comunque estratto. Gli artefatti risultanti vengono archiviati per un utilizzo successivo, ma gli eventuali artefatti archiviati in precedenza non vengono riutilizzati. Per comprendere questo comportamento, considera lo scenario seguente:

1. Viene creata una nuova pipeline.
1. La pipeline viene eseguita (esecuzione n. 1) e il commit HEAD corrente è `becdddb`. L’esecuzione ha esito positivo e gli artefatti risultanti vengono archiviati.
1. Viene impostata la variabile `CM_DISABLE_BUILD_REUSE`.
1. La pipeline viene rieseguita senza modificare il codice. Anche se sono presenti artefatti archiviati associati a `becdddb`, non vengono riutilizzati per via della variabile `CM_DISABLE_BUILD_REUSE`.
1. Il codice viene modificato e la pipeline eseguita. Il commit HEAD ora è `f6ac5e6`. L’esecuzione ha esito positivo e gli artefatti risultanti vengono archiviati.
1. La variabile `CM_DISABLE_BUILD_REUSE` viene eliminata.
1. La pipeline viene rieseguita senza modificare il codice. Poiché sono presenti artefatti archiviati associati a `f6ac5e6`, questi artefatti verranno riutilizzati.

### Avvertenze {#caveats}

* Gli artefatti di generazione non vengono riutilizzati in diversi programmi, indipendentemente dal fatto che l’hash di commit sia identico.
* Gli artefatti di build vengono riutilizzati all’interno dello stesso programma anche se il ramo e/o la pipeline sono diversi.
* La [Gestione della versione Maven](/help/managing-code/maven-project-version.md) sostituisce la versione del progetto solo nelle pipeline di produzione. Se si utilizza lo stesso commit per entrambe le pipeline di sviluppo e di produzione e la pipeline di sviluppo viene eseguita per prima, le versioni vengono distribuite nell’area di staging e di produzione senza modifiche. Tuttavia, in questo caso viene comunque creato un tag.
* Se il recupero degli artefatti archiviati non ha esito positivo, la fase di build viene eseguita come se non fossero stati archiviati artefatti.
* Le variabili di pipeline diverse da `CM_DISABLE_BUILD_REUSE` non vengono considerate quando Cloud Manager opta per riutilizzare gli artefatti di generazione creati in precedenza.

## Sviluppa il tuo codice in base alle best practice {#develop-your-code-based-on-best-practices}

I team tecnici e di consulenza Adobi hanno sviluppato un [set completo di best practice per gli sviluppatori AEM](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/developing/bestpractices/best-practices).
