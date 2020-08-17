---
description: Paradox-Datentypen
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 44494e9945a84f978449b6bab02bd967e40d9a20
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340456"
---
# <a name="paradox-data-types"></a>Paradox-Datentypen
Der ODBC-Paradox-Treiber ordnet den ODBC-SQL-Datentypen die Paradox-Datentypen zu. In der folgenden Tabelle werden alle Paradox-Datentypen aufgelistet und die ODBC-SQL-Datentypen angezeigt, denen Sie zugeordnet sind.  
  
|Paradox-Datentyp|ODBC-Datentyp|  
|-----------------------|--------------------|  
|Alphanumerische|SQL_VARCHAR|  
|AutoIncrement [1]|SQL_INTEGER|  
|BCD [1]|SQL_DOUBLE|  
|Bytes [1]|SQL_BINARY|  
|DATE|SQL_DATE|  
|Bild [2]|SQL_LONGVARBINARY|  
|Logisch [1]|SQL_BIT|  
|Long [1]|SQL_INTEGER|  
|Memo [2]|SQL_LONGVARCHAR|  
|Money [1]|SQL_DOUBLE|  
|NUMBER|SQL_DOUBLE|  
|SHORT|SQL_SMALLINT|  
|Uhrzeit [1]|SQL_TIMESTAMP|  
|Zeitstempel [1]|SQL_TIMESTAMP|  
  
 [1] gilt nur für die Paradox-Version 5. *x*.  
  
 [2] gültig nur für die Version 4 von Paradox. *x* und 5. *x*.  
  
> [!NOTE]  
>  **SQLGetTypeInfo** gibt ODBC-SQL-Datentypen zurück. Alle Konvertierungen in Anhang D der *ODBC-Programmier Referenz* werden für die zuvor in diesem Thema aufgeführten ODBC-SQL-Datentypen unterstützt.  
  
 In der folgenden Tabelle sind die Einschränkungen für die Datentypen Paradox aufgeführt.  
  
|Datentyp|BESCHREIBUNG|  
|---------------|-----------------|  
|Alphanumerische|Beim Erstellen einer alphanumerischen Spalte mit 0 (null) oder einer nicht angegebenen Länge wird tatsächlich eine 255-Byte-Spalte zurückgegeben.|  
|BYTES|Wenn Sie NULL in eine binäre Spalte mit dem Paradox5-Treiber einfügen, wird es in 0 geändert.|  
|LONG|Der maximale negative Wert, der vom Paradox-Treiber für den Long-Datentyp in Paradox 5 unterstützt wird. *x* ist nicht-2 ^ 31 (-2147483648), da es seit Long dem ODBC-Datentyp SQL_INTEGER zugeordnet werden muss. Der maximal unterstützte negative Wert ist-2 ^ 31 + 1 (-2147483647).|  
|timestamp|Wenn ein Wert vom Paradox-Treiber in eine timestamp-Spalte eingefügt und anschließend aus der Spalte abgerufen wird, unterscheidet sich der abgerufene Wert möglicherweise von dem eingefügten Wert von bis zu 1 Sekunde aufgrund der Rundung.|  
  
 Weitere Einschränkungen für Datentypen finden Sie unter [Datentyp Einschränkungen](../../odbc/microsoft/data-type-limitations.md).
