---
title: Regole di qualità codice personalizzate
seo-title: Regole di qualità codice personalizzate
description: Segui questa pagina per informazioni sulle regole di qualità del codice personalizzate eseguite da Cloud Manager.
seo-description: Segui questa pagina per informazioni sulle regole di qualità del codice personalizzate eseguite da Adobe Experience Manager Cloud Manager.
uuid: a 7 feb 465-1982-46 be -9 e 57-e 67 b 59849579
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: utilizzo
discoiquuid: d 2338 c 74-3278-49 e 6-a 186-6 ef 62362509 f
translation-type: tm+mt
source-git-commit: f76b8e6a036ab920f11fb913d3ad29818f1e153f

---


# Custom Code Quality Rules {#custom-code-quality-rules}

Questa pagina descrive le regole di qualità del codice personalizzate eseguite da Cloud Manager create in base alle best practice di AEM Engineering.

>[!NOTE]
>
>Gli esempi di codice forniti qui sono solo a scopo illustrativo.

## SonarQube Rules {#sonarqube-rules}

La sezione seguente evidenzia le regole sonarqube:

### Do not use potentially dangerous functions {#do-not-use-potentially-dangerous-functions}

**Chiave**: Cqrules: CWE -676

**Tipo**: Vulnerabilità

**Gravità**: Principale

**Poiché**: Versione 2018.4.0

The methods ***Thread.stop()*** and ***Thread.interrupt()*** can produce hard-to-reproduce issues and, in some cases, security vulnerabilities. Il loro utilizzo deve essere rigorosamente monitorato e convalidato. In generale, il passaggio del messaggio è un modo più sicuro per raggiungere obiettivi simili.

#### Non-Compliant Code {#non-compliant-code}

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

#### Compliant Code {#compliant-code}

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

### Do not use format strings which may be externally controlled {#do-not-use-format-strings-which-may-be-externally-controlled}

**Chiave**: Cqrules: CWE -134

**Tipo**: Vulnerabilità

**Gravità**: Principale

**Poiché**: Versione 2018.4.0

L&#39;utilizzo di una stringa di formato da un&#39;origine esterna (come un parametro di richiesta o un contenuto generato dall&#39;utente) può esporre un&#39;applicazione a attacchi di negazione di servizi. In alcune circostanze una stringa di formato potrebbe essere controllata esternamente, ma è consentita solo dalle fonti affidabili.

#### Non-Compliant Code {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text");
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### HTTP requests should always have socket and connect timeouts {#http-requests-should-always-have-socket-and-connect-timeouts}

**Chiave**: Cqrules: Connectiontimeoutmechanism

**Tipo**: Bug

**Gravità**: Critico

**Poiché**: Versione 2018.6.0

Quando si eseguono richieste HTTP dall&#39;interno di un&#39;applicazione AEM, è importante assicurarsi che i timeout corretti siano configurati per evitare inutili dispendio di thread. Purtroppo, il comportamento predefinito del client HTTP predefinito di Java (java.net.Ht tpurlconnection) e il client Apache HTTP utilizzato comunemente non devono mai essere timeout, pertanto i timeout devono essere impostati in modo esplicito. Inoltre, come procedura ottimale, questi timeout non devono superare i 60 secondi.

#### Non-Compliant Code {#non-compliant-code-2}

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

#### Compliant Code {#compliant-code-1}

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

### Product APIs annotated with @ProviderType should not be implemented or extended by customers {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

**Chiave**: CQBP -84, dipendenze CQBP -84

**Tipo**: Bug

**Gravità**: Critico

**Poiché**: Versione 2018.7.0

L&#39;API AEM contiene interfacce Java e classi che possono essere utilizzate, ma non implementate, mediante codice personalizzato. For example, the interface *com.day.cq.wcm.api.Page* is designed to be implemented by ***AEM only***.

Quando vengono aggiunti nuovi metodi a queste interfacce, questi metodi aggiuntivi non influiscono sul codice esistente che utilizza tali interfacce e, di conseguenza, l&#39;aggiunta di nuovi metodi a queste interfacce è considerata compatibile con le versioni precedenti. However, if custom code ***implements*** one of these interfaces, that custom code has introduced a backwards-compatibility risk for the customer.

