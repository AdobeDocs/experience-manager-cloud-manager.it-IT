---
title: Note sulla versione 2018.7.0
seo-title: Note sulla versione 2018.7.0
description: Ulteriori informazioni su Cloud Manager Release 2018.7.0
seo-description: Segui questa pagina per ottenere informazioni su Cloud Manager Release 2018.7.0.
uuid: d7b49e32-01dc-48ce-b744-e6a806fbdd8a
contentOwner: jsyal
topic-tags: release-notes
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: b64bf9ab-27ed-4f33-adc8-d73d34094f1b
translation-type: tm+mt
source-git-commit: 2dda85baa5e7ed9bfd8933df3580ec6fc3c210fd
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 4%

---


# Note sulla versione 2018.7.0 {#release-notes-for}

La sezione seguente illustra la versione [!UICONTROL Cloud Manager] 2018.7.0 che offre la funzione *scalabilità automatica*.

**Il** ridimensionamento automatico è abilitato tramite la scalabilità orizzontale dei  `Dispatcher/Publish` segmenti nell&#39;ambiente di produzione per supportare un aumento improvviso di carico, volume, accesso e altre metriche monitorate definite.

## Data di rilascio {#release-date}

La data di rilascio per la versione [!UICONTROL Cloud Manager] 2018.7.0 è il 10 settembre 2018.

## Novità {#what-s-new}

* **Provisioning** : ora  [!UICONTROL Cloud Manager] sarà possibile scalare automaticamente l&#39;ambiente di produzione sul programma del cliente ridimensionandolo orizzontalmente con i segmenti Dispatcher/Publish. Nell’interfaccia utente è stata aggiunta la sezione Provisioning di Program Setup (Provisioning), che verrà visualizzata se l’opzione di ridimensionamento automatico è abilitata nel programma del cliente. Per ulteriori informazioni, fare riferimento a [Configurazione del programma](setting-up-program.md).

* **Ambienti**  - È ora possibile visualizzare una visualizzazione dettagliata degli ambienti di produzione e fase insieme alle dimensioni, allo storage, alla regione e allo stato dei nodi associati a ciascun ambiente. Per ulteriori informazioni, fare riferimento a [Gestione degli ambienti](manage-your-environment.md).

* **Analisi**  della qualità del codice - Nuova regola per identificare un utilizzo API non corretto. Per ulteriori informazioni, fare riferimento a [Custom Code Quality Rules](custom-code-quality-rules.md).

* **Test**  delle prestazioni - Durante la visualizzazione dei risultati dei test delle prestazioni, sono disponibili grafici per l&#39;utilizzo della CPU, tempi di attesa I/O disco, frequenza errori di pagina, utilizzo della larghezza di banda del disco, utilizzo della larghezza di banda di rete, tempo di risposta della pagina di picco e tempo di risposta della pagina di 95° percentuale. Fare riferimento alla sezione *Performance Testing* nella pagina [Comprendere i risultati dei test](understand-your-test-results.md).

* **Test**  delle prestazioni - Durante la visualizzazione dei risultati dei test delle prestazioni, è possibile scaricare l&#39;elenco degli errori di pagina e delle richieste lente. Fare riferimento alla sezione *Performance Testing* nella pagina [Comprendere i risultati dei test](understand-your-test-results.md).

## Correzioni di bug {#bug-fixes}

* In alcune circostanze, la sincronizzazione interna del sistema non riusciva in modo appropriato, dando luogo a visualizzazioni incoerenti dei dati.
* In alcuni casi, l&#39;attivazione manuale della pipeline non è stata selezionata automaticamente, causando problemi di convalida del modulo.
* Script di build specifici del cliente potrebbero causare errori durante il passaggio di compilazione in base alle incompatibilità dei plug-in.

## Problemi noti {#known-issues}

* Sebbene i clienti siano in grado di selezionare il trigger di commit, la pipeline potrebbe non avviarsi in realtà in base a nuovi commit.
* La barra laterale di notifica [!UICONTROL Experience Cloud] potrebbe non caricare le notifiche in modo coerente. Le notifiche, tuttavia, sono visibili in [!UICONTROL Experience Cloud] e, se configurate, saranno comunque inviate tramite e-mail.

