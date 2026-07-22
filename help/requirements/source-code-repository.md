---
title: Archivio del codice sorgente
description: Scopri l’archivio Git fornito per ciascun programma in Cloud Manager.
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
TQID: https://experienceleague.adobe.com/hdEpqKW0NluPs-w37SeLzpd-EHJNqb2nfSAMQ35man8
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: b24e9550f11486e7ed8da31d5da27f85ad5acaf2
workflow-type: tm+mt
source-wordcount: 236
ht-degree: 44%

---

# Archivio del codice sorgente {#source-code-repository}

Scopri l’archivio Git fornito per ciascun programma in Cloud Manager.

## Archivio di Cloud Manager {#cloud-manager-repository}

Il tuo abbonamento a [!UICONTROL AEM Managed Services] include un archivio del codice sorgente fornito e gestito da Adobe. A ciascun programma viene assegnato un archivio Git univoco, in cui il codice associato viene memorizzato e protetto.

Come best practice, utilizza sempre l’archivio Git di Cloud Manager, che viene fornito vuoto, senza rami configurati o progetti di esempio. Cloud Manager fornisce un token di accesso privato per l’archivio Git, consentendoti di utilizzare qualsiasi client Git per creare rami, gestire il codice, recuperare la cronologia del commit e altro ancora.

Per ulteriori informazioni su come impostare i rami in Git, consulta [Configurazione dei rami di rilascio](/help/getting-started/configuring-branches.md)

Per ulteriori informazioni su come utilizzare l&#39;archivio Git di Cloud Manager con la pipeline CI/CD, consulta [Configurare le pipeline di produzione](/help/using/production-pipelines.md) e [Configurare le pipeline non di produzione](/help/using/non-production-pipelines.md).

## Repository locale {#on-premise-repository}

Se disponi di un archivio Git esistente e desideri continuare a utilizzarlo, utilizza la funzione Git per più archivi remoti. Lo sviluppo continua nell’archivio Git. Quando un ramo della versione è pronto per la distribuzione in produzione, puoi inviare il codice più recente all’archivio Git di Cloud Manager e attivare la pipeline CI/CD di Cloud Manager.

Per visualizzare i comandi Git comuni, vedere la [Guida di riferimento Git](https://education.github.com/git-cheat-sheet-education.pdf).
