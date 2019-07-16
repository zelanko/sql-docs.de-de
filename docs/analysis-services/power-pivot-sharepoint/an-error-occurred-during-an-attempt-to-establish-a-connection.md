---
title: Fehler beim Versuch, eine Verbindung herstellen | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 28d5bd077da96e3dd6f8a48004c3a5df1b681f61
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68208349"
---
# <a name="an-error-occurred-during-an-attempt-to-establish-a-connection"></a>Beim Versuch zum Herstellen einer Verbindung ist ein Fehler aufgetreten.
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Dieser Fehler tritt auf, wenn Sie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Daten auf einem Server abfragen, auf dem [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint nicht installiert ist. Es wird auch angezeigt, wenn es sich bei der SQL Server Analysis Services ( [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)])-Dienst beendet wird, oder wenn Sie versuchen, zeigen Sie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Daten aus einer früheren Version.  
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Gilt für|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint|  
|Produktversion|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Ursache|Fehler beim Herstellen der Datenverbindung.|  
|Meldungstext|Während des Herstellens einer Verbindung mit der externen Datenquelle ist ein Fehler aufgetreten. Die folgenden Verbindungen wurden nicht aktualisiert: [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Daten|  
  
## <a name="explanation"></a>Erklärung  
 Excel Services gibt diesen Fehler zurück, wenn Sie Abfragen [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Daten in einer Excel-Arbeitsmappe, die auf SharePoint und die SharePoint-Umgebung veröffentlicht wird, verfügt nicht über eine [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint-Server oder SQL Server Analysis Services ( [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]) Dienst wurde beendet.  
  
 Der Fehler tritt auf, wenn Sie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Daten nach Slices aufteilen oder filtern, während keine Abfrage-Engine verfügbar ist.  
  
## <a name="user-action"></a>Benutzeraktion  
 Installieren Sie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint, oder verschieben Sie die [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Arbeitsmappe in eine SharePoint-Umgebung, in der [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint installiert ist. Weitere Informationen finden Sie unter [PowerPivot für SharePoint 2010-Installation](http://msdn.microsoft.com/8d47dde7-c941-4280-a934-e2fe3f9a938f).  
  
 Wenn die Software installiert ist, stellen Sie sicher, dass der SQL Server Analysis Services ( [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]) wird ausgeführt. Prüfen Sie **Dienste auf dem Server verwalten** in der Zentraladministration. Prüfen Sie auch die Dienste-Konsolenanwendung in der Verwaltung.  
  
 Für [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Arbeitsmappen, die in einer SQL Server 2008 R2-Version von [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für Excel erstellt wurden, muss die SQL Server 2008 R2-Version vom OLE DB-Anbieter für Analysis Services installiert werden. Dieser Fehler tritt auf, wenn Sie den Anbieter installiert, die Datei Microsoft.AnalysisServices.ChannelTransport.dll jedoch nicht registriert haben. Weitere Informationen zur Dateiregistrierung finden Sie unter [Installieren des OLE DB-Anbieters für Analysis Services auf SharePoint-Servern](http://msdn.microsoft.com/2c62daf9-1f2d-4508-a497-af62360ee859).  
  
## <a name="see-also"></a>Siehe auch  
 [Die Datenverbindung verwendet die Windows-Authentifizierung, und Benutzeranmeldeinformationen konnten nicht delegiert werden. Die folgenden Verbindungen wurden nicht aktualisiert: PowerPivot-Daten](../../analysis-services/power-pivot-sharepoint/the-data-connection-user-could-not-be-delegated.md)  
  
  
