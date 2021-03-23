---
title: Archivio del codice sorgente
seo-title: Archivio del codice sorgente per Adobe AEM Cloud Manager
description: Segui questa pagina per scoprire l’archivio Git fornito per ciascun programma in Cloud Manager.
seo-description: Segui questa pagina per scoprire l’archivio Git fornito per ciascun programma disponibile in Adobe AEM Cloud Manager.
uuid: 2c42775f-8703-43f7-bad2-7dc086ea9dd7
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requirements
discoiquuid: f90f0f4c-c1ff-47f6-8d97-ff5018561bf2
feature: Provisioning
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 2%

---


# Archivio del codice sorgente {#source-code-repository}

## Archivio di Cloud Manager {#cloud-manager-repository}

La tua sottoscrizione [!UICONTROL AEM Managed Services] includerà un archivio di codice sorgente predisposto e gestito da Adobe. Al programma di ciascun cliente viene assegnato un **Git Repository** singolo e univoco, in cui il codice associato verrà memorizzato e protetto.

Come best practice, utilizza sempre l’archivio Git di Cloud Manager, vuoto senza rami configurati o progetti di esempio. Per utilizzare l’archivio Git di Cloud Manager, riceverai un **token di accesso privato** che ti consentirà di utilizzare qualsiasi client compatibile con Git per creare rami, archiviare e recuperare il codice, elencare la cronologia del commit, ecc.

Per ulteriori informazioni su come impostare i rami in Git, consulta [Configurazione dei rami della versione](configure-your-release-branches.md).

Per ulteriori informazioni su come utilizzare l’ **archivio Git di Cloud Manager** con la pipeline CI/CD, consulta [Configurazione della pipeline CI/CD](configuring-pipeline.md).

## Archivio on-premise {#on-premise-repository}

In alcuni casi, disporrai di un archivio Git esistente e desideri continuare a utilizzarlo. In questi casi, è possibile utilizzare la funzione supportata di Git per più archivi remoti. Lo sviluppo quotidiano continuerebbe a verificarsi nel tuo archivio Git. Quando un ramo di rilascio è pronto per una distribuzione in produzione, invierai il codice più recente all’archivio Git di Cloud Manager e attiverai la pipeline CI/CD di Cloud Manager.

>[!NOTE]
>
>Per visualizzare i comandi Git comuni, consulta la [Guida di riferimento rapido Git](https://education.github.com/git-cheat-sheet-education.pdf).

