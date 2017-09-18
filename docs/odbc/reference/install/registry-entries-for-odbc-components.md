---
title: Le voci del Registro di sistema per i componenti ODBC | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- subkeys [ODBC]
- installing ODBC components [ODBC], registry entries
- registry entries for components [ODBC]
- subkeys [ODBC], for components
- registry entries for components [ODBC], about registry entries
ms.assetid: c90aa8a4-6ece-48de-901c-17d23739a9ff
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d28365bb906cdaec6027a5549d5bdedebfee7a00
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="registry-entries-for-odbc-components"></a>Voci del Registro di sistema per i componenti ODBC
> [!NOTE]  
>  A partire da Windows XP e Windows Server 2003, ODBC è incluso nel sistema operativo Windows. Solo in modo esplicito, è necessario installare ODBC nelle versioni precedenti di Windows.  
  
 Il programma di installazione DLL mantiene le informazioni nel Registro di sistema su ogni componente ODBC installati. Nei computer che eseguono Microsoft Windows NT e Microsoft Windows 95/98, queste informazioni vengono archiviate in sottochiavi della chiave del Registro di sistema seguente:  
  
 HKEY_LOCAL_MACHINE  
  
 SOFTWARE  
  
 ODBC  
  
 Odbcinst.ini  
  
 Poiché una sottochiave della struttura ad albero HKEY_LOCAL_MACHINE Odbcinst.ini, le informazioni sui componenti ODBC sono disponibile per tutti gli utenti del computer.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Sottochiave ODBC Core](../../../odbc/reference/install/odbc-core-subkey.md)  
  
-   [Sottochiave ODBC Drivers](../../../odbc/reference/install/odbc-drivers-subkey.md)  
  
-   [Sottochiavi di specifica del driver](../../../odbc/reference/install/driver-specification-subkeys.md)  
  
-   [Sottochiave Default Driver](../../../odbc/reference/install/default-driver-subkey.md)  
  
-   [Sottochiave ODBC Translators](../../../odbc/reference/install/odbc-translators-subkey.md)  
  
-   [Sottochiavi di specifica delle funzioni di conversione](../../../odbc/reference/install/translator-specification-subkeys.md)