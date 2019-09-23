---
title: Utilizzo di Cloud Manager
seo-title: Utilizzo di Adobe AEM Cloud Manager
description: Descrizione dell'interfaccia utente di AEM Cloud Manager
seo-description: Descrizione dell’interfaccia utente di Adobe AEM Cloud Manager
page-status-flag: mai attivato
uuid: cef44d35-75ed-44bb-9636-2de2bca5e458
contentOwner: jsyal
discoiquuid: c37566d5-0d1b-4c44-abd7-b271ea443c1a
translation-type: tm+mt
source-git-commit: 4c1c6786db9b8972f9315bd2f12fc1752881492f

---


# Utilizzo di Cloud Manager{#using-cloud-manager}

In questa sezione viene illustrata l’interfaccia utente [!UICONTROL Cloud Manager] e viene illustrato il flusso di lavoro dall’impostazione del programma alla distribuzione del codice seguita da controlli di qualità.

## Prerequisiti {#prerequisites}

Prima di accedere ai dettagli relativi all'utilizzo di [!UICONTROL Cloud Manager], è consigliabile passare alle seguenti sezioni:

* [Concetti principali prima di utilizzare [!UICONTROL Cloud Manager]](understanding-concepts.md)
* [Configurazione delle configurazioni generali per [!UICONTROL Cloud Manager]](setting-configurations-for-cloud-manager.md)

## Getting Started with [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Una volta configurate le configurazioni generali per [!UICONTROL Cloud Manager], potete usare il [!UICONTROL Cloud Manager].

1. Accedi ad Adobe [!UICONTROL Experience Cloud] e vedrai l'elenco delle soluzioni.

   ![](assets/screen_shot_2018-04-22at92951am.png)

1. Selezionare il programma e fare clic sull'icona in alto a sinistra per aprire [!UICONTROL Cloud Manager].

   ![](assets/screen_shot_2018-04-22at93346am.png)

## Impostazione del programma {#setting-up-program}

Dopo la registrazione, il proprietario dell'azienda dovrà effettuare una configurazione iniziale del programma. Ciò comporta l'impostazione della descrizione del programma e la definizione dei KPI che verranno utilizzati per il test delle prestazioni. Facoltativamente, è possibile caricare una miniatura.

I KPI definiti fungono da riferimento per il test delle prestazioni che viene passato ogni volta che la pipeline viene eseguita.

>[!NOTE]
>
>I KPI definiti vengono misurati sui test eseguiti nell'ambiente **stage** . In genere, questi KPI vengono ridotti per adattarsi alle funzionalità dell’ambiente di visualizzazione.
>
>Ad esempio, un utente che si aspetta una media di 1000 visualizzazioni di pagina al minuto nell’ambiente di produzione e che dispone di quattro `dispatcher/publish` server in produzione, deve ridimensionare questo valore a 250 visualizzazioni di pagina al minuto (supponendo che l’ambiente in cui si trova lo stage sia costituito da una sola coppia di `dispatcher/publish` server).
>
>Inoltre, molti utenti dispongono di un CDN (Akamai, CloudFront) davanti al proprio ambiente di produzione. Poiché [!UICONTROL Cloud Manager] i test vengono eseguiti direttamente sull’ambiente di passaggio, l’indicatore KPI deve riflettere solo il traffico previsto attraverso la rete CDN, ovvero gli errori della cache. In genere si tratta di un sottoinsieme relativamente piccolo del traffico di produzione totale.

### Uso [!UICONTROL Cloud Manager] per definire i KPI {#using-cloud-manager-to-define-kpis}

Per impostare il programma e definire KPI, procedere come segue:

1. Fate clic su **Programma** di installazione per avviare il processo di configurazione in [!UICONTROL Cloud Manager].
1. Viene visualizzata la schermata **Modifica informazioni** programma.

   Caricate una miniatura nel programma. È inoltre possibile aggiungere una descrizione pertinente al programma e fare clic su **Avanti**.

