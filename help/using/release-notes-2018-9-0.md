---
title: Note sulla versione 2018.9.0
seo-title: Note sulla versione di AEM Cloud Manager per 2018.9.0
description: Segui questa pagina per ottenere informazioni sulla versione 2018.9.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2018.9.0 di AEM Cloud Manager.
uuid: 3 af 5808 f -828 f -4846-bee 4-1 e 62194 b 48 ad
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: note sulla versione
discoiquuid: 85 a 1 dcf 3-2 eef -4 ba 8-b 4 d 1-09 e 4 a 88 c 7 bd 0
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Note sulla versione 2018.9.0 {#release-notes-for}

La [!UICONTROL Cloud Manager] versione 2018.9.0 aggiunge il supporto per un&#39;API Adobe I/O basata su I, compresi Eventi, per integrare [!UICONTROL Cloud Manager]la pipeline CI/CD con altri sistemi. Inizia anche la riscrittura del livello dell&#39;interfaccia utente in Reagisci.

## Data di rilascio {#release-date}

La Data di rilascio per [!UICONTROL Cloud Manager] la versione 2018.9.0 è il 01 novembre 2018.

## Novità {#whats-new}

* **Pipeline CI/CD** - Nuova API e sistema evento per integrare [!UICONTROL Cloud Manager]la pipeline CI/CD con altri sistemi. Per ulteriori informazioni, consultate la documentazione [!UICONTROL Cloud Manager] API (https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html).

* **Interfaccia utente** - Introduzione al nuovo livello dell&#39;interfaccia utente più reattivo e di prestazioni.

## Correzioni di bug {#bug-fixes}

* Nella [!UICONTROL Cloud Manager] 2018.8.0, le durate della pagina Attività venivano elencate in minuti e ore, ma tali informazioni non venivano riportate nell&#39;intestazione della tabella.
* In rare occasioni, i clienti non erano in grado di avviare la nuova procedura guidata di progetto dell&#39;applicazione.
* L&#39;etichetta del pulsante nella finestra di dialogo guidata per il progetto applicazione risultava fuorviante.
* In alcuni casi, facendo clic sul pulsante Dettagli dalla pagina Attività si passerà alla pagina Panoramica.
* Alcune circostanze rare e impreviste generavano una scheda mancante nella pagina Panoramica.
* L&#39;icona Risorse è stata visualizzata nella pagina Elenco programma per tutti i clienti.
* In caso di errori di back-end, a volte un&#39;esecuzione della pipeline restava nel passaggio *Validate* .
* In alcune circostanze, la lunghezza della descrizione del programma era determinata.

## Problemi noti {#known-issues}

* I rami creati utilizzando la procedura guidata di creazione dei progetti non possono contenere trattini.
* La barra laterale [!UICONTROL Experience Cloud] Notifica Adobe non può caricare le notifiche in modo coerente. Le notifiche, tuttavia, sono visibili in Adobe [!UICONTROL Experience Cloud] e, se configurate, continueranno a essere inviate tramite e-mail.

