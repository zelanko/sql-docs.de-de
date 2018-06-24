---
title: Konnte nicht geladen werden, Datei oder Assembly &#39;Microsoft.AnalysisServices.SharePoint.Integration&#39; | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e350b67-5e18-4b90-8fb7-a0109cbb27b7
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 59a210726cb772d3f6feadb5e9440f2d09ac4dcf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060127"
---
# <a name="could-not-load-file-or-assembly-39microsoftanalysisservicessharepointintegration39"></a>Konnte nicht geladen werden, Datei oder Assembly &#39;Microsoft.AnalysisServices.SharePoint.Integration&#39;
  In SharePoint 2010-Umgebungen mit PowerPivot für SharePoint tritt dieser Fehler auf, wenn die Lösung auf Anwendungsebene für PowerPivot nicht ordnungsgemäß bereitgestellt wurde.  
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Gilt für|PowerPivot für SharePoint|  
|Produktversion|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Ursache|Die Powerpivotwebapp-Lösung wurde nicht ordnungsgemäß oder überhaupt nicht bereitgestellt.|  
|Meldungstext|Datei oder Assembly "Microsoft.AnalysisServices.SharePoint.Integration" konnte nicht geladen werden|  
  
## <a name="explanation"></a>Erklärung  
 PowerPivot für SharePoint stellt seine Funktionen mithilfe von Lösungspaketen auf einem SharePoint-Server bereit. Eine der Lösungen wurde nicht ordnungsgemäß bereitgestellt. Daher tritt dieser Fehler auf, wenn Sie versuchen, den PowerPivot-Katalog oder andere PowerPivot-Anwendungsseiten auf einer SharePoint-Website zu öffnen.  
  
## <a name="user-action"></a>Benutzeraktion  
 Stellen Sie das Lösungspaket bereit.  
  
1.  Klicken Sie in der Zentraladministration unter Systemeinstellungen auf **Farmlösungen verwalten**.  
  
2.  Klicken Sie auf **Powerpivotwebapp**.  
  
3.  Klicken Sie auf **Lösung bereitstellen**.  
  
4.  Wählen Sie die Webanwendung aus, für die dieser Fehler aufgetreten ist. Bei mehr als einer Webanwendung stellen Sie die Lösung für alle Anwendungen erneut bereit.  
  
5.  Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen von PowerPivot-Lösungen in SharePoint](deploy-power-pivot-solutions-to-sharepoint.md)  
  
  