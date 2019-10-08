---
title: Creare un progetto di applicazione AEM
seo-title: Creare un progetto di applicazione AEM
description: 'null'
seo-description: Segui questa pagina per saperne di più sulla configurazione di un progetto AEM quando inizi a utilizzare Cloud Manager.
uuid: 7b976ebf-5358-49d8-a58d-0bae026303fa
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: guida introduttiva
discoiquuid: 76c1a8e4-d66f-4a3b-8c0c-b80c9e17700e
translation-type: tm+mt
source-git-commit: 519f43ff16e0474951f97798a8e070141e5c124b

---


# Creare un progetto di applicazione AEM {#create-an-aem-application-project}

## Utilizzo della procedura guidata per creare un progetto di applicazione AEM {#using-wizard-to-create-an-aem-application-project}

Quando i clienti sono collegati a Cloud Manager, vengono forniti con un repository git vuoto. I clienti attuali di Adobe Managed Services (AMS) (o i clienti interni di AEM che eseguono la migrazione ad AMS) in genere hanno già il codice di progetto in git (o un altro sistema di controllo della versione) e importeranno il loro progetto nell’archivio Git di Cloud Manager. I nuovi clienti, tuttavia, non hanno progetti esistenti.

Per aiutare a far iniziare i nuovi clienti, Cloud Manager è ora in grado di creare un progetto AEM minimo come punto di partenza. Questo processo è basato sul tipo di archivio del progetto [**AEM**](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-10-08T12:52:50.071-0400

2018.8.0: Added this new section

 -->

Per creare un progetto di applicazione AEM in Cloud Manager, procedi come segue:

1. Una volta effettuato l'accesso a Cloud Manager e la configurazione del programma di base è completa, nella schermata **Panoramica** verrà visualizzata una speciale chiamata alla scheda azione, se il repository è vuoto.

   ![](assets/image2018-10-3_14-29-44.png)

1. Fate clic su **Crea** per passare alla schermata Impostazione **** tubazione.

   ![](assets/image2018-10-3_14-30-22.png)

1. Fate clic su **Crea per** aprire una finestra di dialogo che consente all'utente di fornire i parametri richiesti da AEM Project Archetype. Nel modulo predefinito, la finestra di dialogo richiede due valori:

   * **Titolo** : per impostazione predefinita questo valore è impostato su Nome *programma*

   * **Nuovo nome** ramo - per impostazione predefinita è *principale*
   ![](assets/screen_shot_2018-10-08at55825am.png)

   Nella finestra di dialogo è disponibile un cassetto che può essere aperto facendo clic sul quadratino nella parte inferiore della finestra di dialogo. Nel modulo espanso, la finestra di dialogo mostra tutti i parametri di configurazione per Archetype. Molti di questi parametri hanno valori predefiniti che vengono generati in base al **Titolo**.

   ![](assets/screen_shot_2018-10-08at60032am.png)

   >[!NOTE]
   >
   >Ad esempio, se il **Titolo** è ***We.Finance***, il parametro ID artefatto del Paradiso di base viene generato come ***com.wefinance***. Se necessario, questi valori possono essere modificati.
   >
   >
   >Ad esempio, potete passare dal ***valore generato com.wefinance*** a ***net.wefinance***.

1. Fate clic su **Crea** nel passaggio precedente per creare il progetto iniziale utilizzando archetype e impegnatevi sul ramo git denominato. Al termine, è possibile impostare la pipeline.

## Impostazione del progetto {#setting-up-your-project}

### Modifica dei dettagli di impostazione del progetto {#modifying-project-setup-details}

Per essere generati e distribuiti correttamente con Cloud Manager, i progetti AEM esistenti devono rispettare alcune regole di base:

* I progetti devono essere realizzati con Apache Maven.
* Nella directory principale dell’archivio Git deve essere presente un file *pom.xml* . Questo file *pom.xml* può fare riferimento a tutti i sottomoduli (che a loro volta possono avere altri sottomoduli, ecc.) se necessario.

* Potete aggiungere riferimenti ad altri archivi di artefatti Maven nei file *pom.xml* . Tuttavia, l'accesso ai repository di artifact protetti da password o protetti da rete non è supportato.
* I pacchetti di contenuto distribuibile vengono rilevati mediante la scansione dei file *zip* del pacchetto di contenuto contenuti contenuti in una directory denominata *target*. Un numero qualsiasi di sottomoduli può produrre pacchetti di contenuto.

* Gli artifact del Dispatcher distribuibile vengono rilevati mediante la scansione di file *zip* (ancora, contenuti in una directory denominata *target*) con directory denominate *conf* e *conf.d*.

* In presenza di più pacchetti di contenuto, l'ordine delle distribuzioni dei pacchetti non è garantito. Se è necessario un ordine specifico, per definire l’ordine è possibile utilizzare le dipendenze del pacchetto di contenuto.

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-10-08T09:20:10.106-0400

2018.8.0: added existing in the opening sentence

 -->

## Dettagli ambiente build {#build-environment-details}

Cloud Manager crea e verifica il codice utilizzando un ambiente di build specializzato. Questo ambiente ha i seguenti attributi:

* L'ambiente di costruzione è basato su Linux, derivato da Ubuntu 18.04.
* Apache Maven 3.6.0 è installato.
* La versione Java installata è Oracle JDK 8u202.
* Sono installati alcuni pacchetti di sistema aggiuntivi necessari:

   * bzip2
   * decomprimere
   * libpng
   * imagemagick
   * graphicsmagick

* Altri pacchetti possono essere installati in fase di creazione come descritto [di seguito](#installing-additional-system-packages).
* Ogni costruzione è fatta su un ambiente incontaminato; il contenitore di compilazione non mantiene alcuno stato tra le esecuzioni.
* Maven è sempre eseguito con il comando: mvn — *batch-mode clean org.jacoco:jacoco-maven-plugin:Preparare-agent package*
* Maven è configurato a livello di sistema con un file settings.xml che include automaticamente il repository pubblico di Adobe **Artifact** . Per ulteriori informazioni, consultate [Adobe Public Maven Repository](https://repo.adobe.com/) .

## Attivazione dei profili condivisi in Cloud Manager {#activating-maven-profiles-in-cloud-manager}

In alcuni casi limitati, potrebbe essere necessario variare leggermente il processo di creazione quando si esegue in Cloud Manager rispetto a quando viene eseguito su workstation sviluppatore. Per questi casi, [Maven Profiles](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) può essere utilizzato per definire in che modo la build deve essere diversa in ambienti diversi, incluso Cloud Manager.

L'attivazione di un profilo Maven all'interno dell'ambiente di generazione di Cloud Manager deve essere eseguita cercando la presenza di una variabile di ambiente denominata `CM_BUILD`. Questa variabile verrà sempre impostata all'interno dell'ambiente di generazione di Cloud Manager. In alternativa, un profilo destinato a essere utilizzato solo al di fuori dell'ambiente di build di Cloud Manager dovrebbe essere fatto cercando l'assurdità di questa variabile.

Ad esempio, se desideri inviare un messaggio semplice solo quando la build viene eseguita in Cloud Manager, effettua questa operazione:

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
>Per testare questo profilo su una workstation sviluppatore, è possibile attivarlo sulla riga di comando (con `-PcmBuild`) o nell'ambiente di sviluppo integrato (IDE).

Se desideri inviare un messaggio semplice solo quando la build viene eseguita al di fuori di Cloud Manager, effettua le seguenti operazioni:

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

## Variabili di ambiente {#environment-variables}

### Variabili di ambiente standard {#standard-environ-variables}

In alcuni casi, il processo di creazione di un cliente può dipendere da variabili di configurazione specifiche che non sarebbe appropriato inserire nel repository git. Cloud Manager consente di configurare queste variabili da un Customer Success Engineer (CSE) cliente per cliente. Queste variabili sono memorizzate in una posizione di archiviazione protetta e sono visibili solo nel contenitore di compilazione per il cliente specifico. I clienti che desiderano utilizzare questa funzione devono contattare il CSE per configurare le proprie variabili.

Una volta configurate, queste variabili saranno disponibili come variabili di ambiente. Per utilizzarle come proprietà Maven, potete farvi riferimento all'interno del file pom.xml, potenzialmente all'interno di un profilo come descritto in precedenza:

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                  <property>
                        <name>env.CM_BUILD</name>
                  </property>
            </activation>
            <properties>
                  <my.custom.property>${env.MY_CUSTOM_PROPERTY}</my.custom.property>  
            </properties>
        </profile>
```

>[!NOTE]
>
>I nomi delle variabili di ambiente possono contenere solo caratteri alfanumerici e caratteri di sottolineatura (_). Per convenzione, i nomi devono essere tutti maiuscoli.

## Installazione di pacchetti di sistema aggiuntivi {#installing-additional-system-packages}

Alcune build richiedono l'installazione di pacchetti di sistema aggiuntivi per funzionare completamente. Ad esempio, una build può richiamare uno script Python o ruby e, di conseguenza, deve disporre di un interprete lingua appropriato installato. Questo può essere fatto chiamando [exec-maven-plugin](https://www.mojohaus.org/exec-maven-plugin/) per richiamare APT. In genere, questa esecuzione deve essere racchiusa in un profilo Maven specifico per Cloud Manager. Ad esempio, per installare python:

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
>L'installazione di un pacchetto di sistema in questo modo **non** lo installa nell'ambiente di runtime utilizzato per eseguire Adobe Experience Manager. Se hai bisogno di installare un pacchetto di sistema nell’ambiente AEM, contatta il tuo Customer Success Engineers (CSE).

## Skiping Content Packages {#skipping-content-packages}

In Cloud Manager, le build possono generare un numero qualsiasi di pacchetti di contenuto.
Per diversi motivi, può essere utile produrre un pacchetto di contenuti ma non distribuirlo. Questo può essere utile, ad esempio, quando si creano pacchetti di contenuto utilizzati solo per il test o che verranno reinseriti in un pacchetto da un altro passaggio del processo di creazione, ovvero come pacchetto secondario di un altro pacchetto.

Per soddisfare questi scenari, Cloud Manager cercherà una proprietà denominata ***cloudManagerTarget*** nelle proprietà dei pacchetti di contenuto incorporati. Se questa proprietà è impostata su none, il pacchetto verrà ignorato e non distribuito. Il meccanismo per impostare questa proprietà dipende dal modo in cui la build produce il pacchetto di contenuto. Ad esempio, con il filevault-maven-plugin si configura il plugin come segue:

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

Con content-package-maven-plugin è simile:

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

## Sviluppare il codice in base alle best practice {#develop-your-code-based-on-best-practices}

I team Adobe Engineering e Consulting hanno sviluppato una serie [completa di best practice per gli sviluppatori](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/best-practices.html)di AEM.
