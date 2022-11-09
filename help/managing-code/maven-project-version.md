---
title: Gestione delle versioni dei progetti Maven
description: Scopri come Maven gestisce il controllo delle versioni dei progetti in Cloud Manager.
exl-id: a1d676e0-27cc-4b0d-8799-527c0520946a
source-git-commit: 9312999660b324f0f9d2b44dfbf49c4813a3a6e9
workflow-type: ht
source-wordcount: '260'
ht-degree: 100%

---


# Gestione delle versioni dei progetti Maven {#project-version}

Scopri come Maven gestisce il controllo delle versioni dei progetti in Cloud Manager.

## Gestione delle versioni dei progetti in Maven {#how-maven}

Per le distribuzioni di staging e produzione, Cloud Manager genera una versione univoca e incrementale.

Questa versione viene visualizzata nella pagina dei dettagli di esecuzione della pipeline e nella pagina dell’attività. Quando viene eseguita una build, il progetto Maven viene aggiornato per utilizzare la versione e viene creato un tag nell’archivio Git con tale versione come nome.

Se la versione del progetto originale soddisfa determinati criteri, la versione del progetto Maven aggiornata unirà la versione del progetto originale e quella generata da Cloud Manager. Tuttavia, il tag utilizza sempre la versione generata. Affinché tale unione si verifichi, la versione originale del progetto deve essere formata da esattamente tre segmenti di versione, ad esempio `1.0.0` o `1.2.3`, ma non `1.0` o `1`, mentre la versione originale non deve terminare con `-SNAPSHOT`.

>[!NOTE]
>
>Il valore della versione del progetto originale deve essere impostato in modo statico nell’elemento `<version>` del livello superiore `pom.xml` nel ramo dell’archivio Git.

Se la versione originale soddisfa questi criteri, la versione generata verrà aggiunta alla versione originale come segmento di nuova versione. Anche la versione generata verrà leggermente modificata per includere l’ordinamento e la gestione delle versioni corrette. Ad esempio, supponendo una versione generata di `2019.926.121356.0000020490`:

| Versione | Versione in `pom.xml` | Commenti |
|---|---|---|
| `1.0.0` | `1.0.0.2019_0926_121356_0000020490` | Versione originale formata correttamente |
| `1.0.0-SNAPSHOT` | `2019.926.121356.0000020490` | Versione snapshot, sovrascritta |
| `1` | `2019.926.121356.0000020490` | Versione incompleta, sovrascritta |

>[!NOTE]
>
>Indipendentemente dal fatto che la versione originale fosse incorporata nella versione inizializzata da Cloud Manager, la versione originale è disponibile come proprietà Maven con il nome `cloudManagerOriginalVersion`.
