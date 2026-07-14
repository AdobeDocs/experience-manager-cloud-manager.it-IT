---
title: Configurazioni di Dispatcher
description: Scopri come distribuire i file di configurazione di Dispatcher utilizzando Cloud Manager
exl-id: ffc2b60e-bde7-48ca-b268-dea0f8fd4e30
TQID: https://experienceleague.adobe.com/KpGTN-444bigrhLddGnZvxkZsThcVc1B--oEoAKTdos
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: 1692390e24f8fa7d719bd8293a99586ec4ec36d4
workflow-type: tm+mt
source-wordcount: 557
ht-degree: 44%

---

# Configurazioni di Dispatcher {#manage-your-dispatcher-configurations}

Scopri come distribuire i file di configurazione di Dispatcher utilizzando Cloud Manager

## Distribuire le configurazioni di Dispatcher con Cloud Manager {#deploying-dispatcher-configurations}

Cloud Manager può distribuire i file di configurazione del server web e del Dispatcher se sono memorizzati nell’archivio Git con pacchetti di contenuti AEM standard.

Per utilizzare questa funzionalità, la build Maven produce un file .zip contenente almeno due directory: `conf` e `conf.d`. Questo file .zip può essere prodotto utilizzando `maven-assembly-plugin`.

Nei progetti generati da Cloud Manager utilizzando la [procedura guidata per la creazione di progetti](/help/getting-started/using-the-wizard.md) incorporata viene creata automaticamente la struttura di progetto Maven corretta. Questo approccio è consigliato se hai poca esperienza con Adobe Managed Services (AMS).

Quando esegui l’implementazione in un’istanza di Dispatcher, le directory sull’istanza vengono sostituite da quelle presenti nell’archivio Git. Per impostare correttamente le variabili di ambiente appropriate in `/etc/sysconfig/httpd`, collaborare con il team Customer Success in quanto i file di configurazione del server Web e del Dispatcher richiedono spesso dettagli specifici dell&#39;ambiente.

## Configurazione del Dispatcher per la clientela di Managed Service esistente {#steps-for-configuring-dispatcher}

Per completare la configurazione iniziale di Dispatcher, effettuare le seguenti operazioni:

