---
title: Utilizzo di Cloud Manager
seo-title: Utilizzo di Adobe AEM Cloud Manager
description: Interfaccia utente di AEM Cloud Manager
seo-description: Interfaccia utente di Adobe AEM Cloud Manager
page-status-flag: never-activated
uuid: cef 44 d 35-75 ed -44 bb -9636-2 de 2 bca 5 e 458
contentOwner: jsyal
discoiquuid: c 37566 d 5-0 d 1 b -4 c 44-abd 7-b 271 ea 443 c 1 a
translation-type: tm+mt
source-git-commit: 4c1c6786db9b8972f9315bd2f12fc1752881492f

---


# Using Cloud Manager{#using-cloud-manager}

This section explains the User Interface (UI) for [!UICONTROL Cloud Manager] and explains the workflow from setting up the program to code deployment followed by quality checks.

## Prerequisiti {#prerequisites}

Before you get into the details of using the [!UICONTROL Cloud Manager], it is recommended to go though the following sections:

* [Comprendere i concetti prima di utilizzare [! UICONTROL Cloud Manager]](understanding-concepts.md)
* [Configurazione delle configurazioni generali per [! UICONTROL Cloud Manager]](setting-configurations-for-cloud-manager.md)

## Getting Started with [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Once you have setup the general configurations for [!UICONTROL Cloud Manager], you are ready to use the [!UICONTROL Cloud Manager].

1. Log in to the Adobe [!UICONTROL Experience Cloud] and you will see the list of solutions.

   ![](assets/screen_shot_2018-04-22at92951am.png)

1. Select the program and click on the top left icon to open [!UICONTROL Cloud Manager].

   ![](assets/screen_shot_2018-04-22at93346am.png)

## Setting Up Program {#setting-up-program}

Dopo l&#39;iscrizione, il proprietario aziendale dovrà effettuare una configurazione iniziale del programma. Ciò richiede l&#39;impostazione della descrizione del programma e la definizione dei KPI che verranno utilizzati per il test delle prestazioni. È possibile caricare una miniatura.

I KPI definiti fungono da linea di base per il test delle prestazioni che vengono trasmesse ogni volta che la pipeline viene eseguita.

>[!NOTE]
>
>The KPIs defined are measured on tests run on the **stage** environment. In genere, questi KPI vengono ridotti in base alle capacità dell&#39;ambiente dell&#39;area di visualizzazione.
>
>For example, a user expecting an average of 1000 page views per minute in their production environment and having four `dispatcher/publish` servers in production should scale this to 250 page views per minute (assuming their stage environment consists of only a single `dispatcher/publish` server pair).
>
>Inoltre, molti utenti avranno una rete CDN (Akamai, cloudfront) davanti al loro ambiente di produzione. Since [!UICONTROL Cloud Manager] tests against the stage environment directly, the KPI should reflect only the traffic expected to pass through the CDN, that is, the cache misses. In genere si tratta di un sottoinsieme relativamente piccolo del traffico di produzione totale.

### Using [!UICONTROL Cloud Manager] to define KPIs {#using-cloud-manager-to-define-kpis}

Per configurare il programma e definire i KPI, effettuate le seguenti operazioni:

1. Click **Setup Program** to start the setup process in [!UICONTROL Cloud Manager].
1. The **Edit Program Information** screen displays.

   Caricate una miniatura nel programma. You can also add a relevant description to your program and click **Next**.

1. The **Configure Users** screen displays.

   Potete configurare i ruoli del team e gli utenti. Fai clic su **Avanti**.

1. The **Configure General Business KPIs** screen displays.

   Potete definire i due KPI (aspettative per ogni distribuzione):

   1. Qual è il 95 ° tempo di risposta percentile accettabile?

      1. Valore consigliato - 3 secondi
   1. Quante visualizzazioni di pagina al minuto sono sotto il caricamento del picco?

      1. Valore consigliato - 200 pv/m


1. Click **Submit** to complete the setup wizard.

   You will see the home screen for [!UICONTROL Cloud Manager] change to **Deploy**.

## Available Environments {#available-environments}

The **Available Environments** in the [!UICONTROL Cloud Manager] lists all the managed AEM environments.

A ciascun ambiente elencato viene associato uno stato.

## Configuring Pipeline {#configuring-pipeline}

### Setting up Pipeline {#setting-up-pipeline}

