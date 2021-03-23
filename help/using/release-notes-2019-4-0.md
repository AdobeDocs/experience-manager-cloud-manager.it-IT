---
title: Note sulla versione 2019.4.0
seo-title: Note sulla versione di AEM Cloud Manager 2019.4.0
description: Segui questa pagina per ottenere informazioni sulla versione 2019.4.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2019.4.0 di AEM Cloud Manager.
feature: Informazioni sulla versione
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 7%

---


# Note sulla versione 2019.4.0 {#release-notes-for}

La versione [!UICONTROL Cloud Manager] 2019.4.0 non contiene modifiche funzionali significative. Per ulteriori informazioni, consulta le sezioni seguenti.

## Data di rilascio {#release-date}

La data di rilascio per la versione 2019.4.0 di [!UICONTROL Cloud Manager] è il 18 aprile 2019.

## Novità {#whats-new}

* L’interfaccia utente di Cloud Manager è ora disponibile in inglese, francese, tedesco e giapponese.
* I passaggi di distribuzione ora contengono il processo attualmente in esecuzione, ovvero, quando un backup è in esecuzione, i pacchetti sono in fase di installazione e i load balancer sono in fase di riconfigurazione

## Correzioni di bug {#bug-fixes}

* L’approccio di distribuzione utilizzato per le modifiche a Dispatcher è stato migliorato per gestire ulteriori casi d’uso.
* Alcuni tipi di dimensioni dell&#39;istanza non venivano visualizzati correttamente nella pagina Ambienti .
* Le regole di qualità del codice relative alle dipendenze CQBP-84 hanno prodotto falsi positivi per le librerie di Adobi incorporate, come i componenti core WCM e Asset Share Commons.
* Il pulsante dei dettagli per il passaggio di scansione del codice era attivato quando i dettagli non erano disponibili.
* Il messaggio di errore che compare quando si specifica un valore non valido per l&#39;indicatore KPI della visualizzazione della pagina al minuto presenta un limite inferiore errato.
* La categoria di distribuzione in una pipeline non di produzione è stata capitalizzata in modo errato.
* Nella scheda dell’invito all’azione della pagina **Panoramica** era presente testo non corretto quando l’archivio Git non era configurato correttamente.

## Problemi noti {#known-issues}

* I valori SLA potrebbero essere arrotondati in modo errato.
