---
title: Scaricare e installare sqlpackage | Microsoft Docs
description: Scaricare e installare sqlpackage per Windows, macOS o Linux
ms.custom: tools|sos
ms.date: 06/18/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: pensivebrian
ms.author: broneill
manager: craigg
ms.openlocfilehash: ecefe3f1abe47a1a4f1af967cb1a15ee9f4dd52b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47800259"
---
# <a name="download-and-install-sqlpackage"></a>Scaricare e installare sqlpackage

Sqlpackage viene eseguito in Windows, macOS e Linux.

Scaricare e installare la versione più recente di .NET Framework e macOS e Linux anteprime:

|Piattaforma|Scarica|Data di rilascio|Versione|Compilazione|
|:---|:---|:---|:---|:---|
|Windows|[Programma di installazione](https://go.microsoft.com/fwlink/?linkid=875508)|22 giugno 2018|17.8|14.0.4079.2|
|macOS (anteprima)|[.zip](https://go.microsoft.com/fwlink/?linkid=873927)|9 maggio 2018 |0.0.1|15.0.4057.1|
|Linux (anteprima)|[.zip](https://go.microsoft.com/fwlink/?linkid=873926)|9 maggio 2018 |0.0.1|15.0.4057.1|

Per informazioni dettagliate relative alla versione più recente, vedere la [note sulla versione](sqlpackage-release-notes.md).

## <a name="get-sqlpackage-for-windows"></a>Ottenere sqlpackage per Windows

Questa versione di sqlpackage include un'esperienza di installazione di Windows standard e un file ZIP: 

1. Scaricare ed eseguire la [dacframework. msi installer per Windows](https://go.microsoft.com/fwlink/?linkid=875508).
2. Aprire una nuova finestra del prompt dei comandi ed eseguire sqlpackage.exe
    - Sqlpackage è installato per il ```C:\Program Files\Microsoft SQL Server\140\DAC\bin``` cartella

## <a name="get-sqlpackage-preview-for-macos"></a>Ottenere sqlpackage (anteprima) per macOS

1. Scaricare [sqlpackage per macOS](https://go.microsoft.com/fwlink/?linkid=873927).
2. Per estrarre il file e avviare sqlpackage, aprire una nuova finestra del terminale e digitare i comandi seguenti:

   **Installazione file con estensione zip:**

   ```bash
   mv ~/Downloads/sqlpackage-linux-<version string> ~/sqlpackage 
   echo 'export PATH="$PATH:~/sqlpackage"' >> ~/.bash_profile
   source ~/.bash_profile
   sqlpackage
   ```

## <a name="get-sqlpackage-preview-for-linux"></a>Ottenere sqlpackage (anteprima) per Linux

1. Scaricare [sqlpackage per Linux](https://go.microsoft.com/fwlink/?linkid=873926) usando uno dei programmi di installazione o l'archivio GZ:
2. Per estrarre il file e avviare sqlpackage, aprire una nuova finestra del terminale e digitare i comandi seguenti:

   **Installazione file con estensione zip:**

   ```bash
   cd ~
   mkdir sqlpackage
   unzip ~/Downloads/sqlpackage-linux-<version string>.zip ~/sqlpackage 
   echo 'export PATH="$PATH:~/sqlpackage"' >> ~/.bashrc
   source ~/.bashrc
   sqlpackage
   ```

   > [!NOTE]
   > In Debian, Red Hat e Ubuntu, è possibile dipendenze mancanti. Usare i comandi seguenti per installare queste dipendenze a seconda della versione di Linux:

   **Debian:**

   ```bash
   sudo apt-get install libuwind8
   ```

   **RedHat:**

   ```bash
   yum install libunwind
   yum install libicu
   ```

   **Ubuntu:**

   ```bash
   sudo apt-get install libunwind8

   # install the libicu library based on the Ubuntu version
   sudo apt-get install libicu52      # for 14.x
   sudo apt-get install libicu55      # for 16.x
   sudo apt-get install libicu57      # for 17.x
   sudo apt-get install libicu60      # for 18.x
   ```

## <a name="uninstall-sqlpackage-preview"></a>Disinstallare sqlpackage (anteprima)

Se è stato installato tramite il programma di installazione di Windows di sqlpackage, quindi disinstallare simile a quello di rimuovere qualsiasi applicazione Windows.

Se sqlpackage è stato installato con un file ZIP o un altro archivio, è sufficiente eliminare i file.

## <a name="supported-operating-systems"></a>Sistemi operativi supportati

Sqlpackage viene eseguito in Windows, macOS e Linux ed è supportata nelle piattaforme seguenti:

### <a name="windows"></a>Windows

- Windows 10
- Windows 8.1
- Windows 8
- Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2012
- Windows Server 2008 R2

### <a name="macos"></a>macOS

- macOS 10.13 High Sierra
- macOS 10.12 Sierra

### <a name="linux-x64"></a>Linux (x64)

- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="next-steps"></a>Next Steps

- Altre informazioni su [sqlpackage](sqlpackage.md)

[Informativa sulla privacy di Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
