---
title: Introduzione a Cloud Manager
seo-title: Introduzione a Cloud Manager
description: 'Questa pagina funge da punto di partenza per imparare a utilizzare Cloud Manager. '
seo-description: 'Questa pagina funge da punto di partenza per imparare a usare Adobe AEM Cloud Manager ed evidenzia i vantaggi e le funzioni chiave. '
uuid: 62 d68e79-c2ba-4d8b-ba7d-33709014d5b6
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduzione
discoiquuid: ebcc91a5-be9e-4684-8146-d88f4013d4d1
translation-type: tm+mt
source-git-commit: d7c9ab3795fb3df02ab7dffd1328760ccd914a18

---


# Introduzione a [!UICONTROL Cloud Manager]{#introduction-to-cloud-manager}

## Introduzione {#introduction}

[!UICONTROL Cloud Manager], parte dei servizi Adobe Managed Cloud, consente alle organizzazioni di gestire autonomamente Experience Manager nel cloud. Include un framework di integrazione continua e consegna continua (CI/CD) che consente ai team IT e ai partner di implementazione di accelerare la fornitura di personalizzazioni o aggiornamenti senza compromettere le prestazioni o la sicurezza.

Tramite il portale [!UICONTROL Cloud Manager] dei clienti self-service, **le organizzazioni** possono eseguire o sfruttare i seguenti elementi:

* **Integrazione continua / Consegna** continua del codice per ridurre il tempo sul mercato da mesi/settimane a giorni/ore.
* **Ispezione del codice, test delle prestazioni e convalida** della sicurezza basati sulle best practice prima di passare alla produzione per ridurre al minimo le interruzioni di produzione.
* **Implementazione** automatica, programmata o manuale anche al di fuori delle ore di lavoro per garantire la massima flessibilità e controllo.
* **La funzione di ridimensionamento automatico** rileva in modo intelligente la necessità di una maggiore capacità e porta automaticamente online altri segmenti Dispatcher/Publish.

La seguente immagine illustra il flusso di processo CI/CD utilizzato in [!UICONTROL Cloud Manager]:

![](assets/screen_shot_2018-05-12at73843pm.png)

## Funzioni principali in [!UICONTROL Cloud Manager]{#key-features-in-cloud-manager}

Le organizzazioni possono sfruttare le seguenti funzionalità, con [!UICONTROL Cloud Manager]:

### Interfaccia self-service {#self-service-interface}

L’interfaccia utente [!UICONTROL Cloud Manager] consente ai clienti di accedere e gestire facilmente l’ambiente cloud e la pipeline CI/CD per le applicazioni Experience Manager.

I clienti definiscono indicatori prestazioni chiave (KPI, Key Performance Indicators) specifici per l'applicazione: visualizzazioni della pagina di picco al minuto e tempo di risposta previsto per un caricamento di pagina, che in ultima analisi costituiscono la base per la misurazione di un'implementazione di successo. I ruoli e le autorizzazioni per i diversi membri del team possono essere facilmente definiti. La nuova interfaccia self-service permette di mettere il controllo nelle mani degli utenti, ma offre anche collegamenti alle best practice e l'accesso agli esperti di Adobe che possono fornire le necessarie indicazioni in base alle esigenze.

Per esplorare e iniziare a usare l’interfaccia utente [!UICONTROL Cloud Manager]di Adobe Connect, consulta Accesso [alla](https://helpx.adobe.com/experience-manager/cloud-manager/using/first-time-login.html)prima volta.

### Pipeline CI/CD {#ci-cd-pipeline}

Una delle funzionalità chiave di [!UICONTROL Cloud Manager] è la capacità di esercitare una pipeline CI/CD ottimizzata per velocizzare la distribuzione di codice personalizzato o aggiornamenti, come l'aggiunta di nuovi componenti sul sito web.

Attraverso l' [!UICONTROL Cloud Manager] interfaccia utente, i clienti possono configurare e avviare la propria pipeline CI/CD. Durante questo ciclo di produzione, viene eseguita un'analisi approfondita del codice per garantire che solo le applicazioni di alta qualità passino all'ambiente di produzione.

Per ulteriori informazioni sulla configurazione della pipeline dall' [!UICONTROL Cloud Manager]interfaccia utente, vedere [Configurare la pipeline](https://helpx.adobe.com/experience-manager/cloud-manager/using/configuring-pipeline.html)CI/CD.

### Modalità di distribuzione flessibili {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] offre ai clienti modalità di implementazione flessibili e configurabili in modo da poter distribuire esperienze in base alle esigenze aziendali in continua evoluzione.

Con una modalità di attivazione automatica, il codice viene distribuito automaticamente in un ambiente basato su eventi specifici come commit del codice. È inoltre possibile pianificare le distribuzioni del codice durante l'intervallo di tempo specificato, anche al di fuori dell'orario di lavoro.

Indipendentemente dal trigger di distribuzione, i controlli di qualità vengono sempre eseguiti nell'ambito dell'esecuzione della pipeline CI/CD, ogni volta che viene attivata una distribuzione. I controlli di qualità comprendono l'ispezione del codice, i test di sicurezza e i test delle prestazioni forniti senza alcun sforzo da parte dei clienti o dei partner.

Per ulteriori informazioni sulla distribuzione dei controlli di qualità e codice, consulta [Distribuzione del codice](deploying-code.md)

### Ridimensionamento automatico {#autoscaling}

[!UICONTROL Cloud Manager] rileva la necessità di una capacità aggiuntiva quando l'ambiente di produzione è soggetto a un carico insolitamente elevato e porta automaticamente una capacità aggiuntiva online tramite la funzione di scalabilità automatica.

Durante un evento di scalabilità automatica, attiva [!UICONTROL Cloud Manager] automaticamente il processo di provisioning di scalabilità automatica, invia una notifica dell'evento di scalabilità automatica e mette in linea la capacità aggiuntiva in pochi minuti. La capacità aggiuntiva verrà fornita nell'ambiente di produzione, nella stessa area o nelle stesse aree e sarà conforme alle stesse specifiche di sistema dei nodi Dispatcher/Publish in esecuzione.

La funzione di ridimensionamento automatico verrà applicata solo al livello Dispatcher/Publish e verrà sempre eseguita con un metodo di ridimensionamento orizzontale, con almeno un segmento aggiuntivo di una coppia Dispatcher/Publish e fino a un massimo di dieci segmenti. Qualsiasi capacità aggiuntiva fornita verrà scalata manualmente entro un periodo di dieci giorni lavorativi, come determinato dal CSE (Customer Success Engineer).
