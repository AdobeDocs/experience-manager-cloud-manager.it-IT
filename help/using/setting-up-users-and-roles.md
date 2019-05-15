---
title: Aggiunta di utenti e ruoli
seo-title: Aggiunta di utenti e ruoli
description: 'null'
seo-description: Puoi assegnare specifiche appartenenze di ruolo aggiungendo l'utente a un profilo di prodotto di Experience Manager in Admin Console. Segui questa sezione per saperne di più.
uuid: fa 204 c 28-83 df -48 bb -8360-e 158 f 080 dee 7
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requisiti
discoiquuid: 1 b 421993-22 c 3-4 de 0-ba 64-c 1080 d 07 ad 5 e
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Aggiunta di utenti e ruoli{#add-users-and-roles}

Molte funzioni in [!UICONTROL Cloud Manager] richiedono autorizzazioni specifiche per il funzionamento. Ad esempio, solo alcuni utenti possono impostare gli indicatori di prestazioni chiave (KPI) per un programma. Queste autorizzazioni sono raggruppate in modo logico in ruoli.

[!UICONTROL Cloud Manager] al momento definisce quattro ruoli per gli utenti che determinano la disponibilità di funzioni specifiche:

* Proprietario aziendale
* Program Manager
* Gestione distribuzione
* Sviluppatore

>[!CAUTION]
>
>Per utilizzare [!UICONTROL Cloud Manager], devi avere un Adobe ID e il contesto prodotto Servizi gestiti Adobe.

## Definizioni dei ruoli {#role-definitions}

>[!NOTE]
>
>La persona per sviluppatori in Admin Console non è correlata al ruolo Sviluppatore in [!UICONTROL Cloud Manager].

La tabella seguente riepiloga i ruoli:

| [!UICONTROL Cloud Manager] Ruoli | Descrizione |
|--- |--- |
| Proprietario aziendale | Responsabile della definizione dei KPI, approvazione di implementazioni di produzione e sostituzione di importanti errori a 3 gradi. |
| Program Manager | Utilizza [!UICONTROL Cloud Manager] per eseguire l&#39;impostazione del team, lo stato di revisione e i KPI. Possono approvare importanti errori a 3 gradi. |
| Gestione distribuzione | Gestisce le operazioni di distribuzione. Utilizza [!UICONTROL Cloud Manager] per eseguire distribuzioni di fase/produzione. Può modificare gli pipeline CI/CD. Possono approvare importanti errori a 3 gradi. Può accedere all&#39;archivio Git. Contattate il rappresentante CSE/AMS per richiederlo. |
| Sviluppatore | Sviluppa e verifica il codice dell&#39;applicazione personalizzato. Viene utilizzato [!UICONTROL Cloud Manager] principalmente per visualizzare lo stato. Should get access to the Git repository for code commit. Per concedere l&#39;accesso all&#39;archivio Git, contattate il rappresentante CSE/AMS quando aggiungete un utente con questo ruolo. |
| Customer Success Engineer | In genere supporta il successo dei clienti per i clienti AMS. Interagisce con [!UICONTROL Cloud Manager] allo scopo di eseguire distribuzioni che richiedono la supervisione CSE. |
| Autore contenuto | In genere non interagisce [!UICONTROL Cloud Manager]con. Può utilizzare [!UICONTROL Cloud Manager] il commutatore di programmi (da [!UICONTROL Experience Cloud]) per accedere a AEM. |

>[!NOTE]
>
>L&#39;accesso all&#39;archivio [!UICONTROL Cloud Manager] Git è gestito dal CSE. Contattateli per aggiungere e rimuovere utenti.
>
>Se un utente appena aggiunto richiede l&#39;accesso all&#39;archivio Git, sarà necessario contattare il rappresentante CSE/AMS per ottenere l&#39;accesso. Questi ruoli non forniscono accesso automatico all&#39;archivio Git. Potete disporre di un massimo di 3 utenti con accesso repository Git.

## Utilizzo di Admin Console per creare un profilo {#using-admin-console-to-create-a-profile}

I ruoli vengono gestiti da [!UICONTROL Cloud Manager] Adobe Admin Console. Le iscrizioni di ruolo specifiche vengono fornite aggiungendo l&#39;utente a un [!UICONTROL Cloud Manager] profilo di prodotto in Admin Console.

Puoi assegnare specifiche appartenenze di ruolo aggiungendo l&#39;utente a un [!UICONTROL Cloud Manager]**profilo** di prodotto in Adobe Admin Console, una posizione centrale per la gestione delle adesioni Adobe nell&#39;intera organizzazione. Per ulteriori informazioni su Adobe Admin Console, consulta la documentazione di [Admin Console](https://helpx.adobe.com/enterprise/using/admin-console.html).

>[!NOTE]
>
>Per accedere ad admin console e configurare il team (utenti e ruoli), aprite un browser e visitate [https://adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise).

Per fornire le autorizzazioni appropriate basate su ruoli agli [!UICONTROL Cloud Manager] utenti, un amministratore nell **&#39;organizzazione del cliente**, devi creare nuovi profili di prodotto in Contesto [!UICONTROL AEM Managed Services] prodotto.

Per concedere le autorizzazioni appropriate basate su ruoli agli [!UICONTROL Cloud Manager] utenti, in qualità di amministratore devi creare quattro nuovi Profili di prodotto in Contesto [!UICONTROL AEM Managed Services] prodotto corrispondente a ciascuno dei quattro [!UICONTROL Cloud Manager] ruoli:

* Proprietario aziendale
* Gestione distribuzione
* Sviluppatore
* Program Manager

Puoi creare o aggiungere utenti/gruppi a tali profili di prodotto con [Admin Console](https://adminconsole.adobe.com/) , [!UICONTROL Cloud Manager]come illustrato nella figura seguente:

1. Accedi ad Admin Console e fai clic su **Nuovo profilo** per aggiungere un nuovo profilo.

   ![](assets/admin_console_roles-1.png)

1. Fill in the fields to set up a new role for [!UICONTROL Cloud Manager].

   Immettete **Nome profilo**, **Nome visualizzato** per creare un nuovo profilo. Inoltre, potete selezionare un **gruppo di autorizzazioni** per il profilo.

   Fai clic su **Fine** per completare il passaggio di creazione del profilo.

   >[!NOTE]
   >
   >Quando create tali profili di prodotto, il nome **visualizzato** deve essere il valore tecnico definito da [!UICONTROL Cloud Manager] (vedete la tabella seguente). Il nome **profilo** può essere qualsiasi cosa. Per evitare confusione, si consiglia di utilizzare i valori nella *colonna Nome* profilo consigliato di seguito. A tal fine, quando create il profilo di prodotto, deselezionate **Come nome profilo** e specificate il valore corrispondente come Nome **visualizzato**.

   | **Ruolo** | **Nome visualizzato (richiesto)** | **Nome profilo consigliato** |
   |---|---|---|
   | Proprietario aziendale | CM_ BUSINESS_ OWNER_ ROLE_ PROFILE | [!UICONTROL Cloud Manager] - Ruolo proprietario business |
   | Gestione distribuzione | CM_ DEPLOYMENT_ MANAGER_ ROLE_ PROFILE | [!UICONTROL Cloud Manager] - Ruolo di gestione distribuzione |
   | Sviluppatore | CM_ DEVELOPER_ ROLE_ PROFILE | [!UICONTROL Cloud Manager] - Ruolo sviluppatore |
   | Program Manager | CM_ PROGRAM_ MANAGER_ ROLE_ PROFILE | [!UICONTROL Cloud Manager] - Ruolo manager programma |

   ![](assets/screen_shot_2018-05-04at171819.png)

1. Dopo aver creato il profilo di prodotto, puoi aggiungere utenti (o gruppi) a questi profili di prodotto.

   ![](assets/image2018-4-9_15-19-26.png)

   ![](assets/image2018-4-9_15-16-47.png)

