---
title: Note sulla versione 2021.7.0
description: Segui questa pagina per ottenere informazioni sulla versione 2021.7.0 di Cloud Manager
feature: Informazioni sulla versione
source-git-commit: e490a8f1dd17e63f35ed00d4cdf95b6e7a07b150
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 6%

---

# Note sulla versione 2021.7.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per [!UICONTROL Cloud Manager] la versione 2021.7.0.

>[!NOTE]
>Fai riferimento a [Note sulla versione corrente](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access) per visualizzare le ultime note sulla versione per Cloud Manager in AEM come Cloud Service.

## Data di rilascio {#release-date}

La data di rilascio per la versione 2021.7.0 di [!UICONTROL Cloud Manager] è il 15 luglio 2021.
La prossima versione è prevista per il 12 agosto 2021.

## Novità {#whats-new}

* I clienti ora possono utilizzare Azul 8 e 11 JDK per i processi di creazione di Cloud Manager e possono scegliere di utilizzare uno di questi JDK per i plug-in Maven compatibili con toolchain *o* per l’intera esecuzione del processo Maven.

* L&#39;IP in uscita verrà ora registrato nel file di registro dei passaggi della build.

* I pulsanti **Manage Git** (Gestisci Git) sono stati rinominati in **Access Git Info** e la finestra di dialogo è stata aggiornata visivamente.

* La versione di AEM Project Archetype utilizzata da Cloud Manager è stata aggiornata alla versione 28.

* Alcune riconfigurazioni impreviste della topologia potrebbero comportare la mancata disponibilità di rapporti di test dettagliati dalla pagina dei dettagli dell’esecuzione della pipeline.

## Correzioni di bug {#bug-fixes}

* La navigazione manuale alla pagina dei dettagli di esecuzione per un’esecuzione non esistente non mostrava un errore, ma solo una schermata di caricamento infinita.

* In alcuni casi, il tentativo automatico per i contenitori con errore utilizzati nelle prestazioni di Sites non ha effetto per 2 ore, dando luogo a un errore di test.

## Problemi noti {#known-issues}

I clienti che passano all&#39;uso di Azul JDK dovrebbero essere consapevoli che non tutte le applicazioni esistenti si compileranno senza errori su Azul JDK. Si consiglia vivamente di eseguire il test localmente prima di passare a un altro metodo.