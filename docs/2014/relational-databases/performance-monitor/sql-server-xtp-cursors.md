---
title: XTP-Cursor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 84bf4654-3ef7-4d7f-a269-c8bb4ed4acad
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d31540020df2a4aa4f30f144de4d7e606b471e9e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48097000"
---
# <a name="xtp-cursors"></a>XTP-Cursor
  Das XTP-Leistungsobjekt für Cursor enthält Leistungsindikatoren für interne Cursor der XTP-Engine. Cursor sind die Bausteine auf unterer Ebene der XTP-Engine verwendet zum Verarbeiten [!INCLUDE[tsql](../../includes/tsql-md.md)] Abfragen. Daher können Sie diese in der Regel nicht direkt steuern.  
  
 Diese Tabelle beschreibt die **XTP-Cursor** Leistungsindikatoren.  
  
|Leistungsindikator|Description|  
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
  
## <a name="see-also"></a>Siehe auch  
 [XTP &#40;In-Memory-OLTP&#41; -Leistungsindikatoren](../../integration-services/performance/performance-counters.md)  
  
  
