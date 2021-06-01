---
title: Introduzione a Cloud Manager
seo-title: Introduzione a Cloud Manager
description: 'Questa pagina offre una guida introduttiva per Cloud Manager. '
seo-description: 'Questa pagina offre una guida introduttiva per Adobe AEM Cloud Manager e ne evidenzia vantaggi e principali funzioni. '
uuid: 62d68e79-c2ba-4d8b-ba7d-33709014d5b6
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: ebcc91a5-be9e-4684-8146-d88f4013d4d1
feature: Guida introduttiva
level: Beginner
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
source-git-commit: 81c14382821de6b2d249000a79799747a6d9cb19
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 79%

---

# Introduzione a [!UICONTROL Cloud Manager]{#introduction-to-cloud-manager}

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="Introduzione a Cloud Manager"
>abstract="Consente alle organizzazioni di gestire in modo autonomo gli Experienci Manager nel cloud. Include un framework di integrazione continua e distribuzione continua (CI/CD, Continuous Integration/Continuous Delivery) che consente ai team IT e ai partner dell’implementazione di accelerare la distribuzione di personalizzazioni o aggiornamenti senza compromettere prestazioni o sicurezza."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=en#cloud-manager" text="Creare programmi"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=en#cloud-manager" text="Creare ambienti"

## Introduzione {#introduction}

[!UICONTROL Cloud Manager], parte di Adobe Experience Manager (AEM) in Cloud, consente alle organizzazioni di gestire in modo autonomo gli Experienci Manager nel cloud. Include un framework di integrazione continua e distribuzione continua (CI/CD, Continuous Integration/Continuous Delivery) che consente ai team IT e ai partner dell’implementazione di accelerare la distribuzione di personalizzazioni o aggiornamenti senza compromettere prestazioni o sicurezza.

Questo sito di documentazione descrive in modo specifico le funzioni e le funzioni di Cloud Manager disponibili per i clienti di Adobe Managed Services (AMS). La documentazione sulle funzioni e sulle funzioni di Cloud Manager per i clienti AEM come Cloud Service si trova in [Implementazione di applicazioni per AEM come Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/home.html?lang=en).

Tramite il portale clienti self-service di [!UICONTROL Cloud Manager], le **organizzazioni** possono eseguire o sfruttare quanto segue:

* **Integrazione continua/distribuzione continua** del codice per ridurre i tempi di realizzazione da mesi/settimane a giorni/ore.
* **Ispezione del codice, test delle prestazioni e convalida di sicurezza** basati sulle procedure consigliate ed effettuati prima del passaggio alla fase produttiva, al fine di ridurre al minimo le interruzioni di produzione.
* **Distribuzione automatica, programmata o manuale** anche al di fuori dell’orario di lavoro, per garantire flessibilità e controllo di massimo grado.
* **Funzione di scalabilità automatica** che rileva in modo intelligente la necessità di capacità aggiuntive e porta automaticamente in linea altri segmenti Dispatcher/Publish.

L’immagine riportata di seguito illustra il flusso di processo CI/CD utilizzato in [!UICONTROL Cloud Manager]:

![](assets/screen_shot_2018-05-12at73843pm.png)

## Funzioni principali in [!UICONTROL Cloud Manager] {#key-features-in-cloud-manager}

Con [!UICONTROL Cloud Manager] le organizzazioni possono sfruttare le seguenti funzionalità:

### Interfaccia self-service {#self-service-interface}

L’interfaccia utente di [!UICONTROL Cloud Manager] offre ai clienti un accesso semplificato e la possibilità di gestire l’ambiente cloud e la pipeline CI/CD per le applicazioni di Experience Manager.

