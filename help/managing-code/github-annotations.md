---
title: Annotazioni di verifica GitHub
description: Scopri in che modo le verifiche GitHub annotano le PR negli archivi privati per fornire un feedback utile.
exl-id: 15178de8-8a8a-4300-8510-88875ad0fc8c
source-git-commit: 6f5d51ef59aef831574bd55cee6b12a29e3d70d2
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 98%

---


# Annotazioni di controllo GitHub {#github-annotations}

Scopri in che modo le verifiche GitHub annotano le PR negli archivi privati per fornire un feedback utile.

## Panoramica {#overview}

Se stai usando [archivi privati](private-repositories.md) per il programma Cloud Manager, le verifiche in GitHub vengono eseguite automaticamente per ogni richiesta pull. Queste verifiche vengono annotate con informazioni utili, per comprendere il prima possibile eventuali problemi riscontrati con il codice.

![Esempio di annotazioni di controllo GitHub](assets/github-check-annotations.png)

I problemi di [Qualità del codice](/help/using/code-quality-testing.md) rilevati da [SonarQube](/help/using/custom-code-quality-rules.md) sono elencati in modo chiaro.

![Esempio di annotazione del problema del codice](assets/github-check-annotations-example.png)

Viene fornita la riga di codice esatta con il problema sulla quale è possibile fare clic per mostrare il codice pertinente. Queste annotazioni vengono fornite per tutti i problemi di codice, non solo per quelli modificati nella richiesta pull.

![Esempio di annotazione del problema del codice](assets/github-check-annotations-example-code.png)

Tutte le righe con annotazioni vengono aggregate nella scheda **File modificati** nella richiesta pull di GitHub. Le annotazioni per i file che non sono stati modificati nella richiesta pull vengono visualizzate nella rispettiva sezione.

![Esempio di annotazioni nella scheda File modificati](assets/github-check-annotations-files-changed.png)

## Pipeline di qualità del codice {#code-quality-pipelines}

I risultati della [qualità del codice](/help/using/code-quality-testing.md) sono visibili anche nella pipeline, che viene attivata automaticamente da Cloud Manager nella parte inferiore della scheda **Controlli**. È inoltre accessibile dai **Dettagli** del controllo della richiesta pull.

![Esempio di annotazioni](assets/github-check-annotations-code-quality.png)

![Esempio di annotazioni](assets/github-check-annotations-code-quality-2.png)

Puoi anche visualizzare i problemi in formato CSV. Questo metodo può essere recuperato [visualizzando i dettagli dell’esecuzione della pipeline in Cloud Manager](/help/using/managing-pipelines.md).
