---
title: Comprendere i risultati del test
seo-title: Comprendere i risultati del test
description: Ulteriori informazioni sui gate a tre livelli durante l’esecuzione di una pipeline in Cloud Manager
seo-description: Segui questa pagina per scoprire i gate a tre livelli durante l’esecuzione di una pipeline, la scansione del codice, le prestazioni e i test di sicurezza che convalidano il programma in Cloud Manager.
uuid: 93caa01f-0df2-4a6f-81dc-23dfee24dc93
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: 83299ed8-4b7a-4b1c-bd56-1bfc7e7318d4
translation-type: tm+mt
source-git-commit: b5233e1932888b515d8dc26a6493cbd26686bc3c
workflow-type: tm+mt
source-wordcount: '1563'
ht-degree: 7%

---


# Comprendere i risultati del test {#understand-your-test-results}

Durante l’esecuzione della pipeline, vengono acquisite e confrontate diverse metriche con gli indicatori prestazioni chiave (KPI, Key Performance Indicators) definiti dal proprietario dell’azienda o con gli standard impostati da Adobe Managed Services.

Questi sono segnalati utilizzando il sistema di verifica a tre livelli come definito in questa sezione.

## Cancelli a tre livelli durante l’esecuzione di una pipeline {#three-tier-gates-while-running-a-pipeline}

La pipeline è composta da tre gate:

* Qualità del codice
* Test delle prestazioni
* Test di sicurezza

Per ciascuno di questi cancelli, esiste una struttura a tre livelli per i problemi identificati dal cancello.

* **Critico** : si tratta di problemi identificati dal gate che causano un errore immediato della pipeline.
* **Importante** : si tratta di problemi identificati dal gate che fanno sì che la pipeline entri in uno stato di pausa. Un manager distribuzione, un project manager o un proprietario business possono ignorare i problemi, nel qual caso la pipeline procede, oppure possono accettare i problemi, nel qual caso la pipeline si interrompe con un errore.
* **Informazioni** : si tratta di problemi identificati dal gate che sono forniti a scopo puramente informativo e non hanno alcun impatto sull’esecuzione della pipeline.

>[!NOTE]
>
>In una pipeline di solo qualità del codice, non è possibile ignorare importanti errori nel gate di test della qualità del codice, in quanto il passaggio di test della qualità del codice è l’ultimo passaggio della pipeline.

## Test di qualità del codice {#code-quality-testing}

Questo passaggio valuta la qualità del codice dell&#39;applicazione. Si tratta dell’obiettivo principale di una pipeline di sola qualità del codice e viene eseguita immediatamente dopo la fase di compilazione in tutte le pipeline non di produzione e produzione. Per ulteriori informazioni sui diversi tipi di pipeline, consulta [Configurazione della pipeline CI-CD](/help/using/configuring-pipeline.md) .

### Verifica della qualità del codice {#understanding-code-quality-testing}

Nel testing della qualità del codice, il codice sorgente viene analizzato per garantire che soddisfi alcuni criteri di qualità. Attualmente, questo è implementato da una combinazione di SonarQube, esame a livello di pacchetto di contenuti tramite OakPAL e convalida del dispatcher tramite lo strumento di ottimizzazione del Dispatcher. Ci sono più di 100 regole che combinano regole Java generiche e regole specifiche per AEM. Alcune delle regole specifiche AEM vengono create in base alle best practice di AEM Engineering e sono denominate [Regole per la qualità del codice personalizzato](/help/using/custom-code-quality-rules.md).

>[!NOTE]
>È possibile scaricare l&#39;elenco completo delle regole [qui](/help/using/assets/CodeQuality-rules-AMS.xlsx).

I risultati di questo passaggio vengono consegnati come *Valutazione*. La tabella seguente riassume le valutazioni per vari criteri di prova:

