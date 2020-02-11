---
title: MSSQLSERVER_2814 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2814 (Database Engine error)
ms.assetid: 22800748-9be9-4511-9428-6b8b40e5bef9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4c8def0fad1ae7eddb9de2e7206923b872c41ed2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67046772"
---
# <a name="mssqlserver_2814"></a>MSSQLSERVER_2814
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|2814|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PR_POSSIBLE_INFINITE_RECOMPILE|  
|Meldungstext|Es wurde ein mögliche unbegrenzte Neukompilierung für SQLHANDLE %hs, PlanHandle %hs, Startoffset %d, Endoffset %d erkannt. Die letzte Ursache für die Neukompilierung war %d.|  
  
## <a name="explanation"></a>Erklärung  
 Eine oder mehrere Anweisungen haben bewirkt, dass der Abfragebatch mindestens 50 Mal neu kompiliert wurde. Die angegebene Anweisung sollte korrigiert werden, um weitere Neukompilierungen zu vermeiden.  
  
 In der folgenden Tabelle werden die Ursachen für die Neukompilierung aufgelistet.  
  
|Ursachencode|BESCHREIBUNG|  
|-----------------|-----------------|  
|1|Schema geändert|  
|2|Statistiken geändert|  
|3|Verzögerte Kompilierung|  
|4|Festgelegte Option geändert|  
|5|Temp. Tabelle geändert|  
|6|Remote-Rowset geändert|  
|7|For Browse-Berechtigungen geändert|  
|8|Abfragebenachrichtigungsumgebung geändert|  
|9|Partitionierte Sicht geändert|  
|10|Cursoroptionen geändert|  
|11|Option (Neukompilierung) angefordert|  
  
## <a name="user-action"></a>Benutzeraktion  
  
1.  Zeigen Sie die Anweisung an, die die Neukompilierung verursacht, indem Sie die folgende Abfrage ausführen. Ersetzen Sie die Platzhalter *sql_handle*, *starting_offset*, *ending_offset* und *plan_handle* durch die in der Fehlermeldung angegebenen Werte. Beachten Sie, dass die Spalten **database_name** und **object_name** für Ad-hoc- und vorbereitete [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen den Wert NULL haben.  
  
     SELECT DB_NAME(st.dbid) AS database_name  
  
     , OBJECT_NAME (st.objectid) AS object_name  
  
     , st.text  
  
     FROM sys.dm_exec_query_stats AS qs  
  
     CROSS APPLY sys.dm_exec_sql_text (*sql_handle*) AS st  
  
     WHERE qs.statement_start_offset = *starting_offset*  
  
     AND qs.statement_end_offset = *ending_offset*  
  
     AND qs.plan_handle = *plan_handle*;  
  
2.  Ändern Sie auf Grundlage der Beschreibung des Ursachencodes die Anweisung, den Batch oder die Prozedur, um Neukompilierungen zu vermeiden. Eine gespeicherte Prozedur kann z. B. eine oder mehrere SET-Anweisungen enthalten. Diese Anweisungen sollten aus der Prozedur entfernt werden. Weitere Beispiele für die Ursachen von Neukompilierungen und Lösungen finden Sie unter [Batch Compilation, Recompilation, and Plan Caching Issues in SQL Server 2005 (Probleme bei der Batchkompilierung, Neukompilierung und beim Zwischenspeichern von Ausführungsplänen in SQL Server 2005)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/administrator/cc966425(v=technet.10)).  
  
3.  Wenn das Problem wiederholt auftritt, wenden Sie sich an den Microsoft-Kundendienst.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL:StmtRecompile (Ereignisklasse)](../event-classes/sql-stmtrecompile-event-class.md)  
  
  
