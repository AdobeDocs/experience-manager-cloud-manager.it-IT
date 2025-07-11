---
title: Aggiornamenti del Service Pack per gli ambienti di sviluppo - versione beta privata
description: Scopri come avviare gli aggiornamenti del service pack per gli ambienti di sviluppo tramite l’interfaccia utente di Cloud Manager.
hide: true
hidefromtoc: true
exl-id: 996a8eee-843f-45a6-8f7a-31ea405c2b32
source-git-commit: b2a14280e84bb934053968b0e93e33d30fb6086a
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 1%

---

# Aggiornamenti dei Service Pack per gli ambienti di sviluppo (versione beta privata) {#stage-prod-only}

Scopri come avviare gli aggiornamenti del service pack per gli ambienti di sviluppo tramite l’interfaccia utente di Cloud Manager.

>[!NOTE]
>
>Questa funzionalità è disponibile solo per [il programma beta privato](/help/release-notes/current.md#beta-program).

## Panoramica {#service-pack-updates-overview}

Puoi avviare gli aggiornamenti del service pack per gli ambienti di sviluppo tramite l’interfaccia utente di Cloud Manager. Questa funzione consente di verificare la disponibilità di aggiornamenti dei service pack e di gestire il processo di installazione in modo indipendente.

**Vantaggi chiave**

* Offre un maggiore controllo sugli aggiornamenti dei service pack di Cloud Manager.
* Riduce la dipendenza dai Customer Success Engineer (CSE) di Adobe per l’avvio degli aggiornamenti.
* Tiene traccia dell’intero processo di aggiornamento tramite Cloud Manager.

**Limitazioni correnti**

* L’opzione di aggiornamento self-service è disponibile solo per gli ambienti di sviluppo.
* Per gli aggiornamenti non riusciti è disponibile una segnalazione di errori limitata.
* In caso di problemi, contatta i CSE di Adobe per ulteriori indagini.

## Avviare un aggiornamento del service pack

1. Accedi a Cloud Manager con i privilegi di Responsabile della distribuzione.
1. Passare alla pagina Panoramica programma.
1. Nella sezione Ambienti, fai clic sull&#39;icona ![Altro, puntini di sospensione](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).

   ![Verifica aggiornamento Service Pack nel menu a discesa](/help/using/assets/service-pack-check-for-updates.png)

1. Dal menu a discesa, fare clic su ![Apri in icona chiaro](https://spectrum.adobe.com/static/icons/workflow_18/Smock_OpenInLight_18_N.svg) **Controlla aggiornamenti** per cercare gli aggiornamenti dei Service Pack disponibili.

   ![Viene visualizzato un elenco degli aggiornamenti disponibili](/help/using/assets/service-pack-versions.png)

1. Fare clic sulla versione del service pack desiderata dall&#39;elenco.
1. Fare clic su **Aggiorna Service Pack** per avviare il processo di aggiornamento.
1. Nella finestra di dialogo di conferma, controlla i dettagli e conferma l’aggiornamento.

   Una volta confermata, il processo di installazione viene avviato e l’avanzamento può essere tracciato in Cloud Manager.

## Tracciare l’aggiornamento del service pack

Dopo aver avviato l’aggiornamento, puoi monitorare lo stato di avanzamento nella pagina Attività di Cloud Manager.

**Per tenere traccia dell&#39;aggiornamento del service pack:**

1. Dal dashboard di Cloud Manager, accedi alla pagina Attività.
1. Cercare la voce Service Pack Installation (Installazione Service Pack).

   ![Installazioni Service Pack](/help/using/assets/service-pack-installation.png)

1. Fai clic sulla voce per visualizzare gli aggiornamenti dettagliati sullo stato e sull’avanzamento, in modo analogo a quanto segue:

   ![Avanzamento dell&#39;installazione del service pack](/help/using/assets/service-pack-progression.png)

### Risoluzione dei problemi di installazione

* Se l&#39;installazione non riesce, Cloud Manager attiva automaticamente un rollback allo stato precedente.
* Se i problemi persistono, fai clic su **Scarica registro** per raccogliere i registri degli errori, quindi contatta il supporto Adobe per la risoluzione dei problemi.

## Approvare o rifiutare l&#39;esecuzione del service pack

Al termine dell&#39;installazione, per completare l&#39;aggiornamento è necessaria l&#39;approvazione o il rifiuto dell&#39;utente.

**Per approvare o rifiutare l&#39;esecuzione del Service Pack:**

1. Apri la pagina Attività in Cloud Manager.
1. Individuare la richiesta di approvazione in sospeso per l&#39;aggiornamento del service pack.

   ![Rifiuta o approva l&#39;aggiornamento del service pack](/help/using/assets/service-pack-reject-approve.png)

1. Effettua una delle operazioni seguenti:

   * Per completare l&#39;aggiornamento, fare clic su **Approva**.

   ![Approvazione del service pack](/help/using/assets/service-pack-approve.png)

   * Per annullare l&#39;aggiornamento, fare clic su **Rifiuta**.
L&#39;installazione del service pack è stata annullata e non sono state applicate modifiche.

   ![Rifiuto del service pack](/help/using/assets/service-pack-reject.png)
