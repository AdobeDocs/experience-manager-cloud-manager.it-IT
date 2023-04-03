---
title: Regole per la qualità del codice personalizzato
description: Scopri i dettagli sulle regole della qualità del codice personalizzato eseguite da Cloud Manager come parte del test della qualità del codice, in base alle best practice di AEM Engineering.
exl-id: 7d118225-5826-434e-8869-01ee186e0754
source-git-commit: ef87e13eb81faf5605cdd16c6fd46d5f7b3233a9
workflow-type: ht
source-wordcount: '3531'
ht-degree: 100%

---


# Regole per la qualità del codice personalizzato {#custom-code-quality-rules}

Scopri i dettagli sulle regole della qualità del codice personalizzato eseguite da Cloud Manager come parte del [test della qualità del codice](/help/using/code-quality-testing.md), in base alle best practice di AEM Engineering.

>[!NOTE]
>
>I campioni di codice qui forniti hanno valore puramente illustrativo. Consulta la [Documentazione sui concetti di SonarQube](https://docs.sonarqube.org/latest/) per scoprire di più sui concetti e sulle regole di qualità.

## Regole di SonarQube {#sonarqube-rules}

Nella sezione seguente sono descritte le regole di SonarQube eseguite da Cloud Manager.

### Non utilizzare funzioni potenzialmente pericolose {#do-not-use-potentially-dangerous-functions}

* **Chiave**: CQRules:CWE-676
* **Tipo**: vulnerabilità
* **Gravità**: importante
* **Da**: versione 2018.4.0

I metodi `Thread.stop()` e `Thread.interrupt()` possono generare problemi difficili da riprodurre e, in alcuni casi, vulnerabilità di sicurezza. Il loro utilizzo deve essere controllato e convalidato. In generale, il passaggio di messaggi è un modo più sicuro per raggiungere obiettivi simili.

#### Codice non conforme {#non-compliant-code}

```java
public class DontDoThis implements Runnable {
  private Thread thread;
 
  public void start() {
    thread = new Thread(this);
    thread.start();
  }
 
  public void stop() {
    thread.stop();  // UNSAFE!
  }
 
  public void run() {
    while (true) {
        somethingWhichTakesAWhileToDo();
    }
  }
}
```

#### Codice conforme {#compliant-code}

```java
public class DoThis implements Runnable {
  private Thread thread;
  private boolean keepGoing = true;
 
  public void start() {
    thread = new Thread(this);
    thread.start();
  }
 
  public void stop() {
    keepGoing = false;
  }
 
  public void run() {
    while (this.keepGoing) {
        somethingWhichTakesAWhileToDo();
    }
  }
}
```

### Non utilizzare stringhe di formato che possono essere controllate esternamente {#do-not-use-format-strings-which-may-be-externally-controlled}

* **Chiave**: CQRules:CWE-134
* **Tipo**: vulnerabilità
* **Gravità**: importante
* **Da**: versione 2018.4.0

L’utilizzo di una stringa di formato da un’origine esterna (come un parametro di richiesta o contenuti generati dall’utente) può esporre un’applicazione al rifiuto di attacchi del servizio. In alcune circostanze una stringa di formato può essere controllata esternamente, ma è consentita solo da fonti attendibili.

#### Codice non conforme {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text"));
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### Le richieste HTTP devono sempre avere i timeout del socket e della connessione {#http-requests-should-always-have-socket-and-connect-timeouts}

* **Chiave**: CQRules:ConnectionTimeoutMechanism
* **Tipo**: bug
* **Gravità**: critico
* **Da**: versione 2018.6.0

Durante l’esecuzione delle richieste HTTP da un’applicazione AEM, è fondamentale assicurarsi che siano configurati i timeout appropriati al fine di evitare un inutile consumo di thread. Sfortunatamente, il comportamento predefinito di entrambi i client HTTP predefiniti di Java™, `java.net.HttpUrlConnection`, e il client Apache HTTP Components comunemente utilizzato non si interrompe mai, pertanto i timeout devono essere impostati in modo esplicito. Come best practice, questi timeout non devono superare i 60 secondi.

#### Codice non conforme {#non-compliant-code-2}

```java
@Reference
private HttpClientBuilderFactory httpClientBuilderFactory;
 
public void dontDoThis() {
  HttpClientBuilder builder = httpClientBuilderFactory.newBuilder();
  HttpClient httpClient = builder.build();

  // do something with the client
}

public void dontDoThisEither() {
  URL url = new URL("http://www.google.com");
  URLConnection urlConnection = url.openConnection();
 
  BufferedReader in = new BufferedReader(new InputStreamReader(
    urlConnection.getInputStream()));
 
  String inputLine;
  while ((inputLine = in.readLine()) != null) {
    logger.info(inputLine);
  }
 
  in.close();
}
```

#### Codice conforme {#compliant-code-1}

```java
@Reference
private HttpClientBuilderFactory httpClientBuilderFactory;
 
public void doThis() {
  HttpClientBuilder builder = httpClientBuilderFactory.newBuilder();
  RequestConfig requestConfig = RequestConfig.custom()
    .setConnectTimeout(5000)
    .setSocketTimeout(5000)
    .build();
  builder.setDefaultRequestConfig(requestConfig);
 
  HttpClient httpClient = builder.build();
   
  // do something with the client
}

public void orDoThis() {
  URL url = new URL("http://www.google.com");
  URLConnection urlConnection = url.openConnection();
  urlConnection.setConnectTimeout(5000);
  urlConnection.setReadTimeout(5000);
 
  BufferedReader in = new BufferedReader(new InputStreamReader(
    urlConnection.getInputStream()));
 
  String inputLine;
  while ((inputLine = in.readLine()) != null) {
    logger.info(inputLine);
  }
 
  in.close();
}
```

### Chiudere sempre gli oggetti ResourceResolver {#resourceresolver-objects-should-always-be-closed}

* **Chiave**: CQRules:CQBP-72
* **Tipo**: code smell
* **Gravità**: importante
* **Da**: versione 2018.4.0

Gli oggetti `ResourceResolver` ottenuti da `ResourceResolverFactory` consumano risorse di sistema. Sebbene esistano misure per recuperare tali risorse quando un oggetto `ResourceResolver` non è più in uso, è più efficiente chiudere in modo esplicito qualsiasi oggetto `ResourceResolver` aperto con una chiamata al metodo `close()`.

Un equivoco comune è che gli oggetti `ResourceResolver` creati utilizzando una sessione JCR esistente non devono essere chiusi in modo esplicito, altrimenti la sessione JCR sottostante verrà chiusa. Questo non succede. Indipendentemente da come si apre un oggetto `ResourceResolver`, quando non viene più utilizzato deve essere chiuso. Poiché `ResourceResolver` implementa l’interfaccia `Closeable`, è possibile utilizzare anche la sintassi `try-with-resources` anziché richiamare esplicitamente `close()`.

#### Codice non conforme {#non-compliant-code-4}

```java
public void dontDoThis(Session session) throws Exception {
  ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
  // do some stuff with the resolver
}
```

#### Codice conforme {#compliant-code-2}

```java
public void doThis(Session session) throws Exception {
  ResourceResolver resolver = null;
  try {
    resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
    // do something with the resolver
  } finally {
    if (resolver != null) {
      resolver.close();
    }
  }
}

public void orDoThis(Session session) throws Exception {
  try (ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object) session))){
    // do something with the resolver
  }
}
```

### Non utilizzare i percorsi dei servlet Sling per registrare i servlet {#do-not-use-sling-servlet-paths-to-register-servlets}

* **Chiave**: CQRules:CQBP-75
* **Tipo**: code smell
* **Gravità**: importante
* **Da**: versione 2018.4.0

Come descritto nella [documentazione di Sling](https://sling.apache.org/documentation/the-sling-engine/servlets.html), si sconsiglia di associare i servlet ai percorsi. I servlet associati ai percorsi non possono utilizzare controlli dell’accesso JCR standard e, di conseguenza, richiedono un’ulteriore misura di sicurezza. Anziché utilizzare i servlet associati ai percorsi, si consiglia di creare nodi nell’archivio e di registrare i servlet in base al tipo di risorsa.

#### Codice non conforme {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### Le eccezioni rilevate devono essere registrate o generate, non entrambe {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

* **Key**: CQRules:CQBP-44---CatchAndEitherLogOrThrow
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2018.4.0

In generale, un’eccezione deve essere registrata una sola volta. Registrare le eccezioni più volte può causare confusione sul numero di volte che un’eccezione si è verificata. Il modello più comune che porta a questo problema è la registrazione e la generazione di un’eccezione rilevata.

#### Codice non conforme {#non-compliant-code-6}

```java
public void dontDoThis() throws Exception {
  try {
    someOperation();
  } catch (Exception e) {
    logger.error("something went wrong", e);
    throw e;
  }
}
```

#### Codice conforme {#compliant-code-3}

```java
public void doThis() {
  try {
    someOperation();
  } catch (Exception e) {
    logger.error("something went wrong", e);
  }
}

public void orDoThis() throws MyCustomException {
  try {
    someOperation();
  } catch (Exception e) {
    throw new MyCustomException(e);
  }
}
```

### Evitare le istruzioni di registro immediatamente seguite dalle istruzioni di generazione {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

* **Chiave**: CQRules:CQBP-44---ConsecutivelyLogAndThrow
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2018.4.0

Un altro modello comune da evitare è registrare un messaggio e generare immediatamente un’eccezione. Questo indica in genere che il messaggio di eccezione viene duplicato nei file di log.

#### Codice non conforme {#non-compliant-code-7}

```java
public void dontDoThis() throws Exception {
  logger.error("something went wrong");
  throw new RuntimeException("something went wrong");
}
```

#### Codice conforme {#compliant-code-4}

```java
public void doThis() throws Exception {
  throw new RuntimeException("something went wrong");
}
```

### Evitare la registrazione a livello INFO durante la gestione delle richieste GET o HEAD {#avoid-logging-at-info-when-handling-get-or-head-requests}

* **Chiave**: CQRules:CQBP-44---LogInfoInGetOrHeadRequests
* **Tipo**: code smell
* **Gravità**: minore

In generale, per demarcare le azioni importanti si utilizza il livello registro INFO e, per impostazione predefinita, AEM è configurato per registrare al livello INFO o superiore. I metodi GET e HEAD devono essere sempre di sola lettura e non costituiscono pertanto azioni importanti. È probabile che la registrazione a livello INFO in risposta alle richieste GET o HEAD generi un notevole disturbo nel registro, rendendo così più difficile identificare le informazioni utili nei file di log. La registrazione durante la gestione delle richieste GET o HEAD deve essere a livello WARN o ERROR quando si è verificato un errore o a livello DEBUG o TRACE se è utilie fornire informazioni più approfondite sulla risoluzione dei problemi.

>[!NOTE]
>
>Questo non si applica alla registrazione del tipo access.log per ogni richiesta.

#### Codice non conforme {#non-compliant-code-8}

```java
public void doGet() throws Exception {
  logger.info("handling a request from the user");
}
```

#### Codice conforme {#compliant-code-5}

```java
public void doGet() throws Exception {
  logger.debug("handling a request from the user.");
}
```

### Non utilizzare Exception.getMessage() come primo parametro di un’istruzione di registrazione {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

* **Chiave**: CQRules:CQBP-44---ExceptionGetMessageIsFirstLogParam
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2018.4.0

Come best practice, i messaggi del registro devono fornire informazioni contestuali sulla posizione in cui è stata generata un’eccezione nell’applicazione. Mentre il contesto può essere determinato anche tramite l’utilizzo di tracce dello stack, in generale il messaggio di registro sarà più facile da leggere e comprendere. Di conseguenza, quando si registra un’eccezione, non è consigliabile utilizzare il messaggio di eccezione come messaggio di registro. Il messaggio di eccezione contiene la descrizione del problema che si è verificato, mentre il messaggio di registro deve essere utilizzato per comunicare al lettore del registro cosa stava facendo l’applicazione quando si è verificata l’eccezione. Il messaggio di eccezione è comunque registrato. Specificando il messaggio, i registri saranno più facili da comprendere.

#### Codice non conforme {#non-compliant-code-9}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error(e.getMessage(), e);
  }
}
```

#### Codice conforme {#compliant-code-6}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### La registrazione nei blocchi catch deve essere a livello WARN o ERROR {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}

* **Chiave**: CQRules:CQBP-44---WrongLogLevelInCatchBlock
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2018.4.0

Come suggerisce il nome, le eccezioni Java™ dovrebbero sempre essere utilizzate in circostanze eccezionali. Di conseguenza, quando viene rilevata un’eccezione, è importante garantire che i messaggi del registro vengano registrati al livello appropriato: WARN o ERROR. In questo modo i messaggi verranno visualizzati correttamente nei registri.

#### Codice non conforme {#non-compliant-code-10}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.debug(e.getMessage(), e);
  }
}
```

