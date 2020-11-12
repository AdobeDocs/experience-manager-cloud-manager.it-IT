---
title: Note sulla versione 2020.11.0
seo-title: AEM Cloud Manager - Note sulla versione 2020.11.0
description: Segui questa pagina per ottenere informazioni sulla versione 2020.11.0 di Cloud Manager
seo-description: Segui questa pagina per ottenere informazioni su AEM Cloud Manager Release 2020.11.0
translation-type: tm+mt
source-git-commit: 30d782f5a095b1b07ec4f2039def9ba30a559325
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 7%

---

# Note sulla versione 2020.11.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per la [!UICONTROL Cloud Manager] release 2020.11.0.

## Data di rilascio {#release-date}

La Data di rilascio per la [!UICONTROL Cloud Manager] versione 2020.11.0 è il 12 novembre 2020.

## Novità {#whats-new}

* La scheda **Informazioni** in Cloud Manager viene aggiornata con le nuove immagini nell&#39;interfaccia utente.

## Correzioni di bug {#bug-fixes}

* Alcuni errori di distribuzione causati dal cliente verranno ora visualizzati esplicitamente nei registri di distribuzione.

* Il caricamento delle dipendenze eseguite prima dell&#39;esecuzione della creazione richiede il download di un plug-in Maven.

* Il collegamento dal piè di pagina di Cloud Manager per selezionare una lingua ora passerà alla posizione corretta.

* A volte, durante la scansione del codice, il processo SonarQube non veniva avviato. Ora verrà rilevato automaticamente e verrà tentato un riavvio.

* Durante il processo di ricerca per indicizzazione del sito utilizzato per il test delle prestazioni, le richieste per le quali il timeout nei primi tre livelli di attraversamento della profondità verranno automaticamente ritentate.