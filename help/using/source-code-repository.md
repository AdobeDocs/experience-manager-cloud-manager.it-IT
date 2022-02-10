---
title: Archivio del codice sorgente
seo-title: Source Code Repository for Adobe AEM Cloud Manager
description: Segui questa pagina per scoprire l’archivio Git fornito per ciascun programma in Cloud Manager.
seo-description: Follow this page to learn about the git repository that is provisioned for each program you have in Adobe AEM Cloud Manager.
uuid: 2c42775f-8703-43f7-bad2-7dc086ea9dd7
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requirements
discoiquuid: f90f0f4c-c1ff-47f6-8d97-ff5018561bf2
feature: Provisioning
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 4f0e1d163001fd18cfa838256c813152d65c3b4c
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 2%

---

# Archivio del codice sorgente {#source-code-repository}

## Archivio Cloud Manager {#cloud-manager-repository}

Le [!UICONTROL AEM Managed Services] l’abbonamento includerà un archivio del codice sorgente predisposto e gestito da Adobe. Al programma di ogni cliente viene assegnato un unico e unico **Archivio Git**, in cui il codice associato verrà memorizzato e protetto.

Come best practice, utilizza sempre l’archivio Git di Cloud Manager, vuoto senza rami configurati o progetti di esempio. Per utilizzare l’archivio Git di Cloud Manager, viene fornito un **token di accesso privato** che ti permetterà di utilizzare qualsiasi client compatibile con Git per creare rami, archiviare e recuperare il codice, elencare la cronologia del commit, ecc.

Per ulteriori informazioni su come impostare i rami in Git, vedi [Configurazione dei rami della versione](configure-your-release-branches.md).

Per ulteriori informazioni su come utilizzare Cloud Manager’s **Archivio Git** con la pipeline CI/CD, fare riferimento ai documenti [Configurare le pipeline di produzione](configuring-production-pipelines.md) e [Configurazione di pipeline non di produzione](configuring-non-production-pipelines.md) per saperne di più.

## Archivio on-premise {#on-premise-repository}

In alcuni casi, disporrai di un archivio Git esistente e desideri continuare a utilizzarlo. In questi casi, è possibile utilizzare la funzione supportata di Git per più archivi remoti. Lo sviluppo quotidiano continuerebbe a verificarsi nel tuo archivio Git. Quando un ramo di rilascio è pronto per una distribuzione in produzione, invierai il codice più recente all’archivio Git di Cloud Manager e attiverai la pipeline CI/CD di Cloud Manager.

>[!NOTE]
>
>Per visualizzare i comandi Git comuni, consulta la sezione [Foglio di riferimento Git](https://education.github.com/git-cheat-sheet-education.pdf).