>[!CAUTION]
>
>La pipeline non può essere impostata finché l&#39;archivio git non avrà almeno un ramo.

Before you start to deploy your code, you must configure your pipeline settings from the [!UICONTROL Cloud Manager].

To learn more about pipeline configuration, see **Pipeline Overview** section in ** [Understanding Concepts before Using [!UICONTROL Cloud Manager]](understanding-concepts.md)**.

>[!NOTE]
>
>Potete modificare le impostazioni della pipeline dopo l&#39;impostazione iniziale.

### Configuring Pipeline Settings from the [!UICONTROL Cloud Manager] {#configuring-pipeline-settings-from-the-cloud-manager}

Follow the steps below from the [!UICONTROL Cloud Manager] to configure the bahavior and preferences for your pipeline:

1. Access the **Branch** tab to set up the application branch.

   Selezionare il ramo git che si desidera impostare.

   >[!NOTE]
   >
   >I rami presenti nell&#39;archivio Git sono collegati al programma.

   ![](assets/screen_shot_2018-05-06at73604pm.png)

1. Access the **Environments** tab to select **Stage** and **Production** options.

   Potete definire trigger che avvia la pipeline:

   * **Manuale** : un utente deve fare clic manualmente nell&#39;interfaccia per avviare la pipeline.
   Ora definite i parametri che controllano la distribuzione di produzione. Le tre opzioni disponibili sono le seguenti:

   * **Usa approvazione dal vivo**- Una distribuzione deve essere approvata manualmente da un proprietario aziendale, un manager progetto o un manager distribuzione tramite l&#39; [!UICONTROL Cloud Manager] interfaccia utente.
   * **Utilizzo della Supervisione** CSE - Un CSE è coinvolto per avviare la distribuzione.
   ![](assets/screen_shot_2018-05-06at73715pm.png)

1. Access the **Testing** tab to define your testing criteria for your program.

   Ora potete configurare i parametri di test delle prestazioni.

   ![](assets/screen_shot_2018-05-06at73750pm.png)

## Deploying Code {#deploying-code}

Dopo aver configurato la pipeline (archivio, ambiente e ambiente di test), puoi distribuire il codice.

### Deploying Code from [!UICONTROL Cloud Manager] {#deploying-code-from-cloud-manager}

Segui i passaggi indicati di seguito per distribuire il codice nell&#39;ambiente di produzione:

1. Click **Deploy** from the [!UICONTROL Cloud Manager] to start the deployment process.
1. The **Stage Deployment** screen displays.

   Click **Build** to start the process.

1. Il processo completo di build prende in considerazione diversi parametri per controllare e distribuire il codice.

   I seguenti parametri sono controllati:

   **Distribuzione dell&#39;area di visualizzazione**

   * Archivio
   * Test di unità
   * Scansione codice
   * Implementato nell&#39;ambiente Stage
   **Test preproduzione**

   * Test di sicurezza
   * Test delle prestazioni
   >[!NOTE]
   >
   >Inoltre, potete visualizzare i registri o rivedere i risultati per i criteri di verifica indicati sopra.

## Results from Quality Checks {#results-from-quality-checks}

La pipeline contiene tre gate: Qualità del codice, Test delle prestazioni e testing di sicurezza.

Per ciascuno di questi gate, esiste una struttura a tre gradi per i problemi identificati dal gate.

* **Critical** - These are issues identified by the gate which cause an immediate failure of the pipeline.
* **Importante** : questi sono problemi identificati dal gate che provocano la messa in pausa della pipeline. Un manager distribuzione, un manager progetto o un proprietario aziendale può ignorare i problemi, nel qual caso la pipeline procede oppure possono accettare i problemi, nel qual caso la pipeline si interrompe con un errore.
* **Informazioni** : sono problemi identificati dal gate che sono forniti esclusivamente a scopo informativo e non hanno alcun impatto sull&#39;esecuzione della pipeline.

### Code Scanning {#code-scanning}

![](assets/screen_shot_2018-04-22at101443am.png)

### Performance Testing {#performance-testing}

*I test delle prestazioni* vengono [!UICONTROL Cloud Manager] implementati mediante un test per 30 minuti.

