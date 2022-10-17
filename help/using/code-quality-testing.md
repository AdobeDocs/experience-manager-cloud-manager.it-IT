---
title: Test della qualità del codice
description: Scopri come funziona il test della qualità del codice delle pipeline e come può migliorare la qualità delle distribuzioni.
exl-id: 6a574858-a30e-4768-bafc-8fe79f928294
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: ht
source-wordcount: '2863'
ht-degree: 100%

---


# Test della qualità del codice {#code-quality-testing}

Scopri come funziona il test della qualità del codice delle pipeline e come può migliorare la qualità delle distribuzioni.

## Introduzione {#introduction}

Durante l’esecuzione della pipeline, varie metriche vengono acquisite e confrontate con gli indicatori prestazioni chiave (KPI, Key Performance Indicator) definiti dal proprietario business o dagli standard impostati da Adobe Managed Services.

Questi sono segnalati utilizzando un sistema di valutazione a tre livelli.

## Valutazioni a tre livelli {#three-tiered-ratings}

La pipeline è composta da tre gate:

* Qualità del codice
* Test delle prestazioni
* Test di sicurezza

Per ciascuno di questi gate, esiste una struttura a tre livelli per i problemi identificati dal gate.

* **Critico**: si tratta di problemi che causano un errore immediato della pipeline.
* **Importante**: si tratta di problemi che fanno sì che la pipeline entri in uno stato di pausa. Un Responsabile della distribuzione, un Project manager o un Proprietario business può ignorare i problemi, nel qual caso la pipeline procede, oppure può accettare i problemi, nel qual caso la pipeline si arresta con un errore. Se si ignorano errori importanti si innesca un [timeout.](/help/using/code-deployment.md#timeouts)
* **Info**: si tratta di problemi che vengono forniti a scopo puramente informativo e che non hanno alcun impatto sull’esecuzione della pipeline.

>[!NOTE]
>
>In una pipeline di sola qualità del codice, non è possibile ignorare importanti errori nel gate di qualità del codice, poiché il passaggio del test della qualità del codice è l’ultimo passaggio della pipeline.

## Test della qualità del codice {#code-quality-testing-step}

Questo passaggio valuta la qualità del codice dell’applicazione, che è lo scopo principale di una pipeline di sola qualità del codice, e viene eseguito subito dopo il passaggio di compilazione in tutte le pipeline non di produzione e di produzione. Per ulteriori informazioni, consulta il documento [Configurazione delle pipeline di non produzione](/help/using/non-production-pipelines.md).

Il test di qualità del codice esegue l’analisi del codice sorgente per garantire che soddisfi determinati criteri di qualità. Questa funzione viene implementata tramite una combinazione di analisi SonarQube, controllo a livello di pacchetto di contenuti tramite OakPAL e convalida del dispatcher tramite lo strumento di ottimizzazione del Dispatcher.

Sono presenti più di 100 regole che combinano regole Java generiche e regole specifiche per AEM. Alcune delle regole specifiche per AEM vengono create in base alle best practice di AEM Engineering e sono denominate [regole per la qualità del codice personalizzato.](/help/using/custom-code-quality-rules.md)

>[!TIP]
>
>È possibile scaricare l’elenco completo delle regole [utilizzando questo collegamento.](/help/assets/CodeQuality-rules-latest-AMS.xlsx)

I risultati dei test di qualità del codice sono forniti come valutazione, come sintetizzato in questa tabella.

| Nome | Definizione | Categoria | Soglia di errore |
|--- |--- |--- |--- |
| Valutazione della sicurezza | A = Nessuna vulnerabilità<br/>B = Almeno 1 vulnerabilità minore<br/>C = Almeno 1 vulnerabilità grave<br/>D = Almeno 1 vulnerabilità critica<br/>E = Almeno 1 vulnerabilità bloccante | Critico | &lt; B |
| Valutazione dell’affidabilità | A = Nessun bug<br/>B = Almeno 1 bug minore <br/>C = Almeno 1 bug grave<br/>D = Almeno 1 bug critico<br/>E = Almeno 1 bug bloccante | Importante | &lt; C |
| Valutazione della manutenzione | Definita dal costo residuo di correzione dei code smell, espressa come percentuale del tempo già dedicato all’applicazione<br/><ul><li>A = &lt;=5%</li><li>B = 6-10%</li><li>C = 11-20%</li><li>D = 21-50%</li><li>E = >50%</li></ul> | Importante | &lt; A |
| Copertura | Definita da una combinazione di copertura di righe di codice del test di unità e di copertura delle condizioni utilizzando la formula: <br/>`Coverage = (CT + CF + LC) / (2 * B + EL)`  <ul><li>`CT` = Condizioni valutate come `true` almeno una volta durante l’esecuzione dei test di unità</li><li>`CF` = Condizioni valutate come `false` almeno una volta durante l&#39;esecuzione dei test di unità</li><li>`LC` = Linee coperte = line_to_cover - uncover_lines</li><li>`B` = numero totale di condizioni</li><li>`EL` = numero totale di righe eseguibili (lines_to_cover)</li></ul> | Importante | &lt; 50% |
| Test di unità ignorati | Numero di test di unità ignorati | Info | > 1 |
| Problemi aperti | Tipi di problemi generali: vulnerabilità, bug e code smell | Info | > 0 |
| Linee duplicate | Definito come il numero di righe coinvolte nei blocchi duplicati. Un blocco di codice viene considerato duplicato nelle seguenti condizioni.<br>Progetti non Java:<ul><li>Ci dovrebbero essere almeno 100 token successivi e duplicati.</li><li>Tali token devono essere distribuiti almeno: </li><li>30 righe di codice per COBOL </li><li>20 righe di codice per ABAP </li><li>10 righe di codice per altre lingue</li></ul>Progetti Java:<ul></li><li> Devono essere presenti almeno 10 istruzioni successive e duplicate indipendentemente dal numero di token e righe.</li></ul>Le differenze nel rientro e nelle stringhe letterali vengono ignorate quando si rilevano duplicati. | Info | > 1% |
| Compatibilità Cloud Service | Numero di problemi di compatibilità Cloud Service identificati | Info | > 0 |

>[!NOTE]
>
>Fai riferimento a [Definizioni delle metriche di SonarQube](https://docs.sonarqube.org/latest/user-guide/metric-definitions/) per informazioni più dettagliate.

>[!NOTE]
>
>Per ulteriori informazioni sulle regole di qualità del codice personalizzato eseguite da [!UICONTROL Cloud Manager], consulta il documento [Regole per la qualità del codice personalizzato.](custom-code-quality-rules.md)

### Gestione dei falsi positivi {#dealing-with-false-positives}

Il processo di analisi della qualità non è perfetto e talvolta identificherà erroneamente problemi che non sono effettivamente tali. Tali problemi sono denominati falsi positivi.

In questi casi, il codice sorgente può essere annotato con annotazione Java standard `@SuppressWarnings` che specifica l’ID della regola come attributo di annotazione. Ad esempio, un falso positivo comune è che la regola SonarQube rilevi che le password hardcoded siano aggressive riguardo al modo in cui viene identificata una password hardcoded.

Il codice seguente è abbastanza comune in un progetto AEM, che ha un codice per la connessione a un servizio esterno.

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube originerà quindi una vulnerabilità di blocco. Ma dopo aver esaminato il codice, riconosci che non si tratta di una vulnerabilità e puoi annotare il codice con l’ID regola appropriato.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Tuttavia, se il codice era effettivamente questo:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Quindi la soluzione corretta è quella di rimuovere la password hardcoded.

>[!NOTE]
>
>Anche se è una best practice fare l’annotazione `@SuppressWarnings` nel modo più specifico possibile (ad esempio, annotare solo l’istruzione o il blocco specifici che causano il problema), è possibile annotare a livello di classe.

## Test di sicurezza {#security-testing}

[!UICONTROL Cloud Manager] esegue i controlli di integrità e sicurezza AEM esistenti nell’ambiente di staging dopo la distribuzione e segnala lo stato tramite l’interfaccia utente. I risultati vengono aggregati da tutte le istanze AEM nell’ambiente.

Questi stessi controlli di integrità possono essere eseguiti in qualsiasi momento tramite la console web o il dashboard operazioni.

Se una delle istanze segnala un errore per una determinata verifica di integrità, la verifica di integrità dell’intero ambiente non riesce. Come nel caso dei test di qualità e prestazioni del codice, questi controlli di integrità sono organizzati in categorie e segnalati utilizzando il sistema di gating a tre livelli. L’unica distinzione è che non esiste alcuna soglia nel caso di test di sicurezza. Tutti i controlli di integrità sono superati o falliti.

Nella tabella seguente sono elencati i controlli di integrità.

| Nome | Implementazione del controllo di integrità | Categoria |
|---|---|---|
| La Compatibilità Attach API di firewall deserializzazione è in uno stato accettabile. | [Compatibilità Attach Api di firewall deserializzazione](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html?lang=it#security) | Critico |
| Il firewall deserializzazione è funzionale. | [Firewall deserializzazione funzionale](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html?lang=it#security) | Critico |
| Il firewall deserializzazione è caricato. | [Firewall deserializzazione caricato](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html?lang=it#security) | Critico |
| L’implementazione `AuthorizableNodeName` non espone l’ID autorizzabile nel nome/percorso del nodo. | [Generazione nome nodo autorizzabile](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html?lang=it#security) | Critico |
| Le password predefinite sono state modificate. | [Account di accesso predefiniti](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html?lang=it#users-and-groups-in-aem) | Critico |
| Il servlet GET predefinito di Sling è protetto dagli attacchi DOS. | Sling Get Servlet | Critico |
| Il gestore Java Script di Sling è configurato in modo appropriato. | Sling Java Script Handler | Critico |
| Il gestore di script JSP di Sling è configurato in modo appropriato. | Gestore di script Jsp di Sling | Critico |
| SSL è configurato correttamente. | Configurazione SSL | Critico |
| Non è stato trovato alcun criterio di profilo utente chiaramente non sicuro. | Accesso predefinito profilo utente | Critico |
| Il filtro Referrer Sling è configurato per prevenire attacchi CSRF. | [Filtro referrer sling](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html?lang=it#security) | Importante |
| Il manager libreria HTML Adobe Granite è configurato in modo appropriato. | Configurazione manager libreria CQ HTML | Importante |
| Il bundle di supporto CRXDE è disabilitato. | Supporto CRXDE | Importante |
| Il bundle e il servlet Sling DavEx sono disabilitati. | Verifica stato DavEx | Importante |
| Il contenuto di esempio non è installato. | Pacchetti contenuti di esempio | Importante |
| Il filtro di richiesta WCM e il filtro di debug WCM sono disabilitati. | [Configurazione filtri WCM](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/osgi-configuration-settings.html?lang=it#configuring) | Importante |
| Il bundle e il servlet Sling WebDAV sono configurati in modo appropriato. | Verifica stato WebDAV | Importante |
| Il server Web è configurato per impedire il clickjacking. | Configurazione server Web | Importante |
| La replica non sta utilizzando l’utente `admin`. | Utenti replica e trasporto | Info |

## Test delle prestazioni {#performance-testing}

### AEM Sites {#aem-sites}

Cloud Manager esegue il test delle prestazioni per i programmi di AEM Sites. Il test delle prestazioni viene eseguito per circa 30 minuti attivando gli utenti virtuali (contenitori) che simulano gli utenti effettivi per accedere alle pagine in ambienti di staging e simulare il traffico. Queste pagine vengono trovate utilizzando un crawler.

#### Utenti virtuali {#virtual-users}

Il numero di utenti o contenitori virtuali generati da Cloud Manager è determinato dai KPI (tempo di risposta e visualizzazioni pagina/min) definiti dall’utente con il ruolo **Proprietario business** durante la [creazione o modifica del programma.](/help/getting-started/program-setup.md) In base ai KPI definiti, verranno attivati fino a 10 contenitori che simulano gli utenti effettivi. Le pagine selezionate per il test vengono suddivise e assegnate a ogni utente virtuale.

#### Crawler {#crawler}

Prima dell’inizio del periodo di test di 30 minuti, Cloud Manager eseguirà la ricerca per indicizzazione dell’ambiente di staging utilizzando un set di uno o più URL di seed configurati dal Customer Success Engineer. Partendo da questi URL, l’HTML di ogni pagina viene ispezionato e i collegamenti vengono attraversati in modalità di ampiezza.

* Per impostazione predefinita, questo processo di ricerca per indicizzazione è limitato a un massimo di 5000 pagine.
* Il numero massimo di pagine da sottoporre a test può essere sovrascritto impostando la [variabile di ambiente](/help/getting-started/build-environment.md#environment-variables) `MAX_PAGES`.
   * I valori consentiti sono `2000` - `7000`.
* Le richieste del crawler hanno un timeout fisso di 10 secondi.

#### Set di pagine per il test {#page-sets}

Le pagine sono selezionate da tre set di pagine. Cloud Manager utilizza i registri di accesso dalle istanze AEM in ambienti di produzione e di staging per determinare i seguenti bucket.

* **Pagine Live popolari**: questa opzione è selezionata per assicurarsi che vengano testate le pagine più popolari a cui accedono i clienti live. Cloud Manager legge il registro di accesso e determina le prime 25 pagine più visitate dai clienti live per generare un elenco di `Popular Live Pages` principali. L’intersezione di queste che sono presenti anche nell’ambiente di pre-produzione viene quindi sottoposta a ricerca per indicizzazione nell’ambiente di staging.

* **Altre pagine live**: questa opzione viene selezionata per assicurarsi che vengano testate le pagine che non rientrano nelle prime 25 pagine live più popolari, che possono non essere popolari, ma che sono importanti da testare. Simile alle pagine live più popolari, queste vengono estratte dal registro di accesso e devono essere presenti anche nell&#39;ambiente di staging.

* **Nuove pagine**: questa opzione viene selezionata per testare le nuove pagine che possono essere state distribuite solo nell’area di staging non ancora in produzione, ma che è necessario testare.

##### Distribuzione del traffico tra set di pagine selezionati {#distribution-of-traffic}

Puoi scegliere da uno a tutti e tre i set nella scheda **Test** della [configurazione della pipeline.](/help/using/production-pipelines.md) La distribuzione del traffico si basa sul numero di set selezionati. In altre parole, se sono selezionati tutti e tre, il 33% del totale delle visualizzazioni di pagina viene destinato a ogni set. Se ne sono selezionati due, il 50% viene indirizzato a ciascun set. Se ne è selezionato uno, il 100% del traffico viene indirizzato a tale set.

Consideriamo questo esempio.

* Abbiamo una suddivisione 50/50 tra le pagine live più popolari e i nuovi set di pagine.
* Non vengono utilizzate altre pagine live.
* Il nuovo set di pagine contiene 3000 pagine.
* Il KPI per le visualizzazioni di pagina al minuto è impostato su 200.

Nel periodo di test di 30 minuti:

* Ognuna delle 25 pagine del set di pagine popolari live viene visitata 120 volte: `((200 * 0.5) / 25) * 30 = 120`
* Ognuna delle 3000 pagine del nuovo set di pagine verrà visualizzata una volta: `((200 * 0.5) / 3000) * 30 = 1`

#### Test e reporting {#testing-reporting}

Cloud Manager esegue un test delle prestazioni per i programmi AEM Sites richiedendo le pagine come utente non autenticato per impostazione predefinita sul server di pubblicazione dello staging per un periodo di test di 30 minuti. Misura le metriche generate dall’utente virtuale (tempo di risposta, tasso di errore, visualizzazioni al minuto, ecc.) per ogni pagina e varie metriche a livello di sistema (CPU, memoria, dati di rete) per tutte le istanze.

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

Consulta la sezione [Test delle prestazioni autenticati](#authenticated-performance-testing) per ulteriori informazioni sull’utilizzo dell’autenticazione di base per i test delle prestazioni per Sites e Assets.

>[!NOTE]
>
>Durante il periodo di test vengono monitorate sia le istanze di authoring che quelle di pubblicazione. Se non viene ottenuta alcuna metrica per un’istanza, tale metrica viene segnalata come sconosciuta e il passaggio corrispondente non riuscirà.

#### Test delle prestazioni autenticati {#authenticated-performance-testing}

Se necessario, i clienti AMS con siti autenticati possono specificare un nome utente e una password che Cloud Manager utilizzerà per accedere al sito web durante il test delle prestazioni dei siti.

Il nome utente e la password sono specificati come variabili della pipeline con i nomi `CM_PERF_TEST_BASIC_USERNAME` e `CM_PERF_TEST_BASIC_PASSWORD`.

Il nome utente deve essere archiviato in una variabile di `string` e la password deve essere archiviata in una variabile `secretString`. Se vengono specificati entrambi, ogni richiesta del crawler dei test delle prestazioni e degli utenti virtuali del test conterrà queste credenziali come autenticazione HTTP Basic.

Per impostare queste variabili utilizzando Cloud Manager CLI, esegui:

```shell
$ aio cloudmanager:set-pipeline-variables <pipeline id> --variable CM_PERF_TEST_BASIC_USERNAME <username> --secret CM_PERF_TEST_BASIC_PASSWORD <password>
```

Fai riferimento alla documentazione API [Variabili della pipeline utente di patch](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/patchPipelineVariables) per scoprire come utilizzare l’API.

### AEM Assets {#aem-assets}

Cloud Manager esegue test delle prestazioni per i programmi AEM Assets caricando ripetutamente le risorse per un periodo di test di 30 minuti.

#### Requisiti di onboarding {#onboarding-requirement}

Per il test delle prestazioni delle risorse, il CSE (Customer Success Engineer) creerà un utente e una password `cloudmanager` durante l’onboarding dell’authoring nell’ambiente di staging. I passaggi del test delle prestazioni richiedono un utente chiamato `cloudmanager` e la password associata impostata dal CSE. Questo non deve essere rimosso dall&#39;istanza di authoring né le relative autorizzazioni modificate. Questa operazione potrebbe non riuscire nel test delle prestazioni delle risorse.

#### Immagini e risorse per il test {#assets-for-testing}

I clienti possono caricare le proprie risorse da testare. Questa operazione può essere eseguita dalla schermata **Configurazione della pipeline** o **Modifica**. Sono supportati formati immagine comuni come JPEG, PNG, GIF e BMP insieme ai file Photoshop, Illustrator e Postscript.

Se non viene caricata alcuna immagine, Cloud Manager utilizzerà un’immagine e un documento PDF predefiniti per il test.

#### Distribuzione delle risorse da sottoporre a test {#distribution-of-assets}

La distribuzione del numero di risorse di ciascun tipo caricate al minuto è impostata nella schermata **Configurazione della pipeline** o **Modifica**.

Ad esempio, se utilizzi una suddivisione 70/30 e sono presenti 10 risorse caricate al minuto, verranno caricate 7 immagini e 3 documenti al minuto.

#### Test e reporting {#testing-and-reporting}

Cloud Manager creerà una cartella sull’istanza di authoring utilizzando il nome utente e la password come configurato dal CSE. Le risorse vengono quindi caricate nella cartella utilizzando una libreria open-source. I test eseguiti dal passaggio di test delle risorse vengono scritti utilizzando una [libreria open source.](https://github.com/adobe/toughday2) Il tempo di elaborazione di ciascuna risorsa e di varie metriche a livello di sistema vengono misurati nell’arco della durata del test di 30 minuti. Questa funzione consente di caricare sia immagini che documenti PDF.

>[!TIP]
>
>Fare riferimento al documento [Configurare le pipeline di produzione](/help/using/production-pipelines.md) per ulteriori informazioni. Consulta il documento [Configurazione del programma](/help/getting-started/program-setup.md) per scoprire come impostare il programma e definire i KPI.

### Grafici dei risultati del test delle prestazioni {#performance-testing-results-graphs}

Sono disponibili diverse metriche nella **Finestra di dialogo Test delle prestazioni**

![Elenco delle metriche](/help/assets/understand_test-results-screen1.png)

I pannelli delle metriche possono essere espansi per visualizzare un grafico, fornire un collegamento a un download o entrambi.

![Metriche espanse come grafico](/help/assets/screen_shot_2018-09-05at83933pm.png)

Questa funzionalità è disponibile per le metriche seguenti.

* **Utilizzo CPU**: un grafico dell’utilizzo della CPU durante il periodo del test

* **Tempo di attesa I/O del disco**: un grafico del tempo di attesa I/O del disco durante il periodo del test

* **Frequenza errori pagina**: un grafico degli errori di pagina al minuto durante il periodo di test
   * Un file CSV in cui sono elencate le pagine che hanno prodotto un errore durante il test

* **Utilizzo della larghezza di banda del disco**: un grafico dell&#39;utilizzo della larghezza di banda del disco durante il periodo di test

* **Utilizzo della larghezza di banda di rete**: un grafico dell&#39;utilizzo della larghezza di banda di rete durante il periodo di test

* **Tempo di risposta al picco**: un grafico del tempo di risposta di picco al minuto durante il periodo di test

* **Tempo di risposta del 95° percentile**: un grafico del tempo di risposta del 95° percentile al minuto durante il periodo di test
   * Un file CSV che elenca le pagine il cui il tempo di risposta del 95° percentile ha superato l’indicatore KPI definito

## Ottimizzazione dell’analisi dei pacchetti di contenuto {#content-package-scanning-optimization}

Come parte del processo di analisi della qualità, Cloud Manager esegue l’analisi dei pacchetti di contenuto prodotti dalla build Maven. Cloud Manager offre ottimizzazioni per accelerare questo processo, che sono efficaci quando vengono osservati determinati vincoli per la creazione di pacchetti. La più significativa è l’ottimizzazione eseguita per i progetti che producono un singolo pacchetto di contenuto, generalmente denominato pacchetto “all”, che contiene una serie di altri pacchetti di contenuti prodotti dalla build, contrassegnati come ignorati. Quando Cloud Manager rileva questo scenario, anziché decomprimere il pacchetto “all”, i singoli pacchetti di contenuto vengono analizzati direttamente e ordinati in base alle dipendenze. Ad esempio, considera il seguente output di build.

* `all/myco-all-1.0.0-SNAPSHOT.zip` (pacchetto di contenuto)
* `ui.apps/myco-ui.apps-1.0.0-SNAPSHOT.zip` (pacchetto contenuto ignorato)
* `ui.content/myco-ui.content-1.0.0-SNAPSHOT.zip` (pacchetto contenuto ignorato)

Se gli unici elementi all’interno di `myco-all-1.0.0-SNAPSHOT.zip` sono i due pacchetti di contenuto ignorato, allora i due pacchetti incorporati verranno analizzati al posto del pacchetto di contenuto “all”.

Per i progetti che producono decine di pacchetti incorporati, è stato dimostrato che questa ottimizzazione risparmia fino a 10 minuti per esecuzione della pipeline.

Un caso speciale può verificarsi quando il pacchetto di contenuti “all” contiene una combinazione di pacchetti di contenuti ignorati e bundle OSGi. Ad esempio, se `myco-all-1.0.0-SNAPSHOT.zip` contiene i due pacchetti incorporati precedentemente menzionati e uno o più bundle OSGi, allora viene creato un nuovo pacchetto di contenuto minimo con solo i bundle OSGi. Questo pacchetto viene sempre denominato `cloudmanager-synthetic-jar-package` e i bundle contenuti sono inseriti in `/apps/cloudmanager-synthetic-installer/install`.

>[!NOTE]
>
>* Questa ottimizzazione non influisce sui pacchetti distribuiti in AEM.
>* Poiché la corrispondenza tra i pacchetti di contenuto incorporati e i pacchetti di contenuto ignorati si basa sui nomi di file, questa ottimizzazione non può essere eseguita se più pacchetti di contenuto ignorati hanno esattamente lo stesso nome di file oppure se il nome di file viene modificato durante l’incorporazione.

