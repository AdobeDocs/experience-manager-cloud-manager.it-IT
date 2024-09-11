---
title: Informazioni di accesso all’archivio
description: Scopri come accedere e gestire gli archivi Git gestiti da Adobe utilizzando la gestione account Git self-service da Cloud Manager.
exl-id: 1cc88c82-67c7-4553-a1b8-d2ab22be466c
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '361'
ht-degree: 100%

---

# Informazioni di accesso all’archivio {#accessing-repos}

Scopri come accedere e gestire gli archivi Git gestiti da Adobe utilizzando la gestione account Git self-service da Cloud Manager.

## Accesso ai dati dell’archivio dalla pagina Panoramica {#overview-page}

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Passa alla scheda **Pipeline** dalla pagina **Panoramica del programma**.

   ![Pulsante Accedi a dati archivio nella scheda Ambienti](assets/pipelines-card.png)

1. Fai clic su **Accedi a dati archivio**. Nella finestra di dialogo **Informazioni archivio per...** è possibile visualizzare quanto segue:

   * Il nome utente di Git.
   * La password di Git.
   * L’URL dell’archivio Git di Cloud Manager.
   * Comandi Git predefiniti per aggiungere rapidamente un remoto all’archivio Git e inviare il codice.

   ![Finestra dati archivio](assets/access-repo-info.png)

1. Per accedere alla password, è necessario generare una nuova password. Fai clic su **`Generate password`**.

1. Conferma la generazione password nella finestra di dialogo **Procedere?** facendo clic su **Genera password**.

   ![Conferma la generazione della password](assets/confirm-password-generation.png)

1. Nel campo **Password** viene generata la password. Fai clic sull’icona Copia per copiarla negli Appunti.

   * La generazione di una password invalida la password precedente.
   * Cloud Manager non salva la password di accesso. Assicurarsi di salvare la password in modo sicuro.
   * Se si perde la password, è necessario generarne una nuova.

   ![Esempio di password generata](assets/generated-password.png)

Con queste credenziali puoi clonare una copia locale dell’archivio, apportare qui le modifiche e, una volta terminato, riconfermarle nell’archivio del codice remoto in Cloud Manager.

>[!NOTE]
>
>* L’opzione **Accedi a dati archivio** è visibile agli utenti con il ruolo di **Sviluppatore** o **Responsabile della distribuzione**.
>* Il pulsante **Accedi a dati archivio** visualizza solo le informazioni di accesso all’archivio per gli archivi gestiti da Adobe. L’accesso alle informazioni degli [archivi privati](private-repositories.md) non è disponibile in Cloud Manager.

## Accesso alle informazioni dell’archivio dalla finestra Archivi {#repositories-window}

Un pulsante **Accedi a dati archivio** è disponibile anche nella barra degli strumenti della finestra [**Archivi**](managing-repositories.md). Visualizza le stesse informazioni sull’accesso agli archivi gestiti da Adobe.

## Revoca di una password di accesso {#revoke-password}

Puoi revocare una password di accesso in qualsiasi momento. [Crea un ticket di supporto per tale richiesta](https://experienceleague.adobe.com/?support-solution=Experience+Manager&amp;support-tab=home?lang=it#support).

Il ticket sarà trattato con priorità alta e dovrebbe essere revocato nell’arco della giornata.
