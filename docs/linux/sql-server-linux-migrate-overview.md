---
title: La migrazione dei database di SQL Server in Linux | Documenti Microsoft
description: In questo argomento vengono descritte le diverse opzioni per la migrazione di database e i dati di SQL Server in Linux.
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 1619489d-377a-4f32-8930-d4f536539689
ms.custom: H1Hack27Feb2017
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: 61b4ba948df071768380d4a6f2b4ddc4421692d8
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="migrate-databases-and-structured-data-to-sql-server-on-linux"></a>Eseguire la migrazione di database e i dati strutturati a SQL Server in Linux 

È possibile eseguire la migrazione dei database e dei dati a SQL Server 2017 RC2 in esecuzione in Linux. Il metodo che si sceglie di usare dipende dai dati di origine e lo scenario specifico. Le sezioni seguenti forniscono le procedure consigliate per i diversi scenari di migrazione.

## <a name="migrate-from-sql-server-on-windows"></a>Eseguire la migrazione da SQL Server in Windows
Se si desidera eseguire la migrazione di database di SQL Server in Windows a 2017 di SQL Server in Linux, la tecnica consigliata consiste nell'utilizzare SQL Server backup e ripristino.

1. Creare un backup del database nel computer Windows.
2. Trasferire il file di backup nel computer di destinazione SQL Server per Linux.
3. Ripristinare il backup del computer Linux. 

Per un'esercitazione sulla migrazione di un database tramite backup e ripristino, vedere l'argomento seguente:

- [Ripristinare un database di SQL Server da Windows a Linux](sql-server-linux-migrate-restore-database.md).

È inoltre possibile esportare il database in un file BACPAC (un file compresso che contiene i dati e lo schema di database). Se si dispone di un file BACPAC, è possibile trasferire questo file nel computer Linux e quindi importarlo in SQL Server. Per altre informazioni, vedere gli argomenti seguenti:

- [Esportare e importare un database con SSMS o SqlPackage.exe](sql-server-linux-migrate-ssms.md)

## <a name="migrate-from-other-database-servers"></a>Eseguire la migrazione da altri server di database
È possibile migrare i database in altri sistemi di database di SQL Server 2017 in Linux. Sono inclusi i database Microsoft Access, DB2, MySQL, Oracle e Sybase. In questo scenario, utilizzare il SQL Server Management Assistant (SSMA) per automatizzare la migrazione a SQL Server in Linux. Per ulteriori informazioni, vedere [SSMA utilizzare per la migrazione dei database di SQL Server in Linux](sql-server-linux-migrate-ssma.md).  

## <a name="migrate-structured-data"></a>Eseguire la migrazione di dati strutturati
Sono inoltre disponibili le tecniche per l'importazione di dati non elaborati. File di dati che sono stati esportati da altre origini dati o il database potrebbe avere strutturato. In questo caso, è possibile utilizzare lo strumento di bcp per l'inserimento bulk dei dati. In alternativa, è possibile eseguire SQL Server Integration Services in Windows per importare i dati in un database di SQL Server in Linux. SQL Server Integration Services consente di eseguire trasformazioni più complesse dei dati durante l'importazione. 

Per ulteriori informazioni su queste tecniche, vedere gli argomenti seguenti:

- [Copia bulk di dati con bcp](sql-server-linux-migrate-bcp.md)
- [Estrarre, trasformare e caricare i dati per SQL Server in Linux con SSIS](sql-server-linux-migrate-ssis.md) 
