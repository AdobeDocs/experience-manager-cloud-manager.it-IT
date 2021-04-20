---
title: Note sulla versione 2019.6.0
seo-title: Note sulla versione di AEM Cloud Manager 2019.6.0
description: Segui questa pagina per ottenere informazioni sulla versione 2019.6.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2019.6.0 di AEM Cloud Manager.
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 9%

---

# Note sulla versione 2019.6.0 {#release-notes-for}

La versione [!UICONTROL Cloud Manager] 2019.6.0 aggiunge nuove regole di qualità del codice e una nuova procedura guidata di aggiornamento del prodotto. Per ulteriori informazioni, consulta le sezioni seguenti.

## Data di rilascio {#release-date}

La data di rilascio di [!UICONTROL Cloud Manager] versione 2019.6.0 è il 20 giugno 2019 .

## Novità {#whats-new}

* Nuova procedura guidata di aggiornamento del prodotto per facilitare la corretta esecuzione di un aggiornamento AEM. Per ulteriori informazioni, consulta [Procedura guidata di aggiornamento del prodotto](overview-productupdate-wizard.md) .
* Regole sulla qualità del codice che esaminano le strutture dei contenuti. Per ulteriori informazioni, consulta [Regole per la qualità del codice personalizzato](custom-code-quality-rules.md) .
* La dimensione massima di un push git è stata aumentata a 1 GB.

## Correzioni di bug {#bug-fixes}

* In alcuni casi, non è stato possibile avviare le pipeline a causa di un errore precedente.

## Problemi noti {#known-issues}

* Il download CSV della qualità del codice non viene sempre ordinato in base alla gravità.
* I falsi positivi possono essere segnalati dalla regola *ConfigAndInstallShouldOnlyContainOsgiNodes* se le configurazioni OSGi sono posizionate in una cartella nidificata sotto una cartella *config* .