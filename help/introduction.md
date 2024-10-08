---
title: Introduzione a Cloud Manager per AMS
description: Inizia qui per scoprire Cloud Manager per Adobe Managed Services (AMS) e come consente alle organizzazioni di gestire autonomamente Adobe Experience Manager nel cloud.
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
source-git-commit: 4c4a2688cab8e5c81efa4b7b5e26f3c7b5dc30d6
workflow-type: ht
source-wordcount: '1256'
ht-degree: 100%

---


# Introduzione a [!UICONTROL Cloud Manager] per AMS {#introduction-to-cloud-manager}

Inizia qui per scoprire Cloud Manager per Adobe Managed Services (AMS) e come consente alle organizzazioni di gestire autonomamente Adobe Experience Manager nel cloud.

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="Introduzione a Cloud Manager per AMS"
>abstract="Consente alle organizzazioni di gestire autonomamente Adobe Experience Manager nel cloud. Include un framework di integrazione continua e distribuzione continua (CI/CD) che consente ai team IT e ai partner dell’implementazione di accelerare la distribuzione di personalizzazioni o aggiornamenti senza compromettere le prestazioni o la sicurezza."
>additional-url="https://experienceleague.adobe.com/it/docs/experience-manager-learn/cloud-service/cloud-manager/programs#cloud-manager" text="Creare programmi"
>additional-url="https://experienceleague.adobe.com/it/docs/experience-manager-learn/cloud-service/cloud-manager/environments#cloud-manager" text="Creare ambienti"

## Introduzione {#introduction}

[!UICONTROL Cloud Manager] per Adobe Experience Manager offre agli sviluppatori la possibilità di creare esperienze cliente significative attraverso flussi di lavoro semplificati, basati sulle best practice di Adobe Experience Manager. Le pipeline CI/CD ottimizzate per Adobe Experience Manager ti consentono di unire facilmente i flussi di lavoro di sviluppo semplicemente archiviando il codice, che può poi essere spostato per essere pronto alla produzione. Durante la fase di creazione, gli aggiornamenti del codice personalizzato vengono accuratamente testati in base alle best practice per fornire ai clienti applicazioni affidabili. Cloud Manager utilizza un approccio API aperto e consente di integrarsi con i sistemi senza interrompere i processi e gli strumenti esistenti.

>[!NOTE]
>
>Questa documentazione descrive in modo specifico le funzioni di Cloud Manager per Adobe Managed Services (AMS).
>
>La documentazione equivalente per AEM as a Cloud Service si trova nella [documentazione di AEM as a Cloud Service](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/implementing/home).

Con Cloud Manager, il team di sviluppo potrà usufruire delle seguenti funzionalità:

* CI/CD (Continuous integration/continuous delivery) del codice per ridurre i tempi di realizzazione da mesi/settimane a giorni/ore.

* Ispezione del codice, test delle prestazioni e convalida di sicurezza basati sulle best practice ed effettuati prima del passaggio alla fase produttiva, al fine di ridurre al minimo le interruzioni di produzione.

* Connettività API per integrare i processi DevOps esistenti.

* Funzione di scalabilità automatica che rileva in modo intelligente la necessità di capacità aggiuntive e porta automaticamente online altri segmenti Dispatcher/pubblicazione.

![Flusso CI/CD](/help/assets/screen_shot_2018-05-12at73843pm.png)Il flusso di processo CI/CD utilizzato in [!UICONTROL Cloud Manager].

## Funzioni principali in [!UICONTROL Cloud Manager] {#key-features-in-cloud-manager}

Di seguito sono riportati approfondimenti su alcune funzioni principali di Cloud Manager.

### Interfaccia self-service {#self-service-interface}

L’interfaccia utente di [!UICONTROL Cloud Manager] ti consente di accedere e gestire facilmente l’ambiente cloud e la pipeline CI/CD per le applicazioni di Adobe Experience Manager.