#### Codice conforme {#compliant-code-7}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Non stampare tracce dello stack sulla Console {#do-not-print-stack-traces-to-the-console}

* **Chiave**: CQRules:CQBP-44---ExceptionPrintStackTrace
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2018.4.0

Il contesto è fondamentale per comprendere i messaggi del registro. L’utilizzo di `Exception.printStackTrace()` fa sì che solo la traccia dello stack venga trasmessa al flusso di errore standard, perdendo così tutto il contesto. Inoltre, in un&#39;applicazione multi-thread come AEM se vengono stampate più eccezioni utilizzando questo metodo in parallelo, le rispettive tracce di stack possono sovrapporsi e creare confusione. Le eccezioni devono essere registrate solo tramite il framework di registrazione.

#### Codice non conforme {#non-compliant-code-11}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    e.printStackTrace();
  }
}
```

#### Codice conforme {#compliant-code-8}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Non inviare ai flussi di output standard o errore standard {#do-not-output-to-standard-output-or-standard-error}

* **Chiave**: CQRules:CQBP-44—LogLevelConsolePrinters
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2018.4.0

La registrazione ad AEM deve sempre essere effettuata tramite il framework di registrazione SLF4J. L’output diretto nei flussi di output standard o errore standard perde le informazioni strutturali e contestuali fornite dal framework di registrazione e può, a volte, causare problemi di prestazioni.

#### Codice non conforme {#non-compliant-code-12}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    System.err.println("Unable to do something");
  }
}
```

