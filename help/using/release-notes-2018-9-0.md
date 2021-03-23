---
title: Note sulla versione 2018.9.0
seo-title: Note sulla versione di AEM Cloud Manager 2018.9.0
description: Segui questa pagina per ottenere informazioni sulla versione 2018.9.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2018.9.0 di AEM Cloud Manager.
uuid: 3af5808f-828f-4846-bee4-1e62194b48ad
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 85a1dcf3-2eef-4ba8-b4d1-09e4a88c7bd0
feature: Informazioni sulla versione
translation-type: tm+mt
source-git-commit: c5d32d49782c899d013fcc60b9c4d2b67e9350ae
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 9%

---


# Note sulla versione 2018.9.0 {#release-notes-for}

La versione [!UICONTROL Cloud Manager] 2018.9.0 aggiunge il supporto per un’API basata su Adobe I/O, compresi gli eventi, per l’integrazione della pipeline CI/CD di [!UICONTROL Cloud Manager] con altri sistemi. Questa versione avvia anche la riscrittura del livello dell’interfaccia utente in React.

## Data di rilascio {#release-date}

La data di rilascio per la versione 2018.9.0 di [!UICONTROL Cloud Manager] è il 10 novembre 2018.

## Novità {#whats-new}

* **Pipeline CI/CD**  - Nuovo sistema API ed evento per l’integrazione della pipeline CI/CD  [!UICONTROL Cloud Manager]con altri sistemi. Per ulteriori informazioni, consulta la [!UICONTROL Cloud Manager] documentazione API (https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html) .

* **Interfaccia utente** : introduzione di un nuovo livello di interfaccia utente più reattivo.

## Correzioni di bug {#bug-fixes}

* In [!UICONTROL Cloud Manager] 2018.8.0, le durate della pagina Attività sono state elencate in minuti e ore, ma tali informazioni non sono state riportate nell’intestazione della tabella.
* In alcune rare occasioni, i clienti non erano in grado di avviare la nuova procedura guidata di progetto dell’applicazione.
* L&#39;etichetta del pulsante nella finestra di dialogo della procedura guidata per il nuovo progetto dell&#39;applicazione era fuorviante.
* In alcuni casi, facendo clic sul pulsante Dettagli nella pagina Attività si passa alla pagina Panoramica .
* Alcune circostanze rare e inaspettate causavano la mancanza di una scheda nella pagina Panoramica .
* L’icona Risorse veniva visualizzata nella pagina Elenco programmi per tutti i clienti.
* In caso di errori di back-end, a volte l’esecuzione di una pipeline sembrava rimanere nel passaggio *Validate* .
* In alcune circostanze, la lunghezza della descrizione del programma è stata calcolata in modo errato.

## Problemi noti {#known-issues}

* I rami creati con Creazione guidata progetto applicazione non possono contenere trattini.
* La barra laterale delle notifiche dell’Adobe [!UICONTROL Experience Cloud] potrebbe non caricare le notifiche in modo coerente. Le notifiche, tuttavia, sono visibili nell’Adobe [!UICONTROL Experience Cloud] e, se configurate, saranno comunque inviate tramite e-mail.

