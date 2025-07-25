---
title: Autorizzazioni personalizzate
description: Scopri come utilizzare le autorizzazioni personalizzate per creare nuovi profili con autorizzazioni personalizzate e configurabili per limitare l’accesso a programmi, pipeline e ambienti per gli utenti di Cloud Manager.
exl-id: a81eda9f-aa89-40ea-8e4c-52367a0a6aba
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '1373'
ht-degree: 98%

---

# Autorizzazioni personalizzate {#custom-permissions}

Scopri come utilizzare le autorizzazioni personalizzate per creare nuovi profili con autorizzazioni personalizzate e configurabili per limitare l’accesso a programmi, pipeline e ambienti per gli utenti di Cloud Manager.

## Introduzione {#introduction}

Cloud Manager dispone di un set di ruoli predefiniti che determinano l’accesso a varie funzioni di Cloud Manager:

* Proprietario business
* Responsabile del programma
* Responsabile della distribuzione
* Sviluppatore

Le autorizzazioni personalizzate consentono agli utenti di creare nuovi profili di autorizzazioni personalizzati con autorizzazioni configurabili per limitare l’accesso a programmi, pipeline e ambienti per gli utenti di Cloud Manager.

>[!TIP]
>
>Per informazioni dettagliate sui ruoli predefiniti, consulta [Autorizzazioni basate sul ruolo](/help/requirements/role-based-permissions.md).

## Usare le autorizzazioni personalizzate {#using}

La creazione e l’utilizzo di autorizzazioni personalizzate richiede i tre passaggi seguenti:

