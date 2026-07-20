---
title: Aggiungere un archivio di Adobe in Cloud Manager
description: Scopri come aggiungere archivi gestiti da Adobe in Cloud Manager.
exl-id: 24c6ca97-ea70-41b8-b4c7-b8b0f406a57d
TQID: https://experienceleague.adobe.com/LBI6V07enOlxe8yh-XwlkL-mdMWR0MJyKi1gUQtjtK4
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 036302d4861b59e783ac731da12078be59cdc5c4
workflow-type: tm+mt
source-wordcount: 225
ht-degree: 69%

---

# Aggiungere un archivio di Adobe in Cloud Manager {#adobe-repositories}

Scopri come aggiungere un archivio gestito da Adobe in Cloud Manager.

La pagina **Archivi** consente di aggiungere altri archivi gestiti da Adobe a un programma selezionato.

**Per aggiungere un archivio di Adobe in Cloud Manager:**

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati a cui desideri aggiungere un archivio gestito da Adobe.

1. Nella pagina **Panoramica programma**, nel menu laterale, fare clic sull&#39;icona ![Cartella](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **Archivi**.

1. Nella pagina **Archivi**, in alto a destra, fai clic su **Aggiungi archivio**.

   ![Pulsante Aggiungi archivio](/help/managing-code/assets/repositories-tab.png)

1. Nella finestra di dialogo **Aggiungi archivio**, accertati che **Archivio Adobe** sia selezionato come tipo di archivio.

1. Nei rispettivi campi di testo, immetti quanto segue:

   * **Nome archivio**: un nome descrittivo per il nuovo archivio.
   * **Anteprima URL archivio** - Non è necessario immettere un percorso URL o modificare il percorso esistente perché l&#39;infrastruttura del repository è già configurata, integrata e gestita da Adobe.
   * **Descrizione (facoltativa)**: una descrizione dettagliata dell’archivio.

   ![Finestra di dialogo Aggiungi archivio](/help/managing-code/assets/repository-add-adobe.png)

1. Fai clic su **Salva**.
Il nuovo archivio viene visualizzato nella tabella della pagina **Archivi**.

A questo punto potrai associarvi una [pipeline CI/CD](/help/overview/ci-cd-pipelines.md) o gestirlo all’interno della pagina[&#128279;](/help/managing-code/managing-repositories.md) **Archivi**.

>[!TIP]
>
>Puoi anche aggiungere archivi GitHub da gestire direttamente come [archivi privati](/help/managing-code/private-repositories.md).
