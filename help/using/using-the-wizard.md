---
title: Utilizzo della procedura guidata
description: Seguite questa pagina per apprendere come utilizzare la procedura guidata per creare un progetto applicazione AEM
translation-type: tm+mt
source-git-commit: 7146a41d64365c9de03d32f4fc4c33f9e366c244
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Utilizzo della procedura guidata {#using-wizard-to-create-an-aem-application-project}

Quando i clienti sono collegati a Cloud Manager, vengono forniti con un repository git vuoto. Gli attuali clienti di Adobe Managed Services (AMS) (o AEM clienti interni che stanno effettuando la migrazione ad AMS) in genere hanno già il codice di progetto in git (o un altro sistema di controllo della versione) e importeranno il loro progetto nell’archivio Git di Cloud Manager. I nuovi clienti, tuttavia, non hanno progetti esistenti.

Per aiutare a far iniziare i nuovi clienti, Cloud Manager è ora in grado di creare un progetto AEM minimo come punto di partenza. Questo processo è basato sul [**AEM Project Archetype**](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).


Per creare un progetto di applicazione AEM in Cloud Manager, procedi come segue:

1. Una volta effettuato l’accesso a Cloud Manager e quando la configurazione del programma di base è completa, nella schermata **Panoramica** verrà visualizzato uno speciale invito all’azione, se l’archivio è vuoto.

   ![](assets/image2018-10-3_14-29-44.png)

1. Fare clic su **Crea per** per aprire una finestra di dialogo che consente all&#39;utente di fornire i parametri richiesti dall&#39;Archetype AEM progetto. Nel modulo predefinito, la finestra di dialogo richiede due valori:

   * **Titolo** : per impostazione predefinita è impostato su Nome  *programma*

   * **Nuovo nome**  ramo - per impostazione predefinita è  *principale*

   ![](assets/screen_shot_2018-10-08at55825am.png)

   Nella finestra di dialogo è disponibile un cassetto che può essere aperto facendo clic sul quadratino nella parte inferiore della finestra di dialogo. Nel modulo espanso, la finestra di dialogo mostra tutti i parametri di configurazione per Archetype. Molti di questi parametri hanno valori predefiniti che vengono generati in base al **Titolo**.

   ![](assets/screen_shot_2018-10-08at60032am.png)

   >[!NOTE]
   >
   >Ad esempio, se il **Titolo** è ***We.Finance***, il parametro ID artefatto di base di Paradiso viene generato come ***com.wefinance***. Se lo desiderate, questi valori possono essere modificati.
   >
   >
   >Ad esempio, è possibile passare da ***valore com.wefinance*** generato a ***net.wefinance***.

1. Fare clic su **Crea** nel passaggio precedente per creare il progetto iniziale utilizzando archetype e per eseguire il commit nel ramo git denominato. Al termine, è possibile impostare la pipeline.