Interfaces (and classes) which are only intended to be implemented by AEM are annotated with *org.osgi.annotation.versioning.ProviderType* (or, in some cases, a similar legacy annotation *aQute.bnd.annotation.ProviderType*). Questa regola identifica i casi in cui tale interfaccia è implementata (o una classe estesa) tramite codice personalizzato.

#### Non-Compliant Code {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### ResourceResolver objects should always be closed {#resourceresolver-objects-should-always-be-closed}

**Chiave**: Cqrules: CQBP -72

**Tipo**: Odore codice

**Gravità**: Principale

**Poiché**: Versione 2018.4.0

Gli oggetti resourceresolver ottenuti da resourceresolverfactory consumano risorse di sistema. Sebbene siano disponibili misure per reclamare queste risorse quando un resourceresolver non è più in uso, è più efficiente chiudere esplicitamente qualsiasi oggetto resourceresolver aperto chiamando il metodo close ().

Un errore relativamente comune è che gli oggetti resourceresolver creati utilizzando una sessione JCR esistente non devono essere chiusi in modo esplicito o che in tal modo chiuderanno la sessione JCR sottostante. Questo non è il caso, a prescindere dalla modalità di apertura di un resourceresolver, qualora non venga più utilizzato. Poiché resourceresolver implementa l&#39;interfaccia chiusibile, è anche possibile utilizzare la sintassi try-with-resources invece di richiamare esplicitamente close ().

#### Non-Compliant Code {#non-compliant-code-4}

```java
public void dontDoThis(Session session) throws Exception {
  ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
  // do some stuff with the resolver
}
```

#### Compliant Code {#compliant-code-2}

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

### Do not use Sling servlet paths to register servlets {#do-not-use-sling-servlet-paths-to-register-servlets}

**Chiave**: Cqrules: CQBP -75

**Tipo**: Odore codice

**Gravità**: Principale

**Poiché**: Versione 2018.4.0