1. Viene visualizzata la schermata **Configura utenti** .

   Potete configurare i ruoli e gli utenti del team. Fai clic su **Avanti**.

1. Viene visualizzata la schermata **Configura KPI** business generale.

   Puoi definire i tuoi due KPI (aspettative per ogni distribuzione):

   1. Qual è il tempo di risposta del 95° percentile accettabile per voi?

      1. Valore consigliato - 3 secondi
   1. Quante visualizzazioni di pagina al minuto sotto il carico massimo?

      1. Valore consigliato - 200 pv/m


1. Fate clic su **Invia** per completare la procedura guidata di configurazione.

   Viene visualizzata la schermata iniziale per [!UICONTROL Cloud Manager] la modifica a **Distribuzione**.

## Ambienti disponibili {#available-environments}

Gli ambienti **** disponibili [!UICONTROL Cloud Manager] elencano tutti gli ambienti AEM gestiti.

A ciascuno degli ambienti elencati sarà associato uno stato.

## Configurazione della pipeline {#configuring-pipeline}

### Impostazione della tubazione {#setting-up-pipeline}

>[!CAUTION]
>
>Impossibile impostare la pipeline finché il repository git non dispone di almeno un ramo.

Prima di iniziare a distribuire il codice, devi configurare le impostazioni della pipeline dal [!UICONTROL Cloud Manager].

Per ulteriori informazioni sulla configurazione della tubazione, consulta la sezione Panoramica **della** tubazione in ** [Concetti prima di utilizzare [!UICONTROL Cloud Manager]](understanding-concepts.md)**.

>[!NOTE]
>
>È possibile modificare le impostazioni della pipeline dopo la configurazione iniziale.

### Configurazione delle impostazioni della tubazione dal [!UICONTROL Cloud Manager]{#configuring-pipeline-settings-from-the-cloud-manager}

Per configurare il comportamento e le preferenze della pipeline, effettuate le operazioni seguenti [!UICONTROL Cloud Manager] :

1. Accedere alla scheda **Filiale** per impostare il ramo dell'applicazione.

   Selezionare il ramo git che si desidera impostare.

   >[!NOTE]
   >
   >Le filiali presenti nel repository Git sono collegate al programma.

   ![](assets/screen_shot_2018-05-06at73604pm.png)

1. Accedete alla scheda **Ambienti** per selezionare le opzioni **Stage** e **Produzione** .

   È possibile definire il trigger che avvierà la pipeline:

   * **Manuale** : qualcuno deve fare clic manualmente nell'interfaccia per avviare la pipeline.
   Ora definite i parametri che controllano la distribuzione di produzione. Le tre opzioni disponibili sono le seguenti:

   * **Usa approvazione** Go Live: una distribuzione deve essere approvata manualmente dal proprietario aziendale, dal project manager o dal manager della distribuzione tramite l' [!UICONTROL Cloud Manager] interfaccia utente.
   * **Usa CSE Oversight** : un CSE è impegnato per avviare effettivamente la distribuzione.
   ![](assets/screen_shot_2018-05-06at73715pm.png)

1. Accedete alla scheda **Test** per definire i criteri di test per il programma.

   Ora potete configurare i parametri del test delle prestazioni.

   ![](assets/screen_shot_2018-05-06at73750pm.png)

## Distribuzione del codice {#deploying-code}

Dopo aver configurato la pipeline (repository, ambiente e ambiente di verifica), potete distribuire il codice.

### Distribuzione del codice da [!UICONTROL Cloud Manager]{#deploying-code-from-cloud-manager}

Per distribuire il codice nell’ambiente di produzione, effettuate le operazioni seguenti:

1. Fate clic su **Distribuisci** dal [!UICONTROL Cloud Manager] menu per avviare il processo di distribuzione.
1. Viene visualizzata la schermata Distribuzione **** stage.

   Fate clic su **Genera** per avviare il processo.

