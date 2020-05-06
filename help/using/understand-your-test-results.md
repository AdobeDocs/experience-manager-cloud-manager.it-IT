---
title: Comprendere i risultati del test
seo-title: Comprendere i risultati del test
description: 'null'
seo-description: Segui questa pagina per apprendere tre livelli di cancelli durante l’esecuzione di una pipeline, la scansione del codice, le prestazioni e i test di sicurezza che convalidano il programma in Cloud Manager.
uuid: 93caa01f-0df2-4a6f-81dc-23dfee24dc93
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: 83299ed8-4b7a-4b1c-bd56-1bfc7e7318d4
translation-type: tm+mt
source-git-commit: 278858465592482449080fedc3c0165805db223d
workflow-type: tm+mt
source-wordcount: '1461'
ht-degree: 8%

---


# Comprendere i risultati del test {#understand-your-test-results}

Durante il processo di **pipeline** , vengono acquisite diverse metriche e confrontate con gli indicatori prestazioni chiave (KPI, Key Performance Indicators) definiti dal proprietario dell&#39;azienda o con gli standard impostati da Adobe Managed Services.

Questi sono segnalati utilizzando il sistema di monitoraggio a tre livelli come definito in questa sezione.

## Gate a tre livelli durante l&#39;esecuzione di una tubazione  {#three-tier-gates-while-running-a-pipeline}

La conduttura prevede tre cancelli:

* Qualità del codice
* Test delle prestazioni
* Test di protezione

Per ciascuno di questi cancelli, esiste una struttura a tre livelli per i problemi identificati dal cancello.

* **Critico** - Si tratta di problemi identificati dal cancello che causano un immediato fallimento della conduttura.
* **Importante** : si tratta di problemi identificati dal gate che causano l&#39;ingresso della pipeline in stato di pausa. Un gestore di distribuzione, un project manager o un proprietario aziendale possono ignorare i problemi, nel qual caso la pipeline procede, oppure possono accettare i problemi, nel qual caso la pipeline si interrompe con un errore.
* **Informazioni** - Si tratta di problemi identificati dalla porta che sono forniti esclusivamente a scopo informativo e non hanno alcun impatto sull&#39;esecuzione della conduttura.

>[!NOTE]
>
>In una tubazione Solo qualità codice, non è possibile ignorare importanti errori nel gate di verifica della qualità del codice, poiché il passaggio Test della qualità del codice è l&#39;ultimo passaggio della pipeline.

## Verifica della qualità del codice {#code-quality-testing}

Come parte della pipeline, il codice sorgente viene analizzato per garantire che le distribuzioni soddisfino determinati criteri di qualità. Attualmente, questo è implementato tramite una combinazione di SonarQube e l&#39;esame a livello di pacchetto di contenuti tramite OakPAL. Esistono più di 100 regole che combinano regole Java generiche e regole specifiche di AEM. La tabella seguente riassume la valutazione per i criteri di prova:

| Nome | Definizione | Categoria | Soglia di errore |
|--- |--- |--- |--- |
| Valutazione sicurezza | A = 0 Vulnerabilità <br/>B = almeno 1 Vulnerabilità<br/> minore C = almeno 1 Vulnerabilità maggiore <br/>D = almeno 1 Vulnerabilità critica <br/>E = almeno 1 Vulnerabilità blocco | Critico | &lt; B |
| Valutazione affidabilità | A = 0 Bug <br/>B = almeno 1 Bug Minore <br/>C = almeno 1 Bug Principale <br/>D = almeno 1 Bug Critico E = almeno 1 Bug Blocco | Importante | &lt; C |
| Classificazione manutenibilità | L&#39;eccezionale costo di riparazione per gli odori di codice è: <br/><ul><li>&lt;=5% del tempo che è già passato nell&#39;applicazione, la valutazione è A </li><li>tra il 6 e il 10% il rating è a B </li><li>tra l&#39;11% e il 20% il rating è a C </li><li>tra il 21% e il 50% la valutazione è una D</li><li>un valore superiore al 50% è un E</li></ul> | Importante | &lt; A |
| Copertura | Una combinazione di copertura della linea di prova di unità e copertura della condizione utilizzando la seguente formula: <br/>`Coverage = (CT + CF + LC)/(2*B + EL)`  <br/>dove: CT = condizioni che sono state valutate come &#39;true&#39; almeno una volta durante l&#39;esecuzione di unit test <br/>CF = condizioni che sono state valutate come &#39;false&#39; almeno una volta durante l&#39;esecuzione di unit test <br/>LC = linee coperte = lines_to_cover - uncover_lines <br/><br/> B = numero totale di condizioni <br/>EL = numero totale di linee eseguibili (lines_to_cover) | Importante | &lt; 50% |
| Test di unità ignorati | Numero di unit test ignorati. | Info | > 1 |
| Problemi aperti | Tipi di problemi generali - Vulnerabilità, bug e odori di codice | Info | > 1 |
| Linee duplicate | Numero di righe coinvolte in blocchi duplicati. <br/>Per considerare un blocco di codice come duplicato: <br/><ul><li>**Progetti non Java:**</li><li>Devono essere presenti almeno 100 token successivi e duplicati.</li><li>Tali token devono essere ripartiti almeno su: </li><li>30 righe di codice per COBOL </li><li>20 righe di codice per ABAP </li><li>10 righe di codice per altre lingue</li><li>**Progetti Java:**</li><li> Devono essere presenti almeno 10 istruzioni successive e duplicate, indipendentemente dal numero di token e di righe.</li></ul> <br/>Le differenze nei rientri e nei letterali di stringa vengono ignorate durante il rilevamento di duplicati. | Info | > 1% |
| Compatibilità con i servizi cloud | Numero di problemi di compatibilità del servizio cloud identificati. | Info | >0 |


