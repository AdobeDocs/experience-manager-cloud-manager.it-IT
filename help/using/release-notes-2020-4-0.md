---
title: Note sulla versione 2020.4.0
seo-title: Note sulla versione di AEM Cloud Manager 2020.4.0
description: Segui questa pagina per ottenere informazioni sulla versione 2020.4.0 di Cloud Manager
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2020.4.0 di AEM Cloud Manager
feature: Informazioni sulla versione
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 38%

---

# Note sulla versione 2020.4.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per [!UICONTROL Cloud Manager] la versione 2020.4.0.

## Data di rilascio {#release-date}

La data di rilascio per la versione 2020.4.0 è il 9 aprile 2020.[!UICONTROL Cloud Manager]

## Novità {#whats-new}

* Sono state apportate modifiche alla pagina di panoramica di navigation Cloud Manager per consentire all’utente di modificare o cambiare il programma.
* Sono state apportate modifiche per consentire all’utente di modificare il programma dalla scheda del programma nella pagina di destinazione di Cloud Manager.
* È stato introdotto il nuovo stato di pipeline “**In esecuzione**”, visualizzato per l’ambiente a cui la pipeline è associata.
* Sono stati introdotti miglioramenti nella pagina di esecuzione della pipeline, che ne facilitano la comprensione. Ciò include la visualizzazione del nome della pipeline (solo per pipeline non di produzione) e del tipo e un contrassegno per indicare se lo stato della pipeline è In corso/Annullato/Non riuscito.
* Il processo utilizzato per generare password git è stato reso più flessibile per affrontare eventuali problemi nel livello di servizio sottostante.

## Correzioni di bug {#bug-fixes}

* Talvolta i dati di monitoraggio potrebbero essere visualizzati in modo errato o non in base a variazioni minori dei valori tecnici.
* La configurazione Maven utilizzata nel contenitore di build è stata aggiornata per evitare deadlock durante il download dei metadati dell’artefatto.
* Talvolta, il processo di test delle prestazioni di Assets non era in grado di decifrare la password AEM, causando errori di test.
* Alcune topologie con istanze di standby potrebbero avere falsi negativi nel test di sicurezza.
* Se l’ambiente stage conteneva un’istanza interrotta, il passaggio del test di sicurezza potrebbe non riuscire.
* Le notifiche di Experience Cloud non venivano ricevute in modo costante.

