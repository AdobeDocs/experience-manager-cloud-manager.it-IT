---
title: Regole di qualità codice personalizzate
seo-title: Regole di qualità codice personalizzate
description: Segui questa pagina per informazioni sulle regole sonarqube personalizzate eseguite da Cloud Manager.
seo-description: Segui questa pagina per informazioni sulle regole sonarqube personalizzate eseguite da Adobe Experience Manager Cloud Manager.
uuid: a 7 feb 465-1982-46 be -9 e 57-e 67 b 59849579
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: utilizzo
discoiquuid: d 2338 c 74-3278-49 e 6-a 186-6 ef 62362509 f
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Regole di qualità codice personalizzate {#custom-code-quality-rules}

Questa pagina descrive le regole sonarqube personalizzate eseguite da Cloud Manager. Queste regole aumentano le regole standard sonarqube con le best practice di AEM Engineering.

>[!NOTE]
>
>Gli esempi di codice forniti qui sono solo a scopo illustrativo.

## Regole sonarqube {#sonarqube-rules}

La sezione seguente evidenzia le regole sonarqube:

### Non utilizzare funzioni potenzialmente pericolose {#do-not-use-potentially-dangerous-functions}

**Chiave**: Cqrules: CWE -676

**Tipo**: Vulnerabilità

**Gravità**: Principale

**Poiché**: Versione 2018.4.0

I metodi ***Thread. stop ()*** e ***Thread. stop ()*** possono produrre problemi difficili e, in alcuni casi, vulnerabilità di sicurezza. Il loro utilizzo deve essere rigorosamente monitorato e convalidato. In generale, il passaggio del messaggio è un modo più sicuro per raggiungere obiettivi simili.

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

**Chiave**: Cqrules: CWE -134

**Tipo**: Vulnerabilità

**Gravità**: Principale

**Poiché**: Versione 2018.4.0

L&#39;utilizzo di una stringa di formato da un&#39;origine esterna (come un parametro di richiesta o un contenuto generato dall&#39;utente) può esporre un&#39;applicazione a attacchi di negazione di servizi. In alcune circostanze una stringa di formato potrebbe essere controllata esternamente, ma è consentita solo dalle fonti affidabili.

#### Codice non conforme {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text");
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### Le richieste HTTP devono disporre sempre di socket e timeout di connessione {#http-requests-should-always-have-socket-and-connect-timeouts}

**Chiave**: Cqrules: Connectiontimeoutmechanism

**Tipo**: Bug

**Gravità**: Critico

**Poiché**: Versione 2018.6.0

Quando si eseguono richieste HTTP dall&#39;interno di un&#39;applicazione AEM, è importante assicurarsi che i timeout corretti siano configurati per evitare inutili dispendio di thread. Purtroppo, il comportamento predefinito del client HTTP predefinito di Java (java.net.Ht tpurlconnection) e il client Apache HTTP utilizzato comunemente non devono mai essere timeout, pertanto i timeout devono essere impostati in modo esplicito. Inoltre, come procedura ottimale, questi timeout non devono superare i 60 secondi.

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

### Le API prodotto con @ providertype non devono essere implementate o estese dai clienti {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

**Chiave**: CQBP -84, dipendenze CQBP -84

**Tipo**: Bug

**Gravità**: Critico

**Poiché**: Versione 2018.7.0

L&#39;API AEM contiene interfacce Java e classi che possono essere utilizzate, ma non implementate, mediante codice personalizzato. Ad esempio, l&#39;interfaccia *com.day.cq.wc m. api. La pagina* è progettata per essere implementata solo da ***AEM***.

Quando vengono aggiunti nuovi metodi a queste interfacce, questi metodi aggiuntivi non influiscono sul codice esistente che utilizza tali interfacce e, di conseguenza, l&#39;aggiunta di nuovi metodi a queste interfacce è considerata compatibile con le versioni precedenti. Tuttavia, se il codice ***personalizzato implementa*** una di queste interfacce, il codice personalizzato ha introdotto un rischio di compatibilità retrocompatibile per il cliente.

Le interfacce (e le classi) destinate unicamente all&#39;implementazione da parte di AEM sono annotate con *org. osgi. annotation. versioning. providertype* (o, in alcuni casi, con annotazione *legacy spete. bnd. annotdertype*). Questa regola identifica i casi in cui tale interfaccia è implementata (o una classe estesa) tramite codice personalizzato.

#### Codice non conforme {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### Gli oggetti resourceresolver devono essere sempre chiusi {#resourceresolver-objects-should-always-be-closed}

**Chiave**: Cqrules: CQBP -72

**Tipo**: Odore codice

**Gravità**: Principale

**Poiché**: Versione 2018.4.0

Gli oggetti resourceresolver ottenuti da resourceresolverfactory consumano risorse di sistema. Sebbene siano disponibili misure per reclamare queste risorse quando un resourceresolver non è più in uso, è più efficiente chiudere esplicitamente qualsiasi oggetto resourceresolver aperto chiamando il metodo close ().

Un errore relativamente comune è che gli oggetti resourceresolver creati utilizzando una sessione JCR esistente non devono essere chiusi in modo esplicito o che in tal modo chiuderanno la sessione JCR sottostante. Questo non è il caso, a prescindere dalla modalità di apertura di un resourceresolver, qualora non venga più utilizzato. Poiché resourceresolver implementa l&#39;interfaccia chiusibile, è anche possibile utilizzare la sintassi try-with-resources invece di richiamare esplicitamente close ().

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

### Non utilizzare i percorsi servlet Sling per registrare servlet {#do-not-use-sling-servlet-paths-to-register-servlets}

**Chiave**: Cqrules: CQBP -75

**Tipo**: Odore codice

**Gravità**: Principale

**Poiché**: Versione 2018.4.0

Come descritto nella documentazione [Sling](http://sling.apache.org/documentation/the-sling-engine/servlets.html), i servlet di binding per percorsi vengono scoraggiati. I servlet associati al percorso non possono utilizzare controlli di accesso JCR standard e, di conseguenza, richiedono un ulteriore rigonfiamento della sicurezza. Anziché utilizzare servlet associati al percorso, si consiglia di creare nodi nell&#39;archivio e di registrare i servlet in base al tipo di risorsa.

#### Codice non conforme {#non-compliant-code-5}

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

### Evitare di avere un&#39;istruzione di registro seguita da un&#39;istruzione throw {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

**Chiave**: Cqrules: CQBP -44—Successivelylogandthrow

**Tipo**: Odore codice

**Gravità**: Secondario

**Poiché**: Versione 2018.4.0

Un altro pattern comune da evitare consiste nel registrare un messaggio e quindi su un&#39;eccezione. In genere ciò indica che il messaggio di eccezione verrà duplicato nei file di registro.

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

### Evitare di effettuare l&#39;accesso a Informazioni durante la gestione di richieste GET o HEAD {#avoid-logging-at-info-when-handling-get-or-head-requests}

**Chiave**: Cqrules: CQBP -44—Loginfoingetorheadrequests

**Tipo**: Odore codice

**Gravità**: Secondario

In generale, il livello di registro INFO deve essere utilizzato per delimitare azioni importanti e, per impostazione predefinita, AEM è configurato per effettuare il login a livello INFO o superiore. I metodi GET e HEAD devono essere solo operazioni di sola lettura e quindi non costituiscono interventi importanti. L&#39;accesso a livello INFO in risposta alle richieste GET o HEAD creerà probabilmente un rumore di registro significativo, rendendo più difficile identificare le informazioni utili nei file di registro. L&#39;accesso durante la gestione delle richieste GET o HEAD dovrebbe essere a livello di AVVISO o di ERRORE quando si verifica un errore o a livelli DEBUG o TRACE se sono utili informazioni di risoluzione dei problemi più rigorose.

>[!CAUTION]
>
>Questo non vale per l&#39;accesso a access. log-type per ogni richiesta.

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

### Non utilizzare Exception. getmessage () come primo parametro di un&#39;istruzione logging {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

**Chiave**: Cqrules: CQBP -44—Exceptiongetmessageisfirstlogparam

**Tipo**: Odore codice

**Gravità**: Secondario

**Poiché**: Versione 2018.4.0

Come procedura ottimale, i messaggi del registro devono fornire informazioni contestuali su dove si è verificato un&#39;eccezione nell&#39;applicazione. Anche se il contesto può essere determinato anche utilizzando le tracce dello stack, in generale il messaggio di registro diventerà più semplice da leggere e comprendere. Di conseguenza, quando si registra un&#39;eccezione, è consigliabile utilizzare il messaggio dell&#39;eccezione come messaggio di registro. Il messaggio di eccezione conterrà ciò che è andato a buon fine; il messaggio di registro sarà utilizzato per indicare a un lettore di registro ciò che l&#39;applicazione stava realizzando quando si è verificata l&#39;eccezione. Il messaggio di eccezione continuerà a essere registrato; specificando il vostro messaggio, i registri saranno più facili da comprendere.

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

### La registrazione dei blocchi catch dovrebbe essere a livello di AVVISO o di ERRORE {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}

**Chiave**: Cqrules: CQBP -44—Wrongloglevelincatchblock

**Tipo**: Odore codice

**Gravità**: Secondario

**Poiché**: Versione 2018.4.0

Come suggerisce il nome, le eccezioni Java devono essere sempre utilizzate in circostanze *eccezionali* . Di conseguenza, quando viene rilevata un&#39;eccezione, è importante assicurarsi che i messaggi del registro siano collegati al livello appropriato: ALERT o ERROR. In questo modo i messaggi vengono visualizzati correttamente nei registri.

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

### Non stampare le tracce di stack nella console {#do-not-print-stack-traces-to-the-console}

**Chiave**: Cqrules: CQBP -44—Exceptionprintstacktrace

**Tipo**: Odore codice

**Gravità**: Secondario

**Poiché**: Versione 2018.4.0

Come indicato, il contesto è fondamentale per comprendere i messaggi di registro. L&#39;utilizzo di Exception. printstacktrace () causa l **&#39;output** della traccia dello stack nel flusso di errore standard, perdendo in tal modo tutto il contesto. Inoltre, in un&#39;applicazione multi-thread come AEM se più eccezioni vengono stampate utilizzando in parallelo questo metodo, le tracce dello stack possono sovrapporsi che generano confusione significativa. Le eccezioni devono essere registrate solo tramite il framework di registrazione.

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

### Non restituire Output a Output standard o Errore standard {#do-not-output-to-standard-output-or-standard-error}

**Chiave**: Cqrules: CQBP -44—loglevelconsoleprinters

**Tipo**: Odore codice

**Gravità**: Secondario

**Poiché**: Versione 2018.4.0

La registrazione in AEM deve essere sempre realizzata tramite il framework di registrazione (SLF 4 J). L&#39;output diretto direttamente ai flussi di errore standard o standard perde le informazioni strutturali e contestuali fornite dal framework di registrazione e può, in alcuni casi, causare problemi di prestazioni.

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

### Evitare hardcoded /apps e /libs percorsi {#avoid-hardcoded-apps-and-libs-paths}

**Chiave**: Cqrules: CQBP -71

**Tipo**: Odore codice

**Gravità**: Secondario

**Poiché**: Versione 2018.4.0

In generale, i percorsi che iniziano con /libs e /apps non devono essere codificati in quanto i percorsi a cui fanno riferimento sono più comunemente memorizzati come percorsi rispetto al percorso di ricerca Sling (che per impostazione predefinita è impostata su /libs,/app). L&#39;utilizzo del percorso assoluto potrebbe introdurre lievi difetti che verrebbero visualizzati solo successivamente nel ciclo di vita del progetto.

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
