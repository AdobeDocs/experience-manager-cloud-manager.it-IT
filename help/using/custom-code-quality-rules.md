---
title: Regole per la qualità del codice personalizzato
description: Scopri le specifiche delle regole di qualità del codice personalizzato eseguite da Cloud Manager durante il test di qualità del codice. Queste regole si basano sulle best practice dei tecnici di AEM.
exl-id: 7d118225-5826-434e-8869-01ee186e0754
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '3482'
ht-degree: 93%

---


# Regole per la qualità del codice personalizzato {#custom-code-quality-rules}

Scopri i dettagli sulle regole per la qualità del codice personalizzato eseguite da Cloud Manager nell’ambito del [test di qualità del codice](/help/using/code-quality-testing.md), in base alle best practice indicate dal team ingegneristico dell’AEM.

>[!NOTE]
>
>I campioni di codice qui forniti hanno valore puramente illustrativo. Consulta la [Documentazione sui concetti di SonarQube](https://docs.sonarsource.com/sonarqube/latest/) per scoprire di più sui concetti e sulle regole di qualità.

>[!NOTE]
>
>Le regole SonarQube complete non sono disponibili per il download a causa di informazioni proprietarie di Adobe. È possibile scaricare l’elenco completo delle regole [utilizzando questo collegamento](/help/assets/CodeQuality-rules-latest-AMS.xlsx). Continua a leggere questo documento per descrizioni ed esempi delle regole.

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

L’utilizzo di una stringa di formato da un’origine esterna (come un parametro di richiesta o contenuti generati dall’utente) può esporre un’applicazione ad attacchi DoS. In alcune circostanze una stringa di formato può essere controllata esternamente, ma ciò è consentito solo da fonti attendibili.

#### Codice non conforme {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text"));
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### Le richieste HTTP devono sempre avere timeout del socket e connessione {#http-requests-should-always-have-socket-and-connect-timeouts}

* **Chiave**: CQRules:ConnectionTimeoutMechanism
* **Tipo**: bug
* **Gravità**: critico
* **Da**: versione 2018.6.0

Durante l’esecuzione delle richieste HTTP da un’applicazione AEM, è fondamentale che siano configurati i timeout appropriati al fine di evitare un consumo di thread inutile. Sfortunatamente, sia il client HTTP predefinito di Java™, `java.net.HttpUrlConnection`, che il client Apache HTTP Components, ampiamente utilizzato, non hanno un timeout predefinito. Pertanto, i timeout devono essere configurati esplicitamente. Come best practice, questi timeout non devono superare i 60 secondi.

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

### Gli oggetti `ResourceResolver` devono essere sempre chiusi {#resourceresolver-objects-should-always-be-closed}

* **Chiave**: CQRules:CQBP-72
* **Tipo**: code smell
* **Gravità**: importante
* **Da**: versione 2018.4.0

Gli oggetti `ResourceResolver` ottenuti da `ResourceResolverFactory` consumano risorse di sistema. Sebbene esistano misure per recuperare tali risorse quando un oggetto `ResourceResolver` non è più in uso, è più efficiente chiudere in modo esplicito qualsiasi oggetto `ResourceResolver` aperto chiamando il metodo `close()`.

Un equivoco comune è che gli oggetti `ResourceResolver` creati con una sessione JCR esistente non devono essere chiusi in modo esplicito. Un altro equivoco è che la chiusura di questi oggetti comporti la chiusura della sessione JCR sottostante. Non è così. Indipendentemente da come un oggetto `ResourceResolver` viene aperto, quando non viene più utilizzato deve essere chiuso. Poiché `ResourceResolver` implementa l’interfaccia `Closeable`, è possibile utilizzare anche la sintassi `try-with-resources` anziché richiamare esplicitamente `close()`.

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

### Non utilizzare i percorsi Sling Servlet per registrare i Servlet {#do-not-use-sling-servlet-paths-to-register-servlets}

* **Chiave**: CQRules:CQBP-75
* **Tipo**: code smell
* **Gravità**: importante
* **Da**: versione 2018.4.0

Come descritto nella [documentazione di Sling](https://sling.apache.org/documentation/the-sling-engine/servlets.html), i servlet di associazione da percorsi sono sconsigliati. I servlet associati ai percorsi non possono utilizzare controlli dell’accesso JCR standard e, di conseguenza, richiedono un’ulteriore misura di sicurezza. Anziché utilizzare i servlet associati ai percorsi, si consiglia di creare nodi nell’archivio e di registrare i servlet in base al tipo di risorsa.

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

* **Chiave**: CQRules:CQBP-44---CatchAndEitherLogOrThrow
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2018.4.0

In generale, un’eccezione deve essere registrata una sola volta. Registrare le eccezioni più volte può causare confusione, in quanto non è chiaro quante volte si sono verificate. Il pattern più comune che comporta questo problema è la registrazione e la generazione di un’eccezione rilevata.

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

### Evitare le istruzioni di registro seguite immediatamente dalle istruzioni di generazione {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

* **Chiave**: CQRules:CQBP-44---ConsecutivelyLogAndThrow
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2018.4.0

Un altro modello comune da evitare è registrare un messaggio e generare immediatamente un’eccezione. Questo problema indica in genere che il messaggio di eccezione verrà duplicato nei file di log.

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

### Evita la registrazione a INFO durante la gestione delle richieste GET o HEAD {#avoid-logging-at-info-when-handling-get-or-head-requests}

* **Chiave**: CQRules:CQBP-44---LogInfoInGetOrHeadRequests
* **Tipo**: code smell
* **Gravità**: minore

In generale, per demarcare le azioni importanti si utilizza il livello registro INFO e, per impostazione predefinita, AEM è configurato per registrare al livello INFO o superiore. I metodi GET e HEAD devono essere sempre di sola lettura e non costituiscono pertanto azioni importanti. È probabile che la registrazione a livello INFO in risposta alle richieste GET o HEAD generi un notevole disturbo nel registro, rendendo così più difficile identificare le informazioni utili nei file di log. Quando si gestiscono le richieste GET o HEAD, la registrazione deve essere a livello WARN o ERROR in caso di errori. Per informazioni più approfondite sulla risoluzione dei problemi, la registrazione deve essere a livello DEBUG o TRACE.

>[!NOTE]
>
>Questo flusso di lavoro non si applica alla registrazione di tipo access.log per ogni richiesta.

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

### Non utilizzare `Exception.getMessage()` come primo parametro di un’istruzione di registrazione {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

* **Chiave**: CQRules:CQBP-44---ExceptionGetMessageIsFirstLogParam
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2018.4.0

Come best practice, i messaggi del registro devono fornire informazioni contestuali sulla posizione in cui è stata generata un’eccezione nell’applicazione. Mentre il contesto può essere determinato anche tramite l’utilizzo di tracce dello stack, in generale il messaggio di registro sarà più facile da leggere e comprendere. Di conseguenza, quando si registra un’eccezione, non è consigliabile utilizzare il messaggio di eccezione come messaggio di registro. Il messaggio dell’eccezione deve specificare quali problemi si sono verificati. Al contrario, il messaggio del registro deve essere utilizzato per comunicare il lettore le operazioni che l’applicazione stava effettuando quando si è verificata l’eccezione. Il messaggio di eccezione è comunque registrato. Specificando il messaggio, i registri saranno più facili da comprendere.

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

### La registrazione dei blocchi catch deve essere a livello WARN o ERROR {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}

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

### Non stampare le tracce dello stack sulla console {#do-not-print-stack-traces-to-the-console}

* **Chiave**: CQRules:CQBP-44---ExceptionPrintStackTrace
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2018.4.0

Il contesto è fondamentale per comprendere i messaggi del registro. L’utilizzo di `Exception.printStackTrace()` fa sì che solo la traccia dello stack venga trasmessa al flusso di errore standard, perdendo così tutto il contesto. Inoltre, in un’applicazione multi-thread come AEM se vengono stampate più eccezioni utilizzando questo metodo in parallelo, le rispettive tracce di stack possono sovrapporsi e creare confusione. Le eccezioni devono essere registrate solo tramite il framework di registrazione.

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

### Non trasmettere a output standard o errore standard {#do-not-output-to-standard-output-or-standard-error}

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

### Evitare percorsi `/apps` e `/libs` hardcoded {#avoid-hardcoded-apps-and-libs-paths}

* **Chiave**: CQRules:CQBP-71
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2018.4.0

I percorsi che iniziano con `/libs` e `/apps` in genere non devono essere hardcoded. Questi percorsi vengono generalmente archiviati rispetto al percorso di ricerca Sling, che ha come impostazione predefinita `/libs,/apps`. L’utilizzo del percorso assoluto può presentare difetti minimi che appariranno solo successivamente nel ciclo di vita del progetto.

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

### Non utilizzare il modulo di pianificazione Sling {#sonarqube-sling-scheduler}

* **Chiave**: CQRules:AMSCORE-554
* **Tipo**: code smell/compatibilità con Cloud Service
* **Gravità**: minore
* **Da**: versione 2020.5.0

Non utilizzare lo Sling Scheduler per le attività che richiedono un’esecuzione garantita. I processi pianificati Sling garantiscono l’esecuzione e sono più adatti per gli ambienti cluster che per quelli non cluster.

Per ulteriori informazioni sulla gestione dei processi Sling negli ambienti cluster, consulta la [documentazione sull&#39;evento Sling di Apache e sulla gestione dei processi](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html).

### Non utilizzare le API AEM obsolete {#sonarqube-aem-deprecated}

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
>OakPAL è un framework che convalida i pacchetti di contenuti con un archivio Oak autonomo. È stato sviluppato da un partner AEM e vincitore del premio AEM Rock Star North America 2019.

### La clientela non deve implementare o estendere le API di prodotto annotate con @ProviderType {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

* **Chiave**: CQBP-84
* **Tipo**: bug
* **Gravità**: critico
* **Da**: versione 2018.7.0

L’API AEM contiene interfacce e classi Java™ che devono essere utilizzate solo con il codice personalizzato, ma non devono essere implementate. Ad esempio, solo AEM implementa l’interfaccia `com.day.cq.wcm.api.Page`.

L’aggiunta di nuovi metodi a queste interfacce non influisce sul codice esistente, rendendola compatibile con le versioni precedenti. Tuttavia, se il codice personalizzato implementa una di queste interfacce, genera un rischio di retrocompatibilità con le versioni precedenti.

Le interfacce e le classi che devono essere implementate solo da AEM sono annotate con `org.osgi.annotation.versioning.ProviderType` o, a volte, con l’annotazione `aQute.bnd.annotation.ProviderType` precedente. Questa regola rileva le istanze in cui il codice personalizzato implementa tale interfaccia o estende una classe.

#### Codice non conforme {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### I pacchetti cliente non devono creare o modificare nodi in `/libs` {#oakpal-customer-package}

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

Un problema comune che si verifica in progetti complessi è che lo stesso componente OSGi viene configurato più volte. Questo problema crea ambiguità riguardo alla configurazione da utilizzare. Questa regola è “sensibile alla modalità di esecuzione”, in quanto individua solo i problemi in cui lo stesso componente è configurato più volte nella stessa modalità di esecuzione o nella stessa combinazione di modalità di esecuzione.

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

Per motivi di sicurezza, i percorsi contenenti `/config/` e `/install/` sono leggibili solo dagli utenti amministratori in AEM e devono essere utilizzati solo per la configurazione OSGi e i bundle OSGi. Se si inseriscono altri tipi di contenuto in percorsi che contengono questi segmenti, si verifica un comportamento dell’applicazione per cui si passa involontariamente tra utenti amministratori e non amministratori.

Un problema comune è l’utilizzo di nodi denominati `config` nelle finestre di dialogo dei componenti o quando si specifica la configurazione dell’Editor Rich Text per la modifica in linea. Per risolvere questo problema, il nodo che causa la violazione deve essere rinominato con un nome conforme. Per la configurazione del rich text editor, specifica la nuova posizione con la proprietà `configPath` nel nodo `cq:inplaceEditing`.

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

Simile alla [regola I pacchetti non devono contenere configurazioni OSGi duplicate](#oakpal-package-osgi), questo è un problema comune nei progetti complessi in cui diversi pacchetti di contenuto scrivono nello stesso percorso di nodo. Benché sia possibile utilizzare le dipendenze tra pacchetti di contenuti per garantire risultati coerenti, è meglio evitare del tutto le sovrapposizioni.

### La modalità di authoring predefinita non deve corrispondere all’interfaccia classica {#oakpal-default-authoring}

* **Chiave**: ClassicUIAuthoringMode
* **Tipo**: compatibilità code smell / Cloud Service
* **Gravità**: minore
* **Da**: versione 2020.5.0

La configurazione OSGi `com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl` definisce la modalità di authoring predefinita in AEM. Poiché l’interfaccia classica è diventata obsoleta a partire dalla versione 6.4 di AEM, ora viene segnalato un problema se la modalità di authoring predefinita è configurata sull’interfaccia classica.

### I componenti con finestre di dialogo devono avere finestre di dialogo per l’interfaccia touch {#oakpal-components-dialogs}

* **Chiave**: ComponentWithOnlyClassicUIDialog
* **Tipo**: code smell/compatibilità con Cloud Service
* **Gravità**: minore
* **Da**: versione 2020.5.0

I componenti AEM con una finestra di dialogo per l’interfaccia classica devono avere anche una finestra di dialogo per l’interfaccia touch, in modo da fornire un’authoring ottimale e per compatibilità con il modello di distribuzione di Cloud Service, che supporta l’interfaccia classica. Questa regola verifica i seguenti scenari:

* Un componente con una finestra di dialogo dell’interfaccia classica (ovvero un nodo figlio `dialog`) deve avere una finestra di dialogo corrispondente dell’interfaccia Touch (ovvero un nodo figlio `cq:dialog`).
* Un componente che ha una finestra di dialogo di progettazione per l’interfaccia utente classica (ad es. un nodo `design_dialog`) deve avere anche una finestra di dialogo di progettazione corrispondente per l’interfaccia utente touch (cioè un nodo `cq:design_dialog` secondario).
* Un componente con una finestra di dialogo Interfaccia classica e una finestra di dialogo di progettazione Interfaccia classica deve avere una finestra di dialogo Interfaccia Touch corrispondente così come una finestra di dialogo di progettazione Interfaccia Touch corrispondente.

La documentazione sugli strumenti di modernizzazione AEM fornisce dettagli e strumenti per la conversione dei componenti dall’interfaccia classica all’interfaccia touch. Per ulteriori dettagli, consulta la [documentazione sugli strumenti di modernizzazione AEM](https://opensource.adobe.com/aem-modernize-tools/).

### Gli agenti di replica inversa non devono essere utilizzati {#oakpal-reverse-replication}

* **Chiave**: ReverseReplication
* **Tipo**: code smell/compatibilità con Cloud Service
* **Gravità**: minore
* **Da**: versione 2020.5.0

La replica inversa non è supportata nelle distribuzioni di Cloud Service, come descritto in [Note sulla versione: rimozione degli agenti di replica](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/release-notes/aem-cloud-changes#replication-agents).

Se utilizzi la replica inversa, contatta Adobe per scoprire le soluzioni alternative.

### Le risorse da librerie client abilitate per i proxy devono essere in una cartella denominata risorse {#oakpal-resources-proxy}

* **Chiave**: ClientlibProxyResource
* **Tipo**: bug
* **Gravità**: minore
* **Da**: versione 2021.2.0

Le librerie client AEM possono contenere risorse statiche come immagini e font. Come descritto nella [documentazione sull&#39;utilizzo di librerie lato client](https://experienceleague.adobe.com/it/docs/experience-manager-65/content/implementing/developing/introduction/clientlibs#using-preprocessors), quando si utilizzano librerie client con proxy le risorse statiche devono essere contenute in una cartella secondaria denominata `resources` affinché sia possibile farvi riferimento nelle istanze di pubblicazione.

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

### Utilizzo di processi di flusso di lavoro non compatibili con Cloud Service {#oakpal-usage-cloud-service}

* **Chiave**: CloudServiceIncompatibleWorkflowProcess
* **Tipo**: code smell
* **Gravità**: bloccante
* **Da**: versione 2021.2.0

Con il passaggio ai micro-servizi Asset per l’elaborazione delle risorse in AEM Cloud Service, diversi processi di flusso di lavoro utilizzati nelle versioni locali e AMS di AEM non sono più supportati o non sono necessari.

Lo strumento di migrazione nell’[archivio GitHub di AEM Assets as a Cloud Service](https://github.com/adobe/aem-cloud-migration) può essere utilizzato per aggiornare i modelli di flusso di lavoro durante la migrazione ad AEM as a Cloud Service.

### È preferibile utilizzare modelli modificabili rispetto ai modelli statici {#oakpal-static-template}

* **Chiave**: StaticTemplateUsage
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2021.2.0

Anche se l’utilizzo di modelli statici è sempre stato comune nei progetti AEM, i modelli modificabili sono altamente consigliati, in quanto offrono la massima flessibilità e supportano funzioni aggiuntive non presenti nei modelli statici. Ulteriori informazioni sono disponibili in [Modelli di pagina - Documentazione modificabile](https://experienceleague.adobe.com/it/docs/experience-manager-65/content/implementing/developing/platform/templates/page-templates-editable).

La migrazione da modelli statici a modificabili può essere in gran parte automatizzata utilizzando gli [strumenti di modernizzazione AEM](https://opensource.adobe.com/aem-modernize-tools/).

### L’utilizzo dei componenti di base precedenti è sconsigliato {#oakpal-usage-legacy}

* **Chiave**: LegacyFoundationComponentUsage
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2021.2.0

I componenti Foundation legacy (ovvero i componenti in `/libs/foundation`) sono stati dichiarati obsoleti per diverse versioni AEM a favore dei [componenti core](https://experienceleague.adobe.com/it/docs/experience-manager-core-components/using/introduction). L’utilizzo dei componenti di base precedenti come base per i componenti personalizzati, tramite sovrapposizione o ereditarietà, è sconsigliato e deve essere convertito nel componente di base corrispondente.

Gli [strumenti di modernizzazione AEM](https://opensource.adobe.com/aem-modernize-tools/) possono facilitare questa conversione.

### I nodi di definizione dell’indice di ricerca personalizzato devono essere nodi secondari diretti di `/oak:index` {#oakpal-custom-search}

* **Chiave**: OakIndexLocation
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2021.2.0

AEM Cloud Service richiede che le definizioni dell’indice di ricerca personalizzato (ad esempio, nodi di tipo `oak:QueryIndexDefinition`) siano nodi secondari diretti di `/oak:index`. Gli indici in altre posizioni devono essere spostati per essere compatibili con AEM Cloud Service. Ulteriori informazioni sugli indici di ricerca sono disponibili nella [documentazione sulla ricerca e l&#39;indicizzazione dei contenuti](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/operations/indexing).

### I nodi di definizione dell’indice di ricerca personalizzato devono avere una compatVersion di 2 {#oakpal-custom-search-compatVersion}

* **Chiave**: IndexCompatVersion
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2021.2.0

AEM Cloud Service richiede che le definizioni di indici di ricerca personalizzati (ovvero nodi di tipo `oak:QueryIndexDefinition`) abbiano la proprietà `compatVersion` impostata su `2`. AEM Cloud Service non supporta altri valori. Ulteriori informazioni sugli indici di ricerca sono disponibili nella [documentazione sulla ricerca e l&#39;indicizzazione dei contenuti](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/operations/indexing).

### I nodi discendenti dei nodi di definizione dell’indice di ricerca personalizzato devono essere di tipo `nt:unstructured` {#oakpal-descendent-nodes}

* **Chiave**: IndexDescendantNodeType
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2021.2.0

È possibile che si verifichino problemi difficili da risolvere quando un nodo di definizione dell’indice di ricerca personalizzato ha nodi secondari non ordinati. Per evitarli, si consiglia che tutti i nodi discendenti di un nodo `oak:QueryIndexDefinition` siano di tipo `nt:unstructured`.

### I nodi di definizione dell’indice di ricerca personalizzato devono contenere un nodo secondario denominato `indexRules` con elementi secondari {#oakpal-custom-search-index}

* **Chiave**: IndexRulesNode
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2021.2.0

Un nodo di definizione dell’indice di ricerca personalizzato definito correttamente deve contenere un nodo secondario denominato `indexRules` che, a sua volta, deve avere almeno un elemento secondario. Ulteriori informazioni sono disponibili nella [documentazione di Oak](https://jackrabbit.apache.org/oak/docs/query/lucene.html).

### I nodi di definizione dell’indice di ricerca personalizzato devono rispettare le convenzioni di denominazione {#oakpal-custom-search-definitions}

* **Chiave**: IndexName
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2021.2.0

AEM Cloud Service richiede che le definizioni dell’indice di ricerca personalizzato (ovvero, nodi di tipo `oak:QueryIndexDefinition`) debbano essere denominate seguendo un pattern specifico descritto in [Ricerca e indicizzazione dei contenuti.](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use)

### I nodi di definizione dell’indice di ricerca personalizzato devono utilizzare il tipo di indice Lucene {#oakpal-index-type-lucene}

* **Chiave**: IndexType
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2021.2.0

AEM Cloud Service richiede che le definizioni dell’indice di ricerca personalizzate (ovvero nodi di tipo `oak:QueryIndexDefinition`) abbiano una proprietà `type` con il valore impostato su `lucene`. L’indicizzazione utilizzando tipi di indice precedenti deve essere aggiornata prima della migrazione ad AEM Cloud Service. Per ulteriori informazioni, consulta la sezione [Documentazione di ricerca e indicizzazione dei contenuti](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use).

### I nodi di definizione dell’indice di ricerca personalizzato non devono contenere una proprietà denominata `seed` {#oakpal-property-name-seed}

* **Chiave**: IndexSeedProperty
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2021.2.0

AEM Cloud Service non consente che le definizioni dell’indice di ricerca personalizzato (ovvero, i nodi di tipo `oak:QueryIndexDefinition`) contengano una proprietà denominata `seed`. L’indicizzazione utilizzando questa proprietà deve essere aggiornata prima della migrazione ad AEM Cloud Service. Per ulteriori informazioni, consulta la [Documentazione di ricerca e indicizzazione dei contenuti](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use).

### I nodi di definizione dell’indice di ricerca personalizzato non devono contenere una proprietà denominata `reindex` {#oakpal-reindex-property}

* **Chiave**: IndexReindexProperty
* **Tipo**: code smell
* **Gravità**: minore
* **Da**: versione 2021.2.0

AEM Cloud Service non consente che le definizioni dell’indice di ricerca personalizzato (ovvero, i nodi di tipo `oak:QueryIndexDefinition`) contengano una proprietà denominata `reindex`. L’indicizzazione utilizzando questa proprietà deve essere aggiornata prima della migrazione ad AEM Cloud Service. Per ulteriori informazioni, consulta la [Documentazione di ricerca e indicizzazione dei contenuti](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use).

### I nodi di definizione dell’indice non devono essere distribuiti nel pacchetto di contenuti dell’interfaccia utente {#oakpal-ui-content-package}

* **Chiave**: IndexNotUnderUIContent
* **Tipo**: miglioramento
* **Gravità**: minore
* **Da**: versione 2024.6.0

AEM Cloud Service non consente di distribuire nel pacchetto di contenuti dell’interfaccia utente le definizioni di indici di ricerca personalizzati (nodi di tipo `oak:QueryIndexDefinition`).

>[!WARNING]
>
>Ti invitiamo a risolvere questo problema il prima possibile poiché, a partire dalla [versione di agosto 2024 di Cloud Manager](/help/release-notes/current.md), causerà un errore nelle pipeline.

### La definizione dell’indice testuale personalizzato di tipo `damAssetLucene` deve avere il prefisso `damAssetLucene` {#oakpal-dam-asset-lucene}

* **Chiave**: CustomFulltextIndexesOfTheDamAssetCheck
* **Tipo**: miglioramento
* **Gravità**: minore
* **Da**: versione 2024.6.0

AEM Cloud Service non consente che la definizione di indici testuali personalizzati di tipo `damAssetLucene` sia preceduta da un prefisso diverso da `damAssetLucene`.

>[!WARNING]
>
>Ti invitiamo a risolvere questo problema il prima possibile poiché, a partire dalla [versione di agosto 2024 di Cloud Manager](/help/release-notes/current.md), causerà un errore nelle pipeline.

### I nodi di definizione dell’indice non devono contenere proprietà con lo stesso nome {#oakpal-index-property-name}

* **Chiave**: DuplicateNameProperty
* **Tipo**: miglioramento
* **Gravità**: minore
* **Da**: versione 2024.6.0

AEM Cloud Service non consente che le definizioni dell’indice di ricerca personalizzato (ovvero, i nodi di tipo `oak:QueryIndexDefinition`) contengano una proprietà denominata con lo stesso nome.

>[!WARNING]
>
>Ti invitiamo a risolvere questo problema il prima possibile poiché, a partire dalla [versione di agosto 2024 di Cloud Manager](/help/release-notes/current.md), causerà un errore nelle pipeline.

### Non è consentito personalizzare alcune definizioni di indici predefiniti {#oakpal-customizing-ootb-index}

* **Chiave**: RestrictIndexCustomization
* **Tipo**: miglioramento
* **Gravità**: minore
* **Da**: versione 2024.6.0

AEM Cloud Service non consente modifiche non autorizzate ai seguenti indici integrati:

* `nodetypeLucene`
* `slingResourceResolver`
* `socialLucene`
* `appsLibsLucene`
* `authorizables`
* `pathReference`

>[!WARNING]
>
>Ti invitiamo a risolvere questo problema il prima possibile poiché, a partire dalla [versione di agosto 2024 di Cloud Manager](/help/release-notes/current.md), causerà un errore nelle pipeline.

### La configurazione dei tokenizer negli analizzatori deve essere creata con il nome `tokenizer` {#oakpal-tokenizer}

* **Chiave**: AnalyzerTokenizerConfigCheck
* **Tipo**: miglioramento
* **Gravità**: minore
* **Da**: versione 2024.6.0

AEM Cloud Service vieta la creazione di tokenizzatori con nomi non corretti negli analizzatori. I tokenizzatori devono sempre essere definiti come `tokenizer`.

### La configurazione delle definizioni di indicizzazione non deve contenere spazi {#oakpal-indexing-definitions-spaces}

* **Chiave**: PathSpacesCheck
* **Tipo**: miglioramento
* **Gravità**: minore
* **Da**: versione 2024.7.0

AEM Cloud Service non consente la creazione di definizioni di indicizzazione che contengono proprietà con spazi.

## Strumento di ottimizzazione del Dispatcher {#dispatcher-optimization-tool-rules}

Nella sezione seguente sono elencati i controlli DOT (Dispatcher Optimization Tool) eseguiti da Cloud Manager. Segui i collegamenti per ogni verifica della definizione GitHub e dei dettagli relativi.

* [Token imprevisti nella configurazione del Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unexpected-tokens)

* [Virgolette senza corrispondenza nella configurazione del Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unmatched-quote)

* [Parentesi mancante nella configurazione del Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-brace)

* [Parentesi aggiuntiva nella configurazione del Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-extra-brace)

* [Proprietà obbligatoria mancante nella configurazione del Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-mandatory-property)

* [Proprietà obsoleta nella configurazione del Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-deprecated-property)

* [Configurazione del Dispatcher non trovata](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-not-found)

* [La configurazione Httpd include un file non trovato](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---httpd-configuration-include-file-not-found)

* [Configurazione generale del Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-general)

* [La cache farm di pubblicazione del Dispatcher deve avere `serveStaleOnError` abilitato](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-servestaleonerror-enabled)

* [I filtri farm di pubblicazione del Dispatcher devono contenere le regole di negazione predefinite della versione 6.x.x dell’archetipo di AEM](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-contain-the-default-deny-rules-from-the-6xx-version-of-the-aem-archetype)

* [La proprietà `statfileslevel` della cache farm di pubblicazione del Dispatcher deve essere >= 2](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-statfileslevel-property-should-be--2)

* [La proprietà `gracePeriod` della farm di pubblicazione del Dispatcher deve essere >= 2](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-graceperiod-property-should-be--2)

* [Ogni farm del Dispatcher deve avere un nome univoco](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---each-dispatcher-farm-should-have-a-unique-name)

* [La cache farm di pubblicazione del Dispatcher deve avere le proprie regole `ignoreUrlParams` configurate in modalità elenco Consentiti](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-its-ignoreurlparams-rules-configured-in-an-allow-list-manner)

* [I filtri farm di pubblicazione del Dispatcher devono specificare i selettori Sling consentiti per creare un elenco Consentiti](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-selectors-in-an-allow-list-manner)

* [I filtri farm di pubblicazione del Dispatcher devono specificare i pattern di suffisso Sling consentiti per creare un elenco Consentiti](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-suffix-patterns-in-an-allow-list-manner)

* [La direttiva “Richiedi tutto concesso” non deve essere utilizzata in una sezione di directory VirtualHost con un percorso di directory radice](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-require-all-granted-directive-should-not-be-used-in-a-virtualhost-directory-section-with-a-root-directory-path)
