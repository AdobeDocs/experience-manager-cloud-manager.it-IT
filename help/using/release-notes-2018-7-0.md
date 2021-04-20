---
title: Note sulla versione 2018.7.0
seo-title: Note sulla versione 2018.7.0
description: Scopri la versione 2018.7.0 di Cloud Manager
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2018.7.0 di Cloud Manager.
uuid: d7b49e32-01dc-48ce-b744-e6a806fbdd8a
contentOwner: jsyal
topic-tags: release-notes
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: b64bf9ab-27ed-4f33-adc8-d73d34094f1b
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 12%

---


# Note sulla versione 2018.7.0 {#release-notes-for}

La sezione seguente illustra la versione [!UICONTROL Cloud Manager] 2018.7.0 che offre la funzione *scalabilità automatica*.

**Il ridimensionamento automatico è abilitato tramite la scalabilità orizzontale dei segmenti nell’ambiente di produzione per supportare un aumento improvviso del carico, del volume, degli accessi e di altre metriche monitorate definite.**`Dispatcher/Publish`

## Data di rilascio {#release-date}

La data di rilascio di [!UICONTROL Cloud Manager] versione 2018.7.0 è il 10 settembre 2018.

## Novità {#what-s-new}

* **Provisioning** :  [!UICONTROL Cloud Manager] ora è possibile scalare automaticamente l’ambiente di produzione sul programma del cliente tramite ridimensionamento orizzontale con i segmenti Dispatcher/Publish. Nell’interfaccia utente è stata introdotta la sezione Provisioning in Configurazione programma che verrà visualizzata se l’opzione di scalabilità automatica è abilitata nel programma per il cliente. Per ulteriori informazioni, fai riferimento a [Configurazione del programma](setting-up-program.md) .

* **Ambienti**  - È ora possibile visualizzare una visualizzazione dettagliata degli ambienti di produzione e stage insieme alle dimensioni, allo spazio di archiviazione, alla regione e allo stato dei nodi associati a ciascun ambiente. Per ulteriori informazioni, consulta [Gestire gli ambienti](manage-your-environment.md) .

* **Analisi della qualità del codice**  - Nuova regola per identificare un utilizzo API errato. Per ulteriori informazioni, consulta [Regole per la qualità del codice personalizzato](custom-code-quality-rules.md) .

* **Test delle prestazioni**  - Durante la visualizzazione dei risultati dei test delle prestazioni, sono disponibili grafici per l&#39;utilizzo della CPU, Tempo di attesa I/O del disco, Tasso di errore della pagina, Utilizzo della larghezza di banda del disco, Utilizzo della larghezza di banda della rete, Tempo di risposta della pagina di picco e Tempo di risposta della pagina del 95° percentile. Fare riferimento alla sezione *Test delle prestazioni* nella pagina [Comprendere i risultati del test](understand-your-test-results.md).

* **Test delle prestazioni**  - Durante la visualizzazione dei risultati dei test delle prestazioni, è possibile scaricare l’elenco degli errori di pagina e delle richieste lente. Fare riferimento alla sezione *Test delle prestazioni* nella pagina [Comprendere i risultati del test](understand-your-test-results.md).

## Correzioni di bug {#bug-fixes}

* In alcune circostanze, la sincronizzazione interna del sistema non è riuscita in modo appropriato, dando luogo a visualizzazioni incoerenti dei dati.
* In alcuni casi, l’attivazione manuale della pipeline non veniva selezionata automaticamente, causando problemi di convalida del modulo.
* Script di build specifici del cliente potrebbero causare errori durante il passaggio di compilazione in base alle incompatibilità dei plug-in.

## Problemi noti {#known-issues}

* Sebbene i clienti siano in grado di selezionare il trigger di commit, la pipeline potrebbe non avviarsi in realtà in base a nuovi commit.
* La barra laterale delle notifiche [!UICONTROL Experience Cloud] potrebbe non caricare le notifiche in modo coerente. Le notifiche, tuttavia, sono visibili in [!UICONTROL Experience Cloud] e, se configurate, saranno comunque inviate tramite e-mail.

