---
title: Archivio del codice sorgente
seo-title: Repository del codice di origine per  Adobe AEM Cloud Manager
description: Segui questa pagina per saperne di più sul repository Git fornito per ogni programma disponibile in Cloud Manager.
seo-description: Seguite questa pagina per informazioni sul repository git fornito per ciascun programma disponibile in  Adobe AEM Cloud Manager.
uuid: 2c42775f-8703-43f7-bad2-7dc086ea9dd7
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requirements
discoiquuid: f90f0f4c-c1ff-47f6-8d97-ff5018561bf2
translation-type: tm+mt
source-git-commit: 697311cd00ef96568f6befd2fe76febafc27961e
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Archivio del codice sorgente {#source-code-repository}

## Repository di Cloud Manager {#cloud-manager-repository}

L&#39;iscrizione [!UICONTROL AEM Managed Services] includerà un archivio del codice sorgente con provisioning e gestione  Adobe. A ciascun programma del cliente viene assegnato un **Repository Git** singolo e univoco, in cui il codice associato verrà memorizzato e protetto.

Di regola, è consigliabile utilizzare sempre l&#39;archivio Git di Cloud Manager, vuoto senza rami configurati o progetti di esempio. Per utilizzare l&#39;archivio Git di Cloud Manager, ti verrà fornito un **token di accesso privato** che ti consentirà di utilizzare qualsiasi client compatibile con Git per creare rami, memorizzare e recuperare il codice, elencare la cronologia di commit, ecc.

Per ulteriori informazioni su come impostare i rami in Git, vedere [Configurazione dei rami di rilascio](configure-your-release-branches.md).

Per ulteriori informazioni sull&#39;utilizzo dell&#39; **Repository Git di Cloud Manager** con la pipeline CI/CD, vedere [Configurazione della pipeline CI/CD](configuring-pipeline.md).

## Repository locale {#on-premise-repository}

In alcuni casi, si dispone di un repository Git esistente e si desidera continuare a utilizzarlo. In questi casi, è possibile utilizzare la funzione supportata da Git per più repository remoti. Lo sviluppo quotidiano continuerebbe a verificarsi nel repository Git. Quando un ramo release è pronto per una distribuzione in produzione, invierete il codice più recente al repository Git di Cloud Manager e attiverete la pipeline CI/CD di Cloud Manager.

>[!NOTE]
>
>Per visualizzare i comandi Git più comuni, vedere il [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf).

