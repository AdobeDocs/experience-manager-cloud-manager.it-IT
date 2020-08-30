---
title: Note sulla versione 2018.7.0
seo-title: Note sulla versione 2018.7.0
description: 'null'
seo-description: Segui questa pagina per ottenere informazioni su Cloud Manager Release 2018.7.0.
uuid: d7b49e32-01dc-48ce-b744-e6a806fbdd8a
contentOwner: jsyal
topic-tags: release-notes
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: b64bf9ab-27ed-4f33-adc8-d73d34094f1b
translation-type: tm+mt
source-git-commit: ace032fbb26235d87d61552a11996ec2bb42abce
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 5%

---


# Note sulla versione 2018.7.0 {#release-notes-for}

La sezione seguente illustra la versione [!UICONTROL Cloud Manager] 2018.7.0 che offre la funzione di *scalabilità* automatica.

**Il ridimensionamento** automatico è abilitato tramite la scalabilità orizzontale dei `Dispatcher/Publish` segmenti nell&#39;ambiente di produzione per supportare un improvviso aumento di carico, volume, accesso e altre metriche monitorate definite.

## Data di rilascio {#release-date}

La data di rilascio per la [!UICONTROL Cloud Manager] versione 2018.7.0 è il 10 settembre 2018.

## Novità {#what-s-new}

* **Provisioning** : ora [!UICONTROL Cloud Manager] è possibile scalare automaticamente l&#39;ambiente di produzione sul programma del cliente ridimensionandolo orizzontalmente con i segmenti Dispatcher/Publish. Nell’interfaccia utente è stata aggiunta la sezione Provisioning di Program Setup (Provisioning), che verrà visualizzata se l’opzione di ridimensionamento automatico è abilitata nel programma del cliente. Per ulteriori informazioni, fare riferimento a [Configurazione del programma](setting-up-program.md) .

* **Ambienti** - È ora possibile visualizzare una visualizzazione dettagliata degli ambienti di produzione e fase insieme alle dimensioni, allo storage, alla regione e allo stato dei nodi associati a ciascun ambiente. Per ulteriori informazioni, consulta [Gestione degli ambienti](manage-your-environment.md) .

* **Analisi** della qualità del codice - Nuova regola per identificare un utilizzo API non corretto. Per ulteriori informazioni, fare riferimento a Regole [di qualità del codice](custom-code-quality-rules.md) personalizzate.

* **Test** delle prestazioni - Durante la visualizzazione dei risultati dei test delle prestazioni, sono disponibili grafici per l&#39;utilizzo della CPU, Tempo di attesa I/O disco, Frequenza errori di pagina, Utilizzo della larghezza di banda del disco, Utilizzo della larghezza di banda della rete, Tempo di risposta della pagina di picco e Tempo di risposta della pagina 95esima percentuale. Fare riferimento alla sezione *Performance Testing* nella pagina [Comprendere i risultati](understand-your-test-results.md) dei test.

* **Test** delle prestazioni - Durante la visualizzazione dei risultati dei test delle prestazioni, è possibile scaricare l&#39;elenco degli errori di pagina e delle richieste lente. Fare riferimento alla sezione *Performance Testing* nella pagina [Comprendere i risultati](understand-your-test-results.md) dei test.

## Correzioni di bug {#bug-fixes}

* In alcune circostanze, la sincronizzazione interna del sistema non riusciva in modo appropriato, dando luogo a visualizzazioni incoerenti dei dati.
* In alcuni casi, l&#39;attivazione manuale della pipeline non è stata selezionata automaticamente, causando problemi di convalida del modulo.
* Script di build specifici del cliente potrebbero causare errori durante il passaggio di compilazione in base alle incompatibilità dei plug-in.

## Problemi noti {#known-issues}

* Sebbene i clienti siano in grado di selezionare il trigger di commit, la pipeline potrebbe non avviarsi in realtà in base a nuovi commit.
* La barra laterale delle [!UICONTROL Experience Cloud] notifiche potrebbe non caricare le notifiche in modo coerente. Le notifiche, tuttavia, sono visibili nel [!UICONTROL Experience Cloud] file e, se configurate, vengono comunque inviate tramite e-mail.

