---
title: Tools und Anwendungen, die in Analysis Services verwendete | Microsoft-Dokumentation
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8d3ecb5de4c70c09bc367b9008f5d62c6a23faef
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68162285"
---
# <a name="tools-and-applications-used-in-analysis-services"></a>In Analysis Services verwendete Tools und Anwendungen
[!INCLUDE[ssas-appliesto-sqlas-aas](../includes/ssas-appliesto-sqlas-aas.md)]

  Suchen die Tools und Anwendungen, die Sie zum Erstellen von Analysis Services-Modellen benötigen und Verwalten von Datenbanken bereitgestellt.  
  
## <a name="analysis-services-model-designers"></a>Analysis Services-Modell-Designer  
 Modelle werden mithilfe von Projektvorlagen in SQL Server Data Tools (SSDT), einer Visual Studio-Shell erstellt. Projektvorlagen bieten die Modell-Designer zum Erstellen der Objekte des Datenmodells, die Analysis Services-Lösung bilden. SSDT ist ein kostenloser Webdownload monatlich aktualisiert.

 **[SQL Server Datatools (SSDT) herunterladen](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt)** 
  
 Modelle verfügen über eine Einstellung des Kompatibilitätsgrades, der die Funktionsverfügbarkeit bestimmt und welches Release von Analysis Services das Modell ausführt.  Ob Sie angeben können, dass es sich bei ein bestimmten Kompatibilitätsgrad wird festgelegt, teilweise vom Modell-Designer.  
  
 Tabellarische Modelle verwenden die neueste Funktionalität nutzen, wie z. B. die BIM-Dateien im JSON-Tabellenformat und bidirektionale kreuzfilterung, müssen erstellt oder mit dem Kompatibilitätsgrad 1200 oder höher aktualisiert werden.  
  
 Wenn Sie mit einen niedrigeren Kompatibilitätsgrad benötigen, vielleicht können weil Sie ein Modell mit einer früheren Version von Analysis Services bereitstellen möchten weiterhin im Modell-Designer in SSDT. Neuere Versionen des Tools unterstützen jeden Modelltyp (tabellarisch oder mehrdimensional) mit jedem Kompatibilitätsgrad erstellen.   

## <a name="administrative-tools"></a>Verwaltungstools  
  
 SQL Server Management Studio (SSMS) ist das primäre Verwaltungstool für alle SQL Server-Funktionen, einschließlich Analysis Services. SSMS ist ein kostenloser Webdownload monatlich aktualisiert. 
  
**[Hier können Sie SQL Server Management Studio herunterladen.](../ssms/download-sql-server-management-studio-ssms.md)** 
  
 SSMS umfasst erweiterte Ereignisse (xEvents), eine einfache Alternative zu SQL Server Profiler-ablaufverfolgungen zum Überwachen der Aktivität und Diagnostizieren von Problemen auf SQL Server 2016 und Azure Analysis Services-Server bereitstellen. Weitere Informationen finden Sie unter [Überwachen von Analysis Services mit den erweiterten Ereignissen von SQL Server](../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md) .  
  
### <a name="sql-server-profiler"></a>SQL Server Profiler  
 Auch wenn er zugunsten von xEvents offiziell als veraltet eingestuft ist, bietet SQL Server Profiler ein vertrautes Konzept zum Überwachen von Verbindungen, der MDX-Abfrageausführung und anderer Servervorgänge. SQL Server Profiler wird standardmäßig installiert. Sie finden Sie mit SQL Server-Anwendungen für Apps in Windows.  
  
### <a name="powershell"></a>PowerShell  
 Mithilfe von PowerShell-Befehlen können Sie viele Verwaltungsaufgaben durchführen. Finden Sie unter [PowerShell-Referenz](../analysis-services/powershell/analysis-services-powershell-reference.md) für Weitere Informationen.  
  
### <a name="community-and-third-party-tools"></a>Community- und Drittanbietertools  
 Community-Codebeispiele finden Sie auf der [Analysis Services-Codeplex-Seite](http://sqlsrvanalysissrvcs.codeplex.com/) . [Foren](http://social.msdn.microsoft.com/Forums/sqlserver/home?forum=sqlanalysisservices) können hilfreich sein, wenn Sie Empfehlungen für Drittanbietertools suchen, die Analysis Services unterstützen.  
  
## <a name="see-also"></a>Siehe auch  
 [Kompatibilitätsgrad einer mehrdimensionalen Datenbank](../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md)   
 [Kompatibilitätsgrad für tabellarische Modelle](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  
