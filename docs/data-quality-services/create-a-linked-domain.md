---
title: "Creazione di un dominio collegato | Microsoft Docs"
ms.custom: ""
ms.date: "11/08/2011"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dqs.kb.linkeddomain.f1"
ms.assetid: fd99d422-c53d-4d7c-9cdd-303c703683b6
caps.latest.revision: 20
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 20
---
# Creazione di un dominio collegato
  In questo argomento viene descritto come creare un dominio collegato in una Knowledge Base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Un dominio collegato viene creato da un altro dominio esistente in precedenza ed eredita tutti i valori, le regole e le proprietà dal dominio al quale è collegato, ad eccezione del nome e della descrizione. È possibile gestire un set di domini collegati come un unico dominio. Connettendo un dominio all'altro, si crea un dominio che eredita il proprio contenuto da un altro dominio.  
  
## Scenari  
 I domini collegati sono particolarmente utili negli scenari descritti di seguito.  
  
### Mapping di più campi a domini che condividono valori, regole e proprietà  
 Non è possibile eseguire il mapping di due campi allo stesso dominio, ma è possibile eseguire il mapping di un campo a un dominio, quindi eseguire il mapping di un secondo campo a un dominio collegato al primo dominio. In questo modo si esegue il mapping dei campi a due domini diversi che dispongono dello stesso contenuto e proprietà (ad eccezione del nome e della descrizione). Per altre informazioni, vedere [Esecuzione del mapping di due campi a domini collegati](#Map).  
  
### Controllo del flusso di dati ai domini compositi  
 I domini collegati consentono di controllare il flusso di dati tra campi e domini compositi. È possibile fare distinzione tra quando dati da un campo passano in un dominio composito e quando dati da un altro campo molto simile non vengono trasferiti nel dominio composito. A tale scopo, si specifica quale di due domini collegati fa parte di un dominio composito e quale invece no. Dal punto di vista del dominio, i domini collegati sono identici, in quanto contengono le stesse informazioni. Dal punto di vista di un dominio composito, tuttavia, i domini collegati sono diversi, in quanto uno partecipa al dominio composito, mentre l'altro no.  
  
 Un esempio può essere un record che contiene i campi seguenti: Nome cliente, Cognome cliente e Nome di battesimo del padre. Si supponga di eseguire il mapping del nome del cliente e del nome di battesimo del padre a un dominio Nome e di rendere il dominio Nome e il dominio Cognome parte di un dominio composito denominato Nome completo. Il problema è che il nome di battesimo del padre verrà aggiunto al dominio composito senza un cognome. Se tuttavia si collega ognuno dei due campi del nome a un dominio, quindi si collegano i due domini, è possibile aggiungere il dominio Nome cliente al dominio composito Nome completo senza aggiungere il campo Nome di battesimo del padre a tale dominio, evitando con questo l'aggiunta del nome di battesimo del padre al dominio composito.  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Prerequisites"></a> Prerequisiti  
 Per creare un dominio collegato, è necessario disporre di una Knowledge Base e di un dominio esistente al quale si desidera effettuare il collegamento.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 Per creare un dominio collegato, è necessario disporre del ruolo dqs_kb_editor o dqs_administrator nel database DQS_MAIN.  
  
##  <a name="Create"></a> Creazione di un dominio collegato  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Eseguire l'applicazione Client Data Quality](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Nella schermata iniziale del [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] aprire o creare una Knowledge Base. Selezionare **Gestione dominio** come attività, quindi fare clic su **Apri** o **Crea**. Per ulteriori informazioni, vedere [Create a Knowledge Base](../data-quality-services/create-a-knowledge-base.md) o [Open a Knowledge Base](../data-quality-services/open-a-knowledge-base.md).  
  
3.  Dal **Elenco domini** sul **Domain Management** pagina, fare clic sul dominio che si desidera collegare un nuovo dominio a e quindi fare clic su **Crea dominio collegato**.  
  
    > [!NOTE]  
    >  Non è disponibile un'icona dedicata per la creazione di un dominio collegato. È possibile effettuare l'operazione solo utilizzando comando disponibile nel menu di scelta rapida.  
  
4.  Nella finestra di dialogo **Crea dominio** immettere un nome univoco per la Knowledge Base e una descrizione di un massimo di 256 caratteri. Verificare che il nome del dominio collegato sia corretto.  
  
5.  Fare clic su **OK** per completare la creazione del dominio collegato.  
  
6.  Se necessario, è possibile modificare il nome o la descrizione del dominio collegato nella scheda Proprietà dominio.  
  
7.  Fare clic su **Fine** per completare l'attività di gestione del dominio, come descritto in [End the Domain Management Activity](../Topic/End%20the%20Domain%20Management%20Activity.md).  
  
##  <a name="Map"></a> Esecuzione del mapping di due campi a domini collegati  
  
1.  Aprire una Knowledge Base all'attività di individuazione delle informazioni ed eseguire il mapping della Knowledge Base al database e alla tabella o vista.  
  
2.  Eseguire il mapping di un campo a un dominio, quindi tentare di eseguire il mapping di un secondo campo allo stesso dominio.  
  
3.  Nella finestra popup che indica che il dominio è già in uso, fare clic su Sì per creare un dominio collegato.  
  
4.  Nella finestra di dialogo Crea dominio immettere un nome di dominio e una descrizione, quindi fare clic su OK.  
  
##  <a name="FollowUp"></a> Completamento: Dopo la creazione di un dominio collegato  
 Dopo avere creato un dominio collegato, è possibile eseguire ulteriori attività di gestione del dominio, quali l'individuazione delle informazioni per aggiungere informazioni o l'aggiunta di criteri di corrispondenza al dominio. Per ulteriori informazioni, vedere [eseguire l'individuazione delle informazioni](../data-quality-services/perform-knowledge-discovery.md), [gestione di un dominio](../data-quality-services/managing-a-domain.md), o [creare un criterio di corrispondenza](../data-quality-services/create-a-matching-policy.md).  
  
##  <a name="Behavior"></a> Comportamento di un dominio collegato  
 È possibile modificare le impostazioni per un dominio collegato come segue:  
  
-   È possibile modificare il nome e la descrizione di un dominio collegato.  
  
-   Per modificare le proprietà del dominio per le proprietà **Tipo di dati**, **Utilizza valori iniziali**o **Formato output in** , selezionare il dominio collegato e modificare le impostazioni nella scheda **Proprietà dominio** per quel dominio. Non è possibile modificare tali impostazioni nelle proprietà del dominio collegato. Per altre informazioni, vedere [Create a Domain](../data-quality-services/create-a-domain.md).  
  
-   Impostazioni di **dati di riferimento**, **le regole di dominio**, **i valori di dominio**, e **relazioni basate su termini** schede della pagina di gestione di dominio possono essere modificate per il dominio collegato o il dominio a cui era collegato a, le modifiche verranno ereditate da altro dominio.  
  
 I domini collegati presentano le caratteristiche seguenti:  
  
-   Non è possibile scollegare due domini. Per rimuovere il collegamento, eliminare uno dei domini collegati.  
  
-   Quando si seleziona un dominio collegato nell'elenco di domini della pagina Gestione dominio, la stringa che identifica il dominio collegato nel riquadro che contiene la tabella **Valore** contiene un'indicazione che il dominio è collegato.  
  
-   Se si elimina un dominio al quale è collegato un altro dominio, entrambi domini verranno eliminati. È tuttavia possibile eliminare un dominio collegato senza che venga eliminato il dominio cui era collegato.  
  
-   Non è possibile collegare un dominio collegato a un dominio che è a sua volta collegato con un altro dominio.  
  
-   Non è possibile creare un dominio collegato o un dominio composito collegato a un dominio composito.  
  
-   Quando si fa doppio clic su un dominio collegato in una qualsiasi delle schede Gestione dominio, il dominio verrà aperto alla modifica con un'indicazione nella stringa del nome che si tratta di un dominio collegato.  
  
  