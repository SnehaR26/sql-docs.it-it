---
title: Comando oggetto Panoramica | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- command object [ADO]
ms.assetid: e84a14b1-3c2a-4f7d-a966-9e08a93948df
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 808c63575b93f9e4fa3b6459d2111637021218c1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47759855"
---
# <a name="command-object-overview"></a>Panoramica dell'oggetto Command
Con un **comando** dell'oggetto, è possibile eseguire le operazioni seguenti:  
  
-   Definire il testo del comando (ad esempio, un'istruzione SQL o una stored procedure) eseguibile tramite il **CommandText** proprietà.  
  
-   Definire le query con parametri o argomenti di stored procedure utilizzando **parametri** gli oggetti e il **parametri** raccolta.  
  
-   Eseguire un comando e restituire un **Recordset** dell'oggetto, se appropriato, tramite il **Execute** (metodo).  
  
-   Specificare il tipo di comando usando il **CommandType** proprietà prima dell'esecuzione per ottimizzare le prestazioni.  
  
-   Specificare le informazioni specifiche sul testo del comando utilizzando il **sottolinguaggio** proprietà delle **comando** oggetto.  
  
-   Controllare se il provider deve salvare una versione preparata (o compilata) del comando prima dell'esecuzione utilizzando il **Prepared** proprietà.  
  
-   Impostare il numero di secondi di attesa di un provider per un comando da eseguire tramite il **CommandTimeout** proprietà.  
  
-   Associare una connessione aperta con un **comandi** oggetto impostando relativo **ActiveConnection** proprietà.  
  
-   Impostare il **Name** proprietà per identificare le **comando** oggetto come un metodo sull'oggetto associato **connessione** oggetto.  
  
-   Passare un **comandi** dell'oggetto per il **origine** proprietà di un **Recordset** per ottenere i dati.  
  
-   Passare un **Stream** oggetto che contiene un comando (ad esempio, un comando XML) a un provider che lo supporta.
