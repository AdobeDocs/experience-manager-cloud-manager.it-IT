---
title: Domande frequenti su Cloud Manager
description: Scopri le risposte alle domande più frequenti su Cloud Manager per clienti AMS.
exl-id: 52c1ca23-5b42-4eae-b63a-4b22ef1a5aee
TQID: https://experienceleague.adobe.com/aBIiazPCm-krE6rew6k-HSl-Uvc79eagMzM7uYciWdc
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 4dcc367f82c51626ca449ff389a9c9574a562ff7
workflow-type: tm+mt
source-wordcount: 764
ht-degree: 69%

---

# Domande frequenti su Cloud Manager {#cloud-manager-faqs}

Questo documento fornisce le risposte alle domande più frequenti su Cloud Manager per clienti AMS.

<!-- 
## Is it possible to use Java 11 with Cloud Manager builds? {#java-11}

Yes. You need to add the `maven-toolchains-plugin` with the correct settings for Java 11.

* This process is documented [here](/help/getting-started/using-the-wizard.md).
* For an example, see the [WKND sample project code](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75). 
-->

## Dopo il passaggio da Java 8 a Java 11, l’esecuzione della build non riesce e genera un errore relativo a maven-scr-plugin. Cosa posso fare? {#maven-src-plugin}

La build di AEM Cloud Manager non riesce quando si tenta di passare da Java 8 a Java 11. Se riscontri il seguente errore, rimuovi `maven-scr-plugin` e converti tutte le annotazioni OSGi in annotazioni OSGi R6.

```text
[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]
```

Per istruzioni su come rimuovere questo plug-in, [consulta qui](https://cqdump.joerghoh.de/2019/01/03/from-scr-annotations-to-osgi-annotations/).

## Dopo il passaggio da Java 8 a Java 11, l’esecuzione della build non riesce e genera un errore relativo a RequireJavaVersion. Cosa posso fare? {#requirejavaversion}

Per le build di Cloud Manager è possibile che l’esecuzione di `maven-enforcer-plugin` non riesca e generi questo errore.

```text
[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion
```

Questo problema si verifica perché Cloud Manager utilizza una versione diversa di Java per eseguire il comando Maven. Questa versione è diversa da quella utilizzata per compilare il codice. Ometti `requireJavaVersion` dalle configurazioni `maven-enforcer-plugin`.

## Il controllo di qualità del codice non è riuscito e ora la distribuzione è interrotta. C’è un modo per aggirare questo controllo? {#deployment-stuck}

Sì. Tutti gli errori di qualità del codice, ad eccezione delle valutazioni di sicurezza, sono metriche non critiche. Di conseguenza, possono essere ignorati come parte di una pipeline di implementazione espandendo gli elementi nell’interfaccia utente dei risultati.

Un utente con il ruolo di [Responsabile della distribuzione, Project Manager o Proprietario business](/help/requirements/users-and-roles.md#role-definitions) può ignorare i problemi. In tale caso, la pipeline procede. In alternativa, può accettare i problemi, nel qual caso la pipeline si interrompe con un errore.

Consulta i documenti [Gate a tre livelli durante l’esecuzione di una pipeline](/help/using/code-quality-testing.md#three-tier-gates-while-running-a-pipeline) e [Configurazione di pipeline non di produzione](/help/using/non-production-pipelines.md#understanding-the-flow) per ulteriori dettagli.

## Le distribuzioni di Cloud Manager non superano il test delle prestazioni negli ambienti di Adobe Managed Services. Come si risolve questo problema per superare le metriche critiche? {#debug-critical-metrics}

Non esiste un&#39;unica risposta definitiva a questa domanda. Tuttavia, i seguenti punti sul passaggio del test delle prestazioni sono utili:

* Questo passaggio rappresenta un passaggio delle prestazioni web. Ossia, si tratta del tempo necessario per caricare una pagina in un browser web.
* Durante il test, gli URL elencati nel file .csv risultante vengono caricati in un browser Chrome all’interno dell’infrastruttura Cloud Manager.
* Una metrica comune che non riesce costituisce il tasso di errore. Pertanto, affinché un URL possa passare, l’URL principale deve essere caricato con uno stato `200` e in meno di `20` secondi. Se il caricamento di una pagina supera i `20` secondi, viene contrassegnato come errore `504`.
* Se il sito richiede l’autenticazione dell’utente, consulta il documento [Comprendere i risultati del test](/help/using/code-quality-testing.md#authenticated-performance-testing) per configurare il test, per l’autenticazione sul sito.

Consulta il documento [Comprendere i risultati del test](/help/using/code-quality-testing.md) per ulteriori informazioni sui controlli di qualità.

## Posso usare SNAPSHOT per la versione del progetto Maven? {#snapshot}

Sì. Nelle implementazioni per gli sviluppatori, i file `pom.xml` del ramo Git devono contenere `-SNAPSHOT` alla fine del valore `<version>`.

In questo modo è possibile installare le distribuzioni successive quando la versione non è stata modificata. Nelle distribuzioni per gli sviluppatori, non viene aggiunta o generata alcuna versione automatica per la build Maven.

È possibile impostare la versione su `-SNAPSHOT` per le build o le implementazioni negli ambienti di staging e produzione. Cloud Manager imposta automaticamente un numero di versione corretto e crea un tag in Git. Se necessario, puoi fare riferimento a questo tag in un secondo momento.

Ulteriori dettagli sulla gestione delle versioni sono [documentati qui](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/project-version-handling).

## Come funziona il controllo delle versioni di pacchetti e bundle per le distribuzioni di staging e produzione? {#staging-production}

Nelle distribuzioni di staging e produzione, viene generata una versione automatica [come documentato qui](/help/managing-code/maven-project-version.md).

Per il controllo delle versioni personalizzate nelle distribuzioni di staging e produzione, imposta una versione Maven corretta in tre parti come `1.0.0`. Aumenta il numero della versione per ogni esecuzione della distribuzione nell’ambiente di produzione.

Cloud Manager aggiunge automaticamente la versione alle build di staging e produzione e crea un ramo Git. Non è richiesta alcuna configurazione speciale. Se non imposti una versione Maven come descritto in precedenza, la distribuzione viene comunque eseguita correttamente e viene impostata automaticamente una versione.

## La build Maven non riesce per le distribuzioni Cloud Manager, ma viene generata localmente senza errori. Qual è la causa? {#maven-build-fail}

Per ulteriori dettagli, consulta questa [risorsa Git](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md).

## Non riesco a impostare una variabile con un comando aio. Cosa posso fare? {#set-variable}

Quando si tenta di elencare o impostare le variabili della pipeline tramite comandi `aio`, viene visualizzato un errore 403 come il seguente.

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

Per ulteriori dettagli, consulta [Autorizzazioni API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions).
