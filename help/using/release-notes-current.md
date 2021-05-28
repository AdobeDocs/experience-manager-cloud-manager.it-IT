---
title: Note sulla versione 2021.5.0
description: Segui questa pagina per ottenere informazioni sulla versione 2021.5.0 di Cloud Manager
feature: Informazioni sulla versione
source-git-commit: 3f17f252d89a1753c9cb121461b048f619d28415
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 5%

---

# Note sulla versione 2021.5.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per [!UICONTROL Cloud Manager] la versione 2021.5.0.

>[!NOTE]
>Fai riferimento a [Note sulla versione corrente](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access) per visualizzare le ultime note sulla versione per Cloud Manager in AEM come Cloud Service.

## Data di rilascio {#release-date}

La data di rilascio per la versione 2021.5.0 è il 6 maggio 2021.
[!UICONTROL Cloud Manager]
La prossima versione è prevista per il 10 giugno 2021.

## Novità {#whats-new}

* La regola di qualità PackageOverlaps ora rileva i casi in cui lo stesso pacchetto è stato distribuito più volte, ovvero in più posizioni incorporate, nello stesso set di pacchetti distribuito.

* L’endpoint dell’archivio nell’API pubblica ora include l’URL Git.

* Nel flusso di lavoro Modifica programma , all’utente sarà consentito impostare solo valori KPI non decimali.

* Sono stati risolti gli errori intermittenti rilevati durante il push del codice a Git di Adobe.

* L&#39;esperienza del programma Edit è stata aggiornata.

## Correzioni di bug {#bug-fixes}

* Invece di rimuovere le variabili &quot;eliminate&quot;, le variabili delle pipeline API le contrassegnavano solo con lo stato &quot;ELIMINATO&quot;.

* Alcuni problemi di qualità del tipo di odore del codice hanno avuto un impatto errato sul rating di affidabilità.

* Quando è stata avviata l’esecuzione di una pipeline tra la mezzanotte e l’1:00 UTC, la versione dell’artefatto generata da Cloud Manager non era garantita come maggiore di una versione creata il giorno precedente.

* Alcuni clienti di Adobe Managed Services (AMS) non sono stati in grado di creare nuovi progetti in Adobe I/O Developer Console utilizzando l’API Cloud Manager.
