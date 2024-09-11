---
title: Gestione delle versioni dei progetti Maven
description: Scopri come Maven gestisce il controllo delle versioni dei progetti in Cloud Manager.
exl-id: a1d676e0-27cc-4b0d-8799-527c0520946a
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '249'
ht-degree: 100%

---


# Gestione delle versioni dei progetti Maven {#project-version}

Scopri come Maven gestisce il controllo delle versioni dei progetti in Cloud Manager.

## Gestione delle versioni dei progetti in Maven {#how-maven}

Per le distribuzioni di staging e di produzione, Cloud Manager genera una versione univoca e incrementale.

Questa versione viene visualizzata nella pagina dei dettagli di esecuzione della pipeline e nella pagina dell’attività. Quando viene eseguita una build, il progetto Maven viene aggiornato per utilizzare questa versione. Nell’archivio Git viene creato un tag con tale versione come nome.

Se la versione del progetto originale soddisfa determinati criteri, la versione del progetto Maven aggiornata unirà sia la versione del progetto originale che la versione generata da Cloud Manager. Tuttavia, il tag utilizza sempre la versione generata. Affinché tale unione si verifichi, la versione originale del progetto deve essere formata da esattamente tre segmenti di versione, ad esempio `1.0.0` o `1.2.3`, ma non `1.0` o `1`, mentre la versione originale non deve terminare con `-SNAPSHOT`.

>[!NOTE]
>
>Il valore della versione originale di questo progetto deve essere impostato in modo statico nell’elemento `<version>` del file `pom.xml` di livello superiore nel ramo dell’archivio Git.

Se la versione originale soddisfa questi criteri, la versione generata viene aggiunta alla versione originale come segmento di nuova versione. Anche la versione generata verrà leggermente modificata per includere l’ordinamento e la gestione delle versioni corrette. Ad esempio, supponendo una versione generata di `2019.926.121356.0000020490`:

| Versione | Versione in `pom.xml` | Commenti |
| --- | --- | --- |
| `1.0.0` | `1.0.0.2019_0926_121356_0000020490` | Versione originale formata correttamente |
| `1.0.0-SNAPSHOT` | `2019.926.121356.0000020490` | Versione snapshot, sovrascritta |
| `1` | `2019.926.121356.0000020490` | Versione incompleta, sovrascritta |

>[!NOTE]
>
>Indipendentemente dal fatto che la versione originale sia stata integrata o meno nella versione inizializzata da Cloud Manager, è ancora accessibile come proprietà Maven denominata `cloudManagerOriginalVersion`.
