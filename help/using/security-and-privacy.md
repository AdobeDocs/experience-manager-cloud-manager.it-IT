---
title: Protezione e privacy
seo-title: Sicurezza e privacy per AEM Cloud Manager
description: Segui questa pagina per informazioni sulla sicurezza e sulla privacy delle tue risorse (code/artefatti).
seo-description: Segui questa pagina per informazioni sulla sicurezza e sulla privacy delle tue risorse (code/artefatti) utilizzando AEM Cloud Manager.
uuid: 68 bc 2330-a 62 c -4 c 2 c -925 c-daa 6788 b 143 a
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: 67 a 54 bae -99 a 9-4405-91 e 3-9 a 0 a 8 b 3 ccc 98
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Protezione e privacy {#security-and-privacy}

[!UICONTROL Cloud Manager] dispone di ruoli preconfigurati con autorizzazioni appropriate. Ad esempio, uno sviluppatore sviluppa il codice e dispone dell&#39;autorizzazione per inviare il codice all&#39;archivio **Git**. In alternativa, un proprietario aziendale dispone di autorizzazioni diverse che consentono loro di definire gli indicatori prestazioni chiave (KPI) e di approvare le implementazioni.

## Autorizzazioni basate su ruolo {#role-based-permissions}

### Ruoli utente {#user-roles}

La gestione dei ruoli viene [!UICONTROL Cloud Manager] effettuata all&#39;interno di [Adobe Admin Console](https://helpx.adobe.com/enterprise/using/admin-console.html). Qualsiasi utente di [!UICONTROL Cloud Manager] deve essere membro dell&#39;organizzazione IMS del cliente e deve disporre del contesto prodotto Servizi gestiti Adobe. Le iscrizioni di ruolo specifiche vengono fornite aggiungendo l&#39;utente a un [!UICONTROL Cloud Manager] profilo di prodotto in Admin Console.

Per ulteriori informazioni su come configurare i ruoli, consultate [Configurazione di utenti e ruoli](setting-up-users-and-roles.md).

Nell&#39;elenco seguente sono definiti i possibili ruoli che puoi assegnare nell&#39;Admin Console.

| **[!UICONTROL Cloud Manager]Ruolo** | **Descrizione** |
|---|---|
| Proprietario aziendale | Utente principale che completa la [!UICONTROL Cloud Manager] configurazione iniziale. Responsabile della definizione dei KPI, approvazione di implementazioni di produzione e sostituzione di importanti errori a 3 gradi. |
| Program Manager | Utilizza [!UICONTROL Cloud Manager] per eseguire l&#39;impostazione del team, lo stato di revisione e i KPI. Potrebbe approvare importanti errori a 3 gradi. |
| Gestione distribuzione | Gestisce le operazioni di distribuzione. Utilizza [!UICONTROL Cloud Manager] per eseguire distribuzioni di fase e produzione. Potrebbe approvare importanti errori a 3 gradi. Può accedere all&#39;archivio Git. |
| Sviluppatore | Sviluppa e verifica il codice dell&#39;applicazione personalizzato. Viene utilizzato [!UICONTROL Cloud Manager] principalmente per visualizzare lo stato. Consente di accedere all&#39;archivio Git. |
| Customer Success Engineer | In genere supporta il successo dei clienti per i clienti AMS. Interagisce con [!UICONTROL Cloud Manager] allo scopo di eseguire distribuzioni che richiedono la supervisione di Customer Success Engineer (CSE). |
| Autore contenuto | In genere non interagisce [!UICONTROL Cloud Manager]con. Questo utente può utilizzare il [!UICONTROL Cloud Manager] commutatore programmi (da [!UICONTROL Experience Cloud]) per accedere ad Adobe Experience Manager (AEM). |

### Autorizzazioni utente {#user-permissions}

Ogni ruolo ha autorizzazioni specifiche, attività preconfigurate o autorizzazioni associate a ciascun ruolo. In questa tabella sono elencate le funzioni disponibili e i ruoli che possono eseguire la funzione.

Per ulteriori informazioni su come configurare gli utenti, consultate [Configurazione di utenti e ruoli](setting-up-users-and-roles.md).

| Autorizzazione | Descrizione | Proprietario aziendale | Gestione distribuzione | Program Manager | Sviluppatore | CSE |
|--- |--- |--- |--- |--- |--- |--- |
| Leggi applicazione | Consultate i dettagli del programma. | x | x | x | x | x |
| Scrivi applicazione | Configurare il programma (inclusi i KPI). | x |
| Ambiente di lettura | Consultate Dettagli sull&#39;ambiente. | x | x | x | x | x |
| Creazione di un&#39;esecuzione | Avvia pipeline. | x | x | x |
| Leggi esecuzione | Vedere stato di esecuzione. | x | x | x | x | x |
| Riprendi esecuzione | Può riprendere l&#39;esecuzione in pausa. | x | x | x | x |
| Esecuzione dell&#39;implementazione di Approve in produzione | Fornire Golive Approval. | x | x | x |
| Pianificazione pianificazione distribuzione in produzione | Pianificare distribuzione produzione. | x | x | x | x |
| Distribuzione in produzione | Distribuite l&#39;applicazione in produzione quando viene messa in pausa per la navigazione CSE. | x |
| Annullamento esecuzione | Annulla l&#39;esecuzione corrente. | x | x | x |
| Esecuzione di errori di qualità del gate | Approva errori di qualità importanti. | x | x | x |
| Creazione pipeline | Setup/Edit Pipeline. | x |
| Pipeline | Consultate Dettagli della pipeline. | x | x | x | x | x |
| Scrittura pipeline | Setup/Edit Pipeline. | x |
| Pipeline modifica approvazione | Consente di modificare l&#39;opzione Proprietario business. | x |
| Pipeline modifica distribuzione gestita | Consente di modificare l&#39;opzione di supervisione CSE. | x |
| Soluzione | Leggere i KPI del programma. | x | x | x | x | x |
| Scrittura della soluzione | Configurare il programma (incluso KPI)/Edit Pipeline. | x |
| Leggi passaggio | Vedi i risultati delle metriche di qualità. | x | x | x | x | x |

## Isolamento risorse {#resource-isolation}

I clienti che utilizzano le [!UICONTROL Cloud Manager] credenziali IMS devono autenticare quando tutte le autorizzazioni collegate verranno [!UICONTROL Cloud Manager] configurate e associate alla loro organizzazione IMS. Durante il processo di registrazione, il team di provisioning garantisce che l&#39;isolamento delle risorse sia applicato [!UICONTROL Cloud Manager].

## Sicurezza dei dati {#data-security}

Il codice in è [!UICONTROL Cloud Manager] cifrato in transito. Binarie che vengono anche cifrate in transito e crittografate quando memorizzate.

Ogni cliente riceve un proprio **archivio Git** e il suo codice è protetto e non condiviso con **altre organizzazioni**.

## Privacy dei dati {#data-privacy}

[!UICONTROL Cloud Manager] aderisce ai principi sulla privacy definiti da Adobe. Il codice push è sicuro per gli sviluppatori nell&#39;archivio **Git** attraverso HTTPS.

The [! L&#39;interfaccia utente DNL (interfaccia utente) per [!UICONTROL Cloud Manager]] è integrata su servizi che rispettano un framework di controllo comune definito da Adobe. [! Interfaccia utente DNL (interfaccia utente) per [!UICONTROL Cloud Manager]] utilizza servizi protetti da diversi provider cloud.
