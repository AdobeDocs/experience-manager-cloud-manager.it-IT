---
title: Aggiungi utenti e ruoli
seo-title: Aggiungi utenti e ruoli
description: 'null'
seo-description: Puoi assegnare appartenenze a ruoli specifici aggiungendo l’utente a un profilo di prodotto di Cloud Manager nell’Admin Console. Segui questa sezione per saperne di più.
uuid: fa204c28-83df-48bb-8360-e158f080dee7
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requirements
discoiquuid: 1b421993-22c3-4de0-ba64-c1080d07ad5e
translation-type: tm+mt
source-git-commit: 73203dca7b20570103af429cf933610941b787be

---


# Add Users and Roles{#add-users-and-roles}

Many features in  require specific permissions to operate. [!UICONTROL Cloud Manager] For example, only certain users are allowed to set the Key Performance Indicators (KPIs) for a program. These permissions are logically grouped into roles.

[!UICONTROL Cloud Manager] currently defines four roles for users which govern the availability of specific features:

* Business Owner
* Program Manager
* Deployment Manager
* Sviluppatore

>[!CAUTION]
>
>Per utilizzare [!UICONTROL Cloud Manager], è necessario disporre di un Adobe ID e del contesto di prodotto dei servizi gestiti Adobe.

## Role Definitions {#role-definitions}

>[!NOTE]
>
>The Developer persona in Admin Console is unrelated to the Developer role in .[!UICONTROL Cloud Manager]

The following table summarizes the roles:

| [!UICONTROL Cloud Manager] Ruoli | Descrizione |
|--- |--- |
| Business Owner | Responsible for defining KPIs, approving production deployments and overriding important 3-tier failures. |
| Program Manager | Utilizza [!UICONTROL Cloud Manager] per eseguire la configurazione del team, esaminare lo stato e visualizzare i KPI. Può approvare importanti fallimenti a 3 livelli. |
| Gestione distribuzione | Gestisce le operazioni di distribuzione. Utilizza [!UICONTROL Cloud Manager] per eseguire distribuzioni di fase/produzione. È possibile modificare le tubazioni CI/CD. Può approvare importanti fallimenti a 3 livelli. Può accedere al repository Git. Contattate il rappresentante CSE/AMS per richiederlo. |
| Sviluppatore | Sviluppa e verifica il codice applicazione personalizzato. Viene utilizzato principalmente [!UICONTROL Cloud Manager] per visualizzare lo stato. Dovrebbe accedere al repository Git per il commit del codice. Per concedere l’accesso al repository Git, contattate il rappresentante CSE/AMS quando aggiungete un utente con questo ruolo. |
| Customer Success Engineer | In genere supporta il successo dei clienti per i clienti AMS. Interagisce con [!UICONTROL Cloud Manager] lo scopo di eseguire distribuzioni che richiedono la sorveglianza CSE. |
| Content Author | Generalmente non interagisce con [!UICONTROL Cloud Manager]. Può usare [!UICONTROL Cloud Manager] il selettore programmi (dopo aver navigato da [!UICONTROL Experience Cloud]) per accedere ad AEM. |

>[!NOTE]
>
>L’accesso all’archivio [!UICONTROL Cloud Manager] Git è gestito dal CSE. Contattateli per aggiungere e rimuovere utenti.
>
>Se un nuovo utente richiede l’accesso al repository Git, è necessario contattare il rappresentante CSE/AMS per ottenere l’accesso concesso. Questi ruoli non forniscono l'accesso automatico all'archivio Git. È possibile avere un massimo di 3 utenti con accesso al repository Git.

## Utilizzo di Admin Console per creare un profilo {#using-admin-console-to-create-a-profile}

I ruoli vengono gestiti [!UICONTROL Cloud Manager] da Adobe Admin Console. Le appartenenze a ruoli specifici vengono fornite aggiungendo l'utente a un profilo di [!UICONTROL Cloud Manager] prodotto in Admin Console.

You can assign specific role memberships by adding the user to a  Product Profile in the Adobe Admin Console, a central location for managing your Adobe entitlements across your entire organization. [!UICONTROL Cloud Manager]**** Per ulteriori informazioni su Adobe Admin Console, consulta la documentazione di [Admin Console](https://helpx.adobe.com/enterprise/using/admin-console.html).

>[!NOTE]
>
>To acces the admin console and set up your team (users and roles), open a browser and visit https://adminconsole.adobe.com.[](https://adminconsole.adobe.com/enterprise)

In order to provide the appropriate role-based permissions to  users, an administrator in the customer's Organization, must create new Product Profiles under the  Product Context.[!UICONTROL Cloud Manager]****[!UICONTROL AEM Managed Services]

To provide the appropriate role-based permissions to  users, as an administrator you must create four new Product Profiles under the  Product Context corresponding to each of the four  roles:[!UICONTROL Cloud Manager][!UICONTROL AEM Managed Services][!UICONTROL Cloud Manager]

* Business Owner
* Deployment Manager
* Sviluppatore
* Program Manager

You can create, or add, users/groups to these Product Profiles with the Admin Console for , as shown in the figure below:[](https://adminconsole.adobe.com/)[!UICONTROL Cloud Manager]

1. Log in to Admin console and click New Profile to add a new profile.****

   ![](assets/admin_console_roles-1.png)

1. Fill in the fields to set up a new role for .[!UICONTROL Cloud Manager]

   Enter Profile Name, Display Name to create a new profile. ******** Additionally, you can select a Permission Group for the profile.****

   Click Done to complete the profile creation step.****

   >[!NOTE]
   >
   >Quando si creano questi profili di prodotto, il Nome **** visualizzato deve essere il valore tecnico definito da [!UICONTROL Cloud Manager] (vedere la tabella seguente). The Profile Name can be anything, although to avoid confusion it is recommended to use the values in the Recommended Profile Name column below. ****** To do this, when creating the Product Profile, uncheck the Same as Profile Name and specify the corresponding value as the Display Name.********

   | **Ruolo** | **Nome visualizzato (obbligatorio)** | **Nome profilo consigliato** |
   |---|---|---|
   | Proprietario | CM_BUSINESS_OWNER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - Ruolo Proprietario |
   | Gestione distribuzione | CM_DEPLOYMENT_MANAGER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - Ruolo di Gestione distribuzione |
   | Sviluppatore | CM_DEVELOPER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - Ruolo sviluppatore |
   | Program Manager | CM_PROGRAM_MANAGER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - Ruolo del manager del programma |

   ![](assets/screen_shot_2018-05-04at171819.png)

1. Dopo aver creato il profilo di prodotto, puoi aggiungere utenti (o gruppi) a questi profili di prodotto.

   ![](assets/image2018-4-9_15-19-26.png)

   ![](assets/image2018-4-9_15-16-47.png)

