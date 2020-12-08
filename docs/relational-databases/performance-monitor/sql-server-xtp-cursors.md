---
title: SQL Server-XTP-Cursor | Microsoft-Dokumentation
description: Hier lernen Sie das Leistungsobjekt für „SQL Server-XTP-Cursor“ kennen, das Leistungsindikatoren für interne Cursor der In-Memory-OLTP-Engine enthält.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 84bf4654-3ef7-4d7f-a269-c8bb4ed4acad
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: 39c491efc7b0001b7f6b44bda127e7b128c31851
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96505525"
---
# <a name="sql-server-xtp-cursors"></a>SQL Server-XTP-Cursor
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Das Leistungsobjekt für SQL Server-XTP-Cursor enthält Leistungsindikatoren für interne Cursor der In-Memory-OLTP-Engine. Cursor sind die Bausteine auf unterer Ebene, die die In-Memory-OLTP-Engine zur Verarbeitung von [!INCLUDE[tsql](../../includes/tsql-md.md)]-Abfragen verwendet. Daher können Sie diese in der Regel nicht direkt steuern.  
  
 In dieser Tabelle werden die Leistungsindikatoren für **SQL Server-XTP-Cursor** beschrieben.  
  
|Leistungsindikator|BESCHREIBUNG|  
|-------------|-----------------|  
|**Cursorlöschvorgänge/s**|Die durchschnittliche Anzahl der pro Sekunde erfolgten Cursorlöschvorgänge.|  
|**Cursoreinfügevorgänge/s**|Die durchschnittliche Anzahl der pro Sekunde erfolgten Cursoreinfügevorgänge.|  
|**Gestartete Cursorscans/s**|Die durchschnittliche Anzahl der pro Sekunde gestarteten Cursorscans.|  
|**Cursor-UNIQUE-Verstöße/s**|Die durchschnittliche Anzahl der pro Sekunde erfolgten Verstöße gegen die UNIQUE-Einschränkung.|  
|**Cursorupdates/s**|Die durchschnittliche Anzahl der pro Sekunde erfolgten Cursorupdates.|  
|**Cursorschreibkonflikte/s**|Die durchschnittliche Anzahl der pro Sekunde erfolgten Write-Write-Konflikte in dieselbe Zeilenversion.|  
|**Dusty-Corner-Scanwiederholungen/s (durch den Benutzer ausgegeben)**|Die durchschnittliche Anzahl von Scanwiederholungen aufgrund von Schreibkonflikten während Dusty-Corner-Sweep-Vorgängen, die pro Sekunde durch vollständige Tabellenscans eines Benutzers ausgegeben werden. Dieser Leistungsindikator befindet sich auf einer sehr niedrigen Ebene und dient nicht der Verwendung durch Kunden.|  
|**Entfernte abgelaufene Zeilen/s**|Die durchschnittliche Anzahl abgelaufener Zeilen, die pro Sekunde von Cursorn entfernt werden.|  
|**Berührte abgelaufene Zeilen/s**|Die durchschnittliche Anzahl abgelaufener Zeilen, die pro Sekunde von Cursorn berührt werden.|  
|**Zurückgegebene Zeilen/s**|Die durchschnittliche Anzahl von Zeilen, die pro Sekunde von Cursorn zurückgegeben werden.|  
|**Berührte Zeilen/s**|Die durchschnittliche Anzahl von Zeilen, die pro Sekunde von Cursorn berührt werden.|  
|**Berührte vorläufig gelöschte Zeilen/s**|Die durchschnittliche Anzahl ablaufender Zeilen, die pro Sekunde von Cursorn berührt werden. Eine Zeile läuft ab, wenn die Transaktion, durch die sie gelöscht wurde, immer noch aktiv ist (d. h., es wurde noch kein Commit ausgeführt bzw. sie wurde nicht abgebrochen).|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Leistungsindikatoren für SQL Server XTP &#40;In-Memory-OLTP&#41;](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)  
  
  
