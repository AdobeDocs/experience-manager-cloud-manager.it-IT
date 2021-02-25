---
title: Domande frequenti su Cloud Manager
seo-title: Domande frequenti su Cloud Manager
description: Consulta le domande frequenti su Cloud Manager per ottenere alcuni suggerimenti per la risoluzione dei problemi
seo-description: Segui questa pagina per ottenere le risposte sulle domande frequenti su Cloud Manager
translation-type: tm+mt
source-git-commit: d901fd27626640e71d367d3f138d7ba2e907fa9a
workflow-type: tm+mt
source-wordcount: '885'
ht-degree: 0%

---


# Domande frequenti su Cloud Manager {#cloud-manager-faqs}

La sezione seguente contiene le risposte alle domande frequenti più frequenti relative a Cloud Manager.

## È possibile utilizzare Java 11 con le build di Cloud Manager? {#java-11-cloud-manager}

AEM build Cloud Manager non riesce quando si tenta di passare da Java 8 a 11. Il problema può avere molte cause e la maggior parte delle cause più comuni sono documentati di seguito:

* Aggiungete il maven-toolchain-plugin con le impostazioni corrette per Java 11 come documentato [qui](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/create-application-project/using-the-wizard.html?lang=en#getting-started).  Ad esempio, vedere il [codice del progetto di esempio wknd](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

* Se si verifica l’errore riportato di seguito, è necessario rimuovere l’uso del plug-in maven-scr-e convertire tutte le annotazioni OSGi in annotazioni OSGi R6. Per istruzioni, vedere [qui](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/).

   `[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]`

* Per le build di Cloud Manager, il plug-in maven per l&#39;applicazione non riesce con l&#39;errore `"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion"`. Si tratta di un problema noto a causa del quale Cloud Manager utilizza una versione diversa di Java per eseguire il comando maven invece di compilare il codice. Per il momento, omettete `requireJavaVersion` dalle configurazioni del plug-in &quot;maven-esecuter&quot;.

## La nostra distribuzione è bloccata perché il controllo Qualità codice non è riuscito. C&#39;è un modo per aggirare questo assegno? {#deployment-stuck}

Tutti gli errori di qualità del codice, tranne *Valutazione sicurezza*, sono metriche non critiche, pertanto possono essere ignorate espandendo gli elementi nell&#39;interfaccia utente dei risultati.

Un utente con il ruolo [Gestione distribuzione, Project Manager o Business Owner](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=en#requirements) può ignorare i problemi, nel qual caso la pipeline procede o possono accettare i problemi, nel qual caso la pipeline si interrompe con un errore.  Per ulteriori informazioni, vedere [Porte a tre livelli durante l&#39;esecuzione di una tubazione](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use).

## Le distribuzioni di Cloud Manager non riescono al passaggio del test delle prestazioni negli ambienti Adobe Managed Services. Come facciamo a eseguire il debug di questa operazione per passare le metriche critiche? {#debug-critical-metrics}

Per informazioni sui risultati, vedere [Comprendere i risultati dei test](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use).

Alcune note sul passaggio Performance Test:

* Il *Passo prestazioni* è un passaggio delle prestazioni Web, ovvero il momento in cui caricare la pagina utilizzando un browser Web.
* Gli URL elencati nel file risultato *CSV* vengono caricati in un browser Chrome nell&#39;infrastruttura di Cloud Manager durante il test.
* Una metrica comune che non riesce è la *frequenza di errore*. Affinché un URL possa passare, l&#39;URL principale deve essere caricato con lo stato `200` e in meno di `20` secondi. I carichi di pagina superiori a `20` secondi sono contrassegnati come errori `504`.
* Se il sito richiede l&#39;autenticazione dell&#39;utente, vedere [Autenticazione delle prestazioni](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=en#how-to-use) per configurare il test per l&#39;autenticazione sul sito.

## Siamo autorizzati a usare SNAPSHOT nella versione del progetto Maven? Come funziona il controllo delle versioni dei pacchetti e dei file JAR dei bundle per le installazioni di fase e produzione? {#snapshot-version}

1. Per le distribuzioni di sviluppo, il ramo Git `pom.xml` file deve contenere -SNAPSHOT alla fine del valore `<version>`. Questo consente la distribuzione successiva in cui la versione non viene modificata per essere ancora installata. Nelle distribuzioni di sviluppo, non viene aggiunta o generata alcuna versione automatica per la build mMobile.

1. Nell&#39;implementazione di fase e produzione, viene generata una versione automatica come documentato [here](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/activating-maven-project.html?lang=en#managing-code).

1. Per le versioni personalizzate nelle implementazioni di fase e produzione, impostate una versione Maven di 3 parti come `1.0.0`. Aumentate la versione ogni volta che dovete eseguire un&#39;altra distribuzione in produzione.

1. Cloud Manager aggiunge automaticamente la propria versione alle build di Stage e Produzione e crea anche un ramo Git. Non è richiesta alcuna configurazione speciale. Se si ignora il passaggio 3, la distribuzione funzionerebbe comunque correttamente e verrebbe automaticamente impostata una versione.

1. Se lasciate la versione con `-SNAPSHOT` per le build o le distribuzioni di fase e produzione, anche questo va bene. Cloud Manager imposta automaticamente un numero di versione corretto e crea un tag per voi in Git. Se necessario, potete fare riferimento a questo tag in un secondo momento.

1. Se desiderate provare alcuni codici sperimentali sull&#39;ambiente di sviluppo, potete creare un nuovo ramo Git e impostare la tubazione per utilizzare quel ramo diverso. Questa funzione è utile quando le distribuzioni iniziano a non funzionare e si desidera eseguire il test con versioni precedenti del codice per vedere quando si è interrotta.

   Il comando Git di seguito crea un ramo remoto denominato *testbranch1* rispetto a un commit preesistente specifico `485548e4fbafbc83b11c3cb12b035c9d26b6532b`.  Questo ramo speciale può essere utilizzato in Cloud Manager senza influenzare altri rami:

   `git push origin 485548e4fbafbc83b11c3cb12b035c9d26b6532b:refs/heads/testbranch1`

   Per ulteriori informazioni, consultare la [documentazione Git](https://git-scm.com/book/en/v2/Git-Internals-Git-References).

   Se si desidera eliminare il ramo test in un secondo momento, utilizzare il comando delete:

   `git push origin --delete testbranch1`

## La build Maven non riesce nelle installazioni di Cloud Manager, ma viene generata localmente senza errori. Come eseguire il debug? {#maven-build-fail}

Per ulteriori informazioni, vedere [Git Resource](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md).

## Impossibile impostare una variabile tramite le variabili della pipeline impostate da aio cloud manager. Come risolvere questi problemi? {#set-variable}

Se viene visualizzato un errore `403` durante il tentativo di elencare o impostare le variabili della pipeline tramite comandi simili a quelli riportati di seguito, è necessario aggiungere il ruolo di prodotto *Gestione distribuzione* Cloud Manager nel Admin Console .\
Per ulteriori informazioni, consultate [Autorizzazioni API](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md).

Comandi ed errori correlati:

`$ aio cloudmanager:list-pipeline-variables 222`

Errore: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1`

Errore: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`
