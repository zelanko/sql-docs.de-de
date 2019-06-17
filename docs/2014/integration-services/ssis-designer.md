---
title: SSIS-Designer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Integration Services, SSIS Designer
- Business Intelligence Development Studio, Integration Services in
- tools [Integration Services], SSIS Designer
- SSIS, SSIS Designer
- SSIS Designer, about SSIS Designer
- Integration Services, SSIS Designer
ms.assetid: 006d68ea-1b5c-4c1e-8079-3910288e012c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ea0776247555b9a5b63e2bbaa9ae9243abf6863c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62766428"
---
# <a name="ssis-designer"></a>SSIS-Designer
  [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer ist ein grafisches Tool, mit dem Sie [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Pakete erstellen und verwalten können. [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer ist in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] im Rahmen eines [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekts verfügbar.  
  
 Mit dem [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer können die folgenden Aufgaben ausgeführt werden:  
  
-   Erstellen der Ablaufsteuerung in einem Paket.  
  
-   Erstellen der Datenflüsse in einem Paket.  
  
-   Hinzufügen von Ereignishandlern zum Paket und zu Paketobjekten.  
  
-   Anzeigen des Paketinhalts.  
  
-   Zur Laufzeit, Anzeigen des Ausführungsstatus des Pakets.  
  
 Im folgenden Diagramm werden der [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer und das Fenster **Toolbox** angezeigt.  
  
 ![Screenshot des SSIS-Designers und der Toolbox](media/denali-designerandtoolbox.gif "Screenshot of SSIS Designer and Toolbox")  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] enthält zusätzliche Dialogfelder und Fenster, um Paketen Funktionalität hinzuzufügen, und [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] stellt Fenster und Dialogfelder zum Konfigurieren der Entwicklungsumgebung und zum Verwenden von Paketen bereit. Weitere Informationen finden Sie unter [SQL Server Integration Services-Benutzeroberfläche](integration-services-user-interface.md).  
  
 [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer ist nicht vom [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst abhängig (der Dienst, mit dem Pakete verwaltet und überwacht werden), und der Dienst muss nicht ausgeführt werden, um Pakete im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer zu erstellen oder zu ändern. Wenn Sie jedoch den Dienst beenden, während der [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer geöffnet ist, können Sie die Dialogfelder des [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designers nicht mehr öffnen und möglicherweise wird die Fehlermeldung „Der RPC-Server ist nicht verfügbar“ angezeigt. Sie müssen den Designer schließen, [!INCLUDE[ssIS](../includes/ssis-md.md)] beenden und anschließend [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], das [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]-Projekt und das Paket öffnen, um den [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Designer zurückzusetzen und die Verwendung des Pakets fortzusetzen.  
  
## <a name="undo-and-redo"></a>Rückgängig machen und Wiederholen  
 Sie können bis zu 20 Aktionen im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer rückgängig machen und wiederholen. Bei Paketen ist Rückgängig/Wiederholen auf den Registerkarten **Ablaufsteuerung**, **Datenfluss**, **Ereignishandler**und **Parameter** sowie im Fenster **Variablen** verfügbar. Bei Projekten ist Rückgängig/Wiederholen im Fenster **Projektparameter** verfügbar.  
  
 In der neuen **SSIS-Toolbox** können Sie keine Änderungen rückgängig machen oder wiederholen.  
  
 Wenn Sie Änderungen an einer Komponente vornehmen, für die der Komponenten-Editor verwendet wird, können Sie Änderungen gruppenweise statt einzeln rückgängig machen und wiederholen. Die Gruppe von Änderungen wird in der Dropdownliste zum Rückgängigmachen und Wiederholen als einzelne Aktion angezeigt.  
  
 Klicken Sie auf die Symbolleistenschaltfläche „Rückgängig“, auf das Menüelement **Bearbeiten/Rückgängig** oder drücken Sie STRG+Z, um eine Aktion rückgängig zu machen. Klicken Sie auf die Symbolleistenschaltfläche „Wiederholen“, auf das Menüelement **Bearbeiten/Wiederholen** oder drücken Sie STRG+Y, um eine Aktion zu wiederholen. Sie können mehrere Aktionen rückgängig machen und wiederholen, indem Sie auf den Pfeil neben der Symbolleistenschaltfläche klicken, um mehrere Aktionen in der Dropdownliste zu markieren, und anschließend in der Liste klicken.  
  
## <a name="parts-of-the-ssis-designer"></a>Teile des SSIS-Designers  
 [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer weist fünf ständig angezeigte Registerkarten auf, nämlich je eine Registerkarte zum Erstellen der Paketablaufsteuerung, der Datenflüsse, der Parameter und der Ereignishandler sowie eine Registerkarte zum Anzeigen der Inhalte eines Pakets. Zur Laufzeit wird eine sechste Registerkarte angezeigt, auf der der Ausführungsstatus eines ausgeführten Pakets und nach Beendigung des Pakets die Ausführungsergebnisse angezeigt werden.  
  
 Darüber hinaus enthält der [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer den Verbindungs-Manager-Bereich zum Hinzufügen und Konfigurieren der Verbindungs-Manager, die von einem Paket zum Herstellen einer Verbindung mit Daten verwendet werden.  
  
### <a name="control-flow-tab"></a>Ablaufsteuerung (Registerkarte)  
 Die Ablaufsteuerung in einem Paket erstellen Sie in der Entwurfsoberfläche der Registerkarte **Ablaufsteuerung** . Ziehen Sie Elemente aus dem Fenster **Toolbox** auf die Entwurfsoberfläche, und verbinden Sie sie zu einer Ablaufsteuerung. Klicken Sie dazu auf das Elementsymbol, und ziehen Sie den Pfeil von einem Element zum anderen.  
  
 Weitere Informationen finden Sie unter [Control Flow](control-flow/control-flow.md).  
  
### <a name="data-flow-tab"></a>Datenfluss (Registerkarte)  
 Falls ein Paket einen Datenflusstask enthält, können Sie dem Paket Datenflüsse hinzufügen. Die Datenflüsse in einem Paket erstellen Sie in der Entwurfsoberfläche der Registerkarte **Datenfluss** . Ziehen Sie Elemente aus dem Fenster **Toolbox** auf die Entwurfsoberfläche, und verbinden Sie sie zu einem Datenfluss. Klicken Sie dazu auf das Elementsymbol, und ziehen Sie den Pfeil von einem Element zum anderen.  
  
 Weitere Informationen finden Sie unter [Data Flow](data-flow/data-flow.md).  
  
### <a name="parameters-tab"></a>Parameter (Registerkarte)  
 Mit Integration Services-Parametern (SSIS) können Sie Eigenschaften in Paketen zur Zeit der Paketausführung Werte zuweisen. Sie können Projektparameter auf Projektebene und Paketparameter auf Paketebene erstellen. Projektparameter werden verwendet, um jegliche externen Eingaben bereitzustellen, die das Projekt für ein oder mehrere Pakete im Projekt empfängt. Mit Paketparametern können Sie die Paketausführung ändern, ohne das Paket bearbeiten und erneut bereitstellen zu müssen. Mit dieser Registerkarte können Sie Paketparameter verwalten.  
  
 Weitere Informationen zu Parametern finden Sie unter [Integration Services-Parameter &#40;SSIS&#41;](integration-services-ssis-package-and-project-parameters.md).  
  
> [!IMPORTANT]  
>  Parameter sind nur für Projekte verfügbar, die für das Projektbereitstellungsmodell entwickelt wurden. Daher sehen Sie die Registerkarte "Parameter" nur für Pakete, die ein Teil eines Projekts sind, das für die Verwendung des Projektbereitstellungsmodells konfiguriert wurde.  
  
### <a name="event-handlers-tab"></a>Registerkarte Ereignishandler  
 Die Ereignisse in einem Paket erstellen Sie in der Entwurfsoberfläche der Registerkarte **Ereignishandler** . Wählen Sie auf der Registerkarte **Ereignishandler** das Paket oder das Paketobjekt aus, für das Sie einen Ereignishandler erstellen möchten, und wählen Sie anschließend das Ereignis aus, das dem Ereignishandler zugeordnet werden soll. Ein Ereignishandler weist eine Ablaufsteuerung und optional Datenflüsse auf.  
  
 Weitere Informationen finden Sie unter [Hinzufügen eines Ereignishandlers zu einem Paket](../../2014/integration-services/add-an-event-handler-to-a-package.md).  
  
### <a name="package-explorer-tab"></a>Registerkarte Paket-Explorer  
 Pakete können komplex sein und viele Tasks, Verbindungs-Manager, Variablen und sonstige Elemente einschließen. Im Paket-Explorer wird eine vollständige Liste der Paketelemente angezeigt.  
  
 Weitere Informationen finden Sie unter [Anzeigen von Paketobjekten](view-package-objects.md).  
  
#### <a name="progressexecution-result-tab"></a>Status/Ausführungsergebnisse (Registerkarten)  
 Während ein Paket ausgeführt wird, wird auf der Registerkarte **Status** der Ausführungsstatus des Pakets angezeigt. Wenn die Ausführung des Pakets beendet wurde, sind die Ausführungsergebnisse weiterhin auf der Registerkarte **Ausführungsergebnisse** verfügbar.  
  
> [!NOTE]  
>  Zum Aktivieren bzw. Deaktivieren der Anzeige von Meldungen auf der Registerkarte **Status** schalten Sie die Option **Debug-Statusbericht** im Menü **SSIS** um.  
  
##### <a name="connection-managers-area"></a>Verbindungs-Manager (Bereich)  
 Die Verbindungs-Manager, die ein Paket verwendet, können Sie im Bereich **Verbindungs-Manager** hinzufügen und ändern. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] enthält Verbindungs-Manager zum Herstellen von Verbindungen mit verschiedenen Datenquellen, beispielsweise mit Textdateien, OLE DB-Datenbanken und .NET-Providern.  
  
 Weitere Informationen finden Sie unter [Integration Services-Verbindungen &#40;SSIS&#41;](connection-manager/integration-services-ssis-connections.md) und [Erstellen von Verbindungs-Managern](../../2014/integration-services/create-connection-managers.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Erstellen von Paketen in SQL Server-Datentools](create-packages-in-sql-server-data-tools.md)  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Integration Services-Benutzeroberfläche](integration-services-user-interface.md)  
  
  
