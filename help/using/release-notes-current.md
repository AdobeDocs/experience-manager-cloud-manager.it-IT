---
title: Note sulla versione 2021.2.0
seo-title: Note sulla versione di AEM Cloud Manager per la versione 2021.2.0
description: Segui questa pagina per ottenere informazioni sulla release 2021.2.0 di Cloud Manager
seo-description: Segui questa pagina per ottenere informazioni su AEM Cloud Manager Release 2021.2.0
translation-type: tm+mt
source-git-commit: d956c7a2d3833e357920a9602e4f5a5b37f2c98a
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 4%

---

# Note sulla versione 2021.2.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per la versione [!UICONTROL Cloud Manager] 2021.2.0.

## Data di rilascio {#release-date}

La data di rilascio per la versione [!UICONTROL Cloud Manager] 2021.2.0 è l&#39;11 febbraio 2021.

## Novità {#whats-new}

* Il tipo di archivio AEM progetto utilizzato nella creazione di progetti e sandbox è stato aggiornato alla versione 25.

* L&#39;elenco delle API obsolete identificate durante la scansione del codice è stato ridefinito in modo da includere classi e metodi aggiuntivi obsoleti nelle versioni SDK dell&#39;Cloud Service più recente.

* Le distribuzioni di produzione ora vengono distribuite in parallelo alle istanze di pubblicazione e dispatcher associate.

* Profilo SonarQube per Cloud Manager aggiornato per rimuovere la regola Sonar `squid:S2142`. Ciò non entrerà più in conflitto con i controlli di interruzione del thread.

* Le proprietà impostate nei file `pom.xml` del cliente con il prefisso sonar verranno ora rimosse in modo dinamico per evitare errori di creazione e scansione di qualità.

* Sono state aggiunte ulteriori regole sulla qualità del codice per i problemi di compatibilità del Cloud Service.

## Correzioni di bug {#bug-fixes}

* In alcuni casi, la pipeline CI/CD (distribuzione) non è riuscita durante una fase di test delle prestazioni a causa di un contenitore che esegue il test di caricamento che ha rilevato un errore.

* In alcuni casi, il contenitore del test di caricamento potrebbe riportare l&#39;esecuzione come non riuscita anche se si verifica una sola eccezione. L&#39;errore verrà segnalato solo se il processo di test non può essere ripristinato.

* Alcune incongruenze tra i casing tra il modo in cui sono stati memorizzati i nomi dell&#39;ambiente potrebbero causare errori di test delle prestazioni.

* Alcuni guasti della pipeline sono stati erroneamente riportati come errori della pipeline.