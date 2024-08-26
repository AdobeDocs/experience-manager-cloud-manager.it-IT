---
title: Integrazione Git con Adobe Cloud Manager
description: Questa serie di video illustra la configurazione e l’integrazione di un archivio Git gestito dal cliente (on-premise) con Adobe Cloud Manager.
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 17%

---


# Integrazione Git con Adobe Cloud Manager

Adobe Cloud Manager viene fornito con un singolo archivio Git utilizzato per distribuire il codice utilizzando le pipeline CI/CD di Cloud Manager. Puoi utilizzare l’archivio Git Cloud Manager preconfigurato oppure integrare un archivio Git on-premise o gestito dal cliente con Cloud Manager.

## Panoramica dell’integrazione Git

>[!VIDEO](https://video.tv.adobe.com/v/28710/) (3 minuti, 11 secondi)

Questa serie di video esplora diversi casi d’uso relativi all’integrazione di un archivio Git gestito dal cliente con Cloud Manager.

* [Sincronizzazione iniziale](#initial-sync)
* [Strategia di base per la ramificazione](#branching-strategy)
* [Sviluppo dei rami delle funzioni](#feature-development)
* [Implementazione nell’ambiente di produzione](#production-deployment)
* [Sincronizzazione dei tag della versione](#sync-tags)

Questa serie di video presuppone una conoscenza di base di Git e della gestione del controllo del codice sorgente. Per ulteriori dettagli su Git, vedi [risorse aggiuntive di seguito](#additional-resources).

I passaggi e le convenzioni di denominazione descritti in questa serie di video rappresentano alcune best practice per l’utilizzo di un archivio Git gestito dal cliente e di Cloud Manager. Le convenzioni e i flussi di lavoro rappresentati dovrranno essere adattati per i singoli team di sviluppo.

Per una panoramica completa di Cloud Manager, consulta [Introduzione a Cloud Manager](/help/introduction.md).

## Sincronizzazione iniziale {#initial-sync}

Primi passaggi per sincronizzare un archivio Git gestito dal cliente con l’archivio Git di Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12) (8 minuti)

## Strategia di diramazione di base {#branching-strategy}

Imposta una strategia di diramazione di base per sfruttare le [pipeline di produzione](/help/using/production-pipelines.md) e le [pipeline non di produzione](/help/using/non-production-pipelines.md) di Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12) (3 minuti, 48 secondi)

## Sviluppo di rami di funzioni {#feature-development}

Utilizza un ramo della funzione per isolare le modifiche al codice in un archivio Git gestito dal cliente e sincronizzalo con l’archivio Git di Cloud Manager per utilizzare una pipeline non di produzione per testare la qualità del codice e la convalida.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12) (9 minuti)

## Distribuzione di produzione {#production-deployment}

Prepara il codice per una versione di produzione in un archivio Git gestito dal cliente e sincronizzalo con l’archivio Git di Cloud Manager per la distribuzione in ambienti di staging e produzione.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12) (6 minuti, 6 secondi)

## Sincronizzazione dei tag della versione {#sync-tags}

Puoi sincronizzare i tag della versione da un archivio Git di Cloud Manager a un archivio Git gestito dal cliente. Questa funzionalità fornisce visibilità sul codice distribuito negli ambienti di staging e produzione.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12) (2 minuti, 57 secondi)

## Risorse aggiuntive {#additional-resources}

* [Introduzione a Cloud Manager](/help/introduction.md)
* [Risorse GitHub](https://docs.github.com/en/get-started/getting-started-with-git/set-up-git)
* [Tutorial Atlassian Git](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Scheda di riferimento rapido di Git](https://education.github.com/git-cheat-sheet-education.pdf)
