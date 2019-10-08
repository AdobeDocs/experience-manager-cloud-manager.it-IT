---
title: Gestione delle versioni del progetto Maven
seo-title: Gestione delle versioni del progetto Maven
description: Ulteriori informazioni sulla gestione della versione del progetto Paradiso.
seo-description: Segui questa pagina per saperne di più su Maven Project Version Handling
translation-type: tm+mt
source-git-commit: 519f43ff16e0474951f97798a8e070141e5c124b

---


# Gestione delle versioni del progetto Maven {#project-version}

## Comprendere la gestione della versione del progetto di corvo {#understanding-project-version}

Per le distribuzioni di fase e produzione, Cloud Manager genera una versione univoca e incrementale.

Questa versione viene visualizzata nella pagina dei dettagli di esecuzione della pipeline e nella pagina dell'attività. Quando viene eseguita una build, il progetto Maven viene aggiornato per utilizzare questa versione e viene creato un tag nel repository git con quella versione come nome.

Se la versione del progetto originale soddisfa determinati criteri, la versione aggiornata del progetto Maven unirà sia la versione del progetto originale che la versione generata da Cloud Manager. Tuttavia, il tag utilizza sempre la versione generata. Affinché l'unione avvenga, la versione originale del progetto deve essere formata con esattamente tre segmenti di versione, ad esempio 1.0.0 o 1.2.3, ma non 1.0 o 1, e la versione originale non deve terminare con -SNAPSHOT.

Se la versione originale non soddisfa questo criterio, la versione generata verrà aggiunta alla versione originale come segmento di nuova versione. Anche la versione generata verrà leggermente modificata per includere l'ordinamento e la gestione delle versioni corrette. Ad esempio, supponendo una versione generata di 2019.926.121356.0000020490:

| **Versione** | **versione in pom.xml** | **Commento** |
|---|---|---|
| 1.0.0 | 1.0.0.2019_0926_121356_0000020490 | Versione originale formata correttamente |
| 1.0.0-SNAPSHOT | 2019.926.121356.0000020490 | Versione snapshot, sovrascritta |
| 1 | 2019.926.121356.0000020490 | Versione incompleta, sovrascritta |

>[!NOTE]
>
>Indipendentemente dal fatto che la versione originale sia stata incorporata o meno nella versione inizializzata di Cloud Manager, la versione originale è disponibile come proprietà Maven con il nome *cloudManagerOriginalVersion*.
