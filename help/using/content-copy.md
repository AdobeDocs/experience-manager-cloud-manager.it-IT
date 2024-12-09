---
title: Copia dei contenuti per coerenza ambiente
description: Lo strumento di copia dei contenuti di Cloud Manager Adobe consente agli utenti di copiare contenuti mutabili On-demand dagli ambienti di produzione Adobe Experience Manager 6.x ospitati da Managed Services in ambienti più bassi per i test.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: 2c96feb62a4db2424430c9c410563a7f61320fd2
workflow-type: tm+mt
source-wordcount: '1364'
ht-degree: 42%

---


# Copia del contenuto per coerenza dell’ambiente {#content-copy}

Lo strumento di copia dei contenuti di Cloud Manager Adobe consente agli utenti di copiare contenuti mutabili On-demand dagli ambienti di produzione Adobe Experience Manager 6.x ospitati da Managed Services in ambienti più bassi per i test.

## Informazioni sulla copia del contenuto {#introduction}

I dati attuali e reali sono utili a scopo di test, convalida e accettazione da parte degli utenti. Lo strumento Copia contenuto consente di copiare contenuti dall’ambiente di produzione AEM 6.x in hosting AMS a un ambiente di staging o sviluppo. Questo flusso di lavoro supporta vari scenari di test.

Un set di contenuti definisce il contenuto da copiare. Un set di contenuti include un elenco di percorsi JCR con il contenuto mutabile da copiare. Il contenuto si sposta da un ambiente di origine a un ambiente di destinazione. Tutte queste operazioni vengono eseguite all’interno dello stesso programma Cloud Manager.

I percorsi seguenti sono consentiti in un set di contenuti:

```text
/content/**
/conf/**
/etc/**
/var/workflow/models/**
/var/commerce/**
```

Durante la copia del contenuto, l’ambiente di origine è l’origine di riferimento.

* Se modifichi il contenuto nell’ambiente di destinazione e i percorsi corrispondono, viene sovrascritto dal contenuto di origine.
* Se i percorsi sono diversi, il contenuto dell’origine viene unito al contenuto della destinazione.

## Autorizzazioni {#permissions}

Per utilizzare lo strumento di copia del contenuto, all’utente deve essere assegnato il ruolo di **Responsabile della distribuzione** negli ambienti di origine e di destinazione.

## Creare un set di contenuti {#create-content-set}

Prima di poter copiare qualsiasi contenuto, è necessario definire un set di contenuti. Una volta definiti, i set di contenuti possono essere riutilizzati per copiare il contenuto. Per creare un set di contenuti, effettua le seguenti operazioni.

**Per creare un set di contenuti:**

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Nell&#39;angolo superiore sinistro della pagina fare clic su ![Mostra icona menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) per aprire il menu sul lato sinistro.

1. Dal menu a sinistra, nella pagina **Servizi**, fare clic sull&#39;icona ![Casella ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Set di contenuti**.

1. Fare clic su **Aggiungi set di contenuti** nell&#39;angolo superiore destro della pagina.

   ![Set di contenuti](/help/assets/content-sets.png)

1. Nella finestra di dialogo **Aggiungi set di contenuti**, nella scheda **Dettagli**, nei campi **Nome** e **Descrizione**, digitare un nome e una descrizione facoltativa per il set di contenuti, quindi fare clic su **Continua**.

   ![Dettagli dei set di contenuti](/help/assets/add-content-set-details.png)

1. Nella scheda **Percorsi contenuto**, nel campo di testo **Percorso**, specificare il percorso del contenuto che può essere modificato e che deve essere incluso nel set di contenuti.

   Solo i percorsi che iniziano con `/content`, `/conf`, `/etc`, `/var/workflow/models` o `/var/commerce` possono essere inclusi.

1. Fai clic sull&#39;icona **![Aggiungi cartella](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderAdd_18_N.svg) Aggiungi percorso** per aggiungere (o includere) il percorso al set di contenuti.

1. (Facoltativo) Se necessario, aggiungi percorsi aggiuntivi (fino a 50) ripetendo i due passaggi precedenti. In caso contrario, procedere al passaggio successivo.

   ![Aggiungi percorsi al set di contenuti](/help/assets/add-content-set-paths.png)

