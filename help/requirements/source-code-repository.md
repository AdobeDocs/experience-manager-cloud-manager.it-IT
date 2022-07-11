---
title: Archivio del codice sorgente
description: Scopri l’archivio Git fornito per ciascun programma in Cloud Manager.
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 2%

---


# Archivio del codice sorgente {#source-code-repository}

Scopri l’archivio Git fornito per ciascun programma in Cloud Manager.

## Archivio Cloud Manager {#cloud-manager-repository}

Le [!UICONTROL AEM Managed Services] La sottoscrizione include un archivio del codice sorgente predisposto e gestito da Adobe. A ciascun programma viene assegnato un archivio git singolo e univoco, in cui il codice associato verrà memorizzato e protetto.

Come best practice, utilizza sempre l’archivio Git di Cloud Manager, che viene vuoto senza rami configurati o progetti di esempio. Per utilizzare l’archivio Git di Cloud Manager, riceverai un token di accesso privato che ti consentirà di utilizzare qualsiasi client Git per creare rami, archiviare e recuperare il codice, elencare la cronologia del commit e così via.

Per ulteriori informazioni su come impostare i rami in git, consulta [Configurazione dei rami della versione.](/help/getting-started/configuring-branches.md)

Per ulteriori informazioni su come utilizzare l’archivio Git di Cloud Manager con la pipeline CI/CD, consulta i documenti [Configurare le pipeline di produzione](/help/using/production-pipelines.md) e [Configurazione di pipeline non di produzione](/help/using/non-production-pipelines.md) per saperne di più.

## Archivio on-premise {#on-premise-repository}

È possibile disporre di un archivio Git esistente e continuare a utilizzarlo, nel qual caso è possibile utilizzare la funzione Git per più archivi remoti. Lo sviluppo quotidiano continuerebbe a verificarsi nell’archivio Git. Quando un ramo di rilascio è pronto per una distribuzione in produzione, puoi inviare il codice più recente all’archivio Git di Cloud Manager e attivare la pipeline CI/CD di Cloud Manager.

Per visualizzare i comandi git comuni, consulta la sezione [Foglio di riferimento Git](https://education.github.com/git-cheat-sheet-education.pdf) sul sito web GitHub.
