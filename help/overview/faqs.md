---
title: Domande frequenti su Cloud Manager
description: Scopri le risposte alle domande più frequenti su Cloud Manager per clienti AMS.
exl-id: 52c1ca23-5b42-4eae-b63a-4b22ef1a5aee
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '748'
ht-degree: 100%

---


# Domande frequenti su Cloud Manager {#cloud-manager-faqs}

Questo documento fornisce le risposte alle domande più frequenti su Cloud Manager per clienti AMS.

## È possibile utilizzare Java 11 con le build di Cloud Manager? {#java-11}

Sì. È necessario aggiungere il `maven-toolchains-plugin` con le impostazioni corrette per Java 11.

* Questo processo è documentato [qui](/help/getting-started/using-the-wizard.md).
* Ad esempio, consulta il [codice del progetto di esempio WKND](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

## Dopo il passaggio da Java 8 a Java 11, l’esecuzione della build non riesce e genera un errore relativo a maven-scr-plugin. Cosa posso fare? {#maven-src-plugin}

La build di AEM Cloud Manager potrebbe non riuscire durante il tentativo di passaggio da Java 8 a 11. Se riscontri il seguente errore, rimuovi `maven-scr-plugin` e converti tutte le annotazioni OSGi in annotazioni OSGi R6.

```text
[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]
```

Per istruzioni su come rimuovere questo plug-in, [consulta qui](https://cqdump.joerghoh.de/2019/01/03/from-scr-annotations-to-osgi-annotations/).

## Dopo il passaggio da Java 8 a Java 11, l’esecuzione della build non riesce e genera un errore relativo a RequireJavaVersion. Cosa si può fare? {#requirejavaversion}

Per le build di Cloud Manager, il `maven-enforcer-plugin` potrebbe restituire questo errore

```text
[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion
```

Si tratta di un problema noto dovuto al fatto che Cloud Manager utilizza una versione diversa di Java per eseguire il comando Maven anziché compilare il codice. Ometti `requireJavaVersion` dalle configurazioni `maven-enforcer-plugin`.

## Impossibile eseguire il controllo di qualità del codice e ora l’implementazione è bloccata. C’è un modo per aggirare questo controllo? {#deployment-stuck}

Sì. Tutti gli errori di qualità del codice, ad eccezione delle valutazioni di sicurezza, sono metriche non critiche. Di conseguenza, possono essere ignorati come parte di una pipeline di implementazione espandendo gli elementi nell’interfaccia utente dei risultati.

Un utente con il ruolo di [Responsabile della distribuzione, Project Manager o Proprietario business](/help/requirements/users-and-roles.md#role-definitions) può ignorare i problemi. In tale caso, la pipeline procede. In alternativa, può accettare i problemi, nel qual caso la pipeline si arresta con un errore.

Consulta i documenti [Gate a tre livelli durante l’esecuzione di una pipeline](/help/using/code-quality-testing.md#three-tier-gates-while-running-a-pipeline) e [Configurazione di pipeline non di produzione](/help/using/non-production-pipelines.md#understanding-the-flow) per ulteriori dettagli.

## Le distribuzioni di Cloud Manager non superano il test delle prestazioni negli ambienti di Adobe Managed Services. Come si può eseguire il debug di questo problema per superare le metriche critiche? {#debug-critical-metrics}

La risposta a questa domanda non è univoca. Tuttavia, potrebbero essere utili i seguenti punti sul passaggio del test delle prestazioni:

* Questo passaggio rappresenta un passaggio delle prestazioni web. In altre parole, si tratta del momento in cui si carica la pagina utilizzando un browser web.
* Gli URL elencati nel file .csv risultante durante il test vengono caricati in un browser Chrome nell’infrastruttura di Cloud Manager.
* Una metrica comune che non riesce costituisce il tasso di errore. Pertanto, affinché un URL possa passare, l’URL principale deve essere caricato con uno stato `200` e in meno di `20` secondi. Se il caricamento di una pagina supera i `20` secondi, viene contrassegnato come errore `504`.
* Se il sito richiede l’autenticazione dell’utente, consulta il documento [Comprendere i risultati del test](/help/using/code-quality-testing.md#authenticated-performance-testing) per configurare il test, per l’autenticazione sul sito.

Consulta il documento [Comprendere i risultati del test](/help/using/code-quality-testing.md) per ulteriori informazioni sui controlli di qualità.

## Posso usare SNAPSHOT per la versione del progetto Maven? {#snapshot}

Sì. Nelle implementazioni per gli sviluppatori, i file `pom.xml` del ramo Git devono contenere `-SNAPSHOT` alla fine del valore `<version>`.

Questo consente di installare le implementazioni successive anche se la versione non è stata modificata. Per le distribuzioni nell’ambiente di sviluppo, non viene aggiunta né generata una versione automatica della build Maven.

È possibile impostare la versione su `-SNAPSHOT` per le build o le implementazioni negli ambienti di staging e produzione. Cloud Manager imposta automaticamente un numero di versione corretto e crea un tag in Git. Se necessario, puoi fare riferimento a questo tag in un secondo momento.

Ulteriori dettagli sulla gestione delle versioni sono [documentati qui](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/project-version-handling).

## Come funziona il controllo delle versioni di pacchetti e bundle per le distribuzioni di staging e produzione? {#staging-production}

Nelle distribuzioni di staging e produzione, viene generata una versione automatica [come documentato qui](/help/managing-code/maven-project-version.md).

Per il controllo delle versioni personalizzato per le distribuzioni negli ambienti di staging e produzione, imposta una versione Maven in tre parti appropriata, come ad esempio `1.0.0`. Aumenta il numero della versione per ogni esecuzione della distribuzione nell’ambiente di produzione.

Cloud Manager aggiunge automaticamente la versione alle build di staging e produzione e crea un ramo Git. Non è richiesta alcuna configurazione speciale. Se non si imposta una versione maven come descritto in precedenza, la distribuzione avviene comunque e viene impostata una versione automaticamente.

## L’esecuzione della build Maven non riesce per le distribuzioni di Cloud Manager, ma a livello locale non genera errori. Qual è il problema? {#maven-build-fail}

Per ulteriori dettagli, consulta questa [risorsa Git](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md).

## Non riesco a impostare una variabile con un comando aio. Cosa si può fare? {#set-variable}

Quando si tenta di elencare o impostare le variabili della pipeline tramite comandi `aio`, è possibile che venga visualizzato un errore 403 come il seguente.

```shell
$ aio cloudmanager:list-pipeline-variables 222

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1

setting variables... !

Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)
```

In questo caso, l’utente che esegue questi comandi deve essere aggiunto al ruolo **Responsabile della distribuzione** in Admin Console.

Per ulteriori dettagli, consulta [Autorizzazioni API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/).
