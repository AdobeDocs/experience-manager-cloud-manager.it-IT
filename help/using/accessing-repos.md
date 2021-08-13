---
title: Accesso agli archivi
seo-title: Accesso agli archivi
description: Questa pagina descrive come accedere e gestire l’archivio Git.
seo-description: Segui questa pagina per scoprire come accedere e gestire l’archivio Git.
feature: Archivi Git
exl-id: 403fc93d-60fc-4439-8c9d-0a512ca34458
source-git-commit: 5bbe76a46b7a15ccbab85c4487d2a20aaf59a4e7
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 4%

---

# Accesso agli archivi {#accessing-repos}

Puoi accedere e gestire il tuo archivio Git utilizzando Self-Service Git Account Management (Gestione account Git self-service) dall’interfaccia utente di Cloud Manager.

## Utilizzo della gestione account Git self-service {#self-service-git}

Utilizza il pulsante **Access Repo Info** disponibile dall’interfaccia utente di Cloud Manager, che si trova più in evidenza sulla scheda della pipeline.

1. Passa alla scheda **Pipelines** dalla pagina **Panoramica del programma**.

1. Per accedere e gestire l’archivio Git, visualizzerai l’opzione **Access Repo Info** .

   ![](assets/access-repo1.png)

   Inoltre, se selezioni la scheda della pipeline **Non-Produzione** , visualizzerai anche l&#39;opzione **Accedi alle informazioni sul repository**.

   ![](assets/access-repo-nonprod.png)


   >[!NOTE]
   >L&#39;opzione **Access Repo Info** è visibile agli utenti nel ruolo Developer o Deployment Manager. Facendo clic su questo pulsante si apre una finestra di dialogo che consente all’utente di trovare l’URL del proprio archivio Git di Cloud Manager insieme al nome utente e alla password.

   ![](assets/access-repo-create.png)

   Le considerazioni importanti per gestire il Git in Cloud Manager sono le seguenti:

   * **URL**: URL del repository
   * **Nome utente**: Nome utente
   * **Password**: valore visualizzato quando si fa clic sul pulsante **Generate Password (Genera password)**.


      >[!NOTE]
      >Un utente può estrarre una copia del proprio codice e apportare modifiche nell&#39;archivio del codice locale. Quando è pronto, l’utente può eseguire nuovamente il commit delle modifiche del codice nell’archivio del codice remoto in Cloud Manager.
