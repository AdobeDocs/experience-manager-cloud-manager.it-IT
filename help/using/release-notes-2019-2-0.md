---
title: Note sulla versione 2019.2.0
seo-title: Note sulla versione di AEM Cloud Manager per 2019.2.0
description: Segui questa pagina per ottenere informazioni sulla versione 2019.2.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2019.2.0 di AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Note sulla versione 2019.2.0 {#release-notes-for}

La [!UICONTROL Cloud Manager] versione 2019.2.0 aggiunge una nuova funzionalità di monitoraggio sistema. Questo consente ai clienti di visualizzare lo stato dei loro ambienti Adobe Managed Services a livello di sistema.


## Data di rilascio {#release-date}

La Data di rilascio per [!UICONTROL Cloud Manager] la versione 2019.2.0 è il 21 febbraio 2019.

## Novità {#whats-new}

* Nuova funzionalità di monitoraggio del sistema. Refer to [Monitor your Environments](monitor-your-environments.md) to learn more.
* Il modulo di dispatcher nei progetti generati mediante procedura guidata ora contiene un file Leggimi.
* L&#39;ordinamento di ordinamento dei problemi di scansione del codice è stato migliorato in base alla priorità del problema.
* Le istanze dello stage vengono ora sempre ripristinate al sistema di bilanciamento del carico, anche nel caso di un errore di distribuzione.
* Un nuovo ruolo per sviluppatori API è disponibile nell&#39;Admin Console, che consente agli utenti specifici di concedere l&#39;autorizzazione per creare integrazioni nella console I/O di Adobe. Per ulteriori informazioni, consulta [Gestione degli sviluppatori](https://www.adobe.com/go/aac_api_prod_learn) .
* La versione di Maven Archetype è stata aggiornata alla versione 16.
* La versione di Maven è stata aggiornata alla versione 3.6.0.

## Correzioni di bug {#bug-fixes}

* In alcuni casi, i pipeline non venivano eseguiti quando l&#39;ambiente di destinazione era in hosting in Azure.
* L&#39;ordinamento degli ambienti non era coerente.
* Il test delle prestazioni potrebbe non riuscire quando i percorsi di pagina sono stati identificati in un carattere virgola.
* Quando un&#39;esecuzione della pipeline è stata avviata dall&#39;interfaccia Web, il pulsante Indietro del browser non funziona correttamente.
* I collegamenti Ulteriori informazioni nella pagina Panoramica non aprono una nuova scheda.
* Quando si carica una miniatura di un programma, potrebbe non essere stata immediatamente visualizzata.
* In alcuni casi, la scansione del codice non riusciva a causa della configurazione specifica del progetto.
* Il collegamento Ulteriori informazioni sulla scheda Non Production Pipeline è andato nella posizione sbagliata.
* Quando un gate di qualità è stato ignorato, lo stato veniva visualizzato in modo non coerente.
* I clienti che utilizzano topologie di standby fredda ricevevano risultati errati per i test di sicurezza.
* Durante la creazione di un nuovo progetto mediante la procedura guidata, non era possibile creare un ramo contenente il trattino.

## Problemi noti {#known-issues}

* Quando i dati vengono aggiornati, tutte le serie nascoste non sono nascoste.
* I clienti che desiderano visualizzare i rapporti SLA esistenti dovranno navigare manualmente fino alla prossima versione.

   Per formulare questo URL, segui il pattern (`https://<Experience Cloud URL>/content/mac/<Experience Cloud Tenant>/managedservices/sla.html`), ad esempio se l&#39;URL per Experience Cloud è (`https://weretailprod.experiencecloud.adobe.com`), l&#39;URL dei rapporti SLA è (`https://weretailprod.experiencecloud.adobe.com/content/mac/weretailprod/managedservices/sla/html`).

   Questo problema dovrebbe essere risolto nella prossima release con la disponibilità di report SLA all&#39;interno [!UICONTROL Cloud Manager].
