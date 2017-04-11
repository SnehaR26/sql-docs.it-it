---
title: "Propriet&#224; personalizzate di Excel | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bdcc72b8-8950-47bd-88bf-5db6d48cc6bf
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# Propriet&#224; personalizzate di Excel
  **Proprietà personalizzate delle origini**  
  
 L'origine Excel include sia proprietà personalizzate che le proprietà comuni a tutti i componenti del flusso di dati.  
  
 Nella tabella seguente vengono descritte le proprietà personalizzate dell'origine Excel. Tutte le proprietà sono di lettura/scrittura.  
  
|Nome proprietà|Tipo di dati|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Valore intero|Modalità utilizzata per accedere al database. I valori possibili sono **OpenRowset**, **OpenRowset da variabile**, **Comando SQL**e **Comando SQL da variabile**. Il valore predefinito è **OpenRowset**.|  
|CommandTimeout|Valore intero|Numero di secondi prima del timeout del comando.  Il valore 0 indica un timeout infinito.<br /><br /> **Nota** Questa proprietà non è disponibile in **Editor origine Excel**, ma può essere impostata tramite **Editor avanzato**.|  
|OpenRowset|String|Nome dell'oggetto di database utilizzato per aprire un set di righe.|  
|OpenRowsetVariable|String|Variabile che contiene il nome dell'oggetto di database utilizzato per aprire un set di righe.|  
|ParameterMapping|String|Mapping tra i parametri nel comando SQL e le variabili.|  
|SqlCommand|String|Comando SQL da eseguire.|  
|SqlCommandVariable|String|Variabile che contiene il comando SQL da eseguire.|  
  
 L'output e le colonne di output dell'origine Excel non includono proprietà personalizzate.  
  
 Per altre informazioni, vedere [Origine Excel](../../integration-services/data-flow/excel-source.md).  
  
 **Proprietà personalizzate delle destinazioni**  
  
 La destinazione Excel include sia proprietà personalizzate che le proprietà comuni a tutti i componenti del flusso di dati.  
  
 Nella tabella seguente vengono descritte le proprietà personalizzate della destinazione Excel. Tutte le proprietà sono di lettura/scrittura.  
  
|Nome proprietà|Tipo di dati|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Integer (enumerazione)|Valore che specifica la modalità di accesso della destinazione al relativo database di destinazione.<br /><br /> Di seguito vengono indicati i possibili valori della proprietà.<br /><br /> **OpenRowset** (0): specificare il nome di una tabella o di una vista.<br /><br /> **OpenRowset da variabile** (1): specificare il nome di una variabile contenente il nome di una tabella o di una vista.<br /><br /> **OpenRowset con Fastload** (3): specificare il nome di una tabella o di una vista.<br /><br /> **OpenRowset con Fastload da variabile** (4): specificare il nome di una variabile contenente il nome di una tabella o di una vista.<br /><br /> **Comando SQL** (2): specificare un'istruzione SQL.|  
|CommandTimeout|Valore intero|Numero massimo di secondi durante i quali è possibile eseguire il comando SQL prima del timeout. Il valore **0** corrisponde a un intervallo infinito. Il valore predefinito di questa proprietà è **0**.<br /><br /> Nota: questa proprietà non è disponibile in **Editor destinazione Excel**, ma può essere impostata tramite **Editor avanzato**.|  
|FastLoadKeepIdentity|Boolean|Valore che specifica se copiare i valori Identity durante il caricamento dei dati. Questa proprietà è disponibile solo quando si utilizza una delle opzioni di caricamento rapido. Il valore predefinito di questa proprietà è **False**.|  
|FastLoadKeepNulls|Boolean|Valore che specifica se copiare i valori Null durante il caricamento dei dati. Questa proprietà è disponibile solo con una delle opzioni di caricamento rapido. Il valore predefinito di questa proprietà è **False**.|  
|FastLoadMaxInsertCommitSize|Valore intero|Valore che specifica le dimensioni del batch di cui la destinazione Excel tenta di eseguire il commit durante le operazioni di caricamento rapido. Il valore predefinito è **2147483647**. Il valore **0** indica una singola operazione di commit in seguito all'elaborazione di tutte le righe.|  
|FastLoadOptions|String|Raccolta di opzioni di caricamento rapido. Tra le opzioni di caricamento rapido sono inclusi il blocco delle tabelle e la verifica dei vincoli. È possibile specificare una, nessuna o entrambe le opzioni.<br /><br /> Nota: alcune opzioni per questa proprietà non sono disponibili in **Editor destinazione Excel**, ma possono essere impostate usando **Editor avanzato**.|  
|OpenRowset|String|Quando AccessMode è **OpenRowset**, nome della tabella o della vista a cui accede la destinazione Excel.|  
|OpenRowsetVariable|String|Quando AccessMode è **OpenRowset da variabile**, nome della variabile che contiene il nome della tabella o della vista a cui accede la destinazione Excel.|  
|SqlCommand|String|Quando AccessMode è **Comando SQL**, istruzione Transact-SQL usata dalla destinazione Excel per specificare le colonne di destinazione per i dati.|  
  
 L'input e le colonne di input della destinazione Excel non includono proprietà personalizzate.  
  
 Per altre informazioni, vedere [Destinazione Excel](../../integration-services/data-flow/excel-destination.md).  
  
## Vedere anche  
 [Proprietà comuni](../Topic/Common%20Properties.md)  
  
  