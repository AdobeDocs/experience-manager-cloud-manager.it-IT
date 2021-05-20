---
title: Gestione delle versioni dei progetti Maven
seo-title: Gestione delle versioni dei progetti Maven
description: Ulteriori informazioni sulla gestione delle versioni dei progetti Maven.
seo-description: Segui questa pagina per ulteriori informazioni sulla gestione delle versioni dei progetti Maven.
feature: Guida introduttiva
exl-id: a1d676e0-27cc-4b0d-8799-527c0520946a
source-git-commit: aa2d7cb3d0fa3d6038d364659ce8d5eacb6825c5
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 7%

---

# Gestione delle versioni dei progetti Maven {#project-version}

## Informazioni sulla gestione delle versioni dei progetti Maven {#understanding-project-version}

Per le distribuzioni di stage e produzione, Cloud Manager genera una versione univoca e incrementale.

Questa versione viene visualizzata nella pagina dei dettagli di esecuzione della pipeline e nella pagina dell’attività . Quando viene eseguita una build, il progetto Maven viene aggiornato per utilizzare questa versione e viene creato un tag nell’archivio Git con tale versione come nome.

Se la versione del progetto originale soddisfa determinati criteri, la versione del progetto Maven aggiornata unirà sia la versione del progetto originale che la versione generata da Cloud Manager. Tuttavia, il tag utilizza sempre la versione generata. Affinché l’unione si verifichi, la versione originale del progetto deve essere formata con esattamente tre segmenti di versione, ad esempio 1.0.0 o 1.2.3, ma non 1.0 o 1, e la versione originale non deve terminare con -SNAPSHOT.

>[!NOTE]
>Il valore della versione del progetto originale deve essere impostato in modo statico nell’elemento `<version>` del file di livello principale `pom.xml` nel ramo dell’archivio Git.

Se la versione originale soddisfa questo criterio, la versione generata verrà aggiunta alla versione originale come segmento di nuova versione. Anche la versione generata verrà leggermente modificata per includere l’ordinamento e la gestione delle versioni corrette. Ad esempio, supponendo una versione generata di 2019.926.121356.000020490:

| **Versione** | **versione in pom.xml** | **Commento** |
|---|---|---|
| 1.0.0 | 1.0.0.2019_0926_121356_000020490 | Versione originale formata correttamente |
| 1.0.0-SNAPSHOT | 2019.926.121356.0000020490 | Versione istantanea, sovrascritta |
| 1 | 2019.926.121356.0000020490 | Versione incompleta, sovrascritta |

>[!NOTE]
>
>Indipendentemente dal fatto che la versione originale sia stata incorporata o meno nella versione inizializzata da Cloud Manager, la versione originale è disponibile come proprietà Maven denominata *cloudManagerOriginalVersion.*
