---
title: Note sulla versione 2020.11.0
seo-title: Note sulla versione di AEM Cloud Manager 2020.11.0
description: Segui questa pagina per ottenere informazioni sulla versione 2020.11.0 di Cloud Manager
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2020.11.0 di AEM Cloud Manager
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 8%

---

# Note sulla versione 2020.11.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per [!UICONTROL Cloud Manager] la versione 2020.11.0.

## Data di rilascio {#release-date}

La data di rilascio per la versione 2020.11.0 di [!UICONTROL Cloud Manager] è il 12 novembre 2020.

## Novità {#whats-new}

* La scheda **Informazioni** in Cloud Manager viene aggiornata con le nuove immagini nell’interfaccia utente.

## Correzioni di bug {#bug-fixes}

* Alcuni errori di distribuzione causati dal cliente verranno ora visualizzati esplicitamente nei registri di distribuzione.

* Il caricamento delle dipendenze eseguito prima dell’esecuzione della build richiede il download di un plug-in Maven.

* Il collegamento dal piè di pagina di Cloud Manager per selezionare una lingua passerà ora alla posizione corretta.

* A volte, durante la scansione del codice, il processo SonarQube non veniva avviato. Questo verrà rilevato automaticamente e verrà tentato un riavvio.

* Durante il processo di ricerca per indicizzazione del sito utilizzato nei test delle prestazioni, le richieste che scadono nei primi tre livelli di attraversamento di profondità verranno ritentate automaticamente.