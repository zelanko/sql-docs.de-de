---
title: Paradoxe Datentypen | Microsoft Docs
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
ms.openlocfilehash: a85cf643a6d22b9b2fce15984539d74dc43c62ab
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81290930"
---
# <a name="paradox-data-types"></a>Paradox-Datentypen
Der ODBC Paradox-Treiber ordnet Paradox-Datentypen ODBC SQL-Datentypen zu. In der folgenden Tabelle sind alle Paradox-Datentypen aufgeführt und die ODBC SQL-Datentypen aufgeführt, denen sie zugeordnet sind.  
  
|Paradoxdatentyp|ODBC-Datentyp|  
|-----------------------|--------------------|  
|Alphanumerische|SQL_VARCHAR|  
|AUTOINCREMENT[1]|SQL_INTEGER|  
|BCD[1]|SQL_DOUBLE|  
|BYTES[1]|SQL_BINARY|  
|DATE|SQL_DATE|  
|BILD[2]|SQL_LONGVARBINARY|  
|LOGISCH[1]|SQL_BIT|  
|LONG[1]|SQL_INTEGER|  
|MEMO[2]|SQL_LONGVARCHAR|  
|GELD[1]|SQL_DOUBLE|  
|NUMBER|SQL_DOUBLE|  
|SHORT|SQL_SMALLINT|  
|ZEIT[1]|SQL_TIMESTAMP|  
|ZEITSTEMPEL[1]|SQL_TIMESTAMP|  
  
 [1] Gültig nur für Paradox-Versionen 5. *x*.  
  
 [2] Gültig nur für Paradox-Versionen 4. *x* und 5. *x*.  
  
> [!NOTE]  
>  **SQLGetTypeInfo** gibt ODBC SQL-Datentypen zurück. Alle Konvertierungen in Anhang D der *ODBC-Programmierreferenz* werden für die ODBC SQL-Datentypen unterstützt, die weiter oben in diesem Thema aufgeführt sind.  
  
 Die folgende Tabelle zeigt Einschränkungen für Paradox-Datentypen.  
  
|Datentyp|BESCHREIBUNG|  
|---------------|-----------------|  
|Alphanumerische|Beim Erstellen einer ALPHANUMERIC-Spalte mit Null oder nicht angegebener Länge wird tatsächlich eine 255-Byte-Spalte zurückgegeben.|  
|BYTES|Wenn Sie NULL in eine Binärspalte mit dem Paradox5-Treiber einfügen, wird dieser in 0 geändert.|  
|LONG|Der maximale negative Wert, der vom Paradox-Treiber für den Long-Datentyp in Paradox 5 unterstützt wird. *x* ist nicht -2x31 (-2147483648), wie es sein sollte, da Long dem ODBC-Datentyp SQL_INTEGER. Der maximal für Long unterstützte negative Wert ist tatsächlich -2x31 + 1 (-2147483647).|  
|timestamp|Wenn ein Wert vom Paradox-Treiber in eine TIMESTAMP-Spalte eingefügt und anschließend aus der Spalte abgerufen wird, kann der abgerufene Wert aufgrund von Rundungen um bis zu 1 Sekunde vom eingefügten Wert abweichen.|  
  
 Weitere Einschränkungen für Datentypen finden Sie unter [Datentypeinschränkungen](../../odbc/microsoft/data-type-limitations.md).
