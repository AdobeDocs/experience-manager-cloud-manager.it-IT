---
title: Note sulla versione 2021.10.0
description: Segui questa pagina per ottenere informazioni sulla versione 2021.10.0 di Cloud Manager
feature: Release Information
source-git-commit: 09dd8fe608d95cd9dbc95129cf86b9693c2839b5
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 3%

---

# Note sulla versione 2021.10.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione di [!UICONTROL Cloud Manager] Versione 2021.10.0.

>[!NOTE]
>Fai riferimento a [Note sulla versione corrente](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access) per visualizzare le ultime note sulla versione per Cloud Manager in AEM as a Cloud Service.

## Data di pubblicazione {#release-date}

Data di rilascio per [!UICONTROL Cloud Manager] La versione 2021.10.0 è il 14 ottobre 2021.

## Novità {#whats-new}

* Le pipeline di produzione possono ora essere eseguite in modalità &quot;di emergenza&quot;, evitando i passaggi di test di sicurezza e prestazioni per le implementazioni di emergenza.

* Per coerenza con il Cloud Service, le pipeline di distribuzione esistenti ora vengono referenziate ed etichettate nell’interfaccia utente come pipeline &quot;Full Stack&quot;.

* La scheda della pipeline è stata aggiornata per visualizzare una singola faccia integrata che mostra sia le pipeline di produzione che quelle non di produzione e l’utente può selezionare Esegui/Pausa/Riprendi direttamente dal menu delle azioni associato a ciascuna pipeline.

* Un utente con il ruolo di Deployment Manager può ora eliminare la pipeline di produzione in modo self-service tramite l’interfaccia utente.

* Le esperienze di aggiunta e modifica delle pipeline sono state aggiornate per poter utilizzare modelli moderni e familiari.

* Gli utenti di Cloud Manager ora possono inviare feedback direttamente dall’interfaccia utente tramite l’ **Feedback** in alto a destra della pagina di destinazione.

* I grafici SLA annuali possono ora essere scaricati dall’interfaccia utente di Cloud Manager.

* Le esecuzioni della pipeline di qualità del codice e non di produzione ora utilizzeranno un processo di duplicazione poco profondo più efficiente durante il passaggio di creazione, consentendo ai clienti con archivi Git di dimensioni particolarmente grandi di ottenere tempi di creazione più rapidi.

* La documentazione API di Cloud Manager ora include un parco giochi interattivo che consente agli utenti connessi di sperimentare l’API dal proprio browser. Vedi [Playground API di Cloud Manager](https://www.adobe.io/experience-cloud/cloud-manager/reference/playground/) per ulteriori dettagli.

* La descrizione comandi nella scheda Programma sarà più descrittiva se un’opzione di selezione in &quot;Passa a&quot; è disabilitata. Ora si dirà &quot;Un ambiente di produzione non esiste&quot;.


## Correzioni di bug {#bug-fixes}

* Quando i dati letti dai sistemi interni non venivano immessi correttamente, poteva causare la visualizzazione errata dei dati non correlati forniti dai CSE in Cloud Manager.

* In situazioni specifiche del cliente, gli artefatti non validi scaricati durante il passaggio di compilazione che avrebbero dovuto causare un errore di compilazione venivano ignorati.