I clienti definiscono gli indicatori chiave di prestazioni (KPI, Key Performance Indicators) specifici per l’applicazione, come i picchi di visualizzazioni della pagina al minuto e i tempi di risposta previsti per il caricamento di una pagina, che in ultima analisi costituiscono la base per la misurazione di una distribuzione di successo. È possibile definire facilmente ruoli e autorizzazioni per i diversi membri del gruppo. Se da una parte la nuova interfaccia self-service riporta il controllo nelle mani dell’utente, offre anche collegamenti alle best practice e accesso ai consigli degli esperti di Adobe, in grado di fornire il supporto necessario secondo necessità.

Per esplorare e iniziare a utilizzare l&#39;interfaccia utente di [!UICONTROL Cloud Manager], consulta [Primo accesso](https://helpx.adobe.com/experience-manager/cloud-manager/using/first-time-login.html).

### Pipeline CI/CD {#ci-cd-pipeline}

Una delle funzionalità principali di [!UICONTROL Cloud Manager] è la capacità di sfruttare una pipeline CI/CD ottimizzata per velocizzare la distribuzione di codice personalizzato o aggiornamenti, come l’aggiunta di nuovi componenti sul sito web.

Attraverso l’interfaccia utente di [!UICONTROL Cloud Manager] i clienti possono configurare e avviare la pipeline CI/CD. Durante l’esecuzione della pipeline viene eseguita un’analisi approfondita del codice per garantire che solo le applicazioni di qualità elevata passino all’ambiente di produzione.

Per ulteriori informazioni sulla configurazione della pipeline dall’interfaccia utente di [!UICONTROL Cloud Manager], consulta [Configurare la pipeline CI/CD](https://helpx.adobe.com/experience-manager/cloud-manager/using/configuring-pipeline.html).

### Modalità di distribuzione flessibili {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] offre ai clienti delle modalità di distribuzione flessibili e configurabili, che consentono di distribuire esperienze personalizzate in base alle esigenze aziendali in continua evoluzione.

Grazie alla modalità di attivazione automatica, il codice viene distribuito automaticamente in un ambiente in base a eventi specifici, come ad esempio il commit del codice. È inoltre possibile programmare le distribuzioni del codice durante intervalli di tempo specifici, anche al di fuori dell’orario di lavoro.

Indipendentemente dalla modalità di attivazione della distribuzione, ogni volta che ne viene attivata una vengono sempre eseguiti controlli di qualità come parte dell’esecuzione della pipeline CI/CD. I controlli di qualità, che comprendono l’ispezione del codice, i test di sicurezza e i test delle prestazioni, sono integrati nella soluzione e possono essere usati subito, senza complessità, da parte dei clienti o dei partner.

Per ulteriori informazioni sulla distribuzione del codice e sui controlli di qualità, consulta [Implementare il codice](deploying-code.md)

### Scalabilità automatica {#autoscaling}

Quando l’ambiente di produzione è soggetto a un carico insolitamente elevato, [!UICONTROL Cloud Manager] rileva la necessità di una maggiore capacità e la rende automaticamente disponibile tramite la funzione di scalabilità automatica.

Durante un evento di scalabilità automatica, [!UICONTROL Cloud Manager] attiva automaticamente il processo di provisioning, invia una notifica dell’evento in corso e in pochi minuti rende disponibile la capacità necessaria. Questo avviene nell’ambiente di produzione, nelle stesse aree e in conformità alle stesse specifiche di sistema dei nodi Dispatcher/Publish in esecuzione.

La funzione di scalabilità automatica si applica solo al livello Dispatcher/Publish e viene sempre eseguita con un metodo di scalabilità orizzontale, con almeno un segmento aggiuntivo di una coppia Dispatcher/Publish e fino a un massimo di dieci segmenti. La capacità aggiuntiva fornita verrà scalata manualmente entro un periodo di dieci giorni lavorativi, come determinato dal CSE (Customer Success Engineer).

>[!NOTE]
>I clienti interessati a verificare se la scalabilità automatica è appropriata per la propria applicazione devono contattare il proprio rappresentante CSE o Adobe.
