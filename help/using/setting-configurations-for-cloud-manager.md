---
title: Configurazione delle configurazioni generali per Cloud Manager
seo-title: Configurazione delle configurazioni generali per Adobe AEM Cloud Manager
description: I prerequisiti per configurare Cloud Manager e gestire il contenuto dall'interfaccia utente.
seo-description: I prerequisiti per configurare Adobe AEM Cloud Manager e gestire il contenuto dall’interfaccia utente.
uuid: 65d795f9-aa97-4816-b66b-03b5ae961f47
contentOwner: jsyal
discoiquuid: 03241b88-8d28-401b-aa42-17ead6183cd8
translation-type: tm+mt
source-git-commit: 093e25fa1cf2f5cdc3d8ea0bffd5c02ade854a88

---


# Impostazione delle configurazioni generali per [!UICONTROL Cloud Manager]{#setting-up-general-configurations-for-cloud-manager}

Nella sezione seguente sono evidenziati i prerequisiti per la configurazione [!UICONTROL Cloud Manager] e la gestione del contenuto dall’interfaccia utente.

Questa pagina di sezione illustra i seguenti argomenti

* **Impostazione di utenti e ruoli**
* **Impostazione progetto applicazione AEM**
* **Configurazioni del dispatcher**
* **Tecniche consigliate per lo sviluppo**

Il diagramma seguente illustra le diverse funzioni che consentono [!UICONTROL Cloud Manager] di distribuire in modo continuo codice di qualità superiore:

![](assets/screen_shot_2018-05-01at81926pm.png)

## Impostazione di utenti e ruoli {#setting-up-users-and-roles}

I ruoli vengono gestiti [!UICONTROL Cloud Manager] da Adobe Admin Console. Le appartenenze a ruoli specifici vengono fornite aggiungendo l'utente a un profilo di [!UICONTROL Cloud Manager] prodotto in Admin Console.

>[!CAUTION]
>
>Per utilizzare [!UICONTROL Cloud Manager], è necessario disporre di un Adobe ID e del contesto di prodotto dei servizi gestiti Adobe.

Puoi assegnare appartenenze a ruoli specifici aggiungendo l’utente a un profilo di [!UICONTROL Cloud Manager] prodotto nell’Admin Console.

Create i seguenti ruoli utilizzando Admin Console per [!UICONTROL Cloud Manager]:

