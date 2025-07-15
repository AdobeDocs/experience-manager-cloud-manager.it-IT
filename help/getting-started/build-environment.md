---
title: Ambiente di build
description: Scopri l’ambiente di build specializzato che Cloud Manager usa per creare e testare il codice.
exl-id: b3543320-66d4-4358-8aba-e9bdde00d976
source-git-commit: e9f3ac70735a95a15b1f63cf40496672162de777
workflow-type: tm+mt
source-wordcount: '1161'
ht-degree: 83%

---


# Ambiente di build {#build-environment}

Scopri l’ambiente di build specializzato che Cloud Manager usa per creare e testare il codice.

## Dettagli dell’ambiente {#details}

Gli ambienti di build di Cloud Manager dispongono degli attributi seguenti.

* L’ambiente di build è basato su Linux, derivato da Ubuntu 22.04.
* Apache Maven 3.9.4 è installato.
   * Adobe consiglia agli utenti di [aggiornare i loro archivi Maven per utilizzare HTTPS invece di HTTP](#https-maven).
* Le versioni Java installate sono Oracle JDK 8u371 e Oracle JDK 11.0.22.
   * `/usr/lib/jvm/jdk1.8.0_401`
   * `/usr/lib/jvm/jdk-11.0.22`
* Per impostazione predefinita, la variabile dell’ambiente `JAVA_HOME` è impostata su `/usr/lib/jvm/jdk1.8.0_401`, che contiene Oracle JDK 8u401. Per ulteriori dettagli, vedi la sezione [Versione JDK di esecuzione Maven alternativa](#alternate-maven).
* Sono installati anche alcuni altri pacchetti di sistema necessari.
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* Altri pacchetti possono essere installati in fase di build come descritto nella sezione [Installazione di pacchetti di sistema aggiuntivi](#installing-additional-system-packages).
* Ogni build viene realizzata in un ambiente pulito. Il contenitore di build non mantiene alcuno stato da un’esecuzione all’altra.
* Maven viene eseguito con questi tre comandi:
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* Maven è configurato a livello di sistema con un file `settings.xml`, che include automaticamente l’archivio di artefatti pubblico di Adobe utilizzando un profilo denominato `adobe-public`. Per ulteriori informazioni, consulta l’[Archivio Maven pubblico di Adobe](https://repo1.maven.org/).
* Node.js 18 è disponibile per [pipeline front-end](/help/overview/ci-cd-pipelines.md).

>[!IMPORTANT]
>Il supporto delle toolchain Maven è stato rimosso a partire da Cloud Manager 2025.06.0. La selezione JDK è ora supportata solo tramite `.cloudmanager/java-version`. Per ulteriori informazioni, vedere [Utilizzo di una versione Java specifica](#using-java-version).

>[!NOTE]
>
>Sebbene Cloud Manager non definisca una versione specifica del `jacoco-maven-plugin`, la versione utilizzata deve essere `0.7.5.201505241946` o superiore.

>[!TIP]
>
>Per informazioni sull’utilizzo delle API di Cloud Manager, consulta le seguenti risorse aggiuntive:
>
>* [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager)
>* [Creazione di un’integrazione API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/)
>* [Autorizzazioni API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/)

## Archivi Maven HTTPS {#https-maven}

Cloud Manager [2023.10.0](/help/release-notes/2023/2023-10-0.md) ha iniziato un aggiornamento continuo dell’ambiente di build (completandolo con la versione 2023.12.0), che includeva un aggiornamento a Maven 3.8.8. Come modifica significativa introdotta in Maven 3.8.1 è stato apportato un miglioramento della sicurezza volto a mitigare potenziali vulnerabilità. In particolare, Maven ora disabilita tutte le corrispondenze `http://*` non sicure per impostazione predefinita, come descritto nelle [note sulla versione di Maven](https://maven.apache.org/docs/3.8.1/release-notes.html#cve-2021-26291).

Come risultato di questo miglioramento sulla sicurezza, alcuni utenti potrebbero riscontrare problemi durante la fase di build, in particolare durante il download di artefatti dagli archivi Maven che utilizzano connessioni HTTP non sicure.

Per garantire un’esperienza fluida con la versione aggiornata, Adobe consiglia agli utenti di aggiornare gli archivi Maven per utilizzare HTTPS invece di HTTP. Questo adeguamento è in linea con la crescente tendenza del settore verso protocolli di comunicazione sicuri e contribuisce a mantenere un processo di creazione sicuro e affidabile.

## Utilizzo di una versione Java specifica {#using-java-version}

Per impostazione predefinita, i progetti generati dal processo di build di Cloud Manager utilizzano il JDK di Oracle 8. I clienti che desiderano utilizzare un JDK alternativo possono selezionare una versione JDK alternativa per l’intero processo di esecuzione Maven.

>[!IMPORTANT]
>
>Le toolchain Maven non sono più supportate in Cloud Manager 2025.06.0. Tieni presente che le pipeline contenenti una configurazione maven-toolchains-plugin avranno esito negativo con `Cannot find matching toolchain definitions.` Utilizza il file `.cloudmanager/java-version` per selezionare JDK 11, 17 o 21.
>
>**Guida alla migrazione:**
>
>1. Rimuovere le toolchain eliminando qualsiasi voce `org.apache.maven.plugins:maven-toolchains-plugin` e qualsiasi elemento `toolchains.xml` di cui è stato eseguito il commit nel controllo del codice sorgente.
>1. Selezionare un JDK con `.cloudmanager/java-version`(21, 17 o 11) come descritto in [Versione JDK alternativa per l&#39;esecuzione Maven](#alternate-maven).
>1. Adobe consiglia di cancellare la cache di build di Cloud Manager o di attivare una nuova esecuzione della pipeline.
>

<!--DEPRECATED 
### Maven Toolchains {#maven-toolchains}

The [Maven Toolchains plug-in](https://maven.apache.org/plugins/maven-toolchains-plugin/) lets projects select a specific JDK (or toolchain) to use in the context of toolchains-aware Maven plug-ins. This process is done in the project's `pom.xml` file by specifying a vendor and version value. A sample section in the `pom.xml` file is the following:

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

This process causes all toolchains-aware Maven plug-ins to use the Oracle JDK, version 11.

When using this method, Maven itself still runs using the default JDK (Oracle 8) and the `JAVA_HOME` environment variable is not changed. Therefore, checking or enforcing the Java version through plug-ins like the [Apache Maven Enforcer Plug-in](https://maven.apache.org/enforcer/maven-enforcer-plugin/) does not work and such plug-ins must not be used.

The currently available vendor/version combinations are:

|Vendor|Version|
|---|---|
| Oracle |1.8|
| Oracle |1.11|
| Oracle |11|
| Sun |1.8|
| Sun |1.11|
| Sun |11|

>[!NOTE]
>
>Starting April 2022, Oracle JDK is going to be the default JDK for the development and operation of AEM applications. Cloud Manager's build process automatically switches to using Oracle JDK, even if an alternative option is explicitly selected in the Maven toolchain. See the [April release notes](/help/release-notes/2022/2022-4-0.md) for more details. -->

### Versione JDK alternativa per l’esecuzione di Maven {#alternate-maven}

È possibile selezionare Oracle 8 o Oracle 11 come JDK per l’intera esecuzione Maven. Questo approccio cambia il JDK utilizzato per tutti i plug-in. È quindi possibile verificare e applicare la versione Java utilizzando il [plug-in Apache Maven Enforcer](https://maven.apache.org/enforcer/maven-enforcer-plugin/).

A questo scopo, crea un file denominato `.cloudmanager/java-version` nel ramo dell’archivio Git utilizzato dalla pipeline. Questo file può avere come contenuto `11` o `8`. Qualsiasi altro valore viene ignorato. Se si specifica `11`, verrà utilizzato Oracle 11 e la variabile di ambiente `JAVA_HOME` verrà impostata su `/usr/lib/jvm/jdk-11.0.22`. Se si specifica `8`, verrà utilizzato Oracle 8 e la variabile di ambiente `JAVA_HOME` verrà impostata su `/usr/lib/jvm/jdk1.8.0_401`.

## Variabili di ambiente {#environment-variables}

### Variabili di ambiente standard {#standard-environ-variables}

In alcuni casi, potrebbe essere necessario variare il processo di creazione in base alle informazioni relative al programma o alla pipeline.

Ad esempio, quando utilizzi uno strumento come “gulp” per la minimizzazione di JavaScript, potresti preferire livelli di minimizzazione diversi per gli ambienti di sviluppo rispetto agli ambienti di staging e produzione.

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

#### Ambienti di authoring, anteprima e pubblicazione {#author-preview-publish}

Negli ambienti di authoring, anteprima e pubblicazione è possibile utilizzare sia le normali variabili di ambiente che i segreti.

#### Dispatcher {#dispatcher}

Solo le variabili di ambiente normali possono essere utilizzate con [il Dispatcher](https://experienceleague.adobe.com/it/docs/experience-manager-dispatcher/using/dispatcher). I segreti non possono essere utilizzati.

Tuttavia, le variabili di ambiente non possono essere utilizzate nelle direttive `IfDefine`.

>[!TIP]
>
>Convalida l’utilizzo di variabili di ambiente con il [Dispatcher localmente](https://experienceleague.adobe.com/it/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools) prima della distribuzione.

#### Configurazioni OSGi {#osgi}

Le normali variabili di ambiente e i segreti possono essere utilizzati nelle [configurazioni OSGi](https://experienceleague.adobe.com/it/docs/experience-manager-65/content/implementing/deploying/configuring/configuring-osgi).

### Variabili di pipeline {#pipeline-variables}

In alcuni casi, il processo di compilazione può dipendere da specifiche variabili di configurazione che non sarebbero appropriate per l’inserimento nell’archivio Git o dovrebbero variare tra le esecuzioni della pipeline che utilizzano lo stesso ramo.

Cloud Manager consente di configurare queste variabili tramite l’API o l’interfaccia della riga di comando di Cloud Manager, in base alla pipeline. Le variabili possono essere archiviate come testo normale o crittografate quando inattive. In entrambi i casi, le variabili sono rese disponibili all’interno dell’ambiente di build come una variabile di ambiente a cui è possibile fare riferimento dal file `pom.xml` o da altri script della build.

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
* Ogni nome deve avere una lunghezza inferiore a 100 caratteri.
* Ogni valore di stringa deve avere una lunghezza inferiore a 2048 caratteri.
* Ogni valore della variabile `secretString` deve avere una lunghezza inferiore a 500 caratteri.

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

Per funzionare completamente, alcune build richiedono l’installazione di pacchetti di sistema aggiuntivi. Ad esempio, una build può richiamare uno script Python o Ruby e, di conseguenza, deve disporre di un interprete di lingua appropriato installato. Questo scenario può essere eseguito chiamando [`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/) per richiamare l’APT. Questa esecuzione deve generalmente essere integrata in un profilo Maven specifico per Cloud Manager. Ad esempio, per installare Python puoi effettuare le seguenti operazioni:

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

Questa tecnica può essere utilizzata anche per installare pacchetti specifici per lingua. Ovvero, utilizzando `gem` per pacchett RubyGems o `pip` per pacchetti Python.

>[!NOTE]
>
>Installando un pacchetto di sistema in questo modo, non lo si installa nell’ambiente di runtime utilizzato per l’esecuzione di Adobe Experience Manager. Se hai bisogno di installare un pacchetto di sistema nell’ambiente AEM, contatta il rappresentante Adobe.
