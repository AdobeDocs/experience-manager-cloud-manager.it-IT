---
title: Aggiungere utenti e ruoli
seo-title: Aggiungere utenti e ruoli
description: Scopri utenti e ruoli e come utilizzare Admin Console per creare un profilo
seo-description: Puoi assegnare iscrizioni di ruolo specifiche aggiungendo l’utente a un profilo di prodotto Cloud Manager nell’Admin Console. Segui questa sezione per ulteriori informazioni.
uuid: fa204c28-83df-48bb-8360-e158f080dee7
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requirements
discoiquuid: 1b421993-22c3-4de0-ba64-c1080d07ad5e
feature: Ruoli utente
translation-type: tm+mt
source-git-commit: c5d32d49782c899d013fcc60b9c4d2b67e9350ae
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 32%

---


# Aggiungere utenti e ruoli {#add-users-and-roles}

Molte funzionalità in [!UICONTROL Cloud Manager] richiedono autorizzazioni specifiche per funzionare. Ad esempio, solo alcuni utenti possono impostare gli indicatori prestazioni chiave (KPI, Key Performance Indicators) per un programma. Queste autorizzazioni sono raggruppate in modo logico in ruoli.

[!UICONTROL Cloud Manager] attualmente definisce quattro ruoli per gli utenti che determinano la disponibilità di funzionalità specifiche:

* Business Owner (Proprietario)
* Program Manager (Responsabile programma)
* Deployment Manager (Responsabile implementazione)
* Developer (Sviluppatore)

>[!CAUTION]
>
>Per utilizzare [!UICONTROL Cloud Manager], è necessario disporre di un contesto di prodotto Adobe ID e Adobe Managed Services.

## Definizioni dei ruoli {#role-definitions}

>[!NOTE]
>
>La persona Sviluppatore in Admin Console non è correlata al ruolo Sviluppatore in [!UICONTROL Cloud Manager].

La tabella seguente riepiloga i ruoli:

| [!UICONTROL Cloud Manager] Ruoli | Descrizione |
|--- |--- |
| Business Owner (Proprietario) | Responsabile della definizione dei KPI, dell’approvazione delle implementazioni di produzione e dell’override di importanti errori a 3 livelli. |
| Program Manager (Responsabile programma) | Utilizza [!UICONTROL Cloud Manager] per eseguire la configurazione del team, esaminare lo stato e visualizzare i KPI. Può approvare importanti errori a 3 livelli. |
| Deployment Manager (Responsabile implementazione) | Gestisce le operazioni di distribuzione. Utilizza [!UICONTROL Cloud Manager] per eseguire le distribuzioni di stage/produzione. È possibile modificare le pipeline CI/CD. Può approvare importanti errori a 3 livelli. È possibile accedere all’archivio Git. |
| Developer (Sviluppatore) | Sviluppa e verifica il codice personalizzato dell’applicazione. Utilizza principalmente [!UICONTROL Cloud Manager] per visualizzare lo stato. Può accedere all’archivio Git per il commit del codice. |
| Tecnico di successo del cliente | In genere supporta il successo dei clienti per i clienti AMS. Interagisce con [!UICONTROL Cloud Manager] allo scopo di eseguire implementazioni che richiedono la sorveglianza CSE. |
| Autore del contenuto | In genere non interagisce con [!UICONTROL Cloud Manager]. Per accedere a AEM può essere utilizzato il programma di commutazione [!UICONTROL Cloud Manager] (dopo aver navigato da [!UICONTROL Experience Cloud]). |

## Utilizzo di Admin Console per creare un profilo {#using-admin-console-to-create-a-profile}

I ruoli vengono gestiti per [!UICONTROL Cloud Manager] da Adobe Admin Console. Le iscrizioni di ruolo specifiche vengono fornite aggiungendo l’utente a un [!UICONTROL Cloud Manager] profilo di prodotto in Admin Console.

Puoi assegnare iscrizioni di ruolo specifiche aggiungendo l’utente a un Profilo di prodotto[!UICONTROL Cloud Manager] **** nell’Admin Console di Adobe, una posizione centrale per la gestione dei diritti Adobe in tutta l’organizzazione. Per ulteriori informazioni su Adobe Admin Console, consulta la documentazione di [Admin Console](https://helpx.adobe.com/it/enterprise/using/admin-console.html).

>[!NOTE]
>
>Per accedere ad Admin Console e configurare il team (utenti e ruoli), apri un browser e visita [https://adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise).

Per fornire le autorizzazioni appropriate basate sul ruolo agli utenti di [!UICONTROL Cloud Manager], un amministratore dell’**organizzazione** del cliente deve creare nuovi profili di prodotto nel contesto di prodotto di [!UICONTROL AEM Managed Services].

Per fornire le autorizzazioni appropriate basate sul ruolo agli utenti [!UICONTROL Cloud Manager], in qualità di amministratore è necessario creare quattro nuovi profili di prodotto nel contesto di prodotto [!UICONTROL AEM Managed Services] corrispondente a ciascuno dei quattro ruoli [!UICONTROL Cloud Manager]:

* Business Owner (Proprietario)
* Deployment Manager (Responsabile implementazione)
* Developer (Sviluppatore)
* Program Manager (Responsabile programma)

Puoi creare o aggiungere utenti/gruppi a questi profili di prodotto con l&#39; [Admin Console](https://adminconsole.adobe.com/) per [!UICONTROL Cloud Manager], come illustrato nella figura seguente:

1. Accedi ad Admin Console e fai clic su **Nuovo profilo** per aggiungere un nuovo profilo.

   ![](assets/admin_console_roles-1.png)

1. Compila i campi per impostare un nuovo ruolo per [!UICONTROL Cloud Manager].

   Per creare un nuovo profilo, immetti **Nome profilo** e **Nome visualizzato**. Inoltre, puoi selezionare un **gruppo di autorizzazioni** per il profilo.

   Fai clic su **Fine** per completare il passaggio di creazione del profilo.

   >[!NOTE]
   >
   >Quando si creano questi profili di prodotto, il **Nome visualizzato** deve essere il valore tecnico definito da [!UICONTROL Cloud Manager] (vedi tabella seguente). Il **Nome profilo** può essere qualsiasi cosa, anche se per evitare confusione si consiglia di utilizzare i valori nella colonna sottostante *Nome profilo consigliato*. A questo proposito, durante la creazione del profilo di prodotto, deseleziona **Same as Profile Name (Come nome profilo)** e specifica il valore corrispondente come **Nome visualizzato**.

   | **Ruolo** | **Nome visualizzato (obbligatorio)** | **Nome profilo consigliato** |
   |---|---|---|
   | Business Owner (Proprietario) | CM_BUSINESS_OWNER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - Ruolo proprietario dell&#39;azienda |
   | Deployment Manager (Responsabile implementazione) | CM_DEPLOYMENT_MANAGER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - Ruolo di Deployment Manager |
   | Developer (Sviluppatore) | CM_DEVELOPER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - Ruolo sviluppatore |
   | Program Manager (Responsabile programma) | CM_PROGRAM_MANAGER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - Ruolo di responsabile del programma |

   ![](assets/screen_shot_2018-05-04at171819.png)

1. Una volta creato il profilo di prodotto, puoi aggiungere utenti (o gruppi) a questi profili di prodotto.

   ![](assets/image2018-4-9_15-19-26.png)

   ![](assets/image2018-4-9_15-16-47.png)