1. Il processo di compilazione completo tiene conto di diversi parametri per controllare e distribuire il codice.

   I seguenti parametri controllati sono i seguenti:

   **Implementazione stage**

   * Archivio
   * Test di unità
   * Analisi del codice
   * Implementato in ambiente stage
   **Test pre-produzione**

   * Test di protezione
   * Test delle prestazioni
   >[!NOTE]
   >
   >Inoltre, potete visualizzare i registri o rivedere i risultati per i criteri di test indicati sopra.

## Risultati dai controlli di qualità {#results-from-quality-checks}

La conduttura prevede tre porte: Qualità del codice, test delle prestazioni e test di sicurezza.

Per ciascuno di questi cancelli, esiste una struttura a tre livelli per i problemi identificati dal cancello.

* **Critico** - Si tratta di problemi identificati dal cancello che causano un immediato fallimento della conduttura.
* **Importante** : si tratta di problemi identificati dal gate che causano l'ingresso della pipeline in stato di pausa. Un gestore di distribuzione, un project manager o un proprietario aziendale possono ignorare i problemi, nel qual caso la pipeline procede, oppure accettare i problemi, nel qual caso la pipeline si interrompe con un errore.
* **Informazioni** - Si tratta di problemi identificati dalla porta che sono forniti esclusivamente a scopo informativo e non hanno alcun impatto sull'esecuzione della conduttura.

### Analisi del codice {#code-scanning}

![](assets/screen_shot_2018-04-22at101443am.png)

### Test delle prestazioni {#performance-testing}

*Il test* delle prestazioni in [!UICONTROL Cloud Manager] è implementato utilizzando un test per 30 minuti.

Durante la configurazione della pipeline, il gestore distribuzione può decidere il traffico diretto a ogni bucket. Possono scegliere da una a tutte e tre le tasche. La distribuzione del traffico si basa sul numero di bucket selezionati, ossia se tutti e tre i periodi selezionati sono selezionati, il 33% delle visualizzazioni di pagina totali viene posizionato verso ciascun intervallo; se sono selezionati due, il 50% va a ciascun set; se ne è selezionata una, il 100% del traffico arriva a quel set.

Ad esempio, supponiamo che esista una divisione del 50%/50% tra le pagine Live popolari e le nuove pagine impostate (in questo esempio, non vengono utilizzate altre pagine Live) e che il set Nuove pagine contenga 3000 pagine. L'indicatore KPI per le visualizzazioni di pagina al minuto è impostato su 200. Nel periodo di prova di 30 minuti:

* Ciascuna delle 25 pagine del set Popular Live Pages verrà visualizzata 240 volte - `((200 &#42; 0.5) / 25) &#42; 30 = 120`
* Ognuna delle 3000 pagine del set Nuove pagine verrà visualizzata una sola volta - `((200 &#42; 0.5) / 3000) &#42; 30 = 1`

![](assets/image2018-3-14_16-23-56.png)

### Metriche di test delle prestazioni {#performance-test-metrics}

Durante il periodo di test, vengono acquisite diverse metriche e confrontate con i KPI definiti dal proprietario dell'azienda o con gli standard impostati da AMS.

Questi sono segnalati utilizzando il sistema di rating a tre livelli come segue:

### Gate a tre livelli durante l'esecuzione di una tubazione {#three-tier-gates-while-running-a-pipeline}

Sono presenti tre cancelli come Qualità del codice, Test delle prestazioni e Test di sicurezza.

Per ciascuno di questi cancelli, esiste una struttura a tre livelli per i problemi identificati dal cancello:

* **Critico**: Si tratta di problemi individuati dal cancello che causano un immediato fallimento della conduttura.
* **Importante**: Si tratta di problemi identificati dal gate che causano l'ingresso della pipeline in stato di pausa. Un gestore di distribuzione, un project manager o un proprietario aziendale possono ignorare i problemi, nel qual caso la pipeline procede, oppure accettare i problemi, nel qual caso la pipeline si interrompe con un errore.
* **Informazioni**: Si tratta di questioni individuate dalla porta che sono fornite esclusivamente a scopo informativo e che non hanno alcun impatto sull'esecuzione della conduttura.

