---
title: Aggiungere utenti e ruoli
description: Scopri come utilizzare l’Admin Console per aggiungere utenti e ruoli e creare profili.
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: dd96d773ea3e6b9c45886fe41b28d3dd70cb8a61
workflow-type: tm+mt
source-wordcount: '774'
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

| Ruolo di [!UICONTROL Cloud Manager] | Descrizione |
|--- |--- |
| Proprietario business | Questo utente è responsabile della definizione dei KPI, dell’approvazione delle implementazioni di produzione e della sostituzione di errori importanti di terzo livello quando necessario. |
| Responsabile del programma | Questo utente utilizza [!UICONTROL Cloud Manager] per eseguire la configurazione del team, esaminare lo stato, visualizzare i KPI e, se necessario, può approvare errori importanti di terzo livello. |
| Responsabile della distribuzione | Questo utente gestisce le operazioni di distribuzione e utilizza [!UICONTROL Cloud Manager] per eseguire distribuzioni di staging/produzione, modificare le pipeline CI/CD, approvare errori importanti di terzo livello, se necessario, e può accedere all’archivio Git. |
| Sviluppatore | Questo utente sviluppa ed esegue il test del codice personalizzato dell’applicazione, utilizza principalmente [!UICONTROL Cloud Manager] per visualizzare lo stato di distribuzione e può accedere all’archivio Git per commit di codice. |
| Customer Success Engineer (CSE) | Questo utente in genere supporta il successo dei clienti AMS e interagisce con [!UICONTROL Cloud Manager] al fine di eseguire distribuzioni che richiedono la supervisione del CSE. |
| Autore del contenuto | Questo utente generalmente non interagisce con [!UICONTROL Cloud Manager] ma può utilizzare il selettore di programma [!UICONTROL Cloud Manager] per accedere ad AEM. |

>[!NOTE]
>
>L’utente di tipo Sviluppatore nell’Admin Console non è correlato al ruolo Sviluppatore in [!UICONTROL Cloud Manager].

## Utilizzo di Admin Console per creare un profilo {#using-admin-console-to-create-a-profile}

[!UICONTROL I ruoli di Cloud Manager] vengono gestiti dall’Admin Console. Le appartenenze a ruoli specifici vengono fornite aggiungendo l’utente a un profilo di prodotto [!UICONTROL Cloud Manager].

L’Admin Console è una posizione centrale per la gestione delle assegnazioni Adobe in tutta l’organizzazione. Per ulteriori informazioni su Adobe Admin Console, consulta la documentazione di [Admin Console.](https://helpx.adobe.com/it/enterprise/using/admin-console.html)

Per fornire le autorizzazioni appropriate basate sul ruolo agli utenti di [!UICONTROL Cloud Manager], un amministratore dell’organizzazione del cliente deve creare nuovi profili di prodotto nel contesto del prodotto [!UICONTROL AEM Managed Services] corrispondenti a ciascuno dei quattro ruoli di [!UICONTROL Cloud Manager]:

* Business Owner (Proprietario)
* Responsabile dell’implementazione
* Sviluppatore
* Responsabile del programma

Puoi creare o aggiungere utenti/gruppi a questi profili di prodotto con l’Admin Console.

1. Accedi ad Admin Console all’indirizzo [`https://adminconsole.adobe.com`.](https://adminconsole.adobe.com)

1. Fai clic sulla scheda **Panoramica**, quindi sul prodotto che desideri modificare nella scheda **Prodotti e servizi**. Se non è presente nell’elenco, utilizza la scheda **Prodotti** per individuare il prodotto e fare clic su di esso.

   ![Scheda panoramica di Admin Console](/help/assets/admin-console-overview.png)

1. Sulla scheda **Prodotti**, fai clic sull’ambiente per il quale desideri aggiungere utenti/gruppi ai profili di prodotto.

   ![Scheda Prodotti di Admin Console](/help/assets/admin-console-product.png)

1. Sulla scheda **Profilo prodotto** del prodotto, fai clic su **Nuovo profilo** per aggiungere un nuovo profilo.

   ![Nuovo profilo](/help/assets/admin-console-product-profiles.png)

1. Fornisci le informazioni per configurare un nuovo ruolo per [!UICONTROL Cloud Manager].

   * **Nome profilo**: il **Nome profilo** può essere qualsiasi cosa, anche se per evitare confusione si consiglia di utilizzare i valori nella colonna **Nome profilo consigliato**.
   * **Nome visualizzato**: il **Nome visualizzato** deve essere il valore tecnico definito da [!UICONTROL Cloud Manager] (vedi la tabella seguente).
   * **Gruppo di autorizzazione**: puoi scegliere un gruppo di autorizzazione per il profilo (non sempre disponibile).

   ![Crea un nuovo profilo](/help/assets/screen_shot_2018-05-04at171819.png)

   | Ruolo | Nome visualizzato (obbligatorio) | Nome profilo consigliato |
   |---|---|---|
   | Proprietario business | `CM_BUSINESS_OWNER_ROLE_PROFILE` | [!UICONTROL Cloud Manager]: ruolo Proprietario business |
   | Responsabile della distribuzione | `CM_DEPLOYMENT_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Ruolo Responsabile della distribuzione |
   | Sviluppatore | `CM_DEVELOPER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Ruolo Sviluppatore |
   | Responsabile del programma | `CM_PROGRAM_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Ruolo Responsabile del programma |


1. Fai clic su **Fine** per salvare il nuovo profilo.

## Assegna profili a Utenti o Gruppi di utenti {#assign-profiles}

Dopo aver creato i profili di prodotto, puoi assegnare loro utenti o gruppi di utenti.

1. Accedi ad Admin Console all’indirizzo [`https://adminconsole.adobe.com`.](https://adminconsole.adobe.com)

1. Nell’Admin Console, scegli la scheda **Utenti**.

   ![Scheda Utenti](/help/assets/admin-console-users.png)

1. Fai clic su **Utenti** nel pannello di navigazione a sinistra, quindi fai clic su un utente per modificarlo.

1. Fai clic sul pulsante con i puntini di sospensione nella sezione **Prodotti** e seleziona **Modifica**.

   ![Modifica utente](/help/assets/admin-console-edit-user.png)

1. Nella finestra di dialogo **Modifica prodotti e gruppi di utenti**, fai clic sul pulsante più e seleziona i profili da assegnare all’utente.

   * Se l’utente è già assegnato ai ruoli, il pulsante più sarà un pulsante di modifica (a forma di matita), ma funziona allo stesso modo.

   ![Modifica prodotti e gruppi di utenti](/help/assets/admin-console-edit-products-and-user-groups.png)

1. Fai clic su **Salva** per salvare i profili dell’utente.

Ripeti gli stessi passaggi per assegnare profili a gruppi di utenti, ma seleziona **Gruppi di utenti** dal pannello di navigazione a sinistra nella scheda **Utenti**. Fai clic su un gruppo di utenti e seleziona la scheda **Profili di prodotto assegnati** e fai clic su **Assegna profilo di prodotto** per assegnare i profili.

![Assegna profili al gruppo](/help/assets/admin-console-edit-user-groups.png)
