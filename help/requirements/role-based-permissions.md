---
title: Autorizzazioni basate sul ruolo
description: Scopri le autorizzazioni preconfigurate basate sui ruoli di Cloud Manager per gestire l’accesso alle risorse cloud.
exl-id: b66533fb-db93-40e8-919d-581261fdbf24
source-git-commit: 11a6a53d8cbfb689810a9a8e7d82293a49863084
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 51%

---


# Autorizzazioni basate sul ruolo {#role-based-permissions}

[!UICONTROL Cloud Manager] dispone di ruoli preconfigurati con le autorizzazioni appropriate. Ad esempio, uno sviluppatore sviluppa il codice e dispone dell’autorizzazione per inviare il codice all’archivio Git. Un proprietario business dispone di autorizzazioni diverse che gli consentono di definire gli indicatori prestazioni chiave (KPI, Key Performance Indicator) e di approvare le distribuzioni.

>[!NOTE]
>
>Questa documentazione descrive le autorizzazioni basate sui ruoli per Cloud Manager per Adobe Managed Services (AMS).
>
>La documentazione equivalente per AEM as a Cloud Service si trova nel documento [introduzione a Cloud Manager](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/concepts/cloud-manager-introduction#role-based-permissions) nella documentazione di AEM as a Cloud Service.

## Ruoli utente {#user-roles}

La gestione dei ruoli per [!UICONTROL Cloud Manager] viene eseguita utilizzando [Admin Console](https://helpx.adobe.com/it/enterprise/using/admin-console.html). Qualsiasi utente di [!UICONTROL Cloud Manager] deve essere membro dell&#39;organizzazione IMS del cliente e disporre del contesto di prodotto Managed Services di Adobe. Le appartenenze a ruoli specifici vengono fornite aggiungendo l’utente a un profilo di prodotto [!UICONTROL Cloud Manager] nell’Admin Console.

Per ulteriori informazioni sulla configurazione dei ruoli, vedere [Configurazione di utenti e ruoli](/help/requirements/users-and-roles.md).

Nella tabella seguente sono elencati i ruoli che è possibile assegnare nell&#39;Admin Console.

| [!UICONTROL Ruolo Cloud Manager] | Descrizione |
|---|---|
| Proprietario business | Utente principale che completa la configurazione iniziale di [!UICONTROL Cloud Manager] ed è responsabile della definizione dei KPI, dell&#39;approvazione delle distribuzioni di produzione e della sostituzione di errori importanti di terzo livello quando necessario. |
| Autore del contenuto | L’utente generalmente non interagisce con Cloud Manager, ma può utilizzare il selettore di programma Cloud Manager (arrivando da Experience Cloud) per accedere a Adobe Experience Manager (AEM). |
| Customer Success Engineer (CSE) | L&#39;utente supporta principalmente il successo del cliente AMS e interagisce con [!UICONTROL Cloud Manager] per eseguire le distribuzioni. Queste implementazioni richiedono la supervisione di un Adobe Customer Success Engineer (CSE). |
| Responsabile della distribuzione | L&#39;utente gestisce le operazioni di distribuzione utilizzando [!UICONTROL Cloud Manager] per eseguire le distribuzioni dello staging e della produzione, può approvare errori importanti di terzo livello quando necessario e ha accesso all&#39;archivio Git. |
| Sviluppatore | L&#39;utente sviluppa ed esegue il test del codice personalizzato dell&#39;applicazione, utilizza principalmente [!UICONTROL Cloud Manager] per visualizzare lo stato di distribuzione e ha l&#39;accesso ai commit dell&#39;archivio Git. |
| Responsabile del programma | L&#39;utente utilizza [!UICONTROL Cloud Manager] per eseguire la configurazione del team, esaminare lo stato, visualizzare i KPI e, se necessario, approvare errori importanti di terzo livello. |

## Autorizzazioni utente {#user-permissions}

A ciascuno dei ruoli sono associate autorizzazioni preconfigurate specifiche. Nella tabella seguente sono elencate le autorizzazioni disponibili e i ruoli autorizzati ad eseguirle.

| Autorizzazione | Descrizione | Proprietario business | Responsabile dell’implementazione | Program Manager (Responsabile programma) | Sviluppatore | CSE |
| --- | --- | --- | --- | --- | --- | --- |
| Leggi l&#39;applicazione | KPI del programma di lettura | x | x | x | x | x |
| Applicazione di scrittura | Configurazione o modifica del programma | x | | | | |
| Aggiungere programma | Aggiungere nuovo programma | x | | | | |
| Ambiente di lettura | Consultare dettagli dell’ambiente | x | x | x | x | x |
| Creare esecuzione | Avviare pipeline | x | x | x | | |
| Esecuzione di lettura | Consultare lo stato di esecuzione | x | x | x | x | x |
| Riprendere esecuzione | Possibilità di riprendere l’esecuzione quando è in pausa | x | x | x | | x |
| Approvare l’esecuzione della distribuzione alla produzione | Fornire l’approvazione Go-Live | x | x | x | | |
| Esecuzione della pianificazione della distribuzione alla produzione | Pianificazione della distribuzione di produzione | x | x | x | | x |
| Esecuzione della distribuzione alla produzione | Distribuire l’applicazione in produzione quando viene messa in pausa per la supervisione del CSE | | | | | x |
| Annullamento dell’esecuzione | Annullamento dell’esecuzione corrente | | | x | | |
| Esecuzione sostituzione errori gate di qualità | Approvare importanti errori gate di qualità | x | x | x | | |
| Creare pipeline | Configurare/modificare la pipeline | | x | | | |
| Lettura pipeline | Consultare dettagli della pipeline | x | x | x | x | x |
| Scrittura della pipeline | Configurare/modificare la pipeline | | x | | | |
| Modificare approvazione pipeline | Consente di modificare l&#39;opzione Proprietario business | | x | | | |
| Distribuzione gestita della pipeline modificata | Consente la modifica dell’opzione di supervisione del CSE | | x | | | |
| Elimina pipeline | Consente l’eliminazione della pipeline | | x | | | |
| Leggi Passaggio | Consultare i risultati delle metriche di qualità del passaggio | x | x | x | x | x |
| Generazione del token di accesso personale | Accesso a Git | | x | | x | |

Per ulteriori informazioni sulla configurazione degli utenti, vedere [Configurazione di utenti e ruoli](/help/requirements/users-and-roles.md).

>[!TIP]
>
>Sono inoltre disponibili profili di autorizzazione personalizzati con autorizzazioni configurabili. Per ulteriori dettagli, vedi [Autorizzazioni personalizzate](/help/using/custom-permissions.md).
