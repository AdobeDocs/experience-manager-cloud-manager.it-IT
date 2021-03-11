---
title: Note sulla versione 2021.2.0
seo-title: Note sulla versione di AEM Cloud Manager 2021.2.0
description: Segui questa pagina per ottenere informazioni sulla versione 2021.2.0 di Cloud Manager
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2021.2.0 di AEM Cloud Manager
translation-type: tm+mt
source-git-commit: b5233e1932888b515d8dc26a6493cbd26686bc3c
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 4%

---

# Note sulla versione 2021.2.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per [!UICONTROL Cloud Manager] la versione 2021.2.0.

## Data di rilascio {#release-date}

La data di rilascio per la versione 2021.2.0 di [!UICONTROL Cloud Manager] è l’11 febbraio 2021.

## Novità {#whats-new}

* L’Archetipo di progetto AEM utilizzato nella creazione di progetti e sandbox è stato aggiornato alla versione 25.

* L’elenco delle API obsolete identificate durante la scansione del codice è stato perfezionato per includere classi e metodi aggiuntivi obsoleti nelle ultime versioni dell’SDK di Cloud Service.

* Le distribuzioni di produzione ora vengono distribuite alle istanze di pubblicazione e dispatcher associate in parallelo.

* Profilo SonarQube per Cloud Manager aggiornato per rimuovere la regola Sonar `squid:S2142`. Questo non entrerà più in conflitto con i controlli di interruzione del thread.

* Le proprietà impostate nei file `pom.xml` del cliente con prefisso sonar verranno rimosse in modo dinamico per evitare errori di creazione e di scansione della qualità.

* Sono state aggiunte regole aggiuntive per la qualità del codice per risolvere i problemi relativi alla compatibilità dei Cloud Service.

## Correzioni di bug {#bug-fixes}

* Talvolta, la pipeline CI/CD (distribuzione) non è riuscita durante un passaggio di test delle prestazioni a causa di un contenitore che esegue il test di caricamento che ha rilevato un errore.

* Talvolta, il contenitore di test di carico può segnalare l’esecuzione come non riuscita anche se si verifica una sola eccezione. L&#39;errore viene segnalato solo se non è possibile ripristinare il processo di test.

* Alcune mancate corrispondenze tra i casing tra il modo in cui i nomi dell’ambiente sono stati memorizzati porterebbero a errori di test delle prestazioni.

* Alcuni errori di pipeline non sono stati segnalati correttamente come errori di pipeline.