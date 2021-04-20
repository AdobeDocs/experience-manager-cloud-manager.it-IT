---
title: Autorizzazioni basate sul ruolo
description: Segui questa pagina per scoprire di più sulle autorizzazioni basate su ruoli .
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: 67a54bae-99a9-4405-91e3-9a0a8b3ccc98
feature: User Roles
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 19%

---


# Autorizzazioni basate sul ruolo {#role-based-permissions}

[!UICONTROL Cloud Manager] dispone di ruoli preconfigurati con le autorizzazioni appropriate. Ad esempio, uno sviluppatore sviluppa il codice e dispone dell&#39;autorizzazione per inviare il codice push al **Git Repository**. In alternativa, un proprietario aziendale dispone di autorizzazioni diverse che gli consentono di definire gli indicatori prestazioni chiave (KPI, Key Performance Indicators) e di approvare le distribuzioni.

## Ruoli utente {#user-roles}

La gestione dei ruoli per [!UICONTROL Cloud Manager] viene eseguita all&#39;interno di [Adobe Admin Console](https://helpx.adobe.com/it/enterprise/using/admin-console.html). Qualsiasi utente di [!UICONTROL Cloud Manager] deve essere membro dell’organizzazione IMS del cliente e deve disporre del contesto di prodotto di Adobe Managed Services. Le appartenenze a ruoli specifici vengono fornite aggiungendo l’utente a un [!UICONTROL Cloud Manager] profilo di prodotto nell’Admin Console.

Per ulteriori informazioni su come impostare i ruoli, consulta [Impostazione di utenti e ruoli](setting-up-users-and-roles.md).

L’elenco seguente definisce i ruoli possibili che è possibile assegnare nell’Admin Console.

| **[!UICONTROL Cloud Manager]Ruolo** | **Descrizione** |
|---|---|
| Business Owner (Proprietario) | Utente principale che completa la configurazione iniziale [!UICONTROL Cloud Manager]. Responsabile della definizione dei KPI, dell’approvazione delle implementazioni di produzione e dell’override di importanti errori a 3 livelli. |
| Program Manager (Responsabile programma) | Utilizza [!UICONTROL Cloud Manager] per eseguire la configurazione del team, esaminare lo stato e visualizzare i KPI. Può approvare importanti errori a 3 livelli. |
| Deployment Manager (Responsabile implementazione) | Gestisce le operazioni di distribuzione. Utilizza [!UICONTROL Cloud Manager] per eseguire le distribuzioni di stage e produzione. Può approvare importanti errori a 3 livelli. Ha accesso all’archivio Git. |
| Developer (Sviluppatore) | Sviluppa e verifica il codice personalizzato dell’applicazione. Utilizza principalmente [!UICONTROL Cloud Manager] per visualizzare lo stato. Dispone dell’accesso al repository Git. |
| Tecnico di successo del cliente | In genere supporta il successo dei clienti per i clienti AMS. Interagisce con [!UICONTROL Cloud Manager] allo scopo di eseguire implementazioni che richiedono la supervisione di Customer Success Engineer (CSE). |
| Autore del contenuto | In genere non interagisce con [!UICONTROL Cloud Manager]. Questo utente può utilizzare il [!UICONTROL Cloud Manager] Programma Switcher (dopo aver navigato da [!UICONTROL Experience Cloud]) per accedere a Adobe Experience Manager (AEM). |

## Autorizzazioni utente {#user-permissions}

A ciascuno dei ruoli sono associate specifiche autorizzazioni e attività o autorizzazioni preconfigurate. In questa tabella sono elencate le funzioni disponibili e i ruoli che possono eseguire la funzione.

Per ulteriori informazioni su come impostare gli utenti, consulta [Configurazione di utenti e ruoli](setting-up-users-and-roles.md).

| Autorizzazione | Descrizione | Business Owner (Proprietario) | Deployment Manager (Responsabile implementazione) | Program Manager (Responsabile programma) | Developer (Sviluppatore) | CSE |
|--- |--- |--- |--- |--- |--- |--- |
| Leggi applicazione | Leggi i KPI del programma. | x | x | x | x | x |
| Applicazione di scrittura | Configurazione o modifica del programma. | x |  |  |  |  |
| Aggiungi programma | Aggiungi nuovo programma. | x |  |  |  |  |
| Ambiente di lettura | Consulta Dettagli dell’ambiente . | x | x | x | x | x |
| Crea esecuzione | Avvia pipeline. | x | x | x |  |  |
| Lettura esecuzione | Vedi lo stato di esecuzione. | x | x | x | x | x |
| Riprendi esecuzione | Può riprendere l&#39;esecuzione in pausa. | x | x | x |  | x |
| Approvazione dell&#39;esecuzione della distribuzione in produzione | Fornire l’approvazione GoLive. | x | x | x |  |  |
| Distribuzione della pianificazione di esecuzione in produzione | Pianificazione distribuzione produzione. | x | x | x |  | x |
| Distribuzione di esecuzione in produzione | Distribuisci l&#39;applicazione in produzione quando viene messo in pausa per la sorveglianza CSE. |  |  |  |  | x |
| Annulla esecuzione | Annulla l’esecuzione corrente. |  |  | x |  |  |
| Errori Gate di sostituzione della qualità dell&#39;esecuzione | Approva Errori Importanti Di Controllo Qualità. | x | x | x |  |  |
| Crea pipeline | Imposta/Modifica pipeline. |  | x |  |  |  |
| Lettura pipeline | Vedi Dettagli della pipeline. | x | x | x | x | x |
| Scrittura della pipeline | Imposta/Modifica pipeline. |  | x |  |  |  |
| Modifica approvazione pipeline | Consente di modificare l&#39;opzione Proprietario business. |  | x |  |  |  |
| Modifica distribuzione gestita tramite pipeline | Consente di modificare l&#39;opzione CSE Oversight. |  | x |  |  |  |
| Elimina pipeline | Consente di eliminare una pipeline. |  | x |  |  |  |
| Passaggio | Vedi i risultati delle metriche di qualità dei passaggi. | x | x | x | x | x |
| Genera token di accesso personale | Accedi a Git. |  | x |  | x |  |

