---
title: PowerShell-Reference für Analysis Services PowerPivot für SharePoint | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: powershell
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9228eb879ed1417b31c95d53783d32acf53bcdb4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62509807"
---
# <a name="powershell-reference-for-power-pivot-for-sharepoint"></a>PowerShell-Referenz für PowerPivot für SharePoint
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  In diesem Abschnitt sind die zum Konfigurieren oder Verwalten einer [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] -Installation verwendeten PowerShell-Cmdlets aufgeführt. Weitere Informationen zum Aktivieren der Cmdlets und Anzeigen der integrierten Hilfe finden Sie unter [PowerPivot-Konfiguration mit Windows PowerShell](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell.md).  

>[!NOTE] 
>In diesem Artikel, möglicherweise veraltete Informationen und Beispiele enthalten. Verwenden Sie das Cmdlet "Get-Help", für die neueste Version.
  
## <a name="cmdlet-list"></a>Cmdlet-Liste  
 So zeigen Sie eine Liste der Cmdlets an der PowerShell-Eingabeaufforderung an:  
  
1.  Öffnen Sie die SharePoint-Verwaltungsshell unter Verwendung der Option **Als Administrator ausführen** .  
  
2.  Geben Sie den folgenden Befehl ein: `Get-help *powerpivot*`  
  
|Cmdlet|Unterstützte Versionen|  
|------------|------------------------|  
|[Get-PowerPivotServiceApplication cmdlet (Get-PowerPivotServiceApplication-Cmdlet)](../../analysis-services/powershell/get-powerpivotserviceapplication-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Get-PowerPivotSystemService-Cmdlet](../../analysis-services/powershell/get-powerpivotsystemservice-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Get-PowerPivotSystemServiceInstance-Cmdlet](../../analysis-services/powershell/get-powerpivotsystemserviceinstance-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[New-PowerPivotServiceApplication-Cmdlet](../../analysis-services/powershell/new-powerpivotserviceapplication-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[New-PowerPivotSystemServiceInstance cmdlet (New-PowerPivotSystemServiceInstance-Cmdlet)](../../analysis-services/powershell/new-powerpivotsystemserviceinstance-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Remove-PowerPivotServiceApplication-Cmdlet](../../analysis-services/powershell/remove-powerpivotserviceapplication-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Remove-PowerPivotSystemServiceInstance-Cmdlet](../../analysis-services/powershell/remove-powerpivotsystemserviceinstance-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Set-PowerPivotServiceApplication cmdlet (Set-PowerPivotServiceApplication-Cmdlet)](../../analysis-services/powershell/set-powerpivotserviceapplication-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Set-PowerPivotSystemService cmdlet (Set-PowerPivotSystemService-Cmdlet)](../../analysis-services/powershell/set-powerpivotsystemservice-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Update-PowerPivotSystemService-Cmdlet](../../analysis-services/powershell/update-powerpivotsystemservice-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
  
 Hinweis: Die folgenden Cmdlets funktioniert nur mit SharePoint 2010 die [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] wird nicht unterstützt.  
  
-   Get-PowerPivotEngineService  
  
-   Get-PowerPivotEngineServiceInstance  
  
-   New-PowerPivotEngineServiceInstance  
  
-   Remove-PowerPivotEngineServiceInstance  
  
-   Set-PowerPivotEngineService  
  
-   Set-PowerPivotEngineServiceInstance  
  
-   Update-PowerPivotEngineService  
  
  