Puoi definire indicatori di prestazioni chiave (KPI, Key Performance Indicators) specifici per l’applicazione, come i picchi di visualizzazioni della pagina al minuto o i tempi di risposta previsti per il caricamento della pagina. Questi KPI fungono da base per misurare il successo dell’implementazione. È possibile definire facilmente ruoli e autorizzazioni per i diversi membri del gruppo. L’interfaccia self-service fornisce il controllo completo. Fornisce inoltre collegamenti alle risorse sulle best practice e accesso a esperti di Adobe per indicazioni, se necessario.

Per esplorare e iniziare a utilizzare l’interfaccia utente di [!UICONTROL Cloud Manager], consulta il documento [Primo accesso](/help/getting-started/first-time-login.md).

### Pipeline CI/CD {#ci-cd-pipeline}

Una delle funzionalità principali di [!UICONTROL Cloud Manager] è la capacità di sfruttare una pipeline CI/CD ottimizzata per velocizzare la distribuzione di codici personalizzati o aggiornamenti, come l’aggiunta di nuovi componenti sul sito Web.

Puoi configurare e avviare la pipeline CI/CD attraverso l’interfaccia utente di [!UICONTROL Cloud Manager]. Durante l’esecuzione della pipeline viene eseguita un’analisi approfondita del codice per garantire che solo le applicazioni di qualità elevata passino all’ambiente di produzione.

Per ulteriori informazioni sulla configurazione della pipeline dall’interfaccia utente di [!UICONTROL Cloud Manager], consulta i documenti [Configurazione delle pipeline di produzione](/help/using/production-pipelines.md) e [Configurazione delle pipeline non di produzione](/help/using/non-production-pipelines.md).

### Modalità di distribuzione flessibili {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] offre modalità di distribuzione flessibili e configurabili che consentono di distribuire esperienze in base alle esigenze aziendali in continua evoluzione.

Grazie alla modalità di attivazione automatica, il codice viene distribuito automaticamente in un ambiente in base a eventi specifici, come ad esempio il commit del codice. È inoltre possibile programmare le distribuzioni del codice durante archi temporali specifici, anche al di fuori dell’orario di lavoro.

Indipendentemente dalla modalità di trigger della distribuzione, ogni volta che ne viene attivata una vengono sempre eseguiti controlli di qualità come parte dell’esecuzione della pipeline CI/CD. I controlli di qualità, che comprendono l’ispezione del codice, i test di sicurezza e i test delle prestazioni, sono integrati nella soluzione e possono essere usati subito, senza alcuno sforzo, da te o dai tuoi partner.

Per ulteriori informazioni sulla distribuzione del codice e sui controlli di qualità, consulta il documento [Distribuzione del codice](/help/using/code-deployment.md).

## Funzioni facoltative in Cloud Manager {#optional-features-in-cloud-manager}

Cloud Manager offre funzioni avanzate aggiuntive che possono essere utili per il progetto a seconda della configurazione dell’ambiente e delle esigenze specifiche. Se queste funzionalità sono di tuo interesse, contatta il tuo Customer Success Engineer (CSE) o il rappresentante Adobe per discuterne ulteriormente.

### Scalabilità automatica {#autoscaling}

Quando l’ambiente di produzione è soggetto a un carico insolitamente elevato, [!UICONTROL Cloud Manager] rileva la necessità di una capacità aggiuntiva e la rende automaticamente disponibile online utilizzando la funzione di scalabilità automatica.

Durante un evento di scalabilità automatica, [!UICONTROL Cloud Manager] attiva automaticamente il processo di provisioning, invia una notifica dell’evento in corso e in pochi minuti rende disponibile la capacità necessaria. La capacità aggiuntiva viene eseguita nell’ambiente di produzione, nelle stesse aree e in conformità alle stesse specifiche di sistema dei nodi Dispatcher/pubblicazione in esecuzione.

