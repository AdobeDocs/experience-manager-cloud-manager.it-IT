---
title: Strumento Copia contenuto
description: Lo strumento Copia contenuto di Cloud Manager consente agli utenti di copiare contenuti modificabili su richiesta dagli ambienti di produzione AEM 6.x in hosting AMS in ambienti inferiori per test.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '1144'
ht-degree: 100%

---


# Strumento Copia contenuto {#content-copy}

Lo strumento Copia contenuto di Cloud Manager consente agli utenti di copiare contenuti modificabili su richiesta dagli ambienti di produzione AEM 6.x in hosting AMS in ambienti inferiori per test.

## Introduzione {#introduction}

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

## Creazione di un set di contenuti {#create-content-set}

Prima di poter copiare qualsiasi contenuto, è necessario definire un set di contenuti. Una volta definiti, i set di contenuti possono essere riutilizzati per copiare il contenuto. Per creare un set di contenuti, effettua le seguenti operazioni.

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Dalla pagina **Panoramica**, passa alla schermata **Ambienti**.

1. Dalla schermata **Ambienti**, passa alla pagina **Set di contenuti**.

1. Vicino alla parte in alto a destra della schermata, fai clic su **Aggiungi set di contenuti**.

   ![Set di contenuti](/help/assets/content-sets.png)

1. Nella scheda **Dettagli** della procedura guidata, assegna un nome e una descrizione per il set di contenuti quindi fai clic su **Continua**.

   ![Dettagli dei set di contenuti](/help/assets/add-content-set-details.png)

1. Nella scheda **Percorsi del contenuto** della procedura guidata, specifica i percorsi del contenuto modificabile da includere nel set di contenuti.

   1. Immetti il percorso nel campo **Aggiungi percorso di inclusione**.
   1. Fai clic su **Aggiungi percorso** per aggiungere il percorso al set di contenuti.
   1. Se necessario, fai di nuovo clic su **Aggiungi percorso**.

   ![Aggiungi percorsi al set di contenuti](/help/assets/add-content-set-paths.png)

1. Se devi perfezionare o limitare il set di contenuti, è possibile escludere i percorsi secondari.

   1. Nell’elenco dei percorsi inclusi, fai clic sull’icona **Aggiungi percorsi secondari di esclusione** accanto al percorso da limitare.
   1. Inserisci il percorso secondario da escludere dal percorso selezionato.
   1. Fai clic su **Escludi percorso**.
   1. Fai clic di nuovo su **Aggiungi percorsi secondari di esclusione** per aggiungere altri percorsi da escludere, in base alle esigenze.

   ![Esclusione dei percorsi](/help/assets/add-content-set-paths-excluded.png)

1. Se necessario, è possibile modificare i percorsi specificati.

   1. Fai clic su `X` accanto ai percorsi secondari esclusi per eliminarli.
   1. Fai clic sul pulsante con i puntini di sospensione accanto ai percorsi per visualizzare le opzioni **Modifica** ed **Elimina**.

   ![Modifica dell’elenco dei percorsi](/help/assets/add-content-set-excluded-paths.png)

1. Fai clic su **Crea** per creare il set di contenuti.

Il set di contenuti può ora essere utilizzato per copiare il contenuto tra ambienti diversi.

>[!NOTE]
>
>Puoi aggiungere fino a 50 percorsi in un set di contenuti.
>Non ci sono limitazioni per i percorsi esclusi.

## Modifica di un set di contenuti {#edit-content-set}

Segui passaggi simili a quelli effettuati per la creazione del contenuto. Invece di fare clic su **Aggiungi set di contenuti**, seleziona un set esistente dalla console e quindi seleziona **Modifica** dal menu con i puntini di sospensione.

![Modifica set di contenuti](/help/assets/edit-content-set.png)

Quando modifichi il set di contenuti, potrebbe essere necessario espandere i percorsi configurati per visualizzare i percorsi secondari esclusi.

## Copia contenuto {#copy-content}

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

1. Nella finestra di dialogo **Copia contenuto**, specifica l’ambiente di origine e di destinazione dell’azione di copia del contenuto.
   * Le aree dell’ambiente di destinazione devono essere simili a un sottoinsieme delle aree dell’ambiente di origine.

1. Puoi scegliere di eliminare o mantenere i percorsi di esclusione nell’ambiente di destinazione. Seleziona la casella di controllo `Do not delete exclude paths from destination` per mantenere `exclude paths` specificati nel set di contenuti. Se la casella di controllo è deselezionata, i percorsi di esclusione vengono eliminati nell’ambiente di destinazione.

1. Puoi scegliere di copiare la cronologia delle versioni dei percorsi copiati dall’ambiente di origine a quello di destinazione. Seleziona la casella di controllo `Copy Versions` se desideri copiare tutte le cronologie delle versioni.

   ![Copia del contenuto](/help/assets/copying-content.png)

1. Fai clic su **Copia**.

Viene avviato il processo di copia. Lo stato del processo di copia si riflette nella console del set di contenuti selezionato.

## Attività copia contenuto {#copy-activity}

Puoi monitorare lo stato dei processi di copia nella pagina **Attività copia contenuto**.

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/), quindi seleziona l’organizzazione e il programma appropriati.

1. Dalla pagina **Panoramica**, passa alla schermata **Ambienti**.

1. Dalla schermata **Ambienti**, passa alla pagina **Attività copia contenuto**.

![Attività copia contenuto](/help/assets/copy-content-activity.png)

### Stati della copia del contenuto {#statuses}

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
