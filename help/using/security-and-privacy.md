---
title: Sicurezza e privacy
seo-title: Sicurezza e privacy per AEM Cloud Manager
description: Segui questa pagina per saperne di più sulla sicurezza e la privacy delle tue risorse (codice/artifact).
seo-description: Segui questa pagina per saperne di più sulla sicurezza e la privacy delle tue risorse (codice/artifact) tramite AEM Cloud Manager.
uuid: 68bc2330-a62c-4c2c-925c-data6788b143a
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduzione
discoiquuid: 67a54bae-99a9-4405-91e3-9a0a8b3ccc98
translation-type: tm+mt
source-git-commit: 949d3cf0239a02875ba4ad1888e081f104dec2e2

---


# Sicurezza e privacy {#security-and-privacy}

[!UICONTROL Cloud Manager] dispone di ruoli preconfigurati con autorizzazioni appropriate. Ad esempio, uno sviluppatore sviluppa il codice e ha l'autorizzazione per inviare il codice al repository **** Git. In alternativa, il proprietario di un'azienda dispone di autorizzazioni diverse che consentono di definire gli indicatori prestazioni chiave (KPI, Key Performance Indicators) e di approvare le distribuzioni.

## Autorizzazioni basate sul ruolo {#role-based-permissions}

### Ruoli utente {#user-roles}

La gestione del ruolo per [!UICONTROL Cloud Manager] viene eseguita in [Adobe Admin Console](https://helpx.adobe.com/enterprise/using/admin-console.html). Qualsiasi utente di [!UICONTROL Cloud Manager] deve essere membro dell'Organizzazione IMS del cliente e avere il contesto di prodotto dei servizi gestiti Adobe. Le appartenenze a ruoli specifici vengono fornite aggiungendo l'utente a un profilo di [!UICONTROL Cloud Manager] prodotto nell'Admin Console.

Per ulteriori informazioni su come impostare i ruoli, consulta [Impostazione di utenti e ruoli](setting-up-users-and-roles.md).

Il seguente elenco di tabella definisce i possibili ruoli che puoi assegnare nell’Admin Console.

| **[!UICONTROL Cloud Manager]Ruolo** | **Descrizione** |
|---|---|
| Proprietario | Utente principale che completa la [!UICONTROL Cloud Manager] configurazione iniziale. Responsabile della definizione dei KPI, dell'approvazione delle implementazioni di produzione e della risoluzione di importanti errori a 3 livelli. |
| Program Manager | Utilizza [!UICONTROL Cloud Manager] per eseguire la configurazione del team, esaminare lo stato e visualizzare i KPI. Può approvare importanti fallimenti a 3 livelli. |
| Gestione distribuzione | Gestisce le operazioni di distribuzione. Utilizza [!UICONTROL Cloud Manager] per eseguire distribuzioni di fase e produzione. Può approvare importanti fallimenti a 3 livelli. Ha accesso al repository Git. |
| Sviluppatore | Sviluppa e verifica il codice applicazione personalizzato. Viene utilizzato principalmente [!UICONTROL Cloud Manager] per visualizzare lo stato. Ha l'accesso del commit al repository Git. |
| Customer Success Engineer | In genere supporta il successo dei clienti per i clienti AMS. Interagisce con [!UICONTROL Cloud Manager] lo scopo di eseguire distribuzioni che richiedono la supervisione di Customer Success Engineer (CSE). |
| Content Author | Generalmente non interagisce con [!UICONTROL Cloud Manager]. Questo utente può usare il [!UICONTROL Cloud Manager] programma di commutazione (dopo aver navigato da [!UICONTROL Experience Cloud]) per accedere ad Adobe Experience Manager (AEM). |

### Autorizzazioni utente {#user-permissions}

A ciascun ruolo sono associate autorizzazioni specifiche, attività preconfigurate o autorizzazioni specifiche. In questa tabella sono elencate le funzioni disponibili e i ruoli che possono eseguire la funzione.

Per ulteriori informazioni su come impostare gli utenti, consulta [Impostazione di utenti e ruoli](setting-up-users-and-roles.md).

| Autorizzazione | Descrizione | Proprietario | Gestione distribuzione | Program Manager | Sviluppatore | CSE |
|--- |--- |--- |--- |--- |--- |--- |
| Lettura applicazione | Vedere i dettagli del programma. | x | x | x | x | x |
| Scrivi applicazione | Configurare il programma (inclusi KPI). | x |  |  |  |  |
| Ambiente di lettura | Consultate Dettagli ambiente. | x | x | x | x | x |
| Crea esecuzione | Avviate la tubazione. | x | x | x |  |  |
| Lettura esecuzione | Vedere stato di esecuzione. | x | x | x | x | x |
| Riprendi esecuzione | Può riprendere l'esecuzione in pausa. | x | x | x |  | x |
| Approvazione esecuzione distribuzione in produzione | Fornisci l'approvazione GoLive. | x | x | x |  |  |
| Programma di esecuzione Distribuisci in produzione | Pianificazione distribuzione produzione. | x | x | x |  | x |
| Implementazione in produzione | Implementare l'applicazione in produzione quando viene messa in pausa per CSE Oversight. |  |  |  |  | x |
| Annullamento esecuzione | Annulla esecuzione corrente. | x | x | x |  |  |
| Errori Gate Di Sostituzione Dell'Esecuzione | Approvare Importanti Errori Di Controllo Della Qualità. | x | x | x |  |  |
| Crea tubazione | Impostazione/Modifica tubazione. |  | x |  |  |  |
| Lettura pipeline | Consultate Dettagli sulla tubazione. | x | x | x | x | x |
| Scrittura pipeline | Impostazione/Modifica tubazione. |  | x |  |  |  |
| Approvazione modifica pipeline | Consente di modificare l'opzione Proprietario business. |  | x |  |  |  |
| Distribuzione gestita tramite modifica pipeline | Consente di modificare l'opzione CSE Oversight. |  | x |  |  |  |
| Soluzione | Leggere i KPI del programma. | x | x | x | x | x |
| Soluzione Write | Configurare la configurazione del programma (inclusi i KPI) / Modifica della tubazione. | x |  |  |  |  |
| Lettura passaggio | Vedi i risultati delle metriche sulla qualità dei passaggi. | x | x | x | x | x |

## Isolamento risorse {#resource-isolation}

I clienti che utilizzano [!UICONTROL Cloud Manager] avranno bisogno delle credenziali IMS per l'autenticazione, in quanto tutte le autorizzazioni associate [!UICONTROL Cloud Manager] verranno configurate e associate alla propria organizzazione IMS. Durante il processo di registrazione, il team di provisioning garantisce l'applicazione dell'isolamento delle risorse in [!UICONTROL Cloud Manager].

## Protezione dei dati {#data-security}

Il codice in [!UICONTROL Cloud Manager] è crittografato in transito. I binari generati da Coud Manager vengono inoltre crittografati in transito e cifrati al momento della memorizzazione.

Ogni cliente ottiene il proprio **Git Repository** e il suo codice è sicuro e non condiviso con altre **organizzazioni**.

## Privacy dei dati {#data-privacy}

[!UICONTROL Cloud Manager] aderisce ai principi di privacy definiti da Adobe. Gli sviluppatori inviano il codice in modo sicuro nell'archivio **Git** tramite HTTPS.

L'interfaccia utente di [!DNL [!UICONTROL Cloud Manager]] è basata su servizi conformi a un framework di controllo comune definito da Adobe. L'interfaccia utente di [!DNL (UI) per [!UICONTROL Cloud Manager]] utilizza i servizi protetti di diversi fornitori di cloud.
