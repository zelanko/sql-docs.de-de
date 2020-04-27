---
title: 'Während des Herstellens einer Verbindung mit der externen Datenquelle ist ein Fehler aufgetreten. Die folgenden Verbindungen wurden nicht aktualisiert: Power Pivot-Daten | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1b951da1-f62d-43d2-b40b-270a4a9ab92c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c09c8984e964b4bdfa93b0fcebae2e613d484892
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66071953"
---
# <a name="an-error-occurred-during-an-attempt-to-establish-a-connection-to-the-external-data-source-the-following-connections-failed-to-refresh-powerpivot-data"></a>Während des Herstellens einer Verbindung mit der externen Datenquelle ist ein Fehler aufgetreten. Die folgenden Verbindungen wurden nicht aktualisiert: PowerPivot-Daten
  Dieser Fehler tritt auf, wenn Sie PowerPivot-Daten auf einem Server abfragen, auf dem PowerPivot für SharePoint nicht installiert ist. Er tritt auch auf, wenn der SQL Server Analysis Services (PowerPivot)-Dienst beendet wird, oder wenn Sie versuchen, PowerPivot-Daten von einer früheren Version anzuzeigen.  
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Gilt für|PowerPivot für SharePoint|  
|Produktversion|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Ursache|Fehler beim Herstellen der Datenverbindung.|  
|Meldungstext|Während des Herstellens einer Verbindung mit der externen Datenquelle ist ein Fehler aufgetreten. Die folgenden Verbindungen wurden nicht aktualisiert: PowerPivot-Daten|  
  
## <a name="explanation"></a>Erläuterung  
 Dieser Fehler wird in Excel Services zurückgegeben, wenn der SQL Server Analysis Services (PowerPivot)-Dienst beendet wurde oder wenn Sie PowerPivot-Daten in einer Excel-Arbeitsmappe abfragen, die in SharePoint veröffentlicht ist, und die SharePoint-Umgebung über keinen PowerPivot für SharePoint-Server verfügt.  
  
 Der Fehler tritt auf, wenn Sie PowerPivot-Daten nach Slices aufteilen oder filtern, während keine Abfrage-Engine verfügbar ist.  
  
## <a name="user-action"></a>Benutzeraktion  
 Installieren Sie PowerPivot für SharePoint, oder verschieben Sie die PowerPivot-Arbeitsmappe in eine SharePoint-Umgebung, in der PowerPivot für SharePoint installiert ist. Weitere Informationen finden Sie unter [PowerPivot for SharePoint 2010 Installation](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md).  
  
 Wenn die Software installiert ist, überprüfen Sie, ob die SQL Server Analysis Services (PowerPivot)-Instanz ausgeführt wird. Prüfen Sie **Dienste auf dem Server verwalten** in der Zentraladministration. Prüfen Sie auch die Dienste-Konsolenanwendung in der Verwaltung.  
  
 Für PowerPivot-Arbeitsmappen, die in einer SQL Server 2008 R2-Version von PowerPivot für Excel erstellt wurden, muss die SQL Server 2008 R2-Version vom OLE DB-Anbieter für Analysis Services installiert werden. Dieser Fehler tritt auf, wenn Sie den Anbieter installiert, die Datei Microsoft.AnalysisServices.ChannelTransport.dll jedoch nicht registriert haben. Weitere Informationen zur Dateiregistrierung finden Sie unter [Installieren des OLE DB-Anbieters für Analysis Services auf SharePoint-Servern](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Die Datenverbindung verwendet die Windows-Authentifizierung, und Benutzer Anmelde Informationen konnten nicht delegiert werden. Die folgenden Verbindungen wurden nicht aktualisiert: Power Pivot-Daten](the-data-connection-user-could-not-be-delegated.md)  
  
  
