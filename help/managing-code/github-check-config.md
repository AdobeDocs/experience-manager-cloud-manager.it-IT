---
title: Configurazione verifica GitHub per archivi privati
description: Scopri come controllare le pipeline create automaticamente per convalidare ogni richiesta di pull in un archivio privato.
exl-id: 29c9e487-e196-411a-8cda-6751b0a56066
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 39%

---

# Configurazione di controllo GitHub per archivi privati {#github-check-config}

Scopri come controllare le pipeline create automaticamente per convalidare ogni richiesta di pull in un archivio privato.

## Configurazione dei controlli GitHub {#configuration}

Quando si utilizzano [archivi privati](private-repositories.md#using), viene creata automaticamente una [pipeline di qualità del codice full stack](/help/overview/ci-cd-pipelines.md). Tale pipeline viene avviata ogni volta che la richiesta pull viene aggiornata.

È possibile verificare questi controlli creando un file `.cloudmanager/pr_pipelines.yml` nel ramo predefinito dell’archivio privato.

```yaml
github:
  shouldDeletePreviousComment: false
pipelines:
  - type: CI_CD
    template:
      programId: 1234
      pipelineId: 456
    namePrefix: Full Stack Code Quality Pipeline for PR 
    importantMetricsFailureBehavior: CONTINUE
```

| Parametro | Valori possibili | Predefiniti | Descrizione |
| --- | --- | --- | --- |
| `shouldDeletePreviousComment` | `true` oppure `false` | `false` | Specifica se conservare solo l’ultimo commento con i risultati della scansione del codice in questa richiesta pull GitHub o mantenere tutto. |
| `type` | `CI_CD` | n/d | Definisce il comportamento di una pipeline CI/CD. |
| `template.programID` | Numero intero | Non viene riutilizzata alcuna variabile di pipeline | È possibile riutilizzare le [variabili pipeline](/help/getting-started/build-environment.md#pipeline-variables) impostate su una pipeline esistente, che ogni PR crea automaticamente. |
| `template.pipelineID` | Numero intero | Non viene riutilizzata alcuna variabile di pipeline | È possibile riutilizzare le [variabili pipeline](/help/getting-started/build-environment.md#pipeline-variables) impostate su una pipeline esistente, che ogni PR crea automaticamente. |
| `namePrefix` | Stringa | `Full Stack Code Quality Pipeline for PR` | Utilizzato per impostare il nome della pipeline creata automaticamente. |
| `importantMetricsFailureBehavior` | `CONTINUE` o `FAIL` o `PAUSE` | `CONTINUE` | Imposta il comportamento della metrica importante della pipeline<br>`CONTINUE` = Se una metrica importante non riesce, la pipeline si sposta automaticamente in avanti<br>`FAIL` = La pipeline termina con uno stato FAILED se una metrica importante non riesce<br>`PAUSE` = Il passaggio di analisi del codice riceve uno stato WAITING quando una metrica importante non riesce e deve essere ripreso manualmente. |
