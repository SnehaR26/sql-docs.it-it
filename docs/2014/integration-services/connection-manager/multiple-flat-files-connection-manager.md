---
title: Gestione connessione per più file flat | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- Multiple Flat Files connection manager
- connections [Integration Services], flat files
- flat files
- flat file connections [Integration Services]
- connection managers [Integration Services], Multiple Flat Files
- multiple flat file connections
ms.assetid: 31fc3f7a-d323-44f5-a907-1fa3de66631a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e9c9bd0573a3a6fa8211324066e86446b85ec0f6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48185661"
---
# <a name="multiple-flat-files-connection-manager"></a>gestione connessione per più file flat
  Una gestione connessione per più file flat consente a un pacchetto di accedere a dati contenuti in più file flat. Ad esempio, un'origine file flat può utilizzare una gestione connessione per più file quando l'attività Flusso di dati si trova in un contenitore Ciclo, ad esempio il contenitore Ciclo For. In ogni ciclo del contenitore, l'origine file flat carica dati dal nome file successivo fornito dalla gestione connessione per più file.  
  
 Quando si aggiunge una gestione connessione per più file flat a un pacchetto, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crea una gestione connessione che in fase di esecuzione verrà risolta in una connessione per più file flat, imposta le proprietà della gestione connessione, quindi la aggiunge all'insieme `Connections` del pacchetto.  
  
 Il `ConnectionManagerType` della gestione connessione viene impostata su `MULTIFLATFILE`.  
  
 Per configurare la gestione connessione per più file flat, procedere nel modo seguente:  
  
-   Specificare i file, le impostazioni locali e la tabella codici da utilizzare. Le impostazioni locali vengono utilizzate per interpretare i dati con formato dipendente dalla lingua, come le date, mentre la tabella codici viene utilizzata per convertire i dati stringa in formato Unicode.  
  
-   Specificare il formato dei file. È possibile utilizzare un formato delimitato, a larghezza fissa o non allineato a destra.  
  
-   Specificare i delimitatori della riga di intestazione, delle righe di dati e delle colonne. I delimitatori delle colonne possono essere impostati a livello di file e sovrascritti a livello di colonna.  
  
-   Indicare se la prima riga dei file contiene i nomi delle colonne.  
  
-   Specificare un qualificatore di testo. Ogni colonna può essere configurata in modo da riconoscere un qualificatore di testo.  
  
-   Impostare proprietà quali il nome, il tipo di dati e la larghezza massima delle singole colonne.  
  
 Quando la gestione connessione per più file flat fa riferimento a più file, i percorsi dei file sono separati da una barra verticale. La proprietà `ConnectionString` della gestione connessione ha il formato seguente:  
  
 \<*percorso*>|\<*percorso*>  
  
 Per specificare più file è inoltre possibile utilizzare caratteri jolly. Ad esempio, fare riferimento a tutti i file di testo in C unità, il valore della `ConnectionString` può essere impostata su c:\\*. txt.  
  
 Se una gestione connessione per più file flat fa riferimento a più file, tutti i file devono avere lo stesso formato.  
  
 Per impostazione predefinita la gestione connessione per più file flat imposta la lunghezza delle colonne di tipo stringa su 50 caratteri. Nella finestra di dialogo **Editor gestione connessione per più file flat** è possibile valutare dati di esempio e modificare automaticamente la lunghezza di tali colonne, in modo da evitare il troncamento dei dati o il superamento della larghezza massima delle colonne. La lunghezza della colonna rimane invariata per tutto il flusso di dati, a meno che non venga modificata in un'origine file flat o in una trasformazione. Se su tali colonne viene eseguito il mapping a colonne di destinazione di larghezza inferiore, verrà visualizzato un avviso nell'interfaccia utente e in fase di esecuzione potrebbero verificarsi errori dovuti al troncamento dei dati. È possibile ridimensionare le colonne in modo che siano compatibili con le colonne di destinazione nella gestione connessione file flat, nell'origine file flat o in una trasformazione. Per modificare la lunghezza delle colonne di output, è necessario impostare il `Length` proprietà della colonna di output nel **proprietà Input e Output** scheda il **Editor avanzato** nella finestra di dialogo.  
  
 Se, dopo avere aggiunto e configurato l'origine file flat che utilizza la gestione connessione, si modifica la lunghezza delle colonne nella gestione connessione per più file flat, non sarà necessario ridimensionare manualmente le colonne di output nell'origine file flat. Nella finestra di dialogo **Origine file flat** è disponibile un'opzione che consente di sincronizzare i metadati delle colonne per l'origine file flat.  
  
## <a name="configuration-of-the-multiple-flat-files-connection-manager"></a>Configurazione della gestione connessione per più file flat  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per ulteriori informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , fare clic su uno degli argomenti seguenti:  
  
-   [Editor gestione connessione file Flat più &#40;pagina Generale&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Editor gestione connessione file Flat più &#40;(pagina colonne)&#41;](../multiple-flat-files-connection-manager-editor-columns-page.md)  
  
-   [Editor gestione connessione file Flat più &#40;pagina avanzate&#41;](../multiple-flat-files-connection-manager-editor-advanced-page.md)  
  
-   [Editor gestione connessione file Flat più &#40;pagina di anteprima&#41;](../multiple-flat-files-connection-manager-editor-preview-page.md)  
  
 Per informazioni sulla configurazione di una gestione connessione a livello di codice, vedere <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> e [aggiunta di connessioni a livello di programmazione](../building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Origine File flat](../data-flow/flat-file-source.md)   
 [Destinazione File flat](../data-flow/flat-file-destination.md)   
 [Integration Services &#40;SSIS&#41; le connessioni](integration-services-ssis-connections.md)  
  
  