1. (Facoltativo) Per limitare il set di contenuti, puoi facoltativamente specificare percorsi secondari all’interno di un percorso di contenuto incluso che deve essere escluso.

   1. A destra di un percorso di contenuto incluso che si desidera limitare, fare clic su ![Icona eliminazione cartella](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg).
   1. Nel campo di testo, digitate un percorso relativo al percorso principale visualizzato nella finestra di dialogo.
   1. Fai clic sull&#39;icona ![Elimina cartella](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg) **Escludi percorso**.
   1. Se necessario, ripetere i punti da i. a iii. qui sopra per aggiungere altri percorsi di esclusione; non vi sono limitazioni. In caso contrario, procedere al passaggio successivo.

   ![Esclusione dei percorsi](/help/assets/add-content-set-paths-excluded.png)

1. (Facoltativo) Effettuate una delle seguenti operazioni:

   1. Fai clic sull&#39;icona ![Dimensioni incrociate 500](https://spectrum.adobe.com/static/icons/ui_18/CrossSize500.svg) a destra di un percorso secondario escluso per eliminarlo.
   1. Fai clic sull&#39;icona ![Altro](https://spectrum.adobe.com/static/icons/ui_18/More.svg) a destra di un percorso di contenuto incluso, quindi fai clic su **Modifica** o **Elimina**.

   ![Modifica dell’elenco dei percorsi](/help/assets/add-content-set-excluded-paths.png)

1. Fai clic su **Crea**.

Ora puoi utilizzare il set di contenuti per copiare i contenuti da un ambiente all’altro.

## Modificare o eliminare un set di contenuti {#edit-content-set}

Quando modifichi un set di contenuti, potrebbe essere necessario espandere i percorsi configurati per visualizzare i percorsi secondari esclusi.

**Per modificare o eliminare un set di contenuti:**

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Nell&#39;angolo superiore sinistro della pagina fare clic su ![Mostra icona menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) per aprire il menu sul lato sinistro.

1. Dal menu a sinistra, in **Servizi**, fare clic sull&#39;icona ![Casella ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Set di contenuti**.

1. Nella tabella della pagina **Set di contenuti**, fai clic sull&#39;icona ![Altro](https://spectrum.adobe.com/static/icons/ui_18/More.svg) a destra di un percorso di contenuto incluso, quindi fai clic su **Modifica** o **Elimina**.

![Modifica set di contenuti](/help/assets/edit-content-set.png)


## Copia contenuto {#copy-content}

Dopo aver creato un set di contenuti, puoi utilizzarlo per copiare il contenuto.

Un ambiente potrebbe non essere disponibile per la selezione se si verifica una delle seguenti condizioni:

* L’utente non dispone delle autorizzazioni necessarie.
* Nell’ambiente è attualmente in esecuzione una pipeline o un’operazione di copia del contenuto.

**Per copiare il contenuto:**

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Nell&#39;angolo superiore sinistro della pagina fare clic su ![Mostra icona menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) per aprire il menu sul lato sinistro.

1. Dal menu a sinistra, in **Servizi**, fare clic sull&#39;icona ![Casella ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Set di contenuti**.

1. Nella tabella della pagina **Set di contenuti**, a destra di un percorso di contenuto incluso che si desidera copiare, fare clic sull&#39;icona ![Altro](https://spectrum.adobe.com/static/icons/ui_18/More.svg), quindi su **Copia contenuto**.

   ![Copia contenuto](/help/assets/copy-content.png)

1. Nella finestra di dialogo **Copia contenuto**, seleziona l&#39;ambiente **Source** e l&#39;ambiente **Destinazione** per l&#39;azione di copia del contenuto.

   * Le aree in un ambiente di destinazione devono essere un sottoinsieme di aree in un ambiente di origine.
   * I problemi di compatibilità vengono verificati prima di eseguire un’azione di copia del contenuto. Quando si seleziona l&#39;ambiente **Destination**, il sistema convalida automaticamente gli ambienti di origine e di destinazione. Se la convalida non riesce, il processo viene interrotto e nella finestra di dialogo viene visualizzato un messaggio di errore che spiega il motivo dell&#39;errore.

