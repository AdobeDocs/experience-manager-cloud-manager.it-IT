---
title: Autorizzazioni basate sul ruolo
description: Scopri le autorizzazioni preconfigurate basate sui ruoli di Cloud Manager per gestire l’accesso alle risorse cloud.
exl-id: b66533fb-db93-40e8-919d-581261fdbf24
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 99%

---


# Autorizzazioni basate sul ruolo {#role-based-permissions}

[!UICONTROL Cloud Manager] dispone di ruoli preconfigurati con le autorizzazioni appropriate. Ad esempio, uno sviluppatore sviluppa il codice e dispone dell’autorizzazione per inviare il codice all’archivio Git. Un proprietario business dispone di autorizzazioni diverse che gli consentono di definire gli indicatori prestazioni chiave (KPI, Key Performance Indicator) e di approvare le distribuzioni.

>[!NOTE]
>
>Questa documentazione descrive le autorizzazioni basate sui ruoli per Cloud Manager per Adobe Managed Services (AMS).
>
>La documentazione equivalente per AEM as a Cloud Service si trova nel documento [introduzione a Cloud Manager](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/onboarding/concepts/cloud-manager-introduction#role-based-permissions) nella documentazione di AEM as a Cloud Service.

## Ruoli utente {#user-roles}

La gestione dei ruoli per [!UICONTROL Cloud Manager] viene eseguita utilizzando [Admin Console](https://helpx.adobe.com/it/enterprise/using/admin-console.html). Qualsiasi utente di [!UICONTROL Cloud Manager] deve essere un membro dell’organizzazione IMS del cliente e disporre del contesto di prodotto di Adobe Managed Services. Le appartenenze a ruoli specifici vengono fornite aggiungendo l’utente a un profilo di prodotto [!UICONTROL Cloud Manager] in Admin Console.

Per ulteriori informazioni su come configurare gli utenti, consulta [Configurazione di utenti e ruoli](/help/requirements/users-and-roles.md).

In questa tabella sono elencati i ruoli che è possibile assegnare in Admin Console.

| Ruolo di [!UICONTROL Cloud Manager] | Descrizione |
|---|---|
| Proprietario business | Utente principale che completa la configurazione iniziale di [!UICONTROL Cloud Manager] ed è responsabile della definizione dei KPI, dell’approvazione delle implementazioni di produzione e della sostituzione di errori importanti di terzo livello, quando necessario. |
| Autore del contenuto | Utente che generalmente non interagisce con Cloud Manager, ma può utilizzare il selettore di programma di Cloud Manager (arrivando da Experience Cloud) per accedere ad Adobe Experience Manager (AEM). |
| Customer Success Engineer (CSE) | Utente che supporta principalmente il successo del cliente AMS e interagisce con [!UICONTROL Cloud Manager] per eseguire le distribuzioni. Queste distribuzioni richiedono la supervisione di un Adobe Customer Success Engineer (CSE). |
| Responsabile della distribuzione | Utente che gestisce le operazioni di distribuzione utilizzando [!UICONTROL Cloud Manager] per eseguire le distribuzioni di staging e di produzione, può approvare errori importanti di terzo livello, quando necessario, e ha accesso all’archivio Git. |
| Sviluppatore | L’utente sviluppa ed esegue il test del codice personalizzato dell’applicazione, utilizza principalmente [!UICONTROL Cloud Manager] per visualizzare lo stato di distribuzione e dispone dell’accesso ai commit dell’archivio Git. |
| Responsabile del programma | L’utente utilizza [!UICONTROL Cloud Manager] per eseguire la configurazione del team, esaminare lo stato, visualizzare i KPI e, quando necessario, approvare errori importanti di terzo livello. |

## Autorizzazioni utente {#user-permissions}

A ogni ruolo sono associate specifiche autorizzazioni preconfigurate. In questa tabella sono elencate le autorizzazioni disponibili e i ruoli che possono eseguirle.

| Autorizzazione | Descrizione | Proprietario business | Responsabile della distribuzione | Responsabile del programma | Sviluppatore | CSE |
| --- | --- | --- | --- | --- | --- | --- |
| `Read the Application` | KPI del programma di lettura | x | x | x | x | x |
| `Write Application` | Configurazione o modifica del programma | x | | | | |
| `Add Program` | Aggiungere nuovo programma | x |  |  |  |  |
| `Read Environment` | Consultare dettagli dell’ambiente | x | x | x | x | x |
| `Create Execution` | Avviare pipeline | x | x | x | | |
| `Read Execution` | Consultare lo stato di esecuzione | x | x | x | x | x |
| `Resume Execution` | Possibilità di riprendere l’esecuzione quando è in pausa | x | x | x | | x |
| `Execution Approve Deploy to Production` | Fornire l’approvazione Go-Live | x | x | x | | |
| `Execution Schedule Deploy to Production` | Pianificazione della distribuzione di produzione | x | x | x | | x |
| `Execution Deploy to Production` | Distribuire l’applicazione in produzione quando viene messa in pausa per la supervisione del CSE |  |  |  |  | x |
| `Execution Cancel` | Annullamento dell’esecuzione corrente |  |  | x |  |  |
| `Execution Override Quality Gate Failures` | Approvare importanti errori gate di qualità | x | x | x |  |  |
| `Pipeline Create` | Configurare/modificare la pipeline |  | x |  |  |  |
| `Pipeline Read` | Consultare dettagli della pipeline | x | x | x | x | x |
| `Pipeline Write` | Configurare/modificare la pipeline |  | x |  |  |  |
| P`ipeline Modify Approval` | Consente di modificare l&#39;opzione Proprietario business |  | x |  |  |  |
| `Pipeline Modify Managed Deployment` | Consente la modifica dell’opzione di supervisione del CSE |  | x |  |  |  |
| `Pipeline Delete` | Consente l’eliminazione della pipeline |  | x |  |  |  |
| `Step Read` | Consultare i risultati delle metriche di qualità del passaggio | x | x | x | x | x |
| `Generate Personal Access Token` | Accesso a Git |  | x |  | x |  |

<!-- CQDOC-22080 | Download log files  |  |  | x |  | x |  | -->

Per ulteriori informazioni su come configurare gli utenti, consulta [Configurazione di utenti e ruoli](/help/requirements/users-and-roles.md).

>[!TIP]
>
>Sono inoltre disponibili profili di autorizzazione personalizzati con autorizzazioni configurabili. Per ulteriori dettagli, consulta [Autorizzazioni personalizzate](/help/using/custom-permissions.md).
