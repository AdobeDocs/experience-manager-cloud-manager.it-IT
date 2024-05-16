---
title: Navigazione nell’interfaccia utente di Cloud Manager
description: Scopri come è organizzata l’interfaccia utente di Cloud Manager e come navigare per gestire i programmi e gli ambienti.
exl-id: 9c1545ce-1c6d-417f-a6f4-fe53caef3433
source-git-commit: 9d0f4dd29e2d05ab3f6900ee23c536b91c849e65
workflow-type: tm+mt
source-wordcount: '1292'
ht-degree: 5%

---

# Navigazione nell’interfaccia utente di Cloud Manager {#navigation}

Scopri come è organizzata l’interfaccia utente di Cloud Manager e come navigare per gestire i programmi e gli ambienti.

L’interfaccia utente di Cloud Manage è composta principalmente da due interfacce grafiche:

* [La console Programmi](#my-programs) in cui è possibile visualizzare e gestire tutti i programmi.
* [Finestra Panoramica programma](#program-overview) dove puoi visualizzare i dettagli di e gestire un singolo programma.

## Console Programmi personali {#my-programs}

Quando accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selezionare l&#39;organizzazione appropriata, si arriva al **I miei programmi** console.

![Console Programmi](assets/my-programs-console.png)

La console Programmi personali fornisce una panoramica di tutti i programmi a cui si ha accesso nell&#39;organizzazione selezionata. È composto da diverse parti.

1. [Barre degli strumenti](#toolbars-my-programs-toolbars) per la selezione di organizzazioni, avvisi e impostazioni account
1. [Statistiche e invito all&#39;azione](#statistics) per una panoramica dell’attività recente
1. [Programmi e licenze](#programs-license) per comprendere lo stato attuale della licenza e gestire i programmi
1. [Collegamenti rapidi](#quick-links) per accedere facilmente alle risorse correlate

>[!TIP]
>
>Consulta il documento [Programmi e tipi di programmi](/help/getting-started/program-setup.md) per informazioni dettagliate sui programmi.

### Barre degli strumenti {#my-programs-toolbars}

Sono disponibili due barre degli strumenti sovrapposte.

#### Intestazione di Cloud Manager {#cloud-manager-header}

Il primo è l’intestazione di Cloud Manager, che è persistente durante la navigazione in Cloud Manager. Si tratta di un ancoraggio che consente di accedere alle impostazioni e alle informazioni applicabili ai diversi programmi di Cloud Manager.

![Intestazione di Experience Cloud](assets/experience-cloud-header.png)

1. Il pulsante Cloud Manager ti riporterà alla console I miei programmi di Cloud Manager, indipendentemente dalla tua posizione in Cloud Manager.
1. Tocca o fai clic sul pulsante Feedback per fornire un feedback all’Adobe su Cloud Manager.
1. Il selettore organizzazione visualizza l’organizzazione a cui sei attualmente connesso (in questo esempio, Foundation Internal). Tocca o fai clic per passare a un’altra organizzazione se il tuo Adobe ID è associato a più di una.
1. Toccando o facendo clic sul selettore delle soluzioni puoi passare rapidamente ad altre soluzioni di Experience Cloud.
1. L’icona dell’aiuto fornisce un accesso rapido alle risorse di apprendimento e supporto.
1. L’icona delle notifiche viene contrassegnata con il numero di notifiche incomplete attualmente assegnate [notifiche.](/help/using/notifications.md)
1. Seleziona l’icona che rappresenta l’utente per accedere alle impostazioni utente. Se non hai configurato un’immagine utente, viene assegnata un’icona in modo casuale.

#### Barra degli strumenti del programma {#program-toolbar}

La barra degli strumenti del programma fornisce collegamenti per passare da un programma all’altro e viceversa.

![Barra degli strumenti del programma](assets/program-toolbar.png)

1. Il selettore di programma si apre in un menu a discesa in cui puoi selezionare rapidamente altri programmi o intraprendere azioni appropriate al contesto, ad esempio la creazione di un nuovo programma
1. Il collegamento introduttivo consente di accedere a [percorso di documentazione sull’onboarding](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/overview) per iniziare a utilizzare Cloud Manager.
   * Il percorso di onboarding è progettato per gli as a Cloud Service AEM e non per i Cloud Service AMS, ma molti concetti sono gli stessi.
1. Il pulsante di azione offre azioni appropriate al contesto, ad esempio la creazione di un nuovo programma.

### Statistiche {#statistics}

La sezione Statistiche fornisce dati aggregati per l’organizzazione. Ad esempio, se i programmi sono stati configurati correttamente, è possibile che vengano visualizzate le statistiche delle attività degli ultimi 90 giorni, tra cui:

* Numero di [implementazioni](/help/using/code-deployment.md)
* Numero di [problemi di qualità del codice](/help/using/code-quality-testing.md) identificati
* Numero di build

Oppure, se stai iniziando la configurazione dell’organizzazione, ci potrebbero essere suggerimenti sui passaggi successivi o sulle risorse della documentazione.

### Programmi e licenza {#programs-license}

Il contenuto principale della console Programmi è l&#39;elenco dei programmi e lo stato della licenza.

#### Scheda Programmi {#programs}

Il **Programmi** scheda elenca le schede che rappresentano ogni programma a cui hai accesso. Tocca o fai clic su una scheda per accedere al **Panoramica del programma** pagina del programma per informazioni dettagliate sul programma.

Utilizza le opzioni di ordinamento per trovare meglio il programma necessario.

![Opzioni di ordinamento](assets/my-programs-sorting.png)

* Ordina per
   * Data di creazione (impostazione predefinita)
   * Nome del programma
   * Stato
* Crescente (predefinito) / Decrescente
* Vista griglia (impostazione predefinita)
* Vista a elenco 

Ogni programma è rappresentato da una scheda (o riga in una tabella) che fornisce una panoramica del programma e collegamenti rapidi per intervenire.

![Scheda Programma](assets/program-card.png)

* Immagine del programma (se configurata)
* Nome del programma
* Tipo di servizio: **Experience Manager Cloud** per [Programmi as a Cloud Service AEM](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/home) o **Experience Manager** per i programmi AMS
* Stato
* Soluzioni configurate
* Data di creazione

L’icona delle informazioni consente inoltre di accedere rapidamente a informazioni aggiuntive sul programma (utili nella vista a elenco).

![Informazioni](assets/information-view.png)

L’icona con i puntini di sospensione ti permette di accedere alle azioni aggiuntive che puoi eseguire sul programma.

![Pulsante con i puntini di sospensione per i programmi](assets/program-ellipsis.png)

* Passare a un determinato [ambiente](/help/using/managing-environments.md) del programma
* Apri [panoramica del programma](#program-overview)
* [Modifica il programma](/help/getting-started/program-setup.md)
* Mostra monitoraggio

#### Scheda Licenza {#license-tab}

Il **Licenza** consente di accedere rapidamente alla dashboard delle licenze.

### Collegamenti rapidi {#quick-links}

La sezione dei collegamenti rapidi consente di accedere alle risorse correlate di uso comune.

## Finestra Panoramica programma {#program-overview}

Dopo aver selezionato un programma nella console I miei programmi, viene visualizzata la panoramica del programma.

![Panoramica del programma](assets/program-overview.png)

La panoramica del programma consente di accedere a tutti i dettagli di un programma Cloud Manager. Come la console Programmi, è composta da diverse parti.

1. [Barre degli strumenti](#program-overview-toolbar) per tornare rapidamente alla console Programmi e passare al programma
1. [Schede](#program-tabs) per passare da un aspetto all&#39;altro del programma
1. A [invito all&#39;azione](#cta) sulla base delle ultime azioni del programma
1. Un [panoramica degli ambienti](#environments) del programma
1. Un [panoramica delle pipeline](#pipelines) del programma
1. Collegamenti a [risorse utili](#useful-resources)

### Barre degli strumenti {#program-overview-toolbar}

Le barre degli strumenti per la panoramica del programma sono molto simili a quelle della [Console Programmi.](#my-programs-toolbars) Solo le differenze sono illustrate qui.

#### Intestazione di Cloud Manager {#cloud-manager-header-2}

L’intestazione di Cloud Manager dispone di un menu hamburger che si apre automaticamente per mostrare le schede navigabili della panoramica del programma.

![Menu hamburger di Cloud Manager](assets/cloud-manager-hamburger.png)

Tocca o fai clic sull’icona del menu hamburger per nascondere le schede.

#### Barra degli strumenti del programma {#program-toolbar-2}

La barra degli strumenti del programma consente comunque di passare rapidamente ad altri programmi, ma consente anche di accedere ad azioni appropriate al contesto, come l’aggiunta e la modifica del programma.

![Barra degli strumenti del programma](assets/cloud-manager-program-toolbar.png)

Inoltre, la barra degli strumenti fornisce sempre la scheda su cui ci si trova se si è scelto di nascondere le schede utilizzando il menu hamburger.

### Schede Programma {#program-tabs}

A ogni programma sono associate molte opzioni e molti dati. Questi dati vengono raccolti in schede per semplificare la navigazione nel programma. Le schede consentono di accedere a:

* Panoramica: la panoramica del programma come descritto nel documento corrente
* [Attività](/help/using/managing-pipelines.md#activity) - La cronologia delle esecuzioni delle pipeline del programma
* [Pipeline](/help/using/managing-pipelines.md#pipelines) - Tutte le pipeline configurate per il programma
* [Archivi](/help/managing-code/repositories.md) - Tutti gli archivi configurati per il programma
* [Rapporti](/help/using/monitoring-environments.md#system-monitoring-overview) - Metriche quali i dati SLA
* [Ambienti](/help/using/managing-environments.md) - Tutti gli ambienti configurati per il programma
* [Set di contenuti](/help/using/content-copy.md) - Set di contenuti creati a scopo di copia
* [Attività copia contenuto](/help/using/content-copy.md) - Attività di copia dei contenuti
* Percorsi di apprendimento: risorse di apprendimento aggiuntive su Cloud Manager

Per impostazione predefinita, quando si apre un programma si accede al **Panoramica** scheda. Viene evidenziata la scheda corrente. Seleziona un’altra scheda per visualizzarne i dettagli.

Utilizza il menu hamburger in [Intestazione di Cloud Manager](#cloud-manager-header-2) per nascondere le schede.

### Invito all’azione {#cta}

La sezione relativa agli inviti all&#39;azione fornisce informazioni utili in base allo stato del programma. Per un nuovo programma puoi vedere i passaggi successivi offerti e un promemoria della data di pubblicazione, [impostato durante la creazione del programma.](/help/getting-started/program-setup.md)

Per un programma live, lo stato dell’ultima implementazione con collegamenti per i dettagli e l’avvio di una nuova implementazione.

![Invito all’azione](assets/info-banner.png)

### Scheda Ambienti {#environments}

Il **Ambienti** offre una panoramica degli ambienti e collegamenti per azioni rapide.

Nella scheda **Ambienti** sono elencati solo tre ambienti. Clic **Mostra tutto** per visualizzare tutti gli ambienti del programma.

Consulta il documento [Gestione degli ambienti](/help/using/managing-environments.md) per informazioni dettagliate su come gestire gli ambienti.

### Scheda Pipeline {#pipelines}

Il **Pipeline** offre una panoramica delle pipeline e dei collegamenti per azioni rapide.

Il **Pipeline** nella scheda sono elencate solo tre pipeline. Clic **Mostra tutto** per visualizzare tutte le pipeline del programma.

Consulta il documento [Gestione delle pipeline](/help/using/managing-pipelines.md) per informazioni dettagliate su come gestire le pipeline.

### Risorse utili {#useful-resources}

Il **Risorse utili** Questa sezione fornisce collegamenti a risorse di apprendimento aggiuntive per Cloud Manager.
