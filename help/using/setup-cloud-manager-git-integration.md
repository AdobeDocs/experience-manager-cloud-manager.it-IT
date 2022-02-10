---
title: Integrazione Git con Adobe Cloud Manager
description: Serie video che illustra la configurazione e l’integrazione di un archivio Git gestito dal cliente (on-premise) con Adobe Cloud Manager.
seo-title: Git Integration with Adobe Cloud Manager
seo-description: A video series that walks through the set up and integration of a customer-managed (on-premise) git repository with Adobe Cloud Manager.
feature: Git Repositories
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
source-git-commit: 71d44c7e3673ca62fcd2203ecc0bc4ed9fa22002
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 4%

---

# Integrazione Git con Adobe Cloud Manager

Adobe Cloud Manager viene fornito con un unico archivio Git utilizzato per distribuire il codice utilizzando le pipeline CI/CD di Cloud Manager. I clienti possono utilizzare l’archivio Git di Cloud Manager preconfigurato. I clienti possono anche scegliere di integrare un **gestito dal cliente** archivio Git con Cloud Manager.

## Panoramica dell’integrazione Git

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

Questa serie video illustra diversi casi d’uso relativi all’integrazione di un archivio Git gestito dal cliente con Cloud Manager, tra cui:

* [Sincronizzazione iniziale](#initial-sync)
* [Strategia di diramazione di base](#branching-strategy)
* [Sviluppo di diramazioni](#feature-development)
* [Distribuzione di produzione](#production-deployment)
* [Sincronizzazione dei tag di rilascio](#sync-tags)

Per una panoramica completa, consulta la sezione [Guida utente di Cloud Manager.](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html?lang=it) La serie video si basa su una conoscenza di base della gestione di Git e del controllo del codice sorgente. Consulta la sezione [risorse aggiuntive di seguito](#additional-resources) per ulteriori dettagli su git.

>[!NOTE]
>
> I passaggi e le convenzioni di denominazione descritti in questa serie video rappresentano alcune best practice per l’utilizzo di un archivio Git gestito dal cliente e di Cloud Manager. Si prevede che le convenzioni e i flussi di lavoro descritti saranno adattati per i singoli team di sviluppo.

## Sincronizzazione iniziale {#initial-sync}

Primi passaggi per sincronizzare un archivio Git gestito dal cliente con l’archivio Git di Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## Strategia di diramazione di base {#branching-strategy}

Imposta una strategia di branding di base per sfruttare i vantaggi offerti da Cloud Manager [produzione](configuring-production-pipelines.md) e [gasdotti non di produzione.](configuring-non-production-pipelines.md)

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## Sviluppo di diramazioni {#feature-development}

Utilizza un ramo di funzionalità per isolare le modifiche di codice in un archivio Git gestito dal cliente e sincronizzalo con l’archivio Git di Cloud Manager per utilizzare una pipeline non di produzione per il test di qualità del codice e di convalida.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## Distribuzione di produzione {#production-deployment}

Prepara il codice per una versione di produzione in un archivio Git gestito dal cliente e sincronizza con l’archivio Git di Cloud Manager per distribuire in ambienti di staging e produzione.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## Sincronizzazione dei tag di rilascio {#sync-tags}

Sincronizza i tag di rilascio da un archivio Git di Cloud Manager in un archivio Git gestito dal cliente per fornire visibilità sul codice distribuito negli ambienti di stage e produzione.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## Risorse aggiuntive {#additional-resources}

* [Documentazione di Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)
* [Risorse GitHub](https://try.github.io)
* [Tutorials Git Atlassian](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Foglio di riferimento Git](https://education.github.com/git-cheat-sheet-education.pdf)
