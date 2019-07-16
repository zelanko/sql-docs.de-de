---
title: Ablaufverfolgung und Wiedergabe von Ereignissen | Microsoft-Dokumentation
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
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f441cceed84b873b31c7d4691b08a541a0aee06f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68030161"
---
# <a name="tracing-and-replaying-events"></a>Verfolgen und Wiedergeben von Ereignissen
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  In SMO werden die **Ablaufverfolgung** und **Replay** Objekte in der <xref:Microsoft.SqlServer.Management.Trace> Namespace bieten programmgesteuerten Zugriff auf die [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] Funktionen, die verwendet wird, für die Überwachung einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]oder [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Daten über die einzelnen Ereignisse können aufgezeichnet und in einer Datei oder Tabelle zur späteren Analyse gespeichert werden. Beispielsweise können Sie eine Produktionsumgebung überwachen und feststellen, welche Prozeduren langsam ablaufen und dadurch die Leistung beeinträchtigen.  
  
 Die **Ablaufverfolgung** und **Replay** Objekte stellen einen Satz von Objekten, die verwendet werden können, zum Erstellen von ablaufverfolgungen in einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Diese Objekte können in Ihren eigenen Anwendungen verwendet werden, um manuell Ablaufverfolgungen für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] oder [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] zu erstellen. Darüber hinaus SMO **Ablaufverfolgung** Objekte können verwendet werden, zum Lesen von SQL-Ablaufverfolgungs-Dateien und Tabellen, die durch die Überwachung erstellt wurden [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], oder DTS-Protokollierung.  
  
 SMO **Ablaufverfolgung** Objekten können Sie die folgenden Funktionen ausführen:  
  
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
  
 Die Ablaufverfolgungsdaten aus der **Ablaufverfolgung** und **Replay** Objekte können von der SMO-Anwendung verwendet werden, oder es untersucht werden kann, manuell mithilfe von [SQL Server Profiler](../../../tools/sql-server-profiler/sql-server-profiler.md). Die Ablaufverfolgungsdaten sind auch kompatibel mit der [SQL-Ablaufverfolgung](../../../relational-databases/sql-trace/sql-trace.md) gespeicherte Prozeduren, die auch eine Ablaufverfolgung ermöglichen.  
  
 Die SMO-Ablaufverfolgungsobjekte befinden sich im <xref:Microsoft.SqlServer.Management.Trace>-Namespace, für den ein Verweis auf die Datei Microsoft.SQLServer.ConnectionInfo.dll erforderlich ist.  
  
 Die **Ablaufverfolgung** und **Replay** Objekte erfordern einer [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) <xref:Microsoft.SqlServer.Management.Smo.Server.%23ctor%2A> Objekt zum Herstellen einer Verbindung mit der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Die [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) Objekt befindet sich in der [Microsoft.SqlServer.Management.Common](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common) -Namespace, der ein Verweis auf die Datei Microsoft.SQLServer.ConnectionInfo.dll erforderlich ist.  
  
> [!NOTE]  
>  Die **Ablaufverfolgung** und **Replay** Objekte werden auf einer 64-Bit-Plattform nicht unterstützt.  
  
  
