---
title: Strumento Copia contenuto
description: Lo strumento di copia dei contenuti di Cloud Manager consente agli utenti di copiare contenuti mutabili su richiesta dai propri ambienti di produzione AEM in ambienti più bassi a scopo di test.
source-git-commit: 360cbf7e3a21e530a4e43f13f6d414dae4afa104
workflow-type: tm+mt
source-wordcount: '1017'
ht-degree: 7%

---


# Strumento Copia contenuto {#content-copy}

Lo strumento di copia dei contenuti di Cloud Manager consente agli utenti di copiare contenuti mutabili su richiesta dai propri ambienti di produzione AEM in ambienti più bassi a scopo di test.

## Introduzione {#introduction}

I dati attuali e reali sono utili a scopo di test, convalida e accettazione da parte degli utenti. Lo strumento di copia del contenuto ti consente di copiare il contenuto dall’ambiente di produzione AEM a un ambiente di staging o sviluppo per tale test.

Il contenuto da copiare è definito da un set di contenuti. Un set di contenuti è costituito da un elenco di percorsi JCR che contengono il contenuto modificabile da copiare da un ambiente di origine a un ambiente di destinazione all’interno dello stesso programma Cloud Manager. I percorsi seguenti sono consentiti in un set di contenuti.

```text
/content/**
/conf/**
/etc/**
/var/workflow/models/**
```

Durante la copia del contenuto, l’ambiente sorgente è l’origine della verità.

* Se il contenuto è stato modificato nell’ambiente di destinazione, verrà sovrascritto dal contenuto nell’origine, se i percorsi sono gli stessi.
* Se i percorsi sono diversi, il contenuto dell’origine verrà unito al contenuto della destinazione.

## Autorizzazioni {#permissions}

Per utilizzare lo strumento di copia del contenuto, l’utente deve essere assegnato al **Gestione distribuzione** ruolo negli ambienti di origine e di destinazione.

## Creazione di un set di contenuti {#create-content-set}

Prima di copiare qualsiasi contenuto, è necessario definire un set di contenuti. Una volta definiti, i set di contenuti possono essere riutilizzati per copiare il contenuto. Segui questi passaggi per creare un set di contenuti.

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Dalla pagina **Panoramica**, accedi alla schermata **Ambienti**.

1. Passa a **Set di contenuti** dalla pagina **Ambienti** schermo.

1. Tocca o fai clic sul pulsante **Aggiungi set di contenuti** in alto a destra dello schermo.

   ![Set di contenuti](/help/assets/content-sets.png)

1. Sulla **Dettagli** , fornisci un nome e una descrizione per il set di contenuti e tocca o fai clic su **Continua**.

   ![Dettagli set di contenuti](/help/assets/add-content-set-details.png)

1. Sulla **Percorsi contenuto** specifica i percorsi del contenuto modificabile da includere nel set di contenuti.

   1. Immetti il percorso nella **Aggiungi percorso di inclusione** campo .
   1. Tocca o fai clic sul pulsante **Aggiungi percorso** per aggiungere il percorso al set di contenuti.
   1. Tocca o fai clic sul pulsante **Aggiungi percorso** se necessario.

   ![Aggiungi percorsi al set di contenuti](/help/assets/add-content-set-paths.png)

1. Se devi perfezionare o limitare il set di contenuti, i percorsi secondari possono essere esclusi.

   1. Nell’elenco dei percorsi inclusi, tocca o fai clic sul pulsante **Aggiungi percorsi secondari di esclusione** accanto al percorso da limitare.
   1. Inserisci il percorso secondario da escludere sotto il percorso selezionato.
   1. Tocca o fai clic su **Escludi percorso**.
   1. Tocca o fai clic su **Aggiungi percorsi secondari di esclusione** per aggiungere altri percorsi da escludere, se necessario.

   ![Esclusione dei percorsi](/help/assets/add-content-set-paths-excluded.png)

1. Se necessario, puoi modificare i percorsi specificati.

   1. Tocca o fai clic sulla X accanto ai percorsi secondari esclusi per eliminarli.
   1. Tocca o fai clic sul pulsante dei puntini di sospensione accanto ai percorsi da visualizzare **Modifica** e **Elimina** opzioni.

   ![Modifica dell’elenco dei percorsi](/help/assets/add-content-set-excluded-paths.png)

