---
title: Test della qualità del codice
description: Scopri come funziona il test di qualità del codice delle pipeline e come può migliorare la qualità delle distribuzioni.
exl-id: 6a574858-a30e-4768-bafc-8fe79f928294
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '2764'
ht-degree: 90%

---


# Test di qualità del codice {#code-quality-testing}

Scopri come funziona il test della qualità del codice delle pipeline e come può migliorare la qualità delle distribuzioni.

## Introduzione {#introduction}

Durante l’esecuzione della pipeline, il software acquisisce una serie di metriche. Queste metriche vengono quindi confrontate con gli indicatori prestazioni chiave (KPI) definiti dal proprietario dell’azienda. Oppure vengono confrontati con gli standard impostati da Adobe Managed Services.

I risultati sono riportati mediante l’utilizzo di un sistema di valutazione a tre livelli.

## Valutazioni a tre livelli {#three-tiered-ratings}

La pipeline è composta da tre gate:

* Qualità del codice
* Test delle prestazioni
* Test di sicurezza

Per ciascuno di questi gate, esiste una struttura a tre livelli per i problemi identificati dal gate.

* **Critico**: si tratta di problemi che causano un errore immediato della pipeline.
* **Importante**: si tratta di problemi che causano la sospensione dell’esecuzione della pipeline. Un Responsabile della distribuzione, un Project Manager o un proprietario dell’azienda possono ignorare questi problemi. In caso affermativo, la pipeline procede come previsto. In alternativa, possono accettare i problemi, causando l’arresto della pipeline con un errore. Se si ignorano errori importanti si innesca un [timeout](/help/using/code-deployment.md#timeouts).
* **Info**: si tratta di problemi forniti a scopo puramente informativo e che non hanno alcun impatto sull’esecuzione della pipeline.

>[!NOTE]
>
>In una pipeline di sola qualità del codice, non è possibile ignorare importanti errori nel gate di qualità del codice, poiché il passaggio del test della qualità del codice è l’ultimo passaggio della pipeline.

## Test di qualità del codice {#code-quality-testing-step}

Questo passaggio di test valuta la qualità del codice dell’applicazione, che è lo scopo principale di una pipeline dedicata esclusivamente alla qualità del codice. Viene eseguito immediatamente dopo la fase di build in tutte le pipeline non di produzione e di produzione. Per ulteriori informazioni, vai alla [Configurazione delle pipeline non di produzione](/help/using/non-production-pipelines.md).

Il test di qualità del codice esegue la scansione del codice sorgente per garantire che soddisfi determinati criteri di qualità.

Il software lo implementa tramite una combinazione di analisi SonarQube, un controllo a livello di pacchetto di contenuti con OakPAL e una convalida del Dispatcher tramite il relativo strumento di ottimizzazione.

Sono presenti più di 100 regole che combinano regole Java generiche e regole specifiche per AEM. Alcune delle regole specifiche per l&#39;AEM vengono create in base alle best practice indicate dal team ingegneristico dell&#39;AEM e sono denominate [Regole per la qualità del codice personalizzato](/help/using/custom-code-quality-rules.md).

>[!TIP]
>
>È possibile scaricare l&#39;elenco completo delle regole [utilizzando questo collegamento](/help/assets/CodeQuality-rules-latest-AMS.xlsx).

I risultati dei test di qualità del codice sono forniti come valutazione, come sintetizzato in questa tabella.

| Nome | Definizione | Categoria | Soglia di errore |
|--- |--- |--- |--- |
| Valutazione della sicurezza | A = Nessuna vulnerabilità<br/>B = Almeno 1 vulnerabilità minore<br/>C = Almeno 1 vulnerabilità grave<br/>D = Almeno 1 vulnerabilità critica<br/>E = Almeno 1 vulnerabilità bloccante | Critico | &lt; B |
| Valutazione dell’affidabilità | A = Nessun bug<br/>B = Almeno 1 bug minore <br/>C = Almeno 1 bug grave<br/>D = Almeno 1 bug critico<br/>E = Almeno 1 bug bloccante | Importante | &lt; C |
| Valutazione della manutenzione | Definito dal costo residuo della correzione dei code smell come percentuale del tempo già trascorso nell’applicazione<br/><ul><li>A = &lt;= 5%</li><li>B = 6-10%</li><li>C = 11-20%</li><li>D = 21-50%</li><li>E = > 50%</li></ul> | Importante | &lt; A |
| Copertura | Definito da una combinazione di copertura di righe e copertura di condizioni dello unit test utilizzando la formula: <br/>`Coverage = (CT + CF + LC) / (2 * B + EL)`  <ul><li>`CT` = condizioni già valutate come `true` almeno una volta durante l’esecuzione degli unit test</li><li>`CF` = condizioni già valutate come `false` almeno una volta durante l’esecuzione degli unit test</li><li>`LC` = righe coperte = lines_to_cover - uncovered_lines</li><li>`B` = numero totale di condizioni</li><li>`EL` = numero totale di righe eseguibili (lines_to_cover)</li></ul> | Importante | &lt; 50% |
| Unit test ignorati | Numero di unit test ignorati | Info | > 1 |
| Problemi aperti | Tipi di problemi generali: vulnerabilità, bug e code smell | Info | > 0 |
| Righe duplicate | Definito come il numero di righe presenti in blocchi duplicati. Un blocco di codice si considera duplicato nelle seguenti condizioni.<br>Progetti non Java:<ul><li>Devono esserci almeno 100 token successivi e duplicati.</li><li>Tali token devono essere distribuiti, per lo meno, come segue: </li><li>30 righe di codice per COBOL </li><li>20 righe di codice per ABAP </li><li>10 righe di codice per altri linguaggi</li></ul>Progetti Java:<ul></li><li> Devono essere presenti almeno 10 istruzioni successive e duplicate indipendentemente dal numero di token e righe.</li></ul>Le differenze nel rientro e nelle stringhe letterali vengono ignorate quando si rilevano duplicati. | Info | > 1% |
| Compatibilità Cloud Service | Numero di problemi di compatibilità Cloud Service identificati | Info | > 0 |

>[!NOTE]
>
>Per informazioni più dettagliate, consulta le [Definizioni delle metriche di SonarQube](https://docs.sonarsource.com/sonarqube/latest/user-guide/code-metrics/metrics-definition/).

>[!NOTE]
>
>Per ulteriori informazioni sulle regole per la qualità del codice personalizzato eseguite da [!UICONTROL Cloud Manager], vedere [Regole per la qualità del codice personalizzato](custom-code-quality-rules.md).

### Gestione dei falsi positivi {#dealing-with-false-positives}

Il processo di scansione della qualità non è perfetto e talvolta identifica erroneamente problemi che in realtà non sono critici. Questo scenario è noto come falso positivo.

In questi casi, il codice sorgente può essere annotato con l’annotazione Java standard `@SuppressWarnings` che specifica l’ID della regola come attributo dell’annotazione. Tra i falsi positivi comuni si annovera ad esempio il caso in cui la regola SonarQube per rilevare le password hardcoded può essere molto rigida riguardo al modo in cui una password hardcoded viene identificata.

Il codice riportato di seguito è abbastanza comune in un progetto AEM, che presenta un codice per la connessione a un servizio esterno.

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube genera in questo caso una vulnerabilità bloccante. Dopo aver rivisto il codice, riconosci che tale errore non è una vulnerabilità e puoi annotare il codice con l’ID della regola appropriata.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Tuttavia, se in realtà il codice era:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

la soluzione corretta è rimuovere la password hardcoded.

>[!NOTE]
>
>È consigliabile rendere l’annotazione `@SuppressWarnings` più specifica possibile. In altre parole, annota solo l’istruzione o il blocco specifico che causa il problema. Tuttavia, è possibile aggiungere annotazioni a livello di classe. Ciò consente un’eliminazione più ampia degli avvisi.

## Test di sicurezza {#security-testing}

[!UICONTROL Cloud Manager] esegue le verifiche di integrità e sicurezza AEM esistenti nell’ambiente di staging dopo la distribuzione e segnala lo stato tramite l’interfaccia utente. I risultati vengono aggregati da tutte le istanze AEM nell’ambiente.

Questi stessi controlli di integrità possono essere eseguiti in qualsiasi momento tramite la console web o il dashboard operazioni.

Se una delle istanze segnala un errore per una determinata verifica di integrità, la verifica di integrità dell’intero ambiente non riesce. Come nel caso dei test di qualità e prestazioni del codice, questi controlli di integrità sono organizzati in categorie e segnalati utilizzando il sistema di gating a tre livelli. L’unica distinzione è che non esiste alcuna soglia nel caso di test di sicurezza. Tutti i controlli di integrità sono superati o falliti.

Nella tabella seguente sono elencati i controlli di integrità.

| Nome | Implementazione del controllo di integrità | Categoria |
|---|---|---|
| La Compatibilità Attach API di firewall deserializzazione è in uno stato accettabile. | [Compatibilità Attach Api di firewall deserializzazione](https://experienceleague.adobe.com/it/docs/experience-manager-65/content/security/mitigating-serialization-issues#security) | Critico |
| Il firewall deserializzazione è funzionale. | [Firewall deserializzazione funzionale](https://experienceleague.adobe.com/it/docs/experience-manager-65/content/security/mitigating-serialization-issues#security) | Critico |
| Il firewall deserializzazione è caricato. | [Firewall deserializzazione caricato](https://experienceleague.adobe.com/it/docs/experience-manager-65/content/security/mitigating-serialization-issues#security) | Critico |
| L’implementazione `AuthorizableNodeName` non espone l’ID autorizzabile nel nome/percorso del nodo. | [Generazione nome nodo autorizzabile](https://experienceleague.adobe.com/it/docs/experience-manager-65/content/security/security-checklist#security) | Critico |
| Le password predefinite sono state modificate. | [Account di accesso predefiniti](https://experienceleague.adobe.com/it/docs/experience-manager-65/content/security/security#users-and-groups-in-aem) | Critico |
| Il servlet GET predefinito di Sling è protetto dagli attacchi DOS. | Sling Get Servlet | Critico |
| Il gestore JavaScript di Sling è configurato in modo appropriato. | Gestore JavaScritp di Sling | Critico |
| Il gestore di script JSP di Sling è configurato in modo appropriato. | Gestore di script Jsp di Sling | Critico |
| SSL è configurato correttamente. | Configurazione SSL | Critico |
| Non è stato trovato alcun criterio di profilo utente chiaramente non sicuro. | Accesso predefinito profilo utente | Critico |
| Il filtro Sling Referrer è configurato per prevenire attacchi CSRF. | [Filtro referrer sling](https://experienceleague.adobe.com/it/docs/experience-manager-65/content/security/security-checklist#security) | Importante |
| Il manager libreria HTML Adobe Granite è configurato in modo appropriato. | Configurazione manager libreria CQ HTML | Importante |
| Il bundle di supporto CRXDE è disabilitato. | Supporto CRXDE | Importante |
| Il bundle e il servlet Sling DavEx sono disabilitati. | Verifica stato DavEx | Importante |
| Il contenuto di esempio non è installato. | Pacchetti contenuti di esempio | Importante |
| Il filtro di richiesta WCM e il filtro di debug WCM sono disabilitati. | [Configurazione filtri WCM](https://experienceleague.adobe.com/it/docs/experience-manager-65/content/implementing/deploying/configuring/osgi-configuration-settings#configuring) | Importante |
| Il bundle e il servlet Sling WebDAV sono configurati in modo appropriato. | Verifica stato WebDAV | Importante |
| Il server Web è configurato per impedire il clickjacking. | Configurazione server Web | Importante |
| La replica non sta utilizzando l’utente `admin`. | Utenti replica e trasporto | Info |

## Test delle prestazioni {#performance-testing}

### AEM Sites {#aem-sites}

Cloud Manager esegue il test delle prestazioni per i programmi di AEM Sites. Il test delle prestazioni viene eseguito per circa 30 minuti attivando gli utenti virtuali (contenitori) che simulano gli utenti effettivi per accedere alle pagine in ambienti di staging e simulare il traffico. Queste pagine vengono trovate utilizzando un crawler.

#### Utenti virtuali {#virtual-users}

In Cloud Manager gli utenti o i contenitori virtuali vengono attivati in base ai KPI (tempo di risposta e visualizzazioni pagina/min) impostati dal ruolo **Proprietario azienda**. Questi KPI vengono impostati durante la [creazione o modifica del programma](/help/getting-started/program-setup.md).

In base ai KPI definiti, verranno attivati fino a 10 contenitori che simulano gli utenti effettivi. Le pagine selezionate per il test vengono suddivise e assegnate a ogni utente virtuale.

#### Crawler {#crawler}

Prima dell’inizio della fase di test di 30 minuti, Cloud Manager eseguirà la ricerca per indicizzazione dell’ambiente di staging utilizzando un set di uno o più URL di seed configurati dal Customer Success Engineer. Partendo da questi URL, l’HTML di ogni pagina viene ispezionato e i collegamenti vengono attraversati in modalità di ampiezza.

* Per impostazione predefinita, questo processo di ricerca per indicizzazione è limitato a un massimo di 5000 pagine.
* Il numero massimo di pagine da sottoporre a test può essere sovrascritto impostando la [variabile di pipeline](/help/getting-started/build-environment.md#pipeline-variables) `CM_PERF_TEST_CRAWLER_MAX_PAGES`.
   * I valori consentiti sono `2000` - `7000`.
* Le richieste del crawler hanno un timeout fisso di 10 secondi.

#### Set di pagine per il test {#page-sets}

Tre set di pagine selezionano le pagine. Cloud Manager utilizza i registri di accesso dalle istanze AEM in ambienti di produzione e di staging per determinare i seguenti bucket.

* **Pagine live popolari**: assicura che vengano testate le pagine più popolari a cui la clientela accede in tempo reale. Cloud Manager legge il registro di accesso e determina le prime 25 pagine più visitate dalla clientela in tempo reae per generare un elenco di quelle principali`Popular Live Pages`. L’intersezione di queste pagine che sono presenti anche nell’ambiente di staging vengono quindi sottoposte a ricerca per indicizzazione nell’ambiente di staging.

* **Altre pagine live**: assicura che vengano testate le pagine che non rientrano nelle prime 25 pagine live più popolari, che possono non essere popolari, ma che è importante testare. Simili alle pagine live popolari, queste vengono estratte dal registro di accesso e devono essere presenti anche nell’ambiente di staging.

* **Nuove pagine**: testa le nuove pagine che possono essere state distribuite solo nell’area di staging e non ancora nella produzione, ma che è necessario testare.

##### Distribuzione del traffico tra i set di pagine selezionati {#distribution-of-traffic}

Puoi scegliere da uno a tutti e tre i set nella scheda **Test** della [configurazione pipeline](/help/using/production-pipelines.md). La distribuzione del traffico si basa sul numero di set selezionati. In altre parole, se sono selezionati tutti e tre, il 33% del totale delle visualizzazioni di pagina viene destinato a ogni set. Se ne sono selezionati due, il 50% viene indirizzato a ciascun set. Se ne è selezionato uno, il 100% del traffico viene indirizzato a tale set.

Consideriamo questo esempio.

* Abbiamo una suddivisione 50/50 tra le pagine live più popolari e i nuovi set di pagine.
* Non vengono utilizzate altre pagine live.
* Il nuovo set di pagine contiene 3000 pagine.
* I KPI per le *visualizzazioni di pagina al minuto* sono impostati su 200.

Nel periodo di test di 30 minuti:

* Ognuna delle 25 pagine del set di pagine popolari live viene visitata 120 volte: `((200 * 0.5) / 25) * 30 = 120`
* Ognuna delle 3000 pagine del nuovo set di pagine verrà visitata una volta: `((200 * 0.5) / 3000) * 30 = 1`

#### Test e report {#testing-reporting}

Cloud Manager esegue un test delle prestazioni per i programmi AEM Sites richiedendo le pagine come utente non autenticato per impostazione predefinita sul server di pubblicazione dello staging per un periodo di test di 30 minuti. Misura le metriche generate dall’utente virtuale (tempo di risposta, tasso di errore, visualizzazioni al minuto e così via) per ogni pagina e varie metriche a livello di sistema (CPU, memoria, dati di rete) per tutte le istanze.

Nella tabella seguente viene riepilogata la matrice dei test di prestazione utilizzando il sistema di verifica a tre livelli.

| Metrica | Categoria | Soglia di errore |
|---|---|---|
| Frequenza di errori di richiesta pagina | Critico | >= 2% |
| Frequenza di utilizzo della CPU | Critico | >= 80% |
| Tempo di attesa I/O del disco | Critico | >= 50% |
| Tempo di risposta del 95° percentile | Importante | >= KPI a livello di programma |
| Tempo di risposta al picco | Importante | >= 18 secondi |
| Visualizzazioni pagina al minuto | Importante | &lt; KPI a livello di programma |
| Utilizzo della larghezza di banda del disco | Importante | >= 90% |
| Utilizzo della larghezza di banda di rete | Importante | >= 90% |
| Richieste al minuto | Info | >= 6000 |

Consulta [Test delle prestazioni autenticati](#authenticated-performance-testing) per ulteriori dettagli sull&#39;utilizzo dell&#39;autenticazione di base per i test delle prestazioni per Sites e Assets.

>[!NOTE]
>
>Durante il test vengono monitorate sia le istanze di authoring che quelle di pubblicazione. Se non viene ottenuta alcuna metrica per un’istanza, tale metrica viene segnalata come sconosciuta e il passaggio corrispondente non riuscirà.

#### Test delle prestazioni autenticati {#authenticated-performance-testing}

Se necessario,la clientela AMS con siti autenticati può specificare un nome utente e una password che Cloud Manager utilizzerà per accedere al sito web durante il test delle prestazioni dei siti.

Il nome utente e la password sono specificati come variabili della pipeline con i nomi `CM_PERF_TEST_BASIC_USERNAME` e `CM_PERF_TEST_BASIC_PASSWORD`.

Il nome utente viene archiviato in una variabile `string` e la password viene archiviata in una variabile `secretString`. Se entrambe le variabili vengono specificate, ogni richiesta del crawler dei test delle prestazioni e degli utenti virtuali del test conterrà queste credenziali come autenticazione di base HTTP.

Per impostare queste variabili utilizzando Cloud Manager CLI, esegui:

```shell
$ aio cloudmanager:set-pipeline-variables <pipeline id> --variable CM_PERF_TEST_BASIC_USERNAME <username> --secret CM_PERF_TEST_BASIC_PASSWORD <password>
```

Per informazioni su come utilizzare l&#39;API, consulta la documentazione sulle [variabili della pipeline utente](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/patchPipelineVariables).

### AEM Assets {#aem-assets}

Cloud Manager esegue il test delle prestazioni per i programmi AEM Assets caricando ripetutamente le risorse per 30 minuti.

#### Requisito di onboarding {#onboarding-requirement}

Per il test delle prestazioni di Assets, il Customer Success Engineer crea un utente e una password `cloudmanager` durante l’onboarding dell’authoring nell’ambiente di staging. I passaggi del test delle prestazioni richiedono un utente chiamato `cloudmanager` e la password associata impostata dal CSE.

Questo metodo deve rimanere nell’istanza di authoring senza modificarne le autorizzazioni. Se lo modifichi o lo rimuovi, il test delle prestazioni di Assets potrebbe non riuscire.

#### Immagini e Assets per il test {#assets-for-testing}

I clienti possono caricare le proprie risorse da testare. Questo processo può essere eseguito dalla schermata **Configurazione della pipeline** o **Modifica**. Sono supportati formati immagine comuni come JPEG, PNG, GIF e BMP insieme ai file Photoshop, Illustrator e Postscript.

Se non viene caricata alcuna immagine, Cloud Manager utilizza un’immagine e documenti PDF predefiniti per il test.

#### Distribuzione di Assets per il test {#distribution-of-assets}

La distribuzione del numero di risorse di ciascun tipo caricate al minuto è impostata nella schermata **Configurazione della pipeline** o **Modifica**.

Ad esempio, se utilizzi una suddivisione 70/30 e sono presenti 10 risorse caricate al minuto, verranno caricate 7 immagini e 3 documenti al minuto.

#### Test e report {#testing-and-reporting}

Cloud Manager crea una cartella sull’istanza di authoring utilizzando il nome utente e la password configurati dal CSE. Le risorse vengono quindi caricate nella cartella utilizzando una libreria open-source. I test eseguiti dal passaggio di test di Assets vengono scritti utilizzando una [libreria open source](https://github.com/adobe/toughday2). Il tempo di elaborazione di ciascuna risorsa e di varie metriche a livello di sistema vengono misurati nell’arco della durata del test di 30 minuti. Questa funzione consente di caricare sia immagini che documenti PDF.

>[!TIP]
>
>Per ulteriori informazioni, consulta [Configurare le pipeline di produzione](/help/using/production-pipelines.md). Consulta [Configurazione del programma](/help/getting-started/program-setup.md) per scoprire come impostare il programma e definire i KPI.

### Grafici dei risultati dei test delle prestazioni {#performance-testing-results-graphs}

Nella finestra di dialogo **Test delle prestazioni** sono disponibili diverse metriche.

![Elenco delle metriche](/help/assets/understand_test-results-screen1.png)

I pannelli delle metriche possono essere espansi per visualizzare un grafico, fornire un collegamento a un download o entrambi.

![Metriche espanse come grafico](/help/assets/screen_shot_2018-09-05at83933pm.png)

Questa funzionalità è disponibile per le metriche seguenti.

* **Utilizzo CPU**: un grafico dell’utilizzo della CPU durante il periodo del test

* **Tempo di attesa I/O del disco**: un grafico del tempo di attesa I/O del disco durante il periodo del test

* **Frequenza errori pagina**: un grafico degli errori di pagina al minuto durante il periodo di test
   * File CSV in cui sono elencate le pagine che hanno prodotto un errore durante il test

* **Utilizzo della larghezza di banda del disco**: un grafico dell&#39;utilizzo della larghezza di banda del disco durante il periodo di test

* **Utilizzo della larghezza di banda di rete**: un grafico dell&#39;utilizzo della larghezza di banda di rete durante il periodo di test

* **Tempo di risposta al picco**: un grafico del tempo di risposta di picco al minuto durante il periodo di test

* **Tempo di risposta del 95° percentile**: un grafico del tempo di risposta del 95° percentile al minuto durante il periodo di test
   * Un file CSV che elenca le pagine il cui il tempo di risposta del 95° percentile ha superato l’indicatore KPI definito

## Ottimizzazione dell’analisi dei pacchetti di contenuti {#content-package-scanning-optimization}

Come parte del processo di analisi della qualità, Cloud Manager esegue l’analisi dei pacchetti di contenuti prodotti dalla build Maven. Per accelerare questo processo, Cloud Manager offre delle ottimizzazioni che risultano efficaci quando si osservano determinati vincoli per la creazione dei pacchetti.

La chiave per l’ottimizzazione è per i progetti che producono un singolo pacchetto “all”, contenente altri pacchetti di contenuti prodotti dalla build e contrassegnati come ignorati. Quando Cloud Manager rileva questo scenario, anziché decomprimere il pacchetto “all”, scansiona i singoli pacchetti di contenuti e li ordina in base alle dipendenze. Consideriamo ad esempio il seguente output di build.

* `all/myco-all-1.0.0-SNAPSHOT.zip` (pacchetto di contenuti)
* `ui.apps/myco-ui.apps-1.0.0-SNAPSHOT.zip` (pacchetto di contenuti ignorato)
* `ui.content/myco-ui.content-1.0.0-SNAPSHOT.zip` (pacchetto di contenuti ignorato)

Se gli unici elementi all’interno di `myco-all-1.0.0-SNAPSHOT.zip` sono i due pacchetti di contenuto ignorato, allora i due pacchetti incorporati sono analizzati al posto del pacchetto di contenuto “all”.

Per i progetti che producono decine di pacchetti incorporati, è comprovato che questa ottimizzazione consente di risparmiare fino a 10 minuti per ogni esecuzione della pipeline.

Un caso speciale può verificarsi quando il pacchetto di contenuti “all” include una combinazione di pacchetti di contenuti e bundle OSGi ignorati. Ad esempio, se `myco-all-1.0.0-SNAPSHOT.zip` contiene i due pacchetti incorporati precedentemente menzionati oltre a uno o più bundle OSGi, allora viene creato un nuovo pacchetto di contenuti minimo con i soli bundle OSGi. Questo pacchetto viene sempre denominato `cloudmanager-synthetic-jar-package` e i bundle contenuti vengono inseriti in `/apps/cloudmanager-synthetic-installer/install`.

>[!NOTE]
>
>* Questa ottimizzazione non influisce sui pacchetti distribuiti in AEM.
>* La corrispondenza tra pacchetti di contenuti incorporati e ignorati si basa sui nomi dei file. Questa ottimizzazione ha esito negativo se più pacchetti di contenuti ignorati condividono lo stesso nome di file o se il nome del file cambia durante l’incorporamento.
