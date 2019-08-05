---
title: Creare un progetto applicazione AEM
seo-title: Creare un progetto applicazione AEM
description: 'null'
seo-description: Segui questa pagina per saperne di più sulla configurazione di un progetto AEM quando inizi a usare Cloud Manager.
uuid: 7 b 976 ebf -5358-49 d 8-a 58 d -0 bae 026303 fa
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: getting-started
discoiquuid: 76 c 1 a 8 e 4-d 66 f -4 a 3 b -8 c 0 c-b 80 c 9 e 17700 e
translation-type: tm+mt
source-git-commit: 81f4e0b3b31a8be1f0620b70442b0268159e4ec0

---


# Creare un progetto applicazione AEM {#create-an-aem-application-project}

## Utilizzo della procedura guidata per creare un progetto applicazione AEM {#using-wizard-to-create-an-aem-application-project}

Quando i clienti sono collegati a Cloud Manager, vengono forniti con un archivio git vuoto. I clienti correnti di Servizi gestiti Adobe (AMS) (o clienti AEM interni che eseguono la migrazione ad AMS) in genere dispongono già del codice del progetto in git (o di un altro sistema di controllo delle versioni) e importeranno il proprio progetto nell'archivio git di Experience Manager. I nuovi clienti, tuttavia, non hanno progetti esistenti.

Per aiutare i nuovi clienti a iniziare, Cloud Manger è ora in grado di creare un progetto AEM minimo come punto di partenza. Questo processo si basa sull'archivio di progetti [**AEM**](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-10-08T12:52:50.071-0400

2018.8.0: Added this new section

 -->

Segui i passaggi seguenti per creare un progetto applicazione AEM in Cloud Manager:

1. Una volta effettuato il login a Cloud Manager e la configurazione di base del programma è completa, nella schermata **Panoramica** verrà visualizzata una richiesta speciale di invito all'azione, se l'archivio è vuoto.

   ![](assets/image2018-10-3_14-29-44.png)

1. Fate clic su **Crea** per passare alla **schermata Configurazione** pipeline.

   ![](assets/image2018-10-3_14-30-22.png)

1. Fate clic su **Crea per** aprire una finestra di dialogo, che consente all'utente di fornire i parametri richiesti dall'archivio di progetti AEM. Nel modulo predefinito, la finestra di dialogo richiede due valori:

   * **Titolo** : per impostazione predefinita, viene impostato sul nome *del programma*

   * **Nuovo nome** ramo: per impostazione predefinita, questo *è*
   ![](assets/screen_shot_2018-10-08at55825am.png)

   La finestra di dialogo presenta un cassetto che può essere aperto facendo clic sulla maniglia verso il fondo della finestra di dialogo. Nel modulo espanso, la finestra di dialogo mostra tutti i parametri di configurazione per l'Archetype. Molti di questi parametri presentano valori predefiniti generati in base al **Titolo**.

   ![](assets/screen_shot_2018-10-08at60032am.png)

   >[!NOTE]
   >
   >Ad esempio, se **il Titolo** è ***We. Finance***, il parametro ID artefatto di base è generato come ***com. wefinance***. Se necessario, potete modificarli.
   >
   >
   >Ad esempio, potete cambiare dal ***valore com. wefinance generato*** a ***net. wefinance***.

1. Fate clic **su Crea** nel passaggio precedente per creare il progetto iniziale utilizzando l'archetype e assegnando al ramo git denominato. Una volta effettuata questa operazione, potete configurare la pipeline.

## Configurazione del progetto {#setting-up-your-project}

### Modifica dei dettagli di configurazione progetto {#modifying-project-setup-details}

Per creare e distribuire correttamente con Cloud Manager, i progetti AEM esistenti devono rispettare alcune regole di base:

* I progetti devono essere creati utilizzando Apache Maven.
* Nella directory principale *dell'archivio Git deve essere presente un* file pom.xml. Questo *file pom.xml* può fare riferimento a tanti sottomoduli (che a loro volta possono avere altri sottomoduli, ecc.) se necessario.

* Nei file *pom.xml* è possibile aggiungere riferimenti ad altri archivi Artefatti Maven. Tuttavia, l'accesso a archivi artefatti protetti da password o protetti da rete non è supportato.
* I pacchetti di contenuto implementabili vengono scoperti mediante la scansione dei file *ZIP* del pacchetto che sono contenuti in una directory denominata *target*. Un numero qualsiasi di sottomoduli potrebbe produrre pacchetti di contenuto.

* Gli artefatti del dispatcher Deployable vengono scoperti mediante la scansione dei *file zip* (anche contenuti in una directory denominata *target*) con directory denominate *conf* e *conf. d*.

* Se sono presenti più pacchetti di contenuto, l'ordine delle distribuzioni del pacchetto non è garantito. Qualora sia necessario un ordine specifico, per definire l'ordine sarà possibile utilizzare dipendenze del pacchetto di contenuto.

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-10-08T09:20:10.106-0400

