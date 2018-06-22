---
title: Hinzufügen ein Ereignishandlers zu einem Paket | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- event handlers [Integration Services], creating
ms.assetid: 5e56885d-8658-480a-bed9-3f2f8003fd78
caps.latest.revision: 39
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 68d5ed9e638c03b1a34f221ff7e61d8a0df1a454
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049743"
---
# <a name="add-an-event-handler-to-a-package"></a>Hinzufügen eines Ereignishandlers zu einem Paket
  Zur Laufzeit werden von Containern und Tasks Ereignisse ausgelöst. Sie können benutzerdefinierte Ereignishandler erstellen, die auf diese Ereignisse antworten, indem Sie einen Workflow ausführen, wenn das Ereignis ausgelöst wird. Beispielsweise können Sie einen Ereignishandler erstellen, der eine E-Mail-Nachricht sendet, wenn bei einem Task ein Fehler auftritt.  
  
 Ein Ereignishandler ist mit einem Paket vergleichbar. Ein Ereignishandler kann wie ein Paket einen Bereich für Variablen bereitstellen und enthält eine Ablaufsteuerung und optionale Datenflüsse. Sie können Ereignishandler für Pakete, den Foreach-Schleifencontainer, den For-Schleifencontainer, den Sequenzcontainer und alle Tasks erstellen.  
  
 Ereignishandler erstellen Sie mithilfe der Entwurfsoberfläche der Registerkarte **Ereignishandler** im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer.  
  
 Wenn die Registerkarte **Ereignishandler** aktiv ist, enthalten die Knoten **Ablaufsteuerungselemente** und **Wartungsplantasks** der Toolbox im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer den Task und die Container zum Erstellen der Ablaufsteuerung im Ereignishandler. Die Knoten **Datenflussquellen**, **Transformationen**und **Datenflussziele** enthalten die Datenquellen, Transformationen und Ziele zum Erstellen der Datenflüsse im Ereignishandler. Weitere Informationen finden Sie unter [Control Flow](control-flow/control-flow.md) und [Data Flow](data-flow/data-flow.md).  
  
 Die Registerkarte **Ereignishandler** enthält auch den Bereich **Verbindungs-Manager** , in dem Sie die Verbindungs-Manager erstellen und ändern können, mit deren Hilfe Ereignishandler eine Verbindung mit Servern und Datenquellen herstellen. Weitere Informationen finden Sie unter [Erstellen von Verbindungs-Managern](../../2014/integration-services/create-connection-managers.md).  
  
### <a name="to-create-an-event-handler"></a>So erstellen Sie einen Ereignishandler  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Ereignishandler** .  
  
     ![Screenshot der Designoberfläche mit Ereignishandlern](media/eventhandlers.gif "Screenshot of design surface with event handler")  
  
     Das Erstellen der Ablaufsteuerung und der Datenflüsse in einem Ereignishandler ist mit dem Erstellen der Ablaufsteuerung und der Datenflüsse in einem Paket vergleichbar. Weitere Informationen finden Sie unter [Control Flow](control-flow/control-flow.md) und [Data Flow](data-flow/data-flow.md).  
  
4.  Wählen Sie in der Liste **Ausführbare Datei** die ausführbare Datei aus, für die Sie einen Ereignishandler erstellen möchten.  
  
5.  Wählen Sie in der Liste **Ereignishandler** den Ereignishandler aus, den Sie erstellen möchten.  
  
6.  Klicken Sie auf den Link auf der Entwurfsoberfläche der Registerkarte **Ereignishandler** .  
  
7.  Fügen Sie dem Ereignishandler Ablaufsteuerungselemente hinzu, und verbinden Sie die Elemente mithilfe einer Rangfolgeneinschränkung, indem Sie die Einschränkung von einem Ablaufsteuerungselement auf ein anderes ziehen. Weitere Informationen finden Sie unter [Control Flow](control-flow/control-flow.md).  
  
8.  Fügen Sie wahlweise einen Datenfluss-Task hinzu, und erstellen Sie auf der Entwurfsoberfläche der Registerkarte **Datenfluss** einen Datenfluss für den Ereignis-Handler. Weitere Informationen finden Sie unter [Data Flow](data-flow/data-flow.md).  
  
9. Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das neue Paket zu speichern.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Integration Services](../../2014/integration-services/sql-server-integration-services.md)   
 [Integration Services-Protokollierung &#40;SSIS&#41;](performance/integration-services-ssis-logging.md)  
  
  