Durante la configurazione della pipeline, il manager distribuzione può stabilire il volume di traffico da indirizzare a ogni bucket. Possono scegliere ovunque e in tutti e tre i casi. La distribuzione del traffico è basata sul numero di bucket selezionati, ovvero se sono selezionati tutti e tre, il 33% delle visualizzazioni di pagina totale viene collocato verso ogni bucket; se sono selezionati due, 50% fa riferimento a ciascun set; Se è selezionata, il 100% del traffico passa a quel set.

Ad esempio, supponiamo che sia presente una suddivisione da 50% a 50% tra le Pagine Live Live e Nuove pagine (in questo esempio, Altre Pagine live non vengono utilizzate) e il set Nuove pagine contiene 3000 pagine. Le visualizzazioni di pagina per minuto KPI sono impostate su 200. Nel periodo di prova di 30 minuti:

* Each of the 25 pages in the Popular Live Pages set will be hit 240 times - `((200 &#42; 0.5) / 25) &#42; 30 = 120`
* Each of the 3000 pages in the New Pages set will be hit once - `((200 &#42; 0.5) / 3000) &#42; 30 = 1`

![](assets/image2018-3-14_16-23-56.png)

### Performance Test Metrics {#performance-test-metrics}

Durante il periodo di prova, molte metriche vengono acquisite e confrontate con i KPI definiti dal proprietario aziendale o con gli standard impostati da AMS.

Vengono riportate utilizzando il sistema di tre livelli come segue:

### Three-Tier Gates while Running a Pipeline {#three-tier-gates-while-running-a-pipeline}

La pipeline presenta tre gate come Qualità codice, Test prestazioni e Verifica di sicurezza.

Per ciascuno di questi gate, esiste una struttura a tre gradi per i problemi identificati dal gate:

* **Critico**: Questi sono problemi identificati dal gate che causano un errore immediato della pipeline.
* **Importante**: Questi sono problemi identificati dal gate che provocano la messa in pausa della pipeline. Un manager distribuzione, un manager progetto o un proprietario aziendale può ignorare i problemi, nel qual caso la pipeline procede oppure possono accettare i problemi, nel qual caso la pipeline si interrompe con un errore.
* **Informazioni**: Si tratta di problemi identificati dal gate che sono forniti esclusivamente a scopo informativo e non hanno alcun impatto sull&#39;esecuzione della pipeline.

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

### Security Testing {#security-testing}

[!UICONTROL Cloud Manager] esegue le verifiche *Heath Security Heath Check* esistenti dopo la distribuzione e ne segnala lo stato tramite l&#39;interfaccia utente. I risultati vengono aggregati da tutte le istanze AEM nell&#39;ambiente.

Se una delle istanze segnala un errore per un segno di stato specificato, l&#39;intero ambiente non riesce. Come per la qualità del codice e il test delle prestazioni, questi controlli sanitari sono organizzati in categorie e segnalati mediante il sistema di tre livelli. L&#39;unica distinzione consiste nel fatto che non esiste alcuna soglia nel caso di test di sicurezza. Tutti i controlli dello stato sono semplicemente passati o non vanno a buon fine.

I controlli correnti sono:

| **Verifica stato** | **Categoria** |
|---|---|
| Compatibilità Attach Api di firewall deserializzazione | Critico |
| Firewall deserializzazione funzionale | Critico |
| Firewall deserializzazione caricato | Critico |
| Generazione nome nodo autorizzabile | Critico |
| Account di login predefiniti | Critico |
| Sling Get Servlet | Critico |
| Configurazione dispatcher CQ | Critico |
| Configurazione manager libreria CQ HTML | Critico |
| Sling Java Script Handler | Critico |
| Sling Jsp Script Handler | Critico |
| Sling Referrer Filter | Critico |
| Configurazione SSL | Critico |
| Accesso standard profilo utente | Critico |
| Supporto CRXDE | Importante |
| Verifica stato DavEx | Importante |
| Pacchetti contenuti di esempio | Importante |
| Configurazione filtri WCM | Importante |
| Verifica stato WebDAV | Importante |
| Configurazione server Web | Importante |
| Utenti replica e trasporto | Info |

### Quality Check Implementation by SonarQube {#quality-check-implementation-by-sonarqube}

Come parte della pipeline, come illustrato qui sopra, il codice viene analizzato. Attualmente, viene implementato da sonarqube. Abbiamo 93 regole che combinano regole Java generiche e regole specifiche di AEM (incluse alcune dal set di regole esistente di Cognifide). A list of these rules can be found here: [code-quality-rules.xlsx](/help/using/assets/code-quality-rules.xlsx)

