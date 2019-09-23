---
title: Note sulla versione 2019.2.0
seo-title: Note sulla versione di AEM Cloud Manager 2019.2.0
description: Segui questa pagina per ottenere informazioni sulla versione 2019.2.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2019.2.0 di AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 98395c4413b1b6bfbb3a565388ffa32dc3880dff

---


# Note sulla versione 2019.2.0 {#release-notes-for}

La release [!UICONTROL Cloud Manager] 2019.2.0 aggiunge una nuova funzionalità di monitoraggio del sistema. Questo consente ai clienti di visualizzare lo stato dei propri ambienti Adobe Managed Services a livello di sistema.


## Data di rilascio {#release-date}

La data di rilascio per la [!UICONTROL Cloud Manager] versione 2019.2.0 è il 21 febbraio 2019.

## Novità {#whats-new}

* Nuova funzione di monitoraggio del sistema. Per ulteriori informazioni, consulta [Monitorare gli ambienti](monitor-your-environments.md) .
* Il modulo dispatcher nei progetti generati dalla procedura guidata ora contiene un file README.
* È stato migliorato l'ordinamento dei problemi di scansione del codice in base alla priorità del problema.
* Le istanze dello stage ora vengono sempre ripristinate al sistema di bilanciamento del carico anche in caso di errore di distribuzione.
* Nell’Admin Console è disponibile un nuovo ruolo per sviluppatori API che consente a utenti specifici di ottenere l’autorizzazione per creare integrazioni nella console Adobe I/O. Per ulteriori informazioni, consulta [Gestione sviluppatori](https://www.adobe.com/go/aac_api_prod_learn) .
* La versione del Maven Archetype è stata aggiornata alla versione 16.
* La versione di Maven è stata aggiornata alla versione 3.6.0.

## Correzioni dei bug {#bug-fixes}

* In alcune circostanze, le pipeline non venivano eseguite quando l'ambiente di destinazione era ospitato in Azure.
* L'ordine degli ambienti non era coerente.
* Il test delle prestazioni potrebbe non riuscire se i percorsi di pagina rilevati contenevano una virgola.
* Quando l'esecuzione di una pipeline veniva avviata dall'interfaccia utente Web, il pulsante Indietro del browser non funzionava correttamente.
* I collegamenti Ulteriori informazioni nella pagina Panoramica non aprivano una nuova scheda.
* Durante il caricamento di una miniatura del programma, potrebbe non essere stata immediatamente visibile.
* In alcuni casi, la scansione del codice non è riuscita a causa della configurazione specifica del progetto.
* Il collegamento Ulteriori informazioni sulla scheda Non produzione Pipelines è andato nella posizione sbagliata.
* Quando un cancello di qualità veniva ignorato, lo stato veniva visualizzato in modo non coerente.
* I clienti che utilizzano topologie di standby a freddo hanno ricevuto risultati non corretti per i test di sicurezza.
* Durante la creazione di un nuovo progetto tramite la procedura guidata, non era possibile creare un ramo contenente il carattere trattino.

## Problemi noti {#known-issues}

* When monitoring data is refreshed, any hidden series are unhidden.
* Customers wishing to view their existing SLA reports will need to manually navigate until the next release.

   To formulate this URL, follow the pattern (), for example, if URL for your Experience Cloud is (), then your SLA reports URL is ().`https://<Experience Cloud URL>/content/mac/<Experience Cloud Tenant>/managedservices/sla.html``https://weretailprod.experiencecloud.adobe.com``https://weretailprod.experiencecloud.adobe.com/content/mac/weretailprod/managedservices/sla/html`

   This is expected to be resolved in the next release with the availability of SLA reports inside [!UICONTROL Cloud Manager].