1. Tocca o fai clic su **Crea** per creare il set di contenuti.

Il set di contenuti può ora essere utilizzato per copiare il contenuto tra ambienti diversi.

## Modifica di un set di contenuti {#edit-content-set}

Segui passaggi simili come per la creazione di un passaggio di contenuto. Invece di toccare o fare clic **Aggiungi set di contenuti**, seleziona un set esistente dalla console e seleziona **Modifica** dal menu ellissi.

![Modifica set di contenuti](/help/assets/edit-content-set.png)

Quando modifichi il set di contenuti, potrebbe essere necessario espandere i percorsi configurati per visualizzare i percorsi secondari esclusi.

## Copia del contenuto {#copy-content}

Una volta creato un set di contenuti, puoi utilizzarlo per copiare il contenuto. Per copiare il contenuto, effettua le seguenti operazioni.

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Dalla pagina **Panoramica**, accedi alla schermata **Ambienti**.

1. Passa a **Set di contenuti** dalla pagina **Ambienti** schermo.

1. Seleziona un set di contenuti dalla console e seleziona **Copia contenuto** dal menu ellissi.

   ![Copia del contenuto](/help/assets/copy-content.png)

   >[!NOTE]
   >
   >Un ambiente può non essere selezionabile se:
   >
   >* L&#39;utente non dispone delle autorizzazioni appropriate.
   >* L’ambiente dispone di una pipeline in esecuzione o di un’operazione di copia del contenuto in corso.


1. In **Copia contenuto** , specifica l’origine e la destinazione dell’azione di copia del contenuto.

   ![Copia del contenuto](/help/assets/copying-content.png)

1. Tocca o fai clic su **Copia**.

Viene avviato il processo di copia. Lo stato del processo di copia si riflette nella console del set di contenuti selezionato.

## Attività copia contenuto {#copy-activity}

Puoi monitorare lo stato dei processi di copia nel **Copia attività contenuto** pagina.

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Dalla pagina **Panoramica**, accedi alla schermata **Ambienti**.

1. Passa a **Copia attività contenuto** dalla pagina **Ambienti** schermo.

![Attività copia contenuto](/help/assets/copy-content-activity.png)

### Stato della copia del contenuto {#statuses}

Una volta iniziato a copiare il contenuto, il processo può avere uno dei seguenti stati.

| Stato | Descrizione |
|---|---|
| In corso | Operazione di copia del contenuto in corso |
| Non riuscito | Operazione di copia del contenuto non riuscita |
| Completato | Operazione di copia del contenuto completata |

## Limitazioni {#limitations}

Lo strumento di copia del contenuto presenta le seguenti limitazioni.

* Non è possibile eseguire una copia del contenuto da un ambiente inferiore a un ambiente superiore.
* La copia del contenuto può essere eseguita solo all’interno dello stesso livello (ad esempio autore o pubblicazione).
* Impossibile copiare il contenuto tra più programmi.
* Non è possibile eseguire operazioni di copia del contenuto simultanea sullo stesso ambiente.
* Impossibile eseguire la copia del contenuto se è in esecuzione un’operazione attiva nell’ambiente di destinazione o di origine, ad esempio una pipeline CI/CD.
* È possibile specificare fino a dieci percorsi per set di contenuti. Non ci sono limitazioni sui percorsi esclusi.
* Lo strumento di copia del contenuto non deve essere utilizzato come strumento di duplicazione o mirroring perché non può tenere traccia del contenuto spostato o eliminato sull’origine.
* Lo strumento di copia del contenuto non dispone di funzionalità di controllo delle versioni e non è in grado di rilevare automaticamente il contenuto modificato o appena creato nell’ambiente di origine in un set di contenuti dall’ultima operazione di copia del contenuto.
   * Se desideri aggiornare l’ambiente di destinazione con modifiche al contenuto solo a partire dall’ultima operazione di copia del contenuto, devi creare un set di contenuti. In questo set, specifica i percorsi nell’istanza sorgente in cui sono state apportate modifiche dall’ultima operazione di copia del contenuto.
* Le informazioni sulla versione non sono incluse in una copia del contenuto.
