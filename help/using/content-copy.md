---
title: Copia dei contenuti per coerenza in ambienti diversi
description: La copia dei contenuti in Cloud Manager consente agli utenti di copiare contenuti mutabili su richiesta dagli ambienti di produzione Adobe Experience Manager 6.x in hosting da Adobe Managed Services ad ambienti inferiori a scopo di testing.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: e3a656605ac59ca1f95985426932fddf2b53b7c9
workflow-type: tm+mt
source-wordcount: '1321'
ht-degree: 98%

---


# Copia dei contenuti per coerenza in ambienti diversi {#content-copy}

La copia dei contenuti in Cloud Manager consente agli utenti di copiare contenuti mutabili su richiesta dagli ambienti di produzione Adobe Experience Manager 6.x in hosting da Adobe Managed Services ad ambienti inferiori a scopo di testing.

## Informazioni sulla copia dei contenuti {#introduction}

I dati attuali e reali sono utili a scopo di test, convalida e accettazione da parte degli utenti. La funzione di copia dei contenuti consente di copiare contenuti dall’ambiente di produzione AEM 6.x in hosting AMS ad ambienti di staging o sviluppo. Questo flusso di lavoro supporta vari scenari di test.

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

Se modifichi il contenuto nell’ambiente di destinazione e i percorsi corrispondono, viene sovrascritto dal contenuto di origine.

Se i percorsi sono diversi, il contenuto dell’origine viene unito al contenuto della destinazione.

### Autorizzazioni {#permissions}

Per utilizzare la funzione Copia contenuto, all’utente deve essere assegnato il ruolo di **Manager implementazione** negli ambienti di origine e di destinazione.

## Creare un set di contenuti {#create-content-set}

Prima di poter copiare qualsiasi contenuto, è necessario definire un set di contenuti. Una volta definiti, i set di contenuti possono essere riutilizzati per copiare il contenuto. Per creare un set di contenuti, effettua le seguenti operazioni.

**Per creare un set di contenuti:**

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Nell’angolo in alto a sinistra della pagina, fai clic su ![icona Mostra menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) per aprire il menu a sinistra.

