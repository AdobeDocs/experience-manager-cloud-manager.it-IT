---
title: Note sulla versione 2018.7.0
seo-title: Note sulla versione 2018.7.0
description: 'null'
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2018.7.0 di Cloud Manager.
uuid: d 7 b 49 e 32-01 dc -48 ce-b 744-e 6 a 806 fbdd 8 a
contentOwner: jsyal
topic-tags: note sulla versione
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: b 64 bf 9 ab -27 ed -4 f 33-adc 8-d 73 d 34094 f 1 b
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Note sulla versione 2018.7.0 {#release-notes-for}

La sezione seguente delinea la versione [!UICONTROL Cloud Manager] 2018.7.0 che offre funzionalità *di attivazione automatica* .

**Automatico è** abilitata tramite scalabilità orizzontale dei `Dispatcher/Publish` segmenti nell&#39;ambiente di produzione per supportare un incremento improvviso in fase di caricamento, volume, accesso e altre metriche monitorate definite.

## Data di rilascio {#release-date}

La Data di rilascio per [!UICONTROL Cloud Manager] la versione 2018.7.0 è il 10 settembre 2018.

## Novità {#what-s-new}

* **Provisioning** : [!UICONTROL Cloud Manager] ora sarà possibile oscurare l&#39;ambiente di produzione sul programma cliente in modo da ridurre in sequenza i segmenti di dispatcher e pubblicazione. Nuovo nell&#39;interfaccia utente è la sezione Provisioning in Configurazione programma che verrà visualizzata se nel programma cliente viene attivata l&#39;oscuramento automatico. Per ulteriori informazioni, consultate [Configurazione del programma](setting-up-program.md) .

* **Ambienti** : è ora possibile visualizzare una visualizzazione dettagliata degli ambienti Produzione e Area di visualizzazione insieme alle dimensioni, all&#39;archiviazione, alla regione e allo stato dei nodi associati a ciascun ambiente. Per ulteriori informazioni [, consulta Gestione dei tuoi ambienti](manage-your-environment.md) .

* **Analisi qualità codice** - Nuova regola per identificare l&#39;utilizzo di API errato. Per ulteriori informazioni, consulta [Regole](custom-code-quality-rules.md) di qualità codice personalizzate.

* **Test** delle prestazioni: sono disponibili i grafici per la visualizzazione delle prestazioni, i grafici per l&#39;utilizzo della CPU, il tempo di attesa per i dischi/l&#39;ora di attesa, la frequenza di errore pagina, l&#39;utilizzo della larghezza di banda del disco, l&#39;ora di risposta della pagina picco e il 95 ° percentile tempo di risposta pagina. Fate riferimento a * Performance Testing * section on [Understand your Test Results](understand-your-test-results.md) page.

* **Test delle prestazioni** - Durante la visualizzazione dei risultati del test delle prestazioni, è possibile scaricare l&#39;elenco degli errori pagina e delle richieste lente. Fate riferimento a * Performance Testing * section on [Understand your Test Results](understand-your-test-results.md) page.

## Correzioni di bug {#bug-fixes}

* In alcune circostanze, la sincronizzazione interna del sistema non riusciva in modo errato, generando visualizzazioni non coerenti dei dati.
* In alcuni casi, il trigger manuale della pipeline non era selezionato automaticamente per i problemi di convalida del modulo.
* Gli script di build specifici dei clienti potrebbero causare errori durante il passaggio di build in base alle incompatibilità del plug-in.

## Problemi noti {#known-issues}

* Sebbene i clienti siano in grado di selezionare il trigger di conferma, la pipeline potrebbe non avviarsi in base ai nuovi commentamenti.
* La [!UICONTROL Experience Cloud] barra laterale notifica non può caricare le notifiche in modo coerente. Le notifiche, tuttavia, sono visibili nella [!UICONTROL Experience Cloud] e, se configurate, continueranno a essere inviate tramite e-mail.

