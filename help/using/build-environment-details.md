---
title: Informazioni sull’ambiente di creazione
description: Seguite questa pagina per informazioni sugli ambienti
translation-type: tm+mt
source-git-commit: 57a99792e151bd5fe69c8372b6a9d3b100036a51
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Informazioni sull’ambiente di creazione {#build-environment-details}

Cloud Manager crea e verifica il codice utilizzando un ambiente di build specializzato. Questo ambiente ha i seguenti attributi:

* L&#39;ambiente di costruzione è basato su Linux, derivato da Ubuntu 18.04.
* Apache Maven 3.6.0 è installato.
* Le versioni Java installate sono Oracle JDK 8u202 e 11.0.2.
* Sono installati alcuni pacchetti di sistema aggiuntivi necessari:

   * bzip2
   * decomprimere
   * libpng
   * imagemagick
   * graphicsmagick

* Altri pacchetti possono essere installati in fase di creazione come descritto [di seguito](#installing-additional-system-packages).
* Ogni costruzione è fatta su un ambiente incontaminato; il contenitore di compilazione non mantiene alcuno stato tra le esecuzioni.
* Maven è sempre eseguito con questi tre comandi:

   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`

* Maven è configurato a livello di sistema con un file settings.xml che include automaticamente il repository **Artifact**  Adobe pubblico. Per ulteriori informazioni, consultate [archivio](https://repo.adobe.com/) Pubblico Paradiso in Adobe.

>[!NOTE]
>Anche se Cloud Manager non definisce una versione specifica di `jacoco-maven-plugin`, la versione utilizzata deve essere almeno `0.7.5.201505241946`.

## Utilizzo di Java 11 {#using-java-11}

Cloud Manager ora supporta la creazione di progetti per i clienti con Java 8 e Java 11. Per impostazione predefinita, i progetti vengono creati utilizzando Java 8. I clienti che intendono utilizzare Java 11 nei loro progetti possono farlo utilizzando il plugin [Apache Maven Toolchain](https://maven.apache.org/plugins/maven-toolchains-plugin/).

A questo scopo, nel file pom.xml aggiungete una `<plugin>` voce che si presenta così:

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

>[!NOTE]
>I `vendor` valori supportati sono `oracle` e `sun` e i `version` valori supportati sono `1.8`, `1.11`e `11`.

>[!NOTE]
>La build del progetto Cloud Manager utilizza ancora Java 8 per richiamare Maven, pertanto il controllo o l&#39;applicazione della versione Java configurata nel plug-in della catena di strumenti tramite plug-in come il plug-in [](https://maven.apache.org/enforcer/maven-enforcer-plugin/) Apache Maven Enforcer non funziona e tali plug-in non devono essere utilizzati.

## Variabili di ambiente {#environment-variables}

### Variabili di ambiente standard {#standard-environ-variables}

In alcuni casi, i clienti trovano necessario variare il processo di creazione in base alle informazioni sul programma o sulla pipeline.

Ad esempio, se si sta effettuando una riduzione JavaScript in fase di creazione, tramite uno strumento come gulp, potrebbe essere necessario utilizzare un livello di riduzione diverso durante la creazione di un ambiente di sviluppo anziché costruire per il palco e la produzione.

Per supportare questa funzione, Cloud Manager aggiunge queste variabili di ambiente standard al contenitore di build per ogni esecuzione.

| **Nome variabile** | **Definizione** |
|---|---|
| CM_BUILD | Sempre impostato su &quot;true&quot; |
| BRANCH | Il ramo configurato per l&#39;esecuzione |
| CM_PIPELINE_ID | Identificatore numerico della pipeline |
| CM_PIPELINE_NAME | Il nome della pipeline |
| CM_PROGRAM_ID | Identificatore numerico del programma |
| CM_PROGRAM_NAME | Nome del programma |
| ARTIFACTS_VERSION | Per una fase o una pipeline di produzione, la versione sintetica generata da Cloud Manager |

### Variabili pipeline {#pipeline-variables}

In alcuni casi, il processo di creazione di un cliente può dipendere da variabili di configurazione specifiche che non sarebbero adatte a essere inserite nell&#39;archivio Git o che dovrebbero variare tra le esecuzioni della pipeline che utilizzano lo stesso ramo.

Cloud Manager consente di configurare queste variabili tramite l&#39;API di Cloud Manager o l&#39;interfaccia CLI di Cloud Manager in base alla pipeline. Le variabili possono essere memorizzate come testo normale o cifrate a riposo. In entrambi i casi, le variabili sono rese disponibili all&#39;interno dell&#39;ambiente di creazione come variabile di ambiente a cui è possibile fare riferimento all&#39;interno del `pom.xml` file o di altri script di compilazione.

Per impostare una variabile utilizzando CLI, eseguire un comando come:

`$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test`

È possibile elencare le variabili correnti:

`$ aio cloudmanager:list-pipeline-variables PIPELINEID`

I nomi delle variabili possono contenere solo caratteri alfanumerici e carattere di sottolineatura (_). Per convenzione, i nomi devono essere tutti maiuscoli. Esiste un limite di 200 variabili per pipeline, ogni nome deve essere inferiore a 100 caratteri e ogni valore deve essere inferiore a 2048 caratteri.

Se utilizzata all&#39;interno di un `Maven pom.xml` file, è generalmente utile mappare queste variabili alle proprietà Maven utilizzando una sintassi simile a quella riportata di seguito:

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

Alcune build richiedono l&#39;installazione di pacchetti di sistema aggiuntivi per funzionare completamente. Ad esempio, una build può richiamare uno script Python o ruby e, di conseguenza, deve disporre di un interprete lingua appropriato installato. Questo può essere fatto chiamando [exec-maven-plugin](https://www.mojohaus.org/exec-maven-plugin/) per richiamare APT. In genere, questa esecuzione deve essere racchiusa in un profilo Maven specifico per Cloud Manager. Ad esempio, per installare python:

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

Questa stessa tecnica può essere utilizzata per installare pacchetti specifici per la lingua, ad esempio per `gem` RubyGems o `pip` per Python Packages.

>[!NOTE]
>
>L&#39;installazione di un pacchetto di sistema in questo modo **non** lo installa nell&#39;ambiente di runtime utilizzato per eseguire Adobe Experience Manager. Se hai bisogno di installare un pacchetto di sistema nell&#39;ambiente AEM, contatta il tuo Customer Success Engineers (CSE).