1. Ottieni i file di configurazione di produzione correnti dal team Customer Success.
1. Rimuovi i dati specifici dell’ambiente, ad esempio gli IP del renderer di pubblicazione, e sostituiscili con delle variabili.
1. Definisci le variabili richieste in coppie chiave-valore per ogni Dispatcher di destinazione e aggiungili alla cartella [variabili](https://experienceleague.adobe.com/en/docs/experience-manager-learn/ams/dispatcher/variables) in ogni istanza.
1. Verifica le configurazioni aggiornate nell’ambiente di staging.
1. Una volta testato, richiedi al team Customer Success di implementarlo nell’ambiente di produzione.
1. Invia i file al tuo archivio Git.
1. Distribuisci tramite Cloud Manager.

>[!NOTE]
>
>La migrazione delle configurazioni di Dispatcher e server web all’archivio Git viene eseguita durante l’onboarding di Cloud Manager, ma può essere eseguita anche in un secondo momento.

### Esempio {#example}

La struttura specifica del file e della directory varia in base alle specifiche del progetto, ma questo esempio fornisce una chiara spiegazione di come strutturare il progetto in modo da includere le configurazioni di Apache e Dispatcher.

1. Creare una sottodirectory denominata `dispatcher`.

   Utilizzare un nome qualsiasi, ma il nome della directory creato in questo passaggio deve essere uguale al nome utilizzato nel passaggio 1.

1. Questa sottodirectory contiene un modulo Maven che crea il file .zip di Dispatcher utilizzando `maven-assembly-plugin`. Nella directory `dispatcher`, crea un file `pom.xml` con questo contenuto, modificando il riferimento `parent`, `artifactId` e `name` in base alle esigenze.

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <project xmlns="http://maven.apache.org/POM/4.0.0"
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
       <modelVersion>4.0.0</modelVersion>
       <parent>
           <!-- reference to your parent pom -->
       </parent>
   
       <artifactId>dispatcher</artifactId> <!-- feel free to change this -->
       <packaging>pom</packaging>
       <name>dispatcher</name> <!-- feel free to change this -->
   
       <build>
           <plugins>
               <plugin>
                   <groupId>org.apache.maven.plugins</groupId>
                   <artifactId>maven-assembly-plugin</artifactId>
                   <version>3.1.0</version>
                   <executions>
                       <execution>
                           <phase>package</phase>
                           <goals><goal>single</goal></goals>
                           <configuration>
                               <descriptors>
                                   <descriptor>assembly.xml</descriptor>
                               </descriptors>
                               <appendAssemblyId>false</appendAssemblyId>
                           </configuration>
                       </execution>
                   </executions>
               </plugin>
           </plugins>
       </build>
   </project>
   ```

   * Come nel Passaggio 1, artifactId e name possono essere altri valori. `dispatcher` viene utilizzato qui come esempio.

1. `maven-assembly-plugin` richiede `descriptor` per definire la modalità di creazione del file .zip. Per creare questo descrittore, crea un file nella sottodirectory `dispatcher` denominata `assembly.xml` con il contenuto seguente. Tieni presente che a questo nome di file viene fatto riferimento nella riga 26 nel file `pom.xml` precedente.

   ```xml
   <assembly xmlns="http://maven.apache.org/ASSEMBLY/2.0.0"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://maven.apache.org/ASSEMBLY/2.0.0 http://maven.apache.org/xsd/assembly-2.0.0.xsd">
     <id>distribution</id>
     <formats>
       <format>zip</format>
     </formats>
     <includeBaseDirectory>false</includeBaseDirectory>
     <fileSets>
       <fileSet>
         <directory>${basedir}/src</directory>
         <includes>
           <include>**/*</include>
         </includes>
         <outputDirectory></outputDirectory>
       </fileSet>
     </fileSets>
   </assembly>
   ```

1. Crea una sottodirectory denominata `src` (come indicato nel descrittore dell’assemblaggio precedente nella riga 11) all’interno della sottodirectory di Dispatcher per archiviare le configurazioni effettive di Apache e Dispatcher. All’interno di questa directory `src`, crea directory denominate `conf`, `conf.d`, `conf.dispatcher.d` e `conf.modules.d`.

1. Popola le directory `conf`, `conf.d`, `conf.dispatcher.d` e `conf.modules.d` con i file di configurazione. Per esempio, la configurazione predefinita è costituita da questi file e collegamenti simbolici.

   ```
   dispatcher
   ├── assembly.xml
   ├── pom.xml
   └── src
       ├── conf
       │  ├── httpd.conf
       │  └── magic
       ├── conf.d
       │  ├── README
       │  ├── autoindex.conf
       │  ├── available_vhosts
       │  │  ├── aem_author.vhost
       │  │  ├── aem_flush.vhost
       │  │  ├── aem_health.vhost
       │  │  ├── aem_lc.vhost
       │  │  └── aem_publish.vhost
       │  ├── dispatcher_vhost.conf
       │  ├── enabled_vhosts
       │  │  ├── aem_author.vhost -> ../available_vhosts/aem_author.vhost
       │  │  ├── aem_flush.vhost -> ../available_vhosts/aem_flush.vhost
       │  │  └── aem_publish.vhost -> ../available_vhosts/aem_publish.vhost
       │  ├── rewrites
       │  │  ├── base_rewrite.rules
       │  │  └── xforwarded_forcessl_rewrite.rules
       │  ├── userdir.conf
       │  ├── variables
       │  │  └── ams_default.vars
       │  ├── welcome.conf
       │  └── whitelists
       │      └── 000_base_whitelist.rules
       ├── conf.dispatcher.d
       │  ├── available_farms
       │  │  ├── 000_ams_author_farm.any
       │  │  ├── 001_ams_lc_farm.any
       │  │  └── 999_ams_publish_farm.any
       │  ├── cache
       │  │  ├── ams_author_cache.any
       │  │  ├── ams_author_invalidate_allowed.any
       │  │  ├── ams_publish_cache.any
       │  │  └── ams_publish_invalidate_allowed.any
       │  ├── clientheaders
       │  │  ├── ams_author_clientheaders.any
       │  │  ├── ams_common_clientheaders.any
       │  │  ├── ams_lc_clientheaders.any
       │  │  └── ams_publish_clientheaders.any
       │  ├── dispatcher.any
       │  ├── enabled_farms
       │  │  ├── 000_ams_author_farm.any -> ../available_farms/000_ams_author_farm.any
       │  │  └── 999_ams_publish_farm.any -> ../available_farms/999_ams_publish_farm.any
       │  ├── filters
       │  │  ├── ams_author_filters.any
       │  │  ├── ams_lc_filters.any
       │  │  └── ams_publish_filters.any
       │  ├── renders
       │  │  ├── ams_author_renders.any
       │  │  ├── ams_lc_renders.any
       │  │  └── ams_publish_renders.any
       │  └── vhosts
       │      ├── ams_author_vhosts.any
       │      ├── ams_lc_vhosts.any
       │      └── ams_publish_vhosts.any
       └── conf.modules.d
           ├── 00-base.conf
           ├── 00-dav.conf
           ├── 00-lua.conf
           ├── 00-mpm.conf
           ├── 00-proxy.conf
           ├── 00-systemd.conf
           ├── 01-cgi.conf
           └── 02-dispatcher.conf
   ```

1. Infine, nel file `pom.xml` nella directory principale del progetto, aggiungi un elemento `<module>` per includere il modulo Dispatcher.

   Per esempio, se l’elenco dei moduli esistenti è il seguente:

   ```xml
       <modules>
           <module>core</module>
           <module>ui.apps</module>
           <module>ui.content</module>
       </modules>
   ```

   Modificalo nel modo seguente:

   ```xml
       <modules>
           <module>core</module>
           <module>ui.apps</module>
           <module>ui.content</module>
           <module>dispatcher</module>
       </modules>
   ```

   * Come indicato nel passaggio 1, il valore dell’elemento `<module>` deve corrispondere al nome della directory creata.

1. Per effettuare una prova, esegui `mvn clean package` nella directory principale del progetto. Vedrai righe come questa nell&#39;output.

   ```
   [INFO] --- maven-assembly-plugin:3.1.0:single (default) @ dispatcher ---
   [INFO] Reading assembly descriptor: assembly.xml
   [INFO] Building zip: /Users/me/mycompany/dispatcher/target/dispatcher-1.0-SNAPSHOT.zip
   ```

   Puoi anche decomprimere questo file per visualizzarne il contenuto.

   ```shell
   $ unzip -l dispatcher/target/dispatcher-1.0-SNAPSHOT.zip
   Archive:  dispatcher/target/dispatcher-1.0-SNAPSHOT.zip
     Length      Date    Time    Name
   ---------  ---------- -----   ----
           0  09-12-2018 12:53   conf.modules.d/
           0  10-19-2018 10:38   conf.dispatcher.d/
           0  09-12-2018 12:53   conf.dispatcher.d/available_farms/
           0  09-12-2018 12:53   conf.dispatcher.d/filters/
           0  09-12-2018 12:53   conf.dispatcher.d/renders/
           0  09-12-2018 12:53   conf.dispatcher.d/cache/
           0  09-12-2018 12:53   conf.dispatcher.d/clientheaders/
           0  09-12-2018 12:53   conf.dispatcher.d/enabled_farms/
           0  09-12-2018 12:53   conf.dispatcher.d/vhosts/
           0  09-12-2018 12:53   conf.d/
           0  09-12-2018 12:53   conf.d/rewrites/
           0  09-12-2018 12:53   conf.d/whitelists/
           0  09-12-2018 12:53   conf.d/variables/
           0  11-01-2018 13:53   conf.d/enabled_vhosts/
           0  09-12-2018 12:53   conf.d/available_vhosts/
           0  09-12-2018 12:53   conf/
          88  09-12-2018 12:53   conf.modules.d/00-systemd.conf
        4913  09-12-2018 12:53   conf.dispatcher.d/available_farms/999_ams_publish_farm.any
         152  09-12-2018 12:53   conf.dispatcher.d/renders/ams_lc_renders.any
         490  09-12-2018 12:53   conf.dispatcher.d/clientheaders/ams_common_clientheaders.any
        1727  09-12-2018 12:53   conf.d/rewrites/base_rewrite.rules
          36  09-12-2018 12:53   conf.d/enabled_vhosts/aem_author.vhost
       11753  09-12-2018 12:53   conf/httpd.conf
         957  09-12-2018 12:53   conf.modules.d/00-proxy.conf
         944  09-12-2018 12:53   conf.dispatcher.d/available_farms/001_ams_lc_farm.any
         220  09-12-2018 12:53   conf.dispatcher.d/cache/ams_author_invalidate_allowed.any
          43  09-12-2018 12:53   conf.dispatcher.d/enabled_farms/999_ams_publish_farm.any
         516  09-12-2018 12:53   conf.d/welcome.conf
          37  09-12-2018 12:53   conf.d/enabled_vhosts/aem_publish.vhost
       13077  09-12-2018 12:53   conf/magic
          96  09-12-2018 12:53   conf.modules.d/02-dispatcher.conf
        2601  09-12-2018 12:53   conf.dispatcher.d/available_farms/000_ams_author_farm.any
         837  09-12-2018 12:53   conf.dispatcher.d/cache/ams_author_cache.any
          42  09-12-2018 12:53   conf.dispatcher.d/enabled_farms/000_ams_author_farm.any
        2926  09-12-2018 12:53   conf.d/autoindex.conf
        2555  09-12-2018 12:53   conf.d/available_vhosts/aem_lc.vhost
          41  09-12-2018 12:53   conf.modules.d/00-lua.conf
        2234  09-12-2018 12:53   conf.dispatcher.d/filters/ams_publish_filters.any
         220  09-12-2018 12:53   conf.dispatcher.d/cache/ams_publish_invalidate_allowed.any
         402  09-12-2018 12:53   conf.dispatcher.d/dispatcher.any
         573  09-12-2018 12:53   conf.d/whitelists/000_base_whitelist.rules
         871  09-12-2018 12:53   conf.d/available_vhosts/aem_flush.vhost
         139  09-12-2018 12:53   conf.modules.d/00-dav.conf
         742  09-12-2018 12:53   conf.dispatcher.d/filters/ams_author_filters.any
         557  09-12-2018 12:53   conf.dispatcher.d/cache/ams_publish_cache.any
         105  09-12-2018 12:53   conf.dispatcher.d/vhosts/ams_lc_vhosts.any
         101  09-12-2018 12:53   conf.dispatcher.d/vhosts/ams_publish_vhosts.any
        3582  09-12-2018 12:53   conf.d/dispatcher_vhost.conf
        2529  09-12-2018 12:53   conf.d/available_vhosts/aem_publish.vhost
         742  09-12-2018 12:53   conf.modules.d/00-mpm.conf
          88  09-12-2018 12:53   conf.dispatcher.d/filters/ams_lc_filters.any
         177  09-12-2018 12:53   conf.dispatcher.d/clientheaders/ams_lc_clientheaders.any
         366  09-12-2018 12:53   conf.d/README
        2723  09-12-2018 12:53   conf.d/available_vhosts/aem_author.vhost
        3739  09-12-2018 12:53   conf.modules.d/00-base.conf
         138  09-12-2018 12:53   conf.dispatcher.d/renders/ams_author_renders.any
          44  09-12-2018 12:53   conf.dispatcher.d/clientheaders/ams_publish_clientheaders.any
         112  09-12-2018 12:53   conf.dispatcher.d/vhosts/ams_author_vhosts.any
         580  09-12-2018 12:53   conf.d/variables/ams_default.vars
          35  09-12-2018 12:53   conf.d/enabled_vhosts/aem_flush.vhost
        1252  09-12-2018 12:53   conf.d/userdir.conf
         451  09-12-2018 12:53   conf.modules.d/01-cgi.conf
         321  09-12-2018 12:53   conf.dispatcher.d/renders/ams_publish_renders.any
         170  09-12-2018 12:53   conf.dispatcher.d/clientheaders/ams_author_clientheaders.any
         220  09-12-2018 12:53   conf.d/rewrites/xforwarded_forcessl_rewrite.rules
        1753  09-12-2018 12:53   conf.d/available_vhosts/aem_health.vhost
   ---------                     -------
       69017                     66 files
   ```
