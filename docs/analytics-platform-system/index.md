---
title: Documentazione della piattaforma di strumenti analitici Microsoft | Microsoft Docs
description: La piattaforma di strumenti analitici Microsoft, una piattaforma dati progettata per il data warehousing e l'analisi di Big Data, offre integrazione completa dei dati, elaborazione di query ad alta velocità, archiviazione con scalabilità elevata e manutenzione semplice per le soluzioni di business intelligence end-to-end.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 3fc2230d22131da80ee1250c08b19fc16e4aa651
ms.sourcegitcommit: 731c5aed039607a8df34c63e780d23a8fac937e1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909742"
---
# <a name="microsoft-analytics-platform-system"></a>Piattaforma di strumenti analitici Microsoft  
La piattaforma di strumenti analitici Microsoft, una piattaforma dati progettata per il data warehousing e l'analisi di Big Data, offre integrazione completa dei dati, elaborazione di query ad alta velocità, archiviazione con scalabilità elevata e manutenzione semplice per le soluzioni di business intelligence end-to-end.  
  
![Architettura dello strumento](media/architecture-high-level.png "architettura dello strumento")  
  
La piattaforma di strumenti analitici ospita SQL Server Parallel Data Warehouse (PDW), il software che esegue la data warehouse con elaborazione parallela elevata.  
  
La tecnologia PolyBase combina i dati PDW relazionali con i dati Hadoop di più origini, tra cui Hortonworks in Windows Server, Hortonworks in Linux, Cloudera in Linux e archivio BLOB di Microsoft Azure di HDInsight. Queste funzionalità avanzate di integrazione dei dati, oltre all'integrazione completa con gli strumenti di business intelligence, consentono alla piattaforma di strumenti analitici di restituire l'analisi integrata che consente ai decision maker aziendali di prendere decisioni ottimali e più informate.  
  
La piattaforma di strumenti analitici viene spedita al data center come appliance con hardware e software preinstallati e preconfigurati per l'esecuzione di più carichi di lavoro. Quando si acquista la piattaforma di strumenti analitici, si acquistano i nodi di calcolo per PDW a seconda dei requisiti aziendali.  
  
La piattaforma di strumenti analitici non è solo veloce e scalabile, ma è anche progettata con ridondanza elevata e disponibilità elevata, che ne fanno una piattaforma affidabile per la maggior parte dei dati critici aziendali. La piattaforma di strumenti analitici, essendo progettata per la massima semplicità, può essere usata e gestita facilmente. La tecnologia PolyBase di PDW per l'analisi dei dati Hadoop e l'integrazione con gli strumenti di business intelligence ne fanno una piattaforma completa per la compilazione di soluzioni end-to- end.  
  
  
## <a name="parallel-data-warehouse-software-designed-for-massively-parallel-processing"></a>Data warehouse parallela, software progettato per l'elaborazione parallela elevata
  
Usare PDW come componente principale di data warehousing relazionale delle soluzioni di business intelligence end-to-end. Con la progettazione dell'elaborazione parallela elevata di PDW, le query vengono in genere completate 50 volte più velocemente rispetto alle tradizionali data warehouse basate su sistemi di gestione di database SMP (Symmetric Multiprocessing).  
  
> [!NOTE]  
> 50 volte più velocemente significa che le query vengono completate in minuti invece che in ore o in secondi invece che in minuti. Con prestazioni così elevate, i business analyst possono generare risultati più esaurienti in meno tempo ed eseguire facilmente query ad hoc o il drill-down dei dettagli. L'azienda può quindi prendere decisioni migliori più rapidamente.  
  
Oltre a raggiungere prestazioni eccellenti per le query, PDW consente facilmente di:  
  
-   Espandere la data warehouse da pochi terabyte a più di 6 petabyte di dati in una singola appliance aggiungendo "unità di scala" al sistema esistente  
  
-   Considerare i dati sempre attendibili grazie alla ridondanza elevata e alla disponibilità elevata predefinite  
  
-   Risolvere le sfide moderne relative al caricamento e al consolidamento dei dati  
  
-   Integrare i dati Hadoop con i dati relazionali per un'analisi veloce usando la tecnologia PolyBase altamente parallelizzata di PDW  
  
-   Usare strumenti di business intelligence per creare soluzioni end-to-end complete  

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sui vantaggi di PDW, vedere il white paper [A Breakthrough Platform for Next-Generation Data Warehousing and Big Data Solutions (Piattaforma innovativa per soluzioni di Big Data e data warehousing di nuova generazione)](http://msdn.microsoft.com/library/dn520808.aspx) su MSDN.  
  

