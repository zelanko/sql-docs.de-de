---
title: Microsoft Access-Datentypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], Access driver
- Jet-based ODBC drivers [ODBC], Access driver
- desktop database drivers [ODBC], Access driver
- Access driver [ODBC], data types
- access data types [ODBC]
- data types [ODBC], Access driver
ms.assetid: b537348a-bea0-4bd6-84a4-52a75292957f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b99fd70e0119aa01d384066aaa2f3b91eed152b4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63026885"
---
# <a name="microsoft-access-data-types"></a>Microsoft Access-Datentypen
Die folgende Tabelle zeigt die Microsoft Access-Datentypen, Datentypen, die zum Erstellen von Tabellen verwendet, und ODBC-SQL-Datentypen.  
  
|Microsoft Access-Datentyp|-Datentyp (CREATETABLE)|ODBC-SQL-Datentyp|  
|--------------------------------|-------------------------------|------------------------|  
|BIGBINARY[1]|LONGBINARY|SQL_LONGVARBINARY|  
|BINARY|BINARY|SQL_BINARY|  
|BIT|BIT|SQL_BIT|  
|LEISTUNGSINDIKATOR|LEISTUNGSINDIKATOR|SQL_INTEGER|  
|CURRENCY|CURRENCY|SQL_NUMERIC|  
|DATUM/UHRZEIT|DATETIME|SQL_TIMESTAMP|  
|GUID|GUID|SQL_GUID|  
|LANGE BINÄRDATEI|LONGBINARY|SQL_LONGVARBINARY|  
|LANGER TEXT|LONGTEXT|SQL_LONGVARCHAR[2] SQL_WLONGVARCHAR[3]|  
|MEMO|LONGTEXT|SQL_LONGVARCHAR[2] SQL_WLONGVARCHAR[3]|  
|Anzahl (Feldgröße = SINGLE)|EINZELNE|SQL_REAL|  
|Anzahl (Feldgröße = DOUBLE)|DOUBLE|SQL_DOUBLE|  
|NUMBER (FieldSize= BYTE)|BYTE OHNE VORZEICHEN|SQL_TINYINT|  
|Anzahl (Feldgröße = ganze Zahl)|SHORT|SQL_SMALLINT|  
|Anzahl (Feldgröße = LONG Integer-Wert)|LONG|SQL_INTEGER|  
|NUMERIC|NUMERIC|SQL_NUMERIC|  
|OLE|LONGBINARY|SQL_LONGVARBINARY|  
|TEXT|VARCHAR|SQL_VARCHAR[1] SQL_WVARCHAR[2]|  
|VARBINARY|VARBINARY|SQL_VARBINARY|  
  
 [1] auf nur 4.0-Anwendungen sind. Maximale Länge von 4.000 Byte. Verhalten LONGBINARY ähnelt.  
  
 [2] nur für-ANSI-Anwendungen.  
  
 [3] nur für Unicode-"und" Access 4.0-Anwendungen.  
  
> [!NOTE]  
>  **SQLGetTypeInfo** ODBC-Datentypen zurückgegeben. Es wird nicht alle Microsoft Access-Datentypen zurückgegeben, wenn mehr als eine Microsoft Access-Typ in den gleichen ODBC-SQL-Datentyp zugeordnet ist. Alle Konvertierungen, die in Anhang D des der *ODBC Programmer's Reference* werden für die SQL-Datentypen, die in der vorherigen Tabelle aufgeführten unterstützt.  
  
 Die folgende Tabelle zeigt die Einschränkungen für Microsoft Access-Datentypen.  
  
|Datentyp|Description|  
|---------------|-----------------|  
|BINARY, VARBINARY und VARCHAR|Erstellen einer BINARY, VARBINARY und VARCHAR-Spalte 0 (null) oder nicht angegebene Länge gibt tatsächlich eine 510-Byte-Spalte zurück.|  
|BYTE|Auch, wenn ein Feld für die Microsoft Access Zahl mit einem BYTE gleich Feldgröße nicht signiert ist, kann eine negative Zahl in das Feld eingefügt werden, wenn der Microsoft Access-Treiber verwendet.|  
|CHAR, VARCHAR und LONGVARCHAR|Ein Zeichenfolgenliteral kann ANSI-Zeichen (1 bis 255 dezimal) enthalten. Verwenden Sie zwei aufeinander folgende einfache Anführungszeichen ("), um ein einfaches Anführungszeichen (') darzustellen.<br /><br /> Verfahren sollte verwendet werden, um Zeichendaten zu übergeben, bei Verwendung von Sonderzeichen in einem Zeichen-Datentypspalte.|  
|DATE|Date-Werte müssen werden gemäß der kanonischen ODBC-Datumsformat getrennt oder durch das Trennzeichen "DateTime" ("#") getrennt. Andernfalls, Microsoft Access wird der Wert wird als ein arithmetischer Ausdruck behandelt und löst keine Warnung oder einen Fehler.<br /><br /> Z. B. das Datum "5. März 1996" muss, als dargestellt werden {d ' 1996-03-05 "} oder #03/05/1996 #; andernfalls nur 03/05/1993 gesendet wird, wird Microsoft Access dies als 3 geteilt durch 5 geteilt durch 1996 ausgewertet. Dieser Wert wird aufgerundet, um die ganze Zahl 0, und da 1899-12-31 der 0 (null) Tag zugeordnet ist, ist dies das Datum verwendet.<br /><br /> Einem senkrechten Strich (&#124;) kann nicht in einen Datumswert verwendet werden, auch wenn es wieder in Anführungszeichen eingeschlossen.|  
|GUID|Der Datentyp auf der Microsoft Access 4.0 beschränkt.|  
|NUMERIC|Der Datentyp auf der Microsoft Access 4.0 beschränkt.|  
  
 Weitere Einschränkungen für Datentypen finden Sie im [Datumstypen](../../odbc/microsoft/data-type-limitations.md).
