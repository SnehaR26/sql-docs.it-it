---
title: 'Procedura: Navigare tra script | Microsoft Docs'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- sql.data.tools.editor.howto.navigate
ms.assetid: 8664bde5-86ff-4e8b-b5a6-af003316f6ad
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e0627b9a4f0512c7e711212606b855c11011fff3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47702879"
---
# <a name="how-to-navigate-between-scripts"></a>Procedura: Navigazione tra script
L'Editor Transact\-SQL per lo sviluppo offline fornisce due strumenti di navigazione utili, familiari agli utenti di Visual Studio, ovvero Vai a definizione e Trova tutti i riferimenti. È possibile, ad esempio, fare clic con il pulsante destro del mouse sul nome di una tabella e utilizzare "Trova tutti i riferimenti" per elencare tutti i riferimenti alla tabella nel progetto. È possibile fare doppio clic su un risultato della ricerca per andare al file di codice specifico. In questo file, è possibile fare di nuovo clic con il pulsante destro del mouse sul nome della tabella e scegliere "Vai a definizione" per tornare alla definizione della tabella.  
  
> [!WARNING]  
> Nella procedura seguente vengono usate entità create nelle procedure precedenti nelle sezioni [Sviluppo del database connesso](../ssdt/connected-database-development.md) e [Sviluppo di database offline orientato ai progetti](../ssdt/project-oriented-offline-database-development.md).  
  
### <a name="to-navigate-between-scripts"></a>Per navigare tra script  
  
1.  Espandere la cartella **Funzioni** in **Esplora soluzioni** e fare doppio clic su **GetProductsBySupplier.sql**.  
  
2.  Fare clic con il pulsante destro del mouse su `Products` in questa riga di codice e selezionare **Vai a definizione**  
  
    ```  
    SELECT * from Products p  
    ```  
  
3.  Verrà aperto automaticamente Products.sql in cui viene visualizzato il percorso dove viene definito il tipo `Products`.  
  
4.  Tornare a GetProductsBySupplier.sql. Questa volta, scegliere **Trova tutti i riferimenti** nel menu contestuale per `Products`. Nel riquadro **Risultati ricerca simbolo** verrà visualizzato un elenco dei percorsi in cui viene fatto riferimento alla tabella `Products`. Facendo doppio clic su uno dei risultati della ricerca si passerà al percorso del riferimento.  
  
