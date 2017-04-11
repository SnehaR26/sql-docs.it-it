---
title: "Codificare e decodificare identificatori di SLQ Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb9fe0d3-e432-42d3-b324-64dc908b544a
caps.latest.revision: 7
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 7
---
# Codificare e decodificare identificatori di SLQ Server
  Gli identificatori delimitati di SQL Server possono contenere caratteri non supportati nei percorsi di Windows PowerShell. È possibile specificare questi caratteri codificando i valori esadecimali.  
  
1.  **Prima di iniziare:**  [Limitazioni e restrizioni](#LimitationsRestrictions)  
  
2.  **Per elaborare caratteri speciali:**  [Codifica di un identificatore](#EncodeIdent), [Decodifica di un identificatore](#DecodeIdent)  
  
## Prima di iniziare  
 I caratteri non supportati nei nomi dei percorsi di Windows PowerShell possono essere rappresentati o codificati come il carattere "%" seguito dal valore esadecimale del modello di bit che rappresenta il carattere, come in "**%**xx". La codifica può sempre essere utilizzata per gestire i caratteri non supportati nei percorsi di Windows PowerShell.  
  
 Il cmdlet** Encode-SqlName** accetta come input un identificatore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Viene restituita una stringa con tutti i caratteri non supportati dal linguaggio di Windows PowerShell codificati con "% xx". Il cmdlet **Decode-SqlName** accetta come input un identificatore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] codificato e restituisce l'identificatore originale.  
  
###  <a name="LimitationsRestrictions"></a> Limitazioni e restrizioni  
 I cmdlet **Encode-Sqlname** e **Decode-Sqlname** codificano o decodificano solo i caratteri consentiti negli identificatori delimitati di SQL Server, ma non sono supportati nei percorsi di PowerShell. Caratteri codificati da **Encode-SqlName** e decodificati da **Decode-SqlName**:  
  
|||||||||||||  
|-|-|-|-|-|-|-|-|-|-|-|-|  
|**Carattere**|\|/|:|%|\<|>|*|?|[|]|&#124;|  
|**Codifica esadecimale**|%5C|%2F|%3A|%25|%3C|%3E|%2A|%3F|%5B|%5D|%7C|  
  
##  <a name="EncodeIdent"></a> Codifica di un identificatore  
 **Per codificare un identificatore di SQL Server in un percorso di PowerShell**  
  
-   Utilizzare uno dei due metodi per codificare un identificatore di SQL Server:  
  
    -   Specificare il codice esadecimale per il carattere non supportato utilizzando la sintassi% XX, dove XX rappresenta il codice esadecimale.  
  
    -   Passare l'identificatore come stringa tra virgolette al cmdlet **Encode-Sqlname**  
  
### Esempi (codifica)  
 In questo esempio viene specificata la versione codificata del carattere ":" (% 3A):  
  
```  
Set-Location Table%3ATest  
```  
  
 In alternativa, è possibile usare **Encode-SqlName** per compilare un nome supportato da Windows PowerShell:  
  
```  
Set-Location (Encode-SqlName "Table:Test")  
```  
  
##  <a name="DecodeIdent"></a> Decodifica di un identificatore  
 **Per decodificare un identificatore di SQL Server da un percorso di PowerShell**  
  
 Usare il cmdlet **Decode-Sqlname** per sostituire le codifiche esadecimali con i caratteri rappresentati dalla codifica.  
  
### Esempi (decodifica)  
 In questo esempio viene restituito "Table:Test":  
  
```  
Decode-SqlName "Table%3ATest"  
```  
  
## Vedere anche  
 [Identificatori di SQL Server in PowerShell](../../relational-databases/scripting/sql-server-identifiers-in-powershell.md)   
 [Provider PowerShell per SQL Server](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)  
  
  