---
title: Informazioni di accesso all’archivio
description: Scopri come accedere e gestire gli archivi Git gestiti da Adobe con la gestione self-service dell’account Git da Cloud Manager.
exl-id: 1cc88c82-67c7-4553-a1b8-d2ab22be466c
source-git-commit: 4c4a2688cab8e5c81efa4b7b5e26f3c7b5dc30d6
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 37%

---

# Informazioni di accesso all’archivio {#accessing-repos}

Scopri come accedere e gestire gli archivi Git gestiti da Adobe utilizzando la gestione self-service dell’account Git in Cloud Manager.

## Accedere alle informazioni dell’archivio dalla pagina Panoramica {#overview-page}

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Passa alla scheda **Pipeline** dalla pagina **Panoramica del programma**.

   ![Pulsante Accedi a dati archivio nella scheda Ambienti](assets/pipelines-card.png)

1. Fare clic su **Accedi a dati archivio**. Nella finestra di dialogo **Informazioni archivio per...** è possibile visualizzare quanto segue:

   * Il nome utente Git.
   * La password Git.
   * L’URL dell’archivio Git di Cloud Manager.
   * Comandi Git pregenerati per aggiungere rapidamente e inviare in push il codice da un server remoto all’archivio Git.

   ![Finestra dati archivio](assets/access-repo-info.png)

1. Per accedere alla password, è necessario generare una nuova password. Fai clic su **`Generate password`**.

1. Nella finestra di dialogo **Continuare...**, confermare la generazione della password facendo clic su **Genera password**.

   ![Conferma la generazione della password](assets/confirm-password-generation.png)

1. Nel campo **Password** viene generata la password. Fai clic sull’icona Copia per copiarla negli Appunti.

   * La generazione di una password invalida la password precedente.
   * Cloud Manager non salva la password di accesso. Assicurarsi di salvare la password in modo sicuro.
   * Se si perde la password, è necessario generarne una nuova.

   ![Esempio di password generata](assets/generated-password.png)

Con queste credenziali puoi clonare una copia locale dell’archivio, apportare qui le modifiche e, una volta terminato, riconfermarle nell’archivio del codice remoto in Cloud Manager.

>[!NOTE]
>
>* L&#39;opzione **Accedi a dati archivio** è visibile agli utenti con il ruolo **Sviluppatore**, **Responsabile della distribuzione** o entrambi.
>* Il pulsante **Accedi a dati archivio** visualizza solo le informazioni di accesso all’archivio per gli archivi gestiti da Adobe. L’accesso alle informazioni degli [archivi privati](private-repositories.md) non è disponibile in Cloud Manager.

## Accedere alle informazioni del repository dalla finestra Repository {#repositories-window}

Il pulsante **Accedi a dati archivio** è disponibile anche nella barra degli strumenti della finestra [**Archivi**](managing-repositories.md). Vengono visualizzate le stesse informazioni sull’accesso agli archivi gestiti da Adobe.

## Revoca di una password di accesso {#revoke-password}

Puoi revocare una password di accesso in qualsiasi momento. [Crea un ticket di supporto per tale richiesta](https://experienceleague.adobe.com/?support-solution=Experience+Manager&amp;support-tab=home?lang=it#support).

Il ticket viene trattato con priorità elevata e in genere viene revocato entro un giorno.