La tabella seguente riassume la matrice del test di prestazione utilizzando il sistema di controllo a tre livelli:

| **Metrica** | **Categoria** | **Soglia di errore** |
|---|---|---|
| Tasso di errore richiesta pagina % |  Critico | &gt;= 2% |
| Tasso di utilizzo CPU |  Critico | &gt;= 80% |
| Tempo di attesa IO disco |  Critico | &gt;= 50% |
| Tempo di risposta percentuale 95 | Importante | &gt;= Indicatore KPI a livello di programma |
| Tempo di risposta picco | Importante | &gt;= 18 secondi |
| Visualizzazioni pagina al minuto | Importante | &lt; Indicatore KPI a livello di programma |
| Utilizzo della larghezza di banda del disco | Importante | &gt;= 90% |
| Utilizzo della larghezza di banda di rete | Importante | &gt;= 90% |
| Richieste al minuto | Info | &lt; 6000 |

### Test di protezione {#security-testing}

[!UICONTROL Cloud Manager] esegue i controlli *di integrità di* AEM Security esistenti sul passaggio successivo alla distribuzione e ne segnala lo stato tramite l'interfaccia utente. I risultati sono aggregati da tutte le istanze di AEM presenti nell’ambiente.

Se una delle istanze segnala un errore per un determinato controllo dello stato di salute, l'intero ambiente non riesce a controllare lo stato di salute. Come nel caso del Code Quality and Performance Testing, questi controlli dello stato di salute sono organizzati in categorie e riportati utilizzando il sistema di controllo a tre livelli. L'unica distinzione è che non esiste una soglia nel caso di test di sicurezza. Tutti i controlli sanitari sono semplicemente superati o falliti.

Gli attuali controlli sono:

| **Verifica stato** | **Categoria** |
|---|---|
| Compatibilità Attach Api di firewall deserializzazione |  Critico |
| Firewall deserializzazione funzionale |  Critico |
| Firewall deserializzazione caricato |  Critico |
| Generazione nome nodo autorizzabile |  Critico |
| Account di login predefiniti |  Critico |
| Sling Get Servlet |  Critico |
| Configurazione dispatcher CQ |  Critico |
| Configurazione manager libreria CQ HTML |  Critico |
| Sling Java Script Handler |  Critico |
| Sling Jsp Script Handler |  Critico |
| Sling Referrer Filter |  Critico |
| Configurazione SSL |  Critico |
| Accesso standard profilo utente |  Critico |
| Supporto CRXDE | Importante |
| Verifica stato DavEx | Importante |
| Pacchetti contenuti di esempio | Importante |
| Configurazione filtri WCM | Importante |
| Verifica stato WebDAV | Importante |
| Configurazione server Web | Importante |
| Utenti replica e trasporto | Info |

### Quality Check Implementation di SonarQube {#quality-check-implementation-by-sonarqube}

Come parte della pipeline, come illustrato sopra, il codice viene analizzato. Attualmente, questo è implementato da SonarQube. Abbiamo 93 regole che sono una combinazione di regole Java generiche e regole specifiche di AEM (incluse alcune delle regole esistenti di Cognfide). Un elenco di queste regole è reperibile qui: code-quality-rules.xlsx [](/help/using/assets/code-quality-rules.xlsx)

Da queste regole, vengono calcolate una serie di metriche, alcune delle quali vengono utilizzate come gate di qualità prima di consentire la distribuzione nell’ambiente di visualizzazione.

Sono le soglie attuali:

