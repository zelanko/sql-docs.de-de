---
title: ODBC-Unterschlüssel | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8aad5171b98c54aa0c4adbde1a5678e4fd953640
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68093961"
---
# <a name="odbc-subkey"></a>ODBC-Unterschlüssel
Die Werte unter dem ODBC-Unterschlüssel geben ODBC-Ablauf Verfolgungs Optionen an. Diese Optionen werden über die Registerkarte Ablauf Verfolgung im Dialogfeld ODBC-Datenquellen-Administrator festgelegt, das von **sqlmanagedatasources**angezeigt wird. Der ODBC-Unterschlüssel selbst ist optional. Das Format dieser Werte ist wie in der folgenden Tabelle dargestellt.  
  
|Name|Datentyp|Data|  
|----------|---------------|----------|  
|Ablaufverfolgung|REG_SZ|**0** &#124; **1**|  
|TraceFile|REG_SZ|*Tracefile-Pfad*|  
  
 Die Werte haben die Bedeutungen, die in der folgenden Tabelle beschrieben werden.  
  
|value|Bedeutung|  
|-----------|-------------|  
|Ablaufverfolgung|Wenn der Ablauf Verfolgungs Wert auf 1 festgelegt wird, wenn eine Anwendung **sqlzuordchandle** mit der Option SQL_HANDLE_ENV aufruft, wird die Ablauf Verfolgung für die aufrufende Anwendung aktiviert.<br /><br /> Wenn das Trace-Schlüsselwort auf 0 festgelegt ist, wenn eine Anwendung **sqlzuordchandle** mit der SQL_HANDLE_ENV-Option aufruft, wird die Ablauf Verfolgung für die aufrufende Anwendung deaktiviert. Dies ist der Standardwert.<br /><br /> Eine Anwendung kann die Ablauf Verfolgung mit dem SQL_ATTR_TRACE-Verbindungs Attribut aktivieren oder deaktivieren. Dadurch werden jedoch nicht die Daten für diesen Wert geändert.|  
|TraceFile|Wenn die Ablauf Verfolgung aktiviert ist, schreibt der Treiber-Manager in die Ablauf Verfolgungs Datei, die durch den Tracefile-Wert angegeben wird.<br /><br /> Wenn keine Ablauf Verfolgungs Datei angegeben ist, wird der Treiber-Manager in die Datei "SQL. log" auf dem aktuellen Laufwerk geschrieben. Dies ist der Standardwert.<br /><br /> Die Ablauf Verfolgung sollte nur für eine einzelne Anwendung verwendet werden, oder jede Anwendung sollte eine andere Ablauf Verfolgungs Datei angeben. Andernfalls versuchen zwei oder mehr Anwendungen gleichzeitig, dieselbe Ablauf Verfolgungs Datei zu öffnen. Dies führt zu einem Fehler.<br /><br /> Eine Anwendung kann eine neue Ablauf Verfolgungs Datei mit dem SQL_ATTR_TRACEFILE-Verbindungs Attribut angeben. Dadurch werden jedoch nicht die Daten für diesen Wert geändert.|  
  
 Nehmen wir beispielsweise an, dass die Ablauf Verfolgung aktiviert ist und die Ablauf Verfolgungs Datei "c:\ODBC.log" lautet. Die Werte unter dem ODBC-Unterschlüssel lauten wie folgt:  
  
```  
Trace : REG_SZ : 1  
TraceFile : REG_SZ : C:\ODBC.LOG  
  
```