2018.8.0: added existing in the opening sentence

 -->

## Dettagli ambiente build {#build-environment-details}

Cloud Manager crea e verifica il codice utilizzando un ambiente di build specializzato. Questo ambiente dispone dei seguenti attributi:

* L'ambiente di generazione è basato su Linux, derivato da Ubuntu 18.04.
* Apache Maven 3.6.0 è installato.
* La versione Java installata è Oracle JDK 8 u 202.
* Sono installati alcuni pacchetti di sistema aggiuntivi:

   * bzip2
   * decomprimere
   * libpng
   * imagemagick
   * graphicsmagick

* Altri pacchetti possono essere installati in fase di creazione, come descritto [di seguito](#installing-additional-system-packages).
* Ogni build viene realizzata su un ambiente intatto; il contenitore di build non mantiene alcuno stato tra esecuzioni.
* Maven è sempre eseguito con il comando: *mvn —batch-mode clean org. jacoco: jacoco-maven-plugin: prepara-agente, pacchetto*
* Maven è configurato a livello di sistema con un file settings.xml che include automaticamente l'archivio pubblico Adobe **Artifact** . Per ulteriori informazioni, consultate [l'archivio](https://repo.adobe.com/) di Maven pubblico di Adobe.

## Attivazione dei profili Maven in Cloud Manager {#activating-maven-profiles-in-cloud-manager}

In alcuni casi limitati, potrebbe essere necessario variare leggermente il processo di creazione quando viene eseguito in Cloud Manager e non quando viene eseguito sulle workstation per sviluppatori. Per questi casi, [i Profili Maven](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) possono essere utilizzati per definire il modo in cui la build deve essere diversa in ambienti diversi, incluso Cloud Manager.

L'attivazione di un profilo Maven nell'ambiente di creazione di Cloud Manager deve essere eseguita cercando la presenza di una variabile di ambiente denominata `CM_BUILD`. Questa variabile viene sempre impostata all'interno dell'ambiente di generazione di Cloud Manager. In modo analogo, un profilo destinato alla sola uso all'esterno dell'ambiente di creazione di Cloud Manager deve essere eseguito cercando l'ordine di questa variabile.

Ad esempio, se desiderate inviare un messaggio semplice solo quando la build viene eseguita all'interno di Cloud Manager, effettuate questa operazione:

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
>Per testare questo profilo su una workstation sviluppatore, puoi attivarlo sulla riga di comando (con `-PcmBuild`) o nell'ambiente di sviluppo integrato (IDE).

E se desiderate inviare un messaggio semplice solo quando la build viene eseguita all'esterno di Cloud Manager, effettuate questa operazione:

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

## Variabili d'ambiente personalizzate

In alcuni casi, il processo di creazione di un cliente può dipendere da variabili di configurazione specifiche che sarebbe improprio da inserire nell'archivio git. Cloud Manager consente di configurare queste variabili da un Customer Success Engineer (CSE) a livello singolo. Queste variabili sono memorizzate in un percorso di archiviazione protetto e sono visibili solo nel contenitore Build per il cliente specifico. I clienti che desiderano utilizzare questa funzione devono contattare il proprio CSE per configurarne le variabili.

Una volta configurate, queste variabili saranno disponibili come variabili d'ambiente. Per utilizzarle come proprietà Maven, potete farvi riferimento all'interno del file pom.xml, potenzialmente all'interno di un profilo come descritto in precedenza:

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
>I nomi delle variabili dell'ambiente possono contenere solo caratteri alfanumerici e carattere di sottolineatura (_). Per convenzione, i nomi devono essere tutti maiuscoli.

## Installazione di pacchetti di sistema aggiuntivi {#installing-additional-system-packages}

Per alcune build è necessario installare pacchetti di sistema aggiuntivi per funzionare completamente. Ad esempio, una build potrebbe richiamare uno script Python o Ruby e, di conseguenza, deve avere installato un interprete della lingua appropriato. Per farlo, chiamate [exec-maven-plugin](https://www.mojohaus.org/exec-maven-plugin/) per richiamare APT. In genere deve essere racchiuso in un profilo Maven specifico di Cloud Manager. Ad esempio, per installare python:

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

Questa stessa tecnica può essere utilizzata per installare pacchetti specifici per la lingua, ovvero utilizzando `gem` per dumygems o `pip` per pacchetti Python.

>[!NOTE]
>
>L'installazione di un pacchetto di sistema in questo modo **non** lo installa nell'ambiente runtime utilizzato per l'esecuzione di Adobe Experience Manager. Se hai bisogno di un pacchetto di sistema installato nell'ambiente AEM, contatta il tuo Customer Success Engineers (CSE).

## Sviluppo del codice basato sulle best practice {#develop-your-code-based-on-best-practices}

I team Adobe Engineering e Consulting hanno sviluppato un [set completo di best practice per gli sviluppatori di AEM](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/best-practices.html).
