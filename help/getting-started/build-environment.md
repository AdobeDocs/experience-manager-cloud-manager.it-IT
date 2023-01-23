---
title: Ambiente di build
description: Scopri l’ambiente di build specializzato che Cloud Manager usa per creare e testare il codice.
exl-id: b3543320-66d4-4358-8aba-e9bdde00d976
source-git-commit: 42cafc03a607ace183d58adbe1c397c1a6c5c22f
workflow-type: tm+mt
source-wordcount: '1152'
ht-degree: 98%

---


# Ambiente di build {#build-environment}

Scopri l’ambiente di build specializzato che Cloud Manager usa per creare e testare il codice.

## Dettagli dell’ambiente {#details}

Gli ambienti di build di Cloud Manager hanno i seguenti attributi.

* L’ambiente di build è basato su Linux, derivato da Ubuntu 18.04.
* Apache Maven 3.6.0 è installato.
* Le versioni Java installate sono Oracle JDK 8u202 e Oracle JDK 11.0.2.
* Per impostazione predefinita, la variabile di ambiente `JAVA_HOME` è impostata su `/usr/lib/jvm/jdk1.8.0_202`, che contiene Oracle JDK 8u202. Per ulteriori dettagli, vedi la sezione [Versione JDK di esecuzione Maven alternativa](#alternate-maven).
* Sono installati anche alcuni altri pacchetti di sistema necessari.
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* Altri pacchetti possono essere installati in fase di build come descritto nella sezione [Installazione di pacchetti di sistema aggiuntivi.](#installing-additional-system-packages)
* Ogni build viene realizzata in un ambiente incontaminato. Il contenitore di build non mantiene alcuno stato da un’esecuzione all’altra.
* Maven viene sempre eseguito con questi tre comandi:
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* Maven è configurato a livello di sistema con un file `settings.xml` che include automaticamente l’archivio degli artefatti Adobe pubblico utilizzando un profilo denominato `adobe-public`.
   * Per ulteriori dettagli, consulta l’[archivio Maven pubblico di Adobe](https://repo1.maven.org/).

>[!NOTE]
>
>Anche se Cloud Manager non definisce una versione specifica di `jacoco-maven-plugin`, la versione utilizzata deve essere almeno `0.7.5.201505241946`.

>[!TIP]
>
>Per informazioni sull’utilizzo delle API di Cloud Manager, consulta le seguenti risorse aggiuntive:
>* [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager)
>* [Creazione di un’integrazione API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/)
>* [Autorizzazioni API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/)


## Utilizzo di una versione Java specifica {#using-java-version}

Per impostazione predefinita, i progetti sono generati dal processo di build di Cloud Manager utilizzando il JDK di Oracle 8. I clienti che desiderano utilizzare un JDK alternativo hanno due opzioni.

* [Toolchain Maven](#maven-toolchains)
* [Selezione di una versione JDK alternativa per l’intero processo di esecuzione Maven](#alternate-maven)

### Toolchain Maven {#maven-toolchains}

Il [plug-in Toolchains di Maven](https://maven.apache.org/plugins/maven-toolchains-plugin/) consente ai progetti di selezionare un JDK specifico (o toolchain) da utilizzare nel contesto di plug-in Maven che tengono conto delle toolchain. Ciò viene effettuato nel file `pom.xml` del progetto specificando un valore di fornitore e di versione. Esempio di sezione nel file `pom.xml`:

```xml
        <plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-toolchains-plugin</artifactId>
    <version>1.1</version>
    <executions>
        <execution>
            <goals>
                <goal>toolchain</goal>
            </goals>
        </execution>
    </executions>
    <configuration>
        <toolchains>
            <jdk>
                <version>11</version>
                <vendor>oracle</vendor>
            </jdk>
        </toolchains>
    </configuration>
</plugin>
```

In questo esempio, tutti i plug-in Maven che tengono conto delle toolchain utilizzeranno Oracle JDK versione 11.

Quando si utilizza questo metodo, Maven stesso viene comunque eseguito utilizzando il JDK predefinito (Oracle 8) e la variabile di ambiente `JAVA_HOME` non viene modificata. Pertanto, non è possibile controllare o applicare la versione Java tramite plug-in come [Apache Maven Enforcer](https://maven.apache.org/enforcer/maven-enforcer-plugin/) e tali plug-in non devono essere utilizzati.

Le combinazioni fornitore/versione attualmente disponibili sono:

| Fornitore | Versione |
|---|---|
| oracle | 1.8 |
| oracle | 1.11 |
| oracle | 11 |
| sun | 1.8 |
| sun | 1.11 |
| sun | 11 |

>[!NOTE]
>
>A partire da aprile 2022, Oracle JDK sarà il JDK predefinito per lo sviluppo e il funzionamento delle applicazioni AEM. Il processo di build di Cloud Manager passerà automaticamente all’utilizzo di Oracle JDK, anche se nella toolchain Maven è selezionata esplicitamente un’opzione alternativa. Per ulteriori dettagli, consulta le [note sulla versione di aprile](/help/release-notes/2022/2022-4-0.md).

### Versione JDK alternativa per l’esecuzione di Maven {#alternate-maven}

È inoltre possibile selezionare Oracle 8 o Oracle 11 come JDK per l’intera esecuzione di Maven. A differenza delle opzioni toolchain, questo cambia il JDK utilizzato per tutti i plug-in a meno che non sia impostata anche la configurazione di toolchain, nel qual caso la configurazione di toolchain viene ancora applicata per i plug-in Maven che tengono conto delle toolchain. Di conseguenza, controllare e applicare la versione Java con il [plug-in Apache Maven Enforcer](https://maven.apache.org/enforcer/maven-enforcer-plugin/) funzionerà.

A questo scopo, crea un file denominato `.cloudmanager/java-version` nel ramo dell’archivio Git utilizzato dalla pipeline. Questo file può avere come contenuto `11` o `8`. Qualsiasi altro valore viene ignorato. Se `11` è specificato, viene utilizzato Oracle 11 e la variabile di ambiente `JAVA_HOME` è impostata su `/usr/lib/jvm/jdk-11.0.2`. Se è specificato `8`, viene utilizzato Oracle 8 e la variabile di ambiente `JAVA_HOME` è impostata su `/usr/lib/jvm/jdk1.8.0_202`.

## Variabili di ambiente {#environment-variables}

### Variabili di ambiente standard {#standard-environ-variables}

In alcuni casi, potrebbe essere necessario variare il processo di creazione in base alle informazioni relative al programma o alla pipeline.

Per esempio, se la minimizzazione di JavaScript nel tempo di creazione viene eseguita tramite uno strumento come “gulp”, potrebbe essere auspicabile utilizzare un livello di minimizzazione diverso durante la creazione di un ambiente di sviluppo rispetto alla creazione di staging e produzione.

Per supportare questa funzione, Cloud Manager aggiunge al contenitore di creazione le variabili di ambiente standard per ogni esecuzione.

| Nome della variabile | Descrizione |
|---|---|
| `CM_BUILD` | Sempre impostato su `true` |
| `BRANCH` | Ramo configurato per l’esecuzione |
| `CM_PIPELINE_ID` | Identificatore numerico della pipeline |
| `CM_PIPELINE_NAME` | Nome della pipeline |
| `CM_PROGRAM_ID` | Identificatore numerico del programma |
| `CM_PROGRAM_NAME` | Il nome del programma |
| `ARTIFACTS_VERSION` | Per una pipeline di staging o produzione, la versione sintetica generata da Cloud Manager |

### Disponibilità di variabili di ambiente standard {#availability}

Le variabili di ambiente standard possono essere utilizzate in diverse posizioni.

#### Authoring, Anteprima e Pubblicazione {#author-preview-publish}

Negli ambienti di authoring, anteprima e pubblicazione è possibile utilizzare sia le normali variabili di ambiente che i segreti.

#### Dispatcher {#dispatcher}

È possibile utilizzare solo le normali variabili di ambiente con [il dispatcher.](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=it) I segreti non possono essere utilizzati.

Tuttavia, le variabili di ambiente non possono essere utilizzate nelle direttive `IfDefine`.

>[!TIP]
>
>È necessario convalidare l’utilizzo di variabili di ambiente con il [Dispatcher localmente](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools.html?lang=it) prima della distribuzione.

#### Configurazioni OSGi {#osgi}

È possibile utilizzare sia le normali variabili di ambiente che i segreti in [Configurazioni OSGi.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/configuring-osgi.html?lang=it)

### Variabili di pipeline {#pipeline-variables}

In alcuni casi, il processo di creazione può dipendere da specifiche variabili di configurazione che non sarebbero appropriate per l’inserimento nell’archivio Git o dovrebbero variare tra le esecuzioni della pipeline che utilizzano lo stesso ramo.

Cloud Manager consente di configurare queste variabili tramite l’API o il CLI di Cloud Manager in base alla pipeline. Le variabili possono essere archiviate come testo normale o crittografate quando inattive. In entrambi i casi, le variabili sono rese disponibili all’interno dell’ambiente di build come variabile di ambiente a cui è possibile fare riferimento dall’interno del file `pom.xml` o altri script di build.

Per impostare una variabile utilizzando CLI, eseguire un comando simile al seguente.

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

Le variabili attuali possono essere elencate utilizzando un comando simile al seguente.

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

Le variabili devono rispettare determinate limitazioni.

* I nomi delle variabili possono contenere solo caratteri alfanumerici e il carattere di sottolineatura (`_`).
   * Per convenzione, i nomi devono essere tutti maiuscoli.
* Esiste un limite di 200 variabili per pipeline.
* Ogni nome deve contenere meno di 100 caratteri.
* Ogni valore di stringa deve contenere meno di 2048 caratteri.
* Ogni valore secretString deve contenere meno di 500 caratteri.

Quando viene utilizzato all’interno di un file Maven `pom.xml`, generalmente è utile mappare queste variabili alle proprietà Maven utilizzando una sintassi simile alla seguente.

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
            </activation>
            <properties>
                <my.custom.property>${env.MY_CUSTOM_VARIABLE}</my.custom.property> 
            </properties>
        </profile>
```

## Installazione di pacchetti di sistema aggiuntivi {#installing-additional-system-packages}

Per funzionare completamente, alcune build richiedono l&#39;installazione di pacchetti di sistema aggiuntivi. Ad esempio, una build può richiamare uno script Python o Ruby e, di conseguenza, deve disporre di un interprete del linguaggio appropriato installato. Questa operazione può essere eseguita chiamando [`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/) per richiamare l’APT. Generalmente questa esecuzione deve essere racchiusa in un profilo Maven specifico per Cloud Manager. Per esempio, per installare Python:

```xml
        <profile>
            <id>install-python</id>
            <activation>
                <property>
                        <name>env.CM_BUILD</name>
                </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <groupId>org.codehaus.mojo</groupId>
                        <artifactId>exec-maven-plugin</artifactId>
                        <version>1.6.0</version>
                        <executions>
                            <execution>
                                <id>apt-get-update</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>update</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                            <execution>
                                <id>install-python</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>install</argument>
                                        <argument>-y</argument>
                                        <argument>--no-install-recommends</argument>
                                        <argument>python</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

Questa stessa tecnica può essere utilizzata per installare pacchetti specifici per linguaggio, ovvero utilizzando `gem` per pacchetti RubyGems o `pip` per pacchetti Python.

>[!NOTE]
>
>Se si installa in questo modo, il pacchetto di sistema non viene installato nell’ambiente di esecuzione utilizzato per eseguire Adobe Experience Manager. Se hai bisogno di installare un pacchetto di sistema nell’ambiente AEM, contatta il rappresentante Adobe.
