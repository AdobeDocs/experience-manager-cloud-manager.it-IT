---
title: Configurazione verifica GitHub per archivi privati
description: Scopri come controllare le pipeline create automaticamente per convalidare ogni richiesta pull in un archivio privato.
exl-id: 29c9e487-e196-411a-8cda-6751b0a56066
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '236'
ht-degree: 100%

---

# Configurazione verifica GitHub per archivi privati {#github-check-config}

Scopri come controllare le pipeline create automaticamente per convalidare ogni richiesta pull in un archivio privato.

## Configurazione delle verifiche GitHub {#configuration}

Quando si utilizzano gli [archivi privati,](private-repositories.md#using) viene creata automaticamente una [pipeline di qualità del codice full-stack](/help/overview/ci-cd-pipelines.md). Tale pipeline viene avviata ogni volta che la richiesta pull viene aggiornata.

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
| `shouldDeletePreviousComment` | `true` oppure `false` | `false` | Se conservare solo l’ultimo commento insieme ai risultati della scansione del codice in questa richiesta pull di GitHub o mantenerli tutti. |
| `type` | `CI_CD` | n/d | Definisce il comportamento di una pipeline CI/CD. |
| `template.programID` | Numero intero | Non viene riutilizzata alcuna variabile di pipeline | È possibile riutilizzare le [variabili della pipeline](/help/getting-started/build-environment.md#pipeline-variables) impostate su una pipeline esistente, create automaticamente da ciascun PR. |
| `template.pipelineID` | Numero intero | Non viene riutilizzata alcuna variabile di pipeline | È possibile riutilizzare le [variabili della pipeline](/help/getting-started/build-environment.md#pipeline-variables) impostate su una pipeline esistente, create automaticamente da ciascun PR. |
| `namePrefix` | Stringa | `Full Stack Code Quality Pipeline for PR` | Utilizzata per impostare il nome della pipeline creata automaticamente. |
| `importantMetricsFailureBehavior` | `CONTINUE` o `FAIL` o `PAUSE` | `CONTINUE` | Imposta il comportamento metrico importante della pipeline<br>`CONTINUE` = Se una metrica importante non riesce, la pipeline avanza automaticamente<br>`FAIL` = La pipeline termina con lo stato FAILED (NON RIUSCITO) se una metrica importante non riesce<br>`PAUSE` = Il passaggio di scansione del codice riceverà uno stato WAITING (IN ATTESA) quando una metrica importante non riesce e deve essere ripreso manualmente. |
