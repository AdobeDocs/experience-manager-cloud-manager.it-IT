---
title: Domande frequenti su Cloud Manager
seo-title: Domande frequenti su Cloud Manager
description: Consulta le domande frequenti su Cloud Manager per ottenere alcuni suggerimenti per la risoluzione dei problemi
seo-description: Segui questa pagina per ottenere le risposte sulle domande frequenti su Cloud Manager
translation-type: tm+mt
source-git-commit: cb63a8bbe30b28668313dc851f17aa34fc166474
workflow-type: tm+mt
source-wordcount: '873'
ht-degree: 0%

---


# Domande frequenti su Cloud Manager {#cloud-manager-faqs}

La sezione seguente contiene le risposte ad alcune delle domande frequenti più frequenti relative a Cloud Manager.

## 1. È possibile utilizzare Java 11 con le build di Cloud Manager? {#java-11-cloud-manager}

AEM build Cloud Manager non riesce quando si tenta di passare da Java 8 a Java 11. Il problema può avere molte cause e la maggior parte delle cause più comuni sono documentati di seguito:

* Aggiungete il maven-toolchain-plugin con le impostazioni corrette per Java 11 come documentato [qui](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/create-application-project/using-the-wizard.html?lang=en#getting-started).  Ad esempio, vedere il [codice del progetto di esempio wknd](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

* Se si verifica l’errore riportato di seguito, è necessario rimuovere l’uso del plug-in maven-scr-e convertire tutte le annotazioni OSGi in annotazioni OSGi R6. Per istruzioni, vedere [qui](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/).

   `[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]`

* Per Cloud Manager il plug-in maven per l&#39;applicazione non riesce con l&#39;errore `"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion"`. Si tratta di un problema noto a causa del quale Cloud Manager utilizza una versione diversa di Java per eseguire il comando maven invece di compilare il codice. Per il momento, omettete `requireJavaVersion` dalle configurazioni del plug-in &quot;maven-esecuter&quot;.

## 2. La nostra distribuzione è bloccata perché il controllo Qualità codice non è riuscito. C&#39;è un modo per aggirare questo assegno? {#deployment-stuck}

Tutti gli errori di qualità del codice, tranne *Valutazione sicurezza*, sono metriche non critiche, pertanto possono essere ignorate espandendo gli elementi nell&#39;interfaccia utente dei risultati.

Un utente con il ruolo [Gestione distribuzione, Project Manager o Business Owner](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=en#requirements) può ignorare i problemi, nel qual caso la pipeline procede, oppure può accettare i problemi, nel qual caso la pipeline si interrompe con un errore.  Per ulteriori informazioni, vedere [Porte a tre livelli durante l&#39;esecuzione di una tubazione](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use).

## 3. Le distribuzioni di Cloud Manager non riescono al passaggio del test delle prestazioni negli ambienti Adobe Managed Services. Come facciamo a eseguire il debug di questa operazione per passare le metriche critiche? {#debug-critical-metrics}

Per informazioni sui risultati, vedere [Comprendere i risultati dei test](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use).

Alcune note sul passaggio del test delle prestazioni:

* *Performance Step* è un passaggio di prestazioni Web, ovvero è il momento di caricare la pagina utilizzando un browser Web.
* Gli URL elencati nel file CSV risultante vengono caricati in un browser Chrome nell&#39;infrastruttura Cloud Manager durante il test.
* Una metrica comune che non riesce è la *frequenza di errore*. Affinché un URL possa passare, l’URL principale deve essere caricato con lo stato 200 e in meno di 20 secondi. I carichi di pagina superiori a 20 secondi sono contrassegnati come errori 504.
* Se il sito richiede l&#39;autenticazione dell&#39;utente, consultate questa documentazione per configurare il test per l&#39;autenticazione al sito.

## 4. Siamo autorizzati a usare SNAPSHOT nella versione del progetto Maven? Come funziona il controllo delle versioni dei pacchetti e dei file JAR dei bundle per le installazioni di fase e produzione? {#snapshot-version}

1. Per le distribuzioni di sviluppo, i file git branch pom.xml devono contenere -SNAPSHOT alla fine del valore `<version>`. Questo consente le installazioni successive in cui la versione non viene modificata per essere ancora installata. Nelle installazioni di sviluppo, non viene aggiunta o generata alcuna versione automatica per la build maven.

1. Nelle installazioni di fase e produzione, viene generata una versione automatica, come illustrato di seguito.

1. Per le versioni personalizzate nelle implementazioni di fase e produzione, impostate una versione pari a 3 parti come `1.0.0`. Aumentate la versione ogni volta che dovete eseguire un&#39;altra distribuzione in produzione.

1. Cloud Manager aggiunge automaticamente la sua versione alle build di produzione e di stadio e crea anche un ramo git. Non è richiesta alcuna configurazione speciale. Se si ignora il passaggio 3, la distribuzione funzionerebbe comunque correttamente e verrebbe automaticamente impostata una versione.

1. Se lasciate la versione con `-SNAPSHOT` per la creazione o la distribuzione di fase e produzione, anche questo va bene. Cloud Manager imposta automaticamente un numero di versione corretto e crea un tag per voi in git. Se necessario, potete fare riferimento a questo tag in un secondo momento.

1. Se si desidera provare qualche codice sperimentale su dev è possibile creare un nuovo ramo git e impostare la pipeline per utilizzare quel ramo diverso.  Questa funzione è utile quando le distribuzioni iniziano a non funzionare e si desidera eseguire il test con versioni precedenti del codice per vedere quando si è interrotta.

   Il comando git di seguito crea un ramo remoto denominato *testbranch1* rispetto a un commit preesistente specifico `485548e4fbafbc83b11c3cb12b035c9d26b6532b`.  Questo ramo speciale può essere utilizzato in Cloud Manager senza influenzare altri rami:

   `git push origin 485548e4fbafbc83b11c3cb12b035c9d26b6532b:refs/heads/testbranch1`

   Per ulteriori informazioni, consultare la [documentazione Git](https://git-scm.com/book/en/v2/Git-Internals-Git-References).

   Se successivamente si desidera eliminare il ramo test, utilizzare il comando delete (ovviamente, fare attenzione con questo comando):

   `git push origin --delete testbranch1`

## 5. La build Maven non riesce nelle installazioni di Cloud Manager, ma viene generata localmente senza errori. Come eseguire il debug? {#maven-build-fail}

Per ulteriori informazioni, vedere [Git Resource](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md).

## 6. Impossibile impostare una variabile tramite le variabili della pipeline impostate da aio cloud manager. Come risolvere questi problemi? {#set-variable}

Se viene visualizzato un errore 403 quando si tenta di elencare o impostare variabili di pipeline tramite comandi simili a quelli riportati di seguito, è necessario aggiungere il ruolo di prodotto *Gestione distribuzione* Cloud Manager nella console di amministrazione.\
Per ulteriori informazioni, consultate [Autorizzazioni API](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md).

Comandi ed errori correlati:

`$ aio cloudmanager:list-pipeline-variables 222`

Errore: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1`

Errore: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`
