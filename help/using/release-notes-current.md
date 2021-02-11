---
title: Note sulla versione 2021.2.0
seo-title: Note sulla versione di AEM Cloud Manager per la versione 2021.2.0
description: Segui questa pagina per ottenere informazioni sulla release 2021.2.0 di Cloud Manager
seo-description: Segui questa pagina per ottenere informazioni su AEM Cloud Manager Release 2021.2.0
translation-type: tm+mt
source-git-commit: 88b17f05a577b5c46b5b352d7340228353b49a38
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 5%

---

# Note sulla versione 2020.12.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per la versione [!UICONTROL Cloud Manager] 2021.2.0.

## Data di rilascio {#release-date}

La data di rilascio per la versione [!UICONTROL Cloud Manager] 2021.2.0 è l&#39;11 febbraio 2021.

## Novità {#whats-new}

* Il tipo di archivio AEM progetto utilizzato nella creazione di progetti e sandbox è stato aggiornato alla versione 25.

* L&#39;elenco delle API obsolete identificate durante la scansione del codice è stato ridefinito in modo da includere classi e metodi aggiuntivi obsoleti nelle versioni SDK dell&#39;Cloud Service più recente.

* Le distribuzioni di produzione ora vengono distribuite in parallelo alle istanze di pubblicazione e dispatcher associate.

* Profilo SonarQube per Cloud Manager aggiornato per rimuovere Sonar rule squid:S2142. Non si verificherà più un conflitto con i controlli di interruzione del thread

* Le proprietà impostate nei file pom.xml del cliente hanno il prefisso sonar e ora verranno rimosse in modo dinamico per evitare errori di creazione e scansione di qualità.

## Correzioni di bug {#bug-fixes}

* In alcuni casi, la pipeline CI/CD (distribuzione) non è riuscita durante una fase di test delle prestazioni a causa di un contenitore che esegue il test di caricamento che ha rilevato un errore.

* In alcuni casi, il contenitore del test di caricamento potrebbe riportare l&#39;esecuzione come non riuscita anche se si verifica una sola eccezione. L&#39;errore verrà segnalato solo se il processo di test non può essere ripristinato.

* Alcune incongruenze tra i casing tra il modo in cui sono stati memorizzati i nomi dell&#39;ambiente potrebbero causare errori di test delle prestazioni.

* Alcuni guasti della pipeline sono stati erroneamente riportati come errori della pipeline.