---
title: Autorizzazioni personalizzate
description: Scopri come utilizzare le autorizzazioni personalizzate per creare nuovi profili di autorizzazioni personalizzati con autorizzazioni configurabili per limitare l’accesso a programmi, pipeline e ambienti per gli utenti di Cloud Manager.
exl-id: a81eda9f-aa89-40ea-8e4c-52367a0a6aba
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '1416'
ht-degree: 46%

---

# Autorizzazioni personalizzate {#custom-permissions}

Scopri come utilizzare le autorizzazioni personalizzate per creare nuovi profili di autorizzazioni personalizzati con autorizzazioni configurabili per limitare l’accesso a programmi, pipeline e ambienti per gli utenti di Cloud Manager.

## Introduzione {#introduction}

Cloud Manager dispone di un set di ruoli predefiniti che determinano l’accesso a varie funzioni di Cloud Manager:

* Proprietario business
* Responsabile del programma
* Responsabile della distribuzione
* Sviluppatore

Le autorizzazioni personalizzate consentono agli utenti di creare nuovi profili di autorizzazioni personalizzati con autorizzazioni configurabili per limitare l’accesso a programmi, pipeline e ambienti per gli utenti di Cloud Manager.

>[!TIP]
>
>Per informazioni dettagliate sui ruoli predefiniti, vedere [Autorizzazioni basate sul ruolo](/help/requirements/role-based-permissions.md).

## Utilizzare le autorizzazioni personalizzate {#using}

La creazione e l’utilizzo di autorizzazioni personalizzate richiede i tre passaggi seguenti:

