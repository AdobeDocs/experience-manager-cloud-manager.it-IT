---
title: Comprendere i risultati del test
seo-title: Comprendere i risultati del test
description: 'null'
seo-description: Segui questa pagina per informazioni su tre gate di livello durante l'esecuzione di una pipeline, la scansione di codice, le prestazioni e i test di sicurezza convalidati dal programma in Cloud Manager.
uuid: 93 caa 01 f -0 df 2-4 a 6 f -81 dc -23 dfee 24 dc 93
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: utilizzo
discoiquuid: 83299 ed 8-4 b 7 a -4 b 1 c-bd 56-1 bfc 7 e 7318 d 4
translation-type: tm+mt
source-git-commit: e8db535b09f0b273de2d3908a85176f38d307c80

---


# Understand your Test Results {#understand-your-test-results}

During the **Pipeline** process, a number of metrics are captured and compared to either the Key Performance Indicators (KPIs) defined by the business owner, or standards set by Adobe Managed Services.

Vengono riportate utilizzando il sistema di bating a tre livelli come definito in questa sezione.

## Three-Tier Gates while Running a Pipeline  {#three-tier-gates-while-running-a-pipeline}

La pipeline contiene tre gate:

* Qualità codice
* Test delle prestazioni
* Test di sicurezza

Per ciascuno di questi gate, esiste una struttura a tre gradi per i problemi identificati dal gate.

* **Critical** - These are issues identified by the gate which cause an immediate failure of the pipeline.
* **Importante** : questi sono problemi identificati dal gate che provocano la messa in pausa della pipeline. Un manager distribuzione, un manager progetto o un proprietario aziendale può ignorare i problemi, nel qual caso la pipeline procede oppure possono accettare i problemi, nel qual caso la pipeline si interrompe con un errore.
* **Informazioni** : sono problemi identificati dal gate che sono forniti esclusivamente a scopo informativo e non hanno alcun impatto sull&#39;esecuzione della pipeline.

>[!NOTE]
>
>In Pipeline solo codice, gli errori importanti nella gate di test della qualità del codice non possono essere sostituiti perché il passaggio Test qualità codice è il passaggio finale nella pipeline.

## Code Quality Testing {#code-quality-testing}

Come parte della pipeline, il codice sorgente viene analizzato per assicurare che le distribuzioni soddisfino determinati criteri di qualità. Attualmente questa funzione è implementata mediante una combinazione di sonarqube e di un esame a livello di pacchetto con oakpal. Oltre 100 regole combinano regole Java generiche e regole specifiche per AEM. La tabella seguente riepiloga la valutazione per i criteri di verifica:

| Nome | Definizione | Categoria | Soglia non riuscita |
|--- |--- |--- |--- |
| Valutazione della sicurezza | A = 0 Vulnerability <br/>B = at least 1 Minor Vulnerability<br/> C = at least 1 Major Vulnerability <br/>D = at least 1 Critical Vulnerability <br/>E = at least 1 Blocker Vulnerability | Critico | &lt; B |
| Valutazione affidabilità | A = 0 Bug <br/>B = at least 1 Minor Bug <br/>C = at least 1 Major Bug <br/>D = at least 1 Critical Bug E = at least 1 Blocker Bug | Importante | &lt; C |
| Valutazione della capacità | Outstanding remediation cost for code smells is: <br/><ul><li>&lt; = 5% dell&#39;ora che è già entrato nell&#39;applicazione, la valutazione è A </li><li>Tra 6 e 10% la valutazione è una B </li><li>Tra 11 e 20% la valutazione è C </li><li>tra 21 e 50% la valutazione è D</li><li>anything over 50% is an E</li></ul> | Importante | &lt; A |
| Copertura | A mix of unit test line coverage and condition coverage using this formula: <br/>`Coverage = (CT + CF + LC)/(2*B + EL)`  <br/>where: CT = conditions that have been evaluated to &#39;true&#39; at least once while running unit tests <br/>CF = conditions that have been evaluated to &#39;false&#39; at least once while running unit tests <br/>LC = covered lines = lines_to_cover - uncovered_lines <br/><br/> B = total number of conditions <br/>EL = total number of executable lines (lines_to_cover) | Importante | &lt; 50% |
| Test unità ignorati | Numero di test unità ignorati. | Info | &gt; 1 |
| Apri problemi | Tipi di problemi complessivi - Vulnerabilità, bug e porzioni di codice | Info | &gt; 1 |
| Linee duplicate | Numero di righe coinvolte in blocchi duplicati. <br/>Perché un blocco di codice venga considerato duplicato: <br/><ul><li>**Progetti non Java:**</li><li>Ci devono essere almeno 100 token consecutivi e duplicati.</li><li>I token devono essere distribuiti almeno su: </li><li>30 righe di codice per COBOL </li><li>20 righe di codice per ABAP </li><li>10 righe di codice per altre lingue</li><li>**Progetti Java:**</li><li> Devono esserci almeno 10 istruzioni successive e duplicate, indipendentemente dal numero di token e righe.</li></ul> <br/>Le differenze di rientro e di stringa letterali vengono ignorate durante la rilevazione delle duplicazioni. | Info | &gt; 1% |


