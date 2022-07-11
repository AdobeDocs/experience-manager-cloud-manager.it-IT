---
title: Domande frequenti su Cloud Manager
description: Questo documento fornisce le risposte alle domande più frequenti sui clienti di Cloud Manager per AMS.
exl-id: 52c1ca23-5b42-4eae-b63a-4b22ef1a5aee
source-git-commit: 6be659e02df0657ec7d3dbce8c18c44a327a36f4
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 1%

---


# Domande frequenti su Cloud Manager {#cloud-manager-faqs}

Questo documento fornisce le risposte alle domande più frequenti sui clienti di Cloud Manager per AMS.

## È possibile utilizzare Java 11 con le build di Cloud Manager? {#java-11}

Sì. Dovrai aggiungere il `maven-toolchains-plugin` con le impostazioni corrette per Java 11.

* Questo processo è documentato [qui.](/help/getting-started/using-the-wizard.md)
* Ad esempio, consulta [codice del progetto di esempio wknd.](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75)

## La mia build non riesce con un errore su maven-scr-plugin dopo il passaggio da Java 8 a Java 11. Cosa posso fare? {#maven-src-plugin}

La build di AEM Cloud Manager potrebbe non riuscire quando si tenta di passare da Java 8 a 11. Se si verifica il seguente errore, è necessario rimuovere `maven-scr-plugin` e convertire tutte le annotazioni OSGi in annotazioni OSGi R6.

```text
[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]
```

Per istruzioni su come rimuovere questo plug-in, [vedi qui.](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/)

## La mia build non riesce con un errore su RequireJavaVersion dopo il passaggio da Java 8 a Java 11. Cosa posso fare? {#requirejavaversion}

Per le build di Cloud Manager, l’ `maven-enforcer-plugin` potrebbe non riuscire con questo errore

```text
[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion
```

Si tratta di un problema noto a causa del quale Cloud Manager utilizza una versione diversa di Java per eseguire il comando maven anziché compilare il codice. omettere `requireJavaVersion` dal `maven-enforcer-plugin` configurazioni.

## Il controllo della qualità del codice non è riuscito e la distribuzione è bloccata. C&#39;è un modo per aggirare questo assegno? {#deployment-stuck}

Sì. Tutti gli errori di qualità del codice, ad eccezione delle valutazioni di sicurezza, sono metriche non critiche e possono quindi essere ignorati come parte di una pipeline di distribuzione espandendo gli elementi nell’interfaccia utente dei risultati.

Un utente con [Responsabile distribuzione, Project Manager o Proprietario business](/help/requirements/users-and-roles.md#role-definitions) Il ruolo può ignorare i problemi, nel qual caso la pipeline procede o può accettare i problemi, nel qual caso la pipeline si interrompe con un errore.

Vedere i documenti [Cancelli a tre livelli durante l’esecuzione di una pipeline](/help/using/code-quality-testing.md#three-tier-gates-while-running-a-pipeline) e [Configurazione di pipeline non di produzione](/help/using/non-production-pipelines.md#understanding-the-flow) per ulteriori dettagli.

## Le implementazioni di Cloud Manager non riescono al passaggio del test delle prestazioni negli ambienti Adobe Managed Services. Come eseguiamo il debug per passare le metriche critiche? {#debug-critical-metrics}

Non c&#39;è una sola risposta a questa domanda. Ma questi sono alcuni punti importanti sul passaggio del test delle prestazioni che dovresti tenere a mente:

* Questo passaggio rappresenta un passaggio delle prestazioni web, ovvero il tempo necessario per caricare la pagina utilizzando un browser web.
* Gli URL elencati nel file .csv del risultato vengono caricati in un browser Chrome nell’infrastruttura Cloud Manager durante il test.
* Una metrica comune che non riesce è il tasso di errore.
   * Affinché un URL possa passare, l’URL principale deve essere caricato con `200` stato e in meno di `20` secondi.
   * Caricamenti di pagina superiori a `20` i secondi sono contrassegnati come `504` errori.
* Se il tuo sito richiede l’autenticazione dell’utente, consulta il documento [Comprendere i risultati del test](/help/using/code-quality-testing.md#authenticated-performance-testing) per configurare il test da autenticare sul sito.

Vedi il documento [Risultati dei test](/help/using/code-quality-testing.md) per ulteriori informazioni sui controlli di qualità.

## Posso usare SNAPSHOT per la versione del progetto Maven? {#snapshot}

Sì. Per le implementazioni per sviluppatori, il ramo git `pom.xml` i file devono contenere `-SNAPSHOT` alla fine del `<version>` valore.

Ciò consente di installare la distribuzione successiva anche se la versione non è stata modificata. Nelle implementazioni per sviluppatori, non viene aggiunta o generata alcuna versione automatica per la build Maven.

Puoi anche impostare la versione su `-SNAPSHOT` per build o implementazioni di stage e produzione. Cloud Manager imposta automaticamente un numero di versione corretto e crea un tag per te in git. Se necessario, puoi fare riferimento a questo tag in un secondo momento.

Ulteriori dettagli sulla gestione delle versioni sono [qui documentato.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/project-version-handling.html)

## Come funziona il controllo delle versioni di pacchetti e bundle per le distribuzioni di staging e produzione? {#staging-production}

Nelle distribuzioni di staging e produzione, viene generata una versione automatica [come documentato qui.](/help/managing-code/maven-project-version.md)

Per il controllo delle versioni personalizzate nelle distribuzioni di stage e produzione, imposta una versione maven corretta in tre parti come `1.0.0`. Aumenta la versione ogni volta che distribuisci in produzione.

Cloud Manager aggiunge automaticamente la sua versione alle build di stage e produzione e crea un ramo git. Non è richiesta alcuna configurazione speciale. Se non si imposta una versione maven come descritto in precedenza, la distribuzione avrà comunque successo e verrà impostata automaticamente una versione.

## La build Maven non riesce per le implementazioni di Cloud Manager, ma viene generata localmente senza errori. Cosa c&#39;è che non va? {#maven-build-fail}

Vedi questo [risorsa git](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) per ulteriori dettagli.

## Impossibile impostare una variabile utilizzando un comando aio. Cosa posso fare? {#set-variable}

Quando tenti di elencare o impostare le variabili della pipeline tramite , potresti ricevere un errore 403 come ad esempio quanto segue `aio` comandi.

```shell
$ aio cloudmanager:list-pipeline-variables 222

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1

setting variables... !

Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)
```

In questo caso, l&#39;utente che esegue questi comandi deve essere aggiunto al **Gestione distribuzione** nell&#39;Admin Console.

Vedi [Autorizzazioni API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/) per ulteriori dettagli.
