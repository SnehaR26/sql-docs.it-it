---
title: Introduzione ai contenitori di SQL Server in Docker | Microsoft Docs
description: Questa Guida introduttiva illustra come usare Docker per eseguire SQL Server 2017 e le immagini del contenitore 2019. Si userà quindi sqlcmd per creare un database ed eseguire query su di esso.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/07/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.custom: sql-linux
ms.prod_service: linux
ms.assetid: 82737f18-f5d6-4dce-a255-688889fdde69
moniker: '>= sql-server-linux-2017 || >= sql-server-2017 || =sqlallproducts-allversions'
ms.openlocfilehash: ddf8882cfe4c51194515b181fb6b9e6e80426710
ms.sourcegitcommit: 0d6e4cafbb5d746e7d00fdacf8f3ce16f3023306
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/11/2018
ms.locfileid: "49085287"
---
# <a name="quickstart-run-sql-server-container-images-with-docker"></a>Guida introduttiva: Immagini del contenitore in esecuzione SQL Server con Docker

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

In questa guida introduttiva si usa Docker per effettuare il pull ed eseguire l'immagine del contenitore di SQL Server 2017, [mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/). Ci si connette quindi con **sqlcmd** per creare il primo database ed eseguire query.

> [!TIP]
> Se si vuole provare l'immagine di anteprima di SQL Server 2019, vedere la [versione di anteprima di SQL Server 2019 di questo articolo](quickstart-install-connect-docker.md?view=sql-server-linux-ver15).

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

In questa Guida introduttiva, è usare Docker per il pull ed eseguire l'immagine del contenitore, anteprima SQL Server 2019 [mssql-server](https://hub.docker.com/r/microsoft/mssql-server). Ci si connette quindi con **sqlcmd** per creare il primo database ed eseguire query.

::: moniker-end

