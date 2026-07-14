---
title: Navigazione nell’interfaccia utente di Cloud Manager
description: Scopri come è organizzata l’interfaccia utente di Cloud Manager e come spostarsi per gestire i programmi e gli ambienti.
exl-id: 9c1545ce-1c6d-417f-a6f4-fe53caef3433
TQID: https://experienceleague.adobe.com/qTv4G7eSJahDusX68iNXzcw64Aq8xxP6SRAtn-SB0t4
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: fa6be369b979682cebf68852603725d8754605ab
workflow-type: tm+mt
source-wordcount: 1641
ht-degree: 36%

---

# Navigare nell’interfaccia utente di Cloud Manager {#navigation}

Scopri come è organizzata l’interfaccia utente di Cloud Manager e come spostarsi per gestire i programmi e gli ambienti.

L’interfaccia utente di Cloud Manager è composta principalmente da due interfacce grafiche:

* [La console Programmi personali](#my-programs-console) è la posizione da cui visualizzare e gestire tutti i programmi.
* [Nella finestra Panoramica programma](#program-overview) è possibile visualizzare i dettagli e gestire un singolo programma.

## Console Programmi personali {#my-programs-console}

Quando si accede a Cloud Manager all&#39;indirizzo [experience.adobe.com](https://experience.adobe.com/experiencemanager) e si seleziona l&#39;organizzazione appropriata, si accede alla console **Programmi personali**.

![Console Programmi personali](/help/getting-started/assets/cloud-manager-my-programs-console.png)

La console **Programmi personali** fornisce una panoramica di tutti i programmi a cui si ha accesso nell&#39;organizzazione selezionata. È costituito da diverse parti.

|   | Area | Descrizione |
| --- | --- | --- |
| 1 | [Barre degli strumenti](#toolbars-my-programs-toolbars) | Utilizza per la selezione dell’organizzazione, gli avvisi e le impostazioni dell’account. |
| 2 | Scheda del pannello laterale sinistro | Varie schede che consentono di attivare/disattivare la visualizzazione corrente dei programmi, tra cui:<br><ul><li>**Experience Manager** apre la home page delle varie soluzioni AEM</li><li>**Tutti i programmi** che visualizzano tutti i programmi disponibili.</li><li>**License** apre la dashboard delle licenze. La Dashboard delle licenze si applica solo ai *programmi AEM as a Cloud Service* (AEMaaCS) e non ai programmi Adobe Managed Services come AEM 6.5 e AEM 6.5 LTS. Per determinare il tipo di servizio del programma (AEMaaCS o AMS), consulta la [sezione Schede del programma](#program-cards) di questo articolo. Per impostazione predefinita, le schede sono chiuse e possono essere visualizzate utilizzando l&#39;icona del menu ![Mostra, hamburger](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), disponibile sul lato sinistro dell&#39;[intestazione Cloud Manager](#cloud-manager-header).</li></ol> |
| 3 | [I miei programmi](#my-programs-section) | Elenca tutti i programmi disponibili selezionabili.<br>Per informazioni dettagliate sui programmi, vedere [Programmi e tipi di programmi](/help/getting-started/program-setup.md). |
| 4 | [Inviti all&#39;azione e statistiche](#cta-statistics) | Offre una panoramica delle attività recenti. |
| 5 | [Collegamenti rapidi](#quick-links) | Accesso rapido alle risorse correlate. |


### Barre degli strumenti {#my-programs-toolbars}

Sono disponibili due barre degli strumenti.

#### Intestazione di Cloud Manager {#cloud-manager-header}

La prima è l’intestazione Cloud Manager. L’intestazione è sempre visibile quando utilizzi Cloud Manager. Si tratta di una posizione centrale che consente di accedere alle impostazioni e alle informazioni applicabili a tutti i programmi Cloud Manager.

![Intestazione di Experience Cloud](/help/getting-started/assets/cloud-manager-header-toolbar.png)

| Area | Descrizione |
| --- | --- |
| ![Mostra icona menu, hamburger](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) | Menu a discesa che consente di accedere alle schede per parti specifiche di un singolo programma.<br>Per determinare il tipo di servizio di cui dispone il programma (AMS o AEMaaCS), consulta la [sezione Schede del programma](#program-cards) di questo documento. |
| ![Icona rosso e bianco di Adobe](/help/getting-started/assets/AdobeLogoWhiteOnRed.svg) Cloud Manager | Fare clic per aprire la console **I miei programmi** di Cloud Manager, indipendentemente dalla posizione in cui ci si trova in Cloud Manager. |
| *`Name of selected organization`* | Il selettore organizzazione visualizza l&#39;organizzazione a cui si è attualmente connessi (in questo esempio, *Foundation Internal*). Fai clic su per passare a un’altra organizzazione se l’Adobe ID è associata a più organizzazioni. |
| ![Icona Feedback](/help/getting-started/assets/AppComment.svg) Feedback | Fai clic su per fornire ad Adobe un feedback su Cloud Manager. |
| ![Icona Assistente IA](/help/getting-started/assets/AIChat.svg) | L’Assistente per l’intelligenza artificiale offre un’interfaccia di conversazione progettata per semplificare la ricerca delle risposte alle query relative ad AEM. Vedi [Assistente IA](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/ai-in-aem/ai-assistant/ai-assistant-in-aem#) |
| ![Icona Aiuto](https://spectrum.adobe.com/static/icons/workflow_18/Smock_HelpOutline_18_N.svg) | Fai clic su per fornire un accesso rapido alle risorse di apprendimento e supporto. |
| ![Icona campana bianca](/help/getting-started/assets/Bell.svg) | Fai clic per visualizzare il numero di [notifiche](/help/using/notifications.md) incomplete attualmente assegnate |
| ![Icona app](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Apps_18_N.svg) | Fai clic per passare rapidamente dalla pagina Home di AEM alle soluzioni AEM |
| *`Dynamic Account icon`* | Fai clic sull&#39;immagine utente per accedere alle **Impostazioni account** e **Impostazioni programma** oppure per uscire.<br>Se si è scelto di non aggiungere un&#39;immagine utente, verrà assegnata un&#39;icona in modo casuale, come illustrato nell&#39;immagine della barra degli strumenti precedente. |

<!--
1. The ![Show menu icon, hamburger](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) icon on the left side of the header is  
   * The License Dashboard only applies to AEM as a Cloud Service programs, not AMS programs.
   * To determine the type of service your program has (AMS or AEMaaCS), see the [Program Cards section](#program-cards) of this document.
1. The **Adobe Cloud Manager** button takes you back to the **My Programs** console of Cloud Manager no matter where you are in Cloud Manager.
1. Click **Feedback** to provide feedback to Adobe about Cloud Manager.
1. The organization selector displays the organization that you are currently signed into (in this example, Foundation Internal). Click to switch to another organization if your Adobe ID is associated with multiple.
1. Clicking the solutions switcher lets you quickly jump to other Experience Cloud solutions.
1. The Help icon provides quick access to learning and support resources.
1. The notifications icon is badged with the number of currently assigned incomplete [notifications](/help/using/notifications.md)
1. Select the icon representing your user to access your user settings. If you do not select a user picture, an icon is randomly assigned. 
-->

#### Barra degli strumenti del programma {#program-toolbar}

La barra degli strumenti del programma fornisce collegamenti per passare da un programma Cloud Manager all’altro e viceversa.

![barra degli strumenti del programma Cloud Manager](/help/getting-started/assets/cloud-manager-programs-toolbar.png)

|   | Area | Descrizione |
| --- | --- | --- |
| 1 | Programmi personali | Fai clic su per aprire un elenco a discesa in cui puoi scegliere di aggiungere un programma, selezionare altri programmi esistenti o tornare alla pagina Home di Experience Manager. |
| 2 | ![Icona informazioni](/help/getting-started/assets/Info.svg) Guida introduttiva | Fai clic su per accedere al [percorso di documentazione sull&#39;onboarding](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/onboarding/journey/overview) per iniziare a utilizzare Cloud Manager.<br>Il percorso di onboarding è progettato per Cloud Manager su Adobe Experience Manager as a Cloud Service (AEMaaCS) e non per Cloud Manager su Adobe Managed Services (AMS). Tuttavia, molti concetti sono gli stessi. |
| 3 | *`Dynamic action button`* | Il pulsante di azione offre azioni appropriate al contesto su cui è possibile fare clic, ad esempio **Aggiungi programma** (illustrato nell&#39;esempio precedente) o aggiungi un dominio. |

### Invito all’azione e statistiche {#cta-statistics}

La sezione call-to-action and statistics fornisce dati aggregati per la tua organizzazione. Ad esempio, se hai configurato correttamente i programmi, vengono visualizzate le statistiche delle attività degli ultimi 90 giorni, inclusi i seguenti:

* Numero di [implementazioni](/help/using/code-deployment.md)
* Numero di [problemi di qualità del codice](/help/using/code-quality-testing.md) identificati
* Numero di build

Se stai iniziando la configurazione dell’organizzazione, puoi seguire i passaggi successivi o consultare le risorse della documentazione.

### Programmi personali {#my-programs-section}

Il contenuto principale della console Programmi personali è la sezione **Programmi personali** in cui i programmi sono elencati come singole schede. Fai clic su una scheda per accedere alla pagina **Panoramica del programma** per informazioni dettagliate sul programma.

A seconda dei privilegi, potrebbe non essere possibile selezionare alcuni programmi.

Per trovare rapidamente il programma desiderato, è possibile utilizzare le seguenti opzioni di ordinamento:

![Opzioni di ordinamento](/help/getting-started/assets/cloud-manager-my-programs-sorting.png)

* Ordina per:
   * Data di creazione
   * Nome del programma
   * Stato
* ![Icona Ordinamento decrescente](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SortOrderDown_18_N.svg) / ![Icona Ordinamento decrescente](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SortOrderUp_18_N.svg) Ordina rispettivamente i programmi.
* ![Icona visualizzazione griglia classica](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ClassicGridView_18_N.svg) / ![Icona testo puntato o elenco](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TextBulleted_18_N.svg) Visualizza programmi rispettivamente in forma griglia o elenco.

#### Schede del programma {#program-cards}

Una scheda o riga in una tabella rappresenta ogni programma, fornendo una panoramica del programma e collegamenti rapidi per intraprendere azioni.

![Scheda Programma](/help/getting-started/assets/cloud-manager-program-card.png)

* Immagine del programma (se configurata)
* Nome del programma (nell&#39;esempio precedente, *WKND Magazine*)
* Tipo di servizio:
   * **Experience Manager** per i programmi AMS
   * **Experience Manager Cloud** per [programmi AEM as a Cloud Service](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/implementing/home)
* Stato (nell&#39;esempio precedente, *Pronto*)
* Soluzioni configurate
* Data di creazione

Fai clic sull&#39;![icona Info](/help/getting-started/assets/Info.svg) per accedere rapidamente a ulteriori informazioni sul programma (utili nella vista a elenco).

![Informazioni a comparsa in Cloud Manager AMS](/help/getting-started/assets/cloud-manager-information-view.png)

Facendo clic sull&#39;icona ![Altro, i puntini di sospensione](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) consentono di accedere alle azioni aggiuntive che è possibile eseguire sul programma.

![Pulsante con i puntini di sospensione per i programmi](/help/getting-started/assets/cloud-manager-program-ellipsis.png)

* Pagina principale di Experience Manager
* Passare a un determinato [ambiente](/help/using/managing-environments.md) del programma
* Apri la [Panoramica del programma](#program-overview)
* [Modifica il programma](/help/getting-started/program-setup.md)
* Mostra monitoraggio

### Collegamenti rapidi {#quick-links}

La sezione dei collegamenti rapidi consente di accedere a risorse utili e correlate.

## Finestra Panoramica del programma {#program-overview}

Se si seleziona un programma nella console [**Programmi personali**](#my-programs-console), viene visualizzata la pagina **Panoramica del programma**.

![Panoramica del programma](/help/getting-started/assets/cloud-manager-program-overview.png)

**Panoramica del programma** consente di accedere a tutti i dettagli di un programma Cloud Manager. Come **I miei programmi**, è costituito da diverse parti.

1. [Barre degli strumenti](#program-overview-toolbar) per tornare rapidamente alla console **Programmi** e spostarsi nel programma.
1. [Area schede](#program-tabs) per passare da un aspetto all&#39;altro del programma.
1. [Invito all’azione](#cta) basato sulle ultime azioni del programma.
1. [Ambienti](#environments) associati del programma.
1. [Pipeline](#pipelines) associate del programma.

### Barre degli strumenti {#program-overview-toolbar}

Le barre degli strumenti per la panoramica del programma sono molto simili a quelle della [console I miei programmi](#my-programs-toolbars). Qui sono illustrate solo le differenze.

#### Intestazione di Cloud Manager {#cloud-manager-header-2}

L&#39;intestazione di Cloud Manager include un menu a discesa ![Mostra icona menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) che si apre automaticamente per visualizzare le schede navigabili della Panoramica del programma.

Fare clic su ![Mostra icona menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) per nascondere le schede.

#### Barra degli strumenti del programma {#program-toolbar-2}

La barra degli strumenti del programma consente comunque di passare rapidamente ad altri programmi, ma consente anche di accedere ad azioni appropriate al contesto, come l’aggiunta e la modifica del programma.

![Barra degli strumenti del programma](assets/cloud-manager-program-toolbar.png)

Inoltre, se si nascondono le schede utilizzando l&#39;icona ![Mostra menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), la barra degli strumenti può comunque mostrare la scheda in uso.

### Schede Programma {#program-tabs}

A ogni programma sono associate molte opzioni e molti dati. Questi dati sono organizzati in schede per semplificare la navigazione dei programmi. Le schede consentono di accedere ai seguenti elementi:

* Panoramica: la panoramica del programma come descritto nel documento corrente
* [Attività](/help/using/managing-pipelines.md#activity): la cronologia delle esecuzioni delle pipeline del programma
* [Pipeline](/help/using/managing-pipelines.md#pipelines): tutte le pipeline configurate per il programma
* [Archivi](/help/managing-code/managing-repositories.md): tutti gli archivi configurati per il programma
* [Rapporti](/help/using/monitoring-environments.md#system-monitoring-overview): metriche quali i dati SLA
* [Ambienti](/help/using/managing-environments.md): tutti gli ambienti configurati per il programma
* [Set di contenuti](/help/using/content-copy.md): set di contenuti creati per scopi di copia
* [Attività copia contenuto](/help/using/content-copy.md): attività di copia dei contenuti
* Percorsi di apprendimento: risorse di apprendimento aggiuntive su Cloud Manager

Per impostazione predefinita, quando si apre un programma si accede alla scheda **Panoramica**. Viene evidenziata la scheda corrente. Seleziona un’altra scheda per visualizzarne i dettagli.

Per nascondere le schede, utilizzare ![Mostra icona menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) nell&#39;intestazione [Cloud Manager](#cloud-manager-header-2).

### Invito all’azione {#cta}

La sezione relativa agli inviti all’azione fornisce informazioni utili in base allo stato del programma. Per un nuovo programma, sono disponibili i passaggi successivi e un promemoria della data di pubblicazione [impostata durante la creazione del programma](/help/getting-started/program-setup.md).

Per un programma live, viene visualizzato lo stato dell’ultima implementazione, con collegamenti per i dettagli e l’avvio di una nuova implementazione.

![Invito all’azione](assets/info-banner.png)

### Scheda Ambienti {#environments}

La scheda **Ambienti** offre una panoramica degli ambienti e collegamenti per azioni rapide.

Nella scheda **Ambienti** sono elencati solo tre ambienti. Per visualizzare tutti gli ambienti del programma, fai clic su **Mostra tutto**.

Per informazioni dettagliate su come gestire gli ambienti, consulta [Gestione degli ambienti](/help/using/managing-environments.md).

### Scheda Pipeline {#pipelines}

La scheda **Pipeline** offre una panoramica delle pipeline e collegamenti per azioni rapide.

Nella scheda **Pipeline** sono elencate solo tre pipeline. Per visualizzare tutte le pipeline del programma, fai clic su **Mostra tutto**.

Per informazioni dettagliate su come gestirle, consulta [Gestione delle pipeline](/help/using/managing-pipelines.md).

### Risorse utili {#useful-resources}

La sezione **Risorse utili** fornisce collegamenti a risorse di apprendimento aggiuntive per Cloud Manager.
