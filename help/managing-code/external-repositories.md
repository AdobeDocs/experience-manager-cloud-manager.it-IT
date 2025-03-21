---
title: Aggiungere archivi esterni in Cloud Manager - Utenti che adottano in anticipo
description: Scopri come aggiungere un archivio esterno in Cloud Manager. Cloud Manager supporta l’integrazione con gli archivi GitHub, GitLab e Bitbucket.
exl-id: 4500cacc-5e27-4bbb-b8f6-5144dac7e6da
source-git-commit: 58cdebf819f2737be5d8e129ff5b9783888f3c21
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 98%

---

# Aggiungere archivi esterni in Cloud Manager {#external-repositories}

Scopri come aggiungere un archivio esterno in Cloud Manager. Cloud Manager supporta l’integrazione con gli archivi GitHub, GitLab e Bitbucket.

>[!NOTE]
>
>Questa funzione è disponibile solo per [il programma per i primi utilizzatori](/help/release-notes/current.md#early-adoption).

## Configurare un archivio esterno

La configurazione di un archivio esterno in Cloud Manager avviene in tre passaggi:

1. [Aggiungere un archivio esterno](#add-external-repo) a un programma selezionato.
1. Fornire un token di accesso all’archivio esterno.
1. Convalidare la proprietà dell’archivio esterno.


## Aggiungere un archivio esterno {#add-ext-repo}

1. Accedi a Cloud Manager all’indirizzo [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e seleziona l’organizzazione appropriata.

1. Nella console **[Programmi personali](/help/getting-started/navigation.md#my-programs-console) seleziona il programma a cui desideri collegare un archivio esterno.


1. Nel menu laterale, in **Servizi**, seleziona l’![icona della cartella](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **Archivi**.

   ![Pagina Archivi](/help/managing-code/assets/repositories-tab.png)

1. Nell’angolo superiore a destra della pagina **Archivi** fai clic su **Aggiungi archivio**.

1. Nella finestra di dialogo **Aggiungi archivio**, seleziona **Archivio privato** per collegare un archivio Git esterno al programma in uso.

   ![Aggiungi un archivio personale](/help/managing-code/assets/repositories-private-repo-type.png)

1. In ciascun campo, fornisci i seguenti dettagli sull’archivio:

   | Campo | Descrizione |
   | --- | --- |
   | **Nome dell’archivio** | Obbligatorio. Un nome espressivo per il nuovo archivio. |
   | **URL dell’archivio** | Obbligatorio. L’URL dell’archivio.<br><br>Se utilizzi un archivio ospitato da GitHub, il percorso deve terminare in `.git`.<br>Ad esempio, *`https://github.com/org-name/repo-name.git`* (il percorso URL è solo a scopo illustrativo).<br><br>Per gli archivi esterni, è necessario utilizzare il seguente formato di percorso URL: <br>`https://git-vendor-name.com/org-name/repo-name.git`<br> o <br>`https://self-hosted-domain/org-name/repo-name.git`<br> e il fornitore Git corrispondente. |
   | **Seleziona il tipo di archivio** | Obbligatorio. Seleziona il tipo di archivio in uso: **GitHub**, **GitLab** o **BitBucket**. Se il percorso URL dell’archivio precedente include il nome del fornitore Git, ad esempio GitLab o Bitbucket, il tipo di archivio è già preselezionato. |
   | **Descrizione** | Facoltativo. Descrizione dettagliata dell’archivio. |

1. Seleziona **Salva** per aggiungere l’archivio.

1. Nella finestra di dialogo **Convalida della proprietà dell’archivio privato**, fornisci un token di accesso per convalidare la proprietà dell’archivio esterno in modo da potervi accedere.

   ![Selezione di un token di accesso esistente per un archivio](/help/managing-code/assets/repositories-exisiting-access-token.png)
   *Selezione di un token di accesso esistente per un archivio BitBucket.*

   | Tipo di token | Descrizione |
   | --- | --- |
   | **Usa token di accesso esistente** | Se hai già fornito un token di accesso all’archivio per la tua organizzazione e hai accesso a più archivi, puoi selezionare un token esistente. Utilizza l’elenco a discesa **Nome token** per scegliere il token da applicare all’archivio. In caso contrario, aggiungi un nuovo token di accesso. |
   | **Aggiungere un nuovo token di accesso** | **Tipo di archivio: GitHub**<br>• Nel campo di testo **Nome token**, digita il nome da assegnare al token di accesso che vuoi creare.<br>• Crea un token di accesso personale seguendo le istruzioni riportate nella [documentazione GitHub](https://docs.github.com/en/enterprise-server@3.14/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).<br>• Autorizzazioni richieste:<br> • `Read access to metadata`.<br> • `Read and write access to code and pull requests`.<br>• Incolla il token appena creato nel campo **Token di accesso**. |
   |  | **Tipo di archivio: GitLab**<br>• Nel campo di testo **Nome token**, digita il nome da assegnare al token di accesso che vuoi creare.<br>• Crea un token di accesso personale seguendo le istruzioni riportate nella [documentazione GitLab](https://docs.gitlab.com/user/profile/personal_access_tokens/).<br>• Autorizzazioni richieste:<br> • `api`<br> • `read_api`<br> • `read_repository`<br> • `write_repository`<br>• Incolla il token appena creato nel campo **Token di accesso**. |
   |  | **Tipo di archivio: Bitbucket**<br> • Nel campo di testo **Nome token**, digita il nome da assegnare al token di accesso che vuoi creare.<br>• Crea un token di accesso all&#39;archivio utilizzando la [documentazione Bitbucket](https://support.atlassian.com/bitbucket-cloud/docs/create-a-repository-access-token/).<br>• Autorizzazioni richieste:<br> • `Read and write access to code and pull requests`. |

   >[!NOTE]
   >
   >La funzionalità **Aggiungi nuovo token di accesso** è attualmente in fase di adozione anticipata. Ulteriori funzionalità sono in fase di pianificazione. Di conseguenza, le autorizzazioni necessarie per i token di accesso potrebbero cambiare. Inoltre, è possibile che l’interfaccia utente per la gestione dei token venga aggiornata, includendo eventuali funzionalità quali le date di scadenza dei token. Inoltre, potrebbero essere aggiunti controlli automatici per garantire che i token collegati agli archivi rimangano validi.

1. Fai clic su **Convalida**.

Dopo la convalida, l’archivio esterno è pronto per essere utilizzato e collegato a una pipeline.

## Collegare un archivio esterno convalidato a una pipeline {#validate-ext-repo}

1. Aggiungi o modifica una pipeline:
   * [Aggiungere una pipeline di produzione](/help/using/production-pipelines.md)
   * [Aggiungere una pipeline non di produzione](/help/using/non-production-pipelines.md)
   * [Modificare una pipeline](/help/using/managing-pipelines.md#editing-pipelines)

   ![Archivio del codice sorgente della pipeline e ramo Git](/help/managing-code/assets/pipeline-repo-gitbranch.png)
   *Finestra di dialogo Aggiungi pipeline non di produzione con l’archivio selezionato e il ramo Git.*

1. Quando aggiungi o modifichi una pipeline, per specificare il percorso **Codice sorgente** per la pipeline nuova o esistente, scegli l‘archivio esterno che desideri utilizzare dall‘elenco a discesa **Archivio**.

1. Nell’elenco a discesa **Ramo Git** seleziona il ramo di origine della pipeline.

1. Fai clic su **Salva**.


>[!TIP]
>
>Per informazioni dettagliate sulla gestione degli archivi in Cloud Manager, consulta [Archivi di Cloud Manager](/help/managing-code/managing-repositories.md).


## Limitazioni

Gli archivi esterni non possono essere collegati alle pipeline di configurazione.

<!-- THIS BULLET REMOVED AS PER https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release. THEY CAN NOW START AUTOMATICALLY

* Pipelines using external repositories (excluding GitHub-hosted repositories) and the **Deployment Trigger** option [!UICONTROL **On Git Changes**], triggers are not automatically started. They must be manually started. -->