#### Codice conforme {#compliant-code-9}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Evitare percorsi hardcoded /apps e /libs {#avoid-hardcoded-apps-and-libs-paths}

* **Chiave**: CQRules:CQBP-71
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2018.4.0

In generale, i percorsi che iniziano con `/libs` e `/apps` non devono essere codificati in quanto i percorsi a cui si riferiscono sono generalmente memorizzati come percorsi relativi al percorso di ricerca Sling (impostato su `/libs,/apps` per impostazione predefinita). L&#39;utilizzo del percorso assoluto può presentare difetti minimi che appariranno solo successivamente nel ciclo di vita del progetto.

#### Codice non conforme {#non-compliant-code-13}

```java
public boolean dontDoThis(Resource resource) {
  return resource.isResourceType("/libs/foundation/components/text");
}
```

#### Codice conforme {#compliant-code-10}

```java
public void doThis(Resource resource) {
  return resource.isResourceType("foundation/components/text");
}
```

### Lo Sling Scheduler non deve essere utilizzato {#sonarqube-sling-scheduler}

* **Chiave**: CQRules:AMSCORE-554
* **Tipo**: code smell/compatibilità con Cloud Service
* **Gravità**: minore
* **Da**: versione 2020.5.0

Non utilizzare lo Sling Scheduler per le attività che richiedono un’esecuzione garantita. I processi pianificati Sling garantiscono l’esecuzione e sono più adatti per gli ambienti cluster che per quelli non cluster.

