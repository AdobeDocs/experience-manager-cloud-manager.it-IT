---
title: Lo strumento Copia contenuto
description: Lo strumento di copia dei contenuti di Cloud Manager consente agli utenti di copiare contenuti mutabili on-demand dagli ambienti di produzione AEM 6.x ospitati da AMS agli ambienti più bassi per i test.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '1076'
ht-degree: 36%

---


# Strumento di copia del contenuto {#content-copy}

Lo strumento di copia dei contenuti di Cloud Manager consente agli utenti di copiare contenuti mutabili on-demand dagli ambienti di produzione AEM 6.x ospitati da AMS agli ambienti più bassi per i test.

## Introduzione {#introduction}

I dati attuali e reali sono utili a scopo di test, convalida e accettazione da parte degli utenti. Lo strumento Content Copy consente di copiare il contenuto dall’ambiente AEM 6.x ospitato da AMS di produzione agli ambienti di staging o sviluppo. Questo flusso di lavoro supporta vari scenari di test.

Un set di contenuti definisce il contenuto da copiare. Un set di contenuti include un elenco di percorsi JCR con il contenuto mutabile da copiare. Il contenuto si sposta da un ambiente di origine a un ambiente di destinazione. Tutte queste operazioni vengono eseguite all&#39;interno dello stesso programma Cloud Manager.

In un set di contenuti sono consentiti i seguenti percorsi:

```text
/content/**
/conf/**
/etc/**
/var/workflow/models/**
/var/commerce/**
```

Durante la copia del contenuto, l’ambiente sorgente è l’origine di riferimento.

* Se modifichi il contenuto nell’ambiente di destinazione, il contenuto sorgente lo sovrascrive se i percorsi corrispondono.
* Se i percorsi sono diversi, il contenuto dell’origine viene unito al contenuto della destinazione.

## Autorizzazioni {#permissions}

Per utilizzare lo strumento di copia del contenuto, l&#39;utente deve essere assegnato al ruolo **Responsabile dell&#39;implementazione** negli ambienti di origine e di destinazione.

## Creazione di un set di contenuti {#create-content-set}

Prima di poter copiare qualsiasi contenuto, è necessario definire un set di contenuti. Una volta definiti, i set di contenuti possono essere riutilizzati per copiare il contenuto. Per creare un set di contenuti, effettua le seguenti operazioni.

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Dalla pagina **Panoramica**, passa alla schermata **Ambienti**.

1. Dalla schermata **Ambienti**, passa alla pagina **Set di contenuti**.

1. Nella parte superiore destra dello schermo, fai clic su **Aggiungi set di contenuti**.

   ![Set di contenuti](/help/assets/content-sets.png)

1. Nella scheda **Dettagli** della procedura guidata, fornisci un nome e una descrizione per il set di contenuti e fai clic su **Continua**.

   ![Dettagli dei set di contenuti](/help/assets/add-content-set-details.png)

1. Nella scheda **Percorsi del contenuto** della procedura guidata, specifica i percorsi del contenuto modificabile da includere nel set di contenuti.

   1. Immetti il percorso nel campo **Aggiungi percorso di inclusione**.
   1. Fare clic su **Aggiungi percorso** per aggiungere il percorso al set di contenuti.
   1. Fare di nuovo clic su **Aggiungi percorso** in base alle esigenze.

   ![Aggiungi percorsi al set di contenuti](/help/assets/add-content-set-paths.png)

1. Se devi perfezionare o limitare il set di contenuti, è possibile escludere i percorsi secondari.

   1. Nell&#39;elenco dei percorsi inclusi fare clic sull&#39;icona **Aggiungi percorsi secondari di esclusione** accanto al percorso da limitare.
   1. Immetti il percorso secondario da escludere dal percorso selezionato.
   1. Fare clic su **Escludi percorso**.
   1. Di nuovo, fai clic su **Aggiungi percorsi secondari di esclusione** per aggiungere percorsi aggiuntivi da escludere, in base alle esigenze.

   ![Esclusione dei percorsi](/help/assets/add-content-set-paths-excluded.png)

1. Se necessario, è possibile modificare i percorsi specificati.

   1. Fai clic su `X` accanto ai percorsi secondari esclusi per eliminarli.
   1. Fai clic sul pulsante con i puntini di sospensione accanto ai percorsi per visualizzare le opzioni **Modifica** e **Elimina**.

   ![Modifica dell’elenco dei percorsi](/help/assets/add-content-set-excluded-paths.png)

1. Fai clic su **Crea** per creare il set di contenuti.

Il set di contenuti può ora essere utilizzato per copiare il contenuto tra ambienti diversi.

>[!NOTE]
>
>Puoi aggiungere fino a 50 percorsi in un set di contenuti.
>Non ci sono limitazioni per i percorsi esclusi.

## Modifica di un set di contenuti {#edit-content-set}

