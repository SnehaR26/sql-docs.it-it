---
title: 'Passaggio 2: Verifica del pacchetto di distribuzione | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 6c13f5c9-c75e-4e52-94dc-2d2db2c578fe
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5a9f5ef250617b445ce30624537f715be73b3d2f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48102121"
---
# <a name="step-2-verifying-the-deployment-bundle"></a>Passaggio 2: Verifica del pacchetto di distribuzione
  Nella lezione 1 è stato creato il progetto Deployment Tutorial a cui sono stati aggiungi pacchetti e file ausiliari. Nell'attività precedente è stata compilata un'utilità di distribuzione per il progetto.  
  
 In questa attività si procederà alla verifica dei contenuti del pacchetto di distribuzione. Quest'ultimo rappresenta la cartella che verrà copiata nel computer di destinazione e utilizzata per installare i pacchetti. Se è stato utilizzato il valore predefinito, ovvero bin\Deployment, come percorso dell'utilità di distribuzione, il pacchetto di distribuzione si trova nella cartella Bin\Deployment all'interno della cartella Deployment Tutorial del progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
### <a name="to-verify-the-content-of-deployment-bundle"></a>Per verificare il contenuto del pacchetto di distribuzione  
  
1.  Individuare la cartella bin\Deployment nel computer in uso.  
  
2.  Verificare che siano presenti i file seguenti:  
  
    -   DataTransfer.dtsx  
  
    -   datatransferconfig.dtsconfig  
  
    -   Deployment Tutorial.SSISDeploymentManifest  
  
    -   LoadXMLData.dtsx  
  
    -   loadxmldataconfig.dtsconfig  
  
    -   NewCustomers.txt  
  
    -   orders.xml  
  
    -   orders.xsd  
  
    -   Readme.txt  
  
3.  Fare clic con il pulsante destro del mouse su Deployment Tutorial.SSISDeploymentManifest, scegliere **Apri con**, quindi fare clic su **Internet Explorer**. È inoltre possibile aprire il file in un editor di testo, ad esempio Blocco note. Il codice XML dovrebbe risultare analogo al seguente:  
  
     `<?xml version="1.0"?><DTSDeploymentManifest GeneratedBy="Domain\UserName" GeneratedFromProjectName="Deployment Tutorial" GeneratedDate="2006-02-24T13:29:02.6537669-08:00" AllowConfigurationChanges="true"><Package>DataTransfer.dtsx</Package><Package>LoadXMLData.dtsx</Package><ConfigurationFile>datatransferconfig.dtsconfig</ConfigurationFile><ConfigurationFile>loadxmldataconfig.dtsconfig</ConfigurationFile><MiscellaneousFile>Readme.txt</MiscellaneousFile><MiscellaneousFile>orders.xml</MiscellaneousFile><MiscellaneousFile>NewCustomers.txt</MiscellaneousFile><MiscellaneousFile>orders.xsd</MiscellaneousFile></DTSDeploymentManifest>`  
  
4.  Verificare che il valore dei `AllowConfigurationChanges` attributo è **true** e il codice XML includa un `Package` per ognuno dei due pacchetti, una `MiscellaneousFile` per ognuno dei quattro file non pacchetto e un `ConfigurationFile` (elemento) per ognuno dei due file di configurazione XML.  
  
5.  Chiudere Internet Explorer o l'editor di testo.  
  
## <a name="next-lesson"></a>Lezione successiva  
 [Lezione 3: Installazione dei pacchetti](../integration-services/lesson-3-install-ssis-package.md)  
  
![Icona di Integration Services (piccola)](media/dts-16.gif "icona di Integration Services (piccola)")**rimangono fino a Date con Integration Services** <br /> Per i download, gli articoli, gli esempi e i video Microsoft più recenti, oltre alle soluzioni selezionate dalla community, visitare la pagina [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sul sito MSDN:<br /><br /> [Visita la pagina di Integration Services su MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Per ricevere una notifica automatica su questi aggiornamenti, sottoscrivere i feed RSS disponibili nella pagina.  
  
  
