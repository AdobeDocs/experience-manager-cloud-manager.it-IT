---
title: Gestire i token di accesso in Cloud Manager
description: Scopri come visualizzare, modificare ed eliminare i token di accesso utilizzati per Bring Your Own Git in Cloud Manager su Adobe Managed Services.
badge: label="Adottatore anticipato" type="Positive" url="/help/release-notes/current.md#access-tokens"
source-git-commit: aa0eff7eb1f6b0cde9b99b7cbbfb3410e0db94a6
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 3%

---


# Gestire i token di accesso per gli archivi esterni {#manage-access-tokens}

Cloud Manager utilizza i token di accesso per gestire archivi ospitati su piattaforme Git esterne. In precedenza, se un token scadeva, era necessario ripetere l’onboarding dell’archivio associato per rimanere operativo.

Ora la funzionalità **Gestisci token di accesso** consente di gestire i token in modo più efficiente. Puoi visualizzare, rinominare o rimuovere i token collegati ai provider Git esterni supportati, inclusi GitHub Enterprise, GitLab, Bitbucket e Azure DevOps.

Vedi anche [Aggiungere archivi esterni in Cloud Manager](/help/managing-code/external-repositories.md).

>[!NOTE]
>
>Le funzioni descritte in questo articolo sono disponibili solo attraverso il programma di adozione anticipata. Per ulteriori dettagli e per iscriverti come utente iniziale, vedi [Gestione token di accesso](/help/release-notes/current.md#access-tokens).

## Visualizza token di accesso {#view-access-tokens}

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione appropriata.
1. Nella console **[I miei programmi](/help/getting-started/navigation.md#my-programs-console)**, seleziona il programma di cui desideri gestire il token di accesso Git personalizzato.
1. Nel menu laterale, in **Programma**, fare clic su ![Icona struttura cartella](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **Archivi**.
1. Fai clic su **Gestisci token di accesso** nell&#39;angolo superiore destro della pagina.

   Il pulsante **Gestisci token di accesso** è visibile solo se il programma utilizza la funzione Bring Your Own Git.

   ![Finestra di dialogo Gestisci token di accesso contenente un token attivo e un token inattivo](/help/managing-code/assets/access-tokens-manage.png)

1. Nella finestra di dialogo **Gestisci token di accesso**:
   * Sono elencati tutti i token di accesso.
   * Puoi **modificare** qualsiasi token.
   * È possibile **eliminare** solo i token *non attualmente in uso*. Se un token è in uso, il pulsante ![Elimina icona struttura](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg) è disabilitato.

## Modificare un token di accesso {#edit-access-tokens}

1. Nella finestra di dialogo **Gestisci token di accesso**, a destra del nome di un token, fai clic sull&#39;icona ![Modifica](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg).
1. Nella finestra di dialogo **Modifica token di accesso**, aggiorna il nome del token nel campo di testo **Nome token**.

   Impossibile modificare il segreto del token di accesso stesso.

   ![Finestra di dialogo Modifica token di accesso](/help/managing-code/assets/access-tokens-edit.png)

1. Se il token è in uso, una notifica ti avvisa che tutti gli archivi associati vengono automaticamente riconvalidati.

1. Fai clic su **Aggiorna** per salvare le modifiche.

## Eliminare un token di accesso {#delete-access-token}

1. Nella finestra di dialogo **Gestisci token di accesso**, a destra del nome di un token, fai clic sull&#39;icona ![Elimina](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg)

   L&#39;icona è disabilitata (![Icona Elimina struttura](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg)) per i token attualmente in uso.

1. Nella finestra di dialogo **Elimina token di accesso**, fai clic su **Elimina** per rimuovere definitivamente il token.