| Nome | Definizione | Categoria | Soglia errore |
|--- |--- |--- |--- |
| Valutazione della sicurezza | A = 0 Vulnerabilità <br/>B = almeno 1 Vulnerabilità minore<br/> C = almeno 1 Vulnerabilità principale <br/>D = almeno 1 Vulnerabilità critica <br/>E = almeno 1 Vulnerabilità del blocco | Critico | &lt; B |
| Valutazione dell&#39;affidabilità | A = 0 Bug <br/>B = almeno 1 Bug secondario <br/>C = almeno 1 Bug principale <br/>D = almeno 1 Bug critico<br/>E = almeno 1 Bug blocco | Importante | &lt; C |
| Valutazione della manutenzione | Il costo eccezionale di riparazione per gli odori di codice è: <br/><ul><li>&lt;> </li><li>tra il 6% e il 10% il rating è a B </li><li>tra l&#39;11 e il 20% il rating è a C </li><li>tra il 21 e il 50% il rating è un D</li><li>qualsiasi cosa superiore al 50% è un E</li></ul> | Importante | &lt; A |
| Copertura | Una combinazione di copertura della linea di prova di unità e copertura della condizione utilizzando questa formula: <br/>`Coverage = (CT + CF + LC)/(2*B + EL)` <br/>dove: CT = condizioni che sono state valutate come &quot;true&quot; almeno una volta durante l&#39;esecuzione di unit test <br/>CF = condizioni che sono state valutate come &quot;false&quot; almeno una volta durante l&#39;esecuzione di unit test <br/>LC = linee coperte = line_to_cover - uncover_lines <br/><br/> B = numero totale di condizioni <br/>EL = numero totale di linee eseguibili (lines_to_cover) | Importante | &lt; 50% |
| Test di unità ignorati | Numero di prove di unità saltate. | Info | > 1 |
| Problemi aperti | Tipi di problemi generali - Vulnerabilità, Bug e Odori di Codice | Info | > 0 |
| Linee duplicate | Numero di righe interessate dai blocchi duplicati. <br/>Affinché un blocco di codice sia considerato duplicato:  <br/><ul><li>**Progetti non Java:**</li><li>Ci dovrebbero essere almeno 100 token successivi e duplicati.</li><li>Tali gettoni dovrebbero essere distribuiti almeno su: </li><li>30 righe di codice per COBOL </li><li>20 righe di codice per ABAP </li><li>10 righe di codice per altre lingue</li><li>**Progetti Java:**</li><li> Ci dovrebbero essere almeno 10 istruzioni successive e duplicate indipendentemente dal numero di token e righe.</li></ul> <br/>Le differenze nel rientro e nei valori letterali stringa vengono ignorate durante il rilevamento di duplicati. | Info | > 1% |
| Compatibilità Cloud Service | Numero di problemi di compatibilità Cloud Service identificati. | Info | > 0 |


