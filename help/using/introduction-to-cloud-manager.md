---
title: Introduzione a Cloud Manager
seo-title: Introduzione a Cloud Manager
description: 'Questa pagina funge da punto di partenza per imparare a usare Cloud Manager. '
seo-description: 'Questa pagina funge da punto di partenza per l''apprendimento di Adobe AEM Cloud Manager ed evidenzia i vantaggi e le caratteristiche principali. '
uuid: 62 d 68 e 79-c 2 ba -4 d 8 b-ba 7 d -33709014 d 5 b 6
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: ebcc 91 a 5-be 9 e -4684-8146-d 88 f 4013 d 4 d 1
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Introduzione a [!UICONTROL Cloud Manager]{#introduction-to-cloud-manager}

## Introduzione {#introduction}

[!UICONTROL Cloud Manager], parte dei servizi cloud gestiti Adobe, consente alle organizzazioni di gestire autonomamente Experience Manager nel cloud. Include un framework di integrazione continua e continua (CI/CD) che consente ai team IT e ai partner di implementazione di accelerare la distribuzione di personalizzazioni o aggiornamenti senza compromettere le prestazioni o la sicurezza.

Utilizzando il [!UICONTROL Cloud Manager] portale dei clienti self-service **, le Organizzazioni** possono eseguire/sfruttare quanto segue:

* **Integrazione continua/Distribuzione** continua del codice per ridurre il tempo sul mercato da mesi/settimane a giorni/ore.
* **Analisi dei codici, test delle prestazioni e convalida della sicurezza** in base alle best practice prima di eseguire il push per ridurre al minimo le interruzioni di produzione.
* **Distribuzione automatica, pianificata o manuale** anche all&#39;esterno delle ore di ufficio per garantire la massima flessibilità e il controllo.
* **Questa funzione** rileva in modo intelligente la necessità di aumentare la capacità e introduce automaticamente altri segmenti di dispatcher/pubblicazione online online.

L&#39;immagine seguente illustra il flusso di processo CI/CD utilizzato in [!UICONTROL Cloud Manager]:

![](assets/screen_shot_2018-05-12at73843pm.png)

## Funzioni principali [!UICONTROL Cloud Manager]{#key-features-in-cloud-manager}

Le organizzazioni possono sfruttare le seguenti funzionalità, con [!UICONTROL Cloud Manager]:

### Interfaccia self-service {#self-service-interface}

L&#39;interfaccia utente (interfaccia utente) consente [!UICONTROL Cloud Manager] ai clienti di accedere e gestire facilmente l&#39;ambiente cloud e la pipeline CI/CD per le applicazioni Experience Manager.

I clienti definiscono indicatori di prestazioni chiave specifici dell&#39;applicazione (KPI): visualizzazioni di pagina picco per minuto e tempo di risposta previsto per un caricamento di pagina, che in ultima analisi costituiscono la base per misurare una distribuzione corretta. I ruoli e le autorizzazioni per diversi membri del team possono essere definiti facilmente. Anche se la nuova interfaccia self-service riposiziona il controllo in mano, offre anche collegamenti alle best practice e agli esperti di Adobe che possono fornire le indicazioni necessarie a seconda delle esigenze.

Per esplorare e iniziare a usare [!UICONTROL Cloud Manager]l&#39;interfaccia utente, consulta [Accesso alla prima volta](https://helpx.adobe.com/experience-manager/cloud-manager/using/first-time-login.html).

### Pipeline CI/CD {#ci-cd-pipeline}

Una delle funzionalità principali di [!UICONTROL Cloud Manager] è la capacità di eseguire un pipeline CI/CD ottimizzata per velocizzare la distribuzione di codice personalizzato o aggiornamenti, ad esempio l&#39;aggiunta di nuovi componenti nel sito Web.

Tramite l&#39; [!UICONTROL Cloud Manager] interfaccia utente, i clienti possono configurare e arrestare la loro pipeline CI/CD. Durante questa pipeline, viene eseguita una scansione dettagliata del codice per garantire che solo le applicazioni di alta qualità passino all&#39;ambiente di produzione.

Per ulteriori informazioni sulla configurazione della pipeline dall [!UICONTROL Cloud Manager]&#39;interfaccia utente, consulta [Configurazione della pipeline CI/CD](https://helpx.adobe.com/experience-manager/cloud-manager/using/configuring-pipeline.html).

### Modalità di distribuzione flessibili {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] offre ai clienti modalità di distribuzione flessibili e configurabili in modo che possano distribuire esperienze in base alle mutevoli esigenze aziendali.

Con una modalità di attivazione automatica, il codice viene automaticamente distribuito in un ambiente basato su eventi specifici quali l&#39;impegno del codice. Potete anche pianificare le distribuzioni del codice durante determinate cornici temporali, anche all&#39;esterno di un orario lavorativo.

Indipendentemente dal trigger di distribuzione, i controlli di qualità vengono sempre eseguiti durante l&#39;esecuzione della pipeline CI/CD, ogni volta che viene attivata una distribuzione. I controlli di qualità, l&#39;analisi di sicurezza, il testing di sicurezza e i test delle prestazioni sono distribuiti sulla casella senza alcuno sforzo da parte dei clienti o dei loro partner.

Per ulteriori informazioni sulla distribuzione di codice e controlli di qualità, consulta [Implementare il codice](deploying-code.md)

### Oscuramento automatico {#autoscaling}

[!UICONTROL Cloud Manager] rileva la necessità di ulteriore capacità quando l&#39;ambiente di produzione è soggetto a un carico insolitamente elevato e introduce automaticamente una capacità aggiuntiva online tramite funzione di oscuramento.

Durante un evento di oscuramento automatico, attiva [!UICONTROL Cloud Manager] automaticamente il processo di provisioning automatico, invia una notifica dell&#39;evento di oscuramento automatico e reattiva la capacità aggiuntiva entro minuti. La capacità aggiuntiva verrà resa disponibile nell&#39;ambiente di produzione, nella stessa regione o nella stessa regione, e le stesse specifiche del sistema dei nodi Dispatcher/Publish.

La funzione di oscuramento automatico si applica solo al livello Dispatcher/Pubblicazione e verrà sempre eseguita utilizzando un metodo di ridimensionamento orizzontale, con almeno un segmento aggiuntivo di una coppia Dispatcher/Pubblicazione e fino a un massimo di dieci segmenti. Eventuali capacità aggiuntive fornite verranno ridimensionate manualmente entro dieci giorni lavorativi come determinato dal CSE (Customer Success Engineer).