1. Dal menu a sinistra, nella pagina **Servizi**, fai clic su ![icona di una scatola](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Set di contenuti**.

1. Fai clic su **Aggiungi set di contenuti** vicino all’angolo in alto a destra.

   ![Set di contenuti](/help/assets/content-sets.png)

1. Nella scheda **Dettagli** della finestra di dialogo **`Add Content Set`**, nei campi **Nome** e **Descrizione** digita un nome e una descrizione facoltativa per il set di contenuti, quindi fai clic su **Continua**.

   ![Dettagli dei set di contenuti](/help/assets/add-content-set-details.png)

1. Nella scheda **Percorsi contenuto**, nel campo di testo **Percorso** specifica un percorso per i contenuti che possono essere modificati e che devono essere inclusi nel set di contenuti.

   È possibile includere solo contenuti da percorsi che iniziano con `/content`, `/conf`, `/etc`, `/var/workflow/models` o `/var/commerce`.

1. Fai clic su **![icona di aggiunta cartella](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderAdd_18_N.svg) Aggiungi percorso** per aggiungere (o includere) il percorso al set di contenuti.

1. (Facoltativo) Se necessario, ripeti i due passaggi precedenti per aggiungere altri percorsi (fino a un massimo di 50). In caso contrario, procedi al passaggio successivo.

   ![Aggiunta di percorsi al set di contenuti](/help/assets/add-content-set-paths.png)

1. (Facoltativo) Per limitare il set di contenuti, puoi specificare di escludere eventuali percorsi secondari all’interno di un percorso di contenuti incluso.

   1. A destra di un percorso di contenuti incluso che desideri limitare, fai clic su ![icona di eliminazione cartella](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg).
   1. Nel campo di testo, digita un percorso relativo al percorso principale visualizzato nella finestra di dialogo.
   1. Fai clic su ![icona di eliminazione cartella](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg) **Escludi percorso**.
   1. Se necessario, ripeti i precedenti 3 passaggi (a. - c.) di cui sopra per aggiungere altri percorsi di esclusione; non ci sono limitazioni. In caso contrario, procedi al passaggio successivo.

   ![Esclusione dei percorsi](/help/assets/add-content-set-paths-excluded.png)

1. (Facoltativo) Effettua una delle seguenti operazioni:

   1. Fai clic su ![icona a croce Dimensioni 500](https://spectrum.adobe.com/static/icons/ui_18/CrossSize500.svg) a destra di un percorso secondario escluso per eliminarlo.
   1. Fai clic su ![icona Altro](https://spectrum.adobe.com/static/icons/ui_18/More.svg) a destra di un percorso di contenuti incluso, quindi fai clic su **Modifica** o **Elimina**.

   ![Modifica dell’elenco dei percorsi](/help/assets/add-content-set-excluded-paths.png)

1. Fai clic su **Crea**. Ora puoi utilizzare il set di contenuti per copiare i contenuti in altri ambienti.

## Modificare o eliminare un set di contenuti {#edit-content-set}

Quando modifichi un set di contenuti, potrebbe essere necessario espandere i percorsi configurati per visualizzare i percorsi secondari esclusi.

**Per modificare o eliminare un set di contenuti:**

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Nell’angolo in alto a sinistra della pagina, fai clic su ![icona Mostra menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) per aprire il menu a sinistra.

1. Dal menu a sinistra, in **Servizi**, fai clic su ![icona di una scatola](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Set di contenuti**.

1. Nella tabella della pagina **Set di contenuti**, fai clic su ![icona Altro](https://spectrum.adobe.com/static/icons/ui_18/More.svg) a destra di un percorso di contenuti incluso, quindi fai clic su **Modifica** o **Elimina**.

![Modifica set di contenuti](/help/assets/edit-content-set.png)

## Copia contenuto {#copy-content}

Una volta creato un set di contenuti, puoi utilizzarlo per copiare i contenuti.

Un ambiente potrebbe non essere disponibile per la selezione se si verifica una delle seguenti condizioni:

* L’utente non dispone delle autorizzazioni necessarie.
* Nell’ambiente è attualmente in esecuzione una pipeline o un’operazione di copia del contenuto.

**Per copiare i contenuti:**

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Nell’angolo in alto a sinistra della pagina, fai clic su ![icona Mostra menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) per aprire il menu a sinistra.

1. Dal menu a sinistra, in **Servizi**, fai clic su ![icona di una scatola](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Set di contenuti**.

1. Nella tabella della pagina **Set di contenuti**, a destra di un percorso di contenuti incluso che desideri copiare, fai clic su ![icona Altro](https://spectrum.adobe.com/static/icons/ui_18/More.svg), quindi su **Copia contenuto**.

   ![Copia contenuto](/help/assets/copy-content.png)

1. Nella finestra di dialogo **Copia contenuto**, seleziona l’ambiente di **origine** e quello di **destinazione** per l’azione di copia dei contenuti.

   * Le aree dell’ambiente di destinazione devono essere un sottoinsieme di aree di un ambiente di origine.
   * Prima di eseguire un’azione di copia dei contenuti viene verificata la presenza di eventuali problemi di compatibilità. Quando viene selezionato l’ambiente di **destinazione**, il sistema convalida automaticamente gli ambienti di origine e di destinazione. Se la convalida non riesce, il processo viene interrotto e nella finestra di dialogo viene visualizzato un messaggio di errore che ne spiega il motivo.

     ![Copia del contenuto](/help/assets/copying-content.png)

1. (Facoltativo) Effettua una delle operazioni seguenti:

   1. Per *mantenere* i percorsi esclusi nell’ambiente di destinazione, seleziona **`Do not delete exclude paths from destination`**. Questa impostazione mantiene intatti i percorsi esclusi specificati nel set di contenuti.
   1. Per *rimuovere* i percorsi esclusi nell’ambiente di destinazione, deseleziona **`Do not delete exclude paths from destination`**. Questa impostazione elimina i percorsi esclusi specificati nel set di contenuti.
   1. Per copiare la cronologia delle versioni dei percorsi dall’ambiente di origine all’ambiente di destinazione, seleziona **Copia versioni**. Il processo di copia dei contenuti è notevolmente più veloce quando *non* si copia la cronologia delle versioni.

1. Fai clic su **Copia**. Lo stato del processo di copia si riflette nella console del set di contenuti selezionato.

## Controllare lo stato di un processo di copia dei contenuti {#copy-activity}

Puoi monitorare lo stato dei processi di copia nella pagina **Attività copia contenuto**.

**Per controllare lo stato di un processo di copia dei contenuti:**

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione e il programma appropriati.

1. Nell’angolo in alto a sinistra della pagina, fai clic su ![icona Mostra menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) per aprire il menu a sinistra.

1. Dal menu a sinistra, in **Servizi**, fai clic su ![icona Cronologia](https://spectrum.adobe.com/static/icons/workflow_18/Smock_History_18_N.svg) **Attività copia contenuto**.

   ![Attività copia contenuto](/help/assets/copy-content-activity.png)

   Un processo di copia del contenuto può avere uno dei seguenti stati:

   | Stato | Descrizione |
   | --- | --- |
   | In corso | Il processo di copia del contenuto è in corso. |
   | Completata | Processo di copia del contenuto completato correttamente. |
   | Non riuscita | Processo di copia del contenuto non riuscito. |

## Limitazioni della copia dei contenuti {#limitations}

* Non è possibile eseguire una copia del contenuto da un ambiente inferiore a un ambiente superiore.
* La copia del contenuto può essere eseguita solo all’interno dello stesso livello. Vale a dire, autore-autore o pubblicazione-pubblicazione.
* Non è possibile copiare il contenuto tra più programmi o aree geografiche diverse.
* La copia del contenuto per la topologia di archivio dati basata su cloud può essere eseguita solo quando l’ambiente di origine e di destinazione si trovano sullo stesso provider cloud e nella stessa area geografica.
* Non è possibile eseguire operazioni simultanee di copia del contenuto nello stesso ambiente.
* Non è possibile eseguire la copia del contenuto se è in esecuzione un’operazione attiva nell’ambiente di destinazione o di origine, ad esempio una pipeline CI/CD.
* La funzione di copia dei contenuti non deve essere utilizzata come strumento di clonazione o mirroring, in quanto non può tenere traccia dei contenuti spostati o eliminati nell’origine.
* Una volta avviata, una copia del contenuto non può essere messa in pausa o annullata.
* La funzione di copia dei contenuti duplica le risorse e i metadati di Dynamic Media, dall’ambiente superiore all’ambiente inferiore selezionato. Le risorse copiate devono quindi essere rielaborate utilizzando il [Flusso di lavoro di risorse di processo DAM](https://experienceleague.adobe.com/it/docs/experience-manager-65/content/assets/using/assets-workflow) nell’ambiente inferiore per utilizzare la rispettiva configurazione di Dynamic Media.
* [Le configurazioni Dynamic Media con dimensioni delle risorse superiori a 2 GB abilitate](https://experienceleague.adobe.com/it/docs/experience-manager-65/content/assets/dynamic/config-dms7#optional-config-dms7-assets-larger-than-2gb) non sono supportate.
* Le aree dell’ambiente di destinazione devono essere simili a un sottoinsieme delle aree dell’ambiente di origine.

## Problemi noti della funzione Copia contenuto {#known-issues}

{{content-copy-known-issues}}
