---
title: Note sulla versione 2020.4.0
seo-title: Note sulla versione di AEM Cloud Manager per la versione 2020.4.0
description: Segui questa pagina per ottenere informazioni sulla versione 2020.4.0 di Cloud Manager
seo-description: Segui questa pagina per ottenere informazioni su AEM Cloud Manager Release 2020.4.0
translation-type: tm+mt
source-git-commit: 278858465592482449080fedc3c0165805db223d
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Note sulla versione 2020.4.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per la versione [!UICONTROL Cloud Manager] 2020.4.0.

## Data di rilascio {#release-date}

La data di rilascio per la versione [!UICONTROL Cloud Manager] 2020.4.0 è il 09 aprile 2020.

## Novità {#whats-new}

* Modifiche alla pagina di panoramica di Navigazione Cloud Manager per consentire agli utenti di modificare o cambiare il programma.
* Sono state apportate modifiche per consentire all’utente di modificare il programma dalla scheda del programma nella pagina di destinazione di Cloud Manager.
* È stato introdotto il nuovo stato di pipeline “**In esecuzione**”, visualizzato per l’ambiente a cui la pipeline è associata.
* Sono stati introdotti miglioramenti nella pagina di esecuzione della pipeline, che ne facilitano la comprensione. Questo include la visualizzazione del nome della pipeline (solo non di produzione) e del tipo e un contrassegno per indicare se lo stato della pipeline è In corso/Annullato/Non riuscito.
* Il processo utilizzato per generare password git è stato reso più flessibile per affrontare eventuali problemi nel livello di servizio sottostante.

## Correzioni di bug {#bug-fixes}

* Talvolta i dati di monitoraggio potrebbero essere visualizzati in modo errato o non in base a variazioni minori nei valori tecnici.
* La configurazione Maven utilizzata nel contenitore di build è stata aggiornata per evitare deadlock durante il download dei metadati dell’artefatto.
* Il processo di verifica delle prestazioni di Risorse non è stato in grado di decifrare la password AEM, causando errori di verifica.
* Alcune topologie con istanze in standby potrebbero presentare falsi negativi nei test di sicurezza.
* Se l’ambiente di visualizzazione conteneva un’istanza arrestata, il passaggio di test di protezione potrebbe non riuscire.
* Le notifiche di Experience Cloud non venivano ricevute in modo costante.