1. [Crea un nuovo profilo di prodotto](#create).
1. [Assegna autorizzazioni personalizzate al nuovo profilo di prodotto](#assign-permissions).
1. [Assegna utenti al nuovo profilo di prodotto](#assign-users).

Questa sezione descrive questi passaggi. Potrebbe essere utile visualizzare le sezioni [Termini](#terms) e [Autorizzazioni configurabili](#configurable-permissions) durante la creazione di autorizzazioni personalizzate.

>[!NOTE]
>
>Per creare nuovi profili e gestire le autorizzazioni per Cloud Manager, è necessario disporre dei diritti di amministratore del prodotto nell’Admin Console.

### Creare un nuovo profilo di prodotto {#create}

Crea innanzitutto un nuovo profilo di prodotto a cui assegnare autorizzazioni personalizzate.

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)

1. Seleziona il prodotto **AEM Managed Services**.

1. Cercare e l&#39;istanza con il nome corrispondente al pattern `*-cloud-manager` e fare clic per gestire utenti e autorizzazioni.

1. Sei stato reindirizzato alla scheda **Prodotti** dell&#39;Admin Console, dove puoi gestire utenti e autorizzazioni per Cloud Manager. Nell&#39;Admin Console fare clic su **Nuovo profilo**.

![Pulsante Nuovo profilo](/help/assets/admin-console-new-profile.png)

1. Specifica i dettagli generali sul profilo.

   * **Nome del profilo di prodotto** : nome descrittivo del profilo
   * **Nome visualizzato** - Nome abbreviato visualizzato nell&#39;interfaccia utente (opzioni)
   * **Descrizione** : descrizione informativa del profilo che ne spiega la finalità (facoltativa)
   * **Notifica gli utenti via e-mail** - Se selezionata, il sistema avvisa gli utenti via e-mail quando vengono aggiunti o rimossi da questo profilo.

1. Fai clic su **Salva**.

Il nuovo profilo di prodotto viene salvato ed è visibile nell’elenco dei profili di prodotto in Admin Console.

### Assegnare autorizzazioni personalizzate al nuovo profilo di prodotto {#assign-permissions}

Ora che disponi di un nuovo profilo di prodotto, puoi assegnargli le autorizzazioni personalizzate.

1. Nell&#39;Admin Console, fai clic sul nome del [nuovo profilo di prodotto appena creato](#create).

1. Nella finestra visualizzata, seleziona la scheda **Autorizzazioni** per visualizzare un elenco di autorizzazioni modificabili.

   ![Autorizzazioni modificabili](/help/assets/permissions-tab.png)

1. Fai clic sul collegamento **Modifica** per ottenere l&#39;autorizzazione per modificarlo.

1. Viene visualizzata la finestra **Modifica autorizzazioni**.
   * L’autorizzazione selezionata nel passaggio precedente è selezionata nella colonna a sinistra.
   * Gli elementi di autorizzazione disponibili per l’assegnazione dell’autorizzazione si trovano nella colonna centrale indicata con Elementi di **Autorizzazioni disponibili**.
   * Gli elementi di autorizzazione assegnati si trovano nella colonna a destra indicata con **Elementi di autorizzazione inclusi**.

   ![Modifica elementi di autorizzazione](/help/assets/edit-permission-items.png)

1. Fare clic sull&#39;icona più (`+`) accanto all&#39;elemento di autorizzazione per aggiungerlo alla colonna **Elementi di autorizzazione inclusi**. Se necessario, fai clic sull&#39;icona `i` accanto a un elemento di autorizzazione per ulteriori informazioni.

1. Nella parte superiore della colonna **Autorizzazioni disponibili**, fare clic su **Aggiungi tutto** per aggiungere tutte le autorizzazioni. Allo stesso modo, fare clic su **Rimuovi tutto** per rimuovere tutte le autorizzazioni precedentemente selezionate.

1. Al termine della definizione delle autorizzazioni per il nuovo profilo di prodotto, fare clic su **Salva**.

Il nuovo profilo di prodotto viene ora salvato con le relative autorizzazioni personalizzate.

### Assegnare utenti al nuovo profilo di prodotto {#assign-users}

Ora puoi assegnare gli utenti al nuovo profilo di prodotto creato con le autorizzazioni personalizzate.

1. Nell&#39;Admin Console, fare clic sul nome del [nuovo profilo di prodotto a cui sono state appena assegnate le autorizzazioni personalizzate](#assign-permissions).

1. Nella finestra visualizzata, seleziona la scheda **Utenti**.

1. Fai clic su **Aggiungi utenti** e assegna gli utenti al tuo nuovo profilo di prodotto con autorizzazioni personalizzate.

Per ulteriori informazioni su come utilizzare l&#39;Admin Console, vedere **Aggiungere utenti e gruppi di utenti a un profilo di prodotto** nel documento [Gestire i profili di prodotto per gli utenti aziendali](https://helpx.adobe.com/it/enterprise/using/manage-product-profiles.html).

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
| Avvio delle esecuzioni della pipeline | Consenti agli utenti di avviare nuove esecuzioni della pipeline |
| Sostituzione/Rifiuto degli errori importanti della metrica | Consenti agli utenti di ignorare/rifiutare errori importanti di metrica |
| Pianificazione delle distribuzioni in produzione | Consenti agli utenti di pianificare un passaggio di distribuzione in produzione |
| Accesso alle informazioni dell’archivio | Consenti agli utenti di accedere alle informazioni del repository e generare una password di accesso |
| Creazione di un archivio | Consenti agli utenti di creare nuovi archivi Git |
| Eliminazione di un archivio | Consenti agli utenti di eliminare gli archivi Git |
| Modifica di un archivio | Consenti agli utenti di modificare gli archivi Git |
| Generazione del codice di un archivio | Consenti agli utenti di generare progetti da un archetipo |
| Gestione della copia dei contenuti | Consenti agli utenti di gestire le operazioni di copia dei contenuti |

### Autorizzazioni a livello di organizzazione {#organization-level}

Le autorizzazioni a livello di organizzazione vengono sempre applicate a tutti i programmi all’interno di un’organizzazione.

Un esempio di autorizzazione a livello di organizzazione in Cloud Manager è **Repository Info Access**. Questa autorizzazione consente agli utenti di generare un nome utente, una password e un URL dell’archivio per accedere e contribuire ai progetti dei clienti. Anche se il nome utente e la password rimangono coerenti in tutti gli archivi dell’organizzazione, ogni programma ha un URL di archivio univoco.

Per ulteriori informazioni, vedere [Archivio codice Source](/help/requirements/source-code-repository.md).

## Termini {#terms}

I seguenti termini vengono utilizzati per creare e gestire autorizzazioni personalizzate e ruoli predefiniti.

| Termine | Descrizione |
|---|---|
| Autorizzazioni predefinite | Ruoli predefiniti come **Proprietario business**, **Responsabile distribuzione** e così via. per gestire diverse funzioni di Cloud Manager. Per informazioni dettagliate sui ruoli predefiniti, vedere [Autorizzazioni basate sul ruolo](/help/requirements/role-based-permissions.md). |
| Autorizzazioni personalizzate | Funzioni di Cloud Manager che consentono agli utenti di creare profili di autorizzazione per definire ruoli che governino le funzioni supportate di Cloud Manager |
| Profilo di autorizzazione | Creato nell’Admin Console per gestire le autorizzazioni configurabili applicabili agli utenti che fanno parte del profilo di autorizzazione |
| Autorizzazione configurabile | Le autorizzazioni di Cloud Manager possono essere configurate nel profilo di autorizzazione |
| Elemento di autorizzazione | Un programma, ambiente o risorsa pipeline a cui è possibile applicare un’autorizzazione |

Gli elementi autorizzazione si riferiscono all’ambito in cui vengono applicate le autorizzazioni. In genere, si tratta di uno dei seguenti.

| Tipo di elemento di autorizzazione | Esempio | Descrizione |
|---|---|---|
| Organizzazione | organization:companyA | Tutte le risorse applicabili di un’organizzazione. Una risorsa può essere un programma, un ambiente o una pipeline. Se l’utente aggiunge un’organizzazione per qualsiasi autorizzazione, anche tutte le nuove risorse in tale organizzazione dispongono di tale autorizzazione. |
| Programma | Programma A | Tutte le risorse applicabili di un programma |
| Ambiente | Programma A: ambiente | Applicabile in un ambiente specifico |
| Pipeline | Programma A: pipeline | Applicabile a una pipeline specifica |

## Limitazioni {#limitations}

Quando utilizzi le autorizzazioni personalizzate, tieni presente le seguenti limitazioni:

* [È disponibile un set limitato di autorizzazioni](#configurable-permissions) per creare profili personalizzati.
* Risorse come programma, ambiente, pipeline, ecc. create in Cloud Manager potrebbero richiedere fino a due minuti per essere visualizzate in Admin Console e configurare le autorizzazioni.
* In rari scenari in cui un servizio di autorizzazioni personalizzate non risponde, i profili predefiniti sono ancora disponibili e gli utenti nei profili predefiniti dispongono ancora dell’accesso appropriato.

## Domande frequenti {#faq}

### Quali profili di autorizzazione sono profili di autorizzazione predefiniti?

* Proprietario business
* Responsabile del programma
* Responsabile della distribuzione
* Sviluppatore

Per informazioni dettagliate sui ruoli predefiniti, vedere [Autorizzazioni basate sul ruolo](/help/requirements/role-based-permissions.md).

### Cosa succederà ai profili di autorizzazione predefiniti con l’introduzione dei profili personalizzati?

I profili di prodotto predefiniti e i ruoli Cloud Manager continuano a funzionare come prima.

### È possibile modificare i profili di autorizzazione predefiniti?

No, i profili predefiniti non sono modificabili. Non è possibile aggiungere o rimuovere autorizzazioni al profilo di autorizzazione predefinito. È possibile aggiungere o rimuovere utenti solo dai profili predefiniti.

### È necessario eliminare i profili di autorizzazione predefiniti poiché ora sono disponibili i profili personalizzati?

I profili di autorizzazione predefiniti non devono essere eliminati da Admin Console.

### È possibile aggiungere utenti a più profili di autorizzazione?

Sì, un utente può far parte di più profili, inclusi profili di autorizzazione predefiniti e personalizzati. Quando un utente viene assegnato a più profili, le autorizzazioni combinate di tutti i profili di autorizzazione assegnati sono disponibili per tale utente.

### Cosa succede se un utente dispone dell’autorizzazione per modificare un ambiente o una pipeline ma non ha accesso a un programma che contiene l’ambiente o la pipeline?

In questo scenario, l&#39;utente non è in grado di accedere all&#39;ambiente o alla pipeline se non dispone delle autorizzazioni di **Accesso al programma** contenenti l&#39;ambiente o la pipeline.

### Cosa succede se dispongo sia di programmi AEM as a Cloud Service che AMS nella stessa organizzazione IMS? È possibile gestire le autorizzazioni da un profilo? {#ams-and-aemaacs}

Crea un profilo separato per ciascun tipo di prodotto. Vale a dire uno per l&#39;AEM come Cloud Service e uno per Adobe Managed Services o AMS.
