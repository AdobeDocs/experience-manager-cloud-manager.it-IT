---
title: Archivio del codice sorgente
description: Scopri l’archivio Git fornito per ciascun programma in Cloud Manager.
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 4c977cdfbef438fdabd90ee104d98887f2467b49
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 20%

---


# Archivio del codice Source {#source-code-repository}

Scopri l’archivio Git fornito per ciascun programma in Cloud Manager.

## Archivio Cloud Manager {#cloud-manager-repository}

Il tuo abbonamento a [!UICONTROL AEM Managed Services] include un archivio del codice sorgente fornito e gestito da Adobe. A ciascun programma viene assegnato un archivio Git singolo e univoco, in cui il codice associato viene memorizzato e protetto.

Come best practice, utilizza sempre l’archivio Git di Cloud Manager, che si presenta vuoto senza rami configurati o progetti di esempio. Cloud Manager fornisce un token di accesso privato per il proprio archivio Git, consentendo di utilizzare qualsiasi client Git per creare rami, gestire il codice, recuperare la cronologia del commit e altro ancora.

Per ulteriori informazioni su come impostare i rami in Git, consulta [Configurazione dei rami di rilascio](/help/getting-started/configuring-branches.md).

Per ulteriori informazioni su come utilizzare l&#39;archivio Git di Cloud Manager con la pipeline CI/CD, consulta [Configurare le pipeline di produzione](/help/using/production-pipelines.md) e [Configurare le pipeline non di produzione](/help/using/non-production-pipelines.md).

## Archivio on-premise {#on-premise-repository}

È possibile disporre di un archivio Git esistente e continuare a utilizzarlo, nel qual caso è possibile utilizzare la funzione Git per più archivi remoti. Lo sviluppo quotidiano continuerebbe a verificarsi nell’archivio Git. Quando un ramo della versione è pronto per la distribuzione in produzione, puoi inviare il codice più recente all’archivio Git di Cloud Manager e attivare la pipeline CI/CD di Cloud Manager.

Per visualizzare i comandi Git comuni, vedere [Scheda di riferimento Git](https://education.github.com/git-cheat-sheet-education.pdf).
