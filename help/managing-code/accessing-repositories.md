---
title: Informazioni di accesso all’archivio
description: Scopri come accedere e gestire gli archivi Git gestiti da Adobe utilizzando la gestione account Git self-service da Cloud Manager.
exl-id: 1cc88c82-67c7-4553-a1b8-d2ab22be466c
TQID: https://experienceleague.adobe.com/S3oIN4DvfYCvKQLGQmFtWlqHcN5Mv9xvoNKjaMnNlm0
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: c1c7a8a36bd770401393fe7e2c62b306c1a2573d
workflow-type: tm+mt
source-wordcount: 400
ht-degree: 72%

---

# Informazioni di accesso all’archivio {#accessing-repos}

Scopri come accedere e gestire gli archivi Git gestiti da Adobe utilizzando la gestione account Git self-service da Cloud Manager.

## Accesso ai dati dell’archivio dalla pagina Panoramica {#overview-page}

Con Cloud Manager, puoi recuperare le informazioni di accesso all&#39;archivio per gli archivi gestiti da Adobe utilizzando **Accedi a dati archivio** dalla scheda **Pipeline**.

La finestra di dialogo **Informazioni archivio** consente di visualizzare le seguenti informazioni di accesso per gli archivi gestiti da Adobe:

* Il nome utente di Git.
* La password di Git.
* L’URL dell’archivio Git di Cloud Manager.
* Comandi Git pregenerati per aggiungere un remoto all’archivio Git e inviare il codice.

  ![Finestra dati archivio](assets/repository-info.png)

L’accesso alle informazioni degli [archivi privati](/help/managing-code/private-repositories.md) non è disponibile in Cloud Manager.

La funzione **Accedi a dati archivio** è visibile agli utenti con i ruoli **Sviluppatore** o **Responsabile dell’implementazione**.

**Per accedere alle informazioni dell’archivio dalla pagina Panoramica:**

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Dalla pagina **Panoramica del programma**, nella scheda **Pipeline**, fai clic su **Accedi a dati archivio**.

   ![Accedi a dati archivio nella scheda Pipeline](/help/managing-code/assets/pipelines-card2.png)

1. Per accedere alla password, devi generare una nuova password. Nella finestra di dialogo **Informazioni archivio**, seleziona **Genera password**.

1. Nella finestra di dialogo di conferma, seleziona **Genera password**.

1. A destra del campo **Password**, fai clic sull’![icona Copia](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) per copiare la password negli appunti.

   * La generazione di una password invalida la password precedente.
   * Cloud Manager non salverà la password. È tua responsabilità salvare la password in modo sicuro.
   * Poiché Cloud Manager non salva la password, se la si perde è necessario generarne una nuova.

   ![Copia password nella finestra di dialogo Informazioni archivio](/help/managing-code/assets/repository-copy-password.png)

Utilizzando queste credenziali, puoi clonare una copia locale dell’archivio, apportare modifiche all’archivio locale e, una volta pronto, inviare nuovamente eventuali modifiche al codice nell’archivio del codice remoto in Cloud Manager.

## Accesso alle informazioni dell’archivio dalla finestra Archivi {#repositories-window}

La funzione **Accedi a dati archivio** è disponibile anche nella pagina [**Archivi**](/help/managing-code/managing-repositories.md). Visualizza le stesse informazioni sull’accesso agli archivi gestiti da Adobe.

## Revoca di una password di accesso {#revoke-password}

Puoi revocare una password di accesso in qualsiasi momento.

Per farlo, [crea un ticket di supporto per questa richiesta](https://experienceleague.adobe.com/?support-solution=Experience+Manager&support-tab=home?lang=it#support). Al ticket viene assegnata un’alta priorità e di solito viene risolto entro un giorno.
