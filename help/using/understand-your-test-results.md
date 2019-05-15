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
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Comprendere i risultati del test {#understand-your-test-results}

Durante il **processo di pipeline** , diverse metriche vengono acquisite e confrontate con gli indicatori prestazioni chiave (KPI) definite dal proprietario aziendale, o con gli standard impostati dai servizi gestiti Adobe.

Vengono riportate utilizzando il sistema di bating a tre livelli come definito in questa sezione.

## Gate a tre gradi durante l&#39;esecuzione di una pipeline {#three-tier-gates-while-running-a-pipeline}

La pipeline contiene tre gate:

* Qualità codice
* Test delle prestazioni
* Test di sicurezza

Per ciascuno di questi gate, esiste una struttura a tre gradi per i problemi identificati dal gate.

* **Critical** - These are issues identified by the gate which cause an immediate failure of the pipeline.
* **Importante** : questi sono problemi identificati dal gate che provocano la messa in pausa della pipeline. Un manager distribuzione, un manager progetto o un proprietario aziendale può ignorare i problemi, nel qual caso la pipeline procede oppure possono accettare i problemi, nel qual caso la pipeline si interrompe con un errore.
* **Informazioni** : sono problemi identificati dal gate che sono forniti esclusivamente a scopo informativo e non hanno alcun impatto sull&#39;esecuzione della pipeline.

## Test qualità del codice {#code-quality-testing}

Come parte della pipeline, il codice sorgente viene analizzato per assicurare che le distribuzioni soddisfino determinati criteri di qualità. Attualmente, viene implementato da sonarqube. Oltre 100 regole combinano regole Java generiche e regole specifiche per AEM. La tabella seguente riepiloga la valutazione per i criteri di verifica:

| Nome | Definizione | Categoria | Soglia non riuscita |
|--- |--- |--- |--- |
| Valutazione della sicurezza | A = 0 Vulnerability <br/>B = at least 1 Minor Vulnerabilità<br/> C = Almeno 1 Vulnerabilità principale <br/>D = Almeno 1 Vulnerabilità critica <br/>E = Almeno 1 Vulnerabilità di blocco | Critico | &lt; B |
| Valutazione affidabilità | A = 0 Bug <br/>B = at least 1 Children Bug <br/>C = at least 1 Main Bug <br/>D = at least 1 Critical Bug E = at least 1 Blocker Bug | Importante | &lt; C |
| Valutazione della capacità | Costo di correzione non riuscito per l&#39;odore del codice: <br/><ul><li>&lt; = 5% dell&#39;ora che è già entrato nell&#39;applicazione, la valutazione è A </li><li>Tra 6 e 10% la valutazione è una B </li><li>Tra 11 e 20% la valutazione è C </li><li>tra 21 e 50% la valutazione è D</li><li>anything over 50% is an E</li></ul> | Importante | &lt; A |
| Copertura | Un mix di copertura della riga di prova e copertura condizione tramite questa formula: <br/>`Coverage = (CT + CF + LC)/(2*B + EL)`<br/>dove: CT = condizioni che sono state valutate come «true» almeno una volta durante l&#39;esecuzione di test <br/>di unità CF = che sono stati valutati come «false» almeno una volta durante l&#39;esecuzione di test <br/>unità LC = lines lines = lines <br/><br/> B = numero totale di condizioni <br/>EL = numero totale di righe eseguibili (lines_ to_ cover) (lines_ to_ cover) | Importante | &lt; 50% |
| Test unità ignorati | Numero di test unità ignorati. | Info | &gt; 1 |
| Apri problemi | Tipi di problemi complessivi - Vulnerabilità, bug e porzioni di codice | Info | &gt; 1 |
| Linee duplicate | Numero di righe coinvolte in blocchi duplicati. <br/>Perché un blocco di codice venga considerato duplicato: <br/><ul><li>**Progetti non Java:**</li><li>Ci devono essere almeno 100 token consecutivi e duplicati.</li><li>I token devono essere distribuiti almeno su: </li><li>30 righe di codice per COBOL </li><li>20 righe di codice per ABAP </li><li>10 righe di codice per altre lingue</li><li>**Progetti Java:**</li><li> Devono esserci almeno 10 istruzioni successive e duplicate, indipendentemente dal numero di token e righe.</li></ul> <br/>Le differenze di rientro e di stringa letterali vengono ignorate durante la rilevazione delle duplicazioni. | Info | &gt; 1% |


>[!NOTE]
>
>Per definizioni [più dettagliate, fate riferimento alle Definizioni](https://docs.sonarqube.org/display/SONAR/Metric+Definitions) delle metriche.


Potete scaricare l&#39;elenco delle regole qui [sonarqube-rules.xlsx](assets/sonarqube-rules.xlsx)

>[!NOTE]
>
>Per ulteriori informazioni sulle regole sonarqube eseguite da [!UICONTROL Cloud Manager], consultate Regole di qualità codice [personalizzate](custom-code-quality-rules.md).

### Gestione dei falsi positivi {#dealing-with-false-positives}

Il processo di scansione della qualità non è perfetto e a volte identificherà in modo non corretto i problemi che non sono realmente problematici. Questo è denominato &quot;falso positivo&quot;.

In questi casi, il codice sorgente può essere annotato con l&#39;annotazione Java `@SuppressWarnings` standard che specifica l&#39;ID della regola come attributo di annotazione. Ad esempio, un problema comune sta nel fatto che la regola sonarqube per rilevare password hardcoded può essere aggressiva su come viene identificato una password hardcoded.

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
>Sebbene sia consigliabile rendere l&#39; `@SuppressWarnings` annotazione il più specifica possibile, ad esempio annotando solo l&#39;istruzione o il blocco specifico, è possibile inserire annotazioni a livello di classe.

## Test di sicurezza {#security-testing}

[!UICONTROL Cloud Manager] esegue le verifiche ***Heath Security Heath verifica*** esistenti dopo la distribuzione e segnala lo stato tramite l&#39;interfaccia utente. I risultati vengono aggregati da tutte le istanze AEM nell&#39;ambiente.

Se un qualsiasi **tipo di istanze** segnala un errore di verifica dello stato, l&#39;intero **ambiente** non riesce. Come per la qualità del codice e il test delle prestazioni, questi controlli sanitari sono organizzati in categorie e segnalati mediante il sistema di tre livelli. L&#39;unica distinzione consiste nel fatto che non esiste alcuna soglia nel caso di test di sicurezza. Tutti i controlli dello stato sono semplicemente passati o non vanno a buon fine.

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

## Test delle prestazioni {#performance-testing}

*I test delle prestazioni* vengono [!UICONTROL Cloud Manager] implementati mediante un test di 30 minuti.

Durante la configurazione della pipeline, il manager distribuzione può stabilire il volume di traffico da indirizzare a ogni bucket.

Per ulteriori informazioni sui controlli degli intervalli, da [Configura la pipeline CI/CD](configuring-pipeline.md).

>[!NOTE]
>
>Per configurare il programma e definire i KPI, consultate [Configurazione del programma](setting-up-program.md).

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

### Grafici dei risultati di test prestazioni {#performance-testing-results-graphs}

Sono stati aggiunti nuovi grafici e opzioni di download alla finestra di dialogo Risultati test prestazioni.

Quando apri la finestra di dialogo Test prestazioni, i pannelli delle metriche possono essere espansi per visualizzare un grafico, fornire un collegamento a un download o entrambi.

Per [!UICONTROL Cloud Manager] la release 2018.7.0, questa funzionalità è disponibile per le metriche seguenti:

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

