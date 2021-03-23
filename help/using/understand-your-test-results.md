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
feature: Pipeline CI-CD, risultati del test
translation-type: tm+mt
source-git-commit: 12a7d6199983e2d19ef401051f60e3f24bb6d4f8
workflow-type: tm+mt
source-wordcount: '2685'
ht-degree: 4%

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

Questi stessi controlli di integrità possono essere eseguiti in qualsiasi momento tramite la console Web o il dashboard delle operazioni.

Se una delle **Istanze** segnala un errore per una determinata verifica dello stato di salute, l&#39;intero **Ambiente** non riesce a controllare lo stato di salute. Come per i test di qualità e prestazioni del codice, questi controlli di integrità sono organizzati in categorie e segnalati utilizzando il sistema di verifica a tre livelli. L&#39;unica distinzione è che non esiste alcuna soglia nel caso di test di sicurezza. Tutti i controlli sanitari sono semplicemente superati o falliti.

Nella tabella seguente sono elencati i controlli correnti:

| **Nome** | **Implementazione del controllo dello stato** | **Categoria** |
|---|---|---|
| Preparazione dell&#39;API dell&#39;attacco firewall di deserializzazione in uno stato accettabile | [Compatibilità Attach Api di firewall deserializzazione](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html?lang=en#security) | Critico |
| Il firewall di deserializzazione funziona | [Firewall deserializzazione funzionale](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html?lang=en#security) | Critico |
| Firewall di deserializzazione caricato | [Firewall deserializzazione caricato](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html?lang=en#security) | Critico |
| L&#39;implementazione AuthorizableNodeName non espone l&#39;ID autorizzabile nel nome/percorso del nodo. | [Generazione nome nodo autorizzabile](https://experienceleague.adobe.com/docs/experience-manager-64/administering/security/security-checklist.html?lang=en#security) | Critico |
| Le password predefinite sono state modificate | [Account di login predefiniti](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html?lang=en#users-and-groups-in-aem) | Critico |
| Il servlet di GET predefinito Sling è protetto dagli attacchi DOS. | Sling Get Servlet | Critico |
| Il gestore Java Script Sling è configurato in modo appropriato | Sling Java Script Handler | Critico |
| Il gestore di script Sling JSP è configurato in modo appropriato | Sling JSP Script Handler | Critico |
| SSL è configurato correttamente | Configurazione SSL | Critico |
| Nessun criterio di profilo utente ovviamente non sicuro trovato | Accesso standard profilo utente | Critico |
| Il filtro Sling Referrer è configurato per prevenire attacchi CSRF | [Sling Referrer Filter](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html?lang=en#security) | Importante |
| Adobe Granite HTML Library Manager è configurato in modo appropriato | Configurazione manager libreria CQ HTML | Importante |
| Il bundle CRXDE Support è disabilitato | Supporto CRXDE | Importante |
| Il bundle e il servlet Sling DavEx sono disabilitati | Verifica stato DavEx | Importante |
| Contenuto di esempio non installato | Pacchetti contenuti di esempio | Importante |
| Il filtro di richiesta WCM e il filtro di debug WCM sono disabilitati | [Configurazione filtri WCM](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/osgi-configuration-settings.html?lang=en#configuring) | Importante |
| Il bundle e il servlet Sling WebDAV sono configurati in modo appropriato | Verifica stato WebDAV | Importante |
| Il server web è configurato per impedire il click-jacking | Configurazione server Web | Importante |
| La replica non utilizza l&#39;utente &quot;admin&quot; | Utenti replica e trasporto | Info |

## Test delle prestazioni {#performance-testing}

### AEM Sites {#aem-sites}

Cloud Manager esegue test delle prestazioni per i programmi AEM Sites. Il test delle prestazioni viene eseguito per ~ 30 minuti raggruppando gli utenti virtuali (contenitori) che simulano gli utenti effettivi per accedere alle pagine nell’ambiente Stage e simulano il traffico. Queste pagine vengono trovate utilizzando un crawler.

1. **Utenti virtuali**

   Il numero di utenti o contenitori virtuali generati da Cloud Manager è determinato dal KPI (tempo di risposta e pageviews/min) definito dall&#39;utente nel ruolo Proprietario business durante la [creazione o modifica del programma](setting-up-program.md). In base ai KPI definiti, verranno attivati fino a 10 contenitori che simulano gli utenti effettivi. Le pagine selezionate per il test vengono suddivise e assegnate a ogni virtuale.

1. **Cacciatrice**

   Prima dell’inizio del periodo di test di 30 minuti, Cloud Manager eseguirà la ricerca per indicizzazione dell’ambiente Stage utilizzando un set di uno o più URL di seed configurati dal Customer Success Engineer. A partire da questi URL, l’HTML di ogni pagina viene esaminato e i collegamenti vengono attraversati in modo molto semplice. Questo processo di ricerca per indicizzazione è limitato a un massimo di 5000 pagine. Le richieste del crawler hanno un timeout fisso di 10 secondi.

1. **Set di pagine per il test**

   Le pagine sono selezionate da tre set di pagine. Cloud Manager utilizza i registri di accesso delle istanze AEM in Produzione e Stage per determinare i tre blocchi seguenti:

   * *Pagine* Live popolari: Questa opzione è selezionata per assicurarsi che vengano testate le pagine più popolari a cui accedono i clienti live. Cloud Manager legge il registro di accesso e determina le prime 25 pagine più accessibili dai clienti live in modo da generare un elenco delle pagine principali `Popular Live Pages`. L&#39;intersezione di questi elementi, presenti anche in Stage, viene quindi sottoposta a ricerca per indicizzazione nell&#39;ambiente Stage.

   * *Altre pagine* live: Questa opzione è selezionata per garantire che vengano testate le pagine che non rientrano nelle prime 25 pagine live più popolari ma che potrebbero non essere popolari, ma importanti da testare. Analogamente alle pagine popolari in tempo reale, queste vengono estratte dal registro di accesso e devono essere presenti anche in Stage.

   * *Nuove pagine*: Questa opzione è selezionata per testare le nuove pagine che possono essere state distribuite solo in Stage e non ancora in Produzione, ma che devono essere testate.

      **Distribuzione del traffico tra set di pagine selezionati**

      Puoi scegliere da uno a tutti e tre i set nella scheda &quot;Test&quot; della configurazione della pipeline (collegamento Inserisci). La distribuzione del traffico si basa sul numero di set selezionati, ovvero, se sono selezionati tutti e tre, il 33% delle visualizzazioni di pagina totali viene indirizzato a ciascun set; se sono selezionati due, il 50% va a ciascun set; se ne è selezionato uno, il 100% del traffico viene indirizzato a tale set.

      Ad esempio, supponiamo che ci sia una divisione tra il 50% - 50% delle pagine popolari Live e le nuove pagine impostate (in questo esempio, non vengono utilizzate altre pagine Live) e il set Nuove pagine contiene 3000 pagine. Il KPI per le visualizzazioni di pagina al minuto è impostato su 200. Nel periodo di prova di 30 minuti:

      * Ognuna delle 25 pagine del set di pagine popolari in tempo reale verrà visualizzata 120 volte - (200 * 0.5) / 25) * 30 = 120

      * Ognuna delle 3000 pagine del set di nuove pagine verrà visualizzata una volta - (200 * 0.5) / 3000) * 30 = 1

#### Test e reporting {#testing-reporting}

Cloud Manager esegue test delle prestazioni per i programmi AEM Sites richiedendo pagine (come utente non autenticato per impostazione predefinita) sul server di pubblicazione dell’area di visualizzazione per un periodo di test di 30 minuti e misurando le metriche (virtuali) generate dall’utente (tempo di risposta, tasso di errore, visualizzazioni al minuto, ecc.) per ogni pagina e varie metriche a livello di sistema (CPU, memoria, dati di rete) per tutte le istanze.\
Nella tabella seguente sono riepilogate le metriche del test delle prestazioni rispetto a a-vis utilizzando il sistema di verifica a tre livelli:

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

Per ulteriori informazioni sull’utilizzo dell’autenticazione di base per i test delle prestazioni per Sites e Assets, consulta la sezione seguente **Test delle prestazioni autenticati** .

>[!NOTE]
>Ogni istanza viene monitorata durante il periodo del test, sia per Pubblica che per Autore. Se non viene ottenuta alcuna metrica per una sola istanza, tale metrica viene segnalata come sconosciuta e il passaggio corrispondente non riuscirà.

#### Test delle prestazioni autenticati {#authenticated-performance-testing}

Questa funzione è facoltativa per Sites.
I clienti AMS con siti autenticati possono specificare un nome utente e una password che Cloud Manager utilizzerà per accedere al sito web durante il test delle prestazioni di Sites.
Il nome utente e la password sono specificati come Variabili della pipeline con i nomi `CM_PERF_TEST_BASIC_USERNAME` e `CM_PERF_TEST_BASIC_PASSWORD`.
Sebbene non sia strettamente richiesto, si consiglia di utilizzare il tipo di variabile stringa per il nome utente e il tipo di variabile secretString per la password. Se vengono specificati entrambi, ogni richiesta del crawler dei test delle prestazioni e degli utenti virtuali del test conterrà queste credenziali come autenticazione HTTP Basic.

Per impostare queste variabili utilizzando Cloud Manager CLI, esegui:

```shell
$ aio cloudmanager:set-pipeline-variables <pipeline id> --variable CM_PERF_TEST_BASIC_USERNAME <username> --secret CM_PERF_TEST_BASIC_PASSWORD <password>
```

Per informazioni su come utilizzare l’API, consulta [Variabili](https://www.adobe.io/apis/experiencecloud/cloud-manager/api-reference.html#/Variables/patchPipelineVariables) .

### AEM Assets {#aem-assets}

Cloud Manager esegue test delle prestazioni per i programmi AEM Assets caricando ripetutamente le risorse per un periodo di test di 30 minuti.

1. **Requisiti di onboarding**

   Per il test delle prestazioni di Assets, il Customer Success Engineer creerà un `cloudmanager` utente (e password) durante l’onboarding dell’ambiente Authoring in Stage. I passaggi del test delle prestazioni richiedono l’utente denominato `cloudmanager` e la password associata impostata dal CSE. Non deve essere rimosso dall&#39;autore né modificato per quanto riguarda le autorizzazioni. Questa operazione potrebbe non riuscire nel test delle prestazioni di Assets.

1. **Immagini e risorse per il test**

   I clienti possono caricare le proprie risorse da testare. Questa operazione può essere eseguita dalla schermata Configurazione della pipeline o Modifica. Sono supportati i formati immagine più comuni, come JPEG, PNG, GIF e BMP, insieme ai file Photoshop, Illustrator e Postscript. Tuttavia, se non vengono caricate immagini, Cloud Manager utilizzerà un’immagine e un documento PDF predefiniti per il test.

1. **Distribuzione delle risorse da sottoporre a test**

   La distribuzione del numero di risorse di ciascun tipo caricate al minuto viene impostata nella schermata Configurazione della pipeline o Modifica.
Ad esempio, se si utilizza una suddivisione 70/30, come illustrato nella figura riportata di seguito. Le risorse caricate al minuto sono 10, verranno caricate 7 immagini al minuto e 3 documenti.

1. **Test e reporting**

   Cloud Manager creerà una cartella sull’istanza di authoring, utilizzando il nome utente e la password impostati dal CSE dal passaggio 1 (Requisiti di onboarding) come indicato sopra e carica le risorse nella cartella utilizzando una libreria open source. I test eseguiti dal passaggio di test Assets vengono scritti utilizzando questa [libreria open source](https://github.com/adobe/toughday2). Il tempo di elaborazione di ciascuna risorsa e di varie metriche a livello di sistema vengono misurati nell’arco di 30 minuti. Questa funzionalità può caricare sia immagini che documenti PDF.

   >[!NOTE]
   >Per ulteriori informazioni sulla configurazione dei test delle prestazioni, consulta [Configurare la pipeline CI/CD](configuring-pipeline.md). Per informazioni su come impostare il programma e definire i KPI, consulta [Configurazione del programma](setting-up-program.md) .

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

