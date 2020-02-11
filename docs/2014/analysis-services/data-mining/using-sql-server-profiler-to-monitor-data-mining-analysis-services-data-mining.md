---
title: Verwenden von SQL Server Profiler zum Überwachen von Data Mining (Analysis Services Data Mining) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], Analysis Services
ms.assetid: 655ac93c-5c5c-4565-914b-915327f7d349
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3aa29cede2849158162aba27332d5fe7f8f5fae5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66082703"
---
# <a name="using-sql-server-profiler-to-monitor-data-mining-analysis-services---data-mining"></a>Verwenden von SQL Server Profiler zum Überwachen von Data Mining (Analysis Services – Data Mining)
  Wenn Sie über die erforderlichen Berechtigungen verfügen, können Sie SQL Server Profiler zum Überwachen von Data Mining-Aktivitäten verwenden, die als Anforderungen an eine Instanz von SQL Server Analysis Services gesendet werden. Zu Data Mining-Aktivitäten können die Verarbeitung von Modellen oder Strukturen, Vorhersage- und Inhaltsabfragen sowie die Erstellung neuer Modelle oder Strukturen gehören.  
  
 SQL Server Profiler verwendet `trace`, um von verschiedenen Clients stammende Anforderungen zu überwachen – darunter [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], SQL Server Management Studio, Web-Dienste oder die Data Mining-Add-Ins für Excel. Dabei müssen jedoch alle Aktivitäten dieselbe Instanz von SQL Server Analysis Services nutzen. Sie müssen für jede zu überwachende Instanz von SQL Server Analysis Services eine separate Ablaufverfolgung erstellen. Allgemeine Informationen zu Ablaufverfolgungen und der Verwendung von SQL Server Profiler finden Sie unter [Verwenden von SQL Server Profiler zum Überwachen von Analysis Services](../instances/use-sql-server-profiler-to-monitor-analysis-services.md).  
  
 Spezifische Hilfestellungen zu den verschiedenen Typen von zu erfassenden Ereignissen finden Sie unter [Erstellen von Profilerablaufverfolgungen für Replay &#40;Analysis Services&#41;](../instances/create-profiler-traces-for-replay-analysis-services.md).  
  
## <a name="using-traces-to-monitor-data-mining"></a>Verwenden von Ablaufverfolgungen zum Überwachen von Data Mining  
 Wenn Sie Daten in einer Ablaufverfolgung aufzeichnen, können Sie festlegen, ob die Daten in einer Datei, einer Tabelle oder einer Instanz von SQL Server gespeichert werden sollen. Unabhängig davon, welche Methode Sie zum Speichern der Daten wählen, können Sie die Ablaufverfolgung mithilfe von SQL Server Profiler anzeigen und nach Ereignissen filtern. In der folgenden Tabellen werden einige Ereignisse und Unterklassen der Standard-Ablaufverfolgung von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] aufgeführt, die beim Data Mining von Interesse sind.  
  
|EventClass|EventSubclass|BESCHREIBUNG|  
|----------------|-------------------|-----------------|  
|**Query Begin**<br /><br /> **Query End**|**0-MdxQuery**|Enthält den Text aller Aufrufe an von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] gespeicherten Prozeduren.|  
|**Query Begin**<br /><br /> **Query End**|**1-dmxquery**|Enthält den Text und die Ergebnisse von Data Mining Extension (DMX)-Anweisungen.|  
|**Progress Report Begin**<br /><br /> **Progress Report End**|**34-dataminingprogress**|Liefert Informationen über den Status des Data Mining-Algorithmus: Wenn Sie beispielsweise ein Clustering-Modell erstellen, erhalten Sie eine Statusmeldung, die besagt, welcher Kandidaten-Cluster gerade erstellt wird.|  
|**Query Begin**<br /><br /> **Query End**|EXECUTESQL|Enthält den Text der Transact-SQL-Abfrage, die gerade ausgeführt wird.|  
|**Query Begin**<br /><br /> **Query End**|**2-sqlQuery**|Enthält den Text beliebiger Abfragen für Schemarowsets in Form von Systemtabellen.|  
|**Anfang ermitteln**<br /><br /> **Ende ermitteln**|Mehrere|Enthält den Text der DMX-Funktionsaufrufe oder der in XMLA gekapselten DISCOVER-Anweisungen.|  
|**Fehler**|(none)|Enthält den Text von Fehlern, die vom Server an den Client gesendet werden.<br /><br /> Fehlermeldungen, die das Präfix **Fehler (Data Mining):** oder **Information (Data Mining):** aufweisen, werden spezifisch als Antwort auf DMX-Anforderungen erstellt. Es reicht jedoch nicht aus, nur diese Fehlermeldungen anzuzeigen. Andere Fehler, die zum Beispiel vom Parser erzeugt worden sind, können ebenfalls mit Data Mining zu tun haben, verfügen jedoch nicht über ein derartiges Präfix.|  
  
 Durch die Anzeige der Befehlsanweisungen im Ablaufverfolgungsprotokoll können Sie auch die Syntax komplexer Anweisungen überprüfen, die vom Client an den [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server gesendet werden – darunter auch Aufrufe an vom System gespeicherten Prozeduren. Diese Informationen können Ihnen bei der Fehlerbehebung helfen. Sie haben auch die Möglichkeit, gültige Anweisungen als Vorlage zum Erstellen neuer Vorhersageabfragen oder Modelle zu verwenden. Einige Beispiele für gespeicherte Prozeduraufrufe, die Sie über eine Ablaufverfolgung aufzeichnen können, finden Sie unter [Beispiele für Clusteringmodellabfragen](clustering-model-query-examples.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen einer Analysis Services Instanz](../instances/monitor-an-analysis-services-instance.md)   
 [Verwenden Sie SQL Server erweiterte Ereignisse &#40;xevents-&#41; zum Überwachen von Analysis Services](../instances/monitor-analysis-services-with-sql-server-extended-events.md)  
  
  