Fai riferimento a [Documentazione sull’evento Sling di Apache e sulla gestione dei processi](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html) per ulteriori informazioni sulla gestione dei processi Sling in ambienti cluster.

### Le API obsolete di AEM non devono essere utilizzate {#sonarqube-aem-deprecated}

* **Chiave**: AMSCORE-553
* **Tipo**: code smell/compatibilità con Cloud Service
* **Gravità**: minore
* **Da**: versione 2020.5.0

La superficie dell’API AEM è soggetta a revisione costante per identificare le API di cui si sconsiglia l’utilizzo e pertanto considerate obsolete.

Spesso, queste API sono indicate come obsolete meditante l’annotazione Java™ standard *@Deprecated* e quindi individuate da `squid:CallToDeprecatedMethod`.

Tuttavia, in alcuni casi un’API può essere obsoleta nel contesto di AEM, ma potrebbe non esserlo in altri contesti. Questa regola identifica questa seconda classe.

## Regole per i contenuti OakPAL {#oakpal-rules}

Nella sezione seguente sono descritti i controlli OakPAL eseguiti da Cloud Manager.

>[!NOTE]
>
>OakPAL è un framework che convalida i pacchetti di contenuti con un archivio Oak autonomo. È stato sviluppato da un partner di AEM ed è vincitore del premio AEM Rockstar North America 2019.

### Le API di prodotto con notazione @ProviderType non devono essere implementate o estese dai clienti {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

* **Chiave**: CQBP-84
* **Tipo**: bug
* **Gravità**: critico
* **Da**: versione 2018.7.0

L’API AEM contiene interfacce e classi Java™ che devono essere utilizzate solo con il codice personalizzato, ma che non devono essere implementate. Ad esempio, l’interfaccia `com.day.cq.wcm.api.Page` è implementata solo da AEM.

Quando a queste interfacce vengono aggiunti nuovi metodi, essi non influiscono sul codice esistente che utilizza tali interfacce e, di conseguenza, l’aggiunta di nuovi metodi ad esse è considerata retrocompatibile. Tuttavia, se il codice personalizzato implementa una di queste interfacce, genera per il cliente un rischio di retrocompatibilità con le versioni precedenti.

Le interfacce e le classi che devono essere implementate solo da AEM sono annotate con `org.osgi.annotation.versioning.ProviderType` o, in alcuni casi, con l’annotazione precedente simile `aQute.bnd.annotation.ProviderType`. Questa regola identifica i casi in cui tale interfaccia viene implementata o in cui una classe viene estesa dal codice personalizzato.

