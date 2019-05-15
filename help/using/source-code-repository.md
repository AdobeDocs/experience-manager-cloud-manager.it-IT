---
title: Archivio codice sorgente
seo-title: Archivio codice sorgente per Adobe AEM Cloud Manager
description: Segui questa pagina per informazioni sull'archivio git fornito per ogni programma disponibile in Cloud Manager.
seo-description: Segui questa pagina per informazioni sull'archivio git fornito per ogni programma disponibile in Adobe AEM Cloud Manager.
uuid: 2 c 42775 f -8703-43 f 7-bad 2-7 dc 086 ea 9 dd 7
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requisiti
discoiquuid: f 90 f 0 f 4 c-c 1 ff -47 f 6-8 d 97-ff 5018561 bf 2
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Archivio codice sorgente {#source-code-repository}

## Archivio di Cloud Manager {#cloud-manager-repository}

[!UICONTROL AEM Managed Services] L&#39;iscrizione includerà un archivio di codici sorgente con provisioning e gestito da Adobe. A ciascun programma del cliente viene assegnato un archivio **** Git unico e univoco, dove il codice associato sarà memorizzato e protetto.

Come procedura ottimale, utilizzate sempre l&#39;archivio Git del Gestore di cloud, che viene lasciato vuoto senza che sia stato configurato alcun ramo o progetti di esempio. Per utilizzare l&#39;archivio Git di Experience Manager, vi verrà fornito un token di accesso **privato** che vi consentirà di utilizzare un client compatibile con Git per creare rami, memorizzare e recuperare il codice, elencare la cronologia di conferma e così via.

Per ulteriori informazioni su come impostare rami in Git, consultate [Configurazione dei rami di rilascio](configure-your-release-branches.md).

Per ulteriori informazioni su come utilizzare l&#39;archivio Git di **Cloud Manager** con la pipeline CI/CD, consultate [Configurazione della pipeline CI/CD](configuring-pipeline.md).

## Archivio locale {#on-premise-repository}

In alcuni casi, disponete di un archivio Git esistente e desiderate continuare a utilizzarlo. In questi casi, potete utilizzare la funzione supportata di Git per più archivi remoti. Lo sviluppo giorno-giorno continuerà a verificarsi nell&#39;archivio Git. Quando un ramo di rilascio è pronto per un&#39;implementazione alla produzione, invierai il codice più recente nell&#39;archivio Git di Cloud Manager e attiva la pipeline CI/CD di Cloud Manager.

>[!NOTE]
>
>Per visualizzare i comandi Git comuni, consultate [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf).

