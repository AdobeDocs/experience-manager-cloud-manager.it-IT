---
title: Note sulla versione 2019.4.0
seo-title: Note sulla versione di AEM Cloud Manager per la versione 2019.4.0
description: Segui questa pagina per ottenere informazioni sulla versione 2019.4.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni su AEM Cloud Manager Release 2019.4.0.
translation-type: tm+mt
source-git-commit: b368c46c2a9f40d0c3867db6eb2a333bd71fe22a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Note sulla versione 2019.4.0 {#release-notes-for}

La versione [!UICONTROL Cloud Manager] 2019.4.0 non contiene modifiche funzionali significative. Seguite le sezioni riportate di seguito per ulteriori dettagli.

## Data di rilascio {#release-date}

La data di rilascio per la versione [!UICONTROL Cloud Manager] 2019.4.0 è il 18 aprile 2019.

## Novità {#whats-new}

* L&#39;interfaccia utente di Cloud Manager è ora disponibile in inglese, francese, tedesco e giapponese.
* I passaggi di distribuzione ora contengono il processo in esecuzione, ovvero, quando è in esecuzione un backup, i pacchetti vengono installati e i bilanciatori di carico vengono riconfigurati

## Correzioni di bug {#bug-fixes}

* L’approccio di distribuzione utilizzato per le modifiche del dispatcher è stato migliorato per gestire ulteriori casi di utilizzo.
* Alcuni tipi di dimensioni dell&#39;istanza non venivano visualizzati correttamente nella pagina Ambienti.
* Le regole di qualità del codice relative alle dipendenze CQBP-84 generavano falsi positivi per le librerie di Adobi  incorporate, come i componenti core di WCM e i commons di condivisione delle risorse.
* Il pulsante dei dettagli per la fase di scansione del codice era attivato quando i dettagli non erano disponibili.
* Il messaggio di errore che veniva visualizzato quando si specificava un valore non valido per l&#39;indicatore KPI delle visualizzazioni pagina per minuto conteneva un limite inferiore errato.
* La categoria di distribuzione in una pipeline non di produzione è stata capitalizzata in modo errato.
* La chiamata alla scheda azione sulla pagina **Panoramica** conteneva testo non corretto quando il repository git non era configurato correttamente.

## Problemi noti {#known-issues}

* I valori SLA potrebbero essere arrotondati in modo errato.