| Nome | Definizione | Categoria | Soglia di errore |
|--- |--- |--- |--- |
| Valutazione sicurezza | A = 0 Vulnerabilità <br/>B = almeno 1 Vulnerabilità<br/> minore C = almeno 1 Vulnerabilità maggiore <br/>D = almeno 1 Vulnerabilità critica <br/>E = almeno 1 Vulnerabilità blocco |  Critico | &lt; B |
| Valutazione affidabilità | A = 0 Bug <br/>B = almeno 1 Bug Minore <br/>C = almeno 1 Bug Principale <br/>D = almeno 1 Bug Critico E = almeno 1 Bug Blocco | Importante | &lt; C |
| Classificazione manutenibilità | L'eccezionale costo di riparazione per gli odori di codice è: <br/><ul><li>&lt;=5% del tempo che è già passato nell'applicazione, la valutazione è A </li><li>tra il 6 e il 10% il rating è a B </li><li>tra l'11% e il 20% il rating è a C </li><li>tra il 21% e il 50% la valutazione è una D</li><li>un valore superiore al 50% è un E</li></ul> | Importante | &lt; A |
| Copertura | Combinazione di copertura della linea e copertura della condizione utilizzando la seguente formula: <br/>`Coverage = (CT + CF + LC)/(2*B + EL)` <br/>dove: CT = condizioni che sono state valutate come 'true' almeno una volta <br/>CF = condizioni che sono state valutate come 'false' almeno una volta <br/>LC = linee coperte = lines_to_cover - uncover_lines <br/><br/> B = numero totale di condizioni <br/>EL = numero totale di linee eseguibili (lines_to_cover) | Importante | &lt; 50% |
| Test di unità ignorati | Numero di unit test ignorati. | Info | &gt; 1 |
| Problemi aperti | Tipi di problemi generali - Vulnerabilità, bug e odori di codice | Info | &gt; 1 |
| Linee duplicate | Numero di righe coinvolte in blocchi duplicati. <br/>Per considerare un blocco di codice come duplicato: <ul><li> **Progetti non Java:**</li><li>Devono essere presenti almeno 100 token successivi e duplicati.</li><li>Tali token devono essere ripartiti almeno su: </li><li>30 righe di codice per COBOL </li><li>20 righe di codice per ABAP </li><li>10 righe di codice per altre lingue</li></ul><ul><li>**Progetti Java:**</li><li> Devono essere presenti almeno 10 istruzioni successive e duplicate, indipendentemente dal numero di token e di righe.</li></ul>Le differenze nei rientri e nei letterali di stringa vengono ignorate durante il rilevamento di duplicati. | Info | &gt; 1% |

### Falso positivo {#false-positives}

Il processo di scansione della qualità non è perfetto e a volte identificherà erroneamente problemi che non sono effettivamente problematici. Questo è chiamato *falso positivo* (anche se *falso negativo* sarebbe probabilmente più semanticamente corretto). In questi casi, il codice sorgente può essere annotato con l' `@SuppressWarnings` annotazione Java standard che specifica l'ID regola come attributo annotazione. Ad esempio, un problema comune è che la regola SonarQube per rilevare le password hardcoded è molto liberale rispetto a quella che considera una password hardcoded.

Per un esempio specifico, questo codice è abbastanza comune in un progetto AEM con codice per la connessione a un servizio esterno:

```java
@Property(label = "Service Password")
private static final String SERVICE_PASSWORD = "password";
```

SonarQube lo solleverà come una vulnerabilità di blocco. In questo caso, il cliente può identificare che non si tratta di una vulnerabilità e annotarla con l'ID regola appropriato:

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String SERVICE_PASSWORD = "password";
```

Tuttavia, se il codice fosse effettivamente questo:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String SERVICE_PASSWORD = "password";
```

Quindi il cliente deve prendere a cuore l'avviso di SonarQube e rimuovere la password hardcoded. Dovranno comunque aggiungere l' `@SuppressWarnings` annotazione, dal momento che la regola SonarQube viene attivata dal termine `password`.

>[!NOTE]
>
>È consigliabile rendere l’ `@SuppressWarnings` annotazione il più possibile specifica, ovvero annotare solo l’istruzione o il blocco specifici che causa il problema, e annotare a livello di classe.