#### Codice non conforme {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### I pacchetti cliente non devono creare o modificare nodi in /libs {#oakpal-customer-package}

* **Chiave**: BannedPath
* **Tipo**: bug
* **Gravità**: bloccante
* **Da**: versione 2019.6.0

È una best practice consolidata da tempo che la struttura del contenuto `/libs` nell’archivio dei contenuti AEM debba essere considerata di sola lettura dai clienti. Modificare nodi e proprietà in `/libs` crea rischi significativi per gli aggiornamenti principali e secondari. Le modifiche apportate a `/libs` devono essere effettuate esclusivamente da Adobe attraverso i canali ufficiali.

### I pacchetti non devono contenere duplicati delle configurazioni OSGi {#oakpal-package-osgi}

* **Chiave**: DuplicateOsgiConfigurations
* **Tipo**: bug
* **Gravità**: importante
* **Da**: versione 2019.6.0

Un problema comune che si verifica in progetti complessi è che lo stesso componente OSGi viene configurato più volte. Questo crea ambiguità riguardo alla configurazione da utilizzare. Questa regola è “sensibile alla modalità di esecuzione”, in quanto individua solo i problemi in cui lo stesso componente è configurato più volte nella stessa modalità di esecuzione o nella stessa combinazione di modalità di esecuzione.

#### Codice non conforme {#non-compliant-code-osgi}

```text
+ apps
  + projectA
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
  + projectB
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

#### Codice conforme {#compliant-code-osgi}

```text
+ apps
  + shared-config
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

### Le cartelle di configurazione e installazione devono contenere solo nodi OSGi {#oakpal-config-install}

* **Chiave**: ConfigAndInstallShouldOnlyContainOsgiNodes
* **Tipo**: bug
* **Gravità**: importante
* **Da**: versione 2019.6.0

Per motivi di sicurezza, i percorsi contenenti `/config/` e `/install/` sono leggibili solo dagli utenti amministratori in AEM e devono essere utilizzati solo per la configurazione OSGi e i bundle OSGi. Posizionare altri tipi di contenuto in percorsi che contengono questi segmenti determina un comportamento dell’applicazione che comporta un cambio accidentale tra utenti amministratori e non amministratori.

Un problema comune è l’utilizzo di nodi denominati `config` nelle finestre di dialogo dei componenti o quando si specifica la configurazione dell’editor Rich Text per la modifica in linea. Per risolvere questo problema, il nodo che causa la violazione deve essere rinominato con un nome conforme. Per la configurazione del rich text editor, specifica la nuova posizione con la proprietà `configPath` nel nodo `cq:inplaceEditing`.

#### Codice non conforme {#non-compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    + config [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

