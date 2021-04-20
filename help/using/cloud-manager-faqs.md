---
title: Domande frequenti su Cloud Manager
seo-title: Domande frequenti su Cloud Manager
description: Fai riferimento alle domande frequenti su Cloud Manager per ricevere alcuni suggerimenti per la risoluzione dei problemi
seo-description: Segui questa pagina per ottenere le risposte sulle domande frequenti su Cloud Manager
feature: Getting Started
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 0%

---


# Domande frequenti su Cloud Manager {#cloud-manager-faqs}

La sezione seguente fornisce le risposte alle domande frequenti relative a Cloud Manager.

## È possibile utilizzare Java 11 con le build di Cloud Manager? {#java-11-cloud-manager}

La build di AEM Cloud Manager non riesce quando si tenta di passare da Java 8 a 11. Il problema può avere molte cause e la maggior parte delle cause comuni sono documentate di seguito:

* Aggiungi il maven-toolchains-plugin con le impostazioni corrette per Java 11 come documentato [qui](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/create-application-project/using-the-wizard.html?lang=en#getting-started).  Ad esempio, consulta il [codice del progetto di esempio wknd](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

* Se incontri l&#39;errore seguente, devi rimuovere l&#39;uso di `maven-scr-plugin` e convertire tutte le annotazioni OSGi in annotazioni OSGi R6. Per istruzioni, vedi [qui](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/).

   `[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]`

* Per le build di Cloud Manager, il plug-in maven enforcer non riesce con l’errore `"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion"`. Si tratta di un problema noto a causa del quale Cloud Manager utilizza una versione diversa di Java per eseguire il comando maven anziché compilare il codice. Per il momento, ometti `requireJavaVersion` dalle configurazioni di maven-enforcer-plugin.

## La distribuzione è bloccata perché il controllo della qualità del codice non è riuscito. C&#39;è un modo per aggirare questo assegno? {#deployment-stuck}

Tutti gli errori di qualità del codice, ad eccezione di *Security Rating*, sono metriche non critiche e possono essere ignorate espandendo gli elementi nell&#39;interfaccia utente dei risultati.

Un utente con il ruolo [Deployment Manager, Project Manager o Business Owner](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=en#requirements) può ignorare i problemi, nel qual caso la pipeline procede o può accettare i problemi, nel qual caso la pipeline si interrompe con un errore.  Per ulteriori informazioni, consulta [Cancelli a tre livelli durante l’esecuzione di una pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use) .

## Le implementazioni di Cloud Manager non riescono al passaggio del test delle prestazioni negli ambienti Adobe Managed Services. Come eseguiamo il debug per passare le metriche critiche? {#debug-critical-metrics}

Per comprendere i risultati, consulta [Comprendere i risultati del test](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use) .

Alcune note sul passaggio del test delle prestazioni:

* Il *Passaggio prestazioni* è un passaggio delle prestazioni web, ovvero il tempo necessario per caricare la pagina utilizzando un browser Web.
* Gli URL elencati nel file risultato *CSV* vengono caricati in un browser Chrome nell’infrastruttura Cloud Manager durante il test.
* Una metrica comune che non riesce è il *tasso di errore*. Affinché un URL possa passare, l’URL principale deve essere caricato con lo stato `200` e in meno di `20` secondi. I carichi di pagina superiori a `20` secondi sono contrassegnati come errori `504`.
* Se il sito richiede l&#39;autenticazione dell&#39;utente, consulta [Test delle prestazioni autenticate](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=en#how-to-use) per configurare il test per l&#39;autenticazione sul sito.

## Siamo autorizzati a utilizzare SNAPSHOT nella versione del progetto Maven? Come funziona il controllo delle versioni dei pacchetti e dei file jar dei bundle per le implementazioni di Stage e Production? {#snapshot-version}

Per informazioni sul controllo delle versioni dei pacchetti e dei file jar dei bundle per le distribuzioni di Stage e Production, consulta i seguenti scenari:

1. Per le implementazioni per sviluppatori, i file del ramo Git `pom.xml` devono contenere `-SNAPSHOT` alla fine del valore `<version>`. Questo consente la distribuzione successiva in cui la versione non viene modificata per essere comunque installata. Nelle implementazioni per sviluppatori, non viene aggiunta o generata alcuna versione automatica per la build Maven.

1. Nella distribuzione Stage e Produzione, viene generata una versione automatica come documentato [qui](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/activating-maven-project.html?lang=en#managing-code).

1. Per il controllo delle versioni personalizzate nelle implementazioni Stage e Produzione, imposta una versione maven corretta in 3 parti come `1.0.0`. Aumenta la versione ogni volta che devi eseguire un’altra implementazione in produzione.

1. Cloud Manager aggiunge automaticamente la propria versione alle build di Stage e Production e crea persino un ramo Git. Non è richiesta alcuna configurazione speciale. Se si salta il passaggio 3, la distribuzione funzionerà comunque correttamente e verrà impostata automaticamente una versione.

1. Se lasci la versione con `-SNAPSHOT` per le build o le distribuzioni di Stage e Production, non si verificano problemi. Cloud Manager imposta automaticamente un numero di versione corretto e crea un tag per te in Git. Se necessario, puoi fare riferimento a questo tag in un secondo momento.

1. Se desideri provare un codice sperimentale nell’ambiente di sviluppo, puoi creare un nuovo ramo Git e impostare la pipeline in modo che utilizzi tale ramo diverso. Questo è utile quando le distribuzioni iniziano a non funzionare e desideri testare con le versioni precedenti del codice per vedere quando si è verificato un errore.

   Il comando Git seguente crea un ramo remoto denominato *testbranch1* rispetto a un commit preesistente specifico `485548e4fbafbc83b11c3cb12b035c9d26b6532b`.  Questo ramo speciale può essere utilizzato in Cloud Manager senza influenzare altri rami:

   `git push origin 485548e4fbafbc83b11c3cb12b035c9d26b6532b:refs/heads/testbranch1`

   Per ulteriori informazioni, consulta la [documentazione Git](https://git-scm.com/book/en/v2/Git-Internals-Git-References) .

   Se desideri eliminare il ramo di test in un secondo momento, utilizza il comando delete :

   `git push origin --delete testbranch1`

## La build Maven non riesce nelle implementazioni di Cloud Manager, ma viene generata localmente senza errori. Come eseguire il debug? {#maven-build-fail}

Per ulteriori informazioni, consulta [Git Resource](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) .

## Impossibile impostare una variabile tramite variabili della pipeline impostate da aio cloud manager. Come eseguire il debug di questi problemi? {#set-variable}

Se ricevi un errore `403` durante il tentativo di elencare o impostare le variabili della pipeline tramite comandi simili a quelli riportati di seguito, devi aggiungere nell’Admin Console come ruolo di prodotto *Deployment Manager* Cloud Manager .\
Per ulteriori informazioni, consulta [Autorizzazioni API](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md) .

Comandi ed errori correlati:

`$ aio cloudmanager:list-pipeline-variables 222`

*Errore*:  `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1`

*Errore*:  `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`
