---
title: Bereitstellen von PowerPivot-Lösungen in SharePoint | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f202a2b7-34e0-43aa-90d5-c9a085a37c32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6b568790f9a61c01054d4a7225e4a2dbf9a39887
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66071504"
---
# <a name="deploy-powerpivot-solutions-to-sharepoint"></a>Bereitstellen von PowerPivot-Lösungen in SharePoint
  Verwenden Sie die folgenden Anweisungen, um zwei Lösungspakete, die einer SharePoint Server 2010-Umgebung PowerPivot-Funktionen hinzufügen, manuell bereitzustellen. Das Bereitstellen der Lösungen ist ein erforderlicher Schritt für die Konfiguration von PowerPivot für SharePoint auf einem SharePoint 2010-Server. Die vollständige Liste der erforderlichen Schritte finden Sie unter [PowerPivot-Serververwaltung und-Konfiguration in der Zentraladministration](power-pivot-server-administration-and-configuration-in-central-administration.md).  
  
 Alternativ können Sie die Lösungen mithilfe des PowerPivot-Konfigurationstools bereitstellen. Die Verwendung des Konfigurationstools ist für eine einzelne Serverinstallation einfacher und effizienter, aber vielleicht möchten Sie die Zentraladministration und PowerShell verwenden, wenn Sie es vorziehen, mit einem vertrauten Tool zu arbeiten oder wenn Sie mehrere Funktionen gleichzeitig konfigurieren. Weitere Informationen zur Verwendung des Konfigurationstools finden Sie unter [PowerPivot-Konfigurationstools](power-pivot-configuration-tools.md).  
  
 Vor dem Bereitstellen der Lösungen müssen Sie zuerst mithilfe der SQL Server 2012-Installationsmedien PowerPivot für SharePoint installieren. SQL Server-Setup installiert die Lösungspakete, die Sie gleich bereitstellen werden.  
  
 Dieses Thema enthält folgende Abschnitte:  
  
 [Voraussetzung: Stellen Sie sicher, dass die Webanwendung den klassischen Authentifizierungsmodus verwendet](#bkmk_classic)  
  
 [Schritt 1: Bereitstellen der Farmlösung](#bkmk_farm)  
  
 [Schritt 2: Bereitstellen der PowerPivot-Webanwendungslösung in der Zentraladministration](#deployCA)  
  
 [Schritt 3: Bereitstellen der PowerPivot-Webanwendungslösung auf anderen Webanwendungen](#deployUI)  
  
 [Erneutes Bereitstellen oder Zurückziehen der Lösung](#retract)  
  
 [Informationen zu den PowerPivot-Lösungen](#intro)  
  
##  <a name="bkmk_classic"></a> Voraussetzung: Stellen Sie sicher, dass die Webanwendung den klassischen Authentifizierungsmodus verwendet  
 PowerPivot für SharePoint wird nur für Webanwendungen unterstützt, die den klassischen Authentifizierungsmodus in Windows verwenden. Führen Sie das folgende PowerShell-Cmdlet aus, um zu überprüfen, ob die Anwendung den klassischen Modus verwendet, die **SharePoint 2010-Verwaltungsshell**und ersetzt dabei `http://<top-level site name>` mit dem Namen der SharePoint-Website:  
  
```  
Get-spwebapplication http://<top-level site name> | format-list UseClaimsAuthentication  
```  
  
 Der Rückgabewert sollte **FALSE**sein. Ist dies **"true"**, Sie können nicht auf PowerPivot-Daten über diese Webanwendung zugreifen.  
  
##  <a name="bkmk_farm"></a>Schritt 1: Bereitstellen der Farmlösung  
 In diesem Abschnitt erfahren Sie, wie Sie Lösungen mithilfe der PowerShell bereitstellen können. Sie können aber auch das PowerPivot-Konfigurationstool verwenden, um diese Aufgabe abzuschließen. Weitere Informationen finden Sie unter [konfigurieren oder Reparieren von PowerPivot für SharePoint 2010 &#40;PowerPivot-Konfigurationstool&#41;](../configure-repair-powerpivot-sharepoint-2010.md).  
  
 Diese Aufgabe muss nur einmal ausgeführt werden, nachdem Sie PowerPivot für SharePoint installiert haben.  
  
1.  Öffnen Sie auf einen Server, der eine Installation von PowerPivot für SharePoint verfügt, eine SharePoint 2010-Verwaltungsshell mithilfe der **als Administrator ausführen** Option.  
  
2.  Führen Sie das folgende Cmdlet aus, um die Farmlösung hinzuzufügen.  
  
    ```  
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\110\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotFarm.wsp"  
    ```  
  
     Das Cmdlet gibt den Namen der Lösung, deren Lösungs-ID und "Deployed=False" zurück. Im nächsten Schritt wird die Lösung bereitgestellt.  
  
3.  Führen Sie das nächste Cmdlet aus, um die Farmlösung bereitzustellen:  
  
    ```  
    Install-SPSolution -Identity PowerPivotFarm.wsp -GACDeployment -Force  
    ```  
  
##  <a name="deployCA"></a>Schritt 2: Bereitstellen der PowerPivot-Webanwendungslösung in der Zentraladministration  
 Nach dem Bereitstellen der Farmlösung müssen Sie die Webanwendungslösung in der Zentraladministration bereitstellen. Durch diesen Schritt wird das PowerPivot-Management-Dashboard der Zentraladministration hinzugefügt.  
  
1.  Öffnen Sie eine SharePoint 2010-Verwaltungsshell mithilfe der Option **Als Administrator ausführen** .  
  
2.  Führen Sie das nächste Cmdlet aus, um einen Verweis auf die Zentraladministration zu erstellen:  
  
    ```  
    $centralAdmin = $(Get-SPWebApplication -IncludeCentralAdministration | Where { $_.IsAdministrationWebApplication -eq $TRUE})  
    ```  
  
3.  Führen Sie das folgende Cmdlet aus, um die Farmlösung hinzuzufügen.  
  
    ```  
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\110\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotWebApp.wsp"  
    ```  
  
     Das Cmdlet gibt den Namen der Lösung, deren Lösungs-ID und "Deployed=False" zurück. Im nächsten Schritt wird die Lösung bereitgestellt.  
  
4.  Führen Sie das nächste Cmdlet aus, um die Webanwendungslösung in der Zentraladministration zu installieren.  
  
    ```  
    Install-SPSolution -Identity PowerPivotWebApp.wsp -GACDeployment -Force -WebApplication $centralAdmin  
    ```  
  
 Da Sie nun die Webanwendungslösung in der Zentraladministration bereitgestellt haben, können Sie mithilfe der Zentraladministration alle verbleibenden Konfigurationsschritte ausführen.  
  
##  <a name="deployUI"></a>Schritt 3: Bereitstellen der PowerPivot-Webanwendungslösung auf anderen Webanwendungen  
 In der vorherigen Aufgabe haben Sie powerpivotwebapp.wsp in der Zentraladministration bereitgestellt. In diesem Abschnitt stellen Sie die Lösung "powerpivotwebapp.wsp" in jeder vorhandenen Webanwendung bereit, die PowerPivot-Datenzugriff unterstützt. Wenn Sie später weitere Webanwendungen hinzufügen, wiederholen Sie unbedingt diesen Schritt für die zusätzlichen Webanwendungen.  
  
1.  Klicken Sie in der Zentraladministration unter Systemeinstellungen auf **Farmlösungen verwalten**.  
  
2.  Klicken Sie auf **powerpivotwebapp.wsp**.  
  
3.  Klicken Sie auf **Lösung bereitstellen**.  
  
4.  In **bereitstellen für?**, wählen Sie die SharePoint-Webanwendung, die für die Sie die PowerPivot-funktionsunterstützung hinzufügen möchten.  
  
5.  Klicken Sie auf **OK**.  
  
6.  Wiederholen Sie die Schritte für andere SharePoint-Webanwendungen, die den PowerPivot-Datenzugriff ebenfalls unterstützen.  
  
##  <a name="retract"></a> Erneutes Bereitstellen oder Zurückziehen der Lösung  
 Obwohl in der SharePoint-Zentraladministration das Zurückziehen der Lösung möglich ist, müssen Sie die Datei powerpivotwebapp.wsp nur entfernen, wenn Sie systematisch ein Installations- oder ein Patchbereitstellungsproblem behandeln.  
  
1.  Klicken Sie in der SharePoint 2010-Zentraladministration in Systemeinstellungen auf **Farmlösungen verwalten**.  
  
2.  Klicken Sie auf **Powerpivotwebapp.wsp**.  
  
3.  Klicken Sie auf **Lösung zurückziehen**.  
  
 Wenn Sie, die Sie bis zur farmlösung zurückverfolgen auftreten, können Sie es bereitstellen, mit der **Reparatur** -Option in der PowerPivot-Konfigurationstool. Es empfiehlt sich, Reparaturvorgänge über das Tool auszuführen, da Sie sich dadurch ein paar Schritte ersparen. Weitere Informationen finden Sie unter [konfigurieren oder Reparieren von PowerPivot für SharePoint 2010 &#40;PowerPivot-Konfigurationstool&#41;](../configure-repair-powerpivot-sharepoint-2010.md).  
  
 Wenn Sie immer noch alle Lösungen erneut bereitstellen möchten, gehen Sie dabei in folgender Reihenfolge vor:  
  
1.  Ziehen Sie die PowerPivot-Webanwendungslösung aus allen SharePoint-Webanwendungen zurück, die sie verwenden.  
  
2.  Ziehen Sie die PowerPivot-Farmlösung zurück.  
  
3.  Stellen Sie die PowerPivot-Farmlösung erneut bereit.  
  
4.  Stellen Sie die PowerPivot-Webanwendungslösung erneut für alle SharePoint-Webanwendungen bereit.  
  
##  <a name="intro"></a> Informationen zu den PowerPivot-Lösungen  
 PowerPivot für SharePoint verwendet zwei Lösungspakete, um Anwendungsseiten und Programmdateien für die Farm und einzelne Webanwendungen bereitzustellen.  
  
-   Die Farmlösung ist global. Sie wird einmal bereitgestellt und ist dann für jeden neuen Server mit PowerPivot für SharePoint automatisch verfügbar, den Sie der Farm später hinzufügen.  
  
-   Die Webanwendungslösung ist anwendungsspezifisch und muss für jede Webanwendung in der Farm bereitgestellt werden, einschließlich der Zentraladministrationswebanwendung.  
  
 Jede Lösung wird unterschiedlich bereitgestellt.  Die Farmlösung wird bereitgestellt, nachdem das erste PowerPivot für die SharePoint-Instanz installiert wurde. Verwenden Sie das PowerPivot-Konfigurationstool oder PowerShell-Cmdlets, um die Farmlösung bereitzustellen.  
  
 Die Webanwendungslösung wird anfänglich in der Zentraladministration bereitgestellt. Es folgen weitere Bereitstellungen für alle zusätzlichen Webanwendungen, die Anfragen für PowerPivot-Daten unterstützen. Um die webanwendungslösung in der Zentraladministration bereitzustellen, müssen Sie das PowerPivot-Konfigurationstool oder PowerShell-Cmdlet verwenden. Für alle anderen Webanwendungen können Sie die Webanwendungslösung manuell bereitstellen, und zwar mithilfe der Zentraladministration oder der PowerShell.  
  
|Lösung|Description|  
|--------------|-----------------|  
|Powerpivotfarm.wsp|Der globalen Assembly wird Microsoft.AnalysisServices.SharePoint.Integration.dll hinzugefügt.<br /><br /> Der globalen Assembly wird Microsoft.AnalysisServices.ChannelTransport.dll hinzugefügt.<br /><br /> Installiert Funktionen sowie Ressourcendateien und registriert Inhaltstypen.<br /><br /> Fügt Bibliotheksvorlagen für den PowerPivot-Katalog und Datenfeedbibliotheken hinzu.<br /><br /> Anwendungsseiten für die Dienstanwendungskonfiguration, das PowerPivot-Management-Dashboard, die Datenaktualisierung und der PowerPivot-Katalog werden hinzugefügt.|  
|powerpivotwebapp.wsp|Fügt dem Ordner für Webservererweiterungen auf dem Web-Front-End Microsoft.AnalysisServices.SharePoint.Integration.dll-Ressourcendateien hinzu.<br /><br /> Fügt dem Web-Front-End den PowerPivot-Webdienst hinzu.<br /><br /> Fügt die Miniaturbildgenerierung für den PowerPivot-Katalog hinzu.|  
  
## <a name="see-also"></a>Siehe auch  
 [Aktualisieren von PowerPivot für SharePoint](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md)   
 [PowerPivot-Serververwaltung und-Konfiguration in der Zentraladministration](power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [PowerPivot-Konfiguration mit Windows PowerShell](power-pivot-configuration-using-windows-powershell.md)  
  
  
