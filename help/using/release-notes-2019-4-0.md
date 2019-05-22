---
title: Note sulla versione 2019.4.0
seo-title: Note sulla versione di AEM Cloud Manager per 2019.4.0
description: Segui questa pagina per ottenere informazioni sulla versione 2019.4.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2019.4.0 di AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 8031df1c1ce9d7fee4ef33de289c6952370b7589

---


# Note sulla versione 2019.4.0 {#release-notes-for}

La [!UICONTROL Cloud Manager] versione 2019.4.0 non contiene modifiche funzionali significative. Per ulteriori dettagli, seguite le sezioni riportate di seguito.

## Data di rilascio {#release-date}

La Data di rilascio per [!UICONTROL Cloud Manager] la versione 2019.4.0 è il 18 aprile 2019.

## Novità {#whats-new}

* L&#39;interfaccia utente di Experience Manager è ora disponibile in inglese, francese, tedesco e giapponese.
* I passaggi di distribuzione ora contengono il processo in esecuzione, ovvero quando un backup è in esecuzione, i pacchetti sono in fase di installazione e il sistema di bilanciamento del carico viene riconfigurato

## Correzioni di bug {#bug-fixes}

* L&#39;approccio di distribuzione utilizzato per le modifiche al dispatcher è stato migliorato per gestire altri casi d&#39;uso.
* Alcuni tipi di dimensioni dell&#39;istanza non venivano visualizzati correttamente nella pagina Ambienti.
* Le regole CQBP -84 per la qualità del codice hanno prodotto falsi positivi per librerie Adobe incorporate, ad esempio componenti core WCM e condivisione risorse.
* Il pulsante dei dettagli per il passaggio di scansione del codice era attivato quando i dettagli non erano disponibili.
* Il messaggio di errore durante la specificazione di un valore non valido per le visualizzazioni di pagina per minuto KPI ha un bordo inferiore errato.
* La categoria di distribuzione su un pipeline non di produzione è stata composta in modo errato.
* La chiamata alla scheda di azione nella pagina **Panoramica** aveva un testo errato quando l&#39;archivio git non era configurato correttamente.

## Problemi noti {#known-issues}

* I valori SLA possono essere arrotondati in modo errato.
