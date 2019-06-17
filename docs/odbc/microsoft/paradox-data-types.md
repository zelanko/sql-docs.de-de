---
title: Paradox-Datentypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], Paradox driver
- desktop database drivers [ODBC], Paradox driver
- Paradox data types [ODBC]
- Jet-based ODBC drivers [ODBC], Paradox driver
- data types [ODBC], Paradox driver
- Paradox driver [ODBC], data types
ms.assetid: 0c9e5d21-9321-49f8-a055-69459e1c9c85
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8e2f3b1e63578af7c0b42f00113fbb9e87cb8003
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63208406"
---
# <a name="paradox-data-types"></a>Paradox-Datentypen
Die ODBC-Paradox-Treiber ordnet Paradox-Datentypen in ODBC-SQL-Datentypen. Die folgende Tabelle listet alle Paradox-Datentypen und zeigt die ODBC-SQL-Datentypen, die, denen Sie zugeordnet sind.  
  
|Paradox-Datentyp|ODBC-Datentyp|  
|-----------------------|--------------------|  
|ALPHANUMERIC|SQL_VARCHAR|  
|AUTOINCREMENT[1]|SQL_INTEGER|  
|BCD[1]|SQL_DOUBLE|  
|BYTES[1]|SQL_BINARY|  
|DATE|SQL_DATE|  
|IMAGE ' [2]|SQL_LONGVARBINARY|  
|LOGICAL[1]|SQL_BIT|  
|LONG[1]|SQL_INTEGER|  
|MEMO[2]|SQL_LONGVARCHAR|  
|MONEY [1]|SQL_DOUBLE|  
|NUMBER|SQL_DOUBLE|  
|SHORT|SQL_SMALLINT|  
|ZEIT [1]|SQL_TIMESTAMP|  
|TIMESTAMP [1]|SQL_TIMESTAMP|  
  
 [1] gültig nur für Paradox-Version 5. *x*.  
  
 [2] gültig nur für die Paradox-Versionen 4. *x* und 5. *X*.  
  
> [!NOTE]  
>  **SQLGetTypeInfo** gibt der ODBC-SQL-Datentypen. Alle Konvertierungen, die in Anhang D des der *ODBC Programmer's Reference* werden unterstützt, für die ODBC-SQL-Datentypen, die weiter oben in diesem Thema aufgeführt.  
  
 Die folgende Tabelle zeigt die Einschränkungen für Paradox-Datentypen.  
  
|Datentyp|Description|  
|---------------|-----------------|  
|ALPHANUMERIC|Erstellen eine ALPHANUMERISCHE Spalte 0 (null) oder nicht angegebene Länge gibt tatsächlich eine 255-Byte-Spalte zurück.|  
|BYTES|Wenn Sie NULL in einer binären Spalte mit dem Treiber Paradox5 einfügen, wird es auf 0 geändert.|  
|LONG|Der maximale negative Wert von Paradox-Treiber für den Datentyp "Long" Paradox 5 unterstützt. *x* ist kein-2 ^ 31 (-2147483648), so sollte es sich seit langer Zuordnungen in die ODBC-sein SQL_INTEGER geben. Der Maximalwert der negative für Long-Wert unterstützt, ist tatsächlich-2 ^ 31 + 1 (-2147483647).|  
|timestamp|Wenn ein Wert wird von den Paradox-Treiber in eine TIMESTAMP-Spalte eingefügt und anschließend anschließend aus der Spalte abgerufen, abweichen der abgerufene Wert von der eingefügte Wert durch mehr als 1 Sekunde aufgrund der Rundung.|  
  
 Weitere Einschränkungen für Datentypen finden Sie im [Datumstypen](../../odbc/microsoft/data-type-limitations.md).