As described in the [Sling documentation](http://sling.apache.org/documentation/the-sling-engine/servlets.html), bindings servlets by paths is discouraged. I servlet associati al percorso non possono utilizzare controlli di accesso JCR standard e, di conseguenza, richiedono un ulteriore rigonfiamento della sicurezza. Anziché utilizzare servlet associati al percorso, si consiglia di creare nodi nell&#39;archivio e di registrare i servlet in base al tipo di risorsa.

#### Non-Compliant Code {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### Caught Exceptions should be logged or thrown, but not both {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

**Chiave**: Cqrules: CQBP -44—Catchandeitherlogorthrow

**Tipo**: Odore codice

**Gravità**: Secondario

**Poiché**: Versione 2018.4.0

In generale, un&#39;eccezione deve essere registrata esattamente una volta. Le eccezioni di registrazione più volte possono causare confusione in quanto non è chiara quante volte si è verificata un&#39;eccezione. Il pattern più comune che porta alla registrazione e genera un&#39;eccezione rilevata.

#### Non-Compliant Code {#non-compliant-code-6}

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

#### Compliant Code {#compliant-code-3}

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

### Avoid having a log statement immediately followed by a throw statement {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

**Chiave**: Cqrules: CQBP -44—Successivelylogandthrow

**Tipo**: Odore codice

**Gravità**: Secondario

**Poiché**: Versione 2018.4.0

Un altro pattern comune da evitare consiste nel registrare un messaggio e quindi su un&#39;eccezione. In genere ciò indica che il messaggio di eccezione verrà duplicato nei file di registro.

#### Non-Compliant Code {#non-compliant-code-7}

```java
public void dontDoThis() throws Exception {
  logger.error("something went wrong");
  throw new RuntimeException("something went wrong");
}
```

#### Compliant Code {#compliant-code-4}

```java
public void doThis() throws Exception {
  throw new RuntimeException("something went wrong");
}
```

### Avoid logging at INFO when handling GET or HEAD requests {#avoid-logging-at-info-when-handling-get-or-head-requests}

**Chiave**: Cqrules: CQBP -44—Loginfoingetorheadrequests

**Tipo**: Odore codice

**Gravità**: Secondario

In generale, il livello di registro INFO deve essere utilizzato per delimitare azioni importanti e, per impostazione predefinita, AEM è configurato per effettuare il login a livello INFO o superiore. I metodi GET e HEAD devono essere solo operazioni di sola lettura e quindi non costituiscono interventi importanti. L&#39;accesso a livello INFO in risposta alle richieste GET o HEAD creerà probabilmente un rumore di registro significativo, rendendo più difficile identificare le informazioni utili nei file di registro. L&#39;accesso durante la gestione delle richieste GET o HEAD dovrebbe essere a livello di AVVISO o di ERRORE quando si verifica un errore o a livelli DEBUG o TRACE se sono utili informazioni di risoluzione dei problemi più rigorose.

>[!CAUTION]
>
>Questo non vale per l&#39;accesso a access. log-type per ogni richiesta.

#### Non-Compliant Code {#non-compliant-code-8}

```java
public void doGet() throws Exception {
  logger.info("handling a request from the user");
}
```

#### Compliant Code {#compliant-code-5}

```java
public void doGet() throws Exception {
  logger.debug("handling a request from the user.");
}
```

### Do not use Exception.getMessage() as the first parameter of a logging statement {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

**Chiave**: Cqrules: CQBP -44—Exceptiongetmessageisfirstlogparam

**Tipo**: Odore codice

**Gravità**: Secondario

**Poiché**: Versione 2018.4.0

Come procedura ottimale, i messaggi del registro devono fornire informazioni contestuali su dove si è verificato un&#39;eccezione nell&#39;applicazione. Anche se il contesto può essere determinato anche utilizzando le tracce dello stack, in generale il messaggio di registro diventerà più semplice da leggere e comprendere. Di conseguenza, quando si registra un&#39;eccezione, è consigliabile utilizzare il messaggio dell&#39;eccezione come messaggio di registro. Il messaggio di eccezione conterrà ciò che è andato a buon fine; il messaggio di registro sarà utilizzato per indicare a un lettore di registro ciò che l&#39;applicazione stava realizzando quando si è verificata l&#39;eccezione. Il messaggio di eccezione continuerà a essere registrato; specificando il vostro messaggio, i registri saranno più facili da comprendere.

#### Non-Compliant Code {#non-compliant-code-9}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error(e.getMessage(), e);
  }
}
```

#### Compliant Code {#compliant-code-6}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Logging in catch blocks should be at the WARN or ERROR level {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}

**Chiave**: Cqrules: CQBP -44—Wrongloglevelincatchblock

**Tipo**: Odore codice

**Gravità**: Secondario

**Poiché**: Versione 2018.4.0

As the name suggests, Java exceptions should always be used in *exceptional* circumstances. Di conseguenza, quando viene rilevata un&#39;eccezione, è importante assicurarsi che i messaggi del registro siano collegati al livello appropriato: ALERT o ERROR. In questo modo i messaggi vengono visualizzati correttamente nei registri.

#### Non-Compliant Code {#non-compliant-code-10}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.debug(e.getMessage(), e);
  }
}
```

#### Compliant Code {#compliant-code-7}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Do not print stack traces to the console {#do-not-print-stack-traces-to-the-console}

**Chiave**: Cqrules: CQBP -44—Exceptionprintstacktrace

**Tipo**: Odore codice

**Gravità**: Secondario

**Poiché**: Versione 2018.4.0

Come indicato, il contesto è fondamentale per comprendere i messaggi di registro. Using Exception.printStackTrace() causes **only** the stack trace to be output to the standard error stream thereby losing all context. Inoltre, in un&#39;applicazione multi-thread come AEM se più eccezioni vengono stampate utilizzando in parallelo questo metodo, le tracce dello stack possono sovrapporsi che generano confusione significativa. Le eccezioni devono essere registrate solo tramite il framework di registrazione.

#### Non-Compliant Code {#non-compliant-code-11}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    e.printStackTrace();
  }
}
```

#### Compliant Code {#compliant-code-8}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Do not output to Standard Output or Standard Error {#do-not-output-to-standard-output-or-standard-error}

**Chiave**: Cqrules: CQBP -44—loglevelconsoleprinters

**Tipo**: Odore codice

**Gravità**: Secondario

**Poiché**: Versione 2018.4.0

La registrazione in AEM deve essere sempre realizzata tramite il framework di registrazione (SLF 4 J). L&#39;output diretto direttamente ai flussi di errore standard o standard perde le informazioni strutturali e contestuali fornite dal framework di registrazione e può, in alcuni casi, causare problemi di prestazioni.

#### Non-Compliant Code {#non-compliant-code-12}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    System.err.println("Unable to do something");
  }
}
```