La funzione di scalabilità automatica si applica al livello Dispatcher/pubblicazione, utilizzando la scalabilità orizzontale per aggiungere da uno a dieci segmenti di coppie Dispatcher/pubblicazione. Qualsiasi capacità aggiuntiva applicata verrà scalata manualmente entro un periodo di dieci giorni lavorativi, come determinato dal CSE (Customer Success Engineer).

>[!NOTE]
>
>Se hai interesse a verificare se la scalabilità automatica sia appropriata per la tua applicazione, contatta il tuo rappresentante CSE o Adobe.

### Distribuzioni blu/verdi {#blue-green}

La distribuzione blu/verde è una tecnica che riduce i tempi di inattività e i rischi eseguendo due ambienti di produzione identici chiamati blu e verde.

In qualsiasi momento, solo uno degli ambienti è live, con l’ambiente live che serve tutto il traffico di produzione. In generale, il blu è l’ambiente attualmente live e il verde è quello inattivo.

* La distribuzione blu/verde è un componente aggiuntivo per le pipeline CI/CD di Cloud Manager in cui per le distribuzioni viene creato e utilizzato un secondo set di istanze di pubblicazione e Dispatcher (verde). Le istanze verdi vengono collegate quindi al load balancer di produzione e le istanze precedenti (blu) vengono rimosse e terminate.
* Questa implementazione blu/verde considera le istanze come transitorie e ogni iterazione di una pipeline blu/verde crea un nuovo set di server di pubblicazione e Dispatcher.
* Viene creato un load balancer verde come parte della configurazione. Questo load balancer non cambierà mai ed è ciò a cui indirizzare il tuo URL verde o di “test”.
* Durante una distribuzione blu/verde, viene creata una replica esatta dei livelli di pubblicazione/Dispatcher esistenti.

#### Flusso di distribuzione blu/verde {#flow}

Quando la distribuzione blu/verde è abilitata, il flusso di distribuzione è diverso dal flusso di distribuzione standard di Cloud Service.

| Passaggio | Distribuzione blu/verde | Distribuzione standard |
|---|---|---|
| 1 | Distribuzione all’authoring | Distribuzione all’authoring |
| 2 | Pausa per test | - |
| 3 | Viene creata l’infrastruttura verde | - |
| 4 | Distribuzione ai livelli di pubblicazione/dispatcher verdi | Distribuzione all&#39;editore |
| 5 | Pausa per test (fino a 24 ore) | - |
| 6 | L&#39;infrastruttura verde viene aggiunta al load balancer di produzione | - |
| 7 | L&#39;infrastruttura blu viene rimossa dal load balancer di produzione |
| 8 | Pausa per approvazione finale (fino a 24 ore) | - |
| 9 | L&#39;infrastruttura blu viene terminata automaticamente | - |
| 10 | Completamenti pipeline | - |

#### Implementazione blu/verde {#implementing}

Tutti gli utenti AMS che utilizzano Cloud Manager per le distribuzioni di produzione possono utilizzare la distribuzione blu/verde. Tuttavia, l’utilizzo della distribuzione blu/verde richiede una convalida aggiuntiva degli ambienti e della configurazione da parte di un CSE di Adobe.

Se ti interessa la distribuzione blu/verde, prendi in considerazione i seguenti requisiti e limitazioni e contatta il CSE.

#### Requisiti e limitazioni {#limitations}

* Blu/verde è disponibile solo per coppie di pubblicazione/Dispatcher.
* Le coppie Dispatcher/pubblicazione di anteprima non fanno parte delle distribuzioni blu/verde.
* Ogni coppia Dispatcher/pubblicazione è identica a ogni altra coppia Dispatcher/pubblicazione.
* Blu/verde è disponibile solo nell’ambiente di produzione.
* Blu/verde è disponibile in AWS e in Azure.
* Blu/verde non è disponibile solo per i clienti Assets.
