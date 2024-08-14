---
title: Ambiente di build
description: Scopri l’ambiente di build specializzato che Cloud Manager usa per creare e testare il codice.
exl-id: b3543320-66d4-4358-8aba-e9bdde00d976
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '1263'
ht-degree: 53%

---


# L’ambiente di build {#build-environment}

Scopri l’ambiente di build specializzato che Cloud Manager usa per creare e testare il codice.

## Dettagli dell’ambiente {#details}

Gli ambienti di build di Cloud Manager hanno i seguenti attributi.

* L’ambiente di build è basato su Linux, derivato da Ubuntu 22.04.
* Apache Maven 3.9.4 è installato.
   * L&#39;Adobe consiglia agli utenti [di aggiornare gli archivi Maven per utilizzare HTTPS anziché HTTP](#https-maven).
* Le versioni Java installate sono Oracle JDK 8u371 e Oracle JDK 11.0.22.
   * `/usr/lib/jvm/jdk1.8.0_401`
   * `/usr/lib/jvm/jdk-11.0.22`
* Per impostazione predefinita, la variabile di ambiente `JAVA_HOME` è impostata su `/usr/lib/jvm/jdk1.8.0_401`, che contiene Oracle JDK 8u401. Per ulteriori dettagli, vedi la sezione [Versione JDK di esecuzione Maven alternativa](#alternate-maven).
* Sono installati anche alcuni altri pacchetti di sistema necessari.
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* Altri pacchetti possono essere installati in fase di compilazione come descritto nella sezione [Installazione di pacchetti di sistema aggiuntivi](#installing-additional-system-packages).
* Ogni build viene realizzata in un ambiente incontaminato. Il contenitore di build non mantiene alcuno stato da un’esecuzione all’altra.
* Maven viene sempre eseguito con questi tre comandi:
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* Maven è configurato a livello di sistema con un file `settings.xml`, che include automaticamente l’archivio di artefatti pubblico di Adobe utilizzando un profilo denominato `adobe-public`. Per ulteriori dettagli, vedi l&#39;[archivio Maven pubblico di Adobe](https://repo1.maven.org/).
* Node.js 18 è disponibile per [pipeline front-end](/help/overview/ci-cd-pipelines.md).

>[!NOTE]
>
>Sebbene Cloud Manager non definisca una versione specifica del `jacoco-maven-plugin`, la versione utilizzata deve essere `0.7.5.201505241946` o superiore.

>[!TIP]
>
>Consulta le seguenti risorse aggiuntive per scoprire come utilizzare le API di Cloud Manager:
>
>* [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager)
>* [Creazione di un’integrazione API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/)
>* [Autorizzazioni API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/)

## Archivi Maven HTTPS {#https-maven}

In Cloud Manager [2023.10.0](/help/release-notes/2023/2023-10-0.md) è stato avviato un aggiornamento continuo dell&#39;ambiente di build (completato con la versione 2023.12.0), che include un aggiornamento a Maven 3.8.8. Una modifica significativa introdotta in Maven 3.8.1 è stata un miglioramento della sicurezza volto a mitigare potenziali vulnerabilità. In particolare, Maven ora disabilita tutti i mirror non sicuri di `http://*` per impostazione predefinita, come descritto nelle [Note sulla versione di Maven](https://maven.apache.org/docs/3.8.1/release-notes.html#cve-2021-26291).

Come risultato di questo miglioramento sulla sicurezza, alcuni utenti potrebbero riscontrare problemi durante la fase di build, in particolare durante il download di artefatti dagli archivi Maven che utilizzano connessioni HTTP non sicure.

Per garantire un’esperienza fluida con la versione aggiornata, Adobe consiglia agli utenti di aggiornare gli archivi Maven per utilizzare HTTPS invece di HTTP. Questo adeguamento è in linea con la crescente tendenza del settore verso protocolli di comunicazione sicuri e contribuisce a mantenere un processo di creazione sicuro e affidabile.

## Utilizzo di una versione Java specifica {#using-java-version}

Per impostazione predefinita, i progetti generati dal processo di generazione di Cloud Manager utilizzano il JDK Oracle 8. I clienti che desiderano utilizzare un JDK alternativo hanno due opzioni.

* [Toolchain Maven](#maven-toolchains)
* [Selezione di una versione JDK alternativa per l’intero processo di esecuzione Maven](#alternate-maven)

### Toolchain Maven {#maven-toolchains}

Il plug-in [Maven Toolchain](https://maven.apache.org/plugins/maven-toolchains-plugin/) consente ai progetti di selezionare un JDK (o toolchain) specifico da utilizzare nel contesto di plug-in Maven compatibili con le toolchain. Questo processo viene eseguito nel file `pom.xml` del progetto specificando un valore di fornitore e di versione. Di seguito è riportata una sezione di esempio nel file `pom.xml`:

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

Questo procedimento fa sì che tutti i plug-in Maven compatibili con le toolchain utilizzino l’Oracle JDK versione 11.

Quando si utilizza questo metodo, Maven stesso viene comunque eseguito utilizzando il JDK predefinito (Oracle 8) e la variabile di ambiente `JAVA_HOME` non viene modificata. Pertanto, non è possibile controllare o applicare la versione Java tramite plug-in come [Apache Maven Enforcer Plug-in](https://maven.apache.org/enforcer/maven-enforcer-plugin/) e tali plug-in non devono essere utilizzati.

Le combinazioni fornitore/versione attualmente disponibili sono:

| Fornitore | Versione |
|---|---|
| Oracle | 1.8 |
| Oracle | 1.11 |
| Oracle | 11 |
| dom | 1.8 |
| dom | 1.11 |
| dom | 11 |

>[!NOTE]
>
>A partire da aprile 2022, Oracle JDK sarà il JDK predefinito per lo sviluppo e il funzionamento delle applicazioni AEM. Il processo di build di Cloud Manager passa automaticamente all’uso di Oracle JDK, anche se nella toolchain Maven è selezionata esplicitamente un’opzione alternativa. Per ulteriori dettagli, consulta le [note sulla versione di aprile](/help/release-notes/2022/2022-4-0.md).

### Versione JDK alternativa per l’esecuzione Maven {#alternate-maven}

È inoltre possibile selezionare Oracle 8 o Oracle 11 come JDK per l’intera esecuzione di Maven. A differenza delle opzioni toolchain, questo cambia il JDK utilizzato per tutti i plug-in a meno che non sia impostata anche la configurazione delle toolchain, nel qual caso la configurazione delle toolchain viene ancora applicata per i plug-in Maven che tengono conto delle toolchain. Di conseguenza, controllare e applicare la versione Java con il plug-in [Apache Maven Enforcer](https://maven.apache.org/enforcer/maven-enforcer-plugin/) funziona.

Per eseguire questo processo, crea un file denominato `.cloudmanager/java-version` nel ramo dell’archivio Git utilizzato dalla pipeline. Questo file può avere come contenuto `11` o `8`. Qualsiasi altro valore viene ignorato. Se `11` è specificato, viene utilizzato Oracle 11 e la variabile di ambiente `JAVA_HOME` è impostata su `/usr/lib/jvm/jdk-11.0.22`. Se è specificato `8`, viene utilizzato Oracle 8 e la variabile di ambiente `JAVA_HOME` è impostata su `/usr/lib/jvm/jdk1.8.0_401`.

## Variabili di ambiente {#environment-variables}

### Variabili di ambiente standard {#standard-environ-variables}

In alcuni casi, potrebbe essere necessario variare il processo di creazione in base alle informazioni relative al programma o alla pipeline.

Ad esempio, quando utilizzi uno strumento come gulp per la minimizzazione di JavaScript, potresti preferire livelli di minimizzazione diversi per gli ambienti di sviluppo rispetto agli ambienti di staging e produzione.

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

### Disponibilità della variabile di ambiente standard {#availability}

Le variabili di ambiente standard possono essere utilizzate in diverse posizioni.

#### Ambienti di authoring, anteprima e pubblicazione {#author-preview-publish}

Negli ambienti di authoring, anteprima e pubblicazione è possibile utilizzare sia le normali variabili di ambiente che i segreti.

#### Dispatcher {#dispatcher}

Solo le normali variabili di ambiente possono essere utilizzate con [Dispatcher](https://experienceleague.adobe.com/it/docs/experience-manager-dispatcher/using/dispatcher). I segreti non possono essere utilizzati.

Tuttavia, le variabili di ambiente non possono essere utilizzate in `IfDefine` direttive.

>[!TIP]
>
>Convalida l&#39;utilizzo delle variabili di ambiente con [Dispatcher localmente](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools) prima della distribuzione.

#### Configurazioni OSGi {#osgi}

Le normali variabili di ambiente e i segreti possono essere utilizzati nelle [configurazioni OSGi](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/configuring/configuring-osgi).

### Variabili della pipeline {#pipeline-variables}

In alcuni casi, il processo di build può dipendere da specifiche variabili di configurazione che non sarebbero appropriate per l’inserimento nell’archivio Git o che dovrebbero variare tra le esecuzioni della pipeline che utilizzano lo stesso ramo.

Cloud Manager consente di configurare queste variabili tramite l’API o l’interfaccia della riga di comando di Cloud Manager, in base alla pipeline. Le variabili possono essere archiviate come testo normale o crittografate quando inattive. In entrambi i casi, le variabili sono rese disponibili all&#39;interno dell&#39;ambiente di build come variabile di ambiente, a cui è possibile fare riferimento dal file `pom.xml` o da altri script di build.

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
* Ogni valore `secretString` deve contenere meno di 500 caratteri.

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

Per funzionare completamente, alcune build richiedono l’installazione di pacchetti di sistema aggiuntivi. Ad esempio, una build può richiamare uno script Python o Ruby e, di conseguenza, deve disporre di un interprete del linguaggio appropriato installato. Questo scenario può essere eseguito chiamando [`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/) per richiamare APT. Questa esecuzione deve generalmente essere integrata in un profilo Maven specifico per Cloud Manager. Ad esempio, per installare Python puoi effettuare le seguenti operazioni:

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

Questa tecnica può essere utilizzata anche per installare pacchetti specifici per linguaggio. In altre parole, utilizzando `gem` per RubyGems o `pip` per i pacchetti Python.

>[!NOTE]
>
>Installando un pacchetto di sistema in questo modo, non lo si installa nell’ambiente di runtime utilizzato per l’esecuzione di Adobe Experience Manager. Se hai bisogno di installare un pacchetto di sistema nell’ambiente AEM, contatta il rappresentante Adobe.