>[!NOTE]
>
>Per informazioni più dettagliate, fare riferimento a Definizioni [metriche](https://docs.sonarqube.org/display/SONAR/Metric+Definitions) .

Puoi scaricare l&#39;elenco delle regole qui [code-quality-rules.xlsx](/help/using/assets/CodeQuality-rules-latest.xlsx)

>[!NOTE]
>
>Per ulteriori informazioni sulle regole di qualità del codice personalizzate eseguite da [!UICONTROL Cloud Manager], fare riferimento a [Custom Code Quality Rules](custom-code-quality-rules.md).

### Gestione dei falsi positivi {#dealing-with-false-positives}

Il processo di scansione della qualità non è perfetto e a volte identificherà erroneamente i problemi che non sono effettivamente problematici. Questo viene definito &quot;falso positivo&quot;.

In questi casi, il codice sorgente può essere annotato con l&#39; `@SuppressWarnings` annotazione Java standard che specifica l&#39;ID regola come attributo annotazione. Ad esempio, un problema comune è che la regola SonarQube per rilevare le password hardcoded può essere aggressiva per quanto riguarda il modo in cui viene identificata una password hardcoded.

Per un esempio specifico, questo codice è abbastanza comune in un progetto AEM con codice per la connessione a un servizio esterno:

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube solleverà una vulnerabilità di blocco. Dopo aver rivisto il codice, identificate che non si tratta di una vulnerabilità e potete annotarlo con l&#39;ID regola appropriato.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Tuttavia, se il codice fosse effettivamente questo:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Quindi la soluzione corretta è rimuovere la password hardcoded.

>[!NOTE]
>
>Sebbene sia buona norma rendere l’ `@SuppressWarnings` annotazione il più possibile specifica, ovvero annotare solo l’istruzione o il blocco specifico che causa il problema, è possibile inserire delle annotazioni a livello di classe.

## Test di protezione {#security-testing}

[!UICONTROL Cloud Manager] esegue i controlli ***di integrità di*** AEM Security esistenti sul passaggio successivo alla distribuzione e segnala lo stato tramite l&#39;interfaccia utente. I risultati sono aggregati da tutte le istanze di AEM presenti nell’ambiente.

Se una delle **istanze** segnala un errore per una determinata verifica dello stato di salute, l&#39;intero **Ambiente** non riesce a controllare lo stato di salute. Come nel caso del Code Quality and Performance Testing, questi controlli dello stato di salute sono organizzati in categorie e riportati utilizzando il sistema di controllo a tre livelli. L&#39;unica distinzione è che non esiste una soglia nel caso di test di sicurezza. Tutti i controlli sanitari sono semplicemente superati o falliti.

Nella tabella seguente sono elencati i controlli correnti:

| **Nome** | **Implementazione della verifica dello stato** | **Categoria** |
|---|---|---|
| La disponibilità dell&#39;API Attacco firewall di deserializzazione è in uno stato accettabile | Compatibilità Attach Api di firewall deserializzazione | Critico |
| Il firewall di deserializzazione funziona | Firewall deserializzazione funzionale | Critico |
| Il firewall di deserializzazione è caricato | Firewall deserializzazione caricato | Critico |
| L&#39;implementazione AuthorizableNodeName non espone l&#39;ID autorizzabile nel nome/percorso del nodo. | Generazione nome nodo autorizzabile | Critico |
| Le password predefinite sono state modificate | Account di login predefiniti | Critico |
| Il servlet GET predefinito Sling è protetto dagli attacchi DOS. | Sling Get Servlet | Critico |
| Il gestore Sling Java Script è configurato correttamente | Sling Java Script Handler | Critico |
| Il gestore Sling JSP Script è configurato correttamente | Gestore di script JSP Sling | Critico |
| SSL è configurato correttamente | Configurazione SSL | Critico |
| Nessun criterio profilo utente ovviamente non sicuro trovato | Accesso standard profilo utente | Critico |
| Il filtro Sling Referrer è configurato per prevenire attacchi CSRF | Sling Referrer Filter | Importante |
| Adobe Granite HTML Library Manager è configurato correttamente | Configurazione manager libreria CQ HTML | Importante |
| Il bundle di supporto CRXDE è disattivato | Supporto CRXDE | Importante |
| Il bundle Sling DavEx e il servlet sono disattivati | Verifica stato DavEx | Importante |
| Contenuto di esempio non installato | Pacchetti contenuti di esempio | Importante |
| Sia il filtro di richiesta WCM che il filtro di debug WCM sono disattivati | Configurazione filtri WCM | Importante |
| Il bundle WebDAV Sling e il servlet sono configurati correttamente | Verifica stato WebDAV | Importante |
| Il server Web è configurato per impedire il clickjacking | Configurazione server Web | Importante |
| La replica non utilizza l&#39;utente &#39;admin&#39; | Utenti replica e trasporto | Info |

## Test delle prestazioni {#performance-testing}

*Il test* delle prestazioni in [!UICONTROL Cloud Manager] è implementato utilizzando un test di 30 minuti.

Durante la configurazione della pipeline, il gestore distribuzione può decidere il traffico diretto a ogni bucket.

Per ulteriori informazioni sui controlli del bucket, consulta [Configurare la pipeline](configuring-pipeline.md)CI/CD.

>[!NOTE]
>
>Per impostare il programma e definire i KPI, vedi [Configurazione del programma](setting-up-program.md).

La tabella seguente riassume la matrice del test di prestazione utilizzando il sistema di controllo a tre livelli:

| **Metrica** | **Categoria** | **Soglia di errore** |
|---|---|---|
| Tasso di errore richiesta pagina % | Critico | >= 2% |
| Tasso di utilizzo CPU | Critico | >= 80% |
| Tempo di attesa IO disco | Critico | >= 50% |
| Tempo di risposta percentuale 95 | Importante | >= Indicatore KPI a livello di programma |
| Tempo di risposta picco | Importante | >= 18 secondi |
| Visualizzazioni pagina al minuto | Importante | &lt; Indicatore KPI a livello di programma |
| Utilizzo della larghezza di banda del disco | Importante | >= 90% |
| Utilizzo della larghezza di banda di rete | Importante | >= 90% |
| Richieste al minuto | Info | &lt; 6000 |

### Grafici dei risultati del test delle prestazioni {#performance-testing-results-graphs}

Nuovi grafici e opzioni di download sono stati aggiunti alla finestra di dialogo Risultati test delle prestazioni.

Quando apri la finestra di dialogo Performance Test (Test prestazioni), i pannelli delle metriche possono essere espansi per visualizzare un grafico, fornire un collegamento a un download o entrambi.

Per la [!UICONTROL Cloud Manager] release 2018.7.0, questa funzionalità è disponibile per le metriche seguenti:

* **Utilizzo CPU**
   * Un grafico dell&#39;utilizzo della CPU durante il periodo di test.

* **Tempo di attesa I/O disco**
   * Grafico del tempo di attesa I/O del disco durante il periodo di prova.

* **Frequenza errori pagina**
   * Un grafico degli errori di pagina al minuto durante il periodo di prova.
   * Un file CSV che elenca le pagine che hanno prodotto un errore durante il test.

* **Utilizzo della larghezza di banda del disco**
   * Un grafico dell&#39;utilizzo della larghezza di banda del disco durante il periodo di prova.

* **Utilizzo della larghezza di banda di rete**
   * Un grafico dell&#39;utilizzo della larghezza di banda di rete durante il periodo di prova.

* **Tempo di risposta picco**
   * Un grafico del tempo di risposta di picco al minuto durante il periodo di prova.

* **95° tempo di risposta percentuale**
   * Un grafico del 95° percentile del tempo di risposta al minuto durante il periodo di prova.
   * Un file CSV che elenca le pagine il cui tempo di risposta del 95° percentile ha superato l’indicatore KPI definito.

Le immagini seguenti mostrano i grafici di prova delle prestazioni:

![](assets/understand_test-results-screen1.png)

![](assets/screen_shot_2018-09-05at83933pm.png)

