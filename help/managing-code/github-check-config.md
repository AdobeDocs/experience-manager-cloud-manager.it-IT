---
title: Configurazione controllo GitHub per archivi privati
description: Scopri come controllare le pipeline create automaticamente per convalidare ogni richiesta di pull in un archivio privato.
source-git-commit: 85c1e22609dc5646d3de0ccc71e9423d4243e13a
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 7%

---


# Configurazione controllo GitHub per archivi privati {#github-check-config}

Scopri come controllare le pipeline create automaticamente per convalidare ogni richiesta di pull in un archivio privato.

## Configurazione dei controlli GitHub {#configuration}

Quando si utilizza [archivi privati,](private-repositories.md#using) a [pipeline di qualità del codice full stack](/help/overview/ci-cd-pipelines.md) verrà creato automaticamente. Tale pipeline viene avviata ogni volta che la richiesta pull viene aggiornata.

È possibile controllare questi controlli creando un `.cloudmanager/pr_pipelines.yml` nel ramo predefinito dell’archivio privato.

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
|---|---|---|---|
| `shouldDeletePreviousComment` | `true` oppure `false` | `false` | Se conservare solo l’ultimo commento con i risultati della scansione del codice in questa richiesta pull GitHub o mantenere tutti |
| `type` | `CI_CD` | n/d | Definisce il comportamento di una pipeline CI/CD |
| `template.programID` | Intero | Non viene riutilizzata alcuna variabile di pipeline | Può essere utilizzato per riutilizzare [variabili della pipeline](/help/getting-started/build-environment.md#pipeline-variables) che sono impostati su una delle pipeline esistenti create automaticamente da ogni PR. |
| `template.pipelineID` | Intero | Non viene riutilizzata alcuna variabile di pipeline | Può essere utilizzato per riutilizzare [variabili della pipeline](/help/getting-started/build-environment.md#pipeline-variables) che sono impostati su una delle pipeline esistenti create automaticamente da ogni PR. |
| `namePrefix` | Stringa | `Full Stack Code Quality Pipeline for PR` | Utilizzato per impostare il nome della pipeline creata automaticamente |
| `importantMetricsFailureBehavior` | `CONTINUE` o `FAIL` o `PAUSE` | `CONTINUE` | Imposta il comportamento metrico importante della pipeline<br>`CONTINUE` = Se una metrica importante non riesce, la pipeline avanza automaticamente<br>`FAIL` = La pipeline termina con lo stato FAILED (NON RIUSCITO) se una metrica importante non riesce<br>`PAUSE` = Il passaggio di scansione del codice riceverà uno stato IN ATTESA quando una metrica importante non riesce e deve essere ripreso manualmente |
