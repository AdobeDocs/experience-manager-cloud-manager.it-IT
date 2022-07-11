---
title: Integrazione Git con Adobe Cloud Manager
description: Questa serie video illustra la configurazione e l’integrazione di un archivio Git gestito dal cliente (on-premise) con Adobe Cloud Manager.
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
source-git-commit: 91e909273bf2b21d7f6413731923011915079e45
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---


# Integrazione Git con Adobe Cloud Manager

Adobe Cloud Manager viene fornito con un unico archivio Git utilizzato per distribuire il codice utilizzando le pipeline CI/CD di Cloud Manager. È possibile utilizzare l’archivio Git di Cloud Manager preconfigurato oppure è possibile integrare un archivio Git on-premise o gestito dai clienti con Cloud Manager.

## Panoramica dell’integrazione Git

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

Questa serie video esplora diversi casi d’uso relativi all’integrazione di un archivio Git gestito dal cliente con Cloud Manager.

* [Sincronizzazione iniziale](#initial-sync)
* [Strategia di diramazione di base](#branching-strategy)
* [Sviluppo di diramazioni](#feature-development)
* [Distribuzione di produzione](#production-deployment)
* [Sincronizzazione dei tag di rilascio](#sync-tags)

Questa serie video si basa su una conoscenza di base della gestione di Git e del controllo del codice sorgente. Consulta la sezione [risorse aggiuntive di seguito](#additional-resources) per ulteriori dettagli su git.

I passaggi e le convenzioni di denominazione descritti in questa serie video rappresentano alcune best practice per l’utilizzo di un archivio Git gestito dal cliente e di Cloud Manager. Si prevede che le convenzioni e i flussi di lavoro descritti saranno adattati per i singoli team di sviluppo.

Per una panoramica completa di Cloud Manager, consulta il documento [Introduzione a Cloud Manager.](/help/introduction.md)

## Sincronizzazione iniziale {#initial-sync}

Primi passaggi per la sincronizzazione di un archivio Git gestito dal cliente con l’archivio Git di Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## Strategia di diramazione di base {#branching-strategy}

Imposta una strategia di branding di base per sfruttare i vantaggi offerti da Cloud Manager [produzione](/help/using/production-pipelines.md) e [gasdotti non di produzione.](/help/using/non-production-pipelines.md)

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## Sviluppo di diramazioni {#feature-development}

Utilizza un ramo di funzionalità per isolare le modifiche di codice in un archivio Git gestito dal cliente e sincronizzalo con l’archivio Git di Cloud Manager per utilizzare una pipeline non di produzione per il test di qualità del codice e di convalida.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## Distribuzione di produzione {#production-deployment}

Prepara il codice per una versione di produzione in un archivio Git gestito dal cliente e sincronizza con l’archivio Git di Cloud Manager per distribuire in ambienti di staging e produzione.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## Sincronizzazione dei tag di rilascio {#sync-tags}

Sincronizza i tag di rilascio da un archivio Git di Cloud Manager in un archivio Git gestito dal cliente per fornire visibilità sul codice distribuito negli ambienti di staging e produzione.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## Risorse aggiuntive {#additional-resources}

* [Introduzione a Cloud Manager](/help/introduction.md)
* [Risorse GitHub](https://try.github.io)
* [Tutorials Git Atlassian](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Foglio di riferimento Git](https://education.github.com/git-cheat-sheet-education.pdf)
