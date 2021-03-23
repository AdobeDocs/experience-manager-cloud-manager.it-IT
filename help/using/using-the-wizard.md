---
title: Utilizzo della procedura guidata
description: Segui questa pagina per scoprire come utilizzare la procedura guidata per creare un progetto di applicazione AEM
feature: Guida introduttiva
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 10%

---


# Utilizzo della procedura guidata {#using-wizard-to-create-an-aem-application-project}

Quando i clienti sono caricati su Cloud Manager, viene fornito loro un archivio git vuoto. I clienti attuali di Adobe Managed Services (AMS) (o i clienti on-premise AEM che eseguono la migrazione ad AMS) in genere hanno già il loro codice di progetto in git (o in un altro sistema di controllo della versione) e importeranno il loro progetto nell’archivio Git di Cloud Manager. I nuovi clienti, tuttavia, non hanno progetti esistenti.

Per far iniziare nuovi clienti, Cloud Manager è ora in grado di creare un progetto AEM minimo come punto di partenza. Questo processo è basato su [**AEM Project Archetype**](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).


Per creare un progetto di applicazione AEM in Cloud Manager, effettua le seguenti operazioni:

1. Una volta effettuato l’accesso a Cloud Manager e quando la configurazione del programma di base è completa, nella schermata **Panoramica** verrà visualizzato uno speciale invito all’azione, se l’archivio è vuoto.

   ![](assets/image2018-10-3_14-29-44.png)

1. Fai clic su **Crea a** per aprire una finestra di dialogo che consente all&#39;utente di fornire i parametri richiesti dall&#39;Archetipo di progetto AEM. Nel modulo predefinito, la finestra di dialogo richiede due valori:

   * **Titolo** : per impostazione predefinita è impostato su Nome  *programma*

   * **Nuovo nome ramo** : per impostazione predefinita è  *principale*

   ![](assets/screen_shot_2018-10-08at55825am.png)

   La finestra di dialogo presenta un cassetto che può essere aperto facendo clic sul manico verso il fondo della finestra di dialogo. Nel modulo espanso, la finestra di dialogo mostra tutti i parametri di configurazione per Archetype. Molti di questi parametri hanno valori predefiniti che vengono generati in base al **Titolo**.

   ![](assets/screen_shot_2018-10-08at60032am.png)

   >[!NOTE]
   >
   >Ad esempio, se il **Titolo** è ***We.Finance***, il parametro ID dell&#39;artefatto Maven di base viene generato come ***com.wefinance***. Se lo desideri, puoi modificare questi valori.
   >
   >
   >Ad esempio, è possibile passare dal valore ***com.wefinance*** generato a ***net.wefinance***.

1. Fai clic su **Crea** nel passaggio precedente per creare il progetto iniziale utilizzando l’archetipo e esegui il commit nel ramo git denominato. Al termine, puoi impostare la pipeline.