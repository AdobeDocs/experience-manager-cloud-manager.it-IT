---
title: Aggiungere utenti e ruoli
description: Scopri come utilizzare l’Admin Console per aggiungere utenti e ruoli e creare profili.
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: b0dbb602253939464ff034941ffbad84b7df77df
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 16%

---


# Aggiungere utenti e ruoli {#add-users-and-roles}

Molte funzioni in [!UICONTROL Cloud Manager] richiedere autorizzazioni specifiche da utilizzare. Ad esempio, solo alcuni utenti possono impostare gli indicatori prestazioni chiave (KPI, Key Performance Indicators) per un programma. Queste autorizzazioni sono raggruppate in modo logico in ruoli.

[!UICONTROL Cloud Manager] attualmente definisce quattro ruoli per gli utenti che determinano la disponibilità di funzionalità specifiche:

* Business Owner (Proprietario)
* Program Manager (Responsabile programma)
* Responsabile della distribuzione
* Sviluppatore

>[!NOTE]
>
>Per utilizzare [!UICONTROL Cloud Manager], è necessario disporre di un contesto di prodotto Adobe ID e Adobe Managed Services.

## Definizioni dei ruoli {#role-definitions}

In questa tabella vengono riepilogati i ruoli.

| [!UICONTROL Cloud Manager] Ruolo | Descrizione |
|--- |--- |
| Business Owner (Proprietario) | Questo utente è responsabile della definizione dei KPI, dell’approvazione delle implementazioni di produzione e dell’override di importanti errori a 3 livelli quando necessario. |
| Program Manager (Responsabile programma) | Questo utente utilizza [!UICONTROL Cloud Manager] per eseguire la configurazione del team, esaminare lo stato, visualizzare i KPI e approvare importanti errori a 3 livelli quando necessario. |
| Responsabile della distribuzione | Questo utente gestisce le operazioni di distribuzione e utilizza [!UICONTROL Cloud Manager] per eseguire distribuzioni di staging/produzione, modifica le pipeline CI/CD, approva importanti errori a 3 livelli quando necessario e può accedere all’archivio git. |
| Sviluppatore | Questo utente sviluppa e verifica il codice personalizzato dell&#39;applicazione e utilizza principalmente [!UICONTROL Cloud Manager] per visualizzare lo stato di distribuzione e accedere all’archivio git per le conferme di codice. |
| Tecnico di successo del cliente | Questo utente in genere supporta il successo dei clienti per i clienti AMS e interagisce con [!UICONTROL Cloud Manager] al fine di eseguire distribuzioni che richiedono la sorveglianza CSE. |
| Autore del contenuto | Questo utente generalmente non interagisce con [!UICONTROL Cloud Manager] ma può utilizzare [!UICONTROL Cloud Manager] per accedere a AEM. |

>[!NOTE]
>
>La persona Sviluppatore nell’Admin Console non è correlata al ruolo Sviluppatore in [!UICONTROL Cloud Manager].

## Utilizzo di Admin Console per creare un profilo {#using-admin-console-to-create-a-profile}

[!UICONTROL Cloud Manager] I ruoli vengono gestiti dall’Admin Console . Le appartenenze a ruoli specifici vengono fornite aggiungendo l’utente a un [!UICONTROL Cloud Manager] profilo di prodotto.

L’Admin Console è una posizione centrale per la gestione delle adesioni Adobi in tutta l’organizzazione. Per ulteriori informazioni su Adobe Admin Console, consulta la documentazione di [Admin Console.](https://helpx.adobe.com/it/enterprise/using/admin-console.html)

>[!NOTE]
>
>Per accedere ad Admin Console e configurare il team (utenti e ruoli), visita [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com).

Per fornire le autorizzazioni appropriate basate sul ruolo a [!UICONTROL Cloud Manager] gli utenti, un amministratore dell’organizzazione del cliente deve creare nuovi profili di prodotto nella sezione [!UICONTROL AEM Managed Services] contesto del prodotto corrispondente a ciascuno dei quattro [!UICONTROL Cloud Manager] ruoli:

* Business Owner (Proprietario)
* Deployment Manager (Responsabile implementazione)
* Sviluppatore
* Program Manager (Responsabile programma)

Puoi creare o aggiungere utenti/gruppi a questi profili di prodotto con l’Admin Console .

1. Accedi all’Admin Console e fai clic su **Nuovo profilo** per aggiungere un nuovo profilo.

   ![Nuovo profilo](/help/assets/admin_console_roles-1.png)

1. Fornire le informazioni necessarie per impostare un nuovo ruolo per [!UICONTROL Cloud Manager].

   * **Nome profilo**
   * **Nome visualizzato**
   * **Gruppo di autorizzazioni**

1. Fai clic su **Fine** per completare il passaggio di creazione del profilo.

Quando crei profili di prodotto, la **Nome visualizzato** deve essere il valore tecnico definito [!UICONTROL Cloud Manager] (vedere la tabella seguente). La **Nome profilo** può essere qualsiasi cosa, anche se per evitare confusione si consiglia di utilizzare i valori nel **Nome profilo consigliato** colonna. A questo proposito, durante la creazione del profilo di prodotto, deseleziona **Same as Profile Name (Come nome profilo)** e specifica il valore corrispondente come **Nome visualizzato**.

| **Ruolo** | **Nome visualizzato (obbligatorio)** | **Nome profilo consigliato** |
|---|---|---|
| Business Owner (Proprietario) | `CM_BUSINESS_OWNER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Ruolo proprietario dell&#39;azienda |
| Responsabile della distribuzione | `CM_DEPLOYMENT_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Ruolo di Deployment Manager |
| Sviluppatore | `CM_DEVELOPER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Ruolo sviluppatore |
| Program Manager (Responsabile programma) | `CM_PROGRAM_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Ruolo di responsabile del programma |

![Creazione di un nuovo profilo](/help/assets/screen_shot_2018-05-04at171819.png)

Una volta creato il profilo di prodotto, puoi aggiungere utenti (o gruppi) a questi profili di prodotto.

![Modifica utente](/help/assets/image2018-4-9_15-19-26.png)

![Gruppi di utenti](/help/assets/image2018-4-9_15-16-47.png)
