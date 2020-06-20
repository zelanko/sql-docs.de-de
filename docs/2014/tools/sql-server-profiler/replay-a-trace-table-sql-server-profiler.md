---
title: Wiedergeben einer Ablauf Verfolgungs Tabelle (SQL Server Profiler) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 6a0ad817-3d8d-4495-889d-c66a7ef9e8bb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4118846915ea5014f25253b625c8bf2913e11295
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85011438"
---
# <a name="replay-a-trace-table-sql-server-profiler"></a>Wiedergeben einer Ablaufverfolgungstabelle (SQL Server Profiler)
  Die Wiedergabe bezeichnet die Möglichkeit, eine gespeicherte Ablaufverfolgung zu öffnen und erneut wiederzugeben. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] verfügt über eine Multithread-Wiedergabe-Engine, die Benutzerverbindungen und die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung simulieren kann. Die Wiedergabe ist nützlich für die Behandlung von Anwendungs- oder Prozessproblemen. Wenn Sie das Problem identifiziert und Korrekturen implementiert haben, sollten Sie die Ablaufverfolgung, in der das mögliche Problem aufgetreten ist, für die korrigierte Anwendung bzw. den korrigierten Prozess erneut ausführen. Geben Sie anschließend die ursprüngliche Ablaufverfolgung wieder, und vergleichen Sie die Ergebnisse.  
  
 Neben anderen Ereignisklassen, die Sie überwachen möchten, müssen bestimmte Ereignisklassen erfasst werden, um die Wiedergabe zu ermöglichen. Diese Ereignisse werden standardmäßig erfasst, wenn Sie die **TSQL_Replay** -Ablaufverfolgungsvorlage verwenden. Weitere Informationen finden Sie unter [Replay Requirements](replay-requirements.md).  
  
### <a name="to-replay-a-trace-table"></a>So geben Sie eine Ablaufverfolgungstabelle wieder  
  
1.  Öffnen Sie eine Ablaufverfolgungstabelle, die die für die Wiedergabe erforderlichen Ereignisklassen enthält.  
  
2.  Klicken Sie im Menü **Wiedergeben** auf **Start**, und stellen Sie eine Verbindung mit der Serverinstanz her, in der Sie die Ablaufverfolgung wiedergeben möchten.  
  
3.  Geben Sie im Dialogfeld **Wiedergabekonfiguration** auf der Registerkarte **Grundlegende Wiedergabeoptionen** einen Wert für **Wiedergabeserver**an. Klicken Sie auf **Ändern** , um den im Feld **Wiedergabeserver** angezeigten Server zu ändern.  
  
4.  Wählen Sie optional eines der folgenden Ziele zum Speichern der Wiedergabe aus:  
  
    -   **In Datei speichern** gibt eine Datei an, in der die Wiedergabe gespeichert wird.  
  
    -   **In Tabelle speichern**gibt eine Tabelle an, in der die Wiedergabe gespeichert wird.  
  
5.  Wählen Sie entweder **Ereignisse in der Reihenfolge wiedergeben, in der ihr Ablauf verfolgt wurde**oder **Ereignisse mithilfe mehrerer Threads wiedergeben**. In der folgenden Tabelle wird der Unterschied zwischen diesen Einstellungen beschrieben.  
  
    |Option|BESCHREIBUNG|  
    |------------|-----------------|  
    |**Ereignisse in der Reihenfolge wiedergeben, in der ihr Ablauf verfolgt wurde**|Gibt Ereignisse in der Reihenfolge wieder, in der sie aufgezeichnet wurden. Diese Option aktiviert das Debuggen.|  
    |**Ereignisse mithilfe mehrerer Threads wiedergeben**|Diese Option verwendet mehrere Threads, um die einzelnen Ereignisse unabhängig von der Reihenfolge wiederzugeben. Diese Option optimiert die Leistung.|  
  
6.  Wählen Sie **Wiedergabeergebnisse anzeigen** aus, um die Wiedergabe während des Auftretens anzuzeigen.  
  
7.  Optional können Sie auf **Erweiterte Wiedergabeoptionen**klicken, um die folgenden Optionen anzugeben:  
  
    -   Wählen Sie **System-SPIDs wiedergeben**aus, um alle Serverprozess-IDs (SPIDs) wiederzugeben.  
  
    -   Wählen Sie **Nur eine SPID wiedergeben**aus, um die Wiedergabe auf Prozesse zu beschränken, die zu einer bestimmten SPID gehören. Geben Sie im Dialogfeld **SPID für Wiedergabe**die SPID ein.  
  
    -   Wählen Sie **Wiedergabe nach Datum und Zeit beschränken**aus, um Ereignisse wiederzugeben, die während eines bestimmten Zeitraums aufgetreten sind. Wählen Sie ein Datum und eine Uhrzeit für **Startzeit**und **Beendigungszeit**aus, um den in der Wiedergabe enthaltenen Zeitraum anzugeben.  
  
    -   Konfigurieren Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**Systemüberwachungsoptionen, um zu steuern, wie**Prozesse während der Wiedergabe verwaltet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erforderliche Berechtigungen zum Ausführen von SQL Server Profiler](sql-server-profiler.md)   
 [Wiedergeben von Ablaufverfolgungen](replay-traces.md)   
 [Öffnen einer Ablaufverfolgungstabelle &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)   
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
