---
title: Note sulla versione 2018.9.0
seo-title: Note sulla versione di AEM Cloud Manager per la versione 2018.9.0
description: Segui questa pagina per ottenere informazioni sulla versione 2018.9.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni su AEM Cloud Manager Release 2018.9.0.
uuid: 3af5808f-828f-4846-bee4-1e62194b48ad
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 85a1dcf3-2eef-4ba8-b4d1-09e4a88c7bd0
translation-type: tm+mt
source-git-commit: ace032fbb26235d87d61552a11996ec2bb42abce
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Note sulla versione 2018.9.0 {#release-notes-for}

La versione [!UICONTROL Cloud Manager] 2018.9.0 aggiunge il supporto per un&#39;API basata su Adobe I/O , compresi gli eventi, per l&#39;integrazione della pipeline CI/CD di [!UICONTROL Cloud Manager] con altri sistemi. Viene inoltre avviata la riscrittura del livello dell’interfaccia utente in React (Reazione).

## Data di rilascio {#release-date}

La data di rilascio per la versione [!UICONTROL Cloud Manager] 2018.9.0 è il 01 novembre 2018.

## Novità {#whats-new}

* **Pipeline**  CI/CD - Nuovo sistema API ed evento per l&#39;integrazione della pipeline CI/CD con  [!UICONTROL Cloud Manager]altri sistemi. Per ulteriori informazioni, consultare la documentazione relativa alle [!UICONTROL Cloud Manager] API (https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html).

* **Interfaccia** : introduzione di un nuovo livello dell&#39;interfaccia utente più reattivo.

## Correzioni di bug {#bug-fixes}

* In [!UICONTROL Cloud Manager] 2018.8.0, le durate della pagina Attività venivano elencate in minuti e ore, ma tali informazioni non venivano riportate nell&#39;intestazione della tabella.
* In rare occasioni, i clienti non erano in grado di avviare la nuova procedura guidata di progetto dell’applicazione.
* L&#39;etichetta del pulsante nella nuova finestra di dialogo guidata del progetto dell&#39;applicazione era fuorviante.
* In alcuni casi, facendo clic sul pulsante Dettagli nella pagina Attività si passa alla pagina Panoramica.
* Alcune circostanze rare e impreviste causavano la mancanza di una scheda nella pagina Panoramica.
* L’icona Risorse è stata visualizzata nella pagina Elenco programmi per tutti i clienti.
* In caso di errori back-end, talvolta l&#39;esecuzione della pipeline apparirebbe mantenuta nel passaggio *Validate*.
* In alcune circostanze, la lunghezza della descrizione del programma è stata calcolata erroneamente.

## Problemi noti {#known-issues}

* I rami creati con la Creazione guidata progetto applicazione non possono contenere trattini.
* La barra laterale delle notifiche dell&#39;Adobe  [!UICONTROL Experience Cloud] potrebbe non caricare le notifiche in modo coerente. Le notifiche, tuttavia, sono visibili nell&#39;Adobe  [!UICONTROL Experience Cloud] e, se configurato, saranno comunque inviate tramite e-mail.

