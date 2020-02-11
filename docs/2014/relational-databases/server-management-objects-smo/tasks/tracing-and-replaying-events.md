---
title: Ablauf Verfolgung und Wiedergabe von Ereignissen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- replaying events
- traces [SMO]
- events [SMO], replaying
- events [SMO], tracing
ms.assetid: f41b3f85-2f6c-4c3e-9776-8c73d2cc7a53
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d478fa9203988d043212e4187792d816a69c0402
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62724790"
---
# <a name="tracing-and-replaying-events"></a>Verfolgen und Wiedergeben von Ereignissen
  In SMO bieten die Objekte `Trace` und `Replay` im <xref:Microsoft.SqlServer.Management.Trace>-Namespace programmgesteuerten Zugriff auf die [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)]-Funktionalität, mit der eine Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] oder [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] überwacht wird. Daten über die einzelnen Ereignisse können aufgezeichnet und in einer Datei oder Tabelle zur späteren Analyse gespeichert werden. Beispielsweise können Sie eine Produktionsumgebung überwachen und feststellen, welche Prozeduren langsam ablaufen und dadurch die Leistung beeinträchtigen.  
  
 Die Objekte `Trace` und `Replay` bieten einen Objektsatz, mit dem Ablaufverfolgungen auf einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] erstellt werden können. Diese Objekte können in Ihren eigenen Anwendungen verwendet werden, um manuell Ablaufverfolgungen für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] oder [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] zu erstellen. Darüber hinaus können SMO `Trace`-Objekte zum Lesen von SQL-Ablaufverfolgungsdateien und -tabellen verwendet werden, die durch die Überwachung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] oder DTS-Protokollierung erstellt wurden.  
  
 SMO `Trace`-Objekte ermöglichen die Durchführung der folgenden Funktionen:  
  
-   Erstellen einer Ablaufverfolgung.  
  
-   Festlegen von Filtern für die Ablaufverfolgung.  
  
-   Festlegen der zu verfolgenden Ereignisse.  
  
-   Stoppen und Starten einer Ablaufverfolgung.  
  
-   Lesen von Ablaufverfolgungsdateien und Ablaufverfolgungstabellen.  
  
-   Abrufen von Informationen zu Ereignissen in einer Ablaufverfolgung.  
  
-   Abrufen von Informationen zu Filtern in einer Ablaufverfolgung.  
  
-   Programmgesteuertes Bearbeiten von Ablaufverfolgungsdaten.  
  
-   Schreiben von Ablaufverfolgungstabellen und Ablaufverfolgungsdateien.  
  
-   Wiedergeben von Ablaufverfolgungsdateien oder Ablaufverfolgungstabellen.  
  
 Die Ablauf Verfolgungs Daten aus `Trace` dem `Replay` -Objekt und dem-Objekt können von der SMO-Anwendung verwendet werden, oder Sie können mithilfe [SQL Server Profiler](../../../tools/sql-server-profiler/sql-server-profiler.md)manuell untersucht werden. Die Ablauf Verfolgungs Daten sind auch mit den gespeicherten Prozeduren der [SQL](../../sql-trace/sql-trace.md) -Ablauf Verfolgung kompatibel, die ebenfalls Ablauf Verfolgungs Funktionen bieten  
  
 Die SMO-Ablaufverfolgungsobjekte befinden sich im <xref:Microsoft.SqlServer.Management.Trace>-Namespace, für den ein Verweis auf die Datei Microsoft.SQLServer.ConnectionInfo.dll erforderlich ist.  
  
 Für die Objekte `Trace` und `Replay` ist ein <xref:Microsoft.SqlServer.Management.Common.ServerConnection><xref:Microsoft.SqlServer.Management.Smo.Server.%23ctor%2A>-Objekt erforderlich, um eine Verbindung mit einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz herzustellen. Das <xref:Microsoft.SqlServer.Management.Common.ServerConnection>-Objekt befindet sich im <xref:Microsoft.SqlServer.Management.Common>-Namespace, für den ein Verweis auf die Datei Microsoft.SQLServer.ConnectionInfo.dll erforderlich ist.  
  
> [!NOTE]  
>  Die Objekte `Trace` und `Replay` werden nicht auf 64-Bit-Plattformen unterstützt.  
  
  
