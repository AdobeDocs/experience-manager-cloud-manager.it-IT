---
title: Autorizzazioni basate sul ruolo
description: Scopri le autorizzazioni preconfigurate basate sui ruoli di Cloud Manager per gestire l’accesso alle risorse cloud.
exl-id: b66533fb-db93-40e8-919d-581261fdbf24
source-git-commit: 522e5fbc650a8159602eb1aeaf42d64f4e23e8b4
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 16%

---


# Autorizzazioni basate sul ruolo {#role-based-permissions}

[!UICONTROL Cloud Manager] dispone di ruoli preconfigurati con le autorizzazioni appropriate. Ad esempio, uno sviluppatore sviluppa il codice e dispone dell’autorizzazione per inviare il codice all’archivio Git. Un proprietario aziendale dispone di autorizzazioni diverse che gli consentono di definire gli indicatori prestazioni chiave (KPI, Key Performance Indicator) e di approvare le distribuzioni.

## Ruoli utente {#user-roles}

Gestione dei ruoli per [!UICONTROL Cloud Manager] viene eseguito utilizzando [Admin Console.](https://helpx.adobe.com/it/enterprise/using/admin-console.html) Qualsiasi utente di [!UICONTROL Cloud Manager] deve essere membro dell’organizzazione IMS del cliente e disporre del contesto di prodotto di Adobe Managed Services. Le appartenenze a ruoli specifici vengono fornite aggiungendo l’utente a un [!UICONTROL Cloud Manager] profilo di prodotto nell’Admin Console.

Per ulteriori informazioni su come impostare i ruoli, consulta il documento [Impostazione di utenti e ruoli.](/help/requirements/users-and-roles.md)

In questa tabella sono elencati i ruoli che è possibile assegnare nell’Admin Console.

| [!UICONTROL Cloud Manager] Ruolo | Descrizione |
|---|---|
| Business Owner (Proprietario) | Questo è l’utente principale che completa l’iniziale [!UICONTROL Cloud Manager] imposta ed è responsabile della definizione dei KPI, dell’approvazione delle implementazioni di produzione e dell’override di importanti errori a 3 livelli quando necessario. |
| Program Manager (Responsabile programma) | Questo utente utilizza [!UICONTROL Cloud Manager] per eseguire la configurazione del team, esaminare lo stato, visualizzare i KPI e, se necessario, approvare importanti errori a 3 livelli. |
| Responsabile della distribuzione | Questo utente gestisce le operazioni di distribuzione utilizzando [!UICONTROL Cloud Manager] per eseguire distribuzioni di stage e produzione, può approvare importanti errori a 3 livelli quando necessario e ha accesso all’archivio git. |
| Sviluppatore | Questo utente sviluppa ed esegue il test del codice personalizzato dell&#39;applicazione, utilizza principalmente [!UICONTROL Cloud Manager] per visualizzare lo stato di distribuzione e ha eseguito il commit dell’accesso all’archivio git. |
| Tecnico di successo del cliente | Questo utente in genere supporta il successo dei clienti per i clienti AMS e interagisce con [!UICONTROL Cloud Manager] allo scopo di eseguire implementazioni che richiedono la supervisione di Customer Success Engineer (CSE). |
| Autore del contenuto | Questo utente generalmente non interagisce con [!UICONTROL Cloud Manager], ma può utilizzare [!UICONTROL Cloud Manager] programma wwitcher (dopo aver navigato da [!UICONTROL Experience Cloud]) per accedere ad Adobe Experience Manager (AEM). |

## Autorizzazioni utente {#user-permissions}

A ciascuno dei ruoli sono associate autorizzazioni preconfigurate specifiche. In questa tabella sono elencate le autorizzazioni disponibili e i ruoli che possono eseguirle.


| Autorizzazione | Descrizione | Business Owner (Proprietario) | Deployment Manager (Responsabile implementazione) | Program Manager (Responsabile programma) | Developer (Sviluppatore) | CSE |
|--- |--- |--- |--- |--- |--- |--- |
| Leggi applicazione | Leggi KPI del programma | x | x | x | x | x |
| Applicazione di scrittura | Configurazione o modifica del programma | x |  |  |  |  |
| Aggiungi programma | Aggiungi nuovo programma | x |  |  |  |  |
| Ambiente di lettura | Vedi i dettagli dell’ambiente | x | x | x | x | x |
| Crea esecuzione | Avvia pipeline | x | x | x |  |  |
| Lettura esecuzione | Vedi lo stato di esecuzione | x | x | x | x | x |
| Riprendi esecuzione | Può riprendere l&#39;esecuzione in pausa | x | x | x |  | x |
| Approvazione dell&#39;esecuzione della distribuzione in produzione | Fornire l’approvazione in diretta | x | x | x |  |  |
| Distribuzione della pianificazione di esecuzione in produzione | Pianificazione distribuzione produzione | x | x | x |  | x |
| Distribuzione di esecuzione in produzione | Distribuire l&#39;applicazione in produzione quando viene messa in pausa per la sorveglianza CSE |  |  |  |  | x |
| Annulla esecuzione | Annulla esecuzione corrente |  |  | x |  |  |
| Errori Gate di sostituzione della qualità dell&#39;esecuzione | Approvare importanti errori del cancello di qualità | x | x | x |  |  |
| Crea pipeline | Configurare/modificare la pipeline |  | x |  |  |  |
| Lettura pipeline | Vedi i dettagli della pipeline | x | x | x | x | x |
| Scrittura della pipeline | Configurare/modificare la pipeline. |  | x |  |  |  |
| Modifica approvazione pipeline | Consente di modificare l&#39;opzione Proprietario business |  | x |  |  |  |
| Modifica distribuzione gestita tramite pipeline | Consente la modifica dell&#39;opzione di sorveglianza CSE |  | x |  |  |  |
| Elimina pipeline | Consente l’eliminazione della pipeline |  | x |  |  |  |
| Passaggio | Vedi i risultati delle metriche di qualità dei passaggi | x | x | x | x | x |
| Genera token di accesso personale | Accedere a Git |  | x |  | x |  |

Per ulteriori informazioni su come impostare gli utenti, consulta il documento [Impostazione di utenti e ruoli.](/help/requirements/users-and-roles.md)
