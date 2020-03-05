---
title: Autorizzazioni basate sul ruolo
description: Seguite questa pagina per informazioni sulle autorizzazioni basate sul ruolo.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: 67a54bae-99a9-4405-91e3-9a0a8b3ccc98
translation-type: tm+mt
source-git-commit: 157370b193c104915be063d1a4375f81839b88a2

---


# Autorizzazioni basate sul ruolo {#role-based-permissions}

[!UICONTROL Cloud Manager] dispone di ruoli preconfigurati con autorizzazioni appropriate. Ad esempio, uno sviluppatore sviluppa il codice e ha l&#39;autorizzazione per inviare il codice al repository **** Git. In alternativa, il proprietario di un&#39;azienda dispone di autorizzazioni diverse che consentono di definire gli indicatori prestazioni chiave (KPI) e di approvare le distribuzioni.

## Ruoli utente {#user-roles}

La gestione del ruolo per [!UICONTROL Cloud Manager] viene eseguita in [Adobe Admin Console](https://helpx.adobe.com/enterprise/using/admin-console.html). Qualsiasi utente di [!UICONTROL Cloud Manager] deve essere membro dell&#39;Organizzazione IMS del cliente e avere il contesto di prodotto dei servizi gestiti Adobe. Le appartenenze a ruoli specifici vengono fornite aggiungendo l&#39;utente a un profilo di [!UICONTROL Cloud Manager] prodotto nell&#39;Admin Console.

Per ulteriori informazioni su come impostare i ruoli, consulta [Impostazione di utenti e ruoli](setting-up-users-and-roles.md).

Il seguente elenco di tabella definisce i possibili ruoli che puoi assegnare nell’Admin Console.

| **[!UICONTROL Cloud Manager]Ruolo ** | **Descrizione** |
|---|---|
| Proprietario | Utente principale che completa la [!UICONTROL Cloud Manager] configurazione iniziale. Responsabile della definizione dei KPI, dell&#39;approvazione delle implementazioni di produzione e della risoluzione di importanti errori a 3 livelli. |
| Program Manager | Utilizza [!UICONTROL Cloud Manager] per eseguire la configurazione del team, esaminare lo stato e visualizzare i KPI. Può approvare importanti fallimenti a 3 livelli. |
| Gestione distribuzione | Gestisce le operazioni di distribuzione. Utilizza [!UICONTROL Cloud Manager] per eseguire distribuzioni di fase e produzione. Può approvare importanti fallimenti a 3 livelli. Ha accesso al repository Git. |
| Sviluppatore | Sviluppa e verifica il codice applicazione personalizzato. Viene utilizzato principalmente [!UICONTROL Cloud Manager] per visualizzare lo stato. Ha l&#39;accesso del commit al repository Git. |
| Customer Success Engineer | In genere supporta il successo dei clienti per i clienti AMS. Interagisce con [!UICONTROL Cloud Manager] lo scopo di eseguire distribuzioni che richiedono la supervisione di Customer Success Engineer (CSE). |
| Content Author | Generalmente non interagisce con [!UICONTROL Cloud Manager]. Questo utente può usare il [!UICONTROL Cloud Manager] programma di commutazione (dopo aver navigato da [!UICONTROL Experience Cloud]) per accedere ad Adobe Experience Manager (AEM). |

## Autorizzazioni utente {#user-permissions}

A ciascun ruolo sono associate autorizzazioni specifiche, attività preconfigurate o autorizzazioni specifiche. In questa tabella sono elencate le funzioni disponibili e i ruoli che possono eseguire la funzione.

Per ulteriori informazioni su come impostare gli utenti, consulta [Impostazione di utenti e ruoli](setting-up-users-and-roles.md).

| Autorizzazione | Descrizione | Proprietario | Gestione distribuzione | Program Manager | Sviluppatore | CSE |
|--- |--- |--- |--- |--- |--- |--- |
| Lettura applicazione | Leggi KPI del programma. | x | x | x | x | x |
| Scrivi applicazione | Installazione o modifica del programma. | x |  |  |  |  |
| Aggiungi programma | Aggiungi nuovo programma. | x |  |  |  |  |
| Ambiente di lettura | Consultate Dettagli ambiente. | x | x | x | x | x |
| Crea esecuzione | Avviate la tubazione. | x | x | x |  |  |
| Lettura esecuzione | Vedere stato di esecuzione. | x | x | x | x | x |
| Riprendi esecuzione | Può riprendere l&#39;esecuzione in pausa. | x | x | x |  | x |
| Approvazione esecuzione distribuzione in produzione | Fornisci l&#39;approvazione GoLive. | x | x | x |  |  |
| Programma di esecuzione Distribuisci in produzione | Pianificazione distribuzione produzione. | x | x | x |  | x |
| Implementazione in produzione | Implementare l&#39;applicazione in produzione quando viene messa in pausa per CSE Oversight. |  |  |  |  | x |
| Annullamento esecuzione | Annulla esecuzione corrente. | x | x | x |  |  |
| Errori Gate Di Sostituzione Dell&#39;Esecuzione | Approvare Importanti Errori Di Controllo Della Qualità. | x | x | x |  |  |
| Crea tubazione | Impostazione/Modifica tubazione. |  | x |  |  |  |
| Lettura pipeline | Consultate Dettagli sulla tubazione. | x | x | x | x | x |
| Scrittura pipeline | Impostazione/Modifica tubazione. |  | x |  |  |  |
| Approvazione modifica pipeline | Consente di modificare l&#39;opzione Proprietario business. |  | x |  |  |  |
| Distribuzione gestita tramite modifica pipeline | Consente di modificare l&#39;opzione CSE Oversight. |  | x |  |  |  |
| Lettura passaggio | Vedi i risultati delle metriche sulla qualità dei passaggi. | x | x | x | x | x |
| Genera token di accesso personale | Git di accesso. |  | x |  | x |  |