#### Codice conforme {#compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    ./configPath = inplaceEditingConfig (String)
    + inplaceEditingConfig [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

### I pacchetti non devono sovrapporsi {#oakpal-no-overlap}

* **Chiave**: PackageOverlaps
* **Tipo**: bug
* **Gravità**: importante
* **Da**: versione 2019.6.0

Simile alla regola [I pacchetti non devono contenere configurazioni OSGi duplicate](#oakpal-package-osgi), questo è di un problema comune nei progetti complessi in cui diversi pacchetti di contenuto scrivono nello stesso percorso di nodo. Benché sia possibile utilizzare le dipendenze tra pacchetti di contenuti per garantire risultati coerenti, è meglio evitare del tutto le sovrapposizioni.

### La modalità di authoring predefinita non deve essere Interfaccia classica {#oakpal-default-authoring}

* **Chiave**: ClassicUIAuthoringMode
* **Tipo**: code smell/compatibilità con Cloud Service
* **Gravità**: minore
* **Da**: versione 2020.5.0

La configurazione OSGi `com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl` definisce la modalità di authoring predefinita in AEM. Poiché l’interfaccia classica è diventata obsoleta a partire dalla versione 6.4 di AEM, ora viene segnalato un problema se la modalità di authoring predefinita è configurata sull’interfaccia classica.

### I componenti con finestre di dialogo devono avere finestre di dialogo dell’interfaccia Touch {#oakpal-components-dialogs}

* **Chiave**: ComponentWithOnlyClassicUIDialog
* **Tipo**: code smell/compatibilità con Cloud Service
* **Gravità**: minore
* **Da**: versione 2020.5.0

I componenti AEM che hanno una finestra di dialogo per l’interfaccia classica devono avere sempre una finestra di dialogo corrispondente per interfaccia touch, in modo da fornire un’esperienza di authoring ottimale e per compatibilità con il modello di distribuzione di Cloud Service, in cui l’interfaccia classica non è supportata. Questa regola verifica i seguenti scenari:

* Un componente con una finestra di dialogo dell’interfaccia classica (ovvero un nodo figlio `dialog`) deve avere una finestra di dialogo corrispondente dell’interfaccia Touch (ovvero un nodo figlio `cq:dialog`).
* Un componente con una finestra di dialogo di progettazione Interfaccia classica (ossia un nodo `design_dialog`) deve avere una finestra di dialogo di progettazione Interfaccia Touch corrispondente (ossia un nodo figlio `cq:design_dialog`).
* Un componente che ha sia una finestra di dialogo che una finestra di dialogo di progettazione per l’interfaccia classica deve avere anche la finestra di dialogo e la finestra di dialogo di progettazione corripondenti per l’interfaccia touch.

La documentazione sugli strumenti di modernizzazione AEM fornisce dettagli e strumenti per la conversione dei componenti dall’interfaccia classica all’interfaccia touch. Per ulteriori dettagli, consulta la [documentazione sugli strumenti di modernizzazione AEM](https://opensource.adobe.com/aem-modernize-tools/).

### I pacchetti non devono contenere un mix di contenuti mutabili e immutabili {#oakpal-packages-immutable}

* **Chiave**: ImmutableMutableMixedPackage
* **Tipo**: code smell/compatibilità con Cloud Service
* **Gravità**: minore
* **Da**: versione 2020.5.0

Per la compatibilità con il modello di distribuzione di Cloud Service, i singoli pacchetti di contenuti devono contenere contenuti per aree non modificabili dell’archivio (ovvero `/apps` e `/libs`) o per l’area modificabile (ovvero tutto ciò che non si trova in `/apps` o `/libs`), ma non per entrambi i tipi. Ad esempio, un pacchetto che include `/apps/myco/components/text and /etc/clientlibs/myco` non è compatibile con Cloud Service e causa la segnalazione di un problema.

Per ulteriori dettagli, consulta la [documentazione sulla struttura dei progetti AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html?lang=it).

>[!NOTE]
>
>La regola [I pacchetti cliente non devono creare o modificare nodi in /libs](#oakpal-customer-package) è sempre applicabile.

### Gli agenti di replica inversa non devono essere utilizzati {#oakpal-reverse-replication}

* **Chiave**: ReverseReplication
* **Tipo**: code smell/compatibilità con Cloud Service
* **Gravità**: minore
* **Da**: versione 2020.5.0

La replica inversa non è supportata nelle implementazioni di Cloud Service, come descritto in [Note sulla versione: rimozione degli agenti di replica.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/aem-cloud-changes.html?lang=it#replication-agents)

I clienti che utilizzano la replica inversa devono contattare Adobe per soluzioni alternative.

### Le risorse da librerie client abilitate per i proxy devono essere in una cartella “resources” {#oakpal-resources-proxy}

* **Chiave**: ClientlibProxyResource
* **Tipo**: bug
* **Gravità**: minore
* **Da**: versione 2021.2.0

Le librerie client di AEM possono contenere risorse statiche come immagini e font. Come descritto nella documentazione sull’[utilizzo di librerie lato client](https://experienceleague.adobe.com/docs/experience-manager-65/developing/introduction/clientlibs.html?lang=it#using-preprocessors), quando si utilizzano librerie client con proxy, le risorse statiche devono essere all’interno di una cartella figlio denominata `resources` affinché sia possibile farvi riferimento correttamente nelle istanze di pubblicazione.

#### Codice non conforme {#non-compliant-proxy-enabled}

```text
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + images
        + myimage.jpg
```

#### Codice conforme {#compliant-proxy-enabled}

```text
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + resources
        + myimage.jpg
```

### Utilizzo dei processi di flusso di lavoro non compatibili con Cloud Service {#oakpal-usage-cloud-service}

* **Chiave**: CloudServiceIncompatibleWorkflowProcess
* **Tipo**: code smell
* **Gravità**: bloccante
* **Da**: versione 2021.2.0

Con il passaggio ai micro-servizi Asset per l’elaborazione delle risorse in AEM Cloud Service, diversi processi di flusso di lavoro utilizzati nelle versioni locali e AMS di AEM non sono più supportati o non necessari.

Lo strumento di migrazione nell’[archivio GitHub di AEM Assets as a Cloud Service](https://github.com/adobe/aem-cloud-migration) può essere utilizzato per aggiornare i modelli di flusso di lavoro durante la migrazione ad AEM as a Cloud Service.

### L’utilizzo di modelli modificabili è preferibile rispetto a quello dei modelli statici {#oakpal-static-template}

* **Chiave**: StaticTemplateUsage
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2021.2.0

Anche se l’utilizzo di modelli statici è sempre stato comune nei progetti AEM, i modelli modificabili sono altamente consigliati, in quanto offrono la massima flessibilità e supportano funzioni aggiuntive non presenti nei modelli statici. Per ulteriori informazioni consulta la sezione [Modelli di pagina: documentazione modificabile.](https://experienceleague.adobe.com/docs/experience-manager-65/developing/platform/templates/page-templates-editable.html?lang=it)

La migrazione da modelli statici a modificabili può essere in gran parte automatizzata utilizzando gli [Strumenti di modernizzazione AEM.](https://opensource.adobe.com/aem-modernize-tools/)

### L’utilizzo dei componenti Foundation legacy è sconsigliato {#oakpal-usage-legacy}

* **Chiave**: LegacyFoundationComponentUsage
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2021.2.0

I componenti di base precedenti (ad esempio, i componenti in `/libs/foundation`) non sono stati approvati per diverse versioni AEM a favore dei [Componenti core.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=it) L’utilizzo dei componenti di base precedenti come base per i componenti personalizzati, tramite sovrapposizione o ereditarietà, è sconsigliato e deve essere convertito nel componente di base corrispondente.

Questa conversione può essere facilitata dagli [Strumenti di modernizzazione AEM.](https://opensource.adobe.com/aem-modernize-tools/)

### Utilizza solo i nomi e l’ordine delle modalità di esecuzione supportati. {#oakpal-supported-runmodes}

* **Chiave**: SupportedRunmode
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2021.2.0

AEM Cloud Service applica un criterio di denominazione rigoroso per i nomi delle modalità di esecuzione e un ordinamento rigoroso per tali modalità di esecuzione. L’elenco delle modalità di esecuzione supportate è disponibile nella [documentazione sulla distribuzione in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html?lang=it#runmodes) e qualsiasi deviazione da queste sarà identificata come un problema.

### I nodi di definizione dell’indice di ricerca personalizzato devono essere nodi figlio diretti di /oak:index {#oakpal-custom-search}

* **Chiave**: OakIndexLocation
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2021.2.0

AEM Cloud Service richiede che le definizioni dell’indice di ricerca personalizzato (ad esempio, nodi di tipo `oak:QueryIndexDefinition`) siano nodi secondari di `/oak:index`. Gli indici in altre posizioni devono essere spostati per essere compatibili con AEM Cloud Service. Ulteriori informazioni sugli indici di ricerca sono disponibili nella sezione [Documentazione sulla ricerca e l’indicizzazione dei contenuti.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=it)

### I nodi di definizione dell’indice di ricerca personalizzato devono avere una compatVersion di 2 {#oakpal-custom-search-compatVersion}

* **Chiave**: IndexCompatVersion
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2021.2.0

AEM Cloud Service richiede che le definizioni di indici di ricerca personalizzati (ovvero nodi di tipo `oak:QueryIndexDefinition`) abbiano la proprietà `compatVersion` impostata su `2`. Qualsiasi altro valore non è supportato da AEM Cloud Service. Ulteriori informazioni sugli indici di ricerca sono disponibili nella sezione [Documentazione sulla ricerca e l’indicizzazione dei contenuti.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=it)

### I nodi discendenti dei nodi di definizione dell’indice di ricerca personalizzato devono essere di tipo nt:unstructured {#oakpal-descendent-nodes}

* **Chiave**: IndexDescendantNodeType
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2021.2.0

È possibile che si verifichino problemi difficili da risolvere quando un nodo di definizione dell’indice di ricerca personalizzato ha nodi secondari non ordinati. Per evitarli, si consiglia che tutti i nodi discendenti di un nodo `oak:QueryIndexDefinition` siano di tipo `nt:unstructured`.

### I nodi di definizione dell’indice di ricerca personalizzato devono contenere un nodo secondario denominato indexRules con elementi secondari {#oakpal-custom-search-index}

* **Chiave**: IndexRulesNode
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2021.2.0

Un nodo di definizione dell’indice di ricerca personalizzato definito correttamente deve contenere un nodo secondario denominato `indexRules` che, a sua volta, deve avere almeno un elemento secondario. Per ulteriori informazioni consulta la sezione [Documentazione di Oak.](https://jackrabbit.apache.org/oak/docs/query/lucene.html)

### I nodi di definizione dell’indice di ricerca personalizzato devono rispettare le convenzioni di denominazione {#oakpal-custom-search-definitions}

* **Chiave**: IndexName
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2021.2.0

AEM Cloud Service richiede che le definizioni dell’indice di ricerca personalizzate (ovvero, nodi di tipo `oak:QueryIndexDefinition`) debbano essere denominate seguendo un pattern specifico descritto in [Ricerca e indicizzazione dei contenuti.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=it#how-to-use)

### I nodi di definizione dell’indice di ricerca personalizzato devono utilizzare il tipo di indice Lucene  {#oakpal-index-type-lucene}

* **Chiave**: IndexType
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2021.2.0

AEM Cloud Service richiede che le definizioni dell’indice di ricerca personalizzate (ovvero nodi di tipo `oak:QueryIndexDefinition`) abbiano una proprietà `type` con il valore impostato su `lucene`. L’indicizzazione utilizzando tipi di indice precedenti deve essere aggiornata prima della migrazione ad AEM Cloud Service. Per ulteriori informazioni, consulta la sezione [Documentazione di ricerca e indicizzazione dei contenuti](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=it#how-to-use).

### I nodi di definizione dell’indice di ricerca personalizzato non devono contenere una proprietà denominata seed {#oakpal-property-name-seed}

* **Chiave**: IndexSeedProperty
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2021.2.0

AEM Cloud Service non consente che le definizioni dell’indice di ricerca personalizzato (ovvero, i nodi di tipo `oak:QueryIndexDefinition`) contengano una proprietà denominata `seed`. L’indicizzazione utilizzando questa proprietà deve essere aggiornata prima della migrazione ad AEM Cloud Service. Per ulteriori informazioni, consulta la [Documentazione di ricerca e indicizzazione dei contenuti](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=it#how-to-use).

### I nodi di definizione dell’indice di ricerca personalizzato non devono contenere una proprietà denominata reindex {#oakpal-reindex-property}

* **Chiave**: IndexReindexProperty
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2021.2.0

AEM Cloud Service non consente che le definizioni dell’indice di ricerca personalizzato (ovvero, i nodi di tipo `oak:QueryIndexDefinition`) contengano una proprietà denominata `reindex`. L’indicizzazione utilizzando questa proprietà deve essere aggiornata prima della migrazione ad AEM Cloud Service. Per ulteriori informazioni, consulta la sezione [Documentazione di ricerca e indicizzazione dei contenuti](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=it#how-to-use).

## Strumento di ottimizzazione del Dispatcher {#dispatcher-optimization-tool-rules}

Nella sezione seguente sono elencati i controlli DOT (Dispatcher Optimization Tool) eseguiti da Cloud Manager. Segui i collegamenti per ogni verifica della definizione GitHub e dei dettagli relativi.

* [Token imprevisti nella configurazione del Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unexpected-tokens)

* [Virgolette senza corrispondenza nella configurazione del Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unmatched-quote)

* [Parentesi mancante nella configurazione del Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-brace)

* [Parentesi aggiuntiva nella configurazione del Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-extra-brace)

* [Proprietà obbligatoria mancante nella configurazione del Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-mandatory-property)

* [Proprietà obsoleta nella configurazione del Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-deprecated-property)

* [Configurazione del Dispatcher non trovata](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-not-found)

* [File di inclusione della configurazione Httpd non trovato](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---httpd-configuration-include-file-not-found)

* [Configurazione generale del Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-general)

* [La cache farm di pubblicazione del Dispatcher deve avere serveStaleOnError abilitato](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-servestaleonerror-enabled)

* [I filtri farm di pubblicazione del Dispatcher devono contenere le regole di negazione predefinite della versione 6.x.x dell’archetipo di AEM](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-contain-the-default-deny-rules-from-the-6xx-version-of-the-aem-archetype)

* [La proprietà statfileslevel della cache farm di pubblicazione del Dispatcher deve essere >= 2](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-statfileslevel-property-should-be--2)

* [La proprietà gracePeriod della farm di pubblicazione del Dispatcher deve essere >= 2](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-graceperiod-property-should-be--2)

* [Ogni farm del Dispatcher deve avere un nome univoco](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---each-dispatcher-farm-should-have-a-unique-name)

* [La cache farm di pubblicazione del Dispatcher deve avere le regole ignoreUrlParams configurate per creare un elenco Consentiti](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-its-ignoreurlparams-rules-configured-in-an-allow-list-manner)

* [I filtri farm di pubblicazione del Dispatcher devono specificare i selettori Sling consentiti per creare un elenco Consentiti](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-selectors-in-an-allow-list-manner)

* [I filtri farm di pubblicazione del Dispatcher devono specificare i pattern di suffisso Sling consentiti per creare un elenco Consentiti](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-suffix-patterns-in-an-allow-list-manner)

* [La direttiva “Richiedi tutto concesso” non deve essere utilizzata in una sezione di directory VirtualHost con un percorso di directory radice](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-require-all-granted-directive-should-not-be-used-in-a-virtualhost-directory-section-with-a-root-directory-path)