>[!NOTE]
>
>Adobe Admin Console fornisce una posizione centrale per la gestione delle adesioni Adobe in tutta l’organizzazione.
>
>Per ulteriori informazioni su Adobe Admin Console, consulta la documentazione di [Admin Console](https://helpx.adobe.com/enterprise/using/admin-console.html).

| **[!UICONTROL Cloud Manager]Ruoli** | **Descrizione** |
|---|---|
| Proprietario | Responsabile della definizione dei KPI, dell'approvazione delle implementazioni di produzione e della risoluzione di importanti errori a 3 livelli. |
| Program Manager | Utilizza [!UICONTROL Cloud Manager] per eseguire la configurazione del team, esaminare lo stato e visualizzare i KPI. Può approvare importanti fallimenti a 3 livelli. |
| Gestione distribuzione | Gestisce le operazioni di distribuzione. Utilizza [!UICONTROL Cloud Manager] per eseguire distribuzioni di fase/produzione. Può approvare importanti fallimenti a 3 livelli. Ha accesso git. |
| Sviluppatore | Sviluppa e verifica il codice applicazione personalizzato. Viene utilizzato principalmente [!UICONTROL Cloud Manager] per visualizzare lo stato. Ha accesso a git. |
| Customer Success Engineer | In genere supporta il successo dei clienti per i clienti AMS. Interagisce con [!UICONTROL Cloud Manager] lo scopo di eseguire distribuzioni che richiedono la sorveglianza CSE. |
| Content Author | Generalmente non interagisce con [!UICONTROL Cloud Manager]. Può usare [!UICONTROL Cloud Manager] il selettore programmi (dopo aver navigato da [!UICONTROL Experience Cloud]) per accedere ad AEM. |

### Utilizzo di Admin Console per configurare il team {#using-admin-console-to-set-up-team}

Per fornire agli [!UICONTROL Cloud Manager] utenti le autorizzazioni appropriate basate sul ruolo, un amministratore nell'organizzazione del cliente deve creare nuovi profili di prodotto nel contesto del [!UICONTROL AEM Managed Services] prodotto.

>[!NOTE]
>
>Per accedere alla console di amministrazione e configurare il team (utenti e ruoli), aprite un browser e visitate [https://adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise).

L'aggiunta di utenti (o gruppi) a questi profili di prodotto avviene tramite la normale funzionalità di Admin Console, come illustrato nella figura seguente:

1. Accedi ad Admin Console e fai clic su **Nuovo profilo** per aggiungere un nuovo profilo.

   ![](assets/admin_console_roles.png)

1. Compila i campi per impostare un nuovo ruolo per [!UICONTROL Cloud Manager].

   Immettete Nome **** profilo e **Descrizione** per creare un nuovo profilo. Inoltre, potete selezionare un gruppo **di** autorizzazioni per il profilo.

   Fate clic su **Fine** per completare il passaggio di creazione del profilo.

   ![](assets/screen_shot_2018-04-23at75014am.png)

## Impostazione progetto applicazione AEM {#aem-application-project-setup}

Prima di configurare il progetto dell'applicazione in [!UICONTROL Cloud Manager], è necessario considerare uno dei due scenari. Potresti essere un cliente nuovo o già esistente in AEM 6.4.

>[!NOTE]
>
>Per poter accedere a [!UICONTROL Cloud Manager], contatta il Customer Success Engineers (CSE) per ottenere l’URL e le credenziali per iniziare.

Potete impostare un progetto di applicazione per [!UICONTROL Cloud Manager], in base ai due scenari seguenti:

* **Nuovo progetto** AEM:

Un nuovo progetto AEM sfrutta il progetto esistente e lavora con [!UICONTROL Cloud Manager].

Per ulteriori informazioni, consultate [Guida introduttiva ad AEM 6.4](https://chl-author./content/help/en/experience-manager/6-4/sites/deploying/using/deploy.html). Per ulteriori informazioni, consulta Risorse [](https://www.adobe.com/marketing-cloud/experience-manager/resources.html?promoid=759X6WV8&mv=other) AEM.

* **Progetto** AEM esistente:

Un progetto AEM esistente deve confermare le regole per la configurazione del progetto. Puoi aggiornare l’installazione AEM esistente per ottenere nuove funzionalità e miglioramenti offerti in AEM 6.4 e iniziare a utilizzarla [!UICONTROL Cloud Manager]. Tali criteri dovrebbero funzionare con modifiche minime. Contatta il Customer Success Engineers (CSE) per assistenza.

Per ulteriori informazioni sull’aggiornamento dell’istanza di AEM alla versione 6.4, consulta [Aggiornamento ad AEM 6.4](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/upgrade.html).

### Configurazione dell'archivio {#setting-up-repository}

Viene fornito un unico archivio Git inizialmente vuoto per ogni programma in [!UICONTROL Cloud Manager]. Gli sviluppatori e i gestori della distribuzione ricevono l’URL git e le credenziali dal loro CSE.

Con queste informazioni, uno sviluppatore può aggiungere il proprio codice, seguendo le linee guida in **Project Set Up **nella sezione successiva, per completare i requisiti di configurazione prima di utilizzare [!UICONTROL Cloud Manager].

## Configurazioni del dispatcher {#dispatcher-configurations}

[!UICONTROL Cloud Manager] è in grado di distribuire i file di configurazione del server Web e del dispatcher, purché siano memorizzati nell’archivio git, oltre ai normali pacchetti di contenuti AEM.

Per sfruttare questa funzionalità, la build Maven produce un file zip che contiene due directory: ***conf*** e ***conf.d***.

Dopo la distribuzione in un'istanza del dispatcher, il contenuto di queste directory sovrascriverà il contenuto di tali directory nell'istanza del dispatcher. Poiché i file di configurazione del server Web e del dispatcher spesso richiedono informazioni specifiche per l'ambiente, per poter utilizzare correttamente questa funzionalità, è necessario innanzitutto lavorare con i loro Customer Success Engineers (CSE) per estrarre queste variabili di ambiente in /etc/sysconfig/httpd.

Per completare il processo iniziale nella configurazione del dispatcher, effettuate le operazioni seguenti:

1. Ottenete i file di configurazione di produzione correnti dal relativo CSE.
1. Rimuovete i dati specifici dell'ambiente codificato (ad esempio, IP del renderer di pubblicazione) e li sostituisce con le variabili.
1. Definite le variabili richieste nelle coppie chiave-valore per ciascun dispatcher di destinazione e richiede l'aggiunta di CSE a ***/etc/sysconfig/httpd*** in ogni istanza.
1. Sottoponete a test le configurazioni aggiornate sul palco, quindi richiedete a CSE di distribuirle in produzione per verificarne il corretto funzionamento.
1. Invia i file a git.
1. Distribuisci tramite [!UICONTROL Cloud Manager].

Il file zip effettivo può essere prodotto utilizzando il plug-in maven-assembly. I progetti generati utilizzando il modello Multimodulo Lazybones di AEM possono avere la giusta struttura di progetto Maven creata come parte della creazione del progetto.

>[!NOTE]
>
>La configurazione del dispatcher viene eseguita durante l'accesso [!UICONTROL Cloud Manager], ma può essere eseguita anche in un secondo momento.

### Configurazione del dispatcher per il test delle prestazioni {#configuring-dispatcher-for-performance-testing}

Per [!UICONTROL Cloud Manager] eseguire correttamente i test delle prestazioni, il server dispatcher di fasi deve rispondere agli stessi nomi host del dispatcher di produzione in modo coerente con il server di produzione.

*Ad esempio*, se un cliente ha [www.myco.com](http://www.myco.com/) e [www.myotherco.com](http://www.myotherco.com,/) come nomi host di produzione e stage-myco.adobecqms.net come nome host dell’area di visualizzazione, una richiesta come questa deve rispondere correttamente:

```
curl -H"Host: www.myco.com" http://stage-myco.adobecqms.net/en/home.html
```

Ciò richiederà non solo che i nomi host siano configurati correttamente nella configurazione del dispatcher, ma anche che ***/etc/map***, qualsiasi Apache riscrittura o qualsiasi altra regola di ***mappatura/filtro*** del percorso sia implementata in modo coerente tra fase e produzione.

## Tecniche consigliate per lo sviluppo {#development-best-practices}

Prima di utilizzare [!UICONTROL Cloud Manager], è consigliabile conoscere alcune best practice per l'impostazione del progetto e la configurazione del server Web o del dispatcher.

### Configurazione progetto {#project-set-up}

I progetti devono rispettare alcuni criteri per poter funzionare con [!UICONTROL Cloud Manager].

Seguite le best practice per configurare il progetto in [!UICONTROL Cloud Manager]:

* L'unico strumento di costruzione fornito e supportato è Apache Maven. Apache Maven 3.3.9 è installato.
* Le build vengono eseguite in un ambiente Linux in un contenitore Docker come utente principale.
* La versione Java installata è Oracle JDK 8u161.
* Sono installati alcuni pacchetti di sistema aggiuntivi, ad esempio bzip2, unzip, libpng, imagemagick e graphicsmagick. Se avete bisogno di altri pacchetti, dovrete richiederli tramite il vostro CSE.
* Maven è sempre eseguito con il comando mvn -B pacchetto pulito.
* Vi verrà fornito esattamente un repository git. Nella directory principale dell'archivio deve essere presente un file pom.xml. Questo file pom.xml può fare riferimento a tutti i sottomoduli (che a loro volta possono avere altri sottomoduli, ecc.) se necessario, ma deve esserci un solo punto di ingresso.
* Maven è configurato a livello di sistema con un file settings.xml che include automaticamente l’archivio degli artifact pubblico di Adobe (repo.adobe.com).
* Potete aggiungere altri repository nei file pom.xml. Tuttavia, l'accesso ai repository di artifact protetti da password o protetti da rete non è supportato.
* I pacchetti di contenuto distribuibile vengono rilevati mediante la scansione di file zip contenuti in una directory denominata target. Anche in questo caso, un numero qualsiasi di sottomoduli potrebbe produrre pacchetti di contenuto.
* In presenza di più pacchetti di contenuto, l'ordine delle distribuzioni dei pacchetti non è garantito. Se è necessario un ordine specifico, per definire l’ordine è possibile utilizzare le dipendenze del pacchetto di contenuto.

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-05-02T18:18:15.028-0400

change as per KT

 -->

### Passaggi successivi {#the-next-steps}

Una volta configurate le configurazioni generali, potete utilizzarle [!UICONTROL Cloud Manager].

Per iniziare, fare riferimento a [Utilizzo di [!UICONTROL Cloud Manager]](https://helpx.adobe.com/experience-manager/cloud-manager/using/using-cloud-manager.html) [!UICONTROL Cloud Manager].
