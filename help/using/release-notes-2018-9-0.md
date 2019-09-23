---
title: Note sulla versione 2018.9.0
seo-title: Note sulla versione di AEM Cloud Manager per la versione 2018.9.0
description: Segui questa pagina per ottenere informazioni sulla versione 2018.9.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2018.9.0 di AEM Cloud Manager.
uuid: 3af5808f-828f-4846-bee4-1e62194b48ad
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: note sulla versione
discoiquuid: 85a1dcf3-2eef-4ba8-b4d1-09e4a88c7bd0
translation-type: tm+mt
source-git-commit: 949d3cf0239a02875ba4ad1888e081f104dec2e2

---


# Note sulla versione 2018.9.0 {#release-notes-for}

La release [!UICONTROL Cloud Manager] 2018.9.0 aggiunge il supporto per un'API basata su I/O di Adobe, compresi gli eventi, per l'integrazione della pipeline CI/CD con [!UICONTROL Cloud Manager]altri sistemi. Viene inoltre avviata la riscrittura del livello dell’interfaccia utente in React (Reazione).

## Data di rilascio {#release-date}

La Data di rilascio per la [!UICONTROL Cloud Manager] versione 2018.9.0 è il 10 novembre 2018.

## Novità {#whats-new}

* **Pipeline** CI/CD - Nuovo sistema API ed evento per l'integrazione della pipeline CI/CD con [!UICONTROL Cloud Manager]altri sistemi. Per ulteriori informazioni, consultate la documentazione [!UICONTROL Cloud Manager] API (https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html).

* **Interfaccia** : introduzione di un nuovo livello dell’interfaccia utente più reattivo e performante.

## Correzioni dei bug {#bug-fixes}

* Nel [!UICONTROL Cloud Manager] 2018.8.0, le durate della pagina Attività venivano elencate in minuti e ore, ma tali informazioni non venivano riportate nell'intestazione della tabella.
* In rare occasioni, i clienti non erano in grado di avviare la nuova procedura guidata di progetto dell’applicazione.
* L'etichetta del pulsante nella nuova finestra di dialogo guidata del progetto dell'applicazione era fuorviante.
* In alcuni casi, facendo clic sul pulsante Dettagli nella pagina Attività si passa alla pagina Panoramica.
* Alcune circostanze rare e impreviste causavano la mancanza di una scheda nella pagina Panoramica.
* L’icona Risorse è stata visualizzata nella pagina Elenco programmi per tutti i clienti.
* In caso di errori back-end, talvolta l'esecuzione di una pipeline sembrerebbe rimanere nel passaggio *Validate* .
* In alcune circostanze, la lunghezza della descrizione del programma è stata calcolata erroneamente.

## Problemi noti {#known-issues}

* I rami creati con la Creazione guidata progetto applicazione non possono contenere trattini.
* La barra laterale delle [!UICONTROL Experience Cloud] notifiche Adobe potrebbe non caricare le notifiche in modo coerente. Le notifiche, tuttavia, sono visibili in Adobe [!UICONTROL Experience Cloud] e, se configurate, saranno comunque inviate tramite e-mail.

