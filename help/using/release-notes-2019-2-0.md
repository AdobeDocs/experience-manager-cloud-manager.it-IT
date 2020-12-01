---
title: Note sulla versione 2019.2.0
seo-title: Note sulla versione di AEM Cloud Manager per la versione 2019.2.0
description: Segui questa pagina per ottenere informazioni sulla versione 2019.2.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni su AEM Cloud Manager Release 2019.2.0.
translation-type: tm+mt
source-git-commit: 98395c4413b1b6bfbb3a565388ffa32dc3880dff
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Note sulla versione 2019.2.0 {#release-notes-for}

La versione [!UICONTROL Cloud Manager] 2019.2.0 aggiunge una nuova funzionalità di monitoraggio del sistema. Questo consente ai clienti di visualizzare lo stato dei propri ambienti Adobe Managed Services a livello di sistema.


## Data di rilascio {#release-date}

La data di rilascio per la versione [!UICONTROL Cloud Manager] 2019.2.0 è il 21 febbraio 2019.

## Novità {#whats-new}

* Nuova funzione di monitoraggio del sistema. Per ulteriori informazioni, fare riferimento a [Monitorare gli ambienti](monitor-your-environments.md).
* Il modulo dispatcher nei progetti generati dalla procedura guidata ora contiene un file README.
* È stato migliorato l&#39;ordinamento dei problemi di scansione del codice in base alla priorità del problema.
* Le istanze dello stage ora vengono sempre ripristinate al sistema di bilanciamento del carico anche in caso di errore di distribuzione.
* Nel Admin Console  è disponibile un nuovo ruolo per sviluppatori API che consente a utenti specifici di ottenere l&#39;autorizzazione per creare integrazioni nella console Adobe I/O . Per ulteriori informazioni, fare riferimento a [Gestione sviluppatori](https://www.adobe.com/go/aac_api_prod_learn).
* La versione del Maven Archetype è stata aggiornata alla versione 16.
* La versione di Maven è stata aggiornata alla versione 3.6.0.

## Correzioni di bug {#bug-fixes}

* In alcune circostanze, le pipeline non venivano eseguite quando l&#39;ambiente di destinazione era ospitato in Azure.
* L&#39;ordine degli ambienti non era coerente.
* Il test delle prestazioni potrebbe non riuscire se i percorsi di pagina rilevati contenevano una virgola.
* Quando l&#39;esecuzione di una pipeline veniva avviata dall&#39;interfaccia utente Web, il pulsante Indietro del browser non funzionava correttamente.
* I collegamenti Ulteriori informazioni nella pagina Panoramica non aprivano una nuova scheda.
* Durante il caricamento di una miniatura del programma, potrebbe non essere stata immediatamente visibile.
* In alcuni casi, la scansione del codice non è riuscita a causa della configurazione specifica del progetto.
* Il collegamento Ulteriori informazioni sulla scheda Non produzione Pipelines è andato nella posizione sbagliata.
* Quando un cancello di qualità veniva ignorato, lo stato veniva visualizzato in modo non coerente.
* I clienti che utilizzano topologie di standby a freddo hanno ricevuto risultati non corretti per i test di sicurezza.
* Durante la creazione di un nuovo progetto tramite la procedura guidata, non era possibile creare un ramo contenente il carattere trattino.

## Problemi noti {#known-issues}

* Quando si aggiornano i dati di monitoraggio, tutte le serie nascoste non vengono nascoste.
* I clienti che desiderano visualizzare i rapporti SLA esistenti dovranno spostarsi manualmente fino alla prossima release.

   Per formulare questo URL, seguire il pattern (`https://<Experience Cloud URL>/content/mac/<Experience Cloud Tenant>/managedservices/sla.html`), ad esempio, se l&#39;URL per il Experience Cloud  è (`https://weretailprod.experiencecloud.adobe.com`), l&#39;URL dei rapporti SLA è (`https://weretailprod.experiencecloud.adobe.com/content/mac/weretailprod/managedservices/sla/html`).

   Questo problema dovrebbe essere risolto nella prossima release con la disponibilità di rapporti SLA all&#39;interno di [!UICONTROL Cloud Manager].
