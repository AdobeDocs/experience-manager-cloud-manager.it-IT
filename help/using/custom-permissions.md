---
title: Autorizzazioni personalizzate
description: Scopri come utilizzare le autorizzazioni personalizzate per creare nuovi profili di autorizzazioni personalizzati con autorizzazioni configurabili per limitare l’accesso a programmi, pipeline e ambienti per gli utenti di Cloud Manager.
source-git-commit: 769538ec21b21e612619b0c96718f27982574f6c
workflow-type: tm+mt
source-wordcount: '1489'
ht-degree: 96%

---


# Autorizzazioni personalizzate {#custom-permissions}

Scopri come utilizzare le autorizzazioni personalizzate per creare nuovi profili di autorizzazioni personalizzati con autorizzazioni configurabili per limitare l’accesso a programmi, pipeline e ambienti per gli utenti di Cloud Manager.

>[!NOTE]
>
>Questa funzione è disponibile solo per [il programma di adozione anticipata.](/help/release-notes/current.md#early-adoption)

## Introduzione {#introduction}

Cloud Manager dispone di un set di ruoli predefiniti che determinano l’accesso a varie funzioni di Cloud Manager:

* Proprietario business
* Responsabile del programma
* Responsabile della distribuzione
* Sviluppatore

Le autorizzazioni personalizzate consentono agli utenti di creare nuovi profili di autorizzazioni personalizzati con autorizzazioni configurabili per limitare l’accesso a programmi, pipeline e ambienti per gli utenti di Cloud Manager.

>[!TIP]
>
>Per informazioni dettagliate sui ruoli predefiniti, consulta il documento [Autorizzazioni basate sul ruolo.](/help/requirements/role-based-permissions.md)

## Utilizzo di autorizzazioni personalizzate {#using}

Per creare e utilizzare autorizzazioni personalizzate sono necessari tre passaggi:

1. [Creare un nuovo profilo di prodotto.](#create)
1. [Assegnare autorizzazioni personalizzate al nuovo profilo di prodotto.](#assign-permissions)
1. [Assegnare gli utenti al nuovo profilo di prodotto.](#assign-users)

Questa sezione descrive questi passaggi. Durante la creazione delle autorizzazioni personalizzate, potrebbe essere utile consultare le sezioni [Termini](#terms) e [Autorizzazioni configurabili](#configurable-permissions).

>[!NOTE]
>
>Per creare nuovi profili e gestire le autorizzazioni per Cloud Manager, è necessario disporre dei diritti di amministratore del prodotto in Admin Console.

### Creare un nuovo profilo di prodotto {#create}

Per prima cosa è necessario creare un nuovo profilo di prodotto a cui assegnare le autorizzazioni personalizzate.

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)

1. Seleziona il prodotto **AEM Managed Services**.

1. Cerca un’istanza con un nome corrispondente al pattern `*-cloud-manager` e tocca o fai clic per gestire gli utenti e le autorizzazioni.

1. Verrai reindirizzato alla scheda **Prodotti** dell’Admin Console, in cui puoi gestire gli utenti e le autorizzazioni per Cloud Manager. In Admin Console, tocca o fai clic sul pulsante **Nuovo profilo**.

![Pulsante Nuovo profilo](/help/assets/admin-console-new-profile.png)

1. Specifica i dettagli generali sul profilo.

   * **Nome del profilo di prodotto** : nome descrittivo del profilo
   * **Nome visualizzato**: nome abbreviato che verrà visualizzato nell’interfaccia utente (opzioni)
   * **Descrizione** : descrizione informativa del profilo che ne spiega la finalità (facoltativa)
   * **Notifica agli utenti via e-mail** : se questa opzione è selezionata, gli utenti riceveranno una notifica via e-mail quando verranno aggiunti o rimossi da questo profilo.

1. Tocca o fai clic su **Salva** una volta completato.

Il nuovo profilo di prodotto viene salvato ed è visibile nell’elenco dei profili di prodotto in Admin Console.

### Assegnare autorizzazioni personalizzate al profilo {#assign-permissions}

Ora che disponi di un nuovo profilo di prodotto, puoi assegnargli le autorizzazioni personalizzate.

1. In Admin Console, tocca o fai clic sul nome del [nuovo profilo di prodotto appena creato.](#create)

1. Nella finestra visualizzata, seleziona la scheda **Autorizzazioni** per visualizzare un elenco di autorizzazioni modificabili.

   ![Autorizzazioni modificabili](/help/assets/permissions-tab.png)

1. Tocca o fai clic sul collegamento **Modifica** di un’autorizzazione per modificarla.

1. Viene visualizzata la finestra **Modifica autorizzazioni**.
   * L’autorizzazione selezionata nel passaggio precedente è selezionata nella colonna a sinistra.
   * Gli elementi di autorizzazione disponibili per l’assegnazione dell’autorizzazione si trovano nella colonna centrale indicata con Elementi di **Autorizzazioni disponibili**.
   * Gli elementi delle autorizzazioni assegnati si trovano nella colonna di destra indicata con **Elementi di autorizzazione inclusi**.

   ![Modifica elementi di autorizzazione](/help/assets/edit-permission-items.png)

1. Tocca o fai clic sull’icona con il segno più (`+`) accanto all’elemento di autorizzazione per aggiungerlo alla colonna **Elementi di autorizzazione inclusi**.

   * Tocca o fai clic sull’icona `i` accanto a un elemento di autorizzazione per ottenere ulteriori informazioni.

1. Tocca o fai clic sul pulsante **Aggiungi tutte** nella parte superiore della colonna **Autorizzazioni disponibili** per aggiungere tutte le autorizzazioni. Tocca o fai clic su **Rimuovi tutto** per rimuovere tutte le autorizzazioni selezionate in precedenza.

1. Una volta completata la definizione degli elementi di autorizzazioni per il nuovo profilo di prodotto, tocca o fai clic su **Salva**.

Il nuovo profilo di prodotto viene ora salvato con le relative autorizzazioni personalizzate.

### Assegnare utenti alle autorizzazioni personalizzate {#assign-users}

Ora puoi assegnare gli utenti al nuovo profilo di prodotto creato con le autorizzazioni personalizzate.

1. In Admin Console, tocca o fai clic sul nome del [nuovo profilo di prodotto a cui hai appena assegnato le autorizzazioni personalizzate.](#assign-permissions)

1. Nella finestra visualizzata, seleziona la scheda **Utenti**.

1. Tocca o fai clic sul pulsante **Aggiungi utenti** e assegna gli utenti al tuo nuovo profilo di prodotto con autorizzazioni personalizzate.

Consulta la sezione **Aggiungere utenti e gruppi di utenti a un profilo di prodotto** del documento [Gestire i profili di prodotto per gli utenti Enterprise](https://helpx.adobe.com/it/enterprise/using/manage-product-profiles.html) per ulteriori dettagli su come utilizzare Admin Console.

## Autorizzazioni configurabili {#configurable-permissions}

Per creare profili personalizzati sono disponibili le seguenti autorizzazioni.

| Autorizzazione | Descrizione |
|---|---|
| Accesso al programma | Consenti agli utenti di accedere ai programmi |
| Modifica programma | Consenti agli utenti di modificare i programmi |
| Crea pipeline | Consenti agli utenti di creare nuove pipeline |
| Elimina pipeline | Consenti agli utenti di eliminare le pipeline |
| Modifica pipeline | Consenti agli utenti di modificare le pipeline |
| Approvazione/rifiuto delle distribuzioni in produzione | Consenti agli utenti di approvare o rifiutare un passaggio di distribuzione di produzione |
| Annullamento delle esecuzioni della pipeline | Consenti agli utenti di annullare le esecuzioni della pipeline |
| Avvio delle esecuzioni della pipeline | Consenti agli utenti di avviare una nuova esecuzione della pipeline |
| Sostituzione/Rifiuto degli errori importanti della metrica | Consenti agli utenti di ignorare/rifiutare errori importanti di metrica |
| Pianificazione delle distribuzioni in produzione | Consenti agli utenti di pianificare un passaggio di distribuzione in produzione |
| Accesso alle informazioni dell’archivio | Consenti agli utenti di accedere alle informazioni dell’archivio e generare la password di accesso |
| Creazione archivio | Consenti agli utenti di creare nuovi archivi Git |
| Eliminazione archivio | Consenti agli utenti di eliminare gli archivi Git |
| Modifica archivio | Consenti agli utenti di modificare gli archivi Git |
| Genera codice archivio | Consenti agli utenti di generare un progetto da Archetipo |
| Gestione copia contenuto | Consenti agli utenti di gestire le operazioni di copia dei contenuti |

### Autorizzazioni a livello di organizzazione {#organization-level}

Le autorizzazioni a livello di organizzazione si riferiscono alle autorizzazioni che vengono sempre concesse in tutti i programmi all’interno di un’organizzazione.

Le autorizzazioni seguenti sono autorizzazioni a livello di organizzazione:

* **Accesso alle informazioni dell’archivio**: questa autorizzazione a livello di tenant/organizzazione consente agli utenti di generare il nome utente, la password e l’URL dell’archivio per accedere e contribuire al progetto del cliente.
   * Il nome utente e la password per l’accesso all’archivio saranno comuni a tutti gli archivi nell’organizzazione, tuttavia l’URL dell’archivio sarà univoco per ciascun programma.
   * Per ulteriori informazioni, consulta il documento [Archivio del codice sorgente](/help/requirements/source-code-repository.md).

## Termini {#terms}

I seguenti termini vengono utilizzati per creare e gestire autorizzazioni personalizzate e ruoli predefiniti.

| Termine | Descrizione |
|---|---|
| Autorizzazioni predefinite | Ruoli predefiniti come **Proprietario business**, **Responsabile della distribuzione**, ecc. per gestire diverse funzioni di Cloud Manager. Per informazioni dettagliate sui ruoli predefiniti, consulta il documento [Autorizzazioni basate sul ruolo.](/help/requirements/role-based-permissions.md) |
| Autorizzazioni personalizzate | Funzionalità di Cloud Manager che consentono agli utenti di creare profili di autorizzazione per definire i ruoli che gestiscono le funzionalità supportate di Cloud Manager |
| Profilo di autorizzazione | Creato in Admin Console per gestire le autorizzazioni configurabili che saranno applicabili agli utenti che fanno parte del profilo di autorizzazione |
| Autorizzazione configurabile | Autorizzazioni di Cloud Manager che possono essere configurate nel profilo di autorizzazione |
| Elemento di autorizzazione | Un programma, ambiente o risorsa pipeline a cui è possibile applicare un’autorizzazione |

Gli elementi di autorizzazione si riferiscono all’ambito in cui verrà applicata l’autorizzazione. In genere si tratta di uno dei seguenti.

| Tipo di elemento di autorizzazione | Esempio | Descrizione |
|---|---|---|
| Organizzazione | organization:companyA | Tutte le risorse applicabili di un’organizzazione. Una risorsa può essere un programma, un ambiente o una pipeline. Se l’utente aggiunge un’organizzazione per qualsiasi autorizzazione, anche tutte le nuove risorse in tale organizzazione disporranno di tale autorizzazione. |
| Programma | Programma A | Tutte le risorse applicabili di un programma |
| Ambiente | Programma A: ambiente | Applicabile a un ambiente specifico |
| Pipeline | Programma A: pipeline | Applicabile a una pipeline specifica |

## Limitazioni {#limitations}

Quando utilizzi autorizzazioni personalizzate, tieni presente le seguenti limitazioni.

* [È disponibile un set limitato di autorizzazioni](#configurable-permissions) per creare profili personalizzati.
* Risorse come programma, ambiente, pipeline, ecc. create in Cloud Manager potrebbero richiedere fino a due minuti per essere visualizzate in Admin Console e configurare le autorizzazioni.
* In rari scenari in cui il servizio di autorizzazioni personalizzate non risponde, i profili predefiniti restano ancora disponibili e gli utenti nei profili predefiniti dispongono ancora dell’accesso appropriato.

## Domande frequenti {#faq}

### Quali profili di autorizzazione sono profili di autorizzazione predefiniti?

* Proprietario business
* Responsabile del programma
* Responsabile della distribuzione
* Sviluppatore

Per informazioni dettagliate sui ruoli predefiniti, consulta il documento [Autorizzazioni basate sul ruolo.](/help/requirements/role-based-permissions.md)

### Cosa succederà ai profili di autorizzazione predefiniti con l’introduzione dei profili personalizzati?

I profili di prodotto predefiniti e i ruoli di Cloud Manager continuano a funzionare come prima.

### È possibile modificare i profili di autorizzazione predefiniti?

No, i profili predefiniti non sono modificabili. Non è possibile aggiungere o rimuovere autorizzazioni al profilo di autorizzazione predefinito. È possibile aggiungere o rimuovere utenti solo dai profili predefiniti.

### È necessario eliminare i profili di autorizzazione predefiniti poiché ora sono disponibili i profili personalizzati?

I profili di autorizzazione predefiniti non devono essere eliminati da Admin Console.

### È possibile aggiungere utenti a più profili di autorizzazione?

Sì, un utente può far parte di più profili, inclusi profili di autorizzazione predefiniti e personalizzati. Quando un utente viene assegnato a più profili, le autorizzazioni combinate di tutti i profili di autorizzazione assegnati saranno disponibili per tale utente.

### Cosa succede se un utente dispone dell’autorizzazione per modificare un ambiente o una pipeline ma non ha accesso a un programma che contiene l’ambiente o la pipeline?

In questo caso, l’utente non potrà accedere all’ambiente o alla pipeline se non dispone delle autorizzazioni per l’**Accesso al programma** contenenti l’ambiente o la pipeline.

### Cosa succede se dispongo sia di programmi AEM as a Cloud Service che AMS nella stessa organizzazione IMS? È possibile gestire le autorizzazioni da un profilo? {#ams-and-aemaacs}

Devi creare un profilo separato per ciascun tipo di prodotto (ad esempio uno per AEM as Cloud Service e uno per Adobe Managed Services o AMS).