Da queste regole, vengono calcolate diverse metriche, alcune delle quali vengono utilizzate come gate di qualità prima di consentire una distribuzione all&#39;ambiente dell&#39;area di visualizzazione.

Queste sono le soglie correnti:

| Nome | Definizione | Categoria | Soglia non riuscita |
|--- |--- |--- |--- |
| Valutazione della sicurezza | A = 0 Vulnerability <br/>B = at least 1 Minor Vulnerability<br/> C = at least 1 Major Vulnerability <br/>D = at least 1 Critical Vulnerability <br/>E = at least 1 Blocker Vulnerability | Critico | &lt; B |
| Valutazione affidabilità | A = 0 Bug <br/>B = at least 1 Minor Bug <br/>C = at least 1 Major Bug <br/>D = at least 1 Critical Bug E = at least 1 Blocker Bug | Importante | &lt; C |
| Valutazione della capacità | Outstanding remediation cost for code smells is: <br/><ul><li>&lt; = 5% dell&#39;ora che è già entrato nell&#39;applicazione, la valutazione è A </li><li>Tra 6 e 10% la valutazione è una B </li><li>Tra 11 e 20% la valutazione è C </li><li>tra 21 e 50% la valutazione è D</li><li>anything over 50% is an E</li></ul> | Importante | &lt; A |
| Copertura | A mix of line coverage and condition coverage using this formula: <br/>`Coverage = (CT + CF + LC)/(2*B + EL)`  <br/>where: CT = conditions that have been evaluated to &#39;true&#39; at least once <br/>CF = conditions that have been evaluated to &#39;false&#39; at least once <br/>LC = covered lines = lines_to_cover - uncovered_lines <br/><br/> B = total number of conditions <br/>EL = total number of executable lines (lines_to_cover) | Importante | &lt; 50% |
| Test unità ignorati | Numero di test unità ignorati. | Info | &gt; 1 |
| Apri problemi | Tipi di problemi complessivi - Vulnerabilità, bug e porzioni di codice | Info | &gt; 1 |
| Linee duplicate | Numero di righe coinvolte in blocchi duplicati. <br/>Perché un blocco di codice venga considerato duplicato: <ul><li> **Progetti non Java:**</li><li>Ci devono essere almeno 100 token consecutivi e duplicati.</li><li>I token devono essere distribuiti almeno su: </li><li>30 righe di codice per COBOL </li><li>20 righe di codice per ABAP </li><li>10 righe di codice per altre lingue</li></ul><ul><li>**Progetti Java:**</li><li> Devono esserci almeno 10 istruzioni successive e duplicate, indipendentemente dal numero di token e righe.</li></ul>Le differenze di rientro e di stringa letterali vengono ignorate durante la rilevazione delle duplicazioni. | Info | &gt; 1% |

### False Positives {#false-positives}

Il processo di scansione della qualità non è perfetto e a volte identificherà in modo non corretto i problemi che non sono realmente problematici. This is called a *false positive* (although *false negative* would probably be more semantically correct). In these cases, the source code can be annotated with the standard Java `@SuppressWarnings` annotation specifying the rule ID as the annotation attribute. Ad esempio, un problema comune sta nel fatto che la regola sonarqube per rilevare password hardcoded è molto liberale in merito al suo considerato una password hardcoded.

Per esaminare un esempio specifico, questo codice sarebbe abbastanza comune in un progetto AEM con codice per la connessione ad alcuni servizi esterni:

```java
@Property(label = "Service Password")
private static final String SERVICE_PASSWORD = "password";
```

Sonarqube lo alzerà come vulnerabilità di blocco. In questo caso, il cliente può identificare che non si tratta di una vulnerabilità e di annotarla con l&#39;ID regola appropriato:

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String SERVICE_PASSWORD = "password";
```

Tuttavia, se il codice è effettivamente stato questo:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String SERVICE_PASSWORD = "password";
```

Quindi, il cliente deve prendere l&#39;avviso di sonarqube e rimuovere la password hardcoded. They will still, however, need to add the `@SuppressWarnings` annotation since the SonarQube rule is actually being triggered by the term `password`.

>[!NOTE]
>
>It is a best practice to make the `@SuppressWarnings` annotation as specific as possible, i.e. annotate only the specific statement or block causing the issue, it is possible to annotate at a class level.

