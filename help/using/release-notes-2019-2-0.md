---
title: Note sulla versione 2019.2.0
seo-title: Note sulla versione di AEM Cloud Manager 2019.2.0
description: Segui questa pagina per ottenere informazioni sulla versione 2019.2.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2019.2.0 di AEM Cloud Manager.
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 4%

---


# Note sulla versione 2019.2.0 {#release-notes-for}

La versione [!UICONTROL Cloud Manager] 2019.2.0 aggiunge una nuova funzionalità di monitoraggio del sistema. Questo consente ai clienti di visualizzare lo stato dei propri ambienti Adobe Managed Services a livello di sistema.


## Data di rilascio {#release-date}

La data di rilascio per la versione 2019.2.0 di [!UICONTROL Cloud Manager] è il 21 febbraio 2019.

## Novità {#whats-new}

* Nuova funzione di monitoraggio del sistema. Per ulteriori informazioni, consulta [Monitorare gli ambienti](monitor-your-environments.md) .
* Il modulo dispatcher nei progetti generati dalla procedura guidata ora contiene un file README.
* L’ordinamento dei problemi di scansione del codice è stato migliorato per corrispondere alla priorità del problema.
* Le istanze della fase ora vengono sempre ripristinate al load balancer anche in caso di errore di distribuzione.
* Nell’Admin Console è disponibile un nuovo ruolo Sviluppatore API che consente a utenti specifici di ottenere l’autorizzazione per creare integrazioni nella console Adobe I/O. Per ulteriori informazioni, consulta [Gestisci sviluppatori](https://www.adobe.com/go/aac_api_prod_learn) .
* La versione di Maven Archetype è stata aggiornata alla versione 16.
* La versione di Maven è stata aggiornata alla versione 3.6.0.

## Correzioni di bug {#bug-fixes}

* In alcuni casi, le pipeline non venivano eseguite quando l’ambiente di destinazione era ospitato in Azure.
* L&#39;ordinamento degli ambienti era incoerente.
* Il test delle prestazioni potrebbe non riuscire quando i percorsi di pagina rilevati contenevano un carattere virgola.
* Quando l’esecuzione di una pipeline veniva avviata dall’interfaccia utente web, il pulsante Indietro del browser non funzionava correttamente.
* I collegamenti Ulteriori informazioni nella pagina Panoramica non hanno aperto una nuova scheda.
* Durante il caricamento di una miniatura del programma, potrebbe non essere stata visibile immediatamente.
* In alcuni casi, la scansione del codice non è riuscita a causa della configurazione specifica del progetto.
* Il collegamento Ulteriori informazioni sulla scheda Pipelines non di produzione è andato nella posizione sbagliata.
* Quando un gate di qualità veniva ignorato, lo stato veniva visualizzato in modo incoerente.
* I clienti che utilizzano topologie di standby a freddo hanno ricevuto risultati non corretti per i test di sicurezza.
* Durante la creazione di un nuovo progetto tramite la procedura guidata, non è stato possibile creare un ramo contenente il carattere trattino.

## Problemi noti {#known-issues}

* Quando i dati di monitoraggio vengono aggiornati, tutte le serie nascoste vengono nascoste.
* I clienti che desiderano visualizzare i rapporti SLA esistenti dovranno navigare manualmente fino alla versione successiva.

   Per formulare questo URL, segui il pattern (`https://<Experience Cloud URL>/content/mac/<Experience Cloud Tenant>/managedservices/sla.html`), ad esempio, se l’URL dell’Experience Cloud è (`https://weretailprod.experiencecloud.adobe.com`), l’URL dei rapporti SLA è (`https://weretailprod.experiencecloud.adobe.com/content/mac/weretailprod/managedservices/sla/html`).

   Questo problema verrà risolto nella prossima versione con la disponibilità di rapporti SLA all’interno di [!UICONTROL Cloud Manager].
