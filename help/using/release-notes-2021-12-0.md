---
title: Note sulla versione 2021.12.0
description: Queste sono le note sulla versione per la versione 2021.12.0 di Cloud Manager.
feature: Release Information
source-git-commit: 099a4490e3a8578b9f3485fd1514d1e97db977ab
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 3%

---

# Note sulla versione per Cloud Manager versione 2021.12.0 {#release-notes}

La sezione seguente illustra le note generali sulla versione di [!UICONTROL Cloud Manager] versione 2021.12.0.

>[!NOTE]
>
>Per le ultime note sulla versione di Cloud Manager in AEM as a Cloud Service, fai riferimento a [Cloud Manager nelle note sulla versione corrente di AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Data di pubblicazione {#release-date}

La data di rilascio per [!UICONTROL Cloud Manager] la versione 2021.12.0 è il 16 dicembre 2021. La prossima versione è prevista per gennaio 2022.

## Novità {#whats-new}

* L’hash di commit, già visibile nell’interfaccia utente, ora viene fornito anche nell’API.
* La pagina Attività ora include un pop-over per l’esecuzione delle pipeline che fornisce un riepilogo dei dettagli della pipeline a colpo d’occhio.
* Sono stati aggiunti aggiornamenti per includere ulteriori dettagli presentati nella pagina Attività .
* La scheda Informazioni in Cloud Manager ora include l’accesso rapido alle guide API e alle risorse associate.
* Un utente con il ruolo di gestione distribuzione può ora avviare la procedura guidata per la creazione di progetti/rami per un archivio senza rami dal menu azione nella pagina repository.
* Deployment Manager, che si trova nel flusso di lavoro di aggiunta o modifica della pipeline, ora viene informato su come creare un ramo o un progetto se l’archivio selezionato non dispone di rami.
* Nella finestra Modifica pipeline di produzione, quando per la produzione è presente più di un ambiente stage, è disponibile un menu a discesa per la selezione dell’ambiente.
* La versione dell’Archetipo di progetto AEM utilizzato da Cloud Manager è stata aggiornata alla versione 32.

## Correzioni di bug {#bug-fixes}

* Le pipeline di produzione dello stack complete rimangono denominate &quot;pipeline di produzione&quot; anche quando l’utente immette un nome diverso nel campo name.
