---
title: Introduzione a Cloud Manager per AMS
description: Inizia qui per scoprire Cloud Manager per Adobe Managed Services (AMS) e come consente alle organizzazioni di gestire autonomamente Adobe Experience Manager nel cloud.
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
source-git-commit: 22d40a1f07f56ee7a7dddb4897e4079f1e346674
workflow-type: tm+mt
source-wordcount: '1292'
ht-degree: 10%

---


# Introduzione a [!UICONTROL Cloud Manager] per AMS {#introduction-to-cloud-manager}

Inizia qui per scoprire Cloud Manager, ad Adobe Manage Services (AMS) e come consente alle organizzazioni di gestire autonomamente Adobe Experience Manager nel cloud.

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="Introduzione a Cloud Manager per AMS"
>abstract="Consente alle organizzazioni di gestire autonomamente Adobe Experience Manager nel cloud. Include un framework di integrazione continua e distribuzione continua (CI/CD, Continuous Integration/Continuous Delivery) che consente ai team IT e ai partner dell’implementazione di accelerare la distribuzione di personalizzazioni o aggiornamenti senza compromettere prestazioni o sicurezza."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=en#cloud-manager" text="Creare programmi"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=en#cloud-manager" text="Creare ambienti"

## Introduzione {#introduction}

[!UICONTROL Cloud Manager] Adobe Experience Manager offre agli sviluppatori la possibilità di creare esperienze cliente di impatto attraverso flussi di lavoro semplificati, basati sulle best practice di Adobe Experience Manager. Le pipeline CI/CD ottimizzate per Adobe Experience Manager ti consentono di unire facilmente i flussi di lavoro di sviluppo semplicemente archiviando il codice che può poi essere pronto per la produzione. Durante la fase di creazione, gli aggiornamenti del codice personalizzato vengono accuratamente testati in base alle best practice per fornire applicazioni affidabili ai clienti. Cloud Manager utilizza un approccio API aperto e consente di integrarsi con i sistemi senza interrompere i processi e gli strumenti esistenti.

>[!NOTE]
>
>Questa documentazione descrive in modo specifico le funzioni e le funzioni di Cloud Manager per Adobe Managed Services (AMS).
>
>La documentazione equivalente per AEM as a Cloud Service si trova nella sezione [AEM documentazione as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/home.html)

Con Cloud Manager, il team di sviluppo beneficia delle seguenti funzionalità:

* Integrazione continua/consegna continua (CI/CD) di codice per ridurre i tempi di commercializzazione da mesi/settimane a giorni/ore

* Ispezione del codice, test delle prestazioni e convalida di sicurezza basati sulle best practice prima di passare alla produzione per ridurre al minimo le interruzioni di produzione

* Connettività API per integrare i processi DevOps esistenti

* Scalabilità automatica che rileva in modo intelligente la necessità di una maggiore capacità e porta automaticamente online ulteriori segmenti di Dispatcher/pubblicazione

Questa immagine illustra il flusso di processo CI/CD utilizzato in [!UICONTROL Cloud Manager]:

![Flusso CI/CD](/help/assets/screen_shot_2018-05-12at73843pm.png)

## Funzioni principali in [!UICONTROL Cloud Manager] {#key-features-in-cloud-manager}

Di seguito sono riportate alcune approfondimenti su alcune funzioni chiave di Cloud Manager.

### Interfaccia self-service {#self-service-interface}

Interfaccia utente per [!UICONTROL Cloud Manager] consente di accedere e gestire facilmente l’ambiente cloud e la pipeline CI/CD per le applicazioni Adobe Experience Manager.

È possibile definire indicatori di prestazioni chiave specifici per l’applicazione (KPI) (come le visualizzazioni di picco della pagina al minuto e il tempo di risposta previsto per un caricamento di pagina) che costituiscono la base per la misurazione di una distribuzione di successo. È possibile definire facilmente ruoli e autorizzazioni per i diversi membri del gruppo. L&#39;interfaccia self-service ti mette il controllo nelle mani, ma offre anche collegamenti alle risorse delle best practice e l&#39;accesso agli esperti all&#39;interno dell&#39;Adobe che possono fornire la guida necessaria in base alle esigenze.

Per esplorare e iniziare a utilizzare [!UICONTROL Cloud Manager]Interfaccia utente, visualizza il documento [Primo accesso](/help/getting-started/first-time-login.md)

### Pipeline CI/CD {#ci-cd-pipeline}

Una delle funzionalità principali di [!UICONTROL Cloud Manager] è la capacità di sfruttare una pipeline CI/CD ottimizzata per velocizzare la distribuzione di codice personalizzato o aggiornamenti, come l’aggiunta di nuovi componenti sul sito web.

Attraverso il [!UICONTROL Cloud Manager] Interfaccia utente, puoi configurare e avviare la pipeline CI/CD. Come parte di questa pipeline, viene eseguita un’analisi approfondita del codice per garantire che solo le applicazioni di alta qualità passino all’ambiente di produzione.

Per ulteriori informazioni sulla configurazione della pipeline, consulta [!UICONTROL Cloud Manager]Interfaccia utente, visualizzare i documenti [Configurazione delle pipeline di produzione](/help/using/production-pipelines.md) e [Configurazione delle pipeline non di produzione.](/help/using/non-production-pipelines.md)

### Modalità di distribuzione flessibili {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] offre modalità di distribuzione flessibili e configurabili che consentono di fornire esperienze in base alle esigenze aziendali in continua evoluzione.

Con una modalità di attivazione automatica, il codice viene distribuito automaticamente in un ambiente in base a eventi specifici, ad esempio il commit del codice. È inoltre possibile programmare le distribuzioni del codice durante intervalli di tempo specifici, anche al di fuori dell’orario di lavoro.

