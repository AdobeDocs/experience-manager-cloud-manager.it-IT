---
title: Aggiungere utenti e ruoli
description: Scopri come utilizzare l’Admin Console per aggiungere utenti e ruoli e creare profili.
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: b0dbb602253939464ff034941ffbad84b7df77df
workflow-type: ht
source-wordcount: '536'
ht-degree: 100%

---


# Aggiungere utenti e ruoli {#add-users-and-roles}

Molte funzioni in [!UICONTROL Cloud Manager] richiedono autorizzazioni specifiche da utilizzare. Per esempio, solo alcuni utenti possono impostare gli indicatori prestazioni chiave (KPI, Key Performance Indicator) per un programma. Queste autorizzazioni sono raggruppate in modo logico in ruoli.

[!UICONTROL Cloud Manager] attualmente definisce quattro ruoli per gli utenti che determinano la disponibilità di funzioni specifiche:

* Proprietario business
* Responsabile del programma
* Responsabile della distribuzione
* Sviluppatore

>[!NOTE]
>
>Per utilizzare [!UICONTROL Cloud Manager], è necessario disporre di un contesto di prodotto Adobe ID e Adobe Managed Services.

## Definizioni dei ruoli {#role-definitions}

In questa tabella vengono riepilogati i ruoli.

| [!UICONTROL Cloud Manager] Ruolo | Descrizione |
|--- |--- |
| Proprietario business | Questo utente è responsabile della definizione dei KPI, dell’approvazione delle implementazioni di produzione e della sostituzione di errori importanti di terzo livello quando necessario. |
| Responsabile del programma | Questo utente utilizza [!UICONTROL Cloud Manager] per eseguire la configurazione del team, esaminare lo stato, visualizzare i KPI e, se necessario, può approvare errori importanti di terzo livello. |
| Responsabile della distribuzione | Questo utente gestisce le operazioni di distribuzione e utilizza [!UICONTROL Cloud Manager] per eseguire distribuzioni di staging/produzione, modificare le pipeline CI/CD, approvare errori importanti di terzo livello quando necessario e può accedere all’archivio Git. |
| Sviluppatore | Questo utente sviluppa ed esegue il test del codice personalizzato dell’applicazione, utilizza principalmente [!UICONTROL Cloud Manager] per visualizzare lo stato di distribuzione e può accedere all’archivio Git per commit di codice. |
| Customer Success Engineer (CSE) | Questo utente in genere supporta il successo dei clienti AMS e interagisce con il [!UICONTROL Cloud Manager] al fine di eseguire distribuzioni che richiedono la supervisione del CSE. |
| Autore del contenuto | Questo utente generalmente non interagisce con [!UICONTROL Cloud Manager] ma può utilizzare il selettore di programma [!UICONTROL Cloud Manager] per accedere ad AEM. |

>[!NOTE]
>
>L’utente di tipo Sviluppatore nell’Admin Console non è correlata al ruolo Sviluppatore in [!UICONTROL Cloud Manager].

## Utilizzo di Admin Console per creare un profilo {#using-admin-console-to-create-a-profile}

I ruoli [!UICONTROL Cloud Manager] vengono gestiti dall’Admin Console. Le appartenenze a ruoli specifici vengono fornite aggiungendo l’utente a un profilo di prodotto [!UICONTROL Cloud Manager].

L’Admin Console è una posizione centrale per la gestione delle assegnazioni Adobe in tutta l’organizzazione. Per ulteriori informazioni su Adobe Admin Console, consulta la documentazione di [Admin Console.](https://helpx.adobe.com/it/enterprise/using/admin-console.html)

>[!NOTE]
>
>Per accedere ad Admin Console e configurare il team (utenti e ruoli), visita [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com).

Per fornire le autorizzazioni appropriate basate sul ruolo agli utenti [!UICONTROL Cloud Manager], un amministratore dell’organizzazione del cliente deve creare nuovi profili di prodotto nel contesto del prodotto [!UICONTROL AEM Managed Services] corrispondenti a ciascuno dei quattro ruoli [!UICONTROL Cloud Manager]:

* Business Owner (Proprietario)
* Responsabile della distribuzione
* Sviluppatore
* Responsabile del programma

Puoi creare o aggiungere utenti/gruppi a questi profili di prodotto con l’Admin Console.

1. Accedi all’Admin Console e fai clic su **Nuovo profilo** per aggiungere un nuovo profilo.

   ![Nuovo profilo](/help/assets/admin_console_roles-1.png)

1. Fornisci le informazioni necessarie per impostare un nuovo ruolo per [!UICONTROL Cloud Manager].

   * **Nome profilo**
   * **Nome visualizzato**
   * **Gruppo di autorizzazioni**

1. Fai clic su **Fine** per completare il passaggio di creazione del profilo.

Quando si creano questi profili di prodotto, il **Nome visualizzato** deve essere il valore tecnico definito da [!UICONTROL Cloud Manager] (vedi tabella seguente). Il **Nome profilo** può essere qualsiasi cosa, anche se per evitare confusione si consiglia di utilizzare i valori nella colonna **Nome profilo consigliato**. A questo proposito, durante la creazione del profilo di prodotto, deseleziona **Come nome profilo** e specifica il valore corrispondente come **Nome visualizzato**.

| **Ruolo** | **Nome visualizzato (obbligatorio)** | **Nome profilo consigliato** |
|---|---|---|
| Proprietario business | `CM_BUSINESS_OWNER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Ruolo Proprietario business |
| Responsabile della distribuzione | `CM_DEPLOYMENT_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Ruolo Responsabile della distribuzione |
| Sviluppatore | `CM_DEVELOPER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Ruolo Sviluppatore |
| Responsabile del programma | `CM_PROGRAM_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Ruolo Responsabile del programma |

![Crea un nuovo profilo](/help/assets/screen_shot_2018-05-04at171819.png)

Una volta creato il profilo di prodotto, puoi aggiungervi utenti (o gruppi).

![Modifica utente](/help/assets/image2018-4-9_15-19-26.png)

![Gruppi utenti](/help/assets/image2018-4-9_15-16-47.png)
