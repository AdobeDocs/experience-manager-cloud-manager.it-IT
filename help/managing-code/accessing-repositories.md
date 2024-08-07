---
title: Informazioni di accesso all’archivio
description: Scopri come accedere e gestire gli archivi Git gestiti da Adobe con la gestione self-service dell’account Git da Cloud Manager.
exl-id: 1cc88c82-67c7-4553-a1b8-d2ab22be466c
source-git-commit: e93285f7c7495ec9d2f11d289adaf6aaba7e58ea
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 100%

---

# Informazioni di accesso all’archivio {#accessing-repos}

Scopri come accedere e gestire gli archivi Git gestiti da Adobe con la gestione self-service dell’account Git da Cloud Manager.

## Accesso ai dati dell’archivio dalla pagina Panoramica {#overview-page}

Cloud Manager consente di recuperare facilmente le informazioni sull’accesso archivi gestiti da Adobe tramite il pulsante **Accedi a dati archivio** disponibile in primo piano nella scheda della pipeline.

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Passa alla scheda **Pipeline** dalla pagina **Panoramica del programma**.

   ![Pulsante Accedi a dati archivio nella scheda Ambienti](assets/pipelines-card.png)

1. Tocca o fai clic sul pulsante **Accedi a dati archivio** per aprire la finestra di dialogo **Informazioni archivio** e visualizza:

   * Il nome utente di Git.
   * La password di Git.
   * L’URL dell’archivio Git di Cloud Manager.
   * Comandi Git predefiniti per aggiungere rapidamente un remoto all’archivio Git e inviare il codice.

   ![Finestra dati archivio](assets/access-repo-info.png)

1. Per accedere alla password, è necessario generare una nuova password. Per farlo, tocca o fai clic sul pulsante **Genera password**.

1. Conferma la generazione password nella finestra di dialogo **Procedere?** toccando o facendo clic su **Genera password**.

   ![Conferma la generazione della password](assets/confirm-password-generation.png)

1. La password viene generata ed è visibile per la copia nel campo **Password**.

   * La generazione di una password invalida la password precedente.
   * Cloud Manager non salverà la password. È tua responsabilità salvare la password in modo sicuro.
   * Se la password viene persa, è necessario rigenerarne una nuova, poiché Cloud Manager non la salva.

   ![Esempio di password generata](assets/generated-password.png)

Con queste credenziali puoi clonare una copia locale dell’archivio, apportare qui le modifiche e, una volta terminato, riconfermarle nell’archivio del codice remoto in Cloud Manager.

>[!NOTE]
>
>* L’opzione **Accedi a dati archivio** è visibile agli utenti con i ruoli **Sviluppatore** o **Responsabile dell’implementazione**.
>* Il pulsante **Accedi a dati archivio** visualizza solo le informazioni di accesso all’archivio per gli archivi gestiti da Adobe. L’accesso alle informazioni degli [archivi privati](private-repositories.md) non è disponibile in Cloud Manager.

## Accesso alle informazioni dell’archivio dalla finestra Archivi {#repositories-window}

Un pulsante **Accedi a dati archivio** è disponibile anche nella barra degli strumenti della finestra [**Archivi**.](managing-repositories.md) visualizza le stesse informazioni sull’accesso agli archivi gestiti da Adobe.

## Revoca di una password di accesso {#revoke-password}

Puoi revocare una password di accesso in qualsiasi momento. Per farlo, [crea un ticket di supporto per questa richiesta.](https://experienceleague.adobe.com/?support-solution=Experience+Manager&amp;support-tab=home?lang=it#support)

Il ticket sarà trattato con priorità alta e dovrebbe essere revocato nell’arco della giornata.