Questa immagine è costituita da SQL Server in esecuzione su Linux basato su Ubuntu 16.04. Può essere usata con il motore Docker 1.8 o versione successiva su Linux o in Docker per Mac/Windows. Questa Guida introduttiva è incentrata in particolare sull'uso di SQL Server in **linux** immagine. L'immagine Windows non è argomento di questa guida, ma è possibile ottenere informazioni su di essa nella [pagina mssql-server-windows-developer dell'hub Docker](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/).

## <a id="requirements"></a> Prerequisiti

- Motore Docker 1.8 o versione successiva in qualsiasi distribuzione di Linux supportata oppure Docker per Mac/Windows. Per altre informazioni, vedere [Installare Docker](https://docs.docker.com/engine/installation/).
- Almeno 2 GB di spazio su disco.
- Almeno 2 GB di RAM.
- [Requisiti di sistema per SQL Server su Linux](sql-server-linux-setup.md#system).

<!--The following H2 is versioned for 2017 and 2019. Much of the content is duplicated, so
any changes to one section should be duplicated in the other-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="pullandrun2017"></a> Eseguire il pull ed eseguire l'immagine del contenitore

1. Eseguire il pull dal registro contenitori di Microsoft l'immagine del contenitore SQL Server 2017 su Linux.

   ```bash
   sudo docker pull mcr.microsoft.com/mssql/server:2017-latest
   ```

   ```PowerShell
   docker pull mcr.microsoft.com/mssql/server:2017-latest
   ```

   > [!TIP]
   > Se si vuole provare l'immagine di anteprima di SQL Server 2019, vedere la [versione di anteprima di SQL Server 2019 di questo articolo](quickstart-install-connect-docker.md?view=sql-server-linux-ver15#pullandrun2019).

   Il comando riportato sopra esegue il pull dell'immagine del contenitore di SQL Server 2017 più recente. Se si vuole eseguire il pull di un'immagine specifica, aggiungere un segno di due punti e il nome del tag (ad esempio `mcr.microsoft.com/mssql/server:2017-GA-ubuntu`). Per informazioni su tutte le immagini disponibili, vedere [pagina dell'hub Docker mssql-server](https://hub.docker.com/r/microsoft/mssql-server).

   Per i comandi di bash in questo articolo, `sudo` viene usato. In MacOS, `sudo` potrebbe non essere necessaria. In Linux, se non si desidera utilizzare `sudo` per eseguire Docker, è possibile configurare un **docker** gruppo e aggiungere utenti a tale gruppo. Per altre informazioni, vedere [passaggi di post-installazione per Linux](https://docs.docker.com/install/linux/linux-postinstall/).

2. Per eseguire l'immagine del contenitore con Docker, è possibile usare il comando seguente da una shell Bash (Linux/macOS) o da un prompt dei comandi PowerShell con privilegi elevati.

   ```bash
   sudo docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=<YourStrong!Passw0rd>' \
      -p 1433:1433 --name sql1 \
      -d mcr.microsoft.com/mssql/server:2017-latest
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=<YourStrong!Passw0rd>" `
      -p 1433:1433 --name sql1 `
      -d mcr.microsoft.com/mssql/server:2017-latest
   ```

   > [!NOTE]
   > La password deve essere conforme ai criteri password predefiniti di SQL Server, altrimenti il contenitore non potrà configurare SQL Server e smetterà di funzionare. Per impostazione predefinita, la password deve essere composta da almeno 8 caratteri e contenere caratteri di tre delle quattro categorie seguenti: lettere maiuscole, lettere minuscole, cifre in base 10 e simboli. È possibile esaminare il log degli errori eseguendo il comando [docker logs](https://docs.docker.com/engine/reference/commandline/logs/).

   > [!NOTE]
   > Per impostazione predefinita, viene creato un contenitore con l'edizione Developer di SQL Server 2017. Il processo di esecuzione delle edizioni di produzione nei contenitori è leggermente diverso. Per altre informazioni, vedere [Run production container images](sql-server-linux-configure-docker.md#production) (Eseguire immagini del contenitore di produzione).

   La tabella seguente offre una descrizione dei parametri dell'esempio `docker run` precedente:

   | Parametro | Description |
   |-----|-----|
   | **-e 'ACCEPT_EULA=Y'** |  Impostare la variabile **ACCEPT_EULA** su qualsiasi valore per confermare l'accettazione delle [condizioni di licenza ](http://go.microsoft.com/fwlink/?LinkId=746388). Impostazione obbligatoria per l'immagine di SQL Server. |
   | **-e ' SA_PASSWORD =\<YourStrong! Passw0rd\>'** | Specificare la password complessa composta da almeno 8 caratteri e conforme ai [requisiti per le password di SQL Server](../relational-databases/security/password-policy.md). Impostazione obbligatoria per l'immagine di SQL Server. |
   | **-p 1433:1433** | Eseguire il mapping di una porta TCP nell'ambiente host (primo valore) con una porta TCP nel contenitore (secondo valore). In questo esempio, SQL Server è in ascolto sulla porta TCP 1433 nel contenitore e questa funzionalità è esposta alla porta 1433, nell'host. |
   | **--name sql1** | Specificare un nome personalizzato per il contenitore, invece di un nome generato in modo casuale. Se si eseguono più contenitori, non è possibile riutilizzare questo stesso nome. |
   | **MCR.microsoft.com/MSSQL/Server:2017-Latest** | Immagine del contenitore di SQL Server 2017 su Linux. |

3. Per visualizzare i contenitori di Docker, usare il comando `docker ps`.

   ```bash
   sudo docker ps -a
   ```

   ```PowerShell
   docker ps -a
   ```

   L'output risultante dovrebbe essere simile allo screenshot seguente:

   ![Output del comando ps di Docker](./media/sql-server-linux-setup-docker/docker-ps-command.png)

4. Se nella colonna **STATUS** è impostato lo stato**Up**, SQL Server è in esecuzione nel contenitore e in ascolto sulla porta specificata nella colonna **PORTS**. Se la colonna **STATUS** del contenitore di SQL Server è impostata su **Exited**, vedere la [sezione relativa alla risoluzione dei problemi della guida alla configurazione](sql-server-linux-configure-docker.md#troubleshooting).

Anche il parametro `-h` (nome host) è utile, ma non viene usato in questa esercitazione per semplicità. Cambia il nome interno del contenitore sostituendolo con un valore personalizzato. È il nome che viene restituito nella query Transact-SQL seguente:

```sql
SELECT @@SERVERNAME,
    SERVERPROPERTY('ComputerNamePhysicalNetBIOS'),
    SERVERPROPERTY('MachineName'),
    SERVERPROPERTY('ServerName')
```

L'impostazione di `-h` e `--name` sullo stesso valore è un buon modo per identificare facilmente il contenitore di destinazione.

::: moniker-end
<!--End of 2017 "Pull and run" section-->

<!--This is the 2019 version of the "Pull and run" section-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="pullandrun2019"></a> Eseguire il pull ed eseguire l'immagine del contenitore

1. Caricare l'immagine del contenitore SQL Server 2019 CTP 2.0 su Linux da Docker Hub.

   ```bash
   sudo docker pull mcr.microsoft.com/mssql/server:vNext-CTP2.0-ubuntu
   ```

   ```PowerShell
   docker pull mcr.microsoft.com/mssql/server:vNext-CTP2.0-ubuntu
   ```

   > [!TIP]
   > Questa Guida introduttiva Usa l'immagine Docker di SQL Server 2019 CTP 2.0. Se si vuole eseguire l'immagine di SQL Server 2017, vedere la [versione di SQL Server 2017 di questo articolo](quickstart-install-connect-docker.md?view=sql-server-linux-2017#pullandrun2017).

   Il comando precedente esegue il pull l'immagine del contenitore SQL Server 2019 CTP 2.0 più recente basato su Ubuntu. Per usare invece le immagini contenitore basate su RedHat, vedere [le immagini contenitore basate su RHEL eseguire](sql-server-linux-configure-docker.md#rhel). Se si vuole eseguire il pull di un'immagine specifica, aggiungere un segno di due punti e il nome del tag (ad esempio `mcr.microsoft.com/mssql/server:2017-GA`). Per vedere tutte le immagini disponibili, vedere la [pagina mssql-server-linux dell'hub Docker](https://hub.docker.com/r/microsoft/mssql-server-linux/tags/).

   Per i comandi di bash in questo articolo, `sudo` viene usato. In MacOS, `sudo` potrebbe non essere necessaria. In Linux, se non si desidera utilizzare `sudo` per eseguire Docker, è possibile configurare un **docker** gruppo e aggiungere utenti a tale gruppo. Per altre informazioni, vedere [passaggi di post-installazione per Linux](https://docs.docker.com/install/linux/linux-postinstall/).

2. Per eseguire l'immagine del contenitore con Docker, è possibile usare il comando seguente da una shell Bash (Linux/macOS) o da un prompt dei comandi PowerShell con privilegi elevati.

   ```bash
   sudo docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=<YourStrong!Passw0rd>' \
      -p 1433:1433 --name sql1 \
      -d mcr.microsoft.com/mssql/server:vNext-CTP2.0-ubuntu
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=<YourStrong!Passw0rd>" `
      -p 1433:1433 --name sql1 `
      -d mcr.microsoft.com/mssql/server:vNext-CTP2.0-ubuntu
   ```

   > [!NOTE]
   > La password deve essere conforme ai criteri password predefiniti di SQL Server, altrimenti il contenitore non potrà configurare SQL Server e smetterà di funzionare. Per impostazione predefinita, la password deve essere composta da almeno 8 caratteri e contenere caratteri di tre delle quattro categorie seguenti: lettere maiuscole, lettere minuscole, cifre in base 10 e simboli. È possibile esaminare il log degli errori eseguendo il comando [docker logs](https://docs.docker.com/engine/reference/commandline/logs/).

   > [!NOTE]
   > Per impostazione predefinita, viene creato un contenitore con l'edizione Developer di SQL Server 2019 CTP 2.0.

   La tabella seguente offre una descrizione dei parametri dell'esempio `docker run` precedente:

   | Parametro | Description |
   |-----|-----|
   | **-e 'ACCEPT_EULA=Y'** |  Impostare la variabile **ACCEPT_EULA** su qualsiasi valore per confermare l'accettazione delle [condizioni di licenza ](http://go.microsoft.com/fwlink/?LinkId=746388). Impostazione obbligatoria per l'immagine di SQL Server. |
   | **-e ' SA_PASSWORD =\<YourStrong! Passw0rd\>'** | Specificare la password complessa composta da almeno 8 caratteri e conforme ai [requisiti per le password di SQL Server](../relational-databases/security/password-policy.md). Impostazione obbligatoria per l'immagine di SQL Server. |
   | **-p 1433:1433** | Eseguire il mapping di una porta TCP nell'ambiente host (primo valore) con una porta TCP nel contenitore (secondo valore). In questo esempio, SQL Server è in ascolto sulla porta TCP 1433 nel contenitore e questa funzionalità è esposta alla porta 1433, nell'host. |
   | **--name sql1** | Specificare un nome personalizzato per il contenitore, invece di un nome generato in modo casuale. Se si eseguono più contenitori, non è possibile riutilizzare questo stesso nome. |
   | **MCR.microsoft.com/MSSQL/Server:vNext-CTP2.0-Ubuntu** | L'immagine del contenitore Linux di SQL Server 2019 CTP 2.0. |

3. Per visualizzare i contenitori di Docker, usare il comando `docker ps`.

   ```bash
   sudo docker ps -a
   ```

   ```PowerShell
   docker ps -a
   ```

   L'output risultante dovrebbe essere simile allo screenshot seguente:

   ![Output del comando ps di Docker](./media/sql-server-linux-setup-docker/docker-ps-command.png)

4. Se nella colonna **STATUS** è impostato lo stato**Up**, SQL Server è in esecuzione nel contenitore e in ascolto sulla porta specificata nella colonna **PORTS**. Se la colonna **STATUS** del contenitore di SQL Server è impostata su **Exited**, vedere la [sezione relativa alla risoluzione dei problemi della guida alla configurazione](sql-server-linux-configure-docker.md#troubleshooting).

Anche il parametro `-h` (nome host) è utile, ma non viene usato in questa esercitazione per semplicità. Cambia il nome interno del contenitore sostituendolo con un valore personalizzato. È il nome che viene restituito nella query Transact-SQL seguente:

```sql
SELECT @@SERVERNAME,
    SERVERPROPERTY('ComputerNamePhysicalNetBIOS'),
    SERVERPROPERTY('MachineName'),
    SERVERPROPERTY('ServerName')
```

L'impostazione di `-h` e `--name` sullo stesso valore è un buon modo per identificare facilmente il contenitore di destinazione.

::: moniker-end
<!--End of 2019 "Pull and run" section-->

## <a id="sapassword"></a> Modificare la password dell'amministratore di sistema

[!INCLUDE [Change docker password](../includes/sql-server-linux-change-docker-password.md)]

## <a name="connect-to-sql-server"></a>Connessione a SQL Server

La procedura seguente usa lo strumento da riga di comando di SQL Server, **sqlcmd**, all'interno del contenitore per stabilire la connessione a SQL Server.

1. Usare il comando `docker exec -it` per avviare una shell Bash interattiva all'interno del contenitore in esecuzione. Nell'esempio seguente `sql1` è il nome specificato dal parametro `--name`quando è stato creato il contenitore.

   ```bash
   sudo docker exec -it sql1 "bash"
   ```

   ```PowerShell
   docker exec -it sql1 "bash"
   ```

1. Una volta all'interno del contenitore, eseguire la connessione in locale con sqlcmd. Sqlcmd non è incluso nel percorso per impostazione predefinita, quindi occorre specificare il percorso completo.

   ```bash
   /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P '<YourNewStrong!Passw0rd>'
   ```

   > [!TIP]
   > È possibile omettere la password nella riga di comanda perché sia richiesto di essere immessa.

1. Se la connessione viene eseguita correttamente, il prompt dei comandi **sqlcmd** sarà: `1>`.

## <a name="create-and-query-data"></a>Creare i dati e recuperarli tramite query

Nelle sezioni seguenti viene descritto l'uso di **sqlcmd** e Transact-SQL per creare un nuovo database, aggiungere dati ed eseguire una query semplice.

### <a name="create-a-new-database"></a>Creare un nuovo database

La seguente procedura consente di creare un nuovo database denominato `TestDB`.

1. Dal prompt dei comandi **sqlcmd** incollare il comando seguente di Transact-SQL per creare un database di test:

   ```sql
   CREATE DATABASE TestDB
   ```

1. Nella riga successiva scrivere una query perché vengano restituiti i nomi di tutti database nel server:

   ```sql
   SELECT Name from sys.Databases
   ```

1. I due comandi precedenti non sono stati eseguiti immediatamente. È necessario digitare `GO` in una nuova riga per eseguire i comandi precedenti:

   ```sql
   GO
   ```

### <a name="insert-data"></a>Inserire i dati

Creare poi una nuova tabella `Inventory` e inserire due nuove righe.

1. Dal prompt dei comandi **sqlcmd** spostare il contesto nel nuovo database `TestDB`:

   ```sql
   USE TestDB
   ```

1. Creare una nuova tabella denominata `Inventory`:

   ```sql
   CREATE TABLE Inventory (id INT, name NVARCHAR(50), quantity INT)
   ```

1. Inserire i dati nella nuova tabella:

   ```sql
   INSERT INTO Inventory VALUES (1, 'banana', 150); INSERT INTO Inventory VALUES (2, 'orange', 154);
   ```

1. Digitare `GO` per eseguire i comandi precedenti:

   ```sql
   GO
   ```

### <a name="select-data"></a>Selezionare i dati

A questo punto, eseguire una query per restituire i dati dalla tabella `Inventory`.

1. Dal prompt dei comandi **sqlcmd** immettere una query che restituisca le righe dalla tabella `Inventory` che ne contiene oltre 152:

   ```sql
   SELECT * FROM Inventory WHERE quantity > 152;
   ```

1. Eseguire il comando:

   ```sql
   GO
   ```

### <a name="exit-the-sqlcmd-command-prompt"></a>Uscire dal prompt dei comandi sqlcmd

1. Per terminare la sessione **sqlcmd**, digitare `QUIT`:

   ```sql
   QUIT
   ```

1. Per uscire dal prompt dei comandi interattivo nel contenitore, digitare `exit`. Dopo la chiusura della shell Bash interattiva, il contenitore continua l'esecuzione.

## <a id="connectexternal"></a> Eseguire la connessione dall'esterno del contenitore

È anche possibile connettersi all'istanza di SQL Server nel computer che esegue Docker da uno strumento esterno Linux, Windows o macOS che supporti le connessioni SQL.

La procedura seguente usa **sqlcmd** all'esterno del contenitore per stabilire la connessione a SQL Server in esecuzione nel contenitore. Questa procedura presuppone che gli strumenti da riga di comando di SQL Server siano già installati all'esterno del contenitore. Gli stessi principi valgono quando si usano altri strumenti, ma il processo di connessione è specifico di ogni strumento.

1. Trovare l'indirizzo IP del computer che ospita il contenitore. Su Linux usare **ifconfig** o **ip addr**. Su Windows usare **ipconfig**.

1. Eseguire sqlcmd specificando l'indirizzo IP e la porta mappata alla porta 1433 nel contenitore. In questo esempio, che è la stessa porta, la porta 1433, nel computer host. Se è stata specificata un'altra porta mappata nel computer host, è necessario utilizzarlo qui.

   ```bash
   sqlcmd -S 10.3.2.4,1433 -U SA -P '<YourNewStrong!Passw0rd>'
   ```

   ```PowerShell
   sqlcmd -S 10.3.2.4,1433 -U SA -P "<YourNewStrong!Passw0rd>"
   ```

1. Eseguire i comandi Transact-SQL. Al termine, digitare `QUIT`.

Altri strumenti usati comunemente per connettersi a SQL Server sono:

- [Visual Studio Code](sql-server-linux-develop-use-vscode.md)
- [SQL Server Management Studio (SSMS) per Windows](sql-server-linux-manage-ssms.md)
- [Studio di dati di Azure (anteprima)](../azure-data-studio/what-is.md)
- [mssql-cli (Preview)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/)

## <a name="remove-your-container"></a>Rimuovere il contenitore

Se si vuole rimuovere il contenitore di SQL Server usato in questa esercitazione, eseguire i comandi seguenti:

```bash
sudo docker stop sql1
sudo docker rm sql1
```

```PowerShell
docker stop sql1
docker rm sql1
```

> [!WARNING]
> Se si arresta e si rimuove un contenitore, i dati di SQL Server eventualmente presenti nel contenitore vengono eliminati in modo definitivo. Se occorre conservare i dati, [creare un file di backup e copiarlo all'esterno del contenitore](tutorial-restore-backup-in-sql-server-container.md) oppure usare una [tecnica di persistenza dei dati del contenitore](sql-server-linux-configure-docker.md#persist).

## <a name="docker-demo"></a>Demo di Docker

Se, dopo aver provato a usare l'immagine del contenitore di SQL Server per Docker, si vuole sapere come si può usare questo strumento per migliorare le attività di sviluppo e test, il video seguente illustra l'uso di Docker in uno scenario di integrazione continua e distribuzione.

> [!VIDEO https://channel9.msdn.com/Events/Connect/2017/T152/player]

## <a name="next-steps"></a>Passaggi successivi

Per un'esercitazione sul ripristino dei file di backup di database in un contenitore, vedere [Restore a SQL Server database in a Linux Docker container](tutorial-restore-backup-in-sql-server-container.md) (Ripristinare un database di SQL Server in un contenitore Docker Linux). Per esplorare altri scenari, quali l'esecuzione di più contenitori, la persistenza dei dati e la risoluzione dei problemi, vedere [immagini del contenitore configura SQL Server in Docker](sql-server-linux-configure-docker.md).

Nel [repository GitHub mssql-docker](https://github.com/Microsoft/mssql-docker) sono inoltre disponibili risorse, feedback e documentazione su problemi noti.