Segui passaggi simili a quelli impiegati per la creazione del contenuto. Invece di fare clic su **Aggiungi set di contenuti**, selezionare un set esistente dalla console e selezionare **Modifica** dal menu con i puntini di sospensione.

![Modifica set di contenuti](/help/assets/edit-content-set.png)

Quando modifichi il set di contenuti, potrebbe essere necessario espandere i percorsi configurati per visualizzare i percorsi secondari esclusi.

## Copia del contenuto {#copy-content}

Una volta creato un set di contenuti, puoi utilizzarlo per copiare il contenuto. Per copiare il contenuto, effettua le seguenti operazioni.

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Dalla pagina **Panoramica**, passa alla schermata **Ambienti**.

1. Dalla schermata **Ambienti**, passa alla pagina **Set di contenuti**.

1. Seleziona un set di contenuti dalla console e seleziona **Copia contenuto** dal menu con i puntini di sospensione.

   ![Copia contenuto](/help/assets/copy-content.png)

   >[!NOTE]
   >
   >Un ambiente può non essere selezionabile se:
   >
   >* L’utente non dispone delle autorizzazioni appropriate.
   >* L’ambiente dispone di una pipeline in esecuzione o di un’operazione di copia del contenuto in corso.

1. Nella finestra di dialogo **Copia contenuto**, specifica l&#39;origine e la destinazione per l&#39;azione di copia del contenuto.

1. Puoi scegliere di eliminare o mantenere i percorsi di esclusione nell’ambiente di destinazione. Selezionare la casella di controllo `Do not delete exclude paths from destination` per mantenere `exclude paths` specificati nel set di contenuti. Se la casella di controllo è deselezionata, i percorsi di esclusione vengono eliminati nell’ambiente di destinazione.

1. Puoi scegliere di copiare la cronologia delle versioni dei percorsi copiati dall’ambiente di origine a quello di destinazione. Selezionare la casella di controllo `Copy Versions` per copiare tutte le cronologie delle versioni.

   ![Copia del contenuto](/help/assets/copying-content.png)

1. Fai clic su **Copia**.

Viene avviato il processo di copia. Lo stato del processo di copia si riflette nella console del set di contenuti selezionato.

## Attività copia contenuto {#copy-activity}

Puoi monitorare lo stato dei processi di copia nella pagina **Attività copia contenuto**.

1. Accedi a Cloud Manager all&#39;indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/), quindi seleziona l&#39;organizzazione e il programma appropriati.

1. Dalla pagina **Panoramica**, passa alla schermata **Ambienti**.

1. Dalla schermata **Ambienti**, passa alla pagina **Attività copia contenuto**.

![Attività copia contenuto](/help/assets/copy-content-activity.png)

### Stati di copia contenuto {#statuses}

Una volta iniziata la copia del contenuto, il processo può trovarsi in uno dei seguenti stati.

| Stato | Descrizione |
|---|---|
| In corso | Operazione di copia del contenuto in corso |
| Non riuscito | Operazione di copia del contenuto non riuscita |
| Completato | Operazione di copia del contenuto completata |

## Limitazioni {#limitations}

Lo strumento Copia contenuto presenta le seguenti limitazioni.

* Non è possibile eseguire una copia del contenuto da un ambiente inferiore a un ambiente superiore.
* La copia del contenuto può essere eseguita solo all’interno dello stesso livello. Vale a dire, autore-autore o pubblicazione-pubblicazione.
* Non è possibile copiare il contenuto tra più programmi o aree geografiche diverse.
* È possibile eseguire la copia del contenuto per la topologia basata sull&#39;archivio dati cloud solo quando l&#39;ambiente di origine e quello di destinazione si trovano nello stesso provider cloud e nella stessa area.
* Non è possibile eseguire operazioni di copia simultanee del contenuto nello stesso ambiente.
* Non è possibile eseguire la copia del contenuto se è in esecuzione un’operazione attiva nell’ambiente di destinazione o di origine, ad esempio una pipeline CI/CD.
* È possibile specificare fino a cinquanta percorsi per set di contenuti. Non ci sono limitazioni per i percorsi esclusi.
* Lo strumento di copia del contenuto non deve essere utilizzato come strumento di duplicazione o mirroring perché non può tenere traccia del contenuto spostato o eliminato nell’origine.
* Non è possibile mettere in pausa o annullare una copia del contenuto dopo averla avviata.
* Lo strumento Content Copy trasferisce le risorse e i metadati Dynamic Medie dall’ambiente superiore a quello inferiore selezionato. Le risorse copiate devono quindi essere rielaborate utilizzando il flusso di lavoro [Elabora risorse DAM](https://experienceleague.adobe.com/it/docs/experience-manager-65/content/assets/using/assets-workflow) nell&#39;ambiente inferiore per utilizzare la rispettiva configurazione di Dynamic Medie.

* Quando la cronologia delle versioni non viene copiata, il processo di copia del contenuto risulta notevolmente più veloce.
