---
title: Notifiche
description: Scopri in che modo Cloud Manager notifica gli eventi importanti.
exl-id: cfd5655f-2d2c-4304-b25c-6cdffe7ff64c
TQID: https://experienceleague.adobe.com/WBAHeIAH1XL6oVy342wLaUAoAHkUoN1AbcAl2Erkte4
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 65b260abe417925f26d647fb9857d32c30455f9b
workflow-type: tm+mt
source-wordcount: 562
ht-degree: 52%

---

# Notifiche {#notifications}

Scopri in che modo Cloud Manager notifica gli eventi importanti.

## Notifiche in Cloud Manager {#cloud-manager-notifications}

Le notifiche vengono inviate quando una pipeline di produzione viene avviata e completata (con successo o senza successo) durante una distribuzione di produzione. Nonché al raggiungimento dei passaggi **Approvazione diretta** e **Pianificato**. Queste notifiche vengono inviate tramite il sistema di notifica di [!UICONTROL Experience Cloud].

>[!NOTE]
>
>Le notifiche di approvazione e pianificate vengono inviate solo agli utenti nei ruoli **Proprietario business**, **Responsabile del programma** e **Responsabile della distribuzione**.

Le notifiche vengono visualizzate in una barra laterale in [!UICONTROL Cloud Manager] e in tutto Adobe [!UICONTROL Experience Cloud].

L’icona a forma di campana nell’intestazione mostra un indicatore quando ricevi nuove notifiche.

![Icona delle notifiche](/help/assets/notifications-bell-badged.png)

Fai clic sull’icona a forma di campana per aprire la barra laterale e visualizzare le notifiche. La scheda **Notifiche** nella barra laterale elenca le notifiche più recenti, ad esempio le conferme di distribuzione. Le notifiche riguardano i tuoi ambienti.

![Barra laterale delle notifiche](/help/assets/notifications-activities.png)

La scheda **Annunci** include annunci di prodotti Adobe. Gli annunci forniscono informazioni sul prodotto.

![Barra laterale delle notifiche](/help/assets/notificaitons-announcements.png)

Fai clic su una notifica o un annuncio per visualizzarne i dettagli. Le notifiche collegate ad attività come le distribuzioni di pipeline consentono di passare ai dettagli di tale attività, ad esempio alla finestra di esecuzione della pipeline.

Fai clic sull&#39;opzione **Visualizza tutto** nella parte inferiore del pannello per visualizzare tutti gli annunci presenti nella casella in entrata.

Fai clic sull&#39;opzione **Contrassegna tutto come letto** nella parte inferiore del pannello per contrassegnare tutte le notifiche non lette come lette e rimuovere il contrassegno dall&#39;icona a forma di campana.

## Configurazione delle notifiche {#configuration}

Puoi personalizzare le modalità di ricezione delle notifiche e le notifiche ricevute.

Fai clic sull’icona a forma di ingranaggio nella parte superiore della barra laterale delle notifiche.

![Icona delle impostazioni di notifica](/help/assets/notifications-configuration.png)

Viene visualizzata la finestra **Preferenze di Experience Cloud** in cui è possibile definire le sottoscrizioni alle notifiche e le modalità di ricezione delle notifiche.

### Sottoscrizioni {#subscriptions}

Gli abbonamenti definiscono per quali prodotti ricevi le notifiche e per quali notifiche ricevi.

![Iscrizioni alle notifiche](/help/assets/notifications-subscriptions.png)

Per impostazione predefinita, riceverai tutte le notifiche per tutti i prodotti. Per definire i tipi di notifiche ricevute per un prodotto, fai clic su **Personalizza** accanto a esso.

![Personalizzazione dell’iscrizione alle notifiche](/help/assets/notifications-subscriptions-customize.png)

### Priorità {#priority}

Gli avvisi prioritari sono contrassegnati con un tag **ALTA**. Puoi configurarli per inviarli esclusivamente come notifiche. Nella sezione **Priorità** è possibile definire quali categorie si qualificano come notifiche prioritarie.

![Priorità di notifica](/help/assets/notifications-priority.png)

Utilizza l’elenco a discesa per aggiungere all’elenco delle categorie idonee come priorità. Fai clic sull’icona Elimina accanto ai nomi delle categorie per eliminarli.

### Avvisi {#alerts}

Gli avvisi vengono visualizzati nell’angolo in alto a destra della finestra per alcuni secondi. Utilizza la sezione **Avvisi** per definire per quali notifiche ricevi gli avvisi.

![Avvisi di notifica](/help/assets/notifications-alerts.png)

È possibile definire il comportamento degli avvisi.

* **Mostra avvisi per** - Definisce i tipi di notifiche che attivano gli avvisi.
* **Gli avvisi rimangono sullo schermo fino a quando non vengono ignorati** - Controlla se gli avvisi persistono a meno che non vengano attivamente ignorati.
* **Durata** - Definisce per quanto tempo l&#39;avviso rimane sullo schermo se non si è scelto che rimanga sullo schermo.

### E-mail {#emails}

Per impostazione predefinita, le notifiche sono disponibili nell’interfaccia utente delle soluzioni Adobe [!UICONTROL Experience Cloud]. Per ricevere queste notifiche tramite e-mail, accetta nella sezione **E-mail**.

![E-mail di notifica](/help/assets/notifications-emails.png)

Per impostazione predefinita, non vengono inviate e-mail. Puoi scegliere di ricevere le e-mail come segue:

* Istantanea
* Giornaliero
* Settimanale

Quando viene selezionato **Notifiche istantanee**, le e-mail vengono inviate immediatamente per ogni notifica. Con **Riepilogo giornaliero** e **Riepilogo settimanale** puoi scegliere quando inviare il riepilogo giornaliero e quello settimanale.