#### Compliant Code {#compliant-code-9}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Avoid Hardcoded /apps and /libs Paths {#avoid-hardcoded-apps-and-libs-paths}

**Chiave**: Cqrules: CQBP -71

**Tipo**: Odore codice

**Gravità**: Secondario

**Poiché**: Versione 2018.4.0

In generale, i percorsi che iniziano con /libs e /apps non devono essere codificati in quanto i percorsi a cui fanno riferimento sono più comunemente memorizzati come percorsi rispetto al percorso di ricerca Sling (che per impostazione predefinita è impostata su /libs,/app). L&#39;utilizzo del percorso assoluto potrebbe introdurre lievi difetti che verrebbero visualizzati solo successivamente nel ciclo di vita del progetto.

#### Non-Compliant Code {#non-compliant-code-13}

```java
public boolean dontDoThis(Resource resource) {
  return resource.isResourceType("/libs/foundation/components/text");
}
```

#### Compliant Code {#compliant-code-10}

```java
public void doThis(Resource resource) {
  return resource.isResourceType("foundation/components/text");
}
```


## OakPAL Content Rules {#oakpal-rules}

Trovi sotto i controlli oakpal eseguiti da Cloud Manager.

>[!NOTE]
>Oakpal è un framework sviluppato da un partner AEM (e vincitore di 2019 AEM Rockstar North America) che convalida i pacchetti di contenuto utilizzando un archivio Oak indipendente.

### Customer Packages Should Not Create or Modify Nodes Under /libs {#oakpal-customer-package}

**Chiave**: Bannedpaths

**Tipo**: Bug

**Gravità**: Blocker

**Poiché**: Versione 2019.6.0

È una procedura consigliata che la struttura del contenuto /libs nell&#39;archivio dei contenuti AEM sia considerata di sola lettura dai clienti. Modifying nodes and properties under */libs* creates significant risk for major and minor updates. Modifications to */libs* should only be made by Adobe through official channels.

### Packages Should Not Contain Duplicate OSGi Configurations {#oakpal-package-osgi}

**Chiave**: Duplicateosgiconfigurations

**Tipo**: Bug

**Gravità**: Principale

**Poiché**: Versione 2019.6.0

Un problema comune che si verifica su progetti complessi è quello in cui lo stesso componente osgi è configurato più volte. Ciò crea un&#39;ambiguità rispetto alla configurazione da eseguire. Questa regola è &quot;in modalità runmode&quot; in quanto identifica solo i problemi per cui lo stesso componente è configurato più volte nella stessa modalità di esecuzione (o combinazione di runmodes).

#### Non Compliant Code {#non-compliant-code-osgi}

```+ apps
  + projectA
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
  + projectB
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

#### Compliant Code {#compliant-code-osgi}

```+ apps
  + shared-config
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

### Config and Install Folders Should Only Contain OSGi Nodes {#oakpal-config-install}

**Chiave**: Configandinstallshouldonlycontainosginodes

**Tipo**: Bug

**Gravità**: Principale

**Poiché**: Versione 2019.6.0

For security reasons, paths containing */config/ and /install/* are only readable by administrative users in AEM and should be used only for OSGi configuration and OSGi bundles. L&#39;inserimento di altri tipi di contenuto in percorsi che contengono questi segmenti provoca un comportamento dell&#39;applicazione che varia in modo unzionalmente tra gli utenti amministrativi e non amministrativi.

### Packages Should Not Overlap {#oakpal-no-overlap}

**Chiave**: Packageoverlaps

**Tipo**: Bug

**Gravità**: Principale

**Poiché**: Versione 2019.6.0

Similar to the *Packages Should Not Contain Duplicate OSGi Configurations* this is a common problem on complex projects where the same node path is written to by multiple separate content packages. Quando si utilizzano le dipendenze del pacchetto di contenuto per garantire un risultato coerente, è meglio evitare la sovrapposizione completa.
