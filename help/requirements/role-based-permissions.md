---
title: Autorizzazioni basate sul ruolo
description: Scopri le autorizzazioni preconfigurate basate sui ruoli di Cloud Manager per gestire l’accesso alle risorse cloud.
exl-id: b66533fb-db93-40e8-919d-581261fdbf24
source-git-commit: 522e5fbc650a8159602eb1aeaf42d64f4e23e8b4
workflow-type: ht
source-wordcount: '539'
ht-degree: 100%

---


# Autorizzazioni basate sul ruolo {#role-based-permissions}

[!UICONTROL Cloud Manager] dispone di ruoli preconfigurati con le autorizzazioni appropriate. Ad esempio, uno sviluppatore sviluppa il codice e dispone dell’autorizzazione per inviare il codice all’archivio Git. Un proprietario business dispone di autorizzazioni diverse che gli consentono di definire gli indicatori prestazioni chiave (KPI, Key Performance Indicator) e di approvare le distribuzioni.

## Ruoli utente {#user-roles}

La gestione dei ruoli per [!UICONTROL Cloud Manager] viene eseguita utilizzando [Admin Console.](https://helpx.adobe.com/it/enterprise/using/admin-console.html) Qualsiasi utente di [!UICONTROL Cloud Manager] deve essere membro dell’organizzazione IMS del cliente e disporre del contesto di prodotto di Adobe Managed Services. Le appartenenze a ruoli specifici vengono fornite aggiungendo l’utente a un profilo di prodotto [!UICONTROL Cloud Manager] nell’Admin Console.

Per ulteriori informazioni su come configurare i ruoli, consulta il documento [Configurazione di utenti e ruoli.](/help/requirements/users-and-roles.md)

In questa tabella sono elencati i ruoli che è possibile assegnare nell’Admin Console.

| [!UICONTROL Cloud Manager] Ruolo | Descrizione |
|---|---|
| Proprietario business | Questo è l’utente principale che completa la configurazione iniziale di [!UICONTROL Cloud Manager] ed è responsabile della definizione dei KPI, dell’approvazione delle implementazioni di produzione e della sostituzione di errori importanti a 3 livelli quando necessario. |
| Responsabile del programma | Questo utente utilizza [!UICONTROL Cloud Manager] per eseguire la configurazione del team, esaminare lo stato, visualizzare i KPI e, se necessario, approvare importanti errori a 3 livelli. |
| Responsabile della distribuzione | Questo utente gestisce le operazioni di distribuzione utilizzando [!UICONTROL Cloud Manager] per eseguire le distribuzioni dello staging e della produzione, può approvare importanti errori a 3 livelli quando necessario e ha accesso all’archivio Git. |
| Sviluppatore | Questo utente sviluppa ed esegue il test del codice personalizzato dell’applicazione, utilizza principalmente [!UICONTROL Cloud Manager] per visualizzare lo stato di distribuzione e ha l’accesso ai commit dell’archivio Git. |
| Customer Success Engineer (CSE) | Questo utente in genere supporta il successo dei clienti per i clienti AMS e interagisce con [!UICONTROL Cloud Manager] allo scopo di eseguire implementazioni che richiedono la supervisione del Customer Success Engineer (CSE). |
| Autore del contenuto | Questo utente generalmente non interagisce con [!UICONTROL Cloud Manager], ma può utilizzare il selettore di programma di [!UICONTROL Cloud Manager] (arrivando da [!UICONTROL Experience Cloud]) per accedere ad Adobe Experience Manager (AEM). |

## Autorizzazioni utente {#user-permissions}

A ciascuno dei ruoli sono associate autorizzazioni preconfigurate specifiche. In questa tabella sono elencate le autorizzazioni disponibili e i ruoli che possono eseguirle.


| Autorizzazione | Descrizione | Proprietario business | Deployment Manager (Responsabile implementazione) | Program Manager (Responsabile programma) | Developer (Sviluppatore) | CSE |
|--- |--- |--- |--- |--- |--- |--- |
| Applicazione di lettura | KPI del programma di lettura | x | x | x | x | x |
| Applicazione di scrittura | Configurazione o modifica del programma | x |  |  |  |  |
| Aggiungere programma | Aggiungere nuovo programma | x |  |  |  |  |
| Ambiente di lettura | Consultare dettagli dell’ambiente | x | x | x | x | x |
| Creare esecuzione | Avviare pipeline | x | x | x |  |  |
| Esecuzione di lettura | Consultare lo stato di esecuzione | x | x | x | x | x |
| Riprendere esecuzione | Può riprendere l’esecuzione quando è in pausa | x | x | x |  | x |
| Approvare l’esecuzione della distribuzione alla produzione | Fornire l’approvazione Go-Live | x | x | x |  |  |
| Esecuzione della pianificazione della distribuzione alla produzione | Pianificazione della distribuzione di produzione | x | x | x |  | x |
| Esecuzione della distribuzione alla produzione | Distribuire l’applicazione in produzione quando viene messa in pausa per la supervisione del CSE |  |  |  |  | x |
| Esecuzione Annulla | Annullare esecuzione corrente |  |  | x |  |  |
| Esecuzione sostituzione errori gate di qualità | Approvare importanti errori gate di qualità | x | x | x |  |  |
| Creare pipeline | Configurare/modificare la pipeline |  | x |  |  |  |
| Lettura pipeline | Consultare dettagli della pipeline | x | x | x | x | x |
| Scrittura della pipeline | Configurare/modificare la pipeline. |  | x |  |  |  |
| Modificare approvazione pipeline | Consente di modificare l&#39;opzione Proprietario business |  | x |  |  |  |
| Distribuzione gestita della pipeline modificata | Consente la modifica dell’opzione di supervisione del CSE |  | x |  |  |  |
| Elimina pipeline | Consente l’eliminazione della pipeline |  | x |  |  |  |
| Leggi Passaggio | Consultare i risultati delle metriche di qualità del passaggio | x | x | x | x | x |
| Generare token di accesso personale | Accesso a Git |  | x |  | x |  |

Per ulteriori informazioni su come configurare gli utenti, consulta il documento [Configurazione di utenti e ruoli.](/help/requirements/users-and-roles.md)
