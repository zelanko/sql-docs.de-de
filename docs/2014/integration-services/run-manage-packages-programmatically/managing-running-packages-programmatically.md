---
title: Programmgesteuerte Verwaltung von ausgeführten Paketen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- packages [Integration Services], managing
- running packages [Integration Services]
ms.assetid: 0e91f4ac-6f29-40d7-8c28-9b82e4802c35
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2ffaeac67c91c520ba657b96afc97898328a8299
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85422637"
---
# <a name="managing-running-packages-programmatically"></a>Programmgesteuerte Verwaltung von ausgeführten Paketen
  Wenn Sie programmgesteuert mit [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paketen arbeiten, möchten Sie u. U. bestimmen, welche Pakete gerade ausgeführt werden. Die <xref:Microsoft.SqlServer.Dts.Runtime.Application>-Klasse des <xref:Microsoft.SqlServer.Dts.Runtime>-Namespace stellt Methoden und Klassen bereit, um diese Anforderungen zu erfüllen.  
  
 Weitere Informationen zum Überwachen von Paketen finden Sie unter [Paketverwaltung &#40;SSIS-Dienst&#41;](../service/package-management-ssis-service.md).  
  
 Alle in diesem Thema erläuterten Methoden erfordern einen Verweis auf die `Microsoft.SqlServer.ManagedDTS`-Assembly. Nachdem Sie den Verweis in einem neuen Projekt hinzugefügt haben, importieren Sie den <xref:Microsoft.SqlServer.Dts.Runtime>-Namespace mit einer `using`- oder `Imports`-Anweisung.  
  
> [!IMPORTANT]  
>  Die Methoden der <xref:Microsoft.SqlServer.Dts.Runtime.Application>-Klasse zum Arbeiten mit dem SSIS-Paketspeicher unterstützen nur „.“, localhost oder den Namen des lokalen Servers. Sie können "(local)" nicht verwenden.  
  
## <a name="determining-which-packages-are-currently-running"></a>Bestimmen, welche Pakete zurzeit ausgeführt werden  
 Um zu bestimmen, welche Pakete gerade auf dem angegebenen Server ausgeführt werden, rufen Sie die <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetRunningPackages%2A>-Methode auf. Diese Methode gibt eine <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackages>-Auflistung von <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage>-Objekten zurück.  
  
> [!NOTE]  
>  Administratoren können alle Pakete sehen, die zurzeit auf dem Computer ausgeführt werden; allen anderen Benutzern werden nur die Pakete angezeigt, die sie gestartet haben.  
  
## <a name="working-with-running-packages"></a>Arbeiten mit ausgeführten Paketen  
 Nachdem Sie bestimmt haben, welche Pakete zurzeit ausgeführt werden, können Sie Informationen zu den Pakten abrufen und anfordern, dass ein Paket gestoppt wird.  
  
### <a name="getting-information-about-a-running-package"></a>Abrufen von Informationen über ein ausgeführtes Paket  
 Beim Durchlaufen der <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackages>-Auflistung können Sie mithilfe der Eigenschaften des <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage>-Objekts ein Paket suchen oder zusätzliche Informationen zu den Paketen, die ausgeführt werden, erhalten:  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.ExecutionDuration%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.ExecutionStartTime%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.InstanceID%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.PackageDescription%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.PackageID%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.PackageName%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.UserName%2A>  
  
### <a name="stopping-a-running-package"></a>Beenden eines ausgeführten Pakets  
 Sie können die <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.Stop%2A>-Methode eines <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage>-Objekts aufrufen, um anzufordern, dass das Paket beendet wird. Möglicherweise gibt es eine Zeitverzögerung zwischen der Ausgabe der Stop-Anforderung und dem tatsächlichen Beenden des Pakets.  
  
![Integration Services Symbol (klein)](../media/dts-16.gif "Integration Services (kleines Symbol)")immer auf**dem neuesten Stand bleiben mit Integration Services**  <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Paketverwaltung &#40;SSIS-Dienst&#41;](../service/package-management-ssis-service.md)   
 [Enumerating Available Packages Programmatically](../run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)  
  
  