1. (Facoltativo) Effettuate una delle seguenti operazioni:

   1. Per *mantenere* i percorsi esclusi nell&#39;ambiente di destinazione, selezionare **`Do not delete exclude paths from destination`**. Questa impostazione mantiene intatti i percorsi esclusi specificati nel set di contenuti.
   1. Per *rimuovere* i percorsi esclusi nell&#39;ambiente di destinazione, deselezionare **`Do not delete exclude paths from destination`**. Questa impostazione elimina i percorsi esclusi specificati nel set di contenuti.
   1. Per copiare la cronologia delle versioni dei percorsi dall&#39;ambiente di origine all&#39;ambiente di destinazione, selezionare **Copia versioni**.

      ![Copia del contenuto](/help/assets/copying-content.png)

1. Fai clic su **Copia**. Lo stato del processo di copia si riflette nella console del set di contenuti selezionato.

## Monitorare lo stato dell’attività di copia del contenuto {#copy-activity}

Puoi monitorare lo stato dei processi di copia nella pagina **Attività copia contenuto**.

**Monitoraggio dello stato dell&#39;attività di copia del contenuto:**

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Nell&#39;angolo superiore sinistro della pagina fare clic su ![Mostra icona menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) per aprire il menu sul lato sinistro.

1. Dal menu a sinistra, in **Servizi**, fare clic sull&#39;icona ![Cronologia ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_History_18_N.svg) **Copia attività contenuto**.

   ![Attività copia contenuto](/help/assets/copy-content-activity.png)

   Un processo di copia del contenuto può avere uno dei seguenti stati:

   | Stato | Descrizione |
   | --- | --- |
   | In corso | L’operazione di copia del contenuto è in corso. |
   | Completato | Operazione di copia del contenuto completata. |
   | Non riuscito | Copia del contenuto non riuscita. |


## Limitazioni {#limitations}

Lo strumento di copia del contenuto presenta le seguenti limitazioni:

* Non è possibile eseguire una copia del contenuto da un ambiente inferiore a un ambiente superiore.
* La copia del contenuto può essere eseguita solo all’interno dello stesso livello. Vale a dire, autore-autore o pubblicazione-pubblicazione.
* Non è possibile copiare il contenuto tra più programmi o aree geografiche diverse.
* La copia del contenuto per la topologia di archivio dati basata su cloud può essere eseguita solo quando l’ambiente di origine e di destinazione si trovano sullo stesso provider cloud e nella stessa area geografica.
* Non è possibile eseguire operazioni simultanee di copia del contenuto nello stesso ambiente.
* Non è possibile eseguire la copia del contenuto se è in esecuzione un’operazione attiva nell’ambiente di destinazione o di origine, ad esempio una pipeline CI/CD.
* È possibile specificare fino a cinquanta percorsi per set di contenuti. Non ci sono limitazioni per i percorsi esclusi.
* Lo strumento Copia contenuto non deve essere utilizzato come strumento di duplicazione o mirroring perché non può tenere traccia del contenuto spostato o eliminato nell’origine.
* Una volta avviata, una copia del contenuto non può essere messa in pausa o annullata.
* Lo strumento Copia contenuto copia le risorse e i metadati di Dynamic Media, dall’ambiente superiore all’ambiente inferiore selezionato. Le risorse copiate devono quindi essere rielaborate utilizzando il [Flusso di lavoro di risorse di processo DAM](https://experienceleague.adobe.com/it/docs/experience-manager-65/content/assets/using/assets-workflow) nell’ambiente inferiore per utilizzare la rispettiva configurazione di Dynamic Media.
* Il processo di copia del contenuto è notevolmente più veloce quando la cronologia delle versioni non viene copiata.
* [Le configurazioni Dynamic Media con dimensioni delle risorse superiori a 2 GB abilitate](https://experienceleague.adobe.com/it/docs/experience-manager-65/content/assets/dynamic/config-dms7#optional-config-dms7-assets-larger-than-2gb) non sono supportate.
* Quando la cronologia delle versioni non viene copiata, il processo di copia del contenuto risulta notevolmente più veloce.
* Le aree dell’ambiente di destinazione devono essere simili a un sottoinsieme delle aree dell’ambiente di origine.

## Problemi noti {#known-issues}

{{content-copy-known-issues}}