Indipendentemente dall’attivazione della distribuzione, i controlli di qualità vengono sempre eseguiti come parte dell’esecuzione della pipeline CI/CD ogni volta che viene attivata una distribuzione. I controlli di qualità includono, l’ispezione del codice, i test di sicurezza e i test delle prestazioni, tutti elementi preconfigurati senza alcun impegno da parte tua o dei tuoi partner.

Per ulteriori informazioni sulla distribuzione del codice e sui controlli di qualità, consulta il documento [Distribuzione del codice.](/help/using/code-deployment.md)

## Funzionalità opzionali in Cloud Manager {#optional-features-in-cloud-manager}

Cloud Manager offre funzionalità avanzate aggiuntive che possono essere utili per il progetto a seconda della configurazione dell’ambiente e delle esigenze specifiche. Se queste funzioni sono di tuo interesse, contatta il tuo Customer Success Engineer (CSE) o il rappresentante di Adobe per discuterne ulteriormente.

### Scalabilità automatica {#autoscaling}

Quando l&#39;ambiente di produzione è soggetto a un carico insolitamente elevato, [!UICONTROL Cloud Manager] rileva la necessità di una capacità aggiuntiva e la rende automaticamente disponibile utilizzando la funzione di scalabilità automatica.

In tal caso, [!UICONTROL Cloud Manager] attiva automaticamente il processo di provisioning in scala automatica, invia una notifica dell’evento di scalabilità automatica e in pochi minuti rende disponibile ulteriore capacità. Il provisioning della capacità aggiuntiva nell’ambiente di produzione, nelle stesse aree e in corrispondenza delle stesse specifiche di sistema dei nodi Dispatcher/pubblicazione in esecuzione.

La funzione di scalabilità automatica si applica solo al livello Dispatcher/publishing e viene eseguita con un metodo di scalabilità orizzontale, con almeno un segmento aggiuntivo di una coppia Dispatcher/pubblicazione fino a un massimo di dieci segmenti. La capacità aggiuntiva fornita verrà scalata manualmente entro un periodo di dieci giorni lavorativi, come determinato dal CSE (Customer Success Engineer).

>[!NOTE]
>
>Se sei interessato a verificare se la scalabilità automatica è appropriata per la tua applicazione, contatta il tuo rappresentante CSE o Adobe.

### Implementazioni blu/verdi {#blue-green}

L&#39;implementazione blu/verde è una tecnica che riduce i tempi di inattività e i rischi eseguendo due ambienti di produzione identici chiamati blu e verde.

In qualsiasi momento, solo uno degli ambienti è live, con l&#39;ambiente live che serve tutto il traffico di produzione. In generale, il blu è l&#39;ambiente attualmente in diretta e il verde è inattivo.

* La distribuzione blu/verde è un componente aggiuntivo per le pipeline CI/CD di Cloud Manager in cui viene creato e utilizzato un secondo set di istanze di pubblicazione e Dispatcher (verde) per le distribuzioni. Le istanze verdi vengono quindi collegate al load balancer di produzione e le istanze precedenti (blu) vengono rimosse e terminate.
* Questa implementazione di blu/verde considera le istanze come transitorie e ogni iterazione di una pipeline blu/verde creerà un nuovo set di server di pubblicazione e Dispatcher.
* Verrà creato un bilanciamento del carico verde come parte della configurazione. Questo load balancer non cambierà mai ed è ciò a cui puntare il tuo URL verde o &quot;test&quot;.
* Durante una distribuzione blu/verde, verrà creata una replica esatta dei livelli di pubblicazione/Dispatcher esistenti (come letto dal TDL).

#### Flusso di distribuzione blu/verde {#flow}

Quando la distribuzione blu/verde è abilitata, il flusso di distribuzione è diverso dal flusso di distribuzione standard del Cloud Service.

| Incremento | Installazione blu/verde | Distribuzione standard |
|---|---|---|
| 1 | Implementazione per l&#39;authoring | Implementazione per l&#39;authoring |
| 2 | Pausa per test | - |
| 3 | L&#39;infrastruttura verde viene creata | - |
| 4 | Implementazione su livelli di pubblicazione/Dispatcher verdi | Distribuzione all&#39;editore |
| 5 | Pausa per test (fino a 24 ore) | - |
| 6 | L&#39;infrastruttura verde viene aggiunta al load balancer di produzione | - |
| 7 | L&#39;infrastruttura blu viene rimossa dal load balancer di produzione- |
| 8 | L&#39;infrastruttura blu viene terminata automaticamente | - |

#### Implementazione blu/verde {#implementing}

Tutti gli utenti AMS che utilizzano Cloud Manager per le distribuzioni di produzione possono utilizzare la distribuzione blu/verde. Tuttavia, l’utilizzo della distribuzione blu/verde richiede una convalida aggiuntiva degli ambienti e la configurazione tramite un CSE di Adobe.

Se sei interessato alla distribuzione blu/verde, considera i seguenti requisiti e limitazioni e contatta il tuo CSE.

#### Requisiti e limitazioni {#limitations}

* Blu/verde è disponibile solo per coppie di pubblicazione/Dispatcher.
* Le coppie di anteprima Dispatcher/pubblicazione non fanno parte delle distribuzioni blu/verde.
* Ogni coppia Dispatcher/publish è identica a ogni altra coppia Dispatcher/publish.
* Blu/verde è disponibile solo nell&#39;ambiente di produzione.
* Blu/verde è disponibile in AWS e Azure.
* Blu/verde non è disponibile solo per i clienti Assets.
