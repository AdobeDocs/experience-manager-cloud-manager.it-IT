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


# Aggiungi utenti e ruoli{#add-users-and-roles}

Molte funzioni in [!UICONTROL Cloud Manager] richiedono autorizzazioni specifiche per funzionare. Ad esempio, solo alcuni utenti possono impostare i KPI (Key Performance Indicators) per un programma. Tali autorizzazioni sono logicamente raggruppate in ruoli.

[!UICONTROL Cloud Manager] definisce attualmente quattro ruoli per gli utenti che determinano la disponibilità di funzionalità specifiche:

* Proprietario
* Program Manager
* Gestione distribuzione
* Sviluppatore

>[!CAUTION]
>
>Per utilizzare [!UICONTROL Cloud Manager], è necessario disporre di un Adobe ID e del contesto di prodotto dei servizi gestiti Adobe.

## Definizioni dei ruoli {#role-definitions}

>[!NOTE]
>
>La persona Sviluppatore in Admin Console non è correlata al ruolo Sviluppatore in [!UICONTROL Cloud Manager].

La tabella seguente riepiloga i ruoli:

| [!UICONTROL Cloud Manager] Ruoli | Descrizione |
|--- |--- |
| Proprietario | Responsabile della definizione dei KPI, dell'approvazione delle implementazioni di produzione e della risoluzione di importanti errori a 3 livelli. |
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

Puoi assegnare iscrizioni di ruolo specifiche aggiungendo l’utente a un profilo [!UICONTROL Cloud Manager] di **** prodotto in Adobe Admin Console, una posizione centrale per la gestione delle adesioni Adobe in tutta l’organizzazione. Per ulteriori informazioni su Adobe Admin Console, consulta la documentazione di [Admin Console](https://helpx.adobe.com/enterprise/using/admin-console.html).

>[!NOTE]
>
>Per accedere alla console di amministrazione e configurare il team (utenti e ruoli), aprite un browser e visitate [https://adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise).

Per fornire agli [!UICONTROL Cloud Manager] utenti le autorizzazioni appropriate basate sul ruolo, un amministratore dell' **Organizzazione** del cliente deve creare nuovi profili di prodotto nel contesto del [!UICONTROL AEM Managed Services] prodotto.

Per concedere agli [!UICONTROL Cloud Manager] utenti le autorizzazioni appropriate basate sul ruolo, in qualità di amministratore è necessario creare quattro nuovi profili di prodotto nel contesto del [!UICONTROL AEM Managed Services] prodotto corrispondente a ciascuno dei quattro [!UICONTROL Cloud Manager] ruoli:

* Proprietario
* Gestione distribuzione
* Sviluppatore
* Program Manager

Puoi creare o aggiungere utenti/gruppi a questi profili di prodotto con [Admin Console](https://adminconsole.adobe.com/) per [!UICONTROL Cloud Manager], come illustrato nella figura seguente:

1. Accedi ad Admin Console e fai clic su **Nuovo profilo** per aggiungere un nuovo profilo.

   ![](assets/admin_console_roles-1.png)

1. Compila i campi per impostare un nuovo ruolo per [!UICONTROL Cloud Manager].

   Immettete Nome **** profilo e Nome **** visualizzato per creare un nuovo profilo. Inoltre, potete selezionare un gruppo **di** autorizzazioni per il profilo.

   Fate clic su **Fine** per completare il passaggio di creazione del profilo.

   >[!NOTE]
   >
   >Quando si creano questi profili di prodotto, il Nome **** visualizzato deve essere il valore tecnico definito da [!UICONTROL Cloud Manager] (vedere la tabella seguente). Il Nome **** profilo può essere qualsiasi cosa, anche se per evitare confusione si consiglia di utilizzare i valori nella colonna Nome *profilo* consigliato di seguito. A questo scopo, durante la creazione del profilo di prodotto, deselezionate **Come nome** profilo e specificate il valore corrispondente come nome **** visualizzato.

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

