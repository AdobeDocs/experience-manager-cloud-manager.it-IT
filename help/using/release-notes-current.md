---
title: Note sulla versione 2020.4.0
seo-title: Note sulla versione di AEM Cloud Manager per la versione 2020.4.0
description: Segui questa pagina per ottenere informazioni sulla versione 2020.4.0 di Cloud Manager
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2020.4.0 di AEM Cloud Manager
translation-type: tm+mt
source-git-commit: e7da473a22bec1d3d9b3d39bf654af0c596fe86d

---

# Note sulla versione 2020.4.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per la [!UICONTROL Cloud Manager] release 2020.4.0.

## Release Date {#release-date}

La Data di rilascio per la [!UICONTROL Cloud Manager] versione 2020.4.0 è il 09 aprile 2020.

## Novità {#whats-new}

* Modifiche alla pagina di panoramica di Navigazione CM per consentire agli utenti di modificare o cambiare il programma dalla pagina di panoramica di CM.
* Modifiche per consentire all&#39;utente di modificare il programma dalla scheda del programma sulla pagina di destinazione di CM.
* Nuovo stato di tubazione &quot;Pipeline Running&quot; visualizzato rispetto all&#39;ambiente a cui è associato.
* Miglioramenti alla comprensibilità della pagina di esecuzione della pipeline. Questo include la visualizzazione del nome della pipeline (solo non di produzione) e del tipo e un contrassegno per indicare se lo stato della pipeline è In corso/Annullato/Non riuscito.
* Il processo utilizzato per generare password git è stato reso più flessibile ai problemi nel livello di servizio sottostante.

## Correzioni di bug {#bug-fixes}

* Talvolta i dati di monitoraggio potrebbero essere visualizzati in modo errato o non in base a variazioni minori nei valori tecnici.
* La configurazione Maven utilizzata nel contenitore di build è stata aggiornata per evitare il blocco critico durante il download dei metadati dell&#39;artifact.
* Il processo di verifica delle prestazioni di Risorse non è stato in grado di decifrare la password di AEM, causando errori di verifica.
* Alcune topologie con istanze in standby potrebbero presentare falsi negativi nei test di sicurezza.
* Se l’ambiente di visualizzazione conteneva un’istanza arrestata, il passaggio di test di protezione potrebbe non riuscire.
* Notifiche Experience Cloud non ricevute in modo coerente.

