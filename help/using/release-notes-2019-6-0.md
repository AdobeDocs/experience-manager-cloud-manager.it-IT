---
title: Note sulla versione 2019.6.0
seo-title: Note sulla versione di AEM Cloud Manager per la versione 2019.8.0
description: Segui questa pagina per ottenere informazioni sulla versione 2019.6.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2019.6.0 di AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 7cfa0cf66efd5891263bfcc83a5149daec5c8b67

---

# Note sulla versione 2019.6.0 {#release-notes-for}

La release [!UICONTROL Cloud Manager] 2019.6.0 aggiunge nuove regole di qualità del codice e nuova procedura guidata Aggiornamento prodotto. Seguite le sezioni riportate di seguito per ulteriori dettagli.

## Data di rilascio {#release-date}

La data di rilascio per la [!UICONTROL Cloud Manager] versione 2019.6.0 è il 20 giugno 2019.

## Novità {#whats-new}

* Nuova procedura guidata Aggiornamento prodotto per aiutare i clienti a eseguire correttamente un aggiornamento AEM. Per ulteriori informazioni, fare riferimento alla procedura guidata [Aggiornamento](overview-productupdate-wizard.md) prodotto.
* Regole di qualità del codice che esaminano le strutture dei contenuti. Per ulteriori informazioni, fare riferimento a Regole [di qualità del codice](custom-code-quality-rules.md) personalizzate.
* La dimensione massima di un push git è stata aumentata a 1 GB.

## Correzioni dei bug {#bug-fixes}

* In alcuni casi, non è stato possibile avviare i gasdotti a causa di un errore precedente.

## Problemi noti {#known-issues}

* Il download CSV della qualità del codice non sempre viene ordinato in base alla gravità.
* I falsi positivi possono essere segnalati dalla regola *ConfigAndInstallShouldOnlyContainOsgiNodes* se le configurazioni OSGi vengono collocate in una cartella nidificata in una cartella di *configurazione* .