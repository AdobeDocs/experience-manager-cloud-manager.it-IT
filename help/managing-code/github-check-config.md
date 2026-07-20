---
title: Controlli della richiesta pull per archivi privati
description: Scopri come controllare le pipeline create automaticamente per convalidare ogni richiesta pull in un archivio privato.
exl-id: 29c9e487-e196-411a-8cda-6751b0a56066
TQID: https://experienceleague.adobe.com/duceoXUt2SqWI0ZXzyuqZtszLfJkWr53G5O5ze4nxTY
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: b52942282fe5f825181123b3839ef155753c5e23
workflow-type: tm+mt
source-wordcount: 237
ht-degree: 91%

---

# Controlli delle richieste di pull per archivi privati {#github-check-config}

<!--OLD TITLE THAT I THOUGHT WAS BETTER Check configuration for private repositories -->

Scopri come controllare le pipeline create automaticamente per convalidare ogni richiesta pull in un archivio privato.

## Configurazione dei controlli dell’archivio privato {#configuration}

Quando si utilizzano gli [archivi privati,](private-repositories.md#using) viene creata automaticamente una [pipeline di qualità del codice full-stack](/help/overview/ci-cd-pipelines.md). Questa pipeline viene avviata a ogni aggiornamento della richiesta di pull.

È possibile verificare questi controlli creando un file `.cloudmanager/pr_pipelines.yml` nel ramo predefinito dell’archivio privato.

```yaml
pullRequest:
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
