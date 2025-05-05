---
title: Integrazione Git con Adobe Cloud Manager
description: Questa serie di video illustra la configurazione e l’integrazione di un archivio Git gestito dal cliente (on-premise) con Adobe Cloud Manager.
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
source-git-commit: 51bd685a17eb9d68b1ec8245e6167cab02101fc1
workflow-type: ht
source-wordcount: '331'
ht-degree: 100%

---


# Integrazione Git con Adobe Cloud Manager

Adobe Cloud Manager viene fornito con un unico archivio Git utilizzato per distribuire il codice attraverso le pipeline CI/CD di Cloud Manager. È possibile utilizzare l’archivio Git di Cloud Manager preconfigurato oppure integrare un archivio Git on-premise o gestito dal cliente con Cloud Manager.

## Panoramica dell’integrazione Git

>[!VIDEO](https://video.tv.adobe.com/v/37354?captions=ita)

Questa serie di video esplora diversi casi d’uso relativi all’integrazione di un archivio Git gestito dal cliente con Cloud Manager.

* [Sincronizzazione iniziale](#initial-sync)
* [Strategia di base per la ramificazione](#branching-strategy)
* [Sviluppo dei rami delle funzioni](#feature-development)
* [Implementazione nell’ambiente di produzione](#production-deployment)
* [Sincronizzazione dei tag della versione](#sync-tags)

Questa serie di video si rivolge a chi è già a conoscenza delle basi di Git e della gestione del codice sorgente. Per ulteriori informazioni su Git, consulta la sezione [Risorse aggiuntive di seguito](#additional-resources).

I passaggi e le convenzioni di denominazione descritti in questa serie di video rappresentano alcune best practice per l’utilizzo di un archivio Git gestito dal cliente e da Cloud Manager. Le convenzioni e i flussi di lavoro rappresentati dovranno essere adattati per i singoli team di sviluppo.

Per una panoramica completa di Cloud Manager, consulta [Introduzione a Cloud Manager](/help/introduction.md).

## Sincronizzazione iniziale {#initial-sync}

Primi passaggi per sincronizzare un archivio Git gestito dal cliente con l’archivio Git di Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/37352/?quality=12&captions=ita)

## Strategia di diramazione di base {#branching-strategy}

Imposta una strategia di ramificazione di base per sfruttare i vantaggi offerti dalle pipeline di [produzione](/help/using/production-pipelines.md) e [non di produzione](/help/using/non-production-pipelines.md) di Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/37351/?quality=12&captions=ita)

## Sviluppo di rami delle funzioni {#feature-development}

Usa un ramo della funzione per isolare le modifiche apportate al codice in un archivio Git gestito dal cliente e sincronizzale con l’archivio Git di Cloud Manager, per utilizzare una pipeline di non produzione a scopi di test di qualità del codice e di convalida.

>[!VIDEO](https://video.tv.adobe.com/v/37349/?quality=12&captions=ita)

## Distribuzione in produzione {#production-deployment}

Prepara il codice per una versione di produzione in un archivio Git gestito dal cliente e sincronizzalo con l’archivio Git di Cloud Manager, per la distribuzione negli ambienti di staging e di produzione.

>[!VIDEO](https://video.tv.adobe.com/v/37348/?quality=12&captions=ita)

## Sincronizzare i tag della versione {#sync-tags}

Puoi sincronizzare i tag della versione da un archivio Git di Cloud Manager a un archivio Git gestito dal cliente. Questa funzionalità fornisce visibilità sul codice distribuito negli ambienti di staging e di produzione.

>[!VIDEO](https://video.tv.adobe.com/v/37346/?quality=12&captions=ita)

## Risorse aggiuntive {#additional-resources}

* [Introduzione a Cloud Manager](/help/introduction.md)
* [Risorse GitHub](https://docs.github.com/en/get-started/getting-started-with-git/set-up-git)
* [Tutorial Atlassian Git](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Scheda di riferimento rapido di Git](https://education.github.com/git-cheat-sheet-education.pdf)
