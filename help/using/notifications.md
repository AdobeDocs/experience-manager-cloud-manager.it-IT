---
title: Notifiche
description: Scopri in che modo Cloud Manager notifica gli eventi importanti.
exl-id: cfd5655f-2d2c-4304-b25c-6cdffe7ff64c
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 94%

---


# Notifiche {#notifications}

Scopri in che modo Cloud Manager notifica gli eventi importanti.

## Notifiche in Cloud Manager {#cloud-manager-notifications}

[!UICONTROL Cloud Manager] invia notifiche all&#39;avvio e al completamento (riusciti o non riusciti) di una pipeline di produzione, all&#39;inizio di una distribuzione di produzione e al raggiungimento dei passaggi **Approvazione Go-Live** e **Pianificato**. Queste notifiche vengono inviate tramite il sistema di notifica di [!UICONTROL Experience Cloud].

>[!NOTE]
>
>Le notifiche di approvazione e pianificate vengono inviate solo agli utenti nei ruoli **Proprietario business**, **Responsabile del programma** e **Responsabile della distribuzione**.

Le notifiche vengono visualizzate in una barra laterale all’interno di [!UICONTROL Cloud Manager] e in Adobe [!UICONTROL Experience Cloud].

Quando ricevi nuove notifiche, l’icona a forma di campana nell’intestazione viene contrassegnata.

![Icona delle notifiche](/help/assets/notifications-bell-badged.png)

Fai clic sull’icona a forma di campana per aprire la barra laterale e visualizzare le notifiche. La scheda **Notifiche** nella barra laterale elenca le notifiche più recenti, ad esempio le conferme di distribuzione. Le notifiche riguardano i tuoi ambienti.

![Barra laterale delle notifiche](/help/assets/notifications-activities.png)

La scheda **Annunci** include annunci di prodotti Adobe. Gli annunci riguardano il prodotto.

![Barra laterale delle notifiche](/help/assets/notificaitons-announcements.png)

Fai clic su una notifica o un annuncio per visualizzarne i dettagli. Le notifiche collegate ad attività come le distribuzioni di pipeline ti portano ai dettagli di quell’attività, ad esempio la finestra di esecuzione della pipeline.

Fai clic sull’opzione **Visualizza tutto** nella parte inferiore del pannello per visualizzare tutti gli annunci presenti nella casella in entrata.

Fai clic sull’opzione **Contrassegna tutto come letto** nella parte inferiore del pannello per contrassegnare tutte le notifiche non lette come lette e cancellare il contrassegno dell’icona della campana.

## Configurazione delle notifiche {#configuration}

Puoi personalizzare le modalità di ricezione delle notifiche e le notifiche ricevute.

Fai clic sull’icona a forma di ingranaggio nella parte superiore della barra laterale delle notifiche.

![Icona delle impostazioni di notifica](/help/assets/notifications-configuration.png)

Viene aperta la finestra **Preferenze di Experience Cloud**, che consente di definire le iscrizioni alle notifiche e le modalità di ricezione delle notifiche.

### Sottoscrizioni {#subscriptions}

Le iscrizioni definiscono per quali prodotti ricevi le notifiche e quali notifiche.

![Iscrizioni alle notifiche](/help/assets/notifications-subscriptions.png)

Per impostazione predefinita, riceverai tutte le notifiche per tutti i prodotti. Fai clic su **Personalizza** accanto a un prodotto per definire i tipi di notifiche ricevute per quel prodotto.

![Personalizzazione dell’iscrizione alle notifiche](/help/assets/notifications-subscriptions-customize.png)

### Priorità {#priority}

Gli avvisi prioritari saranno contrassegnati con un tag **ALTA** e possono essere configurati per essere ricevuti esclusivamente come avvisi. Nella sezione **Priorità** è possibile definire quali categorie si qualificano come notifiche prioritarie.

![Priorità di notifica](/help/assets/notifications-priority.png)

Utilizza l’elenco a discesa per aggiungere all’elenco delle categorie idonee come priorità. Fai clic sulla X accanto ai nomi delle categorie per rimuoverli.

### Avvisi {#alerts}

Gli avvisi vengono visualizzati nell’angolo in alto a destra della finestra per alcuni secondi. Utilizza la sezione **Avvisi** per definire le notifiche per le quali ricevi gli avvisi.

![Avvisi di notifica](/help/assets/notifications-alerts.png)

È possibile definire il comportamento degli avvisi.

* **Mostra avvisi per** - Definisce i tipi di notifiche che attivano gli avvisi
* **Gli avvisi dovrebbero rimanere sullo schermo fino a quando non li ignoro** - Controlla se gli avvisi devono persistere a meno che non vengano attivamente ignorati
* **Durata** - Definisce per quanto tempo l’avviso deve rimanere sullo schermo se non si è scelto che rimanga sullo schermo.

### E-mail {#emails}

Per impostazione predefinita, le notifiche sono disponibili nell’interfaccia utente delle soluzioni Adobe [!UICONTROL Experience Cloud]. Puoi anche optare per l’invio di queste notifiche tramite e-mail nella sezione **E-mail**.

![E-mail di notifica](/help/assets/notifications-emails.png)

Per impostazione predefinita non vengono inviate e-mail. Puoi scegliere di ricevere e-mail come:

* Istantanea
* Giornaliero
* Settimanale

Quando viene selezionato **Notifiche istantanee**, le e-mail vengono inviate immediatamente per ogni notifica. Con **Riepilogo giornaliero** e **Riepilogo settimanale** puoi scegliere quando inviare il riepilogo giornaliero e quello settimanale.
