---
title: Ablauf Verfolgung und Wiedergabe von Ereignissen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- replaying events
- traces [SMO]
- events [SMO], replaying
- events [SMO], tracing
ms.assetid: f41b3f85-2f6c-4c3e-9776-8c73d2cc7a53
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d83b716d9919bf322097b8ded8409950982d961c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "70148362"
---
# <a name="tracing-and-replaying-events"></a>Verfolgen und Wiedergeben von Ereignissen
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  In SMO bieten die **Trace** - **und Replay** -Objekte <xref:Microsoft.SqlServer.Management.Trace> im-Namespace programmgesteuerten Zugriff [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] auf die-Funktionalität, die zum Überwachen einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Instanz [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]von oder verwendet wird. Daten über die einzelnen Ereignisse können aufgezeichnet und in einer Datei oder Tabelle zur späteren Analyse gespeichert werden. Beispielsweise können Sie eine Produktionsumgebung überwachen und feststellen, welche Prozeduren langsam ablaufen und dadurch die Leistung beeinträchtigen.  
  
 Die **Ablaufverfolgungs** -und **Wiedergabe** Objekte stellen eine Reihe von-Objekten bereit, die zum Erstellen von Ablauf [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Verfolgungen für eine Instanz von verwendet werden können. Diese Objekte können in Ihren eigenen Anwendungen verwendet werden, um manuell Ablaufverfolgungen für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] oder [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] zu erstellen. Außerdem können SMO-Ablauf **Verfolgungs** Objekte zum Lesen von SQL-Ablauf Verfolgungs Dateien und-Tabellen verwendet werden [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]die durch die Überwachung, oder die DTS-Protokollierung erstellt wurden.  
  
 Mit SMO-Ablauf **Verfolgungs** Objekten können Sie die folgenden Funktionen ausführen:  
  
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
  
 Die Ablauf Verfolgungs Daten aus den **Trace** -und **Replay** -Objekten können von der SMO-Anwendung verwendet werden, oder Sie können mithilfe [SQL Server Profiler](../../../tools/sql-server-profiler/sql-server-profiler.md)manuell untersucht werden. Die Ablauf Verfolgungs Daten sind auch mit den gespeicherten Prozeduren der [SQL](../../../relational-databases/sql-trace/sql-trace.md) -Ablauf Verfolgung kompatibel, die ebenfalls Ablauf Verfolgungs Funktionen bieten  
  
 Die SMO-Ablaufverfolgungsobjekte befinden sich im <xref:Microsoft.SqlServer.Management.Trace>-Namespace, für den ein Verweis auf die Datei Microsoft.SQLServer.ConnectionInfo.dll erforderlich ist.  
  
 Die **Trace** -und **Replay** -Objekte erfordern ein [Server Connection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) <xref:Microsoft.SqlServer.Management.Smo.Server.%23ctor%2A> -Objekt, um eine Verbindung mit der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Instanz von herzustellen. Das [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) -Objekt befindet sich im [Microsoft. SqlServer. Management. Common](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common) -Namespace, der einen Verweis auf die Datei Microsoft. SqlServer. ConnectionInfo. dll erfordert.  
  
> [!NOTE]  
>  Die **Ablaufverfolgungs** -und **Wiedergabe** Objekte werden auf einer 64-Bit-Plattform nicht unterstützt.  
  
  