1. [Creare un nuovo profilo di prodotto](#create).
1. [Assegnare autorizzazioni personalizzate al nuovo profilo di prodotto](#assign-permissions).
1. [Assegnare gli utenti al nuovo profilo di prodotto](#assign-users).

Questa sezione descrive questi passaggi. Durante la creazione delle autorizzazioni personalizzate, potrebbe essere utile consultare le sezioni [Termini](#terms) e [Autorizzazioni configurabili](#configurable-permissions).

>[!NOTE]
>
>Per creare nuovi profili e gestire le autorizzazioni per Cloud Manager, è necessario disporre dei diritti di amministratore del prodotto in Admin Console.

### Creare un nuovo profilo di prodotto {#create}

Per prima cosa è necessario creare un nuovo profilo di prodotto a cui assegnare le autorizzazioni personalizzate.

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)

1. Seleziona il prodotto **AEM Managed Services**.

1. Cerca un’istanza con un nome corrispondente al pattern `*-cloud-manager` e fai clic per gestire gli utenti e le autorizzazioni.

1. Viene aperta la scheda **Prodotti** di Admin Console, in cui puoi gestire gli utenti e le autorizzazioni per Cloud Manager. In Admin Console fai clic su **Nuovo profilo**.

![Pulsante Nuovo profilo](/help/assets/admin-console-new-profile.png)

1. Specifica i dettagli generali sul profilo.

   * **Nome del profilo di prodotto** : nome descrittivo del profilo
   * **Nome visualizzato**: nome abbreviato visualizzato nell’interfaccia utente (opzioni)
   * **Descrizione** : descrizione informativa del profilo che ne spiega la finalità (facoltativa)
   * **Notifica agli utenti via e-mail**: se questa opzione è selezionata, gli utenti riceveranno una notifica via e-mail quando verranno aggiunti o rimossi da questo profilo.

1. Fai clic su **Salva**.

Il nuovo profilo di prodotto viene salvato ed è visibile nell’elenco dei profili di prodotto in Admin Console.

### Assegnare autorizzazioni personalizzate al nuovo profilo di prodotto {#assign-permissions}

Ora che disponi di un nuovo profilo di prodotto, puoi assegnargli le autorizzazioni personalizzate.

1. In Admin Console, fai clic sul nome del [nuovo profilo di prodotto appena creato](#create).

1. Nella finestra visualizzata, seleziona la scheda **Autorizzazioni** per visualizzare un elenco di autorizzazioni modificabili.

   ![Autorizzazioni modificabili](/help/assets/permissions-tab.png)

1. Fai clic sul collegamento **Modifica** per ottenere l’autorizzazione per modificarlo.

1. Viene visualizzata la finestra **Modifica autorizzazioni**.
   * L’autorizzazione selezionata nel passaggio precedente è selezionata nella colonna a sinistra.
   * Gli elementi di autorizzazione disponibili per l’assegnazione dell’autorizzazione si trovano nella colonna centrale indicata con Elementi di **Autorizzazioni disponibili**.
   * Gli elementi di autorizzazione assegnati si trovano nella colonna a destra indicata con **Elementi di autorizzazione inclusi**.

   ![Modificare gli elementi di autorizzazione](/help/assets/edit-permission-items.png)

1. Fai clic sull’icona con il segno più (`+`) accanto all’elemento di autorizzazione per aggiungerlo alla colonna **Elementi di autorizzazione inclusi**. Se necessario, fai clic sull’icona `i` accanto a un elemento di autorizzazione per ottenere ulteriori informazioni.

1. Nella parte superiore della colonna **Autorizzazioni disponibili**, fai clic su **Aggiungi tutto** per aggiungere tutte le autorizzazioni. Allo stesso modo fai clic su **Rimuovi tutto** per rimuovere tutte le autorizzazioni selezionate in precedenza.

1. Una volta completata la definizione degli elementi di autorizzazioni per il nuovo profilo di prodotto, fai clic su **Salva**.

Il nuovo profilo di prodotto viene ora salvato con le relative autorizzazioni personalizzate.

### Assegnare gli utenti al nuovo profilo di prodotto {#assign-users}

Ora puoi assegnare gli utenti al nuovo profilo di prodotto creato con le autorizzazioni personalizzate.

1. In Admin Console, fai clic sul nome del [nuovo profilo di prodotto a cui hai appena assegnato le autorizzazioni personalizzate.](#assign-permissions)

1. Nella finestra visualizzata, seleziona la scheda **Utenti**.

1. Fai clic sul pulsante **Aggiungi utenti** e assegna gli utenti al tuo nuovo profilo di prodotto con autorizzazioni personalizzate.

Consulta **Aggiungere utenti e gruppi di utenti a un profilo di prodotto** nel documento [Gestire i profili di prodotto per gli utenti Enterprise](https://helpx.adobe.com/it/enterprise/using/manage-product-profiles.html) per ulteriori dettagli su come utilizzare Admin Console.

## Autorizzazioni configurabili {#configurable-permissions}

Per creare profili personalizzati sono disponibili le seguenti autorizzazioni.

| Autorizzazione | Descrizione |
| --- | --- |
| `Program Access` | Consenti agli utenti di accedere ai programmi |
| `Program Edit` | Consenti agli utenti di modificare i programmi |
| `Pipeline Create` | Consenti agli utenti di creare nuove pipeline |
| `Pipeline Delete` | Consenti agli utenti di eliminare le pipeline |
| `Pipeline Edit` | Consenti agli utenti di modificare le pipeline |
| `Production Deployments Approve/Reject` | Consenti agli utenti di approvare o rifiutare un passaggio di distribuzione di produzione |
| `Pipeline Executions Cancel` | Consenti agli utenti di annullare le esecuzioni della pipeline |
| `Pipeline Executions Start` | Consenti agli utenti di avviare nuove esecuzioni della pipeline |
| `Override/Reject Important Metric Failures` | Consenti agli utenti di ignorare/rifiutare errori importanti di metrica |
| `Production Deployments Schedule` | Consenti agli utenti di pianificare un passaggio di distribuzione in produzione |
| `Repository Info Access` | Consenti agli utenti di accedere alle informazioni dell’archivio e generare una password di accesso |
| `Repository Create` | Consenti agli utenti di creare nuovi archivi Git |
| `Repository Delete` | Consenti agli utenti di eliminare gli archivi Git |
| `Repository Edit` | Consenti agli utenti di modificare gli archivi Git |
| `Repository Code Generate` | Consenti agli utenti di generare progetti da un archetipo |
| `Content Copy Manage` | Consenti agli utenti di gestire le operazioni di copia dei contenuti |

### Autorizzazioni a livello di organizzazione {#organization-level}

Le autorizzazioni a livello di organizzazione vengono sempre applicate a tutti i programmi all’interno di un’organizzazione.

Un esempio di autorizzazione a livello di organizzazione in Cloud Manager è **Accesso alle informazioni dell’archivio**. Questa autorizzazione consente agli utenti di generare un nome utente, una password e un URL dell’archivio per accedere e contribuire ai progetti della clientela. Anche se il nome utente e la password rimangono coerenti in tutti gli archivi dell’organizzazione, ogni programma ha un URL di archivio univoco.

Per ulteriori informazioni, consulta [Archivio del codice sorgente](/help/requirements/source-code-repository.md).

## Termini {#terms}

I seguenti termini vengono utilizzati per creare e gestire autorizzazioni personalizzate e ruoli predefiniti.

| Termine | Descrizione |
| --- | --- |
| Autorizzazioni predefinite | Ruoli predefiniti come **Proprietario business**, **Manager implementazione**, ecc. per gestire diverse funzioni di Cloud Manager. Per informazioni dettagliate sui ruoli predefiniti, consulta [Autorizzazioni basate sul ruolo](/help/requirements/role-based-permissions.md). |
| Autorizzazioni personalizzate | Funzioni di Cloud Manager che consentono agli utenti di creare profili di autorizzazione per definire i ruoli che gestiscono le funzionalità supportate di Cloud Manager |
| Profilo di autorizzazione | Creato in Admin Console per gestire le autorizzazioni configurabili che saranno applicabili agli utenti che fanno parte del profilo di autorizzazione |
| Autorizzazione configurabile | Autorizzazioni di Cloud Manager che possono essere configurate nel profilo di autorizzazione |
| Elemento di autorizzazione | Un programma, ambiente o risorsa pipeline a cui è possibile applicare un’autorizzazione |

Gli elementi di autorizzazione si riferiscono all’ambito in cui verranno applicate le autorizzazioni. In genere, si tratta di uno dei seguenti.

| Tipo di elemento di autorizzazione | Esempio | Descrizione |
| --- | --- | --- |
| Organizzazione | organization:companyA | Tutte le risorse applicabili di un’organizzazione. Una risorsa può essere un programma, un ambiente o una pipeline. Se l’utente aggiunge un’organizzazione per qualsiasi autorizzazione, anche tutte le nuove risorse in tale organizzazione disporranno di tale autorizzazione. |
| Programma | Programma A | Tutte le risorse applicabili di un programma. |
| Ambiente | Programma A: ambiente | Applicabile in un ambiente specifico. |
| Pipeline | Programma A: pipeline | Applicabile su una pipeline specifica. |

## Limitazioni {#limitations}

Quando utilizzi autorizzazioni personalizzate, tieni presente le seguenti limitazioni:

* [È disponibile un set limitato di autorizzazioni](#configurable-permissions) per creare profili personalizzati.
* Risorse come programma, ambiente, pipeline, ecc. create in Cloud Manager potrebbero richiedere fino a due minuti per essere visualizzate in Admin Console e configurare le autorizzazioni.
* In rari scenari in cui il servizio di autorizzazioni personalizzate non risponde, i profili predefiniti restano ancora disponibili e gli utenti nei profili predefiniti dispongono ancora dell’accesso appropriato.

## Domande frequenti {#faq}

### Quali profili di autorizzazione sono profili di autorizzazione predefiniti?

* Proprietario business
* Responsabile del programma
* Responsabile della distribuzione
* Sviluppatore

Per informazioni dettagliate sui ruoli predefiniti, consulta [Autorizzazioni basate sul ruolo](/help/requirements/role-based-permissions.md).

### Cosa succederà ai profili di autorizzazione predefiniti con l’introduzione dei profili personalizzati?

I profili di prodotto predefiniti e i ruoli di Cloud Manager continuano a funzionare come prima.

### È possibile modificare i profili di autorizzazione predefiniti?

No, i profili predefiniti non sono modificabili. Non è possibile aggiungere o rimuovere autorizzazioni al profilo di autorizzazione predefinito. È possibile aggiungere o rimuovere utenti solo dai profili predefiniti.

### È necessario eliminare i profili di autorizzazione predefiniti poiché ora sono disponibili i profili personalizzati?

I profili di autorizzazione predefiniti non devono essere eliminati da Admin Console.

### È possibile aggiungere utenti a più profili di autorizzazione?

Sì, un utente può far parte di più profili, inclusi profili di autorizzazione predefiniti e personalizzati. Un utente assegnato a più profili ha a disposizione le autorizzazioni combinate di tutti i profili di autorizzazione assegnati.

### Cosa succede se un utente dispone dell’autorizzazione per modificare un ambiente o una pipeline ma non ha accesso a un programma che contiene l’ambiente o la pipeline?

In questo caso, l’utente non potrà accedere all’ambiente o alla pipeline se non dispone delle autorizzazioni per l’**Accesso al programma** contenente l’ambiente o la pipeline.

### Cosa succede se dispongo sia di programmi AEM as a Cloud Service che AMS nella stessa organizzazione IMS? È possibile gestire le autorizzazioni da un profilo? {#ams-and-aemaacs}

Crea un profilo separato per ciascun tipo di prodotto. Vale a dire uno per AEM as a Cloud Service e uno per Adobe Managed Services o AMS.
