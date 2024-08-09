---
title: Archivio del codice sorgente
description: Scopri l’archivio Git fornito per ciascun programma in Cloud Manager.
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 83%

---


# Archivio del codice sorgente {#source-code-repository}

Scopri l’archivio Git fornito per ciascun programma in Cloud Manager.

## Archivio di Cloud Manager {#cloud-manager-repository}

Il tuo abbonamento a [!UICONTROL AEM Managed Services] include un archivio del codice sorgente fornito e gestito da Adobe. A ciascun programma viene assegnato un archivio Git singolo e univoco, in cui il codice associato verrà archiviato e protetto.

Come best practice, utilizza sempre l’archivio Git di Cloud Manager, che si presenta vuoto senza rami o progetti di esempio configurati. Per utilizzare l’archivio Git di Cloud Manager, riceverai un token di accesso privato che ti consentirà di utilizzare qualsiasi client Git per creare rami, archiviare e recuperare il codice, elencare la cronologia del commit e così via.

Per ulteriori informazioni su come impostare i rami in Git, consulta [Configurazione dei rami di rilascio](/help/getting-started/configuring-branches.md).

Per ulteriori informazioni su come utilizzare l&#39;archivio Git di Cloud Manager con la pipeline CI/CD, consulta [Configurare le pipeline di produzione](/help/using/production-pipelines.md) e [Configurare le pipeline non di produzione](/help/using/non-production-pipelines.md).

## Archivio locale {#on-premise-repository}

È possibile disporre di un archivio Git esistente e continuare a utilizzarlo, nel qual caso è possibile utilizzare la funzione Git per più archivi remoti. Lo sviluppo quotidiano continuerebbe a verificarsi nell’archivio Git. Quando un ramo di rilascio è pronto per una distribuzione in produzione, puoi inviare il codice più recente all’archivio Git di Cloud Manager e attivare la pipeline CI/CD di Cloud Manager.

Per visualizzare i comandi Git comuni, consulta la sezione [Scheda di riferimento Git](https://education.github.com/git-cheat-sheet-education.pdf) sul sito web GitHub.
