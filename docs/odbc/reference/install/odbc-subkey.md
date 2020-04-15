---
title: ODBC Subkey | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- registry entries for data sources [ODBC], ODBC subkey
- subkeys [ODBC], ODBC subkey
- ODBC subkey [ODBC]
ms.assetid: f9534144-8f42-4946-b0fb-638e9dcde9c8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 96e9a5f4c3cdac5097686528d3c089d9ec5826f7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287440"
---
# <a name="odbc-subkey"></a>ODBC-Unterschlüssel
Die Werte unter dem ODBC-Unterschlüssel geben ODBC-Ablaufverfolgungsoptionen an. Diese Optionen werden über die Registerkarte Ablaufverfolgung des Dialogfelds ODBC Data Source Administrator festgelegt, das von **SQLManageDataSources**angezeigt wird. Der ODBC-Unterschlüssel selbst ist optional. Das Format dieser Werte ist wie in der folgenden Tabelle dargestellt.  
  
|Name|Datentyp|Daten|  
|----------|---------------|----------|  
|Trace|REG_SZ|**0** &#124; **1**|  
|TraceFile|REG_SZ|*tracefile-Pfad*|  
  
 Die Werte haben die in der folgenden Tabelle beschriebene Bedeutung.  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|Trace|Wenn der Trace-Wert auf 1 festgelegt ist, wenn eine Anwendung **SQLAllocHandle** mit der Option SQL_HANDLE_ENV aufruft, ist die Ablaufverfolgung für die aufrufende Anwendung aktiviert.<br /><br /> Wenn das Trace-Schlüsselwort auf 0 festgelegt ist, wenn eine Anwendung **SQLAllocHandle** mit der Option SQL_HANDLE_ENV aufruft, wird die Ablaufverfolgung für die aufrufende Anwendung deaktiviert. Dies ist der Standardwert.<br /><br /> Eine Anwendung kann die Ablaufverfolgung mit dem SQL_ATTR_TRACE-Verbindungsattribut aktivieren oder deaktivieren. Dadurch werden die Daten für diesen Wert jedoch nicht geändert.|  
|TraceFile|Wenn die Ablaufverfolgung aktiviert ist, schreibt der Treiber-Manager in die Ablaufverfolgungsdatei, die durch den TraceFile-Wert angegeben wird.<br /><br /> Wenn keine Ablaufverfolgungsdatei angegeben ist, schreibt der Treiber-Manager in die Sql.log-Datei auf dem aktuellen Laufwerk. Dies ist der Standardwert.<br /><br /> Die Ablaufverfolgung sollte nur für eine einzelne Anwendung verwendet werden, oder jede Anwendung sollte eine andere Ablaufverfolgungsdatei angeben. Andernfalls versuchen zwei oder mehr Anwendungen, dieselbe Ablaufverfolgungsdatei gleichzeitig zu öffnen, was einen Fehler verursacht.<br /><br /> Eine Anwendung kann eine neue Ablaufverfolgungsdatei mit dem SQL_ATTR_TRACEFILE Verbindungsattribut angeben. Dadurch werden die Daten für diesen Wert jedoch nicht geändert.|  
  
 Angenommen, die Ablaufverfolgung ist aktiviert, und die Ablaufverfolgungsdatei lautet C:-Odbc.log. Die Werte unter dem ODBC-Unterschlüssel wären wie folgt:  
  
```  
Trace : REG_SZ : 1  
TraceFile : REG_SZ : C:\ODBC.LOG  
  
```
