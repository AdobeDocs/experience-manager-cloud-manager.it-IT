---
title: Note sulla versione 2021.6.0
description: Segui questa pagina per ottenere informazioni sulla versione 2021.6.0 di Cloud Manager
feature: Informazioni sulla versione
source-git-commit: ee701dd2d0c3921455a0960cbb6ca9a3ec4793e7
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 4%

---

# Note sulla versione 2021.6.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per [!UICONTROL Cloud Manager] la versione 2021.6.0.

>[!NOTE]
>Fai riferimento a [Note sulla versione corrente](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access) per visualizzare le ultime note sulla versione per Cloud Manager in AEM come Cloud Service.

## Data di rilascio {#release-date}

La data di rilascio per la versione 2021.6.0 di [!UICONTROL Cloud Manager] è il 10 giugno 2021.
La prossima versione è prevista per il 15 luglio 2021.

## Novità {#whats-new}

* I test di Assets e Sites ora vengono eseguiti in parallelo (se applicabile), riducendo in tal modo il tempo totale di esecuzione della pipeline. Questa funzione verrà attivata per i clienti nelle prossime settimane.

* Le dipendenze Maven scaricate durante il passaggio di creazione ora verranno memorizzate nella cache tra le esecuzioni della pipeline. Questa funzione verrà attivata per i clienti nelle prossime settimane.

* Il nome del ramo predefinito utilizzato sia durante la creazione del progetto che nel comando push predefinito tramite gestione flussi di lavoro Git è stato modificato in `main`.

* L’esperienza di modifica del programma nell’interfaccia utente è stata aggiornata. Per ulteriori informazioni, consulta [Modifica di un programma](/help/using/setting-up-program.md#editing-program) .

* La regola di qualità `ImmutableMutableMixCheck` è stata aggiornata per classificare i nodi `/oak:index` come immutabili.

* Le regole di qualità `CQBP-84` e `CQBP-84--dependencies` sono state consolidate in un’unica regola. Come parte di questo consolidamento, la scansione delle dipendenze identifica più accuratamente i problemi nelle dipendenze di terze parti che vengono distribuiti nel runtime di AEM.

* In alcune situazioni, se non si calcola la metrica Test ignorati , le esecuzioni della pipeline non avranno esito positivo.

## Correzioni di bug {#bug-fixes}

* Le definizioni dei nodi JCR contenenti una nuova riga dopo che il nome dell&#39;elemento principale non è stato analizzato correttamente.

* L&#39;API degli archivi di elenchi non filtrerebbe gli archivi eliminati.

* Veniva visualizzato un messaggio di errore non corretto quando veniva fornito un valore non valido per il passaggio di pianificazione.

* In alcuni casi, quando l’esecuzione della pipeline ha raggiunto il passaggio di distribuzione a produzione e l’utente interrompe l’esecuzione, il messaggio di stato di distribuzione nell’interfaccia utente non rispecchiava correttamente ciò che stava effettivamente accadendo.
