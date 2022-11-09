---
title: Integrazione Git con Adobe Cloud Manager
description: Questa serie di video illustra la configurazione e l’integrazione di un archivio Git gestito dal cliente (on-premise) con Adobe Cloud Manager.
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
source-git-commit: 91e909273bf2b21d7f6413731923011915079e45
workflow-type: ht
source-wordcount: '347'
ht-degree: 100%

---


# Integrazione Git con Adobe Cloud Manager

Adobe Cloud Manager viene fornito con un unico archivio Git utilizzato per distribuire il codice utilizzando le pipeline CI/CD di Cloud Manager. È possibile utilizzare l’archivio Git di Cloud Manager preconfigurato oppure integrare un archivio Git on-premise o gestito dal cliente con Cloud Manager.

## Panoramica dell’integrazione Git

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

Questa serie di video esplora diversi casi d’uso relativi all’integrazione di un archivio Git gestito dal cliente con Cloud Manager.

* [Sincronizzazione iniziale](#initial-sync)
* [Strategia di base per la ramificazione](#branching-strategy)
* [Sviluppo dei rami delle funzioni](#feature-development)
* [Implementazione nell’ambiente di produzione](#production-deployment)
* [Sincronizzazione dei tag versione](#sync-tags)

Questa serie di video si rivolge a chi conosce già le basi di Git e del controllo del codice sorgente. Per ulteriori dettagli su Git, consulta le [risorse aggiuntive di seguito](#additional-resources).

I passaggi e le convenzioni di denominazione descritti in questa serie di video rappresentano alcune best practice per l’utilizzo di un archivio Git gestito dal cliente e di Cloud Manager. Le convenzioni e i flussi di lavoro rappresentati dovrranno essere adattati per i singoli team di sviluppo.

Per una panoramica completa di Cloud Manager, consulta il documento [Introduzione a Cloud Manager.](/help/introduction.md)

## Sincronizzazione iniziale {#initial-sync}

Primi passaggi per sincronizzare un archivio Git gestito dal cliente con l’archivio Git di Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## Strategia di diramazione di base {#branching-strategy}

Imposta una strategia di diramazione di base per sfruttare i vantaggi offerti dalle pipeline di [produzione](/help/using/production-pipelines.md) e [non di produzione](/help/using/non-production-pipelines.md) di Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## Sviluppo di rami per caratteristiche {#feature-development}

Un ramo della funzione serve per isolare le modifiche apportate al codice in un archivio Git gestito dal cliente e sincronizzarle con l’archivio Git di Cloud Manager per utilizzare una pipeline non di produzione a scopi di test di qualità del codice e di convalida.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## Distribuzione di produzione {#production-deployment}

Prepara il codice per una versione di produzione in un archivio Git gestito dal cliente e sincronizzalo con l’archivio Git di Cloud Manager per la distribuzione in ambienti di staging e produzione.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## Sincronizzazione dei tag versione {#sync-tags}

Sincronizza i tag di versione da un archivio Git di Cloud Manager in un archivio Git gestito dal cliente per fornire visibilità relativa al codice distribuito negli ambienti di staging e produzione.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## Risorse aggiuntive {#additional-resources}

* [Introduzione a Cloud Manager](/help/introduction.md)
* [Risorse GitHub](https://try.github.io)
* [Tutorial Atlassian Git](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Scheda di riferimento rapido di Git](https://education.github.com/git-cheat-sheet-education.pdf)