>[!NOTE]
>
>Per definizioni più dettagliate, fai riferimento a [Definizioni metriche](https://docs.sonarqube.org/display/SONAR/Metric+Definitions) .

>[!NOTE]
>
>Per ulteriori informazioni sulle regole per la qualità del codice personalizzato eseguite da [!UICONTROL Cloud Manager], fai riferimento a [Regole per la qualità del codice personalizzato](custom-code-quality-rules.md).

### Gestione dei falsi positivi {#dealing-with-false-positives}

Il processo di scansione della qualità non è perfetto e talvolta identificherà erroneamente problemi che non sono effettivamente problematici. Questo viene definito &quot;falso positivo&quot;.

In questi casi, il codice sorgente può essere annotato con l’annotazione Java standard `@SuppressWarnings` che specifica l’ID regola come attributo dell’annotazione. Ad esempio, un problema comune è che la regola SonarQube per rilevare le password codificate può essere aggressiva riguardo a come viene identificata una password hardcoded.

Per osservare un esempio specifico, questo codice è abbastanza comune in un progetto AEM con codice per la connessione a un servizio esterno:

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube solleverà quindi una vulnerabilità di blocco. Dopo aver esaminato il codice, identifichi che questa non è una vulnerabilità e puoi annotarla con l’ID regola appropriato.

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
>È buona norma rendere l’annotazione `@SuppressWarnings` il più specifica possibile, ovvero annotare solo l’istruzione o il blocco specifici che causa il problema, ma è possibile annotarla a livello di classe.

## Test di sicurezza {#security-testing}

[!UICONTROL Cloud Manager] esegue la fase  ***AEM Security Heath*** Checkson esistente dopo la distribuzione e segnala lo stato tramite l’interfaccia utente. I risultati vengono aggregati da tutte le istanze AEM nell’ambiente.

Se una delle **Istanze** segnala un errore per una determinata verifica dello stato di salute, l&#39;intero **Ambiente** non riesce a controllare lo stato di salute. Come per i test di qualità e prestazioni del codice, questi controlli di integrità sono organizzati in categorie e segnalati utilizzando il sistema di verifica a tre livelli. L&#39;unica distinzione è che non esiste alcuna soglia nel caso di test di sicurezza. Tutti i controlli sanitari sono semplicemente superati o falliti.

Nella tabella seguente sono elencati i controlli correnti:

| **Nome** | **Implementazione del controllo dello stato** | **Categoria** |
|---|---|---|
| Preparazione dell&#39;API dell&#39;attacco firewall di deserializzazione in uno stato accettabile | Compatibilità Attach Api di firewall deserializzazione | Critico |
| Il firewall di deserializzazione funziona | Firewall deserializzazione funzionale | Critico |
| Firewall di deserializzazione caricato | Firewall deserializzazione caricato | Critico |
| L&#39;implementazione AuthorizableNodeName non espone l&#39;ID autorizzabile nel nome/percorso del nodo. | Generazione nome nodo autorizzabile | Critico |
| Le password predefinite sono state modificate | Account di login predefiniti | Critico |
| Il servlet di GET predefinito Sling è protetto dagli attacchi DOS. | Sling Get Servlet | Critico |
| Il gestore Java Script Sling è configurato in modo appropriato | Sling Java Script Handler | Critico |
| Il gestore di script Sling JSP è configurato in modo appropriato | Sling JSP Script Handler | Critico |
| SSL è configurato correttamente | Configurazione SSL | Critico |
| Nessun criterio di profilo utente ovviamente non sicuro trovato | Accesso standard profilo utente | Critico |
| Il filtro Sling Referrer è configurato per prevenire attacchi CSRF | Sling Referrer Filter | Importante |
| Adobe Granite HTML Library Manager è configurato in modo appropriato | Configurazione manager libreria CQ HTML | Importante |
| Il bundle CRXDE Support è disabilitato | Supporto CRXDE | Importante |
| Il bundle e il servlet Sling DavEx sono disabilitati | Verifica stato DavEx | Importante |
| Contenuto di esempio non installato | Pacchetti contenuti di esempio | Importante |
| Il filtro di richiesta WCM e il filtro di debug WCM sono disabilitati | Configurazione filtri WCM | Importante |
| Il bundle e il servlet Sling WebDAV sono configurati in modo appropriato | Verifica stato WebDAV | Importante |
| Il server web è configurato per impedire il click-jacking | Configurazione server Web | Importante |
| La replica non utilizza l&#39;utente &quot;admin&quot; | Utenti replica e trasporto | Info |

## Test delle prestazioni {#performance-testing}

*Il* test delle prestazioni  [!UICONTROL Cloud Manager] viene implementato utilizzando un test di 30 minuti.

Durante la configurazione della pipeline, il gestore della distribuzione può decidere il traffico da indirizzare a ogni bucket.

Per ulteriori informazioni sui controlli del bucket, consulta [Configurare la pipeline CI/CD](configuring-pipeline.md).

>[!NOTE]
>
>Per impostare il programma e definire i KPI, consulta [Configurare il programma](setting-up-program.md).

Nella tabella seguente viene riepilogata la matrice dei test delle prestazioni utilizzando il sistema di verifica a tre livelli:

| **Metrica** | **Categoria** | **Soglia errore** |
|---|---|---|
| Tasso di errore richiesta pagina % | Critico | >= 2% |
| Frequenza di utilizzo della CPU | Critico | >= 80% |
| Tempo di attesa IO disco | Critico | >= 50% |
| Tempo di risposta del 95% | Importante | >= KPI a livello di programma |
| Tempo di risposta al picco | Importante | >= 18 secondi |
| Visualizzazioni pagina al minuto | Importante | &lt; Program-level=&quot;&quot; KPI=&quot;&quot;> |
| Utilizzo della larghezza di banda del disco | Importante | >= 90% |
| Utilizzo della larghezza di banda di rete | Importante | >= 90% |
| Richieste al minuto | Info | >= 6000 |

### Grafici dei risultati del test delle prestazioni {#performance-testing-results-graphs}

Nella finestra di dialogo Risultati del test delle prestazioni sono state aggiunte nuove opzioni per grafici e download.

Quando apri la finestra di dialogo Prova prestazioni , i pannelli delle metriche possono essere espansi per visualizzare un grafico, fornire un collegamento a un download o entrambi.

Per la versione [!UICONTROL Cloud Manager] 2018.7.0, questa funzionalità è disponibile per le metriche seguenti:

* **Utilizzo CPU**
   * Un grafico dell&#39;utilizzo della CPU durante il periodo di test.

* **Tempo di attesa I/O del disco**
   * Grafico del tempo di attesa I/O del disco durante il periodo di prova.

* **Frequenza errori pagina**
   * Grafico degli errori di pagina al minuto durante il periodo di test.
   * Un file CSV in cui sono elencate le pagine che hanno prodotto un errore durante il test.

* **Utilizzo della larghezza di banda del disco**
   * Grafico dell&#39;utilizzo della larghezza di banda del disco durante il periodo di prova.

* **Utilizzo della larghezza di banda di rete**
   * Grafico dell&#39;utilizzo della larghezza di banda di rete durante il periodo di prova.

* **Tempo di risposta al picco**
   * Un grafico del tempo di risposta di picco al minuto durante il periodo di prova.

* **Tempo di risposta del 95° percentile**
   * Un grafico del tempo di risposta del 95° percentile al minuto durante il periodo di prova.
   * Un file CSV che elenca le pagine il cui tempo di risposta del 95° percentile ha superato il KPI definito.

Le immagini seguenti mostrano i grafici dei test delle prestazioni:

![](assets/understand_test-results-screen1.png)

![](assets/screen_shot_2018-09-05at83933pm.png)