>[!NOTE]
>
>Refer to [Metric Definitions](https://docs.sonarqube.org/display/SONAR/Metric+Definitions) for more detailed definitions.

You can download the list of rules here [code-quality-rules.xlsx](/help/using/assets/CodeQuality-Rules-new.xlsx)

>[!NOTE]
>
>To learn more about the custom code quality rules executed by [!UICONTROL Cloud Manager], please refer to [Custom Code Quality Rules](custom-code-quality-rules.md).

### Dealing with False Positives {#dealing-with-false-positives}

Il processo di scansione della qualità non è perfetto e a volte identificherà in modo non corretto i problemi che non sono realmente problematici. Questo è denominato &quot;falso positivo&quot;.

In these cases, the source code can be annotated with the standard Java `@SuppressWarnings` annotation specifying the rule ID as the annotation attribute. Ad esempio, un problema comune sta nel fatto che la regola sonarqube per rilevare password hardcoded può essere aggressiva su come viene identificato una password hardcoded.

Per esaminare un esempio specifico, questo codice sarebbe abbastanza comune in un progetto AEM con codice per la connessione ad alcuni servizi esterni:

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Sonarqube aumenterà quindi una vulnerabilità di blocco. Dopo aver rivisto il codice, l&#39;utente identifica che non si tratta di una vulnerabilità e può aggiungere annotazioni all&#39;ID della regola appropriato.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Tuttavia, se il codice è effettivamente stato questo:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

La soluzione corretta consiste nel rimuovere la password hardcoded.

>[!NOTE]
>
>While it is a best practice to make the `@SuppressWarnings` annotation as specific as possible, i.e. annotate only the specific statement or block causing the issue, it is possible to annotate at a class level.

## Security Testing {#security-testing}

[!UICONTROL Cloud Manager] esegue le verifiche ***Heath Security Heath verifica*** esistenti dopo la distribuzione e segnala lo stato tramite l&#39;interfaccia utente. I risultati vengono aggregati da tutte le istanze AEM nell&#39;ambiente.

If any of the **Instances** report a failure for a given health check, the entire **Environment** fails that health check. Come per la qualità del codice e il test delle prestazioni, questi controlli sanitari sono organizzati in categorie e segnalati mediante il sistema di tre livelli. L&#39;unica distinzione consiste nel fatto che non esiste alcuna soglia nel caso di test di sicurezza. Tutti i controlli dello stato sono semplicemente passati o non vanno a buon fine.

Nella tabella seguente sono elencati i controlli correnti:

| **Nome** | **Implementazione Health Check** | **Categoria** |
|---|---|---|
| Il firewall di deserializzazione che associa la preparazione API è in stato accettabile | Compatibilità Attach Api di firewall deserializzazione | Critico |
| Il firewall di deserializzazione funziona correttamente | Firewall deserializzazione funzionale | Critico |
| Il firewall di deserializzazione viene caricato | Firewall deserializzazione caricato | Critico |
| L&#39;implementazione authorizablenodename non espone l&#39;ID autorizzabile nel nome/percorso del nodo. | Generazione nome nodo autorizzabile | Critico |
| Le password predefinite sono state modificate | Account di login predefiniti | Critico |
| Sling default GET servlet is protected from DOS attacks. | Sling Get Servlet | Critico |
| Il dispatcher richiede richieste di filtro corrette | Configurazione dispatcher CQ | Critico |
| Adobe Granite HTML Library Manager è configurato correttamente | Configurazione manager libreria CQ HTML | Critico |
| Il gestore di script Java Java è configurato correttamente | Sling Java Script Handler | Critico |
| Il gestore di script Sling JSP è configurato correttamente | Sling JSP Script Handler | Critico |
| Il filtro Riferimento Sling è configurato per impedire attacchi CSRF | Sling Referrer Filter | Critico |
| SSL è configurato correttamente | Configurazione SSL | Critico |
| Non è stato trovato alcun criterio di profilo utente non sicuro | Accesso standard profilo utente | Critico |
| Pacchetto di supporto CRXDE disabilitato | Supporto CRXDE | Importante |
| Il bundle e il servlet Sling davex sono disattivati | Verifica stato DavEx | Importante |
| Il contenuto di esempio non è installato | Pacchetti contenuti di esempio | Importante |
| Entrambi i filtri richiesta WCM e WCM Debug Filter sono disattivati | Configurazione filtri WCM | Importante |
| Il bundle e il servlet webdav sono configurati in modo appropriato | Verifica stato WebDAV | Importante |
| Il server Web è configurato per impedire il clickjacking | Configurazione server Web | Importante |
| La replica non utilizza l&#39;utente «amministratore» | Utenti replica e trasporto | Info |

## Performance Testing {#performance-testing}

*I test delle prestazioni* vengono [!UICONTROL Cloud Manager] implementati mediante un test di 30 minuti.

Durante la configurazione della pipeline, il manager distribuzione può stabilire il volume di traffico da indirizzare a ogni bucket.

You can learn more about bucket controls, from [Configure your CI/CD Pipeline](configuring-pipeline.md).

>[!NOTE]
>
>To setup your program and define your KPIs, see [Setup your Program](setting-up-program.md).

La tabella seguente riepiloga la matrice di test delle prestazioni utilizzando il sistema di bating a tre livelli:

| **Metrica** | **Categoria** | **Soglia non riuscita** |
|---|---|---|
| Tasso errore richiesta pagina % | Critico | &gt;= 2% |
| Tasso di utilizzo CPU | Critico | &gt;= 80% |
| Tempo di attesa del disco | Critico | &gt;= 50% |
| 95 Percentile tempo risposta | Importante | &gt; = KPI a livello di programma |
| Picco di risposta picco | Importante | &gt; = 18 secondi |
| Visualizzazioni di pagina al minuto | Importante | &lt; KPI a livello di programma |
| Utilizzo della larghezza di banda del disco | Importante | &gt;= 90% |
| Utilizzo della larghezza di banda della rete | Importante | &gt;= 90% |
| Richieste per minuto | Info | &lt; 6000 |

### Performance Testing Results Graphs {#performance-testing-results-graphs}

Sono stati aggiunti nuovi grafici e opzioni di download alla finestra di dialogo Risultati test prestazioni.

Quando apri la finestra di dialogo Test prestazioni, i pannelli delle metriche possono essere espansi per visualizzare un grafico, fornire un collegamento a un download o entrambi.

For [!UICONTROL Cloud Manager] Release 2018.7.0, this functionality is available for the following metrics:

* **Utilizzo della CPU**
   * Un grafico dell&#39;utilizzo della CPU durante il periodo di prova.

* **Tempo di attesa I/O**
   * Un grafico di Tempo di attesa I/O del disco durante il periodo di prova.

* **Frequenza errore pagina**
   * Un grafico di errori di pagina al minuto durante il periodo di prova.
   * Pagine di elenco di file CSV che hanno generato un errore durante il test.

* **Utilizzo della larghezza di banda del disco**
   * Grafico dell&#39;utilizzo della larghezza di banda disco durante il periodo di prova.

* **Utilizzo della larghezza di banda della rete**
   * Grafico dell&#39;utilizzo della larghezza di banda della rete durante il periodo di prova.

* **Picco di risposta picco**
   * Un grafico del tempo di risposta picco per minuto durante il periodo di prova.

* **95 ° percentile tempo risposta**
   * Un grafico del 95 ° tempo di risposta percentile per minuto durante il periodo di prova.
   * Elenco di pagine CSV con un decimo tempo di risposta percentile superato il KPI definito.

Le immagini seguenti mostrano i grafici di prova delle prestazioni:

![](assets/understand_test-results-screen1.png)

![](assets/screen_shot_2018-09-05at83933pm.png)

