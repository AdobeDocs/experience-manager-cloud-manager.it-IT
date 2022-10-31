---
title: Aggiungere utenti e ruoli
description: Scopri come utilizzare l’Admin Console per aggiungere utenti e ruoli e creare profili.
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: dd96d773ea3e6b9c45886fe41b28d3dd70cb8a61
workflow-type: tm+mt
source-wordcount: '780'
ht-degree: 22%

---


# Aggiungere utenti e ruoli {#add-users-and-roles}

Molte funzioni in [!UICONTROL Cloud Manager] richiedere autorizzazioni specifiche da utilizzare. Per esempio, solo alcuni utenti possono impostare gli indicatori prestazioni chiave (KPI, Key Performance Indicator) per un programma. Queste autorizzazioni sono raggruppate in modo logico in ruoli.

[!UICONTROL Cloud Manager] attualmente definisce quattro ruoli per gli utenti che determinano la disponibilità di funzionalità specifiche:

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
| Responsabile del programma | Questo utente utilizza [!UICONTROL Cloud Manager] per eseguire la configurazione del team, esaminare lo stato, visualizzare i KPI e approvare importanti errori a 3 livelli quando necessario. |
| Responsabile della distribuzione | Questo utente gestisce le operazioni di distribuzione e utilizza [!UICONTROL Cloud Manager] per eseguire distribuzioni di staging/produzione, modifica le pipeline CI/CD, approva importanti errori a 3 livelli quando necessario e può accedere all’archivio git. |
| Sviluppatore | Questo utente sviluppa e verifica il codice personalizzato dell&#39;applicazione e utilizza principalmente [!UICONTROL Cloud Manager] per visualizzare lo stato di distribuzione e accedere all’archivio git per le conferme di codice. |
| Customer Success Engineer (CSE) | Questo utente in genere supporta il successo dei clienti per i clienti AMS e interagisce con [!UICONTROL Cloud Manager] al fine di eseguire distribuzioni che richiedono la sorveglianza CSE. |
| Autore del contenuto | Questo utente generalmente non interagisce con [!UICONTROL Cloud Manager] ma può utilizzare [!UICONTROL Cloud Manager] per accedere a AEM. |

>[!NOTE]
>
>La persona Sviluppatore nell’Admin Console non è correlata al ruolo Sviluppatore in [!UICONTROL Cloud Manager].

## Utilizzo di Admin Console per creare un profilo {#using-admin-console-to-create-a-profile}

[!UICONTROL Cloud Manager] I ruoli vengono gestiti dall’Admin Console . Le appartenenze a ruoli specifici vengono fornite aggiungendo l’utente a un [!UICONTROL Cloud Manager] profilo di prodotto.

L’Admin Console è una posizione centrale per la gestione delle assegnazioni Adobe in tutta l’organizzazione. Per ulteriori informazioni su Adobe Admin Console, consulta la documentazione di [Admin Console.](https://helpx.adobe.com/it/enterprise/using/admin-console.html)

Per fornire le autorizzazioni appropriate basate sul ruolo a [!UICONTROL Cloud Manager] gli utenti, un amministratore dell’organizzazione del cliente deve creare nuovi profili di prodotto nella sezione [!UICONTROL AEM Managed Services] contesto del prodotto corrispondente a ciascuno dei quattro [!UICONTROL Cloud Manager] ruoli:

* Business Owner (Proprietario)
* Responsabile della distribuzione
* Sviluppatore
* Responsabile del programma

Puoi creare o aggiungere utenti/gruppi a questi profili di prodotto con l’Admin Console.

1. Accedi all&#39;Admin Console all&#39;indirizzo [`https://adminconsole.adobe.com`.](https://adminconsole.adobe.com)

1. Fai clic sul pulsante **Panoramica** fai clic sul prodotto da modificare nella scheda **Prodotti e servizi** il Card. Se non è presente nell’elenco, utilizza il **Prodotti** per individuare il prodotto e fare clic su di esso.

   ![Scheda Panoramica di Admin Console](/help/assets/admin-console-overview.png)

1. Sulla **Prodotti** , fai clic sull’ambiente per il quale desideri aggiungere utenti/gruppi ai profili di prodotto.

   ![Scheda Prodotti di Admin Console](/help/assets/admin-console-product.png)

1. Sulla **Profilo prodotto** scheda del prodotto, fai clic su **Nuovo profilo** per aggiungere un nuovo profilo.

   ![Nuovo profilo](/help/assets/admin-console-product-profiles.png)

1. Fornire le informazioni necessarie per impostare un nuovo ruolo per [!UICONTROL Cloud Manager].

   * **Nome profilo** - **Nome profilo** può essere qualsiasi cosa, anche se per evitare confusione si consiglia di utilizzare i valori nel **Nome profilo consigliato** colonna.
   * **Nome visualizzato** - **Nome visualizzato** deve essere il valore tecnico definito [!UICONTROL Cloud Manager] (vedere la tabella seguente).
   * **Gruppo di autorizzazioni** - Puoi scegliere un gruppo di autorizzazioni per il profilo (non sempre disponibile).

   ![Crea un nuovo profilo](/help/assets/screen_shot_2018-05-04at171819.png)

   | Ruolo | Nome visualizzato (obbligatorio) | Nome profilo consigliato |
   |---|---|---|
   | Proprietario business | `CM_BUSINESS_OWNER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Ruolo proprietario dell&#39;azienda |
   | Responsabile della distribuzione | `CM_DEPLOYMENT_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Ruolo di Deployment Manager |
   | Sviluppatore | `CM_DEVELOPER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Ruolo sviluppatore |
   | Responsabile del programma | `CM_PROGRAM_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Ruolo di responsabile del programma |


1. Fai clic su **Fine** per salvare il nuovo profilo.

## Assegnare profili a utenti o gruppi di utenti {#assign-profiles}

Dopo aver creato i profili di prodotto, puoi assegnare loro utenti o gruppi di utenti.

1. Accedi all&#39;Admin Console all&#39;indirizzo [`https://adminconsole.adobe.com`.](https://adminconsole.adobe.com)

1. Nell’Admin Console, scegli la **Utenti** scheda .

   ![Scheda Utenti](/help/assets/admin-console-users.png)

1. Fai clic su **Utenti** nel pannello di navigazione a sinistra, quindi fai clic su un utente per modificarlo.

1. Fai clic sul pulsante con i puntini di sospensione nel **Prodotti** e seleziona **Modifica**.

   ![Modifica utente](/help/assets/admin-console-edit-user.png)

1. In **Modificare prodotti e gruppi di utenti** , fai clic sul pulsante più e seleziona i profili da assegnare all’utente.

   * Se l’utente è già assegnato ai ruoli, il pulsante più sarà un pulsante di modifica (una matita), ma funziona allo stesso modo.

   ![Modificare prodotti e gruppi di utenti](/help/assets/admin-console-edit-products-and-user-groups.png)

1. Fai clic su **Salva** per salvare i profili all’utente.

Ripeti gli stessi passaggi per assegnare profili a gruppi di utenti, ma seleziona **Gruppi di utenti** dal pannello di navigazione a sinistra nella **Utenti** scheda . Fai clic su un gruppo di utenti e seleziona la **Profili di prodotto assegnati** e fai clic su **Assegna profilo prodotto** per assegnare profili.

![Assegnare profili al gruppo](/help/assets/admin-console-edit-user-groups.png)
