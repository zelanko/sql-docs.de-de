---
title: "\"Microsoft.AnalysisServices.SharePoint.Integration\" konnte nicht geladen werden | Microsoft Docs"
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4da716ab3797f4f6ea54d94c53f753685972df25
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="could-not-load-microsoftanalysisservicessharepointintegration"></a>Microsoft.AnalysisServices.SharePoint.Integration konnte nicht geladen werden.
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  In SharePoint 2010-Umgebungen mit [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint tritt dieser Fehler auf, wenn die Lösung auf Anwendungsebene für [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] nicht ordnungsgemäß bereitgestellt wurde.  
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Gilt für|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint|  
|Produktversion|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Ursache|Die Powerpivotwebapp-Lösung wurde nicht ordnungsgemäß oder überhaupt nicht bereitgestellt.|  
|Meldungstext|Datei oder Assembly "Microsoft.AnalysisServices.SharePoint.Integration" konnte nicht geladen werden|  
  
## <a name="explanation"></a>Erklärung  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint stellt seine Funktionen mithilfe von Lösungspaketen auf einem SharePoint-Server bereit. Eine der Lösungen wurde nicht ordnungsgemäß bereitgestellt. Daher tritt dieser Fehler auf, wenn Sie versuchen, den [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Katalog oder andere [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Anwendungsseiten auf einer SharePoint-Website zu öffnen.  
  
## <a name="user-action"></a>Benutzeraktion  
 Stellen Sie das Lösungspaket bereit.  
  
1.  Klicken Sie in der Zentraladministration unter Systemeinstellungen auf **Farmlösungen verwalten**.  
  
2.  Klicken Sie auf **Powerpivotwebapp**.  
  
3.  Klicken Sie auf **Lösung bereitstellen**.  
  
4.  Wählen Sie die Webanwendung aus, für die dieser Fehler aufgetreten ist. Bei mehr als einer Webanwendung stellen Sie die Lösung für alle Anwendungen erneut bereit.  
  
5.  Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen von Power Pivot-Lösungen in SharePoint](../../analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
