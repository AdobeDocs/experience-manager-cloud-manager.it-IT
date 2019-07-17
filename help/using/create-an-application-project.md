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
source-git-commit: 7cfa0cf66efd5891263bfcc83a5149daec5c8b67

---


# Create an AEM Application Project {#create-an-aem-application-project}

## Using Wizard to Create an AEM Application Project {#using-wizard-to-create-an-aem-application-project}

Quando i clienti sono collegati a Cloud Manager, vengono forniti con un archivio git vuoto. I clienti correnti di Servizi gestiti Adobe (AMS) (o clienti AEM interni che eseguono la migrazione ad AMS) in genere dispongono già del codice del progetto in git (o di un altro sistema di controllo delle versioni) e importeranno il proprio progetto nell'archivio git di Experience Manager. I nuovi clienti, tuttavia, non hanno progetti esistenti.

Per aiutare i nuovi clienti a iniziare, Cloud Manger è ora in grado di creare un progetto AEM minimo come punto di partenza. This process is based on the [**AEM Project Archetype**](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-10-08T12:52:50.071-0400

2018.8.0: Added this new section

 -->

Segui i passaggi seguenti per creare un progetto applicazione AEM in Cloud Manager:

1. Once you log in to Cloud Manager and the basic program setup is complete, a special call to action card will be shown on the **Overview** screen, if the repository is empty.

   ![](assets/image2018-10-3_14-29-44.png)

1. Click **Create** to navigate to the **Pipeline Setup** screen.

   ![](assets/image2018-10-3_14-30-22.png)

1. Click **Create to** open a dialog box, which allows the user to provide the parameters required by the AEM Project Archetype. Nel modulo predefinito, la finestra di dialogo richiede due valori:

   * **Titolo** : per impostazione predefinita, viene impostato sul nome *del programma*

   * **Nuovo nome** ramo: per impostazione predefinita, questo *è*
   ![](assets/screen_shot_2018-10-08at55825am.png)

   La finestra di dialogo presenta un cassetto che può essere aperto facendo clic sulla maniglia verso il fondo della finestra di dialogo. Nel modulo espanso, la finestra di dialogo mostra tutti i parametri di configurazione per l'Archetype. Many of these parameters have default values which are generated based on the **Title**.

   ![](assets/screen_shot_2018-10-08at60032am.png)

   >[!NOTE]
   >
   >For example, if the **Title** is ***We.Finance***, the Base Maven Artifact Id parameter is generated as ***com.wefinance***. Se necessario, potete modificarli.
   >
   >
   >For example, you can change from the generated ***value com.wefinance*** to ***net.wefinance***.

1. Click **Create** in the preceding step to create the starter project by using the archetype and commit to the named git branch. Una volta effettuata questa operazione, potete configurare la pipeline.

## Setting up your Project {#setting-up-your-project}

### Modifying Project Setup Details {#modifying-project-setup-details}

Per creare e distribuire correttamente con Cloud Manager, i progetti AEM esistenti devono rispettare alcune regole di base:

* I progetti devono essere creati utilizzando Apache Maven.
* There must be a *pom.xml* file in the root of the Git repository. This *pom.xml* file can refer to as many submodules (which in turn may have other submodules, etc.) se necessario.

* You can add references to additional Maven artifact repositories in your *pom.xml* files. Tuttavia, l'accesso a archivi artefatti protetti da password o protetti da rete non è supportato.
* Deployable content packages are discovered by scanning for content package *zip* files which are contained in a directory named *target*. Un numero qualsiasi di sottomoduli potrebbe produrre pacchetti di contenuto.

* Deployable Dispatcher artifacts are discovered by scanning for *zip* files (again, contained in a directory named *target*) which have directories named *conf* and *conf.d*.

* Se sono presenti più pacchetti di contenuto, l'ordine delle distribuzioni del pacchetto non è garantito. Qualora sia necessario un ordine specifico, per definire l'ordine sarà possibile utilizzare dipendenze del pacchetto di contenuto.

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-10-08T09:20:10.106-0400

2018.8.0: added existing in the opening sentence

 -->

## Build Environment Details {#build-environment-details}

Cloud Manager builds and tests your code using a specialized build runtime **Environment**. Questo ambiente dispone dei seguenti attributi:

* L'ambiente di generazione è basato su Linux.
* Apache Maven 3.6.0 è installato.
* La versione Java installata è Oracle JDK 8 u 202.
* Sono installati alcuni pacchetti di sistema aggiuntivi:

   * bzip2
   * decomprimere
   * libpng
   * imagemagick
   * graphicsmagick
   * Se hai bisogno di altri pacchetti, dovrai richiederli tramite i tuoi Customer Success Engineers (CSE).

* Maven is always run with the command: *mvn --batch-mode clean org.jacoco:jacoco-maven-plugin:prepare-agent package*
* Maven is configured at a system level with a settings.xml file which automatically includes the public Adobe **Artifact** repository. (Refer to [Adobe Public Maven Repository](https://repo.adobe.com/) for more details).

## Activating Maven Profiles in Cloud Manager {#activating-maven-profiles-in-cloud-manager}

In alcuni casi limitati, potrebbe essere necessario variare leggermente il processo di creazione quando viene eseguito in Cloud Manager e non quando viene eseguito sulle workstation per sviluppatori. For these cases, [Maven Profiles](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) can be used to define how the build should be different in different environments, including Cloud Manager.

Activation of a Maven Profile inside the Cloud Manager build environment should be done by looking for the presence of an environment variable named `CM_BUILD`. Questa variabile viene sempre impostata all'interno dell'ambiente di generazione di Cloud Manager. In modo analogo, un profilo destinato alla sola uso all'esterno dell'ambiente di creazione di Cloud Manager deve essere eseguito cercando l'ordine di questa variabile.

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
>To test this profile on a developer workstation, you can either enable it on the command line (with `-PcmBuild`) or in your Integrated Development Environment (IDE).

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

## Develop your Code Based on Best Practices {#develop-your-code-based-on-best-practices}

Adobe Engineering and Consulting teams have developed a [comprehensive set of best practices for AEM developers](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/best-practices